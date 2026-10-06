# Chapter 13: Sidewall Passivation and Scalloping Control

## Executive Summary

In deep trench etch, sidewalls are inevitably exposed to ions and radicals as off-center ions scatter (Chapter 11). Uncontrolled sidewall erosion creates two problems: **(1) sidewall roughness (scalloping)** — wavy undulations in the trench profile that increase parasitic capacitance and leakage, and **(2) material loss** — chamber coatings erode, electrode surfaces sputter, trench walls degrade. **Sidewall passivation**—depositing protective films—is the primary mitigation strategy. This chapter addresses: *What passivation mechanisms work?* *How do we deposit protective films?* *What causes scalloping and how do we suppress it?* *What are the trade-offs between protection and etch rate?* Understanding sidewall control is essential for achieving smooth profiles and preventing yield loss from electrical degradation.

---

## Part 1: Sidewall Damage and Scalloping Physics

### 1.1 Scalloping Formation Mechanisms

**Scallop** = periodic undulation in sidewall profile (wavelength ~20-200 nm, amplitude ~5-50 nm).

Scalloping forms via two mechanisms:

#### Mechanism 1: Cyclic Ion Exposure

In cyclic etch-passivation processes, sidewalls alternate between being **exposed to etch** and **covered by passivation**:

```
Etch Cycle Visualization

Cycle 1:
    ├─ Etch (1 sec)    → Remove material uniformly, sidewalls exposed
    │
    ├─ Passivate (0.5 sec) → Deposit protective film on ALL surfaces
    │
Cycle 2:
    ├─ Etch (1 sec)    → Bottom exposed to etch, sidewalls protected
    │                     But some sidewalls already at different heights
    │                     (due to non-uniform etch in Cycle 1)
    │
    ├─ Passivate (0.5 sec) → Re-deposit film
    │
Cycle 3-50:
    ├─ Repeat...       → Height variations compound
    │
    └─ Result: Periodic sidewall undulation (scallops)
```

**Physical origin:** Etch depth varies slightly across wafer → some regions deeper than others → different exposure to cycling → scallops form.

#### Mechanism 2: Continuous Etch with Varying Lateral Reactivity

In continuous (non-cyclic) etch, scallops can still form if:
- **Ion flux varies directionally** (more ions from certain angles)
- **Sidewall passivation is incomplete** (patches of unprotected sidewall alternate with protected regions)
- **Pressure/temperature fluctuations** create cyclic variations in etch rate

### 1.2 Scallop Morphology and Impact

**Scallop dimensions:**
- **Wavelength (λ):** 50-200 nm (distance between peaks)
- **Amplitude (A):** 10-50 nm (peak-to-trough height)
- **Aspect ratio (A/λ):** 0.1-0.5 (how "sharp" the scallops are)

**Impact on electrical properties:**

**Effect 1: Increased Capacitance**
Rough sidewalls have more surface area:

$$C_{\text{rough}} = C_{\text{smooth}} \times \left(1 + \frac{A}{\lambda} \times \text{roughness factor}\right)$$

For typical scallops (A=20nm, λ=100nm):
$$C_{\text{rough}} / C_{\text{smooth}} \approx 1.3-1.5 \text{ (30-50% increase)}$$

This increases parasitic capacitance between adjacent gates → worse coupling, slower logic operation.

**Effect 2: Increased Leakage**
Rough sidewalls have more defects and stress concentrations. Oxide on rough Si has more defects:

$$I_{\text{leak}} = I_0 \times \exp\left(K \times A\right)$$

where K depends on defect density and A is scallop amplitude.

For A=20nm increase: Leakage can increase by 2-3×.

**Specification limits:**
- **Target scallop amplitude:** < 10 nm (smooth profiles)
- **Acceptable:** 10-20 nm (minor impact on performance)
- **Unacceptable:** > 30 nm (significant coupling, leakage issues)

---

## Part 2: Passivation Strategies

### 2.1 Plasma-Assisted Passivation

**Approach:** Deposit a thin (~2-10 nm) protective film on sidewalls using plasma.

#### Film Type 1: Oxide Passivation

**Method:** Introduce O₂ or H₂O into etch plasma to form oxide on sidewalls.

**Chemistry:**
$$\text{Si (on sidewall)} + \text{O}_2 \text{ (plasma)} \rightarrow \text{SiO}_x \text{ (oxide film)}$$

**Thickness control:** Adjust O₂ partial pressure or exposure time to control oxide thickness.
- **2 nm oxide:** Minimally protective (some ions penetrate)
- **5 nm oxide:** Good protection (ions stopped by oxide)
- **10 nm oxide:** Excellent protection, but may slow etch rate

**Advantage:** Simple, uses existing chamber gases
**Disadvantage:** Oxide growth consumes material underneath → effective trench width narrows

### 2.2 Cyclic Passivation (Advanced)

**Approach:** Alternate etch and passivation steps to suppress scalloping.

**Ideal Cycle:**
```
Step 1: Etch (1-2 seconds)
        → Remove material from trench bottom
        → Sidewalls exposed but not etched (protected by geometry)

Step 2: Passivate (0.5-1 second)
        → Deposit film on ALL exposed surfaces (top, bottom, sidewalls)

Step 3: Etch (1-2 seconds)
        → Passivation layer removed from bottom (lower pressure/different chemistry)
        → Sidewalls remain protected
```

**Benefit:** Sidewalls are protected during etch phases, only exposed during passivation. Reduces scallop formation.

**Trade-off:** Process time increases significantly (each cycle adds 2-3 seconds; 100 cycles = 200-300 seconds added).

### 2.3 Chemical Passivation

**Approach:** Use etch chemistry that inherently creates protective films.

#### Example 1: Fluorocarbon Polymer Passivation

In CF₄/Ar etch, side reactions create CFₓ polymers:

$$\text{CF}_4 + \text{e}^- \rightarrow \text{CF}_3 + \text{F} + \text{polymer fragments}$$

These fragments can deposit on sidewalls as **CFₓ polymer film** (thickness ~2-5 nm).

**Advantage:** Automatic (no additional process steps)
**Disadvantage:** Film thickness is hard to control; can clog showerhead

#### Example 2: Cl₂/O₂ Hybrid Passivation

Chlorine etch with small O₂ addition:
$$\text{Si} + \text{Cl} \rightarrow \text{SiCl}_x$$
$$\text{SiCl}_x + \text{O}_2 \rightarrow \text{SiCl}_x\text{O}_y \text{ (mixed oxide-chloride, protective)}$$

The mixed compound is less volatile than pure SiCl₄ → deposits on cooler sidewalls, creating protective film.

---

## Part 3: Scalloping Suppression Techniques

### 3.1 Pressure and Temperature Optimization

**Effect of pressure on scalloping:**

Low pressure → longer radical mean free path → radicals penetrate to sidewalls more easily → more uniform sidewall erosion → LESS scalloping

High pressure → radicals consumed by sidewall collisions → uneven distribution → MORE scalloping

```
Scallop Amplitude vs. Pressure

Scallop Amplitude (nm)
    │
 40 ├─────────────────┐
    │                 │ (high P = uneven)
 20 ├─────────────────┤
    │               /─┘
    │             /
 10 ├───────────/─────┤
    │         /       │ (low P = uniform)
  5 │       /         │
    │     /           │
  0 └─────────────────┴──────────
    0   10   20  30  40   50
        Pressure (Pa)

    Optimal for scallop suppression: 5-10 Pa (very low pressure)
    But conflicts with ARDE goal (need moderate P for ARDE control)
```

**Temperature effect:**

High temperature → faster chemical etch, more uniform bottom reach → LESS scalloping

Low temperature → slower etch, more ion-focused → potentially MORE scalloping (ions dominate)

**Optimization:** Moderate temperature (70-80°C) + low-moderate pressure (10-15 Pa) + cyclic approach gives best scallop control.

### 3.2 Gas Chemistry for Scallop Suppression

**Strategy:** Use chemistry that creates inherent sidewall passivation.

| Chemistry | Passivation Mechanism | Scallop Amplitude | Pros | Cons |
|-----------|----------------------|-------------------|------|------|
| **Pure CF₄** | None (aggressive) | 20-40 nm | Fast etch | Rough sidewalls |
| **CF₄ + O₂** | Polymer/oxide film | 10-20 nm | Moderate | Slower |
| **CHF₃** | CFₓ polymer film | 5-15 nm | Good passivation | Slower etch |
| **Cl₂ + O₂** | Mixed oxide film | 10-20 nm | Selective | Complex chemistry |

**Practical recipe:** Use **CHF₃/Ar** for steps where scallop control is critical (early in etch when deep aspects are high), then switch to **CF₄/Ar** for speed when scallop control less critical.

### 3.3 Power Modulation for Uniformity

**Strategy:** Vary RF power to maintain uniform etch across wafer and depth.

**Physical principle:** Higher power → higher plasma density → more radicals and ions → faster etch.

If different regions have different etch rates (due to ARDE, micro-loading, temperature variation), adjust power locally:

```
Spatially-Resolved Power Control

High-Power Region: Center of wafer
    (naturally slower due to thermal drop)
    → boost with extra power

Low-Power Region: Edge of wafer
    (naturally faster due to better cooling)
    → reduce power

Result: More uniform etch rate across wafer → more uniform scallop profile
```

**Equipment requirement:** Multi-zone RF electrode, each with independent power control. Complex but effective.

---

## Part 4: Trade-Offs and Optimization

### 4.1 Passivation vs. Etch Rate

**Trade-off:**

```
Etch Rate vs. Scallop Control

Etch Rate (nm/min)
    │
500 ├──────────┐ (pure aggressive etch)
    │          │ Bad scallops
400 │          ├──────────────
    │          │
300 │          │ (optimized: passivation + etch balance)
    │          │ Good scallops, reasonable speed
200 │          │
    │          ├──────────────
100 │          │ (pure passivation-heavy, cyclic)
    │          │ Excellent scallops, very slow
  0 └──────────┴──────────
    Scallop Amplitude (nm)
    40        20        10        <5
```

**Design choice for 3D NAND:**
- **Target scallop amplitude:** 10-15 nm (acceptable)
- **Etch rate tolerance:** 100-200 nm/min for deep regions (slow but controlled)
- **Result:** 30-40 minute etch times, but good profile quality

### 4.2 Passivation Film Thickness Optimization

Too thin passivation → inadequate protection, ions penetrate
Too thick passivation → trench narrows, etch rate slows, process time increases

```
Passivation Film Thickness Optimization

Trench Width Loss
    │
 40 ├─────────────────┐ (thick film, too much narrowing)
    │                /│
 20 │              /  │ (optimal: 5-10 nm)
    │            /    │
 10 │          /      │ (thin film, some protection)
    │        /        │
  0 └──────/──────────┴──────────
         0    5    10   15
         Film Thickness (nm)
```

**Selection:** 5-10 nm oxide or CFₓ film provides:
- Effective protection (stops most ions)
- Minimal trench narrowing (only 10-20 nm width loss)
- Reasonable process time (cycling adds minimal overhead)

### 4.3 Cyclic vs. Continuous Approach

**Cyclic (Passivation + Etch):**
- **Advantage:** Excellent scallop control, very smooth sidewalls
- **Disadvantage:** Very slow (adds 50-100% to process time)
- **Use case:** Critical applications where electrical performance is paramount

**Continuous (Chemistry + Pressure Optimization):**
- **Advantage:** Faster, simpler control
- **Disadvantage:** Moderate scallop control (acceptable but not excellent)
- **Use case:** High-volume manufacturing where throughput matters

**Hybrid (Cyclic at critical depths, continuous elsewhere):**
- Cyclic for first 20-30 µm (where scallops are most visible)
- Continuous for final 20-30 µm (where scallops less critical, depth-limited anyway)
- **Result:** Good balance of speed and quality

---

## Part 5: Sidewall Quality and Device Impact

### 5.1 Correlation Between Scalloping and Yield Loss

Empirical data from 3D NAND manufacturing:

```
Scallop Amplitude Impact on Yield

Yield Loss (%)
    │
 30 ├────────────────┐ (severe scallops)
    │               /│
 15 ├──────────────/ │ (moderate scallops)
    │            /   │
  5 ├──────────/─────┤ (acceptable scallops)
    │        /       │
  0 └──────/────────┴──────────
        0  10  20  30  40
        Scallop Amplitude (nm)

    Data: Process qualification on 100+ wafers
    Smooth (A<10nm): 1-2% yield loss (normal process variation)
    Moderate (A=15-25nm): 5-10% loss (noticeable, but recoverable with screening)
    Rough (A>30nm): 15-30% loss (unacceptable, process must be redesigned)
```

### 5.2 Electrical Degradation from Rough Sidewalls

**Leakage current increase:**
- Smooth sidewalls (A<10nm): I_leak baseline (1×)
- Moderate scallops (A=20nm): I_leak ~2-3× baseline
- Severe scallops (A=40nm): I_leak ~5-10× baseline

**Threshold voltage variation:**
- Smooth: ΔV_T < ±50 mV (good uniformity)
- Moderate scallops: ΔV_T ~ ±100-200 mV (some cells slower/faster)
- Severe scallops: ΔV_T > ±300 mV (major distribution broadening)

**Practical impact:** Rough sidewalls create statistical variation in cell behavior → some cells fail electrical tests → yield loss.

### 5.3 Inspection and Metrology

**Post-etch scallop measurement:**

**Technique 1: SEM Cross-Section**
- Direct imaging of sidewall profile
- Measures scallop amplitude and wavelength
- Destructive (sample is destroyed)
- Time-consuming (few samples per lot)

**Technique 2: AFM (Atomic Force Microscopy)**
- Non-destructive surface roughness measurement
- Limited to surface-accessible regions (trenches hard to access)
- Gives RMS roughness, less specific information about scallops

**Technique 3: TEM Cross-Section**
- High-resolution imaging
- Can reveal sub-nm details
- Very destructive and expensive
- Used only for detailed analysis

**Practical quality control:** Use SEM on representative samples (2-4 per wafer lot), measure scallop amplitude, compare to spec (target < 15 nm).

---

## Summary

Sidewall passivation and scallop suppression are critical for achieving electrical specs in 3D NAND:

1. **Scalloping Origins:**
   - Cyclic etch-passivation creates periodic undulations
   - Uneven reactivity creates competing high/low regions
   - Amplitude 10-50 nm typical, wavelength 50-200 nm

2. **Electrical Impact:**
   - Increased capacitance (30-50% for moderate scallops)
   - Increased leakage current (2-10× for severe scallops)
   - Threshold voltage variation (affects yield)

3. **Passivation Strategies:**
   - **Oxide film:** 5-10 nm SiO_x deposited via O₂ plasma
   - **Polymer film:** CFₓ inherent from CF₄ etch chemistry
   - **Cyclic:** Alternate etch/passivation (excellent control, slow)
   - **Continuous:** Chemistry + pressure tuning (faster, moderate control)

4. **Optimization Techniques:**
   - Low-moderate pressure (10-15 Pa) for uniformity
   - Moderate temperature (70-80°C) for controlled etch
   - CHF₃ chemistry for inherent passivation
   - Spatial power modulation for wafer uniformity
   - Hybrid cyclic/continuous approach for balance

5. **Specification and Yield:**
   - Target scallop amplitude: < 10 nm (smooth)
   - Acceptable: 10-20 nm (minor electrical impact)
   - Unacceptable: > 30 nm (significant yield loss)
   - Yield correlation: Rough sidewalls cause 5-30% yield loss

Chapter 14 completes the Process Physics section by addressing **temperature effects on ARDE and selectivity**—the final physics coupling that ties together all previous chapters' insights.

---

**Next:** [Chapter 14: Temperature Effects on Ultra-High Aspect Ratio Etch Performance](14-temperature-effects-on-ultra-high-aspect-ratio-performance.md)
