# Reference Content Generation Workflow

## Purpose

This workflow guides the agent in preparing YAML-formatted `reference_content` for thermodynamic data, equations, constants, and metadata required by PyMemSim-MCP or other scientific MCP tools.

The goal is to create a structured thermodynamic reference that can later be passed to an MCP tool function. The MCP tool function will internally parse this reference and construct the runtime `model_source`.

## When to Use

Use this workflow when:

- a simulation requires thermodynamic data or equations;
- the required `reference_content` is not already available;
- the user provides only component names and operating conditions;
- the MCP tool requires YAML thermodynamic reference content;
- a new component, mixture, or property correlation must be prepared.

## Required Inputs

The agent should identify or collect:

- component names;
- component identifiers, when available;
- target simulation type;
- required thermodynamic properties;
- required equations or correlations;
- required units;
- preferred data source, if specified by the user;
- validity range, if available from the source.

## Required Tools / Components

- `pythermodb-reference-maker`
- PyThermoDB-compatible reference structure
- PyThermoLinkDB-compatible model-source format
- reliable external thermodynamic references, when available

## Agent Responsibilities

The agent should:

1. Identify all chemical components involved in the simulation.
2. Determine what thermodynamic data and equations are required.
3. Use `pythermodb-reference-maker` to prepare YAML-based `reference_content`.
4. Ensure the output contains both `data_source` and `equation_source` when equations are required.
5. Preserve all source units explicitly.
6. Avoid inventing values, parameters, or validity ranges.
7. Return the generated YAML as `reference_content` for later MCP execution.

## Boundaries

The agent must not:

- manually create the runtime `model_source`;
- ask the user to provide a pre-built `model_source`;
- invent missing thermodynamic constants or equation coefficients;
- silently change source units;
- remove metadata required for later validation;
- hardcode thermodynamic equations directly into PyMemSim inputs.

The agent prepares `reference_content`. The MCP tool function builds `model_source` internally.

## Step-by-Step Procedure

1. Parse the user request and identify the target simulation.
2. Extract all chemical components.
3. Determine which properties are needed for the simulation.
4. Determine which equations or correlations are needed.
5. Use `pythermodb-reference-maker` to retrieve or construct the required thermodynamic reference.
6. Ensure the YAML reference includes `data_source`.
7. Ensure the YAML reference includes `equation_source` when equations or correlations are needed.
8. Check that all properties, parameters, arguments, returns, and units are explicitly defined.
9. Preserve the original source units in the YAML reference.
10. Return the YAML content as `reference_content`.

## Expected Output

The output should be YAML-compatible thermodynamic `reference_content` ready to be passed to a PyMemSim-MCP tool.

The reference should normally include:

- component definitions;
- thermodynamic constants;
- property data;
- equation definitions;
- equation parameters;
- argument definitions;
- return definitions;
- units;
- metadata and source information, when available.

## Validation Checklist

Before using the reference, check that:

- all components are included;
- `data_source` exists;
- `equation_source` exists when required;
- all units are explicit;
- equation arguments are defined;
- equation parameters are complete;
- return variables are defined;
- no values are invented;
- the reference is suitable for PyThermoDB and PyThermoLinkDB processing.

## Common Failure Cases

### Missing component data

Do not invent missing values. Report the missing data and request or retrieve a reliable source.

### Missing equation parameters

Do not create approximate coefficients unless the user explicitly asks for a rough illustrative example. For production simulation, use a reliable source.

### Missing units

Do not omit units. Add units only when they are supported by the source or clearly defined by the reference format.

### Conflicting data sources

Prefer the source specified by the user. If no source is specified, prefer reliable scientific or official thermodynamic references. Mention any inconsistency if multiple sources disagree.

## Key Rule

The YAML `reference_content` is the agent-facing thermodynamic reference. The runtime `model_source` is constructed internally inside the MCP tool function.
