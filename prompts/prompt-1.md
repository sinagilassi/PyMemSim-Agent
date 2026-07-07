# Prompt 1

Use the thermodynamic-reference-generation skill to construct a YAML-based `reference_content` for the following membrane-separation case.

Components: CO₂ and CH₄
Application: gas-separation membrane simulation
Required use: construction of a model source for PyMemSim-MCP

The reference must include all thermodynamic data and equations required by the membrane simulation workflow. For each component, define the required thermodynamic constants, property names, equation parameters, argument definitions, return variables, symbols, units, and validity information when available.

You can check the **data** folder for thermodynamic data; if the required data are not available there, use reliable external sources.

Save the constructed reference in the results folder.

Do not perform the membrane simulation. Only construct the thermodynamic reference. After generating the YAML content, run the internal validation/checking procedure provided by the skill. Report whether the generated reference passed the skill-level validation before it is submitted to the MCP server.