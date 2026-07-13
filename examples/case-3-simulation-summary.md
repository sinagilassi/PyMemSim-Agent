# Case 3 Simulation Summary

## Execution Status

Status: Completed with warnings

Execution date: 2026-07-13

MCP tool used: `simulate_gas_hfm`

MCP package version: `pymemsim-mcp 0.5.0`

Reference validation: `check_yaml_reference` returned `true`

Warning: the co-current `1.0e-5 mol/s` feed-flow point converged numerically but is physically invalid. It returned a stage cut above 100%, zero retentate flow, and a large molar closure residual. It should not be used for engineering interpretation.

## Validated Inputs

Components:

| Component | Formula | State | Feed mole fraction |
|---|---:|---:|---:|
| oxygen | O2 | g | 0.205 |
| nitrogen | N2 | g | 0.795 |

Operating conditions:

| Quantity | Value | Unit |
|---|---:|---:|
| Feed temperature | 296.15 | K |
| Feed pressure | 690000 | Pa |
| Permeate pressure | 100000 | Pa |

Module geometry:

| Quantity | Value | Unit |
|---|---:|---:|
| Number of fibers | 368 | 1 |
| Fiber length | 0.25 | m |
| Fiber inner diameter | 80e-6 | m |
| Fiber outer diameter | 160e-6 | m |
| Module diameter | 0.0095 | m |

Membrane transport:

| Component | Permeance | Unit |
|---|---:|---:|
| O2 | 9.30 | GPU |
| N2 | 1.80 | GPU |

Simulation options:

| Option | Value |
|---|---|
| Heat transfer mode | isothermal |
| Feed pressure mode | state_variable |
| Permeate pressure mode | state_variable |
| Gas model | ideal |
| Target component | N2-g |
| Length span | [0, 0.25] m |

Thermodynamic reference content included molecular weight and gas viscosity for O2 and N2 from the case-3 input specification.

## Computed Outputs

### Co-current

| Case ID | Feed flow (mol/s) | Stage cut (%) | Retentate N2 (mol %) | Permeate N2 (mol %) | Molar closure residual |
|---|---:|---:|---:|---:|---:|
| case-3-1-01 | 5.00e-4 | 5.3529 | 81.0347 | 52.3639 | 6.51e-16 |
| case-3-1-02 | 4.40e-4 | 6.0666 | 81.2394 | 52.5679 | 4.93e-16 |
| case-3-1-03 | 1.00e-4 | 24.8125 | 86.4756 | 58.3624 | 5.42e-16 |
| case-3-1-04 | 5.00e-5 | 45.7012 | 91.3476 | 65.4235 | 4.07e-16 |
| case-3-1-05 | 4.50e-5 | 49.9783 | 92.1347 | 66.8543 | 1.05e-15 |
| case-3-1-06 | 4.00e-5 | 55.1920 | 92.9837 | 68.5531 | 3.39e-16 |
| case-3-1-07 | 3.50e-5 | 61.7212 | 93.8788 | 70.5824 | 5.81e-16 |
| case-3-1-08 | 3.00e-5 | 70.2024 | 94.7881 | 73.0109 | 5.65e-16 |
| case-3-1-09 | 2.50e-5 | 81.7998 | 95.6662 | 75.9031 | 4.07e-16 |
| case-3-1-10 | 1.00e-5 | 349.3554 | 0.0000 | 34.4882 | -2.49e+0 |

### Counter-current

| Case ID | Feed flow (mol/s) | Stage cut (%) | Retentate N2 (mol %) | Permeate N2 (mol %) | Molar closure residual |
|---|---:|---:|---:|---:|---:|
| case-3-2-01 | 5.00e-4 | 5.3764 | 81.0610 | 52.0267 | 4.34e-16 |
| case-3-2-02 | 4.40e-4 | 6.0967 | 81.2734 | 52.1857 | 4.93e-16 |
| case-3-2-03 | 1.00e-4 | 25.2640 | 87.1485 | 56.8741 | 4.07e-16 |
| case-3-2-04 | 5.00e-5 | 46.7970 | 93.7523 | 63.2967 | 4.07e-16 |
| case-3-2-05 | 4.00e-5 | 56.4047 | 96.2898 | 66.5231 | 5.08e-16 |
| case-3-2-06 | 3.50e-5 | 62.8973 | 97.6914 | 68.7690 | 7.74e-16 |
| case-3-2-07 | 3.00e-5 | 71.1918 | 98.9907 | 71.6129 | 6.78e-16 |
| case-3-2-08 | 2.50e-5 | 82.3763 | 99.8342 | 75.1497 | 4.07e-16 |
| case-3-2-09 | 2.30e-5 | 88.1222 | 99.9648 | 76.7416 | 2.95e-16 |

## Diagnostics

All listed solver calls returned success.

Co-current solver message: `The solver successfully reached the end of the integration interval.`

Counter-current solver message: `The algorithm converged to the desired accuracy.`

The backend logged non-fatal reference-linking warnings about empty `EQUATIONS`. These warnings were not treated as simulation failures because this isothermal pressure-drop case required molecular weight and gas viscosity data, not heat-capacity or other temperature-dependent equations.

## Engineering Interpretation

As feed flow decreases, stage cut increases and retentate nitrogen purity rises because oxygen has the higher membrane permeance and preferentially transfers to the permeate side.

Counter-current operation produces stronger nitrogen enrichment in the retentate than co-current operation at comparable stage cut. Around 82% stage cut, the counter-current case gives about 99.83 mol % N2 in the retentate, while the co-current case gives about 95.67 mol % N2.

The co-current `1.0e-5 mol/s` point is beyond the feasible operating region for this setup and should be excluded from comparisons.

## Limitations

The thermodynamic reference used molecular weight and gas viscosity values from the case specification. No external thermodynamic source retrieval was performed during this run.

The simulations used an isothermal ideal-gas model. Non-isothermal effects and real-gas corrections were not evaluated.

The reported values are deterministic MCP outputs from the executed solver calls; no LLM-generated numerical estimates are included.
