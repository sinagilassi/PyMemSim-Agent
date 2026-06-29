# 📘 Hollow Fiber Membrane (HFM) Input Specification — Case 3 (Air Separation)

## 🔷 1. Module (Contactor) Configuration

### General

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Flow type | - | Co-current & Counter-current | - |
| Number of fibers | N | 368 | - |

---

### Geometry

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Outer diameter | OD | 160e-6 | m |
| Inner diameter | ID | 80e-6 | m |
| Fiber length | L | 0.25 | m |
| Shell diameter | SD | 0.0095 | m |

---

### Structural Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Packing fraction | ϕ | 0.1044 | - |
| Porosity | ε | 0.8956 | - |

---

### Derived / Calculated Properties

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Total membrane area | A | 0.0462 | m² |
| Module volume | V | 1.772e-5 | m³ |
| Area per unit length | aₘ = dA/dz | ~1850 | m²/m³ |

> ⚠️ Note: Verify definition of aₘ in your model
> - If using A/L → different value
> - If using A/V → ≈ 2607 m²/m³

---

## 🔷 2. Feed Specification

| Component | Mole Fraction (-) |
|----------|------------------|
| O₂ | 0.205 |
| N₂ | 0.795 |

---

## 🔷 3. Physical Properties (at NTP)

| Property | O₂ | N₂ | Unit |
|----------|-----|-----|------|
| Molecular weight | 32 | 28 | g/mol |
| Density | 1.331 | 1.165 | kg/m³ |
| Viscosity | 2.04e-5 | 1.76e-5 | Pa·s |

---

## 🔷 4. Membrane Transport Properties

### Permeance

| Component | GPU | Permeance | Unit |
|----------|-----|-----------|------|
| O₂ | 9.30 | 6.98e-9 | mol/(m²·s·Pa) |
| N₂ | 1.80 | 1.35e-9 | mol/(m²·s·Pa) |

---

### Selectivity

| Definition | Value |
|-----------|------|
| α (O₂/N₂) | 5.17 |

---

## 🔷 5. Feed Operating Conditions

| Parameter | Symbol | Value | Unit |
|----------|--------|------|------|
| Feed temperature | T | 296.00 | K |
| Feed pressure | P_f | 690000 | Pa |
| Permeate pressure | P_p | 100000 | Pa |
