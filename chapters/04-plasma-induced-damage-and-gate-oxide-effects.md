# Chapter 4: Plasma-Induced Damage and Gate Oxide Effects

## Executive Summary

The gate line slit etch process exposes conductive floating gates to high-energy plasma. Unlike conventional etch steps that work with isolated dielectrics, slit etch creates electrical consequences: plasma-induced charging, gate oxide rupture, defect formation, and charge trapping. These mechanisms degrade memory cell performance and cause yield loss. This chapter establishes the physics of plasma damage—**charging mechanisms, oxide breakdown, defect formation kinetics, and yield loss analysis**—that drive process design decisions throughout Chapters 5-18.

Understanding damage mechanisms is prerequisite to designing chamber geometry (Chapter 5), passivation strategies (Chapter 8), endpoint detection (Chapter 18), and post-etch recovery (Chapter 18).

---

## Part 1: Floating Gate Charging in Plasma

### 1.1 The Floating Gate Problem

In 3D NAND gate line slit etch, the floating gate (a conductive polysilicon electrode) is exposed to plasma:

```
Before Etch:
────────────────────────────────
[Protected by surrounding material]
    Floating Gate (hidden)
    [No plasma exposure]

During Slit Etch:
────────────────────────────────
    ↓ Plasma exposure ↓
    │   (ions, radicals, photons)
Floating Gate (exposed, now conductive)
    │   (charges accumulate)
    ↓
```

**Key physics:** The floating gate is electrically isolated by thin oxide. When exposed to plasma, it charges like a floating conductor in an electric field—and charge accumulation can reach dangerous levels.

### 1.2 Electron vs. Ion Arrival Rates

Plasma contains electrons (mass ~0.5 MeV/c²) and ions (mass ~1000 MeV/c²—much heavier). In equilibrium plasma:

**Electron thermal velocity:**
$$v_e = \sqrt{\frac{3 k_B T_e}{m_e}} \approx 10^6 \text{ m/s}$$

**Ion thermal velocity:**
$$v_i = \sqrt{\frac{3 k_B T_i}{m_i}} \approx 10^4 \text{ m/s}$$

Electrons are 100× faster than ions due to lower mass.

**Electron and ion flux to floating gate surface:**

$$\Phi_e = n_e \cdot v_e / 4 \approx 10^{13} \text{ electrons/cm}^2\text{/s}$$
$$\Phi_i = n_i \cdot v_i / 4 \approx 10^{11} \text{ ions/cm}^2\text{/s}$$

**Flux ratio:** Electrons arrive ~100× faster than ions.

**Consequence:** If floating gate is initially neutral, electrons arrive first and charge it **negatively**. Once negatively charged, the floating gate repels further electrons and attracts positive ions. Equilibrium is reached when:

$$\Phi_e \cdot P_{\text{stick,e}} = \Phi_i \cdot P_{\text{stick,i}}$$

where P_stick is the sticking coefficient (probability of charge transfer on contact).

### 1.3 Floating Gate Potential in Plasma

In steady state, the floating gate reaches a **floating potential** V_f relative to plasma:

$$V_f \approx -\frac{k_B T_e}{2e} \ln\left(\frac{m_i}{m_e}\right)$$

For typical 3D NAND etch plasma:
- **T_e ~ 2-3 eV** (electron temperature)
- **m_i / m_e ~ 50,000** (Argon ions)

$$V_f \approx -\frac{2.5 \text{ eV}}{2} \ln(50,000) \approx -10.5 \text{ eV}$$

**Result:** The floating gate charges to approximately **−10 to −20 V** relative to plasma potential.

### 1.4 Charge Accumulation Dynamics

The charge accumulation is not instantaneous. Time to reach floating potential:

$$\tau_{\text{charge}} = \frac{C_{\text{gate}} \cdot |V_f|}{\Phi_e \cdot e}$$

where:
- **C_gate:** Capacitance of floating gate oxide (~1-10 pF for typical geometry)
- **Φ_e:** Electron flux

For a 3D NAND slit with floating gate area ~100 nm × 50,000 nm (area ~0.5 µm²):

$$C_{\text{gate}} \approx \epsilon_0 \epsilon_r \cdot A / d \approx 8.85 \times 10^{-12} \times 4 \times 0.5 \times 10^{-8} / 5 \times 10^{-9} \approx 3.5 \text{ pF}$$

Charge at floating potential:
$$Q = C \cdot |V_f| \approx 3.5 \text{ pF} \times 15 \text{ V} \approx 52 \text{ pC}$$

Time to accumulate:
$$\tau \approx \frac{52 \times 10^{-12}}{10^{13} \times 1.6 \times 10^{-19}} \approx 3 \text{ ms}$$

**Gate line slit etch times are typically 5-30 minutes → charging reaches equilibrium long before etch completes.**

### 1.5 Peak Voltage Risk

In some plasma regimes, the floating gate can charge even more negative than the equilibrium value. This occurs when:
- **Ion flux is temporarily reduced** (pressure change, power transient)
- **Electrons arrive unopposed** → overshoot negative potential
- **Peak voltage can reach −30 to −50 V** (transient condition)

At these voltages, **oxide breakdown becomes a serious risk.**

---

## Part 2: Gate Oxide Breakdown and Rupture

### 2.1 Dielectric Breakdown Mechanism

Gate oxide is typically 3-5 nm thick SiO₂. When electric field across oxide exceeds a critical threshold, **dielectric breakdown** occurs: the oxide becomes conductive and fails as an insulator.

**Critical electric field for SiO₂:**

$$E_{\text{crit}} \approx 10 \text{ MV/cm} = 10^7 \text{ V/cm}$$

For a 5 nm oxide under floating gate voltage V_f:

$$E = \frac{|V_f|}{d_{\text{oxide}}} = \frac{20 \text{ V}}{5 \times 10^{-9} \text{ m}} = 4 \times 10^7 \text{ V/m} = 4 \text{ MV/cm}$$

This is **below** the critical field for steady breakdown, but close. **Transient overshoot to −40 V would create 8 MV/cm—exceeding critical field.**

### 2.2 Breakdown Pathways

Even below bulk breakdown, oxide fails via:

#### Pathway 1: Electron Impact Ionization
High-energy electrons (reaching ~10 MeV/c² from RF acceleration) can impact-ionize oxygen atoms in oxide:

$$e^- + \text{O} \rightarrow e^- + e^- + \text{O}^+$$

This creates a cascade of carriers and can form a conductive filament.

#### Pathway 2: Trap-Assisted Tunneling
SiO₂ contains defects (oxygen vacancies, E' centers). Electrons tunnel through oxide via these traps:

$$\Psi_{\text{electron}} \propto e^{-2\kappa x}$$

where κ is the tunneling parameter. At high field (> 3 MV/cm), tunneling probability increases exponentially.

#### Pathway 3: Thermal Oxide Degradation
The floating gate, sitting in hot plasma, heats up. Temperature rise in oxide:

$$\Delta T \approx \frac{P_{\text{dissipated}}}{k_{\text{oxide}}} \approx \text{10-50 K}$$

Elevated temperature accelerates all degradation mechanisms and shifts oxide properties.

### 2.3 Time-Dependent Dielectric Breakdown (TDDB)

**TDDB** is gradual oxide degradation over time. Even at fields below the critical breakdown value, oxide quality degrades:

$$t_{\text{to breakdown}} = A \cdot E^{-\gamma} \cdot \exp\left(\frac{E_a}{k_B T}\right)$$

where:
- **A:** Material constant
- **γ:** Field acceleration exponent (~1-3)
- **E_a:** Activation energy (~0.5-1.0 eV for oxide under high field)
- **T:** Temperature

**Consequence:** Even moderate electric fields (3-4 MV/cm) degrade oxide over exposure time. A 30-minute slit etch at 4 MV/cm causes measurable TDDB wear.

### 2.4 Quantifying Oxide Damage

Oxide damage is quantified by:

1. **Leakage Current:** After etch, measure gate oxide leakage under small bias. Increase in leakage = oxide degradation.

2. **Charge Trap Density:** Use charge-voltage curves to measure trap density increase. TDDB creates defects that trap charge.

3. **Breakdown Voltage:** Find voltage at which oxide abruptly becomes conductive (short). Degraded oxide breaks at lower voltage.

**Typical measurements:**
- **Fresh oxide:** Leakage < 10⁻¹¹ A/cm² at 1V bias
- **After moderate plasma exposure:** Leakage ~ 10⁻⁸ to 10⁻¹⁰ A/cm²
- **After severe exposure:** Leakage > 10⁻⁶ A/cm² (partial breakdown, oxide no longer functional)

---

## Part 3: Defect Formation in Gate Oxide

### 3.1 Types of Oxide Defects Created by Plasma

Plasma exposure creates several defect types:

#### Defect Type 1: Oxygen Vacancies
Oxygen atoms are knocked out of SiO₂ lattice by:
- **Ion impact:** High-energy ions strike oxygen, displacing it
- **Radical attack:** Cl or F radicals remove oxygen chemically
- **Electron impact:** High-energy electrons knock oxygen out

**Result:** Oxygen vacancy (V_O, also called E' center) — a silicon atom missing its bonding oxygen.

**Property:** Oxygen vacancies act as **electron traps**. They capture and hold electrons, creating fixed positive charge in oxide.

#### Defect Type 2: Silicon Interstitials
Silicon atoms displaced from lattice positions become interstitials (Si_i). These:
- **Create dangling bonds:** Unpaired electrons that capture other electrons
- **Increase conductivity:** Excess charge carriers can tunnel through oxide more easily

#### Defect Type 3: Interface States
At the Si/SiO₂ interface, plasma damage creates **interface states**—defects that span the bandgap and trap charge:

$$N_{\text{it}} \approx 10^{10} \text{ to } 10^{12} \text{ cm}^{-2}\text{eV}^{-1}$$

These trap both electrons and holes, modifying transistor behavior.

### 3.2 Defect Creation Rates

The rate of defect creation depends on plasma exposure intensity:

**Defect creation per ion impact:**
$$\Delta N_{\text{defect}} \approx 0.01 \text{ to } 0.1 \text{ defects/ion}$$

(Most ions create minimal damage; a fraction cause significant defect creation)

**Total defect creation during slit etch:**
$$N_{\text{defect, total}} = \Phi_{\text{ions}} \cdot t_{\text{etch}} \cdot Y_{\text{defect}}$$

where:
- **Φ_ions:** Ion flux (~10¹¹ ions/cm²/s)
- **t_etch:** Etch time (~30 min = 1800 s)
- **Y_defect:** Defect creation yield per ion (~0.01-0.1)

$$N_{\text{defect}} \approx 10^{11} \times 1800 \times 0.05 \approx 10^{12} \text{ defects}$$

On a floating gate with area 0.5 µm²:

$$N_{\text{defect}} \approx 10^{12} \times 0.5 \times 10^{-8} \approx 5 \times 10^{3} \text{ total defects}$$

**This is sufficient to significantly degrade oxide quality.**

### 3.3 Defect Annealing and Recovery

Some defects are **recoverable**. Hydrogen passivation and thermal annealing can partially restore oxide:

```
Defect Recovery vs. Temperature

Defect Density
    │
    ├─ Fresh Oxide (baseline)
    │
    ├─ Plasma Damaged Oxide
    │     (30-50% increase in traps)
    │
    ├─ After 200°C Anneal (1 hour)
    │     (20-30% recovery)
    │
    └─ After 400°C Anneal (1 hour)
          (50-70% recovery, but not complete)
```

**Post-etch annealing** (Chapter 18) can recover 50-70% of plasma-induced damage. However, some defects are **permanent**—they cannot be annealed away.

---

## Part 4: Floating Gate Oxide Damage Consequences

### 4.1 Charge Trapping and Threshold Voltage Shift

When defects trap charge in gate oxide, the floating gate's electrical behavior changes.

**Normal floating gate (fresh oxide):**
- Threshold voltage V_T: ~2-3 V (for a memory cell in specific state)
- Charge stored: Q, in isolated floating gate
- Relationship: V_T ∝ Q (charge directly affects switching voltage)

**After plasma damage (oxide traps charge):**
- Trapped charge in oxide: Q_trap
- Effective charge on floating gate: Q_eff = Q + Q_trap
- New threshold voltage: V_T' = V_T + ΔV_T

where ΔV_T ∝ Q_trap (trapped charge shifts threshold)

**Consequence:** Memory cells become harder to program (require higher programming voltage) or fail to hold charge reliably.

### 4.2 Leakage and Data Retention Loss

Increased oxide defect density increases **leakage current**:

$$I_{\text{leak}} \propto N_{\text{defect}} \times e^{-E_a / k_B T}$$

Leakage current causes charge to slowly drain from floating gate:

$$\frac{dQ}{dt} = -\frac{I_{\text{leak}}}{e}$$

**Time to lose significant charge:**

$$t_{\text{retention}} = \frac{Q}{I_{\text{leak}}}$$

For typical 3D NAND cells:
- **Fresh oxide:** Leakage ~pA → t_retention > 10 years
- **Moderately damaged oxide:** Leakage ~nA → t_retention ~ 1 year
- **Severely damaged oxide:** Leakage ~µA → t_retention ~ hours

**Data retention becomes the limiting factor for cells with damaged oxides.**

### 4.3 Cell-to-Cell Leakage Coupling

In some damage scenarios, oxide rupture creates **conductive paths between adjacent floating gates**:

```
Cell A (Floating Gate A)
    │
    ├─ Oxide with rupture/defect
    │
Cell B (Floating Gate B)
```

If a conductive path opens, charge flows from Cell A → Cell B:
- Cell A loses charge (state flip from 1→0 or loss of information)
- Cell B gains charge (state flip)
- Both cells become unreliable

This is a **catastrophic failure** affecting both cells simultaneously.

---

## Part 5: Yield Loss Analysis

### 5.1 Defect-Limited Yield

The yield of a 3D NAND chip depends on the number of functional cells. If plasma damage creates defects, some cells fail.

**Poisson yield model:**

$$Y = e^{-A \cdot D}$$

where:
- **Y:** Fraction of chips with no defects (yield)
- **A:** Chip area (cm²)
- **D:** Defect density (defects/cm²)

For a modern 3D NAND chip (100 Gb capacity):
- **Chip area:** ~50 mm² = 0.5 cm²
- **Number of memory cells:** ~100 Gb / 3 bits/cell (TLC) ≈ 3 × 10¹⁰ cells
- **Defect density from plasma:** D ≈ 10⁶ to 10⁷ defects/cm² (worst case)

$$Y = e^{-0.5 \times 10^7} = e^{-5 \times 10^6} \approx 0 \text{ (unacceptable)}$$

**This is why plasma damage mitigation is critical: uncontrolled damage produces zero yield.**

### 5.2 Process Window for Acceptable Damage

Acceptable plasma damage is typically:
- **Defect density:** < 10⁴ defects/cm² (after mitigation)
- **Oxide leakage:** < 10⁻⁸ A/cm² (after recovery annealing)
- **Charge trap increase:** < 5 × 10¹⁰ cm⁻²eV⁻¹

Within this window, yield is acceptable (~70-90% for advanced nodes).

**Outside this window:**
- Yield drops rapidly (0-10%)
- Chip becomes unsellable
- Entire lot may be scrapped

This is why process control is tight: exceeding damage limits causes complete yield loss.

### 5.3 Spatial Variation in Damage

Plasma damage is not uniform across the chip. Different regions experience different plasma exposure:

```
Damage Distribution Across Wafer

Damage Level
    │
100%├─────────┐
    │  (high)  │
 60%├─────┬────┼─────┐
    │     │    │     │  (moderate, varies with position)
 20%│     │    │     └─────
    │     │    │
  0%└─────┴────┴──────────
    0    50   100  150 (position on wafer, mm)
```

**Center of wafer:** Lower damage (cooler, less ion bombardment)  
**Edge of wafer:** Higher damage (hotter, more edge effects)  
**Within-die variation:** Pattern-dependent (dense regions different from open regions)

**Consequence:** Some die are damaged beyond recovery; others are marginal. Yield loss is spatially correlated—failed die cluster together.

---

## Part 6: Mitigation Strategies Overview

Chapters 5-9 address chamber design to minimize damage. Here we preview key strategies:

### 6.1 Remote Plasma Sources

Instead of direct plasma over the wafer, use a **remote plasma source** upstream:

```
Traditional Plasma Etch:
    Electrode
        ↓
    [High-energy plasma directly over wafer]
        ↓
    Wafer (exposed to ions, energetic electrons, UV photons)

Remote Plasma Source:
    [Plasma generation chamber]
            ↓ (Neutralized, cooled products flow to etch chamber)
        ↓
    [Radical delivery, low-energy ions]
        ↓
    Wafer (mainly neutral radicals, low-energy ions)
```

**Result:** Floating gate exposed to lower-energy ions and less UV → reduced charging and damage.

### 6.2 Floating Gate Grounding

In advanced processes, floating gates can be **partially grounded** via:
- Substrate connection (make substrate conductive to anchor floating gate potential)
- Temporary conductor path during etch (sacrificial layer that bridges floating gate)

**Result:** Floating gate cannot charge to dangerous levels because potential is anchored.

### 6.3 Process Temperature Control

Lower process temperature reduces:
- **TDDB acceleration:** Exponential dependence on T
- **Defect annealing:** Defects created at higher T are less stable
- **Ion kinetic energy:** Cold ions have lower impact energy

**Trade-off:** Lower temperature may reduce etch rate → longer etch times → more total charge exposure.

### 6.4 Endpoint Detection

Stop etch precisely when the gate line slit is complete. Longer etch times = more damage accumulation.

**Aggressive endpoint detection** can reduce etch time by 30-50%, proportionally reducing damage.

---

## Part 7: Damage Measurement and Detection

### 7.1 Post-Etch Electrical Testing

After etch, cells are electrically characterized to detect damage:

**Test 1: Gate Oxide Leakage**
- Apply small bias (1V) to floating gate
- Measure current flowing through oxide
- Fresh oxide: pA-scale; damaged oxide: nA to µA

**Test 2: Program/Erase Voltage**
- Attempt to program cells (inject electrons to floating gate)
- Measure voltage required to shift threshold by standard amount (e.g., 0.5V)
- Damaged cells require higher voltage or cannot program fully

**Test 3: Data Retention**
- Program cells, wait 1 hour, read back
- Count cells that have lost charge
- Damaged cells lose charge faster than specification

### 7.2 Defect Imaging (Destructive)

For process development (not production):
- Cross-section SEM of damaged cells
- TEM (transmission electron microscopy) to visualize defects in oxide
- Cathodoluminescence to detect defect-related light emission

These are **destructive tests** (destroy the sample) but provide direct visual evidence of damage.

### 7.3 Yield Correlation

Compare electrical test results with physical layer defects (optical/SEM inspection of slit geometry):

If cells with **good slit geometry** still fail electrical tests → damage is electrical (oxide, charging), not geometric.

If cells with **poor slit geometry** fail → damage could be geometric (overetch, undercut) or electrical.

---

## Summary

Plasma-induced damage is the defining challenge of 3D NAND gate line slit etch. Key mechanisms:

1. **Floating Gate Charging:**
   - Electrons arrive 100× faster than ions → gate charges negatively
   - Equilibrium potential: −10 to −20 V (transient overshoot to −30+ V possible)
   - Charge accumulation timescale: ~ms (well within etch time)

2. **Gate Oxide Rupture & TDDB:**
   - High floating gate voltage creates 3-8 MV/cm field across 5nm oxide
   - Exceeds critical field → dielectric breakdown
   - Below critical field, TDDB (gradual degradation) still occurs

3. **Defect Formation:**
   - Plasma ions and electrons create oxygen vacancies, Si interstitials, interface states
   - Defects trap charge, increase leakage, reduce oxide quality
   - Partial recovery possible via post-etch annealing (50-70%)

4. **Yield Loss:**
   - Uncontrolled damage → 0% yield
   - Acceptable damage window: < 10⁴ defects/cm² (tight control required)
   - Spatial variation → clustered failures

5. **Mitigation (Previewed):**
   - Remote plasma sources → lower ion energy
   - Floating gate grounding → prevent charging
   - Process temperature control → reduce TDDB
   - Aggressive endpoint detection → minimize etch time

Chapters 5-18 build on this foundation, developing chamber design, process control, and recovery techniques to keep damage within acceptable limits while maintaining etch performance.

---

**Next:** [Chapter 5: Electrode Design for Ultra-High Aspect Ratios](05-electrode-design-for-ultra-high-aspect-ratios.md)
