# Chapter 14: Advanced Schemes — Boron-Doped Carbon, Taller Masks, Metal-Containing Masks, Hybrid Caps & 4F² / 3D DRAM

## Overview

The reference mask is the one a 1b-class capacitor needs. The next array down, the 1d-class of Book #31, has a 37 nm pitch, a 26 nm exit CD, a mold of 2.1 µm, and a mask that has to be both taller and harder: 1.5 µm of boron-doped carbon with a hole aspect ratio of 56. Beyond it are the 4F² vertical-channel cell, whose holes sit on a 30 nm square grid with a web of 9 nm and a mask aspect ratio of 69, and 3D DRAM, whose vertical etches go through a silicon and silicon-germanium superlattice, not oxide.

This chapter carries the open to each. It describes the boron-doped route (M2) and what the fluorine that boron needs costs the cap and the passivation, compares the alternatives for the 1d mask (a taller undoped film, boron-doped carbon, tungsten-doped carbon), shows what a silicon hybrid cap does to the cliff of Chapter 11, quantifies the colder wafer, builds the open for 4F² (M3), and says what carries over to 3D DRAM. It ends with a summary of every route in the book on one page: array, mask, aspect ratio, web, bow, time, cap, loss, and cost.

**Learning Objectives:**
- Explain why boron-doped carbon needs fluorine to open and what the fluorine costs
- Compare undoped, boron-doped, and tungsten-doped masks for the 1d array by time, cap, and module cost
- Show how a silicon hybrid cap removes the top-loss cliff and what selectivity it needs
- Compute the effect of a −60 °C wafer on the bow, the rate, and the cap budget
- Build the open for the 4F² array and identify the specification it fails
- Say what carries over from the carbon open to the etches of 3D DRAM

---

## 14.1 Boron-Doped Carbon and the 1d-Class Open (M2)

### 14.1.1 The Chemistry of the Boron

B-ACL contains about 40 at% boron, which gives it the hardness (E = 105 GPa) and the selectivity (3.5 against 2.3 effective, Book #31) that the mold etch needs. Oxygen alone cannot open it:

```
Boron removal (per mole of boron):
  B + O → B₂O₃ (solid)       involatile (m.p. 450 °C); stays on the wall and the floor
  B + 3 F → BF₃ (gas)         volatile (b.p. −100 °C)         ← the route
  B + 3 Cl → BCl₃ (gas)       volatile (b.p. 12 °C)           ← an alternative (Cl attacks the cap and the stop)
M2 gas:  O₂ / COS / CF₄ (3%) / Ar;  the fluorine carries off the boron as BF₃, the oxygen the carbon as CO
```

### 14.1.2 What the Fluorine Costs

Fluorine does the job that the boron needs, and it also acts on everything else in the plasma:

```
Costs of 3% CF₄ in the M2 plasma:
  The cap:      ACL:SiON falls from 51 (M1) to 38; the cap's rate is 35% higher in relative terms
  The passivant: fluorine removes the S–C film and the SiOₓ as SF₆ and SiF₄: x₀ at −25 °C is 0.075 in
                 a continuous plasma, 15 times M1's 0.005 (Chapter 7)
  The stop:     SiN etches faster in fluorine; the overetch is shorter and ion-limited (22 s in M2)
  The rate:     B-ACL opens at 0.77 of ACL's rate in the same plasma
```

### 14.1.3 The M2 Process

```
M2 (1d-class, Book #31 array): 300 mm dual-frequency CCP
  Cap open (28 s)     60 nm SiON; CF₄ / CHF₃ / Ar (BARC 8 s, SiON 18 s, overetch 2 s)
  Main etch (209 s)   O₂ / COS / CF₄ 3% / Ar; 5 kHz bias, 70% duty, 600 eV; −25 °C;
                      cyclic: 1.5 s deposition (SO₂/COS/Ar, no bias) + 4.5 s etch, 35 cycles
  Overetch (22 s)     as the main etch
  Total               259 s;   ER₀ 560 nm/min (time-averaged); exit rate 5.8 nm/s;   ∂h/∂w = 11.0 nm per nm
```

```
M1 and M2 compared (the numbers of Chapters 1–13):
                               M1 (1b)        M2 (1d)
  Pitch / exit CD              45 / 31 nm     37 / 26 nm
  Mask after open              1350 nm        1450 nm
  Hole aspect ratio at exit    44             56
  Web (nominal, at bow)        14 / 12.2 nm   11 / 9.5 nm   (web AR 96 / 132)
  Bow                          0.67 nm        0.46 nm
  Wiggle (3σ)                  0.70 nm        0.77 nm       (limit 1.0 / 0.82)
  Cap                          40 nm SiON     60 nm SiON
  ACL:SiON                     51             38
  Top loss; edge height        50; 1210 nm    50; 1333 nm
  Total plasma time            184 s          259 s
  Platform throughput          66.1 wph       48.2 wph
  Module cost                  $15.1          $24.0
```

---

## 14.2 Three Masks for the 1d Array

For the 1d capacitor of Book #31 three masks are candidates. At the same −25 °C, cyclic conditions (the conditions of M2), with the opening time from the ARDE model and the cap that holds a top-loss exposure of 17.9 s:

```
1d-class mask options (illustrative; w = 26 nm; mask-open module only):
                                  Undoped ACL     B-ACL (M2)      W-ACL
  Deposited                       1800 nm         1500 nm         1150 nm
  Hole aspect ratio after open    67              56              42
  Open rate ER₀ (nm/min)          654             560             327
  Main etch                       224 s           209 s           259 s
  Total plasma (cap + ME + OE)    274 s           259 s           309 s
  ACL:SiON (blanket)              51              38              30
  Cap that holds x = 17.9 s       56 nm           60 nm           55 nm
  Chemistry                       O₂ / COS        + CF₄ 3%        + Cl₂ / CF₄
  Residue and contamination       sulfur          sulfur, B₂O₃    tungsten (WOₓ, WFₓ), sulfur
  Strip                           O₂ ash          O₂ ash, F       wet and dry; metal in the chamber
  Effective selectivity in the    2.3             3.5             4.8
   mold etch (Book #31)
  Module cost (mask open only)    $22.3           $24.0           $29.2
```

On the cost of the mask open alone, the undoped film is the cheapest of the three: it opens fastest, deposits cheapest, and needs a cap of about the same thickness. It loses elsewhere. At 1.8 µm the mask is a 67:1 tube after the open (Book #31 counts 69:1 from the deposited height) in front of the tube the mold etch cuts, its effective selectivity of 2.3 forces a taller mold-etch time, and Book #31 shows that these dominate; the mask-open saving of $1.7 per wafer is smaller than the mold-etch cost that comes with it. **The mask-open module cannot be optimized alone: its cheapest answer for the 1d array is the wrong one for the module.**

Tungsten-doped carbon is the most selective, opens slowest, costs most, and brings metal into a front-end chamber: tungsten oxide and fluoride residues that survive the strip. It is considered only where nothing else is tall enough.

---

## 14.3 Hybrid Caps

### 14.3.1 Removing the Cliff

Chapter 2 showed that the carbon's height after the open is bounded by the cap's thickness and its selectivity. A silicon hybrid cap, a thin layer of poly-silicon under the SiON, raises the selectivity by a large factor and removes the cliff. For M2:

```
Hybrid cap (25 nm poly-Si under the SiON ARC; M2 plasma, T = 230.5 s, ER_top = 9.33 nm/s):
  ACL:Si selectivity     60       80       100      150
  Cap life t₀ (s)        140      186      233      349
  Exposed time x (s)     90.7     44.2     −2.4     none
  → the cliff vanishes when ACL:Si ≥ 100:  L = 0, mask after open 1500 nm (+50 nm over M2)
```

The silicon must hold its selectivity in the fluorine-containing plasma, and fluorine etches silicon as readily as it etches carbon's boron. At ACL:Si of 80 the cap is as bad as SiON; at 100 the cliff is gone. A hybrid cap is therefore only worth having if the CF₄ is held to 3% or below, which is also what M2's passivation wants.

### 14.3.2 The Cost

```
M2 with a 25 nm poly-Si cap:
  Stack                   resist / BARC / SiON (20 nm) / poly-Si (25 nm) / B-ACL
  Added steps             Cl₂ / HBr silicon open (12 s); poly-Si deposition ($0.9)
  Added time              +12 s (259 → 271 s; 48.2 → 46.3 wafers/h)
  Module cost             $25.6   (+$1.6 over M2)
  Gain                    top loss 50 → 0 nm; edge margin 233 → 400 nm; no cliff; remaining mask 1500 nm
```

The silicon is stripped with the carbon after the capacitor etch, but only if the strip chemistry attacks neither the pillars nor the mold. The hybrid cap is a candidate for the 1d-class and beyond, not a certainty.

---

## 14.4 Colder Wafers

The bow of M2 is proportional to the bare lateral rate, which falls by an order of magnitude every 35 K:

```
Wafer at −60 °C (cryogenic chuck), M2 chemistry:
  v_b factor from 10 °C:           0.0035  (from −25 °C: 0.040)
  Bow (at x₀ = 0.0265)             0.46 × 0.040 = 0.02 nm
  ER₀                              560 × (1 − 0.003 × 35) = 501 nm/min  (−10%)
  Main etch                        209 → 233 s (+24 s)
  Cap at 60 nm                     t₀ 212.6 s, T = 255 s: x = 42 s > τ_w:  L = 8.35 × (42 − 15) = 229 nm  ✗
  Cap needed for x = 17.9 s        a cap of 67 nm  (+12%)
```

Colder wafers reduce the bow to nothing, and they pay for it twice: a longer open, and a cap that has to be 12% thicker to hold it. There is no free lunch in temperature. What the cold wafer allows, once the bow has gone, is a thinner passivation (less COS, less cyclic time) and a faster cycle, and the net can be positive for the 4F² and the extreme arrays. The chuck is the limit: SO₂ at −60 °C adsorbs strongly, the foot film thickens at the cold bottom of the tube, and the closure tail of Chapter 13 gets heavier.

---

## 14.5 4F² Vertical-Channel DRAM (M3)

### 14.5.1 The Array

Book #31 builds the 4F² cell at F = 15 nm: a square grid of pitch 2F = 30 nm, a cell of 900 nm², holes of 21 nm top CD, a mold of 1.82 µm and a hole aspect ratio of about 100. The mask for it:

```
4F² mask (illustrative): B-ACL 1500 nm, cap 64 nm; square grid, pitch 30 nm; exit CD 21.0 nm; cap CD 22.0 nm
  Open fraction                     π × 21² / 4 / 900 = 38.5%
  Web on the axes                   30 − 21 = 9 nm;       along the diagonals 30√2 − 21 = 21.4 nm
  Hole aspect ratio at exit         1450 / 21 = 69;    web aspect ratio  1450 / 9 = 161
  Wall area per hole / per wafer    π × 21 × 1450 = 9.6 × 10⁴ nm² / 1.5 m²
  Holes per die                     1.718 × 10¹⁰; array area 0.155 cm² (1b: 0.298 cm²)
```

### 14.5.2 The Open

The same chemistry and cycle as M2, with a 21 nm hole. The model of Chapters 3 and 7, with the decay lengths for d = 21 nm (ℓ_O 1485, ℓ_p 542, ℓ_c 41 nm), gives:

```
M3 (4F², B-ACL, −25 °C, cyclic, x₀ = 0.0265):
  Process time               cap open 30 s + ME 220 s + OE 24 s = 274 s (45.9 wafers/h)
  Exit rate                  5.3 nm/s;     ∂h/∂w = 15.6 nm per nm
  Top CD / bow / bow depth   22.07 nm / 0.51 nm / 310 nm;   maximum CD 22.58 nm
  Web on the axes at the bow 30 − 22.58 = 7.4 nm   (82% of the 9 nm nominal)
  Coverage at the exit       87% (θ), against 98.6% in M1
  Cap for x = 17.9 s         64 nm   (T = 244 s; ACL:SiON 38)
  Wiggle (3σ)                0.90 nm (E 105 GPa, t 9.0 nm, H 1450 nm, t_s 1.2 nm, σ_a 0.30%)
  Specification (axis web ≥ 7.5 nm; wiggle ≤ 0.67 nm, the 45 nm value scaled by 30/45)     ✗   ✗
```

The 4F² open misses in two places. The **web on the axes** is 0.1 nm short, and a stronger deposition fraction (2.0 s of deposition, 4.0 s of etch; x₀ = 0.020) restores it (bow 0.39 nm, web 7.56 nm) at a cost of 28 s and about 7 nm of cap (+$1.0 per wafer, module cost about $25.9). The **wiggle** is 0.23 nm too large: the 9 nm web is thinner than M2's, and the wiggle goes as 1/t². The ways out are those of Chapter 12: a face asymmetry of 0.20% instead of 0.30% (wiggle 0.60 nm ✓), a stiffer film (W-ACL: 0.54 nm), or a thinner skin (t_s 1.0 nm: 0.75 nm, not enough alone). **The 4F² mask is the first in the book whose specification is set by its mechanics.**

### 14.5.3 The Square Mesh

The square grid is a mesh of walls 9 nm thick along both axes joined at nodes 21.4 nm wide. The ellipticity is directional: the open can widen the hole toward its diagonal neighbours, where the wall is 21.4 nm, but must not widen it along the axes. The hexagonal ellipticity of Chapter 12 becomes a square distortion, and it is harmless if the flats face the axes (Book #31).

---

## 14.6 3D DRAM

The vertical etches of 3D DRAM (slits and holes through a superlattice of silicon and silicon-germanium, Book #31, Chapter 14) are done in halogen chemistry, and the mask for them is carbon opened in the oxygen plasma of this book. Three things change:

```
3D DRAM mask open (illustrative):
                                   Capacitor (M1)        3D DRAM hole / slit
  Material etched                  SiO₂ / SiN            Si / SiGe (Cl₂, HBr)
  Effective selectivity to ACL     2.3–2.6               ≈ 8–12  (halogens barely attack carbon)
  Mask needed                      1400 nm               ≈ 1000 nm for a 3 µm stack
  Hole CD, aspect ratio of the mask   31 nm, 44          40 nm, 25
  Main etch (M1 conditions)        144 s                 94 s     (G = 1000 + 138 + 2 = 1140 nm; ER₀ 12.17 nm/s)
  Cap                              SiON, a cliff         SiON, no cliff (halogens barely attack it)
```

The mask open for 3D DRAM is **easier** than the capacitor's: a thinner, wider mask with a cap that the halogen etch does not attack. What it adds are shapes. A slit mask is a set of fins of carbon 40 nm wide, 1.0 µm tall, and tens of micrometres long. The bimorph of Chapter 12 acts on a fin along its whole length, and the sideways stiffness of a long fin is lower than that of a honeycomb web by the ratio of the spans, so the mask has to be designed with bridges. The physics of the transport, the passivation, and the cap carries over unchanged.

---

## 14.7 All the Routes on One Page

```
Hard mask open: the routes of the book (illustrative):
  Route              Array      Mask (deposited)   AR   Web (bow)  Bow    Time    Cap     Loss    Edge    Module
                                                                    (nm)   (s)     (nm)    (nm)    height  cost
  ───────────────────────────────────────────────────────────────────────────────────────────────────────────────
  M0 baseline        1b, hex    1400 ACL           44   10.5       2.0    181     40      62      1173    $14.4
  M1 reference       1b, hex    1400 ACL           44   12.2       0.67   184     40      50      1210    $15.1
  M1-c (cap 42)      1b, hex    1400 ACL           44   12.2       0.67   185     42      14      1299    $15.2
  M2 1d              1d, hex    1500 B-ACL         56   9.5        0.46   259     60      50      1333    $24.0
  M2 + Si cap        1d, hex    1500 B-ACL         56   9.5        0.46   271     25 Si   0       1500    $25.6
  M3 4F²             4F², sq.   1500 B-ACL         69   7.4 (axis) 0.51   274     64      50      1333    $24.9
  3D DRAM hole       3D         1000 ACL           25   —          —      ≈ 134   40      —       —       —
```

---

## Summary and Key Takeaways

1. **Boron needs fluorine, and fluorine costs the cap and the passivation.** CF₄ 3% carries boron off as BF₃, lowers ACL:SiON from 51 to 38, and raises the passivant removal 15-fold at −25 °C; the cyclic scheme brings it back.

2. **The mask-open module cannot be optimized alone.** An undoped 1.8 µm mask is the cheapest to open ($22.3 against $24.0 for B-ACL) and the most expensive in the mold etch that follows.

3. **A silicon hybrid cap removes the cliff.** At ACL:Si ≥ 100 the cap outlasts the open (L = 0, mask 1500 nm) for +$1.6; at ACL:Si of 80 it is no better than SiON.

4. **Cold is not free.** At −60 °C the bow is 0.02 nm, the open 24 s longer, and the cap has to be 12% thicker (67 nm).

5. **The 4F² open is limited by its mechanics.** Web on the axes 7.4 nm (0.1 nm short), wiggle 0.90 nm (limit 0.67); both can be fixed (a stronger deposition fraction; a 0.2% face asymmetry or a stiffer film).

6. **3D DRAM's mask open is easier, its shapes are not.** Halogen etches are 8–12 selective to carbon: a thinner mask (1.0 µm), no cliff, and long fins that need bridges.

7. **Every scheme pays in cap or time.** M2 needs 60 nm of cap for a 7% taller mask; M3 needs 64 nm; the hybrid needs a new film.

---

## Study Questions

1. For the 1d array compute the main-etch time of an undoped ACL of 2000 nm at the M2 conditions (w = 26 nm, k = 0.010, k₂ = 8 × 10⁻⁶, ER₀ = 654 nm/min), and the cap that holds x = 17.9 s if ACL:SiON = 51 (use ρ = 1.15).

2. A hybrid cap with ACL:Si = 120 and 20 nm of poly-Si is used on M2. Find t₀ and x, and the margin by which the cap outlasts the open. What is the least thickness at which the cap outlasts a total time of 230.5 s?

3. At −40 °C, find the bare lateral rate factor relative to −25 °C (E_a = 0.42 eV), the bow of M2, and the extra main-etch time if ER₀ falls by 0.3% per K.

4. For the 4F² open the deposition fraction is raised so that x₀ = 0.020. Using the proportionality of bow to x₀ at small x, find the bow and the axis web, starting from 0.51 nm and 7.42 nm at x₀ = 0.0265.

5. Compute the wiggle of the 4F² mask for a W-ACL (E = 130 GPa, H = 1250 nm, t = 9.0 nm, t_s = 1.2 nm) at σ_a = 0.30%. Does it meet 0.67 nm?

6. A 3D DRAM hole mask has a CD of 36 nm and a depth of 1100 nm. Using k = 0.011 and k₂ = 10⁻⁵ and ER₀ = 730 nm/min, find the main-etch time and the aspect ratio.

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
