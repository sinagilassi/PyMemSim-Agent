# Prompt 2

Construct the thermodynamic `reference_content` required for a CO₂/CH₄ hollow-fiber membrane simulation.

The reference should support temperature-dependent thermodynamic property evaluation during the simulation. Include component-level data and property correlations required for evaluating molar enthalpy or heat-capacity-related quantities. Use reliable thermodynamic sources where applicable and organize the result in the standard YAML structure expected by the model-source construction workflow.

The YAML output must contain:

1. equation body, parameters, arguments, units, symbols, and return definitions;
2. clear component identifiers for CO₂ and CH₄;
3. unit specifications for all dimensional quantities.

After creating the reference, verify that all required fields are present and that the structure can be parsed by the reference-validation script.

Do not use local or proprietary data sources; only use reliable external sources such as NIST web book.

Save the constructed reference in the results folder.
