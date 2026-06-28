# Thermodynamic Property Correlations and Complete Reference Tables

## Chapter Overview

This chapter documents a structured thermodynamic reference used for computational property evaluation. The reference is organized as a machine-readable databook containing property-specific tables, equation definitions, units, symbols, and complete compound records. The purpose is to make the data understandable both for human readers and for agentic or MCP-enabled simulation workflows.

The source contains one databook, `CUSTOM-REF-1`, with six major property tables: ideal-gas heat capacity, general thermodynamic data, vapor pressure, liquid heat capacity, enthalpy of vaporization, and liquid density.

## 1. Reference Architecture

The reference separates three important parts of a thermodynamic model source:

1. **Property names**, such as `ideal-gas-heat-capacity` or `vapor-pressure`.

2. **Equation definitions**, which describe how a property is calculated from temperature and parameters.

3. **Compound records**, which provide the numerical constants required by the equations.

This design is useful for packages such as PyThermoDB, PyThermoLinkDB, PyMemSim, or MCP endpoints because the same property data can be parsed, validated, converted, and injected into different scientific workflows.

## 2. Ideal Gas Heat Capacity (`ideal-gas-heat-capacity`)

**Property identifier:** `ideal-gas-heat-capacity`  

**Property symbol:** `Cp_IG`  

**Table ID:** `1`

### Description

This table provides the ideal gas heat capacity (Cp_IG) in J/mol.K as a function of temperature (T) in K. Two correlation forms are used depending on the compound. Equation A.1 (dimensionless form Cp/R), Equation A.2 (absolute Cp form)

### Correlation or Data Definition


The ideal-gas heat-capacity table uses two alternative equation forms.

**Equation 1: dimensionless heat-capacity form**

```text
y = T / (A + T)
Cp_IG = R * [ B + (C - B) * y^2 * { 1 + (y - 1) * (D + E*y + F*y^2 + G*y^3) } ]
```

**Equation 2: hyperbolic-function form**

```text
term1 = C / T
term2 = E / T
Cp_IG = [ A + B*(term1/sinh(term1))^2 + D*(term2/cosh(term2))^2 ] / 1000
```


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'universal-gas-constant', 'Eq']`

**Symbol:** `['None', 'None', 'None', 'None', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'R', 'Cp_IG']`

**Unit:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 1, 1, 1, 'J/mol.K', 'J/mol.K']`

### Complete Data Table: Ideal Gas Heat Capacity

| No. | Name | Formula | State | A | B | C | D | E | F | G | universal-gas-constant | Eq |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | g | 33484.8 | 9275.3 | 1218.48 | 20241.4 | 2919.59 | 0 | 0 | 8.314 | 2 |
| 2 | ammonia | NH3 | g | 34083.2 | 26087 | 990.77 | 33100 | 2905.6 | 0 | 0 | 8.314 | 2 |
| 3 | hydrogen chloride | HCl | g | 432.772 | 3.42841 | 3.54436 | -10.4977 | -77.3769 | 403.951 | -442.346 | 8.314 | 1 |
| 4 | chlorine | Cl2 | g | 29197.7 | 8502.8 | 405.49 | -3253.99 | 3892.43 | 0 | 0 | 8.314 | 2 |
| 5 | nitrogen | N2 | g | 29108.8 | 8526.28 | 1678.41 | 66784.8 | 10672.6 | 0 | 0 | 8.314 | 2 |
| 6 | oxygen | O2 | g | 29116.9 | 10437.5 | 2565.44 | 9338.84 | 1149.97 | 0 | 0 | 8.314 | 2 |
| 7 | hydrogen | H2 | g | 20463.6 | 9591.19 | 216.79 | 16524.8 | 3955.44 | 0 | 0 | 8.314 | 2 |
| 8 | sulfur dioxide | SO2 | g | 904.534 | 3.98118 | 5.66358 | 3.21967 | -88.8814 | 186.924 | -121.555 | 8.314 | 1 |
| 9 | carbon monoxide | CO | g | 29104.6 | 8665.81 | 3043.79 | 8336.18 | 1531.93 | 0 | 0 | 8.314 | 2 |
| 10 | carbon dioxide | CO2 | g | 188.274 | 3.50426 | 8.29771 | 4.71883 | -11.7511 | 13.9404 | -6.73002 | 8.314 | 1 |
| 11 | methane | CH4 | g | 33356.3 | 45763.8 | 1025.42 | 48699 | 2664.97 | 0 | 0 | 8.314 | 2 |
| 12 | ethane | C2H6 | g | 903.411 | 4.48148 | 11.6905 | 8.47923 | -77.0215 | 122.977 | -74.06 | 8.314 | 1 |
| 13 | propane | C3H8 | g | 1222.85 | 4.63428 | 6.17777 | -31.8448 | -487.589 | 1216.91 | -972.093 | 8.314 | 1 |
| 14 | n-butane | C4H10 | g | 668.649 | 8.9081 | 14.2467 | 41.0466 | -258.183 | 411.824 | -258.688 | 8.314 | 1 |
| 15 | isobutane | C4H10 | g | 2084.48 | 5.07542 | 7.06198 | -264.302 | -47.2786 | 2309.95 | -3524.86 | 8.314 | 1 |
| 16 | n-pentane | C5H12 | g | 1074.74 | 8.97762 | 11.9251 | 31.168 | -592.504 | 1201.65 | -830.327 | 8.314 | 1 |
| 17 | n-hexane | C6H14 | g | 918.015 | 11.2939 | 18.0587 | 29.3397 | -307.728 | 556.385 | -356.722 | 8.314 | 1 |
| 18 | cyclohexane | C6H12 | g | 671.99 | 4.04945 | 5.43698 | 67.1777 | -795.756 | 1090.93 | -701.787 | 8.314 | 1 |
| 19 | n-heptane | C7H16 | g | 751.215 | 14.7884 | 17.829 | 121.155 | -843.826 | 1360.01 | -824.873 | 8.314 | 1 |
| 20 | n-octane | C8H18 | g | 580.693 | 22.7885 | 32.5066 | 73.7754 | -348.564 | 493.588 | -270.291 | 8.314 | 1 |
| 21 | ethylene | C2H4 | g | 100.68 | 3.46632 | 18.868 | -1.58496 | 6.37008 | 5e-05 | -3e-05 | 8.314 | 1 |
| 22 | propylene | C3H6 | g | 1178.94 | 4.27276 | 4.78834 | -97.5831 | -915.406 | 2188.95 | -1706.13 | 8.314 | 1 |
| 23 | 1-butene | C4H8 | g | 444.427 | 4.00215 | 4.77657 | -103.784 | 269.015 | -545.252 | 27.1531 | 8.314 | 1 |
| 24 | methanol | CH3OH | g | 72.3217 | -43.806 | 18.0425 | -8.74148 | 10.3778 | -0.33156 | -1.059 | 8.314 | 1 |
| 25 | ethanol | C2H5OH | g | 1165.86 | 4.70209 | 9.77865 | -1.17688 | -135.768 | 322.76 | -247.735 | 8.314 | 1 |
| 26 | n-propanol | C3H7OH | g | 61723.9 | 203342 | 757.27 | -96727.7 | 880.13 | 0 | 0 | 8.314 | 2 |
| 27 | n-butanol | C4H9OH | g | 74802.1 | 167505 | -711.59 | 130880 | 2223.47 | 0 | 0 | 8.314 | 2 |
| 28 | ethylene glycol | C2H6O2 | g | 316.79 | 3.05241 | 3.58464 | -152.763 | 212.945 | 84.6065 | -662.811 | 8.314 | 1 |
| 29 | isopropanol | C3H7OH | g | 313.107 | 8.96218 | 9.41683 | 702.945 | -3295.08 | 5345.62 | -3435.86 | 8.314 | 1 |
| 30 | acetic acid | CH3COOH | g | 589.884 | 5.10642 | 5.52776 | 211.49 | -1404.11 | 2057.42 | -1317.65 | 8.314 | 1 |
| 31 | methyl acetate | C3H6O2 | g | 54664.4 | 179100 | 595.63 | -106515 | 660.06 | 0 | 0 | 8.314 | 2 |
| 32 | ethyl acetate | C4H8O2 | g | 99847.2 | 210799 | -947.39 | -52228.8 | 1203.35 | 0 | 0 | 8.314 | 2 |
| 33 | vinyl acetate | C4H6O2 | g | 339.005 | 10.8508 | 11.2026 | 1116.1 | -5117.97 | 8086.03 | -5022.37 | 8.314 | 1 |
| 34 | methyl-tert-butyl ether | C5H12O | g | 100524 | 206853 | -807.44 | 137642 | 2358.16 | 0 | 0 | 8.314 | 2 |
| 35 | acetone | C3H6O | g | 58083.2 | 101389 | -761.09 | 84650.3 | 2186.59 | 0 | 0 | 8.314 | 2 |
| 36 | benzene | C6H6 | g | 560.936 | 4.00088 | 6.20811 | 22.193 | -159.248 | -48.9706 | 155.541 | 8.314 | 1 |
| 37 | toluene | C6H5CH3 | g | 1250.95 | 3.99957 | 10.7337 | -19.7805 | -218.247 | 677.574 | -595.415 | 8.314 | 1 |
| 38 | p-xylene | C8H10 | g | 1299.91 | 4.43091 | 6.06047 | -229.739 | -186.844 | 1156.78 | -1164.53 | 8.314 | 1 |

**Number of records:** 38

## 3. General Thermodynamic and Physical Data (`general-data`)

**Property identifier:** `general-data`  

**Property symbol:** `General Data`  

**Table ID:** `2`

### Description

This table provides general thermodynamic and physical data for selected compounds. Data includes critical properties, acentric factor, phase-change temperatures, and standard formation properties.

### Correlation or Data Definition


This table does not define a temperature-dependent correlation. It provides constant compound properties used by the other property correlations and by thermodynamic models.


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'critical-temperature', 'critical-pressure', 'critical-molar-volume', 'molecular-weight', 'acentric-factor', 'boiling-temperature', 'melting-temperature', 'enthalpy-of-fusion', 'enthalpy-of-formation', 'gibbs-energy-of-formation']`

**Symbol:** `['None', 'None', 'None', 'None', 'Tc', 'Pc', 'Vc', 'MW', 'AcFa', 'Tb', 'Tm', 'EnFus', 'EnFo_IG', 'GiEnFo_IG']`

**Unit:** `['None', 'None', 'None', 'None', 'K', 'bar', 'cm3/mol', 'g/mol', 'None', 'K', 'K', 'J/g', 'J/mol', 'J/mol']`

**Conversion:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]`

### Complete Data Table: General Thermodynamic and Physical Data

| No. | Name | Formula | State | critical-temperature | critical-pressure | critical-molar-volume | molecular-weight | acentric-factor | boiling-temperature | melting-temperature | enthalpy-of-fusion | enthalpy-of-formation | gibbs-energy-of-formation |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | l | 647.096 | 220.64 | 55.947 | 18.015 | 0.3443 | 373.13 | 273.15 | 333.1 | -241820 | -228590 |
| 2 | ammonia | NH3 | g | 405.5 | 113.592 | 75.768 | 17.031 | 0.256 | 239.82 | 195.45 | 332.2 | -45773 | -16150 |
| 3 | hydrogen chloride | HCl | g | 324.55 | 82.631 | 88.719 | 36.461 | 0.128 | 188.2 | 158.95 | 54.9 | -92310 | -95300 |
| 4 | chlorine | Cl2 | g | 416.958 | 79.911 | 122.927 | 70.906 | 0.0874 | 239.17 | 172.15 | 90.3 | 0 | 0 |
| 5 | nitrogen | N2 | g | 126.192 | 33.958 | 89.416 | 28.014 | 0.0372 | 77.36 | 63.15 | 25.7 | 0 | 0 |
| 6 | oxygen | O2 | g | 154.599 | 50.464 | 74.948 | 31.999 | 0.0221 | 90.19 | 54.35 | 13.9 | 0 | 0 |
| 7 | hydrogen | H2 | g | 33.19 | 13.15 | 66.938 | 2.016 | -0.2187 | 20.38 | 13.95 | 58.1 | 0 | 0 |
| 8 | sulfur dioxide | SO2 | g | 430.643 | 78.757 | 122.087 | 64.062 | 0.2552 | 263.13 | 200 | 115.5 | -296850 | -300150 |
| 9 | carbon monoxide | CO | g | 132.86 | 34.982 | 92.088 | 28.01 | 0.0503 | 81.64 | 68.15 | 30 | -110540 | -137270 |
| 10 | carbon dioxide | CO2 | g | 304.128 | 73.773 | 94.117 | 44.009 | 0.2236 | 0 | 216.55 | 204.9 | -393500 | -394380 |
| 11 | methane | CH4 | g | 190.564 | 45.992 | 98.629 | 16.043 | 0.0114 | 111.67 | 90.65 | 58.7 | -74850 | -50835 |
| 12 | ethane | C2H6 | g | 305.322 | 48.722 | 145.843 | 30.07 | 0.0995 | 184.57 | 90.35 | 95.1 | -84680 | -32930 |
| 13 | propane | C3H8 | g | 369.825 | 42.477 | 200.004 | 44.097 | 0.1524 | 231.03 | 85.45 | 79.9 | -103840 | -23470 |
| 14 | n-butane | C4H10 | g | 425.125 | 37.96 | 254.93 | 58.124 | 0.2008 | 272.66 | 134.85 | 80.2 | -126150 | -17154 |
| 15 | isobutane | C4H10 | g | 407.81 | 36.29 | 257.756 | 58.124 | 0.1835 | 261.4 | 113.55 | 78.1 | -134510 | -20878 |
| 16 | n-pentane | C5H12 | g | 469.659 | 33.689 | 306.766 | 72.151 | 0.2517 | 309.21 | 143.4 | 116.4 | -146760 | -8813 |
| 17 | n-hexane | C6H14 | g | 507.795 | 30.416 | 386.753 | 86.178 | 0.3002 | 341.87 | 177.85 | 151.8 | -167190 | -250 |
| 18 | cyclohexane | C6H12 | g | 553.6 | 40.75 | 308.263 | 84.162 | 0.2092 | 353.86 | 279.65 | 32.6 | -123300 | 31910 |
| 19 | n-heptane | C7H16 | g | 541.226 | 27.738 | 445.551 | 100.205 | 0.346 | 371.53 | 182.55 | 140.2 | -187650 | 8165 |
| 20 | n-octane | C8H18 | g | 569.57 | 25.067 | 501.835 | 114.231 | 0.3943 | 398.78 | 216.35 | 181.6 | -208750 | 16000 |
| 21 | ethylene | C2H4 | g | 282.35 | 50.418 | 130.947 | 28.054 | 0.0866 | 169.38 | 104.05 | 119.4 | 52300 | 68110 |
| 22 | propylene | C3H6 | g | 364.211 | 45.55 | 183.247 | 42.081 | 0.1461 | 225.53 | 87.85 | 71.4 | 19170 | 62150 |
| 23 | 1-butene | C4H8 | g | 419.29 | 40.057 | 235.802 | 56.108 | 0.1919 | 266.84 | 87.85 | 68.6 | -540 | 70270 |
| 24 | methanol | CH3OH | l | 513.38 | 82.159 | 113.828 | 32.042 | 0.5625 | 337.63 | 175.5 | 100.3 | -201160 | -162500 |
| 25 | ethanol | C2H5OH | l | 513.9 | 61.48 | 166.917 | 46.069 | 0.6441 | 351.41 | 159.05 | 107 | -234800 | -168280 |
| 26 | n-propanol | C3H7OH | l | 536.75 | 51.75 | 218.99 | 60.096 | 0.6211 | 370.31 | 146.95 | 89.4 | -255200 | -159900 |
| 27 | n-butanol | C4H9OH | l | 563.05 | 44.23 | 274.996 | 74.123 | 0.5905 | 390.9 | 183.85 | 126.4 | -274600 | -150300 |
| 28 | ethylene glycol | C2H4(OH)2 | l | 719.15 | 82 | 190.983 | 62.068 | 0.5129 | 470.22 | 260.15 | 160.4 | -392200 | -301800 |
| 29 | isopropanol | C3H7OH | l | 508.25 | 47.62 | 220.011 | 60.096 | 0.6631 | 355.36 | 185.25 | 90 | -272700 | -173470 |
| 30 | acetic acid | CH3COOH | l | 591.95 | 57.86 | 179.676 | 60.052 | 0.463 | 391.04 | 289.85 | 195.3 | -434830 | -376680 |
| 31 | methyl acetate | C3H6O2 | l | 506.55 | 47.5 | 228.015 | 74.079 | 0.3306 | 330.08 | 175.15 | 107.6 | -411900 | -324200 |
| 32 | ethyl acetate | C4H8O2 | l | 523.2 | 38.301 | 285.992 | 88.106 | 0.3606 | 350.27 | 189.65 | 118.9 | -442910 | -327390 |
| 33 | vinyl acetate | C4H6O2 | l | 519.15 | 39.58 | 269.978 | 86.09 | 0.3526 | 345.86 | 180.35 | 62.4 | -314900 | -227900 |
| 34 | methyl-tert-butyl ether | C5H12O | l | 497.15 | 34.3 | 328.976 | 88.15 | 0.2662 | 328.29 | 164.55 | 86.2 | -283500 | -117500 |
| 35 | acetone | C3H6O | l | 508.1 | 46.924 | 212.299 | 58.08 | 0.3064 | 329.23 | 178.45 | 99.4 | -215700 | -151300 |
| 36 | benzene | C6H6 | l | 562.014 | 49.01 | 255.044 | 78.114 | 0.2103 | 353.24 | 278.65 | 126.3 | 82930 | 129660 |
| 37 | toluene | C7H8 | l | 591.749 | 41.263 | 315.422 | 92.141 | 0.2657 | 383.75 | 178.15 | 72 | 50170 | 122200 |
| 38 | p-xylene | C8H10 | l | 616.25 | 35.11 | 377.958 | 106.168 | 0.3218 | 411.51 | 286.45 | 161.2 | 18030 | 121400 |

**Number of records:** 38

## 4. Vapor Pressure (`vapor-pressure`)

**Property identifier:** `vapor-pressure`  

**Property symbol:** `VaPr`  

**Table ID:** `3`

### Description

This table provides the vapor pressure (P) in bar as a function of temperature (T) in K. The correlation follows Table A.2. Critical pressure (Pc) is taken from Table A.1. Since Pc is stored in bar, the correlation first computes vapor pressure in bar, then converts to Pa.

### Correlation or Data Definition


The vapor-pressure table uses a reduced-temperature expression.

```text
Tr = T / Tc
tau = 1 - Tr
expo = (1 / Tr) * [ A*tau + B*tau^1.5 + C*tau^2.5 + D*tau^5 ]
VaPr = Pc * exp(expo)
```


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'A', 'B', 'C', 'D', 'critical-temperature', 'critical-pressure', 'Eq']`

**Symbol:** `['None', 'None', 'None', 'None', 'A', 'B', 'C', 'D', 'Tc', 'Pc', 'VaPr']`

**Unit:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 'K', 'bar', 'bar']`

### Complete Data Table: Vapor Pressure

| No. | Name | Formula | State | A | B | C | D | critical-temperature | critical-pressure | Eq |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | g | -7.87015 | 1.90677 | -2.31033 | -2.06339 | 647.096 | 220.64 | 1 |
| 2 | ammonia | NH3 | g | -7.30382 | 1.64995 | -2.02162 | -1.96029 | 405.5 | 113.592 | 1 |
| 3 | hydrogen chloride | HCl | g | -6.45414 | 0.934797 | -0.636477 | -1.70435 | 324.55 | 82.631 | 1 |
| 4 | chlorine | Cl2 | g | -6.44245 | 1.49284 | -1.2251 | -2.0154 | 416.958 | 79.911 | 1 |
| 5 | nitrogen | N2 | g | -6.12368 | 1.26061 | -0.760446 | -1.79473 | 126.192 | 33.958 | 1 |
| 6 | oxygen | O2 | g | -6.05147 | 1.23482 | -0.628118 | -1.61418 | 154.599 | 50.464 | 1 |
| 7 | hydrogen | H2 | g | -4.83684 | 0.943915 | 0.76388 | -0.467794 | 33.19 | 13.15 | 1 |
| 8 | sulfur dioxide | SO2 | g | -7.27802 | 1.72687 | -2.37193 | -2.70875 | 430.643 | 78.757 | 1 |
| 9 | carbon monoxide | CO | g | -6.19418 | 1.31964 | -0.943212 | -2.00155 | 132.86 | 34.982 | 1 |
| 10 | carbon dioxide | CO2 | g | -7.02656 | 1.52724 | -2.24631 | -2.63003 | 304.128 | 73.773 | 1 |
| 11 | methane | CH4 | g | -6.02406 | 1.26869 | -0.570278 | -1.37536 | 190.564 | 45.992 | 1 |
| 12 | ethane | C2H6 | g | -6.46128 | 1.35356 | -1.04336 | -2.04465 | 305.322 | 48.722 | 1 |
| 13 | propane | C3H8 | g | -6.71582 | 1.38704 | -1.31134 | -2.56317 | 369.825 | 42.477 | 1 |
| 14 | n-butane | C4H10 | g | -7.08437 | 1.7895 | -1.99474 | -2.32571 | 425.125 | 37.96 | 1 |
| 15 | isobutane | C4H10 | g | -6.90718 | 1.5787 | -1.80329 | -2.42719 | 407.81 | 36.29 | 1 |
| 16 | n-pentane | C5H12 | g | -7.36398 | 1.94324 | -2.47101 | -2.34914 | 469.659 | 33.689 | 1 |
| 17 | n-hexane | C6H14 | g | -7.61139 | 2.00719 | -2.7441 | -2.82541 | 507.795 | 30.416 | 1 |
| 18 | cyclohexane | C6H12 | g | -7.00995 | 1.57524 | -1.96889 | -3.26014 | 553.6 | 40.75 | 1 |
| 19 | n-heptane | C7H16 | g | -7.75446 | 1.84729 | -2.8025 | -3.62502 | 541.226 | 27.738 | 1 |
| 20 | n-octane | C8H18 | g | -8.01014 | 1.98473 | -3.25914 | -4.00358 | 569.57 | 25.067 | 1 |
| 21 | ethylene | C2H4 | g | -6.41245 | 1.45236 | -1.23907 | -1.99681 | 282.35 | 50.418 | 1 |
| 22 | propylene | C3H6 | g | -6.7214 | 1.51765 | -1.50887 | -2.36957 | 364.211 | 45.55 | 1 |
| 23 | 1-butene | C4H8 | g | -7.07828 | 1.87616 | -2.01994 | -2.65117 | 419.29 | 40.057 | 1 |
| 24 | methanol | CH3OH | g | -8.72698 | 1.45005 | -2.77177 | -0.723874 | 513.38 | 82.159 | 1 |
| 25 | ethanol | C2H5OH | g | -8.33802 | 0.087185 | -3.30578 | -0.259857 | 513.9 | 61.48 | 1 |
| 26 | n-propanol | C3H7OH | g | -8.60675 | 2.17363 | -8.04686 | 3.69177 | 536.75 | 51.75 | 1 |
| 27 | n-butanol | C4H9OH | g | -8.33086 | 2.05413 | -8.17566 | 0.190068 | 563.05 | 44.23 | 1 |
| 28 | ethylene glycol | C2H6O2 | g | -7.807 | 0.915488 | -4.92749 | -1.92613 | 719.15 | 82 | 1 |
| 29 | isopropanol | C3H7OH | g | -8.43986 | 1.14922 | -6.93839 | 0.615959 | 508.25 | 47.62 | 1 |
| 30 | acetic acid | CH3COOH | g | -9.34542 | 3.78498 | -3.60238 | -1.55306 | 591.95 | 57.86 | 1 |
| 31 | methyl acetate | C3H6O2 | g | -8.5747 | 4.22426 | -5.36811 | -0.827557 | 506.55 | 47.5 | 1 |
| 32 | ethyl acetate | C4H8O2 | g | -7.89719 | 2.16753 | -3.52331 | -3.10712 | 523.2 | 38.301 | 1 |
| 33 | vinyl acetate | C4H6O2 | g | -7.55444 | 1.36417 | -2.65681 | -2.99348 | 519.15 | 39.58 | 1 |
| 34 | methyl-tert-butyl ether | C5H12O | g | -7.5653 | 2.57784 | -3.91726 | -0.671678 | 497.15 | 34.3 | 1 |
| 35 | acetone | C3H6O | g | -7.67073 | 1.96592 | -2.44544 | -2.89987 | 508.1 | 46.924 | 1 |
| 36 | benzene | C6H6 | g | -7.11499 | 1.84141 | -2.25416 | -3.14745 | 562.014 | 49.01 | 1 |
| 37 | toluene | C6H5—CH3 | g | -7.49889 | 2.08428 | -2.55627 | -2.86014 | 591.749 | 41.263 | 1 |
| 38 | p-xylene | C8H10 | g | -7.67169 | 1.81288 | -2.38796 | -3.45669 | 616.25 | 35.11 | 1 |

**Number of records:** 38

## 5. Liquid Heat Capacity (`liquid-heat-capacity`)

**Property identifier:** `liquid-heat-capacity`  

**Property symbol:** `Cp_LIQ`  

**Table ID:** `4`

### Description

This table provides the liquid heat capacity at constant pressure (Cp_LIQ) in J/mol.K as a function of temperature (T) in K. The correlation follows Table A.5. Critical temperature (Tc) and molecular weight (MW) are taken from Table A.1. The source verification values in the book are reported in J/(g.K), while this implementation returns J/mol.K.

### Correlation or Data Definition


The liquid heat-capacity table uses a reduced-temperature expression.

```text
tau = 1 - T / Tc
Cp_LIQ = R * [ A/tau + B + C*tau + D*tau^2 + E*tau^3 + F*tau^4 ]
```


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'A', 'B', 'C', 'D', 'E', 'F', 'critical-temperature', 'molecular-weight', 'universal-gas-constant', 'Eq']`

**Symbol:** `['None', 'None', 'None', 'None', 'A', 'B', 'C', 'D', 'E', 'F', 'Tc', 'MW', 'R', 'Cp_LIQ']`

**Unit:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 1, 1, 'K', 'g/mol', 'J/mol.K', 'J/mol.K']`

### Complete Data Table: Liquid Heat Capacity

| No. | Name | Formula | State | A | B | C | D | E | F | critical-temperature | molecular-weight | universal-gas-constant | Eq |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | l | 0.25598 | 12.5459 | -31.409 | 97.7665 | -145.424 | 87.0185 | 647.096 | 18.015 | 8.314 | 1 |
| 2 | ammonia | NH3 | l | 0.51838 | 8.11168 | -3.92254 | 16.0808 | -18.0787 | -4.26508 | 405.5 | 17.031 | 8.314 | 1 |
| 3 | hydrogen chloride | HCl | l | 0.428824 | 7.22983 | -9.90842 | 35.9776 | -73.9664 | 63.002 | 324.55 | 36.461 | 8.314 | 1 |
| 4 | chlorine | Cl2 | l | 0.348448 | 9.58177 | -35.8234 | 198.971 | -456.44 | 365.477 | 416.958 | 70.906 | 8.314 | 1 |
| 5 | nitrogen | N2 | l | 0.468003 | 5.85912 | -3.29447 | 10.9494 | -10.9311 | 3.52105 | 126.192 | 28.014 | 8.314 | 1 |
| 6 | oxygen | O2 | l | 0.491044 | 4.97119 | 3.16582 | -15.7302 | 35.1294 | -24.4504 | 154.599 | 31.999 | 8.314 | 1 |
| 7 | hydrogen | H2 | l | 0.412752 | 1.9392 | -0.676502 | 2.16126 | -9.68404 | 14.4102 | 33.19 | 2.016 | 8.314 | 1 |
| 8 | sulfur dioxide | SO2 | l | 0.49203 | 9.88245 | -5.73671 | 12.9913 | -7.89841 | 4.25165 | 430.643 | 64.062 | 8.314 | 1 |
| 9 | carbon monoxide | CO | l | 0.434226 | 6.85227 | -7.82624 | 25.6936 | -39.2193 | 31.5063 | 132.86 | 28.01 | 8.314 | 1 |
| 10 | carbon dioxide | CO2 | l | 0.500361 | 8.83038 | -3.86884 | 10.3246 | 0.675891 | 1.84518 | 304.128 | 44.009 | 8.314 | 1 |
| 11 | methane | CH4 | l | 0.407112 | 7.06137 | -11.1425 | 37.8814 | -60.9459 | 38.0248 | 190.564 | 16.043 | 8.314 | 1 |
| 12 | ethane | C2H6 | l | 0.428053 | 10.459 | -18.1829 | 51.7115 | -75.8845 | 44.5005 | 305.322 | 30.07 | 8.314 | 1 |
| 13 | propane | C3H8 | l | 0.55868 | 12.8024 | -5.7382 | -9.55113 | 26.7025 | -15.7751 | 369.825 | 44.097 | 8.314 | 1 |
| 14 | n-butane | C4H10 | l | 0.494221 | 19.1953 | -11.6462 | -13.0636 | 37.5526 | -18.509 | 425.125 | 58.124 | 8.314 | 1 |
| 15 | isobutane | C4H10 | l | 0.49733 | 18.7737 | -14.5522 | -0.254646 | 19.359 | -15.8819 | 407.81 | 58.124 | 8.314 | 1 |
| 16 | n-pentane | C5H12 | l | 0.493157 | 25.4033 | -18.5711 | -8.45592 | 27.3831 | -5.18679 | 469.659 | 72.151 | 8.314 | 1 |
| 17 | n-hexane | C6H14 | l | 0.503827 | 30.6958 | -16.4378 | -28.1455 | 50.3127 | -18.0447 | 507.795 | 86.178 | 8.314 | 1 |
| 18 | cyclohexane | C6H12 | l | 0.452602 | 29.0405 | -17.2606 | -69.509 | 254.381 | -307.047 | 553.6 | 84.162 | 8.314 | 1 |
| 19 | n-heptane | C7H16 | l | 0.274131 | 39.6908 | -38.3276 | 48.5356 | -116.904 | 115.686 | 541.226 | 100.205 | 8.314 | 1 |
| 20 | n-octane | C8H18 | l | 0.615215 | 42.7536 | -27.3902 | 8.22851 | -58.6527 | 79.1162 | 569.57 | 114.231 | 8.314 | 1 |
| 21 | ethylene | CH2=CH2 | l | 0.475969 | 7.56509 | -3.3615 | -1.60201 | 24.5412 | -22.0721 | 282.35 | 28.054 | 8.314 | 1 |
| 22 | propylene | C3H6 | l | 0.468895 | 12.6776 | -12.484 | 18.3703 | -19.0064 | 15.1986 | 364.211 | 42.081 | 8.314 | 1 |
| 23 | 1-butene | C4H8 | l | 0.474628 | 17.4441 | -16.1444 | 18.5634 | -20.8209 | 16.6548 | 419.29 | 56.108 | 8.314 | 1 |
| 24 | methanol | CH3OH | l | 0.612632 | 13.1955 | -5.20887 | -45.7621 | 91.1903 | -44.4562 | 513.38 | 32.042 | 8.314 | 1 |
| 25 | ethanol | C2H5OH | l | 0.503568 | 22.442 | -36.7832 | 160.373 | -466.433 | 396.028 | 513.9 | 46.069 | 8.314 | 1 |
| 26 | n-propanol | C3H7OH | l | 0.313992 | 42.5981 | -78.4013 | 30.6122 | 40.1022 | -16.5885 | 536.75 | 60.096 | 8.314 | 1 |
| 27 | n-butanol | C4H9OH | l | 1.20398 | 50.5953 | -91.3315 | 37.8978 | 28.2251 | -2.35187 | 563.05 | 74.123 | 8.314 | 1 |
| 28 | ethylene glycol | C2H4(OH)2 | l | -0.106462 | 32.5477 | -27.0002 | 22.1667 | -43.2234 | 21.0741 | 719.15 | 62.068 | 8.314 | 1 |
| 29 | isopropanol | C3H7OH | l | -0.028011 | 37.2727 | -60.2129 | 145.142 | -415.612 | 383.532 | 508.25 | 60.096 | 8.314 | 1 |
| 30 | acetic acid | CH3COOH | l | 0.129079 | 23.2279 | -19.0351 | 11.1724 | -32.2097 | 32.2226 | 591.95 | 60.052 | 8.314 | 1 |
| 31 | methyl acetate | C3H6O2 | l | -3.27015 | 54.9489 | -110.92 | 73.0691 | 86.1528 | -91.368 | 506.55 | 74.079 | 8.314 | 1 |
| 32 | ethyl acetate | C4H8O2 | l | 1.55866 | 24.1895 | -26.451 | 27.6446 | -25.4934 | 29.857 | 523.2 | 88.106 | 8.314 | 1 |
| 33 | vinyl acetate | C4H6O2 | l | 0.532294 | 28.9201 | -26.3297 | 18.0664 | -41.7789 | 48.9985 | 519.15 | 86.09 | 8.314 | 1 |
| 34 | methyl-tert-butyl ether | C5H12O | l | 0.681223 | 28.6416 | -26.2761 | 26.9827 | -34.1771 | 22.9121 | 497.15 | 88.15 | 8.314 | 1 |
| 35 | acetone | C3H6O | l | 0.440183 | 17.6646 | -8.86636 | -11.7267 | 34.1924 | -17.4241 | 508.1 | 58.08 | 8.314 | 1 |
| 36 | benzene | C6H6 | l | 0.497842 | 22.3937 | -15.4079 | 3.39177 | -25.9485 | 39.5106 | 562.014 | 78.114 | 8.314 | 1 |
| 37 | toluene | C6H5—CH3 | l | 0.472576 | 28.7765 | -29.7602 | 48.7931 | -113.293 | 94.2047 | 591.749 | 92.141 | 8.314 | 1 |
| 38 | p-xylene | C8H10 | l | -0.298962 | 48.9714 | -144.539 | 451.28 | -811.387 | 551.297 | 616.25 | 106.168 | 8.314 | 1 |

**Number of records:** 38

## 6. Enthalpy of Vaporization (`enthalpy-of-vaporization`)

**Property identifier:** `enthalpy-of-vaporization`  

**Property symbol:** `EnVap`  

**Table ID:** `5`

### Description

This table provides the enthalpy of vaporization (EnVap) in J/mol as a function of temperature (T) in K.

### Correlation or Data Definition


The enthalpy-of-vaporization table uses a temperature-dependent latent-heat correlation.

```text
t = 1 - T/Tc
EnVap = R*Tc * [ A*t^(1/3) + B*t^(2/3) + C*t + D*t^2 + E*t^6 ]
```


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'A', 'B', 'C', 'D', 'E', 'critical-temperature', 'universal-gas-constant', 'Eq']`

**Symbol:** `['None', 'None', 'None', 'None', 'A', 'B', 'C', 'D', 'E', 'Tc', 'R', 'EnVap']`

**Unit:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 1, 'K', 'J/mol.K', 'J/mol']`

### Complete Data Table: Enthalpy of Vaporization

| No. | Name | Formula | State | A | B | C | D | E | critical-temperature | universal-gas-constant | Eq |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | l | 6.85306 | 7.43794 | -2.9374 | -3.28218 | 8.39683 | 647.096 | 8.314 | 1 |
| 2 | ammonia | NH3 | g | 5.74477 | 7.28288 | -2.42875 | -2.26192 | 2.90939 | 405.5 | 8.314 | 1 |
| 3 | hydrogen chloride | HCl | g | 5.38559 | 3.57761 | 1.70222 | -4.76908 | 5.09553 | 324.55 | 8.314 | 1 |
| 4 | chlorine | Cl2 | g | 5.11396 | 5.49479 | -1.63973 | -2.19362 | 4.35646 | 416.958 | 8.314 | 1 |
| 5 | nitrogen | N2 | g | 5.06317 | 5.51815 | -2.64591 | -1.98111 | 5.33337 | 126.192 | 8.314 | 1 |
| 6 | oxygen | O2 | g | 4.96962 | 5.30532 | -2.42609 | -2.15126 | 3.46629 | 154.599 | 8.314 | 1 |
| 7 | hydrogen | H2 | g | 4.11526 | 2.5116 | -1.53915 | -2.57867 | 2.16545 | 33.19 | 8.314 | 1 |
| 8 | sulfur dioxide | SO2 | g | 6.43138 | 6.40586 | -2.65602 | -0.900937 | 6.50221 | 430.643 | 8.314 | 1 |
| 9 | carbon monoxide | CO | g | 5.36516 | 4.61563 | -1.50262 | -2.36035 | 7.21458 | 132.86 | 8.314 | 1 |
| 10 | carbon dioxide | CO2 | g | 6.2859 | 5.64008 | -1.24063 | -2.04036 | 26.5421 | 304.128 | 8.314 | 1 |
| 11 | methane | CH4 | g | 4.99055 | 5.03515 | -2.28339 | -2.46093 | 4.37828 | 190.564 | 8.314 | 1 |
| 12 | ethane | C2H6 | g | 5.24057 | 7.19587 | -4.63536 | -0.641593 | 2.27141 | 305.322 | 8.314 | 1 |
| 13 | propane | C3H8 | g | 5.53222 | 7.86598 | -5.29834 | 0.075567 | 2.15482 | 369.825 | 8.314 | 1 |
| 14 | n-butane | C4H10 | g | 5.89459 | 7.87769 | -5.04188 | -0.151283 | 3.79078 | 425.125 | 8.314 | 1 |
| 15 | isobutane | C4H10 | g | 5.98536 | 6.87017 | -3.95794 | -0.356806 | 2.95743 | 407.81 | 8.314 | 1 |
| 16 | n-pentane | C5H12 | g | 5.75259 | 9.97315 | -6.8966 | 0.534831 | 4.46323 | 469.659 | 8.314 | 1 |
| 17 | n-hexane | C6H14 | g | 5.82345 | 11.2012 | -8.07144 | 1.34838 | 3.45694 | 507.795 | 8.314 | 1 |
| 18 | cyclohexane | C6H12 | g | 3.43791 | 14.0615 | -8.731 | 0.67173 | 0.025579 | 553.6 | 8.314 | 1 |
| 19 | n-heptane | C7H16 | g | 3.31664 | 21.9928 | -18.8082 | 5.53433 | 2.93102 | 541.226 | 8.314 | 1 |
| 20 | n-octane | C8H18 | g | 4.46423 | 19.7833 | -16.8393 | 5.36049 | 3.9566 | 569.57 | 8.314 | 1 |
| 21 | ethylene | C2H4 | g | 5.14375 | 6.93419 | -4.26883 | -0.58489 | 3.21393 | 282.35 | 8.314 | 1 |
| 22 | propylene | C3H6 | g | 5.29657 | 8.5397 | -6.05892 | 0.507597 | 2.79317 | 364.211 | 8.314 | 1 |
| 23 | 1-butene | C4H8 | g | 5.4955 | 9.24559 | -6.92009 | 1.44801 | 2.30729 | 419.29 | 8.314 | 1 |
| 24 | methanol | CH3OH | l | 5.46558 | 15.6168 | -7.67642 | -4.9266 | 6.33484 | 513.38 | 8.314 | 1 |
| 25 | ethanol | C2H5OH | l | 14.6876 | -15.2712 | 26.0623 | -20.0497 | 15.8165 | 513.9 | 8.314 | 1 |
| 26 | n-propanol | C3H7OH | l | 5.89007 | 16.2925 | -5.77791 | -2.76718 | -8.57552 | 536.75 | 8.314 | 1 |
| 27 | n-butanol | C4H9OH | l | 3.92523 | 18.802 | -5.34859 | -2.93775 | -0.181003 | 563.05 | 8.314 | 1 |
| 28 | ethylene glycol | C2H6O2 | l | 7.07917 | 8.72153 | 1.0135 | -5.21402 | 4.44181 | 719.15 | 8.314 | 1 |
| 29 | isopropanol | C3H7OH | l | 13.8465 | -16.6937 | 32.0984 | -19.9002 | -9.89451 | 508.25 | 8.314 | 1 |
| 30 | acetic acid | CH3COOH | l | 6.68664 | 15.0145 | -22.0866 | 3.0777 | 17.355 | 591.95 | 8.314 | 1 |
| 31 | methyl acetate | C3H6O2 | l | 6.39883 | 13.1255 | -12.78 | 5.8641 | -9.16871 | 506.55 | 8.314 | 1 |
| 32 | ethyl acetate | C4H8O2 | l | 8.5683 | 3.69158 | -0.614594 | -0.635779 | 0.817636 | 523.2 | 8.314 | 1 |
| 33 | vinyl acetate | C4H6O2 | l | 7.95908 | 5.92384 | -2.47345 | -1.44539 | 4.01331 | 519.15 | 8.314 | 1 |
| 34 | methyl-tert-butyl ether | C5H12O | l | 7.67713 | 3.102 | 0.388899 | -1.67283 | 0.763138 | 497.15 | 8.314 | 1 |
| 35 | acetone | C3H6O | l | 5.73175 | 9.17423 | -4.93422 | 0.048998 | 3.73567 | 508.1 | 8.314 | 1 |
| 36 | benzene | C6H6 | l | 5.00747 | 10.6908 | -7.31672 | 1.14071 | 6.78671 | 562.014 | 8.314 | 1 |
| 37 | toluene | C7H8 | l | 4.60779 | 13.9622 | -10.5791 | 2.11246 | 4.28486 | 591.749 | 8.314 | 1 |
| 38 | p-xylene | C8H10 | l | 8.70739 | 1.08184 | 2.57109 | -3.43502 | 9.40551 | 616.25 | 8.314 | 1 |

**Number of records:** 38

## 7. Liquid Density (`liquid-density`)

**Property identifier:** `liquid-density`  

**Property symbol:** `rho_LIQ`  

**Table ID:** `6`

### Description

This table provides liquid density (rho_LIQ) in kg/m3 as a function of temperature (T) in K. Most compounds use the Table A.3 coefficient form. Water is treated separately because Table A.3 refers to Eq. 3.52 instead of A, B, C, D coefficients. Critical temperature (Tc) is taken from Table A.1.

### Correlation or Data Definition


The liquid-density table uses a reduced-temperature density expression.

```text
tau = 1 - T / Tc
rho_LIQ = Dc + A*tau^0.35 + B*tau^(2/3) + C*tau + D*tau^(4/3)
```


### Table Structure

**Columns:** `['No.', 'Name', 'Formula', 'State', 'A', 'B', 'C', 'D', 'critical-temperature', 'critical-density', 'Eq']`

**Symbol:** `['None', 'None', 'None', 'None', 'A', 'B', 'C', 'D', 'Tc', 'Dc', 'rho_LIQ']`

**Unit:** `['None', 'None', 'None', 'None', 1, 1, 1, 1, 'K', 'kg/m3', 'kg/m3']`

### Complete Data Table: Liquid Density

| No. | Name | Formula | State | A | B | C | D | critical-temperature | critical-density | Eq |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | water | H2O | l | 0 | 0 | 0 | 0 | 647.096 | 322 | 1 |
| 2 | ammonia | NH3 | l | 533.086 | -39.199 | 271.407 | -72.5196 | 405.5 | 224.78 | 1 |
| 3 | hydrogen chloride | HCl | l | 981.876 | -441.481 | 1121.74 | -553.362 | 324.55 | 410.97 | 1 |
| 4 | chlorine | Cl2 | l | 908.902 | 948.048 | -1353.27 | 1093.53 | 416.958 | 576.81 | 1 |
| 5 | nitrogen | N2 | l | 471.217 | 492.865 | -561.597 | 391.145 | 126.192 | 313.3 | 1 |
| 6 | oxygen | O2 | l | 748.373 | 396.238 | -416.239 | 372.69 | 154.599 | 426.95 | 1 |
| 7 | hydrogen | H2 | l | 52.8201 | 2.712 | 6.2764 | -4.0288 | 33.19 | 30.12 | 1 |
| 8 | sulfur dioxide | SO2 | l | 1026.41 | 287.942 | -59.1833 | 242.718 | 430.643 | 524.72 | 1 |
| 9 | carbon monoxide | CO | l | 571.931 | -67.0962 | 387.15 | -121.732 | 132.86 | 304.17 | 1 |
| 10 | carbon dioxide | CO2 | l | 897.843 | 170.065 | 169.265 | 37.6341 | 304.128 | 467.6 | 1 |
| 11 | methane | CH4 | l | 267.859 | 129.396 | -73.607 | 69.9714 | 190.564 | 162.66 | 1 |
| 12 | ethane | C2H6 | l | 339.362 | 278.276 | -326.568 | 246.499 | 305.322 | 206.18 | 1 |
| 13 | propane | C3H8 | l | 372.181 | 329.311 | -439.72 | 331.682 | 369.825 | 220.48 | 1 |
| 14 | n-butane | C4H10 | l | 418.698 | 246.844 | -317.627 | 274.887 | 425.125 | 228 | 1 |
| 15 | isobutane | C4H10 | l | 383.578 | 363.764 | -483.814 | 353.496 | 407.81 | 225.5 | 1 |
| 16 | n-pentane | C5H12 | l | 331.173 | 680.899 | -965.202 | 602.369 | 469.659 | 235.2 | 1 |
| 17 | n-hexane | C6H14 | l | 537.415 | 87.8736 | -283.545 | 344.659 | 507.795 | 222.82 | 1 |
| 18 | cyclohexane | C6H12 | l | 370.943 | 865.342 | -1291.81 | 834.198 | 553.6 | 273.02 | 1 |
| 19 | n-heptane | C7H16 | l | 308.627 | 1070.99 | -1663.68 | 989.833 | 541.226 | 224.9 | 1 |
| 20 | n-octane | C8H18 | l | 314.933 | 1030.86 | -1576 | 939.745 | 569.57 | 227.63 | 1 |
| 21 | ethylene | CH2=CH2 | l | 364.883 | 208.842 | -198.15 | 185.26 | 282.35 | 214.24 | 1 |
| 22 | propylene | C3H6 | l | 428.385 | 156.208 | -176.313 | 217.351 | 364.211 | 229.64 | 1 |
| 23 | 1-butene | C4H8 | l | 374.901 | 532.737 | -823.236 | 585.658 | 419.29 | 237.95 | 1 |
| 24 | methanol | CH3OH | l | 164.743 | 2257.85 | -3545.83 | 1929.81 | 513.38 | 281.49 | 1 |
| 25 | ethanol | C2H5OH | l | 748.619 | -412.365 | 776.438 | -436.675 | 513.9 | 276 | 1 |
| 26 | n-propanol | C3H7OH | l | 816.271 | -549.21 | 696.984 | -232.082 | 536.75 | 274.42 | 1 |
| 27 | n-butanol | C4H9OH | l | 777.254 | -446.841 | 578.881 | -172.955 | 563.05 | 269.54 | 1 |
| 28 | ethylene glycol | C2H4(OH)2 | l | 1305.64 | -1374.32 | 1690.88 | -664.817 | 719.15 | 324.99 | 1 |
| 29 | isopropanol | C3H7OH | l | 865.918 | -744.095 | 975.903 | -381.128 | 508.25 | 273.15 | 1 |
| 30 | acetic acid | CH3COOH | l | 925.388 | -312.798 | 340.065 | 29.7201 | 591.95 | 334.22 | 1 |
| 31 | methyl acetate | C3H6O2 | l | 735.46 | -131.494 | 371.833 | -53.9224 | 506.55 | 324.89 | 1 |
| 32 | ethyl acetate | C4H8O2 | l | 660.375 | 8.8513 | 207.169 | 1.5101 | 523.2 | 308.07 | 1 |
| 33 | vinyl acetate | C4H6O2 | l | 752.038 | -204.466 | 468.804 | -107.555 | 519.15 | 318.88 | 1 |
| 34 | methyl-tert-butyl ether | C5H12O | l | 615.165 | -332.918 | 716.566 | -284.875 | 497.15 | 267.95 | 1 |
| 35 | acetone | C3H6O | l | 548.044 | 205.264 | -197.741 | 250.63 | 508.1 | 273.58 | 1 |
| 36 | benzene | C6H6 | l | 502.434 | 531.596 | -663.985 | 469.598 | 562.014 | 306.28 | 1 |
| 37 | toluene | C6H5—CH3 | l | 439.584 | 839.156 | -1234.84 | 797.874 | 591.749 | 292.12 | 1 |
| 38 | p-xylene | C8H10 | l | 660.661 | -279.799 | 602.986 | -192.824 | 616.25 | 280.9 | 1 |

**Number of records:** 38

## 8. Notes for Computational Use

- Temperature arguments are expressed as `temperature | T | K`.

- Equation parameters are read using symbolic names such as `A`, `B`, `Tc`, `Pc`, `R`, and `Dc`.

- The equation body uses Python-compatible mathematical operations through the `math` package.

- All records are grouped by property name, so a parser can select the required property table and then retrieve compound-specific parameters.

- This structure is compatible with model-source construction, where `data_source` stores general data and `equation_source` stores callable property equations.

## 9. Conclusion

The chapter presents a complete machine-readable thermodynamic reference. Each property is represented by its own table, with units, symbols, equation definitions, and all compound records explicitly included. This structure supports reproducible thermodynamic modeling, consistent data parsing, and integration with MCP-enabled process-modeling workflows.
