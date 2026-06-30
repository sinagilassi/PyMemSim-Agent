# Membrane Simulation Workflow

## Purpose

This workflow guides the agent through a membrane separation simulation using PyMemSim-MCP.

The workflow ensures that the agent separates conventional membrane inputs from thermodynamic reference content and relies on the MCP tool function to build the internal runtime `model_source`.

## When to Use

Use this workflow when the user asks to:

- simulate a membrane gas separation process;
- analyze a hollow fiber membrane module;
- calculate stage-cut, recovery, purity, or flow profiles;
- compare membrane operating conditions;
- reproduce or study a PyMemSim case;
- run a PyMemSim-MCP simulation with thermodynamic references.

## Required Inputs

The agent should identify or collect:

- gas or liquid components;
- feed flow rate;
- feed composition;
- feed pressure;
- permeate pressure;
- feed temperature;
- membrane geometry;
- membrane permeance values;
- flow configuration, such as co-current or counter-current;
- solver options, if needed;
- YAML `reference_content`, or enough information to generate it.

## Required Tools / Components

- PyMemSim-MCP
- `pythermodb-reference-maker`
- PyThermoDB
- PyThermoLinkDB
- PyCUC, internally inside the scientific application layer

## Agent Responsibilities

The agent should:

1. Understand the user’s membrane separation problem.
2. Identify required conventional simulation inputs.
3. Identify required thermodynamic reference content.
4. Generate or supply `reference_content` using `pythermodb-reference-maker` when needed.
5. Pass `reference_content` and conventional inputs to the appropriate PyMemSim-MCP tool.
6. Let the MCP tool function internally construct the runtime `model_source`.
7. Let the scientific application layer internally perform unit harmonization through PyCUC.
8. Let PyMemSim perform the deterministic numerical calculation.
9. Explain the returned results in membrane engineering terms.

## Boundaries

The agent must not:

- manually create `model_source` outside the MCP tool function;
- ask the user to provide a pre-built `model_source`;
- call PyCUC as an external workflow step;
- invent missing thermodynamic data;
- invent membrane permeance values;
- silently change or omit units;
- perform the final numerical simulation manually when PyMemSim-MCP is available;
- replace deterministic PyMemSim execution with approximate LLM calculations.

## Step-by-Step Procedure

1. Parse the user request.
2. Identify the membrane separation system and components.
3. Separate the required inputs into:
   - `reference_content` requirements;
   - conventional process and membrane inputs.
4. Check whether `reference_content` is already available.
5. If `reference_content` is missing, follow the Reference Content Generation Workflow.
6. Verify that the YAML reference includes required data and equations.
7. Verify that conventional inputs are complete and physically meaningful.
8. Call the appropriate PyMemSim-MCP tool using:
   - `reference_content`;
   - conventional simulation inputs.
9. Allow the MCP tool function to internally:
   - parse and validate `reference_content`;
   - construct the runtime `model_source`;
   - harmonize units through the scientific application layer;
   - execute PyMemSim.
10. Review the structured results returned by the MCP tool.
11. Explain the results clearly, including assumptions, limitations, and engineering interpretation.

## Expected Output

The final response should include:

- simulation objective;
- main assumptions;
- input summary;
- calculated membrane performance indicators;
- stage-cut, recovery, purity, or flow profiles when available;
- interpretation of trends;
- warnings about missing data or limitations.

## Validation Checklist

Before finalizing the workflow, check that:

- all components are defined;
- feed composition is valid;
- pressure and temperature are physically meaningful;
- membrane geometry is defined;
- permeance values are available;
- `reference_content` contains required thermodynamic data;
- units are explicit;
- numerical results come from PyMemSim-MCP;
- the final explanation does not imply that the LLM performed the numerical calculation.

## Common Failure Cases

### Missing thermodynamic reference

Use `pythermodb-reference-maker` to prepare `reference_content`. Do not create `model_source` manually.

### Missing membrane properties

Ask for membrane geometry or permeance values, or state clearly that a quantitative simulation cannot be completed.

### Unit inconsistency

Preserve source units in `reference_content`. The scientific application layer handles internal conversion through PyCUC.

### Solver failure

Report the failure clearly. Suggest checking feed conditions, pressure ratios, membrane parameters, boundary conditions, or solver options.

### Incomplete simulation result

Explain what was computed and what remains missing. Do not overinterpret incomplete outputs.

## Key Rule

The LLM prepares or supplies `reference_content` and conventional inputs. The MCP tool function builds `model_source` internally and PyMemSim performs the deterministic simulation.
