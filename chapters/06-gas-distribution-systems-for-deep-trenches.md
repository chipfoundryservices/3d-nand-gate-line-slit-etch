# Chapter 6: Gas Distribution Systems for Deep Trenches

## Executive Summary

Radical species (Cl, F atoms) are the primary etchants in gate line slit etch. Unlike ions (which are accelerated by electric fields), radicals are neutral and transport by diffusion and bulk gas flow. In conventional shallow trenches (AR < 50:1), radicals easily reach the bottom. In deep trenches (AR > 500:1), radicals are consumed by sidewall reactions and rarely penetrate to depth. This chapter addresses gas distribution engineering: *How do we deliver sufficient radical flux to the trench bottom?* *What showerhead geometries maximize penetration?* *How do pressure and temperature affect radical transport?* Understanding gas distribution is prerequisite to process window optimization (Chapter 7), chamber passivation (Chapter 8), and ARDE compensation strategies (Chapter 10).

---

## Part 1: Radical Species Transport in Plasma Chambers

### 1.1 Sources of Radicals

In a fluorine-based plasma (e.g., CF₄ + Ar), radicals are generated via:

**Generation Mechanism 1: Electron Impact Dissociation**
$$e^- + \text{CF}_4 \rightarrow e^- + \text{CF}_3 + \text{F}$$

Energetic electrons (T_e ~ 2-3 eV) dissociate CF₄ into CF₃ radicals and atomic fluorine.

**Generation Mechanism 2: Ion Impact Dissociation**
$$\text{Ar}^+ + \text{CF}_4 \rightarrow \text{Ar} + \text{CF}_3 + \text{F}$$

Ions (especially Ar⁺) collide with CF₄ molecules, fragmenting them.

**Generation Mechanism 3: Radical-Molecule Reactions**
$$\text{F} + \text{CF}_4 \rightarrow \text{CF}_3 + \text{F}_2$$

Atomic fluorine reacts with CF₄ to produce more F atoms (chain reaction).

**Result:** Plasma generates a **steady-state radical density**:
$$n_{\text{F}} \approx 10^{13} \text{ cm}^{-3}$$

This is much higher than ion density (~10¹⁰ cm⁻³) because radicals are more stable against recombination than ions.

### 1.2 Radical Lifetime and Diffusion

Radicals are not stable indefinitely. They recombine on surfaces and in the gas phase:

**Surface Recombination:**
$$2\text{F} \rightarrow \text{F}_2 \text{ (on chamber wall or electrode surface)}$$

**Gas-Phase Recombination:**
$$2\text{F} + \text{M} \rightarrow \text{F}_2 + \text{M}$$

where M is a third body (Ar atom, CF₄ molecule, etc.)

**Characteristic lifetime:** τ ~ 10-100 ms (in 10-50 Pa pressure regime)

**Radical diffusion distance:**
$$L_{\text{diffusion}} = \sqrt{D \tau}$$

where D is diffusion coefficient (~0.1-1 cm²/s at low pressure).

For typical conditions:
$$L_{\text{diffusion}} \approx \sqrt{0.5 \text{ cm}^2/\text{s} \times 50 \text{ ms}} \approx 15 \text{ cm}$$

**This seems to suggest radicals can diffuse very far!** But there's a critical catch: radicals react with **any surface they encounter**. They don't diffuse 15 cm through free space; they react with the **first surface** they hit (chamber wall, electrode, wafer, or trench sidewall).

### 1.3 Radical Flux to Trench Bottom

The radical flux reaching the trench bottom depends on:

1. **Generation rate in plasma above trench opening**
2. **Diffusion into trench** (consumed by sidewall reactions)
3. **Survival probability** (what fraction avoid reacting on sidewalls)

**Simple model:**

For a deep trench (depth L, width W):

$$\Phi_{\text{bottom}} = \Phi_{\text{source}} \times e^{-L/L_{\text{eff}}}$$

where **L_eff** is the effective diffusion length, accounting for sidewall reactions:

$$L_{\text{eff}} \approx \frac{W}{2} \times \frac{v_{\text{thermal}}}{v_{\text{reactive}}}$$

**Physical interpretation:**
- Radicals enter trench with thermal velocity v_thermal ~ √(3kT/m)
- They react on sidewalls with reaction velocity v_reactive (related to sticking coefficient)
- If v_reactive << v_thermal, radicals pass through without reacting (good for deep penetration)
- If v_reactive ≈ v_thermal, radicals react immediately on first contact (poor penetration)

**For typical F radicals on Si/SiO₂:**
- v_thermal ~ 10⁵ cm/s
- v_reactive ~ 10⁴-10⁵ cm/s (high reactivity)
- **L_eff ~ W/2 to W** (effective diffusion length comparable to trench width)

**Consequence:**
- For W = 20 nm trench: L_eff ~ 10-20 nm
- Trench depth L = 50 µm = 50,000 nm
- **Penetration factor: exp(-50,000 / 15) ≈ exp(-3,300) ≈ 10⁻¹⁴³³ (essentially zero)**

This extreme AR effect means **radicals cannot reach the bottom of deep trenches via diffusion alone.**

---

## Part 2: Showerhead Design for Radical Delivery

### 2.1 What is a Showerhead?

The **showerhead** (also called "nozzle" or "gas distribution plate") is the perforated plate or electrode through which gas flows into the plasma chamber.

```
Cross-Section of Showerhead

    Gas inlet from mass flow controller
        ↓
    [Manifold (large volume, distributes gas)]
        │
        │
    [Showerhead plate with ~100-1000 holes]
        │
        ↓↓↓ (gas flows downward through holes)
        ↓↓↓
    [Plasma region]
        ↓
    [Wafer with trenches]
```

**Functions of showerhead:**
1. **Distribute gas uniformly** across wafer (prevent hot spots with high local gas density)
2. **Maintain pressure** (balance inflow with pumping)
3. **Create radical species** (plasma generation region immediately below showerhead)

### 2.2 Hole Density and Gas Distribution Uniformity

The showerhead's hole pattern affects gas distribution:

**High hole density (many small holes):**
- Gas exits showerhead with low velocity
- More uniform distribution (gas spreads out before reaching plasma)
- Risk: gas clogging (dust particles can block small holes)

**Low hole density (fewer large holes):**
- Gas exits with high velocity
- Less uniform distribution (localized high-pressure regions)
- Benefit: resistant to clogging

**Typical showerhead design:**
- **Hole diameter:** 2-5 mm
- **Hole density:** 50-200 holes per 300mm wafer (~0.05-0.2 holes/mm²)
- **Gas velocity exiting showerhead:** 1-10 m/s

### 2.3 Pressure Drop Across Showerhead

Gas flowing through showerhead holes experiences pressure drop:

$$\Delta P = \rho v^2 / (2 C_d)$$

where:
- **ρ:** Gas density
- **v:** Gas velocity through holes
- **C_d:** Discharge coefficient (~0.6-0.8)

For typical CF₄ flow (500 sccm at 20 Pa):
- **Pressure upstream (manifold):** ~50 Pa
- **Pressure drop across holes:** ~10-20 Pa
- **Pressure downstream (plasma region):** ~20-30 Pa

**Trade-off:** Larger pressure drop improves uniformity (slows gas) but requires higher source pressure (expensive).

### 2.4 Showerhead Geometry Effects on Radical Delivery

The showerhead geometry affects radical generation location:

#### Showerhead Type 1: Remote Plasma Showerhead
Plasma is generated **in the showerhead itself** (high pressure region with high RF power density).

```
                RF Electrode
                    │
                    ↓
            [Remote Plasma Region]
                    │
    [Radicals generated here, then transported downward]
                    │
            [Showerhead plate]
                    ↓↓↓
            [Low-pressure etch region]
                    ↓
                [Wafer]
```

**Advantage:** Radicals are generated upstream → can transport to plasma region below showerhead  
**Disadvantage:** Some radicals recombine before reaching wafer; lower efficiency

#### Showerhead Type 2: Direct Plasma Showerhead
Plasma extends up to the showerhead (no separation).

```
            [Showerhead = Electrode]
                    │
                    ↓
            [Plasma region extends here]
                    │
                [Radicals generated throughout plasma]
                    ↓
                [Wafer]
```

**Advantage:** Maximum radical generation near wafer → better for deep trenches  
**Disadvantage:** Floating gate exposure to high-energy region (damage risk)

### 2.5 Gas Composition Effects

Different gas mixtures produce different radical species with different transport properties:

| Gas | Radical | Reactivity | Diffusion Length |
|-----|---------|-----------|------------------|
| **CF₄** | F, CF₃ | Very high | Very short (~W/2) |
| **CHF₃** | F, CF₂H | Moderate-high | Short (~W) |
| **C₂F₆** | F, CF₃, C₂F₅ | Moderate | Medium (~2W) |
| **SF₆** | F | High | Very short |

**Trade-off:** High reactivity → fast etch rate but poor deep penetration; lower reactivity → slower etch but better penetration.

**Strategy:** Use **gas mixtures** to balance speed and penetration:
- **For top of trench:** CF₄ (reactive, fast)
- **For middle/bottom:** Shift toward CHF₃ or C₂F₆ (less reactive, better penetration)

---

## Part 3: Bulk Gas Flow Effects

### 3.1 Pumping and Flow Dynamics

The chamber is pumped at the bottom via a **turbomolecular pump** (removes gas at ~100-1000 L/min).

**Gas balance:**
$$\text{Inflow (from showerhead)} = \text{Pumping (from pump)} + \text{Deposition (on wafer)}$$

**Pressure regulation:**
$$P = \frac{\text{Gas flow rate}}{C}$$

where C is the **conductance** (depends on pump size and chamber geometry).

```
Pressure Regulation in Chamber

Pressure (Pa)
    │
 50 ├─────────┐
    │         │ (high inflow)
 30 ├─────────┼─────────┐
    │         │         │ (moderate inflow)
 10 │         │         ├─────────
    │         │         │
  0 └─────────┴─────────┴──────────
      0      500    1000   1500
      Gas flow rate (sccm)

Higher flow → Higher pressure (until pump limits)
```

### 3.2 Radicals Transport by Bulk Flow

While diffusion is poor in deep trenches, **bulk gas flow** can transport radicals:

**Bulk flow velocity:**
$$v_{\text{bulk}} \approx \text{Gas flow rate} / \text{Chamber cross-section} \approx 0.1-1 \text{ m/s}$$

**Time for bulk flow to traverse chamber height (10cm):**
$$t_{\text{transit}} \approx 0.1 \text{ m} / 0.1 \text{ m/s} = 1 \text{ s}$$

**Radicals that enter trench via bulk flow experience directed transport (not random diffusion).**

**Benefit:** Radicals can be "swept" into trenches by gas flow, bypassing some sidewall consumption.

**Mechanism:**
1. Radicals generated above trench opening
2. Gas flow carries them toward pump (downward)
3. Trenches act as "sinks" that capture radicals (low resistance to flow)
4. Radicals flowing toward pump are partially intercepted by trenches

### 3.3 Trench as Flow Resistor

A deep trench creates **high resistance to gas flow**:

**Flow resistance of trench:**
$$R_{\text{trench}} = \frac{L}{A} \times \eta_{\text{viscosity}}$$

where:
- L: Trench depth
- A: Trench cross-sectional area
- η: Gas viscosity

For a 50 µm deep, 20 nm wide trench:
$$R_{\text{trench}} \propto \frac{50 \text{ µm}}{20 \text{ nm} \times 20 \text{ nm}} = \frac{50,000 \text{ nm}}{400 \text{ nm}^2} \text{ (very high)}$$

**Consequence:** Gas preferentially flows through **open areas** rather than into trenches. Trenches receive minimal gas flow → minimal bulk-flow-driven radical delivery.

**Mitigation:** Lower pressure → higher Knudsen number → more molecule-wall collisions → gas behavior transitions from laminar to molecular flow → gas molecules explore trenches more thoroughly.

---

## Part 4: Radical-Starved Regime in Deep Trenches

### 4.1 ARDE Revisited: Radical Starvation

Combining diffusion-limited and flow-limited delivery:

**At shallow depth (0-10 µm):**
- Abundant radical supply from above
- High etch rate
- Minimal ARDE (uniform delivery)

**At intermediate depth (20-40 µm):**
- Declining radical supply (consumed by sidewalls)
- Etch rate drops
- ARDE begins (top faster than bottom)

**At deep depth (40-100 µm):**
- Severe radical depletion (few survive sidewall journey)
- Etch rate very low (radical-limited)
- Extreme ARDE (top rate >> bottom rate)

**Etch rate profile:**

```
Etch Rate vs. Depth (ARDE due to Radical Starvation)

Etch Rate (nm/min)
    │
300 ├─ ─ ─ ─ (initial rate at top)
    │  (high radical supply)
200 ├─ ─ ─ ─ ─ ─ ┐
    │             │ (declining supply)
100 │             ├─ ─ ─ ─ ┐
    │             │         │ (severe depletion)
 20 │             │         ├─ ─ ─ ─ ─ ─ ─
    │             │         │
  0 └─────────────┴─────────┴───────────
    0    10   20   30   40   50 (depth, µm)

Aspect Ratio Effect:
    Top to bottom ratio: 300/20 = 15:1 (severe ARDE)
```

### 4.2 Radical Depletion Model

A quantitative model for radical consumption:

**Local radical density** as function of depth:

$$n_r(z) = n_{r,0} \cdot e^{-z/L_{\text{cons}}}$$

where:
- **n_{r,0}:** Radical density at trench opening
- **L_cons:** Consumption length (how far radicals penetrate before consumed)

For typical Si etch in CF₄ plasma:
$$L_{\text{cons}} \approx 5-20 \text{ µm}$$

**Etch rate at depth z:**

$$R(z) \propto n_r(z) = R_0 \cdot e^{-z/L_{\text{cons}}}$$

**Example:** If L_cons = 10 µm and trench depth is 50 µm:

$$R(50 \text{ µm}) / R(0) = e^{-50/10} = e^{-5} \approx 0.007 = 0.7\%$$

Etch rate at 50 µm depth is **less than 1% of initial rate.**

---

## Part 5: Strategies for Improved Radical Delivery

### 5.1 Pressure Reduction

**Lower pressure → Increase mean free path → Radicals travel farther before hitting sidewalls.**

**Effect of pressure on ARDE:**

```
Pressure (Pa) | Mean Free Path (µm) | L_cons (µm) | ARDE (50µm slit) |
--------------|--------------------|-------------|------------------|
100           | 0.1                 | 5           | 200:1 (terrible)  |
50            | 0.2                 | 8           | 50:1 (severe)     |
10            | 1                   | 15          | 5:1 (moderate)    |
5             | 2                   | 25          | 1:1 (ideal)       |
```

**Trade-off:** Lower pressure → longer mean free path → better ARDE, but:
- Slower etch rate (lower radical density overall)
- Reduced ion generation → lower ion-assisted etch
- Chamber design becomes more critical (uniform showerhead essential)

**Typical 3D NAND practice:** 10-20 Pa (compromise between penetration and speed)

### 5.2 Temperature Reduction

**Lower temperature → Slower radical recombination → Longer radical lifetime → Better penetration.**

**Effect on radical lifetime:**

$$\tau \propto T^{-0.5}$$

Lowering temperature from 100°C to 50°C increases lifetime by ~30% → slightly better penetration.

**Cryogenic processes** (T < -50°C) can achieve much better radical penetration, but:
- Require expensive cryogenic systems
- Thermal stress on equipment
- Potential condensation issues
- Not yet mainstream for 3D NAND gate line slits

### 5.3 Gas Mixture Optimization

**Use gas mixtures with different reactivities:**

```
Standard Recipe (CF₄ only):
    Stage 1 (top 10 µm):  CF₄/Ar (fast, reactive)
    Stage 2 (middle):     CF₄/Ar (same chemistry, etch slows due to radical depletion)
    Stage 3 (bottom):     CF₄/Ar (very slow due to starvation)

Optimized Recipe (variable chemistry):
    Stage 1 (top 10 µm):     CF₄/Ar (fast, reactive)
    Stage 2 (middle 20 µm):  CHF₃/CF₄ (moderate, better penetration)
    Stage 3 (bottom 20 µm):  CHF₃/Ar (less reactive, longest penetration)
```

**Result:** More uniform etch rate across depth (reduced ARDE).

### 5.4 Cyclic Etch-Passivation Approach

Instead of continuous etch, use repeated cycles:

```
Cycle 1: Etch (2 sec)     → Remove material uniformly at all depths
         Passivate (1 sec) → Deposit protective film on sidewalls

Cycle 2: Etch (2 sec)      → Remove material again
         Passivate (1 sec) → Re-deposit passivation

Repeat 10-50 cycles until trench is complete
```

**Mechanism:**
- **Etch step:** Radicals attack surface at all depths (even bottom, where depletion would make etch slow)
- **Passivate step:** Deposit thin film (carbon, oxygen-based) on all surfaces
- **Next etch step:** Sidewalls are protected by passivation; etch concentrates on bottom

**Result:** Bottom etch rate is maintained throughout the process → reduced ARDE.

**Example:** Cryogenic silicon etch combines:
- Cl₂ plasma (etch)
- O₂ plasma (passivation)
- -100°C temperature (slows sidewall etch, enables passivation)

Can achieve **1:1 ARDE** (perfectly vertical sidewalls) for AR up to 10:1.

---

## Part 6: Showerhead Maintenance and Deposit Buildup

### 6.1 Deposit Formation on Showerhead

As gas flows through showerhead, deposits accumulate:

**Deposit sources:**
1. **Polymerized byproducts:** Incomplete etch of CF₄ leads to CFₓ polymer buildup
2. **Dust particles:** Entrained dust from previous wafers
3. **Metal oxides:** Sputtered electrode material

**Consequence:** Deposits clog showerhead holes → uneven gas distribution.

### 6.2 Cleaning Cycles

**In-situ cleaning** required to maintain showerhead:

**Cleaning Method 1: O₂ Plasma Cleaning**
- Run pure O₂ plasma (low power) for 10-30 minutes
- O₂ oxidizes carbon-based deposits (polymerized CF)
- Oxidized deposits volatilize

**Cleaning Method 2: Mechanical Scrubbing**
- Chamber shutdown required
- Manually clean showerhead (remove and scrub holes)
- Reassemble and restart

**Frequency:**
- **After every 50 wafers:** Quick O₂ clean (5 min)
- **After every 200 wafers:** Full O₂ clean (30 min)
- **Weekly:** Disassemble and manual clean (2 hours)

**Trade-off:** Cleaning time = no production → significant throughput loss (~5-10%).

---

## Summary

Gas distribution in 3D NAND gate line slit etch is fundamentally limited by radical transport physics:

1. **Radical Generation:** F atoms created at ~10¹³ cm⁻³ in plasma
2. **Radical Lifetime:** ~10-100 ms before recombination
3. **Diffusion Limited:** Radicals react on first surface contact → effective penetration << trench depth
4. **ARDE Consequence:** Bottom of deep trenches becomes radical-starved → etch rate drops 100-1000×

**Showerhead Design Objectives:**
- Uniform gas distribution (minimize hot spots)
- Maximum radical generation efficiency
- Minimize deposit clogging
- Remote vs. direct plasma trade-offs

**Radical Delivery Strategies:**
- Lower pressure (increase mean free path)
- Lower temperature (longer radical lifetime)
- Variable gas chemistry (optimize reactivity at each depth)
- Cyclic etch-passivation (protect sidewalls, concentrate etch on bottom)

**Trade-offs:** Every strategy that improves deep penetration (lower P, lower T, less reactive chemistry) degrades bulk etch rate. Process design requires finding the optimal balance for each application.

Chapters 7-9 build on gas distribution by addressing pressure-temperature-power optimization (Chapter 7), chamber passivation to protect showerhead and walls (Chapter 8), and RF matching networks that efficiently deliver power despite high-impedance plasma (Chapter 9).

---

**Next:** [Chapter 7: Pressure-Temperature-Power Phase Space Analysis](07-pressure-temperature-power-phase-space-analysis.md)
