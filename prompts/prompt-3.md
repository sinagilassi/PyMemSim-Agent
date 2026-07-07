# Prompt 3

Use the thermodynamic-reference-generation skill to prepare the YAML-based `reference_content` for an O₂/N₂ membrane-separation case.

The objective is to generate a structured thermodynamic reference that can be passed to the PyMemSim-MCP server for model-source construction. The reference should include the required thermodynamic data and temperature-dependent equations for O₂ and N₂.

For each component, include the required property identifiers, equation parameters, argument names, argument units, returned variables, returned units, and any available validity range. The generated YAML should be self-contained and should not rely on undefined variables or implicit unit assumptions.

After the YAML reference is generated, run the skill-level validation procedure and report whether the reference passes structural validation before MCP-side model-source construction.

Do not use local or proprietary data sources; only use reliable external sources such as NIST web book.

Save the constructed reference in the results folder.