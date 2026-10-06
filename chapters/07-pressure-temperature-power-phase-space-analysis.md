# Chapter 7: Pressure-Temperature-Power Phase Space Analysis

## Executive Summary

Gate line slit etch is fundamentally constrained by three competing objectives: **maximize etch rate, minimize damage (Chapter 4), minimize ARDE (Chapter 10)**. These objectives are coupled through three primary process parameters: **pressure (P), temperature (T), and RF power (W)**. This chapter develops the **process window**—the multi-dimensional region of (P, T, W) space where specifications are met. We address: *How do P, T, W interact?* *What are the physical coupling mechanisms?* *How do we map the process window experimentally?* *What trade-offs constrain optimization?* Understanding parameter interactions is essential for recipe development (Chapter 18) and real-time process control strategies.

---

## Part 1: Parameter Interactions and Physical Coupling

### 1.1 Three Process Parameters and Their Effects

**Pressure (P, in Pa):**
- **Controls:** Mean free path of ions/radicals, plasma density, radical penetration
- **High P:** Higher density, faster bulk reactions, poor deep penetration
- **Low P:** Lower density, slower etch, better deep penetration
- **Typical range:** 5-100 Pa (gate line slit: 10-30 Pa)

**Temperature (T, in K or °C):**
- **Controls:** Molecular diffusion, reaction rate constants, radical lifetime, TDDB
- **High T:** Faster reactions (exponential), shorter radical lifetime, increased damage
- **Low T:** Slower reactions, longer radical lifetime, reduced damage
- **Typical range:** 273K to 373K (-10°C to +100°C for gate line slit)

**Power (W, in Watts):**
- **Controls:** Plasma generation rate, ion energy, electron temperature, radical production
- **High W:** More ions, higher energies, more radicals, more damage risk
- **Low W:** Slower etch, better damage control
- **Typical range:** 500-2000 W (dependent on chamber size)

### 1.2 Coupling Mechanism 1: Pressure and Ion Energy

Sheath voltage (and thus ion energy) depends on plasma density:

$$V_{\text{sheath}} = V_{\text{RF}} \times \frac{n_e}{n_e + n_i}$$

Plasma density increases with pressure, so:

```
Pressure (Pa) | Plasma Density | Sheath Voltage | Ion Energy (eV) |
--------------|--------------|--------------|--------------------|
5             | Low (10^9)    | High (300V)    | 300               |
20            | Medium (10^10)| Medium (150V)  | 150               |
50            | High (10^11)  | Low (50V)      | 50                |
100           | Very High     | Very Low (20V) | 20                |
```

**Physical principle:** At higher pressure, more free electrons exist, creating a more conductive plasma that requires lower sheath voltage to sustain.

**Consequence:** Higher pressure → lower ion energy → reduced damage, but also reduced ion-assisted etch.

### 1.3 Coupling Mechanism 2: Power and Plasma Density

RF power input directly controls plasma generation:

$$P_{\text{input}} = n_e \times V_{\text{sheath}} \times \Phi_{\text{ions}} \times e + \text{heating losses}$$

Simplified scaling:
$$n_e \propto \sqrt{P}$$

**Result:**

| Power (W) | Plasma Density | Etch Rate | Damage Risk |
|-----------|----------------|-----------|-------------|
| 500       | Baseline       | Baseline  | Baseline    |
| 1000      | 1.4×           | 1.5-2×    | Higher      |
| 1500      | 1.7×           | 2-3×      | Much higher |
| 2000      | 2×             | 3-4×      | Severe      |

**Consequence:** Power increase is the most direct way to increase etch rate, but it also increases damage—a fundamental trade-off.

### 1.4 Coupling Mechanism 3: Temperature and Etch Rate

Etch rate has Arrhenius temperature dependence:

$$R(T) = R_0 \exp\left(-\frac{E_a}{k_B T}\right)$$

For typical gate line slit etch (E_a ~ 20 kJ/mol):

```
Temperature | Relative Etch Rate | Relative TDDB Damage |
-----------|--------------------|---------------------|
0°C        | 1.0                | 1.0 (fresh oxide)    |
25°C       | 1.5                | 1.2 (minimal)        |
50°C       | 2.2                | 2.0 (moderate)       |
75°C       | 3.3                | 4.5 (increased)      |
100°C      | 5.0                | 10+ (severe)         |
```

**Consequence:** Temperature increase accelerates etch **and** damage degradation. Cannot independently decouple etch rate from damage via temperature alone.

---

## Part 2: Process Window Mapping

### 2.1 Defining the Process Window

The **process window** is the region of (P, T, W) space satisfying all specifications:

**Specifications (typical):**
1. **Etch rate:** 200-400 nm/min (target within ±20%)
2. **ARDE factor:** < 2.5:1 (depth uniformity)
3. **Selectivity Si/SiO₂:** 3-5:1 (timing precision)
4. **Damage level:** < 10⁴ defects/cm² (oxide integrity)
5. **Wafer uniformity:** ±10% center-to-edge

All five constraints must be satisfied **simultaneously** for a process point to be acceptable.

### 2.2 Simplified 2D Process Window (Pressure vs. Power)

For fixed temperature (e.g., 70°C), we can visualize:

```
Power (W)
  2000 │
       │
  1500 │  ░░░░░░  Etch rate too fast
       │  ░  ┌───────┐  
  1000 │  ░  │ PASS  │  ░░░░░░░  Power-limited
       │  ░  │   (✓) │  ░
   500 │  ░  └───────┘  ░░░░░░░░
       │  ░                ░
     0 └─────────────────────────
       0   10   20   30   40   50
           Pressure (Pa)

PASS Zone: Power 800-1400W, Pressure 15-35 Pa

Low pressure → ARDE too high, radical starvation
High pressure → Etch rate too slow, process takes too long
Low power → Etch rate insufficient, ion-assisted etch weak
High power → Damage too severe, oxide breakdown risk
```

### 2.3 3D Phase Space Visualization

In 3D (P, T, W), the process window is a **complex polyhedron** (not a simple box):

```
Process Window Constraints (3D)

Pressure
    ↑
    │
    ├─ Lower limit: ARDE constraint (P too low → poor penetration)
    │
    ├─ Upper limit: Etch rate constraint (P too high → slow)
    │
    └─ Temperature and Power interact with both

Temperature
    ↑
    │
    ├─ Lower limit: Etch rate constraint (T too low → slow)
    │
    ├─ Upper limit: Damage constraint (T too high → TDDB)
    │
    └─ Pressure and Power interact with both

Power
    ↑
    │
    ├─ Lower limit: Etch rate constraint (W too low → insufficient)
    │
    ├─ Upper limit: Damage constraint (W too high → charging, oxide rupture)
    │
    └─ Pressure and Temperature interact with both
```

### 2.4 Experimental Process Window Mapping

**Method 1: Design of Experiments (DOE)**

Systematically vary parameters at discrete levels:

| Parameter | Low | Medium | High |
|-----------|-----|--------|------|
| Pressure | 10 Pa | 20 Pa | 40 Pa |
| Temperature | 40°C | 70°C | 100°C |
| Power | 800W | 1200W | 1600W |

Total combinations: 3³ = 27 experiments per wafer or test series.

**Measurement at each point:**
- Etch depth (SEM cross-section)
- Etch rate uniformity (multiple sites per wafer)
- ARDE factor (measure top vs. bottom rates separately)
- Selectivity (measure oxide/nitride thicknesses)
- Damage level (post-etch electrical testing)

**Analysis:** Plot each measurement as function of (P, T, W). Identify regions satisfying all specs.

**Method 2: Central Composite Design (CCD)**

More efficient than full factorial:
- 8 corner points (2³)
- 6 face-center points (one at ±1 std on each axis at center of others)
- 1 center point
- Total: 15 experiments per design space

**Advantage:** Identifies nonlinear interactions with fewer experiments.

### 2.5 Process Window Shape and Robustness

Real process windows are **not rectangular**—they have complex shapes due to:

1. **ARDE constraint:** As pressure increases, ARDE decreases, widening the P window
2. **Damage constraint:** As temperature increases, damage increases, narrowing the T window
3. **Etch rate constraint:** As power increases, etch rate increases, but plateau at high P

**Robustness of process window:**

```
Robust Window (Wide):
   ┌──────────────────────┐
   │   (✓) Process        │  Can tolerate ±10% parameter drift
   │       Window         │  Forgiving of equipment variation
   └──────────────────────┘

Fragile Window (Narrow):
   ┌─────┐
   │ (✓) │  Must maintain ±3% parameter precision
   └─────┘  Sensitive to equipment drift, wafer-to-wafer variation
```

**Optimal process window design:** Balance width (robustness) with location (specifications). Too narrow → yield loss from parameter excursions; too wide → specifications barely met.

---

## Part 3: Etch Rate Prediction Models

### 3.1 Semi-Empirical Etch Rate Model

Etch rate depends on all three parameters:

$$R(P, T, W) = R_0 \times f(P) \times g(T) \times h(W)$$

**Pressure dependence** f(P):
- Low P: Limited radical/ion flux → f(P) ∝ P^α (α ~ 0.5-1)
- Moderate P: Optimal regime → nearly linear
- High P: Radical depletion → f(P) saturates

**Temperature dependence** g(T):
$$g(T) = \exp\left(-\frac{E_a}{k_B T}\right)$$

Typical: E_a ~ 15-25 kJ/mol

**Power dependence** h(W):
- Low W: Ion-generation limited → h(W) ∝ W^β (β ~ 0.5)
- Moderate W: Linear regime → h(W) ∝ W
- High W: Plasma saturation → h(W) sublinear

### 3.2 Multi-Parameter Fit Example

Experimental data fit to model (gate line slit etch, 20-50 Pa, 50-100°C, 800-1500W):

$$R = 50 \times \sqrt{P/20} \times \exp\left(\frac{-18000}{8.314 \times T}\right) \times \sqrt{W/1000}$$

where:
- R: Etch rate (nm/min)
- P: Pressure (Pa)
- T: Temperature (K)
- W: Power (W)
- Constants: Fitted to experimental data

**Example predictions:**
- At P=20Pa, T=70°C (343K), W=1000W: R = 50 × 1.0 × 1.0 × 1.0 = 50 nm/min
- At P=30Pa, T=70°C, W=1000W: R = 50 × 1.22 × 1.0 × 1.0 = 61 nm/min
- At P=20Pa, T=80°C (353K), W=1000W: R = 50 × 1.0 × 1.24 × 1.0 = 62 nm/min

---

## Part 4: Real-Time Process Control

### 4.1 Feedback-Based Tuning

Process window is initially mapped statically (Chapter 7, Part 2). But during production, **drifts** occur:

**Sources of drift:**
1. **Electrode wear:** Coating erodes over 1000s of wafers → effective area changes
2. **Showerhead clogging:** Deposits accumulate → effective gas distribution changes
3. **Pump degradation:** Aging turbomolecular pump → conductance decreases
4. **Temperature drift:** Environmental changes → wafer temperature drifts ±5°C

**Consequence:** Etch rate drifts over time → must adjust parameters to stay within window.

### 4.2 Real-Time Endpoint Detection

**Optical endpoint detection** monitors etch progress:

During etch, reflectance changes as layers are removed:

```
Reflectance vs. Etch Time

Reflectance (%)
  100 │ Poly layer etch
      │ (Si reflectance: 30%)
   50 ├─ ─ ─ ─
      │  ↓ Transition to oxide
   20 │  Oxide etch
      │  (SiO₂ reflectance: 5%)
      │
      └────────────────────────
        0   5   10  15  20
        Etch time (min)
```

**Endpoint signal:** When reflectance drops (oxide breakthrough), trigger stop of etch.

**Feedback:** If etch takes longer than expected to reach endpoint, something has drifted:
- **Etch took longer:** Etch rate decreased (lower T? lower P? electrode wear?) → next wafer, increase power
- **Etch too fast:** Etch rate increased (higher T?) → next wafer, reduce power

### 4.3 Pressure Feedback Control

Advanced chambers use **dynamic pressure adjustment** during etch:

```
Pressure Profile During Etch (Feedback-Controlled)

Pressure (Pa)
    │
 30 ├─────────────┐
    │             │  (higher P early to maximize etch rate)
 20 ├─────────────┼──────┐
    │             │      │ (reduce P mid-etch for better ARDE)
 10 ├─────────────┼──────┼────┐
    │             │      │    │
  0 └─────────────┴──────┴────┴──────
    0    5   10  15  20   25   30
    Etch time (min)
```

**Logic:**
1. **Start:** High pressure (fast etch, sufficient ion flux)
2. **Middle:** Reduce pressure (ARDE compensation as depth increases)
3. **End:** Very low pressure (gentle approach to stop on target layer)

---

## Part 5: Trade-Off Analysis and Optimization Strategies

### 5.1 Etch Rate vs. Damage Trade-Off

Fundamental conflict: **maximizing etch rate (high P, high T, high W) increases damage.**

| Strategy | Etch Rate Impact | Damage Impact | Window Width |
|----------|------------------|---------------|--------------|
| Increase Power | +++ (large) | +++ (large) | Narrow |
| Increase Temperature | ++ (moderate) | ++++ (severe) | Narrow |
| Increase Pressure | + (small) | 0 (neutral) | Moderate |

**Optimal approach:** Increase pressure for speed (minimal damage), avoid high temperature.

### 5.2 ARDE vs. Etch Rate Trade-Off

Lower pressure improves ARDE but reduces etch rate:

```
Pressure (Pa) | ARDE Factor | Etch Rate | Process Time |
--------------|-----------|---------| -------------|
50            | 2:1       | 400nm/min | 2 hrs        |
20            | 3:1       | 200nm/min | 4 hrs        |
10            | 1.5:1     | 80nm/min  | 10 hrs       |
```

**Process time** (etch time for 50 µm deep slit) scales inversely with etch rate:
- At 50 Pa: 2 hours (fast, but ARDE control tight)
- At 10 Pa: 10 hours (good ARDE, but very long)

**Compromise:** 20 Pa (moderate ARDE + moderate speed) is typical choice for 3D NAND.

### 5.3 Selectivity Tuning Within Process Window

While maintaining etch rate and damage within spec, fine-tune chemistry to adjust selectivity:

**Si/SiO₂ selectivity control:**
- Higher fluorine ratio (more F radicals) → Si etch faster relative to oxide → higher selectivity
- Higher chlorine ratio → more balanced Si/SiO₂ etch → lower selectivity

**Example adjustments (within process window):**
- **Default recipe:** CF₄:Ar = 80:20, P=20Pa, T=70°C, W=1200W → Selectivity 4:1
- **Need higher selectivity:** CF₄:Ar = 90:10, same (P, T, W) → Selectivity 5:1
- **Need lower selectivity:** CHF₃ instead of CF₄, same (P, T, W) → Selectivity 2.5:1

---

## Summary

Process parameter optimization in 3D NAND gate line slit etch involves a multi-dimensional phase space:

1. **Coupling Mechanisms:**
   - Pressure → ion energy, plasma density, ARDE
   - Temperature → reaction rate, damage rate, plasma density
   - Power → plasma generation, ion/radical production, etch rate

2. **Process Window:**
   - Complex polyhedron in (P, T, W) space (not simple rectangle)
   - Constrained by five specifications simultaneously (etch rate, ARDE, selectivity, damage, uniformity)
   - Typical window: 10-30 Pa, 50-90°C, 800-1500W (for ~50µm deep slit)

3. **Experimental Mapping:**
   - Design of Experiments (DOE) or Central Composite Design (CCD)
   - Measure etch rate, uniformity, ARDE, selectivity, damage at each point
   - Identify regions satisfying all constraints

4. **Real-Time Control:**
   - Optical endpoint detection monitors etch progress
   - Feedback adjustment of power/pressure to compensate for drifts
   - Dynamic pressure profiles (higher early, lower as depth increases)

5. **Optimization Trade-Offs:**
   - **Etch rate vs. Damage:** Use pressure increase (low damage impact), avoid temperature
   - **ARDE vs. Speed:** Compromise at ~20 Pa (good uniformity, reasonable speed)
   - **Selectivity tuning:** Adjust gas chemistry within fixed (P, T, W) to achieve target selectivity

Chapters 8-9 build on this phase space mapping by addressing **how chamber geometry (passivation coatings, RF matching networks) enables robust, stable operation within the process window.**

---

**Next:** [Chapter 8: Chamber Passivation and Dielectric Coating Strategies](08-chamber-passivation-and-dielectric-coating-strategies.md)
