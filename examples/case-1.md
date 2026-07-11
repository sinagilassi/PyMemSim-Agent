# 📘 Hollow Fiber Membrane (HFM) Input Specification - Case 1

## 🔷 1. Module (Contactor) Configuration

### General

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Flow type | - | Co-current | - |
| Number of fibers | N | 100 | - |

---

### Geometry

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Outer diameter | OD | 735e-6 | m |
| Inner diameter | ID | 389e-6 | m |
| Fiber length | L | 0.15 | m |
| Shell diameter | SD | 0.01 | m |

---

### Structural Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Packing fraction | ϕ | 0.540 | - |
| Porosity | ε | 0.460 | - |

---

### Derived / Calculated Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Total membrane area | A | 0.0346 | m² |
| Module volume | V | 1.178e-5 | m³ |
| Area per unit length | aₘ = dA/dz | 2309 | m²/m³ |

---

## 🔷 2. Feed Specification

| Component | Mole Fraction (-) |
|----------|------------------|
| CO₂ | 0.60 |
| CH₄ | 0.40 |

- Feed inlet molar flow rates from validation data:
  - case-1-1 at 298.15 K: 0.0025, 0.0015, 0.001, 0.0001, 6e-05, 4e-05, 3e-05 mol/s
  - case-1-2 at 338.15 K: 0.0025, 0.0015, 0.00014, 0.00013, 0.00011, 0.0001, 9e-05, 7e-05 mol/s

---

## 🔷 3. Physical Properties (at NTP)

| Property | CO₂ | CH₄ | Unit |
|----------|-----|-----|------|
| Molecular weight | 44 | 16 | g/mol |
| Density | 1.84 | 0.688 | kg/m³ |
| Viscosity | 1.47e-5 | 1.10e-5 | Pa·s |

---

## 🔷 4. Membrane Transport Properties

### Permeance

| Temperature (K) | CO₂ (GPU) | CH₄ (GPU) |
|-----------------|-----------|-----------|
| 298.15 | 9.43 | 2.63 |
| 338.15 | 17.98 | 6.21 |

---

### Selectivity

| Definition | Value |
|-----------|------|
| α (CO₂/CH₄) | 3.59 |

## 🔷 Feed Operating Conditions

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Feed temperature | T | 298.15 & 338.15 | K |
| Feed pressure | P_f | 405300 | Pa |
| Permeate pressure | P_p | 101300 | Pa |

## 🔷 Experimental results

### Experimental data at 65 °C

| Stage cut (%) | CO₂ mole fraction in permeate, y |
|---:|---:|
| 3.064516 | 0.800423 |
| 6.451613 | 0.798225 |
| 19.35484 | 0.788125 |
| 39.35484 | 0.761837 |

### Experimental data at 25 °C

| Stage cut (%) | CO₂ mole fraction in permeate, y |
|---:|---:|
| 2.251606 | 0.768977 |
| 7.008798 | 0.761349 |
| 13.58751 | 0.761204 |
| 38.71977 | 0.741621 |

## References

1. Tranchino, L., Santarossa, R., Carta, F., Fabiani, C. and Bimbi, L., 1989. Gas separation in a membrane unit: experimental results and theoretical predictions. Separation Science and Technology, 24(14), pp.1207-1226.