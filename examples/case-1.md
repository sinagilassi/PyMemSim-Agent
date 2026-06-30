# 📘 Hollow Fiber Membrane (HFM) Input Specification

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

| Component | GPU | Permeance | Unit |
|----------|-----|-----------|------|
| CO₂ | 31.60 | 2.37e-8 | mol/(m²·s·Pa) |
| CH₄ | 8.81 | 6.61e-9 | mol/(m²·s·Pa) |

---

### Selectivity

| Definition | Value |
|-----------|------|
| α (CO₂/CH₄) | 3.59 |

## 🔷 Feed Operating Conditions

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Feed temperature | T | 298.15~338.15 | K |
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