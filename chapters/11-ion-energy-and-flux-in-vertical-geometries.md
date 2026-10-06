# Chapter 11: Ion Energy and Flux in Vertical Geometries

## Executive Summary

In conventional planar etch, ions approach the wafer nearly perpendicular to the surface, with relatively uniform energy distribution. In 3D NAND gate line slit etch (AR > 500:1), ions enter deep narrow trenches and their trajectories become **ballistic**—they travel in straight lines with minimal scattering, and many are **shadowed** by trench walls. This chapter addresses ion behavior in vertical geometries: *How do ion trajectories differ from planar?* *What is the effective ion flux reaching the trench bottom?* *How does ion energy vary with depth?* *What sidewall damage results from ion scattering?* Understanding ion dynamics in deep trenches is essential for controlling ARDE (Chapter 10), managing damage (Chapter 4), and optimizing selectivity (Chapter 12).

---

## Part 1: Ion Trajectory Physics in Deep Trenches

### 1.1 Ballistic vs. Diffusive Ion Motion

**In planar etch (AR < 5:1):**
- Ion mean free path λ ~ 1-10 cm (very long compared to feature size)
- Ions scatter weakly in the sheath region
- Most ions reach wafer with energies within 20-30% of sheath voltage
- Ion approach angle: nearly perpendicular to surface (±20°)

**In deep trenches (AR > 500:1):**
- Ions still have λ ~ 1-10 cm (unchanged)
- But trench width is 10-30 nm (million times smaller)
- Ions travel **ballistically**—in straight lines from showerhead through trench to bottom
- Ion approach angle **varies dramatically** depending on entry position

### 1.2 Ion Trajectory Geometry

Consider an ion entering a deep trench:

```
Ion Trajectory in Deep Trench

Showerhead (plasma generation region)
    │
    │ Ions flowing downward and slightly scattered
    │
Top of Trench Opening (20 nm wide)
    │
    │ ← Ion enters on left side
    ║
    ║ Ion travels downward + slight angle toward center
    ║
    ║ → Ion may hit right sidewall
    ║
    ║ (OR) Ion reaches bottom if trajectory is centered
    ║
    ║
Bottom of Trench (50 µm deep)
```

**Key insight:** For a 20 nm wide trench and sheath angle ~5-10°, ion trajectories can **significantly deviate**:

```
Angle Deviation Calculation

Ion enters at angle θ = 5° from vertical
After traveling 50 µm vertically:
Horizontal displacement = 50 µm × tan(5°) = 50 µm × 0.087 = 4.4 µm

This is 220× the trench width!
Conclusion: Ion will hit sidewall, not reach bottom
```

**Consequence:** Only ions entering **near the centerline** of the trench (within 1-2 µm horizontal) reach the bottom. Off-center ions hit sidewalls.

### 1.3 Ion Flux Distribution in Trench

The effective ion flux reaching the trench bottom is a small fraction of the total ion flux:

**Total ion flux from plasma:** ~10¹¹ ions/cm²/s (area-averaged across showerhead)

**Effective flux to trench bottom:**

$$\Phi_{\text{bottom}} = \Phi_{\text{total}} \times \frac{A_{\text{centerline}}}{A_{\text{opening}}}$$

where:
- A_centerline: Area of the "acceptance cone" (ions that can reach bottom)
- A_opening: Total trench opening area

For a 20 nm wide trench:
- Acceptance cone width: ~2-3 nm (ions within ±1-1.5 nm of centerline)
- Opening width: 20 nm
- **Flux reduction factor:** (3 nm / 20 nm) ≈ **15% of total flux**

**Consequence:** Even with high total ion flux, the flux **reaching the trench bottom is severely reduced** by geometric shadowing.

---

## Part 2: Ion Energy Distribution in Deep Trenches

### 2.1 Energy Loss During Transit

Ions accelerated through the sheath reach ~100-200 eV by the time they enter the trench opening. As they travel through the trench, they can collide with gas molecules and lose energy:

**Collision probability:**

$$P_{\text{collision}} = \frac{L}{\lambda_{\text{ion}}}$$

where L is trench depth and λ_ion is ion mean free path.

For L = 50 µm and λ_ion = 1 cm:

$$P_{\text{collision}} = \frac{50 \times 10^{-6}}{0.01} = 0.005 = 0.5\%$$

**Conclusion:** Only ~0.5% of ions collide during transit through trench. Most ions reach the bottom with **minimal energy loss** (~2-5% energy loss on average).

### 2.2 Energy Distribution Width

While average energy loss is small, the **distribution** of ion energies at trench bottom is broader than at the opening:

```
Ion Energy Distribution

At Trench Opening:
    Energy (eV)
        │
    200 ├─────────────┐  (tight distribution, ±10eV)
        │      ▂▄▆▄▂ │
    150 │   ▂▆    ▆▂ │
        │▂▆           ├─ Mean: 180 eV
        └─────────────┘

At Trench Bottom (50 µm deep):
    Energy (eV)
        │
    200 ├─────────────┐  (broader, ±40eV)
        │    ▂▆▄▂    │
    150 │  ▂    ▆▂   │
        │ ▂      ▆   ├─ Mean: 175 eV
    100 │▂        ▆▂ │  (some ions lost significant energy)
        └─────────────┘
```

**Physical reason:** Ions with different trajectories spend different amounts of time in the plasma region. Those that take longer paths collect more energy; those that take short paths collect less.

### 2.3 Impact Energy and Ion-Assisted Etch Rate

Etch rate depends on ion energy via:

$$R_{\text{etch}} = R_{\text{radical}} \times \left(1 + \alpha \times E_{\text{ion}}\right)$$

where:
- R_radical: Etch rate from radicals alone
- α: Ion-assist coefficient (~0.01-0.1 eV⁻¹)
- E_ion: Ion energy (eV)

**Example calculation:**
- R_radical = 50 nm/min (chemical etch from F radicals)
- α = 0.05 eV⁻¹
- E_ion at top = 180 eV: R_top = 50 × (1 + 0.05 × 180) = 50 × (1 + 9) = 500 nm/min
- E_ion at bottom = 175 eV: R_bottom = 50 × (1 + 0.05 × 175) = 50 × (1 + 8.75) = 487 nm/min

**Difference:** ~2.6% reduction in etch rate despite only 2.7% energy loss. The **exponential dependence** means small energy changes have measurable effects.

---

## Part 3: Ion Scattering and Sidewall Bombardment

### 3.1 Ion Collisions with Sidewalls

Off-center ions hit sidewalls. When an ion hits a sidewall:

**Outcome 1: Specular Reflection** (~30% of collisions)
Ion bounces elastically off sidewall and continues toward bottom:
- Energy loss: < 5%
- Trajectory altered: angle changes by ~10-20°
- May hit opposite sidewall

**Outcome 2: Inelastic Collision** (~50% of collisions)
Ion loses energy through inelastic processes (excitation, ionization):
- Energy loss: 10-30 eV per collision
- Ion is deflected and may escape trench
- Contributes to sidewall erosion

**Outcome 3: Charge Exchange** (~20% of collisions)
Ion picks up electron from sidewall material, becomes neutral:
- Energy loss: Significant (atom retains kinetic energy but loses electrical charge)
- Neutral atom continues as radical (no longer contributes to ion-assisted etch)
- Contributes to sidewall sputtering

**Consequence:** Each ion-sidewall collision represents **lost ion-assisted etch at bottom** and **gained sidewall damage**.

### 3.2 Sidewall Damage from Ion Bombardment

Sidewalls are exposed to ions at various angles and energies:

**Sidewall erosion rate:**

For a 20 nm wide trench, sidewalls have ~2500× the area of the trench opening:
```
Trench Geometry (50 µm deep, 20 nm wide):
    Opening area: 20 nm × (width perpendicular to page, assume 100 nm) = 2,000 nm²
    Sidewall area: 2 × (50 µm) × (100 nm) = 2 × 5×10⁻³ mm × 100 nm = 1×10⁻³ mm² = 1×10⁷ nm²
    
    Sidewall area / Opening area = 1×10⁷ / 2,000 = 5,000×
```

If ions scatter into sidewalls **5,000× more area** than the opening, and each ion contributes sputtering, the sidewall erosion can be **severe**:

**Sidewall material loss:** 
- Opening: ions at 180 eV, flux ~10¹¹ ions/cm²/s, sputtering yield ~0.3 atoms/ion
- Sidewall: ions at 50-150 eV (scattered), flux ~10¹⁰ ions/cm²/s (due to scattering), sputtering yield ~0.1-0.2 atoms/ion
- Sidewall erosion: ~0.1-0.2 nm/min (much slower than opening, but cumulative over long etch)

**Consequence:** Over a 30-minute etch, sidewall erosion can be 3-6 nm—significant for narrow trenches.

---

## Part 4: Energy Dependence of Key Etch Processes

### 4.1 Ion-Assisted Chemical Etch

The enhancement factor depends on ion energy:

$$R(E) = R_0 \times \left[1 + \beta \times (E - E_{\text{threshold}})\right]$$

where:
- E_threshold: Minimum ion energy to assist etch (typically 10-20 eV)
- β: Ion-assist strength (~0.001-0.01 eV⁻¹)

```
Etch Rate vs. Ion Energy

Etch Rate (nm/min)
    │
500 ├─────────────┐
    │            /│  (etch rate increases linearly with E above threshold)
400 │          /  │
    │        /    │
300 │      /      │  (slope = β)
    │    /        │
200 ├──/──────────┤ E_threshold ≈ 20 eV
    │/            │
100 │             │
    │             
  0 └─────────────┴──────────────
    0   50   100  150  200
        Ion Energy (eV)
```

**Consequence:** Lower ion energy → less ion-assisted etch → slower total rate (more reliance on radicals).

### 4.2 Damage from Ion Impact

Gate oxide damage (Chapter 4) depends on ion energy:

**Damage threshold:** Ions below ~20 eV cause minimal damage (no breaking of oxide bonds)

**Damage rate above threshold:**

$$N_{\text{defects}} = Y(E) \times \Phi_{\text{ions}} \times t$$

where Y(E) is defect creation yield per ion (depends on E).

```
Defect Creation Yield vs. Ion Energy

Yield (defects/ion)
    │
0.1 ├─────────────────┐
    │                /│  (yield increases with E)
0.05├─────────────────┤
    │              /  │
    │          /      │
  0 ├──────────────────┤
    │                  │
    └───────────────────┴──────────
    0   50   100  150  200
        Ion Energy (eV)

    20 eV threshold: Below this, minimal damage
    >100 eV: Significant defect creation
```

**Consequence:** Higher ion energy → more damage to floating gates. This conflicts with the etch-rate advantage of high ion energy.

---

## Part 5: Practical Ion Energy and Flux Control

### 5.1 Ion Energy Tuning via Pressure and Power

From Chapter 7, we know that pressure and power affect plasma properties, which in turn affect sheath voltage (and thus ion energy):

**Ion energy scaling:**

$$E_{\text{ion}} \approx eV_{\text{sheath}} = e \times V_{\text{RF}} \times \frac{n_e}{n_e + n_i}$$

**Pressure effect:**
- **Increase pressure:** Higher plasma density → lower sheath voltage → **lower ion energy** (50-100 eV at high P)
- **Decrease pressure:** Lower plasma density → higher sheath voltage → **higher ion energy** (150-200 eV at low P)

**Power effect:**
- **Increase power:** More plasma generation → higher ion density → but also can increase sheath voltage (competing effects)
- **Typical result:** Power increase slightly increases ion energy (~10 eV per 100W increase)

### 5.2 Ion Flux Control

Ion flux to trench bottom is limited by:

1. **Geometric shadowing:** Only ~15% of total ion flux reaches bottom
2. **Pressure:** Higher pressure → higher ion density, but shorter mean free path → less ballistic transport
3. **Electrode design:** Dome-shaped electrodes → better directional focusing → higher effective flux
4. **Remote plasma sources:** Lower ion density but less scattering damage

**Trade-off analysis:**

| Strategy | Ion Flux Bottom | Ion Energy | Damage Risk | Etch Rate |
|----------|-----------------|-----------|-------------|-----------|
| **High P, Low W** | Moderate | Low (50 eV) | Very Low | Slow |
| **Medium P, Medium W** | Good | Medium (100 eV) | Moderate | Good |
| **Low P, High W** | Low (flux decreases at low P) | High (150 eV) | High | Moderate |
| **Remote Plasma** | Moderate | Very Low (20 eV) | Very Low | Slow |

### 5.3 Ion Flux and Selectivity

Different materials etch at different rates depending on ion energy:

**Silicon etch rate vs. ion energy:**
$$R_{\text{Si}}(E) = 10 + 2 \times (E - 20) \text{ nm/min (for } E > 20 \text{ eV)}$$

**Oxide etch rate vs. ion energy:**
$$R_{\text{SiO}_2}(E) = 5 + 0.5 \times (E - 20) \text{ nm/min (for } E > 20 \text{ eV)}$$

**Selectivity:**
$$S = \frac{R_{\text{Si}}}{R_{\text{SiO}_2}} = \frac{10 + 2(E-20)}{5 + 0.5(E-20)}$$

**Example calculations:**
- At E = 50 eV: S = (10+60)/(5+15) = 70/20 = 3.5:1
- At E = 100 eV: S = (10+160)/(5+40) = 170/45 = 3.8:1
- At E = 150 eV: S = (10+260)/(5+65) = 270/70 = 3.9:1

**Observation:** Selectivity actually **improves slightly at higher ion energy** (because Si etch gets more boost than oxide from ion assistance).

---

## Part 6: Ion Energy Effects on ARDE

### 6.1 Ion-Limited vs. Radical-Limited Regimes

**At high ion energy (>100 eV):**
- Ion-assisted etch dominates
- Bottom of trench receives some ion flux (even if scattered)
- ARDE is partially mitigated by ion-assisted boost at bottom

**At low ion energy (<50 eV):**
- Radical chemical etch dominates
- Bottom receives no ion boost
- ARDE is severe (bottom starved of radicals, no ion help)

### 6.2 ARDE Factor vs. Ion Energy

```
ARDE Factor vs. Ion Energy

ARDE Factor (depth_top / depth_bottom)
    │
 20 ├─────────────────┐
    │ (radical-limited, no ion help at bottom)
 10 ├─────────────────┤
    │               /─┘
    │             /
  5 ├──────────/─────┤
    │       /       │ (ion-assisted provides boost at bottom)
  2 ├─────/─────────┤
    │   /           │
  1 └─/─────────────┴──────────
    0   50   100  150  200
        Ion Energy (eV)

    At 20 eV: ARDE ~15:1 (severe)
    At 100 eV: ARDE ~3:1 (moderate)
    At 150 eV: ARDE ~2:1 (good)
```

**Optimization strategy:** Use **moderate ion energy (80-120 eV)** to balance:
- Good ARDE control (ion-assisted boost at bottom helps uniformity)
- Acceptable damage (not so high as to rupture oxide)
- Reasonable etch rate

---

## Summary

Ion behavior in vertical geometries is fundamentally different from planar etch:

1. **Ballistic Transport:**
   - Ions travel in straight lines through deep trenches
   - Only ions entering near centerline reach bottom (15% geometric efficiency)
   - Off-center ions hit sidewalls and scatter

2. **Energy Distribution:**
   - Minimal energy loss during transit (0.5% collision probability)
   - But broader energy distribution at trench bottom than at opening
   - Energy variation: 175-185 eV (range ~10 eV)

3. **Sidewall Bombardment:**
   - Ions hitting sidewalls cause erosion and defect creation
   - 5000× more sidewall area than trench opening
   - Sidewall damage competing effect with bottom etch

4. **Ion Energy Effects:**
   - Low E (<50 eV): Good for damage control, poor for ARDE
   - High E (>150 eV): Excellent ARDE, poor for damage control
   - Optimal: 80-120 eV (balance between etch rate, uniformity, and damage)

5. **Control Strategies:**
   - **Pressure:** Primary lever (high P → low E, good damage control)
   - **Power:** Secondary lever (high W → slightly higher E)
   - **Electrode design:** Affects ion directionality and flux distribution
   - **Remote plasma:** Lowest damage but slowest etch

6. **Selectivity Coupling:**
   - Ion energy slightly improves Si/SiO₂ selectivity
   - Effect modest (selectivity ~3.5-3.9:1 across reasonable E range)
   - Ion energy tuning is more about ARDE and damage than selectivity precision

Chapters 12-14 build on ion dynamics by addressing **precise selectivity control, sidewall passivation (mitigating ion damage), and thermal effects** that couple with ion energy to create the complete process environment.

---

**Next:** [Chapter 12: Selectivity Mechanisms in Multi-Layer Stacks](12-selectivity-mechanisms-in-multi-layer-stacks.md)
