# Sensitivity Analysis Workflow

## Purpose

This workflow guides the agent through sensitivity analysis for membrane separation simulations using PyMemSim-MCP.

The goal is to vary selected conventional inputs systematically while keeping the thermodynamic reference structure consistent, unless the sensitivity study explicitly concerns thermodynamic data or equations.

## When to Use

Use this workflow when the user asks to:

- study the effect of feed flow rate;
- study the effect of pressure ratio;
- study the effect of temperature;
- compare different feed compositions;
- compare membrane permeance values;
- analyze sensitivity of stage-cut, purity, recovery, or flow profiles;
- run multiple PyMemSim-MCP simulation cases.

## Required Inputs

The agent should identify or collect:

- base-case membrane simulation inputs;
- component list;
- base-case `reference_content`;
- selected sensitivity variable;
- range or list of values to test;
- fixed variables;
- performance metrics to compare;
- solver options, if needed.

## Required Tools / Components

- PyMemSim-MCP
- PyMemSim
- `pythermodb-reference-maker`, if reference content is missing
- PyThermoDB
- PyThermoLinkDB
- PyCUC, internally inside the scientific application layer

## Agent Responsibilities

The agent should:

1. Establish a complete base case.
2. Identify which input variable is being varied.
3. Keep all non-varied inputs fixed unless otherwise specified.
4. Use consistent `reference_content` across cases when components and thermodynamic requirements do not change.
5. Run or request one PyMemSim-MCP simulation per case.
6. Compare returned results using clear engineering metrics.
7. Explain trends without claiming unsupported causality.

## Boundaries

The agent must not:

- manually create the runtime `model_source`;
- change thermodynamic references between cases unless required;
- silently change units between cases;
- invent missing operating conditions;
- invent missing permeance values;
- perform final numerical results manually when PyMemSim-MCP is available;
- compare cases that are not physically consistent.

## Step-by-Step Procedure

1. Parse the user request and identify the sensitivity objective.
2. Define the base-case simulation.
3. Identify the variable to be changed.
4. Define the tested values for the sensitivity variable.
5. Identify variables that must remain fixed.
6. Confirm that `reference_content` is available.
7. If `reference_content` is missing, follow the Reference Content Generation Workflow.
8. Prepare a case list where each case contains:
   - the same `reference_content`, unless thermodynamics are intentionally varied;
   - modified conventional input for the sensitivity variable;
   - unchanged fixed inputs.
9. Run each case through PyMemSim-MCP.
10. Collect structured results.
11. Compare selected performance indicators.
12. Explain the trend in chemical engineering terms.

## Expected Output

The final response should include:

- base-case description;
- sensitivity variable;
- tested values;
- fixed assumptions;
- comparison table or structured summary;
- trend interpretation;
- limitations and possible next checks.

Typical performance indicators include:

- stage-cut;
- permeate purity;
- retentate purity;
- component recovery;
- flow-rate changes;
- composition profiles;
- temperature profiles when heat balance is active.

## Validation Checklist

Before finalizing, check that:

- the base case is complete;
- the sensitivity variable is clearly defined;
- all tested values have units;
- fixed variables remain fixed;
- each case uses consistent thermodynamic reference content unless intentionally varied;
- results come from PyMemSim-MCP;
- trends are explained without unsupported assumptions.

## Common Failure Cases

### Missing range of values

Use a reasonable default only if the user has allowed assumptions. Otherwise, ask for the range or provide a qualitative workflow.

### Missing base-case data

State what information is missing. Do not invent quantitative values.

### Changing multiple variables accidentally

Clearly separate the sensitivity variable from fixed inputs.

### Unit mismatch across cases

Preserve explicit units. Internal conversion is handled by the scientific application layer through PyCUC.

### Solver instability in some cases

Report which cases failed and suggest checking numerical settings, pressure ratios, or boundary conditions.

## Key Rule

Sensitivity analysis varies conventional simulation inputs systematically. The runtime `model_source` is still constructed internally inside each MCP tool function call from the supplied `reference_content`.
