# Chapter 12: Selectivity Mechanisms in Multi-Layer Stacks

## Executive Summary

Gate line slit etch must navigate a multi-layer dielectric stack (Si → SiO₂ → SiN → SiO₂ → Si ...) with **independent control of etch rates for each material**. Selectivity—the ability to etch one material much faster or slower than another—is enabled by fundamental differences in etch chemistry: fluorine atoms react much faster with silicon than with oxides; chlorine produces different products depending on material. This chapter addresses: *What are the mechanisms of material-specific etch?* *How do we achieve different selectivity ratios for different material pairs?* *What chemical and physical processes drive selectivity?* *How do selectivity and other process objectives interact?* Mastering selectivity is prerequisite to precise endpoint control and avoiding over/underetch damage.

---

## Part 1: Fundamental Selectivity Mechanisms

### 1.1 Chemical Reactivity as the Basis for Selectivity

Different materials bind atoms differently, affecting how easily etch radicals can attack:

**Silicon (Si) bonding:**
- Si-Si bond strength: 51 kcal/mol
- Si-O bond strength: 109 kcal/mol (much stronger)
- Si-N bond strength: 92 kcal/mol (moderately strong)

**Etch radical reactivity:**
- F atoms: Extremely reactive, energetically favorable with all Si compounds
- Cl atoms: Moderately reactive, less favorable with oxides than with Si
- O atoms: Very reactive with Si (oxidation), less so with SiO₂

**Consequence:** For Si/SiO₂ selectivity:
- Fluorine-based etch (CF₄, CHF₃): Si etches much faster (selectivity 5-10:1)
- Chlorine-based etch (Cl₂, CCl₄): Si etches faster but less selectively (selectivity 2-5:1)

### 1.2 Reaction Pathway Differences

Different materials follow different etch pathways:

**Silicon in F-based plasma:**
$$\text{Si} + 4\text{F} \rightarrow \text{SiF}_4 \text{ (gaseous, volatile)}$$

SiF₄ sublimes immediately → clean removal.

**Oxide in F-based plasma:**
$$\text{SiO}_2 + 4\text{F} \rightarrow \text{SiF}_4 + 2\text{O}_2 \text{ or } \text{SiOF}_x + \text{products}$$

Reaction is slower (requires breaking Si-O bonds first, then forming SiF₄). Intermediate products (SiOF₂, SiOF) are less volatile → accumulation possible.

**Physical interpretation:** Si etch is **direct** (F attacks Si-Si bonds); SiO₂ etch requires **indirect** pathway (F must first attack oxide lattice structure, which is different).

### 1.3 Surface Passivation as Selectivity Driver

Some materials naturally form passivating layers that slow etch:

**Oxide surfaces in F-based plasma:**
$$\text{SiO}_2 + \text{F} \rightarrow \text{Si-OF} + \text{(passivating surface layer)}$$

The Si-OF layer is less reactive than the underlying SiO₂, creating a natural **etch slowdown** for oxides.

**Silicon surfaces in F-based plasma:**
$$\text{Si} + \text{F} \rightarrow \text{SiF}_x \text{ (no stable passivation)}$$

SiF_x products are volatile → no slowdown.

**Consequence:** This **self-limiting** mechanism provides inherent Si/SiO₂ selectivity without requiring external passivation.

---

## Part 2: Selectivity Control in Gate Line Slit Etch

### 2.1 Multi-Material Selectivity Requirements

Gate line slit must achieve **simultaneous control** of three material pairs:

```
Gate Stack Etch Sequence

Step 1: Etch SiO₂ (top oxide)
        Must NOT etch underlying Poly (selectivity SiO₂/Poly required)

Step 2: Etch Poly (Si gate)
        Must etch fast enough for speed, but not so much as to degrade oxide below
        Must transition to Step 3 when Poly layer is removed

Step 3: Etch SiO₂ (gate oxide, CRITICAL - only 3-5 nm)
        Must etch slowly to avoid penetrating into SiN
        Timing precision critical: ±1 nm = ±20-30% of layer thickness

Step 4: Etch SiN (barrier layer)
        Must NOT etch underlying SiO₂ too fast (selective SiN/SiO₂)

Step 5: Stop on isolation SiO₂ (or reach substrate)
```

**Challenge:** Each step has different selectivity requirements, but we have limited process variables to tune.

### 2.2 Reciprocal Selectivity Problem

**Selectivity is defined as:** S_AB = Rate(A) / Rate(B)

In gate line slit, we need:
- **Step 1:** S_SiO₂/Poly > 1 (SiO₂ faster)
- **Step 2:** S_Poly/SiO₂ > 1 (Poly faster)  ← **OPPOSITE of Step 1!**
- **Step 4:** S_SiN/SiO₂ > 1 (SiN faster)
- **Step 3:** S_SiO₂/SiN < 1 (SiO₂ slower)  ← **OPPOSITE of Step 4!**

**Solution:** Use **different recipes** for different steps:

```
Recipe Switching Strategy

Recipe A (for Step 1):
  Chemistry: CF₄/Ar (lots of F radicals)
  Selectivity: SiO₂/Poly = 1.5:1 (SiO₂ faster)
  Etch rate: 300 nm/min

Recipe B (for Step 2):
  Chemistry: CF₄/Ar (same, optimized for Si)
  Selectivity: Poly/SiO₂ = 3:1 (Poly much faster)
  Etch rate: 300 nm/min

Recipe C (for Step 3):
  Chemistry: CHF₃/Ar or Cl₂/Ar (less aggressive)
  Selectivity: SiO₂/SiN = 0.5:1 (SiO₂ SLOWER)
  Etch rate: 50 nm/min (controlled, slow endpoint approach)

Recipe D (for Step 4):
  Chemistry: CF₄/Ar + minor Cl (nitride-selective)
  Selectivity: SiN/SiO₂ = 2:1 (SiN faster)
  Etch rate: 200 nm/min
```

### 2.3 Ion Energy Effects on Selectivity

Changing ion energy (via pressure, power) affects selectivity:

**Low ion energy (E < 50 eV):**
- Chemical etch dominates
- Material differences in reactivity are pronounced
- **Higher selectivity** (materials etch very differently)
- Example: Si/SiO₂ selectivity ~8:1

**High ion energy (E > 150 eV):**
- Ion-assisted sputtering dominates
- All materials sputter at similar rates (~1-2 atoms/ion)
- **Lower selectivity** (all materials respond similarly to ion impact)
- Example: Si/SiO₂ selectivity ~2:1

**Optimization:** For precise control of gate oxide etch (Step 3), use **low ion energy** to maximize selectivity margin.

---

## Part 3: Endpoint Detection for Selective Etch

### 3.1 Optical Endpoint Signals

Different materials have different optical properties:

**Reflectance values (13.56 MHz RF wavelength ~ 10 µm, not optical):**
Actually, optical endpoint detection uses visible light (400-700 nm) for monitoring.

**Optical reflectance:**
- Silicon (dark, rough): ~30% reflectance
- SiO₂ (lighter, smooth): ~5% reflectance
- SiN (intermediate): ~15-20% reflectance
- Metal (aluminum, if exposed): ~70% reflectance

```
Reflectance During Multi-Layer Etch

Reflectance (%)
   100 ├─────────────────────
       │ 
    70 ├────┐ (metal if exposed)
       │    │
    50 ├────┤
       │    │
    30 ├────┼────┐ (Si - rough)
       │    │    │
    20 ├────┼────┼────┐ (SiN)
       │    │    │    │
     5 ├────┼────┼────┼─── (SiO₂ - smooth)
       │    │    │    │
     0 └────┴────┴────┴─────────
       Step1 Step2 Step3 Step4
```

**Endpoint detection algorithm:**
1. Monitor reflectance continuously
2. When reflectance changes significantly, signal endpoint
3. Example: Reflectance drops from 30% to 5% → Si breakthrough into SiO₂

**False positives:** Reflectance can change due to **surface roughness changes** even within the same material. Rough Si (~20% reflectance) vs. smooth Si (~35% reflectance).

### 3.2 Optical vs. RF Impedance Monitoring

**Optical endpoint (visible/near-UV reflectance):**
- Advantages: Direct measurement of layer change, good for planar features
- Disadvantages: Affected by surface roughness, poor sensitivity to sub-wavelength features in deep trenches, line-of-sight requirement

**RF impedance endpoint (13.56 MHz):**
- Advantages: Doesn't require line-of-sight, sensitive to plasma changes from etch progress
- Disadvantages: Affected by many variables (pressure, temperature, chamber state), less material-specific

**Hybrid approach (best practice):**
Combine optical + RF impedance signals for robust endpoint:
- Optical signal: Primary endpoint trigger (material change confirmed)
- RF impedance: Backup signal + diagnostic (plasma state monitoring)

### 3.3 Over/Underetch Margins

For gate oxide etch (Step 3), the margin for error is extremely tight:

```
Gate Oxide Etch Timing (3-5 nm thick)

Ideal Etch:   Etch for exactly 15-30 seconds → stop at oxide/nitride interface

Underetch:    Stop early → 1-2 nm of oxide remains
              Impact: Gate oxide not completely removed
                     Trench wall sidewalls partially blocked by oxide
                     Floating gate not fully exposed

Overetch:     Stop late → penetrate 1-2 nm into SiN
              Impact: SiN damage → electrical properties change
                     Possible short between gate and floating gate
                     Charge leakage risk

Acceptable Window: ±1 nm (33% of layer thickness)
                   This requires timing precision to ±5-10 seconds for 50 nm/min etch rate
```

### 3.4 Selectivity Margin Calculations

**Selectivity margin** = how long the correct material etches before the underlying layer is exposed:

$$M = \frac{t_{\text{correct}} - t_{\text{stop}}}{1}$$

where:
- t_correct: Time for target material to be completely removed
- t_stop: Time when underlying material should not be touched

**Example:** Gate oxide etch
- Oxide layer: 4 nm
- Underlying SiN: must not etch
- Etch rate for SiO₂: 50 nm/min = 0.83 nm/s
- Etch rate for SiN: 10 nm/min = 0.17 nm/s (lower due to selectivity)

**Time to etch 4 nm SiO₂:** 4 nm / 0.83 nm/s = 4.8 seconds
**Depth SiN etches in 4.8 s:** 0.17 nm/s × 4.8 s = 0.8 nm

**Selectivity margin:** 4 nm (SiO₂) vs. 0.8 nm (SiN) → 5:1 ratio

To be safe, want SiO₂/SiN selectivity > 10:1 to maintain 10× safety margin.

---

## Part 4: Multi-Layer Selectivity Optimization

### 4.1 Gas Chemistry Tuning

Different gas mixtures provide different selectivity ratios:

| Gas Recipe | Si/SiO₂ Selectivity | SiN/SiO₂ Selectivity | Si/SiN Selectivity |
|------------|---------------------|----------------------|--------------------|
| CF₄/Ar    | 6:1                 | 1.2:1               | 5:1                |
| CHF₃/Ar   | 4:1                 | 1.8:1               | 2.2:1              |
| Cl₂/Ar    | 3:1                 | 2.5:1               | 1.2:1              |
| CF₄/Cl₂   | 5:1                 | 2.0:1               | 2.5:1              |

**Optimization for gate line slit:**
- Step 1 (SiO₂/Poly): Use CF₄ (maximize SiO₂/Si selectivity)
- Step 2 (Poly/SiO₂): Use CF₄ (get best Si selectivity over oxide)
- Step 3 (SiO₂ on SiN): Switch to CHF₃ or Cl₂ (increase SiO₂/SiN selectivity margin)
- Step 4 (SiN/SiO₂): Use Cl₂ or mixed chemistry (boost SiN selectivity)

### 4.2 Pressure and Temperature Effects on Selectivity

**Pressure effect on selectivity:**
- **Low pressure (5-10 Pa):** Radicals have longer mean free path → more discriminating (higher selectivity)
- **High pressure (50 Pa):** Radicals react indiscriminately → lower selectivity

**Temperature effect on selectivity:**
- **Low temperature (50°C):** Reaction kinetics favor Si (lower activation energy for Si-F attack)
- **High temperature (100°C):** Kinetics shift → SiO₂ becomes relatively more reactive (lower Si/SiO₂ selectivity)

**Optimization:** For tight selectivity margins in gate oxide etch:
- Use **low pressure** (10-15 Pa) for higher selectivity
- Use **moderate temperature** (60-70°C) to maintain selectivity

### 4.3 Timing-Based Selectivity

Some selectivity is achieved through **endpoint timing** rather than chemistry:

**Approach:** Etch with moderate selectivity, but very carefully time when to stop:

```
Timing-Based Selectivity Example

Recipe: CF₄/Ar, P=20Pa, T=70°C
        Si etch rate: 250 nm/min
        SiO₂ etch rate: 100 nm/min

Etch SiO₂ layer (4 nm):
        Time needed: 4 nm / (100 nm/min) = 0.4 seconds = 24 seconds per run? NO!
        This is too slow. Instead:

Bulk etch SiO₂ at high rate (1-2 min), then approach endpoint carefully:
        Last 100 nm: High rate etch
        Final 20 nm: Slow pressure reduction, lower rate approach
        Endpoint signal: Reflectance change indicates SiO₂/SiN boundary crossed

Result: Achieved high precision without requiring extreme selectivity (>100:1)
```

---

## Part 5: Selectivity Challenges and Solutions

### 5.1 Selectivity Loss Over Time

As etch progresses, selectivity can degrade:

**Cause 1: Surface Roughness Changes**
- Fresh SiO₂: Smooth surface
- After 5 minutes etch: Rough, damaged surface (if ion energy too high)
- Rough SiO₂ etches differently (can etch faster)
- Selectivity degrades as etch proceeds

**Cause 2: Product Accumulation**
- Early etch: Clean chemistry, good selectivity
- Mid-etch: Some byproducts accumulate, slow diffusion, reduce selectivity margin
- Late etch: Deposits can build up, further changing chemistry

**Cause 3: Plasma Property Drift**
- Electrode coating erodes → plasma conductivity changes → selectivity shifts
- Temperature drift → kinetics change
- Pressure regulation drift → selectivity margin narrows

**Mitigation:**
- Monitor selectivity-critical steps carefully
- Use optical endpoint as primary signal
- Reduce pressure further in final approach for oxide etch (improve selectivity safety)
- More frequent in-situ chamber cleaning to maintain plasma properties

### 5.2 Selectivity-ARDE Trade-Off

Ironically, trying to achieve better selectivity can **worsen ARDE:**

**Low pressure improves selectivity** (better material discrimination)
**But low pressure worsens ARDE** (poor radical penetration to trench bottom)

```
Selectivity vs. ARDE Trade-Off

Pressure (Pa)
    │
 50 ├─────────┐
    │  Good   │ ARDE (high P = bad ARDE)
    │ Selectivity
 20 ├────┬────┼─────┐
    │    │    │     │ (moderate on both)
    │    │    │     │
 10 ├────┤    │ Bad │ ARDE (low P = good ARDE)
    │ Bad│    │ Good
    │Select.  │
  0 └────┴────┴─────┴──────
    Selectivity      ARDE
    (higher P worse) (lower P better)

Optimization: ~15-20 Pa balances both concerns
```

### 5.3 Process Robustness vs. Selectivity

Higher selectivity margins require tighter process control:

```
Selectivity-Control Trade-Off

Selectivity S | Process Robustness | Equipment Cost | Recipe Complexity |
-----------|--------------------|-----------------|------------------|
S > 10:1  | Poor (tight control) | Very high       | Very complex      |
S = 5-10:1| Good (moderate tuning)| High           | Moderate          |
S = 2-5:1 | Excellent (forgiving) | Moderate       | Simple            |
S < 2:1   | Too forgiving (bad)  | N/A            | N/A               |

Practical target: S = 3-5:1 (good selectivity without extreme complexity)
```

---

## Summary

Selectivity in 3D NAND gate line slit etch is fundamentally **about material-specific chemistry coupled with precise timing**:

1. **Chemical Selectivity Drivers:**
   - Bond strength differences (Si-Si vs. Si-O)
   - Etch radical reactivity (F very reactive, Cl moderate)
   - Product volatility (SiF₄ volatile, SiO₂ products less so)
   - Surface passivation (natural SiO₂ passivation slows etch)

2. **Reciprocal Selectivity Problem:**
   - Step 2 requires opposite selectivity from Step 1
   - Solution: Use different recipes for different steps
   - Example: CF₄/Ar for Si selectivity, CHF₃/Ar for oxide selectivity

3. **Endpoint Detection:**
   - Optical endpoint: Primary signal (material reflectance change)
   - RF impedance: Backup signal + diagnostics
   - Hybrid approach most robust
   - Timing margins: ±1 nm for 3-5 nm gate oxide (33% tolerance)

4. **Optimization Leverage:**
   - Gas chemistry: Tunable 2-10:1 for different material pairs
   - Ion energy: Affects selectivity significantly (high E reduces selectivity)
   - Pressure: Lower pressure improves selectivity but worsens ARDE
   - Temperature: Lower T favors Si (improves Si/SiO₂ selectivity)

5. **Trade-Offs:**
   - **Selectivity vs. ARDE:** Low P good for selectivity, bad for ARDE
   - **Selectivity vs. Robustness:** Higher selectivity requires tighter control
   - **Selectivity vs. Speed:** Very high selectivity often means slow etch rate

Chapters 13-14 build on selectivity by addressing **sidewall passivation (protecting against ion damage during selective etch steps)** and **temperature effects (thermal coupling between selectivity and ARDE control)**.

---

**Next:** [Chapter 13: Sidewall Passivation and Scalloping Control](13-sidewall-passivation-and-scalloping-control.md)
