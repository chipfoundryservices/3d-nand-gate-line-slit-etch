# Chapter 9: Advanced Matching Networks for Deep Trench Stability

## Executive Summary

RF power is delivered to the plasma at 13.56 MHz frequency. The plasma impedance (combination of resistance and reactance) determines how efficiently power is transferred from the RF source to the plasma. During deep trench etch, plasma impedance changes continuously: as trench depth increases, sheath geometry changes, capacitance shifts, and pressure drifts alter impedance unpredictably. **Matching networks** are tunable networks of capacitors and inductors that continuously adjust to maintain impedance match between source (50Ω line) and load (plasma impedance Z_p, which varies with trench geometry and process parameters). This chapter addresses: *How does impedance change during deep trench etch?* *What are matching network topologies?* *How do automatic feedback systems maintain match?* *What power loss occurs from mismatch?* Understanding RF matching is essential for maximizing etch stability and power efficiency in extreme-AR processes.

---

## Part 1: Impedance in Plasma Systems

### 1.1 Plasma as a Load: Resistance and Reactance

The plasma sheath acts as a **capacitor** (two electrode layers separated by low-density region):

```
Electrode 1 (conductive)
    │
    │ Sheath
    │ (low electron density)
    │
    ├── Capacitance C_sheath
    │
Electrode 2 (conductive)
```

**Sheath capacitance:**
$$C_{\text{sheath}} = \epsilon_0 \frac{A}{d_{\text{sheath}}}$$

where:
- A: Electrode area
- d_sheath: Sheath thickness (~1-10 µm)

For typical 300mm wafer (area ~0.07 m²) and 5 µm sheath:

$$C_{\text{sheath}} \approx 8.85 \times 10^{-12} \times \frac{0.07}{5 \times 10^{-6}} \approx 120 \text{ pF}$$

**Plasma resistance** (from ion-neutral collisions and energy dissipation):

$$R_{\text{plasma}} \approx 1-10 \text{ Ω} \times \text{(depends on pressure, power)}$$

**Plasma impedance** (combination of R and C):

$$Z_p = R_p + \frac{1}{j \omega C_p}$$

where ω = 2π × 13.56 MHz.

At 13.56 MHz:
$$\frac{1}{\omega C} = \frac{1}{2\pi \times 13.56 \times 10^6 \times 120 \times 10^{-12}} \approx 97 \text{ Ω}$$

**Total impedance magnitude:**
$$|Z_p| = \sqrt{R_p^2 + X_C^2} \approx \sqrt{5^2 + 97^2} \approx 97 \text{ Ω}$$

**Key insight:** Plasma impedance is primarily **capacitive** (much higher reactance than resistance).

### 1.2 How Impedance Changes During Etch

As etch progresses and trench depth increases:

**Change 1: Sheath thickness changes**
$$d_{\text{sheath}} \propto \sqrt{P} / \sqrt{P + P_{\text{kinetic}})}$$

As pressure increases, sheath thickness decreases → capacitance increases → reactance decreases.

**Change 2: Plasma density changes**
More ions generated → higher conductivity → resistance decreases.

**Change 3: Wafer temperature drifts**
Higher temperature → higher electron temperature → shifts plasma properties.

**Result:** Impedance drifts continuously during the etch:

```
Plasma Impedance Change During Etch (Capacitive Plasma Load)

Impedance Magnitude (Ω)
    │
100 ├─────────────┐
    │  (t=0)      │  Resistance increasing
 80 │             ├───────────
    │             │  Reactance decreasing
 60 │             │
    │             │  Net effect: impedance drifts
 40 │             │
    │             ├───────────
 20 │             │
    │             └──────────── (t=30 min)
  0 └────────────────────────────
    0    10   20   30 (time, min)
```

### 1.3 Reflection and Power Loss from Mismatch

When load impedance (Z_L = Z_p) doesn't match source impedance (Z_s = 50Ω), **reflection** occurs:

**Reflection coefficient:**
$$\Gamma = \frac{Z_L - Z_s}{Z_L + Z_s}$$

**Reflected power:**
$$P_{\text{reflected}} = P_{\text{incident}} \times |\Gamma|^2$$

**Example 1:** Plasma impedance Z_p = 50Ω (perfect match)
$$\Gamma = \frac{50 - 50}{50 + 50} = 0$$
$$P_{\text{reflected}} = 0$$ (all power delivered to plasma)

**Example 2:** Plasma impedance Z_p = 100Ω (capacitive mismatch)
$$\Gamma = \frac{100 - 50}{100 + 50} = \frac{50}{150} = 0.33$$
$$P_{\text{reflected}} = 0.11 \times P_{\text{incident}} = 11\% \text{ (loss)}$$

**Example 3:** Plasma impedance Z_p = 20Ω (severe mismatch)
$$\Gamma = \frac{20 - 50}{20 + 50} = \frac{-30}{70} = -0.43$$
$$P_{\text{reflected}} = 0.18 \times P_{\text{incident}} = 18\% \text{ (severe loss)}$$

**Consequence:** Without matching, 10-20% of RF power is wasted as reflection at any given time. Over long etch (~30 min), total wasted energy is significant.

---

## Part 2: Matching Network Topologies

### 2.1 L-Type Matching Network

The simplest matching network has two reactive elements (L and C):

```
L-Type Matching Network

Source (Z_s = 50Ω)
    ┤
    ├─────┐
    │     │ L (tunable inductor)
    │     │
    ├─────┼──────┐
    │            │ C (tunable capacitor)
    │            │
    └────────────┴──── Plasma Load (Z_L = varying)
```

**Function:** Inductors and capacitors form a network that transforms the plasma impedance toward 50Ω.

**Design equations:** For given Z_p (real and imaginary parts), calculate L and C values that create impedance match.

**Advantages:**
- Simple (only 2 components)
- Fast tuning possible
- Low cost

**Disadvantages:**
- Can only match certain impedance ranges
- If Z_p changes beyond matching range, network cannot adapt
- Not suitable for wide range of impedance variation

### 2.2 Pi-Type Matching Network

More complex network with three components:

```
Pi-Type Matching Network

Source (Z_s = 50Ω)
    ┤
    ├─────┐
    │     │ C1 (tunable capacitor)
    │     │
    ├─────┼─────┐
    │           │ L (tunable inductor)
    │           │
    ├───────────┼─────┐
    │           │ C2  │ (tunable capacitor)
    │           │     │
    └───────────┴─────┴──── Plasma Load (Z_L)
```

**Advantages:**
- More flexible impedance transformation
- Can match wider range of impedances than L-type
- Better for varying loads

**Disadvantages:**
- More complex (3 components)
- More expensive
- Tuning algorithms more complicated

### 2.3 Automatic Matching Networks

Modern chambers use **automated matching networks** that continuously measure impedance and adjust reactances:

**Feedback Loop:**
1. Measure reflected power (via directional coupler)
2. Calculate impedance from reflected power
3. Compute required L and C adjustments
4. Drive stepper motors to adjust variable capacitors/inductors
5. Repeat every 10-100 ms (adjusts faster than process changes)

**Block Diagram:**
```
RF Source (13.56 MHz)
    ↓
Matching Network (L, C tunable)
    ├─ Directional Coupler (measures forward and reflected power)
    │
    ├─ Impedance Calculator (Z = Z0 × √(P_fwd / P_ref))
    │
    ├─ Feedback Controller (compares Z to 50Ω target)
    │
    └─ Stepper Motors (drive variable capacitors)
    ↓
Plasma Load (Z_p, varying)
```

---

## Part 3: Impedance Evolution During Gate Line Slit Etch

### 3.1 Phase 1: Poly Etch (0-5 min, top layer removal)

**Conditions:**
- Trench shallow (< 5 µm)
- High radical density
- High ion flux
- Electrode area fully coupled to plasma

**Impedance evolution:**
- Z_p starts high-impedance (capacitive, 80-120Ω)
- Plasma density increases rapidly
- Sheath thickness decreases
- Impedance drifts toward lower values (80-60Ω)

**Etch rate:** ~300-400 nm/min (fast, well-supplied radicals)

### 3.2 Phase 2: Oxide Etch (5-15 min, middle layers)

**Conditions:**
- Moderate depth (5-30 µm)
- Plasma density adjusts to new trench geometry
- Radical delivery becomes ARDE-limited
- Pressure may be adjusted downward for better penetration

**Impedance evolution:**
- Z_p changes more slowly (plasma equilibration time ~1-2 min)
- Pressure reduction increases impedance (lower plasma density)
- Overall Z_p ~ 60-80Ω (relatively stable)

**Etch rate:** ~150-250 nm/min (slowing due to ARDE)

**Matching network strategy:**
- Fine adjustments to L and C
- Tracking impedance drift to maintain match

### 3.3 Phase 3: Deep Trench Etch (15-30 min, extreme AR)

**Conditions:**
- Very deep (30-50 µm)
- Extreme ARDE effects
- Radical starvation at bottom
- Possible pressure reduction to <10 Pa (improve penetration)

**Impedance evolution:**
- Lower pressure → higher impedance
- Z_p may drift toward 100-120Ω
- Impedance becomes more volatile (small pressure/power changes cause large Z changes)

**Etch rate:** ~20-100 nm/min (slow, ARDE-limited)

**Matching network challenge:**
- Large impedance swings require aggressive tuning
- At extreme pressures (<10 Pa), plasma becomes less stable
- Reflected power can increase to 20-30% (significant loss)

---

## Part 4: Stability and Control Challenges

### 4.1 Pressure Interaction with Impedance

Pressure changes affect impedance through two mechanisms:

**Effect 1: Ion Mean Free Path**
$$\lambda_{\text{ion}} \propto \frac{1}{P}$$

Lower pressure → longer mean free path → less ion-neutral collisions → lower plasma conductivity → higher impedance.

**Effect 2: Plasma Density**
$$n_e \propto P$$

Lower pressure → lower plasma density → lower capacitance → higher reactance → higher impedance.

**Net result:** Impedance increases nonlinearly with decreasing pressure:

```
Impedance vs. Pressure (for fixed power)

Impedance (Ω)
    │
150 ├────────┐
    │        │ (high impedance at low P)
100 ├────────┼──────┐
    │        │      │
 50 ├────────┼──────┼──────┐
    │        │      │      │
  0 └────────┴──────┴──────┴──────
    0   10   20   30   40   50
        Pressure (Pa)
```

### 4.2 Impedance Stability Metrics

Process stability is quantified by how much impedance varies:

**Impedance variation:**
$$\Delta Z = Z_{\text{max}} - Z_{\text{min}} \text{ during etch}$$

**Typical targets:**
- **High stability:** ΔZ < 10Ω (requires excellent pressure control, ±1 Pa)
- **Moderate stability:** ΔZ ~ 20-30Ω (requires good control, ±3-5 Pa)
- **Poor stability:** ΔZ > 50Ω (loose control, significant mismatch periods)

**Power loss from impedance mismatch:**
$$P_{\text{loss}} = P_{\text{delivered}} \times \left|\frac{Z_L - 50}{Z_L + 50}\right|^2$$

For typical Z_L = 70Ω (intermediate):
$$P_{\text{loss}} = P_{\text{delivered}} \times \left|\frac{20}{120}\right|^2 \approx 0.03 \times P_{\text{delivered}} = 3\%$$

For Z_L = 120Ω (high impedance, poor match):
$$P_{\text{loss}} = P_{\text{delivered}} \times \left|\frac{70}{170}\right|^2 \approx 0.17 \times P_{\text{delivered}} = 17\%$$

### 4.3 Adaptive Matching Strategies

**Strategy 1: Continuous Impedance Feedback**
- Measure forward and reflected power continuously
- Compute impedance every 10 ms
- Adjust L and C automatically to minimize reflection
- Typical matching error: ±5Ω (within acceptable range)

**Strategy 2: Predictive Matching**
- Model how impedance will change based on pressure, power, time
- Pre-tune matching network before impedance actually drifts
- Anticipate impedance changes and adjust proactively

**Example:** If pressure is reduced at t=10 min, predicted impedance increase allows matching network to compensate before plasma actually changes.

**Strategy 3: Dual-Frequency Matching**
- Use two RF frequencies simultaneously (13.56 MHz + 2 MHz)
- Each frequency can have different impedance properties
- Provides more flexibility in matching over wider impedance range

---

## Part 5: Integration with Process Control

### 5.1 Matching Network as Diagnostic Tool

The impedance calculation provides **real-time diagnostic information**:

**Measurement 1: Plasma Density**
Impedance is proportional to plasma density → impedance changes indicate plasma density drifts.

**Application:** If impedance suddenly drops (plasma density spike), it signals:
- Increased power delivery (check RF source)
- Sudden pressure increase (check pump/flow)
- Electrode condition change (check for contamination)

**Measurement 2: Sheath Stability**
Rapid impedance fluctuations indicate sheath instability → signals potential charging problems.

**Application:** If impedance oscillates at >1 Hz (fast), floating gate charging may be occurring.

**Measurement 3: Etch Progress**
Impedance slowly drifts during etch due to geometry changes → can estimate etch depth!

**Application:** Optical endpoint detection may fail (e.g., optical signal noisy), but impedance-based endpoint can serve as backup.

### 5.2 Coupled Control: Pressure + Power + Matching

Advanced chambers link three control systems:

```
Coupled Control System for Deep Trench Etch

Process Control (Chapter 7):
  - Adjust pressure dynamically (high early, low at depth)
  - Adjust power to maintain etch rate
  
    ↓

Impedance Monitoring (this chapter):
  - Measure Z_p continuously
  - Calculate required L and C adjustments
  - Drive matching network

    ↓

Endpoint Detection (Chapter 18):
  - Combine optical endpoint + impedance signal
  - More robust endpoint identification
  - Lower false-positive/negative rate
```

**Benefit:** Coupling these systems creates a **robust, self-correcting process** that compensates for equipment drift and wafer-to-wafer variation.

---

## Summary

Advanced RF matching networks are essential for stable 3D NAND gate line slit etch:

1. **Impedance Physics:**
   - Plasma impedance is primarily capacitive (~100Ω, mostly reactance)
   - Impedance drifts 10-50Ω during etch as sheath geometry and plasma density change
   - Mismatch causes 5-20% power loss (significant over long etch times)

2. **Matching Network Topologies:**
   - **L-type:** Simple (2 components), limited range
   - **Pi-type:** Flexible (3 components), wider range
   - **Automatic:** Continuous feedback, adjusts every 10-100 ms

3. **Impedance Evolution During Gate Line Slit:**
   - **Poly etch (0-5 min):** 80-120Ω, relatively stable
   - **Oxide etch (5-15 min):** 60-80Ω, slow drift
   - **Deep trench (15-30 min):** 100-150Ω, volatile if pressure very low

4. **Stability and Control:**
   - Pressure reduction required for deep penetration → increases impedance volatility
   - Impedance variation ΔZ < 10Ω requires tight pressure control (±1 Pa)
   - Adaptive matching reduces power loss to <5% even with impedance drift

5. **Integration with Process Control:**
   - Impedance as diagnostic (plasma density, sheath stability, etch progress)
   - Coupled pressure + power + matching control for robust operation
   - Impedance-based endpoint detection as backup to optical methods

Chapters 10-14 shift focus from chamber design to **process physics and precision control** of etch mechanisms (ARDE, ion energy, selectivity, sidewall passivation, temperature). The foundation laid in Chapters 5-9 enables the advanced control strategies discussed in later chapters.

---

**Next:** [Chapter 10: Extreme ARDE Physics](10-extreme-arde-physics.md) [already completed]
