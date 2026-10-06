# Chapter 3: Dielectric Stack Chemistry — Si/SiO₂/SiN Interactions in Plasma

## Executive Summary

The gate line slit etch process traverses a multi-layer dielectric stack: silicon (Si), silicon dioxide (SiO₂), and silicon nitride (Si₃N₄). Each material has distinct plasma chemistry, thermal properties, and interaction mechanisms with etch radicals and ions. This chapter establishes the material science foundation for gate line slit etch, addressing: *How do radicals interact with Si, SiO₂, and SiN differently?* *What are the etch rate mechanisms for each material?* *How do thermal properties affect process control?* Understanding this chemistry is prerequisite to selectivity control (Chapter 12) and damage prevention (Chapter 4).

---

## Part 1: Silicon (Si) Chemistry

### 1.1 Silicon Structure and Properties

**Silicon crystal structure:**
- Element: Group IVA, atomic number 14
- Electron configuration: [Ne] 3s² 3p²
- Valence: 4 (forms 4 covalent bonds)
- Crystallography: Diamond cubic structure (FCC-like)
- Density: 2.33 g/cm³ at room temperature
- Melting point: 1414°C (1687 K)

**Thermal properties:**

| Property | Value | Significance |
|---|---|---|
| Thermal conductivity (300K) | 149 W/m·K | Moderate heat transport; not self-cooling at high power |
| Thermal expansion | 2.6 ppm/K | Low; minimal CTE mismatch with SiO₂ |
| Specific heat | 712 J/kg·K | Moderate heat capacity |

### 1.2 Etch Mechanisms for Silicon

Silicon etches via two main mechanisms:

#### Mechanism 1: Fluorine-Based Etch

Fluorine radicals (F) attack silicon, breaking Si-Si bonds:

$$\text{Si} + 2\text{F} \rightarrow \text{SiF}_2 $$
$$\text{SiF}_2 + 2\text{F} \rightarrow \text{SiF}_4 $$

**SiF₄ is gaseous** (volatilizes immediately), removing Si from the surface.

**Rate law:**
$$R_{\text{Si}} = k_F \cdot [F] \cdot [Si surface sites]$$

Etch rate typically: **500-2000 nm/min** (very fast)

#### Mechanism 2: Chlorine-Based Etch

Chlorine radicals (Cl) attack silicon:

$$\text{Si} + 2\text{Cl} \rightarrow \text{SiCl}_2 $$
$$\text{SiCl}_2 + \text{Cl} \rightarrow \text{SiCl}_3 \text{ or } \text{SiCl}_4$$

**SiCl₄ is volatile**, though SiCl₃ and SiCl₂ are quasi-volatile (can re-deposit in cool regions).

**Rate law:**
$$R_{\text{Si}} = k_{\text{Cl}} \cdot [Cl] \cdot E_{\text{ion}}^{0.5}$$

Etch rate typically: **300-1000 nm/min** (moderate to fast, ion-dependent)

### 1.3 Silicon Surface Oxidation

In plasma containing oxygen or water vapor, Si quickly oxidizes:

$$\text{Si} + \text{O}_2 \rightarrow \text{SiO}_2$$

**Native oxide formation:**
- Timescale: Seconds in air at room temperature
- Thickness: 1-3 nm (equilibrium)
- Thermal oxide (500°C+): 10-100nm per oxidation step

**Consequence for gate line slit etch:**
- Fresh Si surface rapidly oxidizes unless etch chemistry is very reactive
- Oxidation on sidewalls can form diffusion barriers, reducing etch rate
- Polymer deposition from etch byproducts competes with oxidation

---

## Part 2: Silicon Dioxide (SiO₂) Chemistry

### 2.1 SiO₂ Structure and Properties

**Silicon dioxide:**
- Empirical formula: SiO₂
- Structure: SiO₄ tetrahedra linked by bridging oxygen
- Density: 2.20-2.27 g/cm³ (depends on deposition method)
- Melting point: 1710°C (no true melting; transforms to viscous liquid)

**Key property: Thermal stability**
- Decomposition temperature: > 2000°C (extremely stable)
- Thermal expansion: 0.5 ppm/K (very low)
- No semiconductor properties (insulator, E_g ~ 9 eV)

### 2.2 Etch Mechanisms for SiO₂

Unlike Si, SiO₂ does not etch in fluorine or chlorine alone. It requires:

#### Mechanism 1: Fluorine Etch with Promoters

Pure F radicals attack SiO₂ very slowly:
$$\text{SiO}_2 + 4\text{F} \rightarrow \text{SiF}_4 + \text{O}_2$$

But in Cl + F mixtures, **Cl atoms promote SiO₂ etch:**

$$\text{SiO}_2 + \text{Cl} + \text{F} \rightarrow \text{SiCl}_x\text{F}_y + \text{volatile products}$$

**Rate law:**
$$R_{\text{SiO}_2} = k_F \cdot [F] \cdot [Cl] + k_{\text{ion}} \cdot E_{\text{ion}}$$

Etch rate typically: **100-500 nm/min** (slower than Si)

#### Mechanism 2: Ion-Assisted Oxide Etch

In low-radical, high-ion environments, ions break Si-O bonds:

$$\text{SiO}_2 + \text{Ion} \rightarrow \text{SiO}_x + \text{volatile O compounds}$$

**Rate law:**
$$R_{\text{SiO}_2, \text{ion}} \propto \Phi_{\text{ions}} \cdot E_{\text{ion}}$$

Etch rate typically: **50-200 nm/min** (moderate, ion-flux-limited)

### 2.3 Selectivity of Si to SiO₂

The selectivity (Si etch rate / SiO₂ etch rate) is crucial for gate line slit etch:

**In F-based plasma:**
- Si etch rate: 1000-2000 nm/min (very fast)
- SiO₂ etch rate: 100-300 nm/min (slow)
- **Selectivity: 5-10:1** (Si etch much faster)

**In Cl-based plasma:**
- Si etch rate: 300-800 nm/min
- SiO₂ etch rate: 50-150 nm/min
- **Selectivity: 3-5:1** (less selective than F)

**Implication for gate line slit etch:**
- Fluorine-based processes (CF₄, CHF₃) have better Si/SiO₂ selectivity
- Better selectivity → tighter process window, easier to stop on oxide layers

---

## Part 3: Silicon Nitride (Si₃N₄) Chemistry

### 3.1 Si₃N₄ Structure and Properties

**Silicon nitride:**
- Empirical formula: Si₃N₄
- Structure: SiN₄ tetrahedra linked by N-Si bonds
- Crystallography: α-Si₃N₄ (hexagonal, stable) and β-Si₃N₄ (cubic, less stable)
- Density: 3.18-3.24 g/cm³ (higher than SiO₂)
- Melting point: 1900°C (extremely high)

**Mechanical properties:**
- Hardness: 8-9 Mohs (harder than SiO₂)
- Young's modulus: 310 GPa (stiffer than SiO₂: 70 GPa)
- Fracture toughness: 6-8 MPa√m (better than SiO₂: 1 MPa√m)

**Dielectric properties:**
- Permittivity: 7-8 (higher than SiO₂: 3.9)
- Refractive index: 1.9-2.0 (higher than SiO₂: 1.46)

### 3.2 Etch Mechanisms for Si₃N₄

Nitride etch chemistry differs from oxide:

#### Mechanism 1: Fluorine Etch

F radicals attack Si-N bonds:
$$\text{Si}_3\text{N}_4 + 12\text{F} \rightarrow 3\text{SiF}_4 + 4\text{NF}_3$$

Both SiF₄ and NF₃ are volatile.

**Rate law:**
$$R_{\text{Si}_3\text{N}_4} = k_F \cdot [F] \cdot [N atoms] + k_{\text{ion}} \cdot E_{\text{ion}}$$

Etch rate typically: **200-600 nm/min** (faster than SiO₂, slower than Si)

#### Mechanism 2: Chlorine Etch

Cl radicals attack Si₃N₄:
$$\text{Si}_3\text{N}_4 + \text{Cl} \rightarrow \text{SiCl}_x + \text{NCl}_y \text{ or } \text{N}_2$$

**Rate law:**
$$R_{\text{Si}_3\text{N}_4} = k_{\text{Cl}} \cdot [Cl] \cdot E_{\text{ion}}^{0.5}$$

Etch rate typically: **100-400 nm/min** (moderate, more ion-dependent)

### 3.3 Selectivity of Nitride to Oxide

For gate line slit etch, we often need **SiN/SiO₂ selectivity:**

**In F-based plasma:**
- SiN etch rate: 200-400 nm/min
- SiO₂ etch rate: 100-300 nm/min
- **Selectivity: 1.5-2.0:1** (SiN etch faster, but not dramatically)

**In Cl-based plasma:**
- SiN etch rate: 150-350 nm/min
- SiO₂ etch rate: 50-150 nm/min
- **Selectivity: 2-3:1** (better than F-based for this pair)

**Implication:**
- For SiN/SiO₂ selectivity, Cl-based processes may be preferred
- For Si/SiO₂ selectivity, F-based processes are preferred
- Achieving both simultaneously is difficult; requires recipe compromise

---

## Part 4: Multi-Layer Selectivity Requirements

### 4.1 Selective Etch Sequence for Gate Line Slit

The gate line slit must navigate a specific sequence:

```
Step 1: Etch SiO₂ (top oxide)
        Need: SiO₂-selective chemistry
        Stop on: Poly gate

Step 2: Etch Poly (Si)
        Need: Si-selective (over SiO₂)
        Stop on: Gate oxide

Step 3: Etch SiO₂ (gate oxide) [CRITICAL]
        Need: Precise timing (only 3-5 nm)
        Stop on: SiN barrier

Step 4: Etch Si₃N₄ (barrier)
        Need: SiN-selective chemistry
        Stop on: SiO₂ (isolation oxide)

Step 5: Stop (reach isolation oxide)
```

Each step requires different selectivity:

| Step | Etch Material | Over Material | Required Selectivity |
|---|---|---|---|
| 1 | SiO₂ | Air/photoresist | Any (no competing material) |
| 2 | Si (poly) | SiO₂ | 3-5:1 (Si faster) |
| 3 | SiO₂ | Si₃N₄ (below) | 0.2-0.5:1 (oxide SLOWER) |
| 4 | Si₃N₄ | SiO₂ | 1.5-3:1 (SiN faster) |

### 4.2 Contradictory Selectivity Requirements

Notice the conflict in Step 2 vs. Step 3:
- **Step 2:** Want Si/SiO₂ selectivity of 3-5:1 (Si etch faster)
- **Step 3:** Want SiO₂/SiN selectivity of 0.2-0.5:1 (SiO₂ etch SLOWER)

**No single gas chemistry optimizes both.**

**Solution:** Use **two different recipes:**

```
Recipe A (for Step 2):
  - High F concentration (CHF₃, CF₄)
  - Moderate Cl concentration
  - Medium power, low pressure
  - Promotes Si/SiO₂ selectivity (~4:1)

Recipe B (for Step 3):
  - Moderate F concentration
  - Increased Cl concentration
  - Lower power, higher pressure
  - Reduces etch rate on oxide (lower selectivity for oxide)
```

This **multi-step process** is typical for advanced gate line slit etch recipes.

---

## Part 5: Thermal Effects on Chemistry

### 5.1 Temperature Dependence of Etch Rate

All etch reactions follow Arrhenius behavior:

$$R(T) = R_0 \cdot \exp\left(-\frac{E_a}{k_B T}\right)$$

where:
- **E_a:** Activation energy (typically 10-50 kJ/mol for plasma etch)
- **k_B:** Boltzmann constant
- **T:** Temperature (K)

**Consequence:** Etch rate increases exponentially with temperature.

#### Example Calculation

For Si etch with E_a = 20 kJ/mol:

| Temperature | Relative Etch Rate |
|---|---|
| 0°C (273 K) | 1.0 |
| 50°C (323 K) | 2.0 |
| 100°C (373 K) | 4.0 |

A 100°C temperature rise increases etch rate by 4×.

### 5.2 Temperature Variations in Gate Line Slits

In deep trenches, temperature is non-uniform:

```
Temperature Profile in Deep Slit

Temp (°C)
    │
100 ├────┐
    │    │  (top: plasma heating)
 70 ├────┼──────┐
    │    │      │  (middle: moderate)
 40 │    │      ├─────────
    │    │      │         (bottom: cooler, poor ion/photon reach)
 10 └────┴──────┴─────────
    0    10    20    30 (depth, µm)
```

**Temperature differences of 30-50°C across the trench** are common, creating etch rate variations of 2-3×.

**Consequence:**
- Top of slit etches faster than bottom (due to temperature gradient)
- Compounds ARDE effects discussed in Chapter 10
- Requires active temperature management (cooled chuck) to stabilize

---

## Summary

The gate line slit etch chemistry must accommodate three different materials (Si, SiO₂, Si₃N₄) with different etch rates and selectivity requirements. Key takeaways:

1. **Fluorine-based etch** (CF₄, CHF₃):
   - Excellent Si/SiO₂ selectivity (5-10:1)
   - Weaker SiN/SiO₂ selectivity (1.5-2:1)
   - Preferred for steps with Si present

2. **Chlorine-based etch** (Cl₂, HCl, CCl₄):
   - Moderate Si/SiO₂ selectivity (3-5:1)
   - Better SiN/SiO₂ selectivity (2-3:1)
   - Preferred for nitride layers

3. **Multi-step recipes** necessary because no single chemistry optimizes all selectivity transitions

4. **Temperature control critical:** Etch rate exponential dependence on T requires ±5-10°C control to maintain within-trench uniformity

Next chapters address how plasma engineering (electrode design, gas distribution, RF power) translates these chemical mechanisms into production-scale processes.

---

**Next:** [Chapter 4: Plasma-Induced Damage and Gate Oxide Effects](04-plasma-induced-damage.md)
