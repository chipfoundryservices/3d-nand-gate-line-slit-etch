# Chapter 10: Extreme ARDE Physics — Ions and Radicals in Ultra-High Aspect Ratios

## Executive Summary

**Aspect Ratio Dependent Etching (ARDE)** is the dominant challenge in gate line slit etch. As aspect ratios exceed 100:1, 500:1, and ultimately 1000:1+, the physics of ion and radical transport fundamentally changes. Ions become ballistic (traveling in straight lines), radicals diffuse into trenches but rarely reach the bottom, and the trench geometry itself becomes the etch rate limiter. This chapter develops ARDE from first principles, deriving the conditions under which different transport regimes dominate, and presenting practical strategies for ARDE compensation in production processes.

---

## Part 1: From Moderate to Extreme Aspect Ratios

### 1.1 Etch Rate Scaling with Aspect Ratio

In conventional silicon etch (planar trenches at AR ~ 3:1), etch rate is relatively uniform:

```
Etch Rate vs. Depth (AR 3:1)

200 nm/min  ├──────────────────────────
            │  (relatively flat)
150 nm/min  │
            │
100 nm/min  ├──────────────────────────
            │
   0 nm/min └─────────────────────────────
               0    1    2    3 (depth, µm)
```

This is because at low AR, the trench opening is wide enough that ions and radicals easily access the trench bottom.

In 3D NAND gate line slit etch (AR > 500:1), etch rate decreases dramatically:

```
Etch Rate vs. Depth (AR 500:1)

400 nm/min  ├─────┐
            │     │  (sharp initial etch)
200 nm/min  │     ├─────────┐
            │           (slow deep etch)
 50 nm/min  │               ├───────────
            │                         
  0 nm/min  └─────────────────────────────
               0   10   20   30  (depth, µm)
```

The etch rate **decreases 5-10× as depth increases** from 0 to 50 µm.

**Quantitatively:**
- At 2-3 µm depth (AR ~ 100:1): etch rate ≈ 300 nm/min
- At 20 µm depth (AR ~ 1000:1): etch rate ≈ 30-50 nm/min
- At 50 µm depth (AR ~ 2500:1): etch rate ≈ 5-10 nm/min

This 30-60× reduction is the central ARDE problem.

### 1.2 Why Etch Rate Decreases with AR: Transport Limitations

Etch rate is fundamentally limited by **species delivery** to the reaction site. In trenches, three transport mechanisms matter:

#### Transport 1: Ion Bombardment
Ions accelerated by the RF sheath travel toward the wafer surface. But in deep trenches:

**Ion Mean Free Path:**
$$\lambda_{\text{ion}} = \frac{k_B T}{e \cdot P} \cdot \alpha$$

where:
- **k_B T:** Thermal energy
- **P:** Pressure
- **α:** Collision cross-section

At typical etch pressures (10-100 Pa) and energies (50-300 eV):
- **Mean free path:** 1-10 cm (ions travel ballistically!)

An ion entering a 20nm-wide trench has a high probability of **striking the sidewall** before reaching the bottom:

```
Ion Trajectories in Deep Trench

Top Opening (AR = 1:1)
    ║ ← Ion path
    ║   (enters trench)
    
Middle (AR = 100:1)
    ║
    ║  (ion deflects off sidewall if trajectory is off-center)
    
Bottom (AR = 1000:1)
    ║
    ║  (only ions traveling along centerline reach bottom)
    
RESULT: Bottom of trench receives only central ion beam
        Sidewalls receive ions from broader angles
```

**Ion flux to trench bottom decreases as AR increases.**

#### Transport 2: Neutral Radical Diffusion
Reactive neutrals (Cl, F atoms) are produced in the plasma above the trench. They diffuse downward into the trench.

**Diffusion length:**
$$L_{\text{diff}} = \sqrt{D \tau_{\text{residence}}}$$

where:
- **D:** Diffusion coefficient (~1-10 cm²/s at low pressure)
- **τ_residence:** Residence time in trench

In a 50 µm deep trench:
- **Residence time:** ~1-10 ms (radicals spend time diffusing)
- **Diffusion length:** √(D τ) ≈ √(1 cm²/s × 10 ms) ≈ 300 µm

Wait—diffusion length is larger than trench depth! This seems to suggest radicals easily reach the bottom...

**But:** Radicals react immediately upon hitting any surface (Si, SiO₂, etc.). They don't diffuse 300 µm through the plasma; they react with the first surface they encounter.

```
Radical Path in Trench

Radical enters trench opening
    ↓ (diffuses downward)
    ↓
    └→ Hits sidewall → REACTS (consumed)
    
Only radicals entering near the centerline
reach the trench bottom before reacting on sidewalls
```

**Radical flux to trench bottom decreases with AR** (fewer radicals survive the sidewall journey to reach the bottom).

#### Transport 3: Product Removal
Etch byproducts (volatile compounds like SiCl₄, SiF₄, AlCl₃) must leave the trench to make room for fresh reactants.

In deep trenches, product removal is also diffusion-limited:

**Residence time of products:**
$$\tau_{\text{product}} \approx \frac{L^2_{\text{trench}}}{D_{\text{product}}}$$

For a 50 µm trench:
$$\tau_{\text{product}} \approx \frac{(50 \times 10^{-4} \text{ cm})^2}{10^{-1} \text{ cm}^2/\text{s}} \approx 2.5 \text{ ms}$$

As products accumulate, their partial pressure increases. **Back-diffusion** (products diffusing back into the trench) becomes significant, reducing net etch rate.

### Summary of Transport Limits

| Transport Mechanism | Characteristic Length | AR Dependence |
|---|---|---|
| **Ion reach** | 1-10 cm (ballistic) | Independent of AR; ions always reach bottom. But flux becomes directional at high AR. |
| **Radical diffusion** | √(D τ); limited by sidewall reactions | ∝ 1/√(AR); fewer radicals survive to reach bottom |
| **Product removal** | Diffusion of volatiles out of trench | ∝ 1/AR; stronger back-diffusion at extreme AR |

---

## Part 2: Etch Rate Models at Extreme AR

### 2.1 Reaction-Limited Regime (Low AR, Abundant Radicals)

At AR < 50:1, radicals and ions are abundant at the trench bottom. Etch rate is limited by **reaction kinetics**, not species delivery:

$$R_{\text{etch}} = k_{\text{rxn}} \cdot C_{\text{radicals}} \cdot C_{\text{ions}}$$

where:
- **k_rxn:** Reaction rate constant (depends on temperature, material)
- **C_radicals, C_ions:** Surface concentrations

Etch rate is **relatively independent of AR** in this regime.

### 2.2 Diffusion-Limited Regime (Extreme AR > 200:1)

At AR > 200:1, radical and/or ion delivery becomes the limiting factor:

$$R_{\text{etch}} = \eta \cdot \Phi_{\text{radicals, delivered}} \cdot f(\text{AR})$$

where:
- **η:** Sticking coefficient (probability radical reacts on contact)
- **Φ_radicals, delivered:** Flux of radicals actually reaching the trench bottom
- **f(AR):** Scaling function that decreases with AR

For extreme AR, empirical fits show:

$$\Phi_{\text{delivered}} \propto \frac{1}{\sqrt{\text{AR}}} \quad \text{or} \quad \frac{1}{\text{AR}^{1.5}}$$

**Etch rate scaling:**

$$R_{\text{etch}} \propto \text{AR}^{-0.5} \text{ to } \text{AR}^{-1.5}$$

### 2.3 Transition Zone (AR 50:1 to 200:1)

Between reaction-limited and diffusion-limited regimes, etch rate follows:

$$R_{\text{etch}} = \frac{R_{\text{reaction}} \cdot R_{\text{diffusion}}}{R_{\text{reaction}} + R_{\text{diffusion}}}$$

This is the gate line slit etch operating range for most 3D NAND processes. Etch rate depends on **both reaction kinetics and transport**.

---

## Part 3: ARDE Mitigation Strategies

### 3.1 Strategy 1: Pressure Tuning

**Insight:** Increasing pressure reduces mean free path for radicals, encouraging sidewall reactions **before** radicals reach the bottom. This sounds counterintuitive—we want to *prevent* sidewall reactions—but there's a sweet spot.

**Effect of Pressure on ARDE:**

```
Low Pressure (5 Pa):
  - Radicals travel far before reacting
  - Many survive to trench bottom
  - Bottom etch rate: HIGH
  - Top/bottom uniformity: Poor (high ARDE)

Medium Pressure (20 Pa):
  - Radicals react with sidewalls sooner
  - Fewer reach bottom, but systematic
  - Bottom etch rate: MEDIUM
  - ARDE reduced (more uniform)

High Pressure (100 Pa):
  - Radicals consumed by sidewalls
  - Very few reach bottom
  - Bottom etch rate: LOW
  - ARDE reduced but etch rate severely cut
```

**Typical approach:** Use medium pressure (15-30 Pa) and compensate for lower etch rate with increased power.

### 3.2 Strategy 2: Gas Chemistry Modification

**Insight:** Different radical species have different diffusion lengths and sidewall reactivity.

| Radical | Diffusion Behavior | ARDE Characteristics |
|---|---|---|
| **Cl (chlorine)** | Fast diffusion, reactive on all materials | High ARDE; reacts with sidewalls and bottom equally |
| **F (fluorine)** | Moderate diffusion, Si-selective | Moderate ARDE; reacts faster on Si than oxide |
| **Complex radicals** (CFx) | Slower diffusion, oxygen-rich | Lower ARDE; sidewall reactions slower |

**Strategy:** Use fluorine-based chemistry (CF₄, CHF₃) to preferentially etch Si (bottom material) over oxide (sidewalls), reducing ARDE.

### 3.3 Strategy 3: Cyclic or Pulsed Etch

**Insight:** Instead of continuous etching, alternate etch and passivation steps.

```
Cyclic Etch Steps

Cycle 1: Etch (2 seconds)   → Remove material at top and bottom
         Passivate (1 sec)  → Deposit protective layer on sidewalls

Cycle 2: Etch (2 seconds)   → Remove material top and bottom; sidewalls protected
         Passivate (1 sec)  → Re-deposit protective layer

Cycle N: Repeat...
```

**Result:** Sidewalls are protected from etch; etch concentrates on top/bottom. ARDE is reduced.

**Example:** Cryogenic silicon etch combines:
- Cl₂ + O₂ (etch chemistry)
- ICP plasma (ion source)
- Ultra-low temperature (-80°C to -120°C)
- Passivation with O₂ plasma

This achieves AR 10:1 to 50:1 with near-vertical sidewalls.

For gate line slits, cyclic approaches are less mature but promising for extreme AR (> 1000:1) applications.

### 3.4 Strategy 4: Feedb–ack Pressure Tuning

**Insight:** Use real-time feedback (optical endpoint detection or RF monitoring) to adjust pressure dynamically as depth increases.

```
Depth-Dependent Pressure Profile

Pressure (Pa)
    │
 30 ├────┐
    │    │  (high pressure at top, reduces ARDE early)
 20 ├────┼─────┐
    │    │     │  (gradual reduction in pressure)
 10 │    │     └────┐
    │    │          └────── (low pressure at depth, maintains etch rate)
  0 └────┴───────────────
    0   10   20   30 (depth, µm)
```

As etch depth increases and AR increases, reduce pressure to compensate for natural ARDE slowdown. This maintains more uniform etch rate throughout the trench.

### 3.5 Strategy 5: Spatial Power Modulation

**Insight:** If different regions of the wafer have different etch rates (micro-loading effects in array structures), apply spatially varying RF power.

**Challenge:** Requires electrode designs with multiple RF zones, increasing equipment complexity.

---

## Part 4: ARDE Measurement and Characterization

### 4.1 Measuring ARDE

**Method 1: Cross-Section SEM**
- Etch test patterns with known geometry
- Cleave wafers and image in SEM
- Measure etch depth at top and bottom of trench
- Calculate ARDE factor: **Depth(top) / Depth(bottom)**

**Method 2: Optical Endpoint Detection**
- Monitor light reflectance during etch
- Reflectance changes as material removal exposes new layers
- Etch rate can be inferred from reflectance rate of change
- Combined with depth monitoring → ARDE profile

**Method 3: Electrical Characterization**
- After etch, measure resistance of gate lines
- Incomplete etch (residue) or damaged oxide increases resistance
- Resistance profile → infer etch completion depth profile
- Indirect but production-relevant

### 4.2 ARDE Factor Definition

**ARDE Factor (also called "selectivity" in some contexts):**

$$\text{ARDE}_{\text{factor}} = \frac{R_{\text{top}}}{R_{\text{bottom}}}$$

where:
- **R_top:** Etch rate at shallow depth (2-5 µm)
- **R_bottom:** Etch rate at deep depth (40-50 µm)

For planar trenches: ARDE ≈ 1.0-1.5  
For 3D NAND slits: ARDE ≈ 5-20 (before compensation)  
After mitigation: ARDE ≈ 2-3 (goal: reduce to ~ 1.5 or better)

### 4.3 Practical ARDE Targets for Production

| Aspect Ratio | ARDE Target | Status |
|---|---|---|
| 10:1 (conventional) | 1.0-1.2 | Easily achievable |
| 50:1 (modern 3D NAND) | 1.5-2.0 | Achievable with standard processes |
| 200:1 (advanced 3D NAND) | 2.0-3.0 | Requires optimization |
| 1000:1 (future) | 3-5 | Very challenging, active R&D |

---

## Part 5: Modeling ARDE at Extreme AR

### 5.1 First-Principles Model (Simplified)

**Assumption:** Etch rate is limited by radical delivery to trench bottom.

**Radical flux to bottom:**
$$\Phi_{\text{bottom}} = \Phi_{\text{source}} \cdot \text{exp}\left(-\frac{\text{AR}}{L_{\text{eff}}}\right)$$

where:
- **Φ_source:** Radical generation rate at trench opening
- **L_eff:** Effective diffusion length before sidewall reaction

**Etch rate:**
$$R = \eta \cdot \Phi_{\text{bottom}} = \eta \cdot \Phi_{\text{source}} \cdot \text{exp}\left(-\frac{\text{AR}}{L_{\text{eff}}}\right)$$

**Implication:** Etch rate decreases **exponentially** with AR at extreme geometries.

Fitting to experimental data for gate line slits (AR 100-1000):
- Typical **L_eff ≈ 50-200** (depends on pressure, gas chemistry)
- **Exponential decay** predicts etch rate reductions matching observations

### 5.2 Computational Modeling (Brief Overview)

Production-scale ARDE optimization uses computational models:

**TCAD Simulations:**
- Solve ion/electron transport equations in trench geometry
- Account for space charge effects, sheath dynamics
- Predict ion and radical flux distributions
- Computationally expensive (1000s of hours for complex geometries)

**Machine Learning:**
- Train models on large experimental datasets
- Predict etch rate as function of pressure, power, gas flow, depth
- Fast predictions enable real-time process optimization
- Increasingly used in advanced fabs

---

## Summary

ARDE at extreme aspect ratios (1000:1) fundamentally differs from conventional trenches due to:
1. **Ion ballistic transport:** Only central ions reach trench bottom
2. **Radical diffusion limitations:** Radicals react with sidewalls before reaching bottom
3. **Product back-diffusion:** Etch byproducts accumulate, inhibiting further etch

**Etch rate decreases by 5-20× as aspect ratio increases from 100:1 to 1000:1.**

Mitigation strategies include:
- Pressure tuning (medium pressure balances sidewall vs. bottom etch)
- Gas chemistry selection (F-based etch selectively attacks Si)
- Cyclic etch-passivation (protect sidewalls, concentrate etch on bottom)
- Feedback control (adjust pressure dynamically with depth)
- Spatial power modulation (compensate for array micro-loading)

Achieving ARDE factors of 1.5-2.0 in production processes for AR > 200:1 requires integrated use of multiple strategies and continuous process optimization.

---

**Next:** [Chapter 11: Ion Energy and Flux in Vertical Geometries](11-ion-energy-vertical.md)
