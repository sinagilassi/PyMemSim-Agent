# Prompt 4

Use the thermodynamic-reference-generation skill to collect and organize the required thermodynamic data and property equations for the specified components.

Components: CO₂ and CH₄
Application: construction of a thermodynamic reference for chemical-engineering model-source generation
Required output: YAML-based `reference_content`

For each component, search for and collect the following thermodynamic properties when available:

* critical temperature, (T_c)
* critical pressure, (P_c)
* critical volume, (V_c), if available
* acentric factor, (\omega), if available
* standard enthalpy of formation, (\Delta H_f^\circ)
* standard Gibbs free energy of formation, (\Delta G_f^\circ)
* molecular weight
* normal boiling point, if available

Also collect or define the following temperature-dependent property equations when available:

* vapor-pressure equation
* ideal-gas heat-capacity equation
* gas-density equation or density correlation, if available

For each data item and equation, include the property name, symbol, value or equation body, parameters, units, temperature range or validity range when available, and source information. The equation definitions must include argument names, argument units, return variable, return unit, and all required coefficients.

use reliable external thermodynamic sources such as NIST, DIPPR-style references, peer-reviewed literature, or authoritative handbooks.

Construct the output in the standard YAML-based `reference_content` format required by the model-source construction workflow.

Save the generated YAML reference in the **results** folder.

After generating the YAML file, run the internal skill-level validation procedure. Check that all required fields are present, all units are explicitly defined, all equations have complete parameter and argument definitions, and no undefined symbols are used in equation bodies. Report whether the reference passed validation. If validation fails, revise the YAML reference and repeat the validation before finalizing the output.
