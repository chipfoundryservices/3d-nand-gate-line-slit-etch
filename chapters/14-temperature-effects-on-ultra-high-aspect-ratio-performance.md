# Chapter 14: Temperature Effects on Ultra-High Aspect Ratio Performance

## Executive Summary

Temperature profoundly affects 3D NAND gate line slit etch through multiple coupled mechanisms: **(1) exponential etch rate dependence** via Arrhenius kinetics, **(2) TDDB acceleration** of oxide degradation (Chapter 4), **(3) within-trench thermal gradients** that create etch rate non-uniformity, and **(4) plasma stability** at process extremes. Unlike pressure or power, which can be tuned to specific values, temperature is **spatially distributed** — the trench center is cooler than the opening, the sidewalls experience intermediate temperatures. This chapter addresses: *What creates temperature gradients in deep trenches?* *How do we measure and control wafer temperature?* *What are thermal transients and how do they affect etch stability?* *How do temperature effects couple with ARDE and selectivity?* Understanding temperature is essential for achieving uniform etch and minimizing damage across the full trench depth.

---

## Part 1: Temperature Distribution in Deep Trenches

### 1.1 Heat Sources in Plasma Etching

Three heat sources warm the wafer during etch:

#### Heat Source 1: RF Plasma Dissipation
RF power generates heat through collisions (electron-neutral, ion-neutral):

$$P_{\text{dissipated}} = \sum_i E_i \times n_i \times \nu_i$$

where E_i is energy per collision, n_i is collision rate, ν_i is collision frequency.

Typical RF power dissipation:
- **Input power:** 1000-1500 W
- **Fraction reaching wafer as heat:** 20-40%
- **Power flux to 300mm wafer:** 50-200 W/cm²

#### Heat Source 2: Ion Bombardment Energy
Ions with 100-200 eV energy transfer their kinetic energy upon impact:

$$E_{\text{ion impact}} = E_{\text{ion}} \times \Phi_{\text{ions}}$$

For typical ion flux ~10¹¹ ions/cm²/s and 100 eV energy:

$$\text{Heat flux} = 100 \text{ eV} \times 10^{11} \text{ cm}^{-2}\text{s}^{-1} \times 1.6 \times 10^{-19} \text{ J/eV} \approx 16 \text{ W/cm}^2$$

#### Heat Source 3: Exothermic Chemical Reactions
Etch reactions release energy:

$$\text{Si} + 4\text{F} \rightarrow \text{SiF}_4 + \Delta H_{\text{rxn}}$$

Reaction enthalpy ΔH_rxn ~ -500 kJ/mol releases heat per Si atom reacted.

**Total heat flux** combining all sources: 100-300 W/cm² (depending on process parameters).

### 1.2 Heat Transport in and Out of Trenches

Heat flows from plasma toward the wafer via:

**Conduction through gas** (very slow, gas thermal conductivity ~10⁻⁵ W/cm·K)
**Ion/electron impact** (direct energy transfer)
**Radiation** (minor at process temperatures)

Heat removed from wafer via:

**Conduction through wafer bulk** (Si thermal conductivity 150 W/m·K — excellent)
**Thermal contact at chuck** (cooled electrode conducts heat away)
**Helium backside gas** (if used, couples wafer to cooled chuck)

**Thermal equilibrium:**

$$P_{\text{in}} = P_{\text{out}}$$

$$P_{\text{plasma}} = k \times A \times \frac{\Delta T}{\text{distance}}$$

where k is thermal conductivity, A is area, ΔT is temperature difference.

### 1.3 Within-Trench Temperature Gradients

In deep trenches, temperature is **non-uniform**:

```
Temperature Profile in Deep Trench

Temperature (°C)
    │
100 ├─────┐ (trench opening, exposed to plasma)
    │     │ (high ion/radical flux, maximum heating)
 80 ├─────┼───────┐
    │     │       │ (trench middle depth)
 60 │     │       │ (moderate plasma coupling)
    │     │       │
 40 │     │       ├───────────
    │     │       │           (trench bottom, far from plasma)
 20 │     │       │           (minimal ion/radical reach)
    │     │       │           (cooled primarily by heat conduction through Si)
  0 └─────┴───────┴────────────
    0    10   20   30   40   50 (depth in trench, µm)

    ΔT (top to bottom): 40-80°C (significant gradient)
```

**Physical mechanism:**
- **Trench opening:** Maximum RF flux, highest ion/radical flux → maximum heating
- **Trench middle:** Intermediate flux (some ions scattered into sidewalls)
- **Trench bottom:** Minimal plasma coupling (ions ballistic, few reach bottom; radicals diffusion-limited)
- **Heat removal:** Only via conduction through Si sidewalls upward to chuck

**Consequence:** Temperature variation creates **within-trench etch rate variation** (ARDE is compounded by thermal effects).

---

## Part 2: Etch Rate Temperature Dependence

### 2.1 Arrhenius Kinetics

Chemical etch rate follows Arrhenius dependence:

$$R(T) = R_0 \exp\left(-\frac{E_a}{k_B T}\right)$$

where:
- **R_0:** Pre-exponential factor
- **E_a:** Activation energy (typically 10-30 kJ/mol for plasma etch)
- **k_B:** Boltzmann constant (8.314 J/mol·K)
- **T:** Temperature (K)

**Example calculations** for E_a = 20 kJ/mol:

| Temperature | Relative Etch Rate | Notes |
|-------------|-------------------|-------|
| 0°C (273K) | 1.0 | Baseline |
| 30°C (303K) | 1.6 | +60% |
| 50°C (323K) | 2.6 | +160% |
| 70°C (343K) | 4.2 | +320% |
| 100°C (373K) | 11.0 | +1000% |

**Key insight:** 100°C temperature rise causes **10-20× etch rate increase** (exponential, not linear).

### 2.2 Within-Trench Etch Rate Variation from Temperature

Combining thermal gradient with Arrhenius kinetics:

**At trench opening (100°C):** 
$$R = R_0 \exp(-20000 / (8.314 × 373)) \approx 11 R_0$$

**At trench bottom (40°C):**
$$R = R_0 \exp(-20000 / (8.314 × 313)) \approx 1.2 R_0$$

**Etch rate ratio:** 11 R_0 / 1.2 R_0 ≈ **9:1 (severe ARDE from temperature alone)**

**Combined with geometric ARDE** (Chapter 10, which creates ~3-5:1 effect):

$$\text{Total ARDE} = 9 × 3 = 27:1 \text{ (catastrophic)}$$

This explains why temperature control is critical — uncontrolled thermal gradients make ARDE unmanageable.

### 2.3 Temperature Control Strategy

To minimize thermal ARDE:

**Goal:** Keep wafer temperature within ±5°C across entire wafer and throughout trench.

**Methods:**

1. **Cooled Chuck**
   - Circulate coolant (water, cryogenic fluid) through electrode
   - Maintain electrode at 10-20°C below target wafer temperature
   - Heat flows from wafer → chuck via conduction and helium coupling

2. **Target Wafer Temperature**
   - **Typical:** 50-80°C (compromise between etch rate and damage)
   - **Cold:** 30-40°C (slower etch, better ARDE control, minimal damage)
   - **Hot:** 80-100°C (fast etch, severe ARDE, high damage risk)

3. **Helium Backside Pressure**
   - Pressurized He between wafer and electrode acts as thermal conductor
   - Higher He pressure → better thermal coupling → reduced gradients
   - Typical: 50-200 torr (adjustable)

4. **Process Temperature Feedback**
   - Infrared thermometer monitors wafer surface temperature
   - Adjust chuck coolant flow or He pressure to maintain setpoint
   - Real-time feedback maintains ±5°C control

---

## Part 3: TDDB Acceleration and Damage

### 3.1 Temperature Dependence of Time-Dependent Dielectric Breakdown

TDDB kinetics depend exponentially on temperature:

$$t_{\text{to breakdown}} = A \times E^{-\gamma} \times \exp\left(\frac{E_a}{k_B T}\right)$$

Rearranging:

$$\log(t) = \log(A) - \gamma \log(E) + \frac{E_a}{2.3 k_B T}$$

**Temperature coefficient:** 

$$\frac{d \log(t)}{dT} = -\frac{E_a}{2.3 k_B T^2}$$

For typical E_a ~ 0.5 eV (TDDB activation energy):

$$\text{Temperature coefficient} \approx -0.02 \text{ per K}$$

This means: **Temperature increase of 50 K reduces breakdown time by factor of e^(0.02×50) ≈ 2.7×**

**Practical impact:**

| Wafer Temperature | TDDB Lifetime | Damage Risk |
|------------------|---------------|------------|
| 30°C | 10+ years | Minimal |
| 50°C | 5-10 years | Low |
| 70°C | 1-2 years | Moderate |
| 100°C | 1-3 months | Severe |

### 3.2 Floating Gate Charging Temperature Dependence

Floating gate charging rate (Chapter 4) depends on electron mobility:

$$\mu_e \propto T^{-3/2}$$

Higher temperature → lower electron mobility → fewer electrons reaching floating gate... but also **higher electron thermal velocity** → more collisions with floating gate.

**Net effect:** Temperature increase slightly reduces charging rate (beneficial for damage control).

However, temperature increase accelerates **TDDB** (bad), which outweighs the charging rate reduction.

**Conclusion:** Lower temperature better overall (less TDDB damage, acceptable charging control).

---

## Part 4: Pressure-Temperature Coupling

### 4.1 Ideal Gas Law Effects

Plasma density depends on pressure and temperature:

$$n_e = \frac{P}{k_B T}$$

At constant pressure, higher temperature → lower plasma density → fewer radicals and ions.

```
Plasma Density vs. Temperature (constant pressure)

Plasma Density (cm⁻³)
    │
 10^10 ├────────────┐
       │            │ (low T = high density)
 5×10^9├────────────┼─────────
       │            │
 10^9  │            │
       │            ├────────── (high T = low density)
       │            │
 10^8  │            │
       │            │
       └────────────┴──────────
       0   50  100  150 (Temperature, °C)

At P = 20 Pa:
    30°C: n_e ~ 5×10^9 cm⁻³
    100°C: n_e ~ 2×10^9 cm⁻³ (60% reduction)
```

### 4.2 Temperature-Pressure Trade-Off

**To maintain constant etch rate** when temperature increases (and plasma density drops), must **increase pressure** (or power):

```
Etch Rate Maintenance

Goal: Keep R_etch = constant despite temperature increase

R ∝ (etch rate kinetics) × (ion/radical flux)

If T increases:
  → Kinetics increase (exponential benefit)
  → Plasma density decreases (flux penalty)
  
To compensate flux loss:
  → Increase pressure (raise plasma density)
  OR
  → Increase power (boost plasma generation)
```

**Practical control strategy:**

| Temperature | Required Pressure | Required Power | Result |
|-------------|-------------------|-----------------|--------|
| 50°C | 20 Pa | 1000 W | Baseline etch rate |
| 70°C | 22 Pa | 1100 W | Same etch rate, better ARDE |
| 30°C | 25 Pa | 900 W | Same etch rate, slower |

### 4.3 Optimal Temperature Selection

**Trade-offs:**

```
Temperature Optimization

Temperature (°C)
    │
100 ├─────────────────────┐ (Fast etch, severe damage)
    │                     │
 70 ├─────────────────────┤ (Good etch, moderate damage) ← OPTIMAL
    │                     │
 50 ├─────────────────────┤ (Slow etch, minimal damage)
    │                     │
 20 ├─────────────────────┤ (Very slow, excellent control)
    │                     │
  0 └─────────────────────┴──────────
      ARDE     Speed   Damage   TDDB
      Poor     Good    Bad      Good
      Good     Poor    Good     Poor
```

**Optimal:** 60-80°C (balance between etch rate, ARDE control, and damage management).

---

## Part 5: Thermal Transients and Process Stability

### 5.1 Temperature Response Time

When RF power changes, wafer temperature changes via:

$$C_{\text{thermal}} \frac{dT}{dt} = P_{\text{in}} - P_{\text{out}}$$

Thermal time constant:

$$\tau_{\text{thermal}} = \frac{C_{\text{thermal}}}{U}$$

where U is the overall heat transfer coefficient.

**Typical values:**
- Thermal capacitance of 300mm Si wafer: ~1000 J/K
- Heat transfer coefficient (chuck coupling): 500-2000 W/K
- Time constant: τ ~ 0.5-2 seconds

**Consequence:** Temperature lags **1-2 seconds** behind power changes.

### 5.2 Power Transients and Temperature Drift

During etch:
- RF power may be modulated (e.g., pulsed RF)
- Showerhead clogging causes plasma density to drift
- Electrode coating erodes → conductivity changes

Each transient causes temperature change:

```
Temperature Response to RF Power Step

Temperature (°C)
    │
 80 ├─────────────────────────┐
    │      Step up in power   │
 70 │                       /─┘
    │                     /
 60 │                   /
    │                 /
 50 │───────────────/─ (settling time ~ 2-3 seconds)
    │
 40 └─────────────────────────────
    0    2    4    6    8    10 (time, sec)

During 2-second settling:
  - Etch rate changes by ~50%
  - ARDE varies (bottom etch slower during ramp-up)
  - Cumulative effect: within-trench depth variation
```

### 5.3 Temperature Feedback Control

Modern chambers use **temperature feedback** to maintain stability:

```
Thermal Feedback Loop

RF Power / Pressure adjustment
    ↑
    │
Temperature Measurement (IR sensor)
    │
    ├─ PID Controller
    │  (P = proportional, I = integral, D = derivative)
    │
    └─ Coolant Flow or He Pressure Valve
       (adjust to compensate for temperature drift)
```

**Control algorithm:**
1. Measure wafer temperature every 100 ms
2. Compare to setpoint (target T)
3. If T high: increase coolant flow or He pressure (improve cooling)
4. If T low: decrease cooling (reduce heat loss)
5. Adjust to maintain T within ±2°C

**Effectiveness:** With feedback, temperature stability improves from ±10-20°C (no control) to ±2-5°C (with control).

---

## Part 6: Integration with ARDE and Selectivity

### 6.1 Thermal ARDE Contributions

Total ARDE has three components:

$$\text{ARDE}_{\text{total}} = \text{ARDE}_{\text{diffusion}} × \text{ARDE}_{\text{thermal}} × \text{ARDE}_{\text{scattering}}$$

where:
- **Diffusion ARDE:** From radical transport limits (Chapter 10) ~ 3-5:1
- **Thermal ARDE:** From temperature gradients ~ 2-4:1
- **Scattering ARDE:** From ion geometric effects (Chapter 11) ~ 1.5-2:1

**Combined:** 3 × 3 × 1.5 = **13.5:1 (uncontrolled)**

**With thermal control:** If thermal ARDE reduced to 1.2:1:

3 × 1.2 × 1.5 = **5.4:1 (manageable)**

### 6.2 Temperature Effects on Selectivity

Selectivity has temperature dependence through activation energy:

$$S_{AB}(T) = \frac{R_A(T)}{R_B(T)} = \frac{R_{A,0} \exp(-E_{a,A}/k_B T)}{R_{B,0} \exp(-E_{a,B}/k_B T)}$$

If E_a,A > E_a,B (different activation energies for different materials):

$$\ln(S) = \ln(R_{A,0}/R_{B,0}) + (E_{a,B} - E_{a,A})/(k_B T)$$

**Consequence:** Selectivity **changes with temperature**.

**Example:**
- At 50°C (323K): Si/SiO₂ selectivity 4:1
- At 70°C (343K): Si/SiO₂ selectivity 3.5:1 (selectivity decreases 12%)

**Implication:** Temperature control affects not just etch rate, but also selectivity margins → must consider together.

---

## Summary

Temperature effects are **critical but often underappreciated** in 3D NAND gate line slit etch:

1. **Heat Sources & Gradients:**
   - RF dissipation, ion impact, chemical reactions → 100-300 W/cm² heat flux
   - Within-trench gradients: 40-80°C difference (top to bottom)
   - Heat removal via chuck conduction and helium coupling

2. **Exponential Etch Rate Dependence:**
   - Arrhenius kinetics with E_a ~ 20 kJ/mol
   - 100°C rise → 10-20× etch rate increase
   - Thermal ARDE alone: 3-5:1 (combines with diffusion and scattering ARDE)

3. **TDDB Acceleration:**
   - Breakdown time reduced by 2.7× per 50°C increase
   - 70°C: ~1-2 year oxide lifetime
   - 100°C: ~1-3 month lifetime (unacceptable)

4. **Pressure-Temperature Coupling:**
   - Higher T reduces plasma density → fewer species
   - Must increase pressure/power to maintain etch rate
   - Creates coupled control requirement (T and P not independent)

5. **Thermal Control Strategy:**
   - Target: 60-80°C wafer temperature
   - Cooled chuck with feedback control
   - Helium backside pressure for thermal coupling
   - ±2-5°C control achievable with modern systems

6. **Selectivity Coupling:**
   - Temperature shifts selectivity ratios (~10% change per 20°C)
   - Must account for thermal effects in process window

**Chapter 14 completes Part III (Process Physics).** All core physics, engineering, and process control fundamentals are now established. Chapters 15-18 (Part IV) address production-scale implementation and advanced phenomena (floating gate contamination, micro-loading, cluster integration, and characterization).

---

**Next:** [Chapter 15: Floating Gate Contamination Prevention](15-floating-gate-contamination-prevention.md) [Ready for development]
