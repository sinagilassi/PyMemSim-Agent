# 📘 Hollow Fiber Membrane (HFM) Input Specification — Case 2

## 🔷 1. Module (Contactor) Configuration

### General

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Flow type | - | Counter-current | - |
| Number of fibers | N | 270 | - |

---

### Geometry

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Outer diameter | OD | 156e-6 | m |
| Inner diameter | ID | 63e-6 | m |
| Fiber length | L | 0.26 | m |
| Shell diameter | SD | 0.005 | m |

---

### Structural Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Packing fraction | ϕ | 0.2628 | - |
| Porosity | ε | 0.7372 | - |

---

### Derived / Calculated Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Total membrane area | A | 0.0344 | m² |
| Module volume | V | 5.11e-6 | m³ |
| Area per unit length | aₘ = dA/dz | ~1323 | m²/m³ |

> Note:
> aₘ calculated from:
> A / V = 0.0344 / 5.11e-6 ≈ 6730 m²/m³ (if volume-based)
> OR from Af/L → depends on your definition in code ⚠️
> (You should confirm which definition you use in PyMemSim)

---

## 🔷 2. Feed Specification

| Component | Mole Fraction (-) |
|----------|------------------|
| CO₂ | 0.50 |
| O₂ | 0.105 |
| N₂ | 0.395 |

---

## 🔷 3. Physical Properties (at NTP)

| Property | CO₂ | O₂ | N₂ | Unit |
|----------|-----|-----|-----|------|
| Molecular weight | 44 | 32 | 28 | g/mol |
| Density | 1.842 | 1.331 | 1.165 | kg/m³ |
| Viscosity | 1.47e-5 | 2.04e-5 | 1.76e-5 | Pa·s |

---

## 🔷 4. Membrane Transport Properties

### Permeance

| Component | GPU |
|----------|-----|
| CO₂ | 61.0 |
| O₂ | 18.0 |
| N₂ | 3.9 |

---

### Selectivity

| Definition | Value |
|-----------|------|
| α (CO₂/O₂) | 3.39 |
| α (CO₂/N₂) | 15.59 |

## 🔷 8. Feed Operating Conditions

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Feed temperature | T | 303.15 | K |
| Feed pressure | P_f | 1570000 | Pa |
| Permeate pressure | P_p | 101300 | Pa |

## 🔷 Experimental results

### Experimental data

| Stage cut (%) | CO₂ mole fraction in permeate, y |
|---:|---:|
| 15.55896 | 0.875103 |
| 32.86546 | 0.852057 |
| 43.77643 | 0.827766 |
| 56.86607 | 0.787357 |
| 69.16579 | 0.714788 |
| 80.05794 | 0.630175 |

## References

1. Rautenbach, R., Knauf, R., Struck, A. and Vier, J., 1996. Simulation and design of membrane plants with AspenPlus. Chemical Engineering & Technology: Industrial Chemistry‐Plant Equipment‐Process Engineering‐Biotechnology, 19(5), pp.391-397.