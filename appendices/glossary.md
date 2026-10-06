# Appendix A: Glossary of 3D NAND Gate Line Slit Etch Terminology

## A-Z Technical Terms

### ARDE (Aspect Ratio Dependent Etching)
Phenomenon where etch rate decreases as trench aspect ratio (depth/width) increases. At AR > 50:1, ions and radicals struggle to reach the trench bottom, reducing etch rate by 5-20×. Primary challenge in gate line slit etch.

### Aspect Ratio (AR)
Ratio of feature depth to width: AR = Depth / Width. Gate line slits operate at AR = 50:1 to 5000:1 depending on stack height and slit width.

### Ballistic Transport
Ion motion where mean free path exceeds trench dimensions, so ions travel in straight lines rather than random walks. Occurs at low pressure (< 50 Pa) in deep trenches.

### Byproduct (or Etch Residue)
Volatile or semi-volatile compounds formed during etch (e.g., SiF₄, SiCl₄, AlCl₃). Must be removed from trench for continued etch and to prevent contamination.

### Capacitive Coupling Plasma (CCP)
Plasma generation method where RF power is applied directly to the electrode below the wafer. Creates a sheath and accelerates ions toward wafer. Common for 3D NAND gate line slit etch.

### Charge-Coupled Damage (CCD)
Damage to floating gate oxide caused by accumulated charge in the floating gate during plasma exposure. Can cause gate oxide rupture or charge trapping defects.

### Chlorine Chemistry
Etch chemistry using Cl₂, HCl, or CCl₄ as etch gases. Produces SiCl₄ (Si etch), SiClₓ compounds (mixed products), and other chlorine byproducts.

### Cryogenic Etch
Etch performed at extremely low temperature (-80°C to -120°C). Enables high selectivity and vertical sidewalls by controlling diffusion and reaction kinetics. Not yet mainstream for 3D NAND gate line slits.

### Critical Dimension (CD)
Smallest feature size that can be reliably printed and etched. For modern 3D NAND: ~15-30 nm for gate line slits.

### Debye Sheath
Thin region (~1-10 µm) near electrode where electric field accelerates ions. Voltage drop across sheath determines ion energy at surface.

### Diffusion-Limited Regime
Etch regime where species delivery (ions, radicals) is the rate-limiting step, not chemical reaction kinetics. Dominates in deep trenches (AR > 200:1).

### Dielectric Stack
Multi-layer structure containing SiO₂, Si₃N₄, and Si materials stacked vertically. Each layer serves a function (isolation, conduction, charge storage).

### Endo-Exo Effect
Difference in etch rate for features with different micro-environments (dense vs. open regions). Related to micro-loading.

### Endpoint Detection
Real-time sensing of etch progress using optical (reflectance) or RF (impedance) monitoring. Triggers etch stop when target layer is reached.

### Floating Gate
Conductive electrode (polysilicon or silicon channel) that stores charge (electrons or holes) in 3D NAND memory cells. Must be isolated from other floating gates by gate line slits.

### Fluorine Chemistry
Etch chemistry using CF₄, CHF₃, or SF₆ as etch gases. Produces SiF₄ (Si etch), CF₂ (passivation), and other fluorine byproducts. Excellent Si/SiO₂ selectivity.

### Gate Line
Horizontal polysilicon conductor running across the 3D NAND chip. Defines word line in memory array. Adjacent gate lines must be isolated by slits.

### Gate Line Slit
Narrow trench (10-30 nm wide, 50-100 µm deep) etched to separate adjacent gate lines. Critical for preventing gate shorts in 3D NAND.

### Hard Mask
Thin layer (oxide or nitride) used to define etch pattern. Protects unwanted regions from etch while defining opening for desired etch path.

### High-Aspect-Ratio (HAR)
Conventional HAR trenches: AR ~ 3:1 to 10:1. Ultra-high aspect ratio (UHAR): AR > 50:1. Gate line slits are extreme HAR, AR > 500:1.

### Inductive Coupling Plasma (ICP)
Plasma generation using RF-driven magnetic coil above the wafer. Decouples plasma generation from ion acceleration. Good for high ion density without extreme ion energy.

### Ion Bombardment
Acceleration of ions (often Ar⁺ in plasma) toward wafer surface using RF sheath voltage. Ion energy (20-300 eV typically) determines sputtering and ion-assisted etch.

### Ion Flux
Number of ions hitting surface per unit area per unit time (ions/cm²/s). Critical parameter for etch rate in ion-assisted chemical etch.

### Microloading
Spatial variation in etch rate due to differences in feature density across the wafer. Dense regions (high feature density) etch slower; open regions etch faster.

### Multi-Layer Selectivity
Ability to etch one material selectively over another while traversing a multi-layer stack. Gate line slit requires Si/SiO₂, SiO₂/SiN selectivity control.

### Native Oxide
Thin oxide layer (~1-3 nm) that forms on silicon surface exposed to air or oxygen. Protects bulk silicon but must be removed or penetrated for etch.

### Neutral Radical (or Free Radical)
Reactive atom or molecule with unpaired electron(s): Cl, F, CFₓ, etc. Responsible for chemical etch; essential for selectivity in plasma etch.

### Outgassing
Release of volatile compounds (H₂O, hydrocarbons, etc.) from chamber walls or materials. Can contaminate etch process if not controlled.

### Passivation
Deposition of protective layer (oxide or polymer) on surface to prevent unwanted reactions. Used in cyclic etch-passivation to suppress sidewall etch and achieve vertical profiles.

### Photoresist
Organic polymer sensitive to UV or EUV light. Used in lithography to define pattern. Must be stripped before or during etch.

### Plasma Sheath
Thin region (~1-10 µm) near electrode where free electron density drops, creating electric field that accelerates ions. Critical for ion energy control.

### Process Window
Range of process parameters (power, pressure, gas flow, temperature) within which etch specifications are met. Narrow window = difficult process control.

### Radical Diffusion
Transport of neutral reactive atoms (Cl, F) into trenches by diffusion. Limited by sidewall reactions in deep trenches; etch rate decreases with ARDE.

### Reaction-Limited Regime
Etch regime where chemical reaction kinetics (not species delivery) limits etch rate. Dominates in shallow trenches (AR < 50:1).

### Reentrant Profile
Sidewall shape where top of feature is wider than bottom. Creates mechanical undercut and can trap byproducts. Avoided in gate line slit etch.

### Residue
Etch byproducts or deposited material left on wafer after etch. In gate line slits, residue on floating gate surfaces causes contamination and yield loss.

### RF (Radiofrequency) Power
Electrical power at 13.56 MHz (or other frequencies) used to sustain plasma and accelerate ions. Measured in watts (W).

### Selectivity
Ratio of etch rates for two different materials. Si/SiO₂ selectivity = Rate(Si) / Rate(SiO₂). High selectivity allows precise endpoint control.

### Sidewall Roughness
Microscopic variations in sidewall smoothness. Quantified as Ra (arithmetic roughness) or RMS (root-mean-square). Affects electrical properties and leakage.

### Slurry (in context of CMP, not plasma etch)
Colloidal suspension used for chemical-mechanical planarization. Not directly relevant to gate line slit etch but important post-etch process.

### Stoichiometric Compounds
Chemical compounds with fixed atomic ratios (e.g., SiO₂ has Si:O = 1:2). Plasma reactions may produce non-stoichiometric intermediates (SiOₓ with x ≠ 2).

### Substrate
Underlying silicon wafer. In 3D NAND context, the substrate sits below the entire gate line slit stack and may be reached if etch is not stopped on isolation layer.

### Thermal Conductivity
Material property determining heat flow (W/m·K). Silicon (149 W/m·K) conducts heat moderately; affects within-trench temperature gradients in slits.

### Time-Dependent Dielectric Breakdown (TDDB)
Gradual degradation of oxide quality over time when electric field is applied. Floating gate oxide exposure to plasma can accelerate TDDB.

### Trench
Narrow gap etched in material. Gate line slit is a trench with extreme aspect ratio (> 500:1) and multiple material transitions.

### Vertical Selectivity
In multi-layer stacks, selectivity between materials arranged vertically (one on top of another). Different from planar selectivity (layer vs. adjacent material at same depth).

---

## Key Acronyms

| Acronym | Definition |
|---|---|
| **AR** | Aspect Ratio |
| **ARDE** | Aspect Ratio Dependent Etching |
| **CCD** | Charge-Coupled Damage |
| **CCP** | Capacitive Coupling Plasma |
| **CD** | Critical Dimension |
| **EUV** | Extreme Ultraviolet |
| **HAR** | High-Aspect-Ratio |
| **ICP** | Inductive Coupling Plasma |
| **RF** | Radiofrequency |
| **RMS** | Root-Mean-Square |
| **SEM** | Scanning Electron Microscope |
| **TDDB** | Time-Dependent Dielectric Breakdown |
| **UHAR** | Ultra-High-Aspect-Ratio |

---

**Back to:** [INDEX.md](../INDEX.md)
