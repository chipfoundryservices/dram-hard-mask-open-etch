# Chapter 2: The Mask Stack — Carbon Films, Cap, Resist & the Incoming Surface

## Overview

The mask open cuts through four films, and each decides something about the etch. The **carbon** sets the rate, the aspect ratio, and how fast the oxygen attacks the wall. The **cap**, a 40 nm layer of silicon oxynitride, sets how long the carbon can be etched before its own top begins to erode. The **resist and underlayer** set the CD and the roughness the etch inherits, and are consumed before the carbon is touched. The **mold's top nitride** sets where the etch stops.

This chapter describes the incoming stack film by film: the families of carbon film and what their hydrogen and density do to the plasma, the cap and why its thickness is a cliff edge, the short etch that opens the cap, the budget that sets the carbon at 1400 nm, the stress and bow the film brings, and the incoming specification the open needs. One result, derived in Section 2.4, runs through the rest of the book: **at a fixed cap, a taller mask stops being taller.** Past about 1430 nm, more carbon only lengthens the open, and the cap gives it back as top loss.

**Learning Objectives:**
- Compare the families of carbon mask (PECVD ACL, HD-ACL, SOC, B-ACL, W-ACL) by density, hydrogen, stiffness, and rate
- Estimate the etch rate of a carbon film from its hydrogen content and density
- Explain why the cap thickness sets a ceiling on the mask height after the open
- Budget the SiON open: resist, underlayer, cap, and overetch
- Derive the 1400 nm carbon thickness from the capacitor etch's mask budget
- Estimate the wafer bow before and after the open, and the open time lost to film variation
- State the incoming specification of the stack

---

## 2.1 Carbon Film Families

### 2.1.1 The Reference: PECVD ACL

```
Reference ACL (illustrative; Book #29):
  Deposition            PECVD from C₃H₆ (or C₂H₂) and He, 400–600 °C
  Thickness             1400 ± 14 nm (3σ); within wafer 0.8%, wafer to wafer 0.6%
  Density               1.80 ± 0.02 g/cm³
  Hydrogen              17 ± 1 at%
  Young's modulus       ≈ 75 GPa
  Stress                −300 ± 30 MPa (compressive)
  Extinction coeff.     k ≈ 0.4 at 633 nm (opaque to alignment light)
```

It is amorphous hydrogenated carbon with a mix of sp³ and sp² bonds. Raising the deposition temperature drives hydrogen out (from about 20 at% at 450 °C to 12 at% at 550 °C, −0.08 at% per °C), raises the density and the sp³ fraction, and raises the stress. The reference is the film for which the mold etch's selectivity of 5.5 was measured (Book #29).

### 2.1.2 Other Films

```
Carbon mask families (illustrative):
                      ρ        H or dopant     E      Stress   Rate vs.   Oxide sel.   Open chemistry
                      g/cm³                    GPa    MPa      ACL (M1)   blanket/eff.
─────────────────────────────────────────────────────────────────────────────────────────────────────────
PECVD ACL (ref.)      1.80     H 17 at%        75     −300     1.00       5.5 / 2.6    O₂/COS
HD-ACL (550 °C)       1.95     H 12 at%        100    −500     0.72       7 / —        O₂/COS, higher bias
SOC (spin-on)         1.35     H 35 at%        12     +20      2.7        2.5 / —      O₂/N₂, low bias
B-ACL (B 40 at%)      2.05     H 8 at%, B      105    −250     0.77 (F)   8–9 / 3.5    O₂/COS + CF₄ 3%
W-ACL (W 10 at%)      2.60     H 10 at%, W     130    −450     0.45       11–12 / 4.8  O₂ + Cl₂/CF₄
```

**HD-ACL** is the same film deposited hotter. It is harder, stiffer, and slower to open. **Spin-on carbon** is a polymer baked in place; it planarizes and is cheap, but it is soft and etches fast, and in this book appears only as a comparison; the support-open layer of Books #30 and #34 uses a 300 nm ACL, at an aspect ratio of 6. **B-ACL**, boron-doped carbon, is the mask of Book #31. Boron does not form a volatile oxide, so the open needs a few percent of CF₄ to carry it off as BF₃, and that fluorine also etches the cap (Chapter 14). **W-ACL** is harder still and contaminates; it is considered only where nothing else is tall enough.

### 2.1.3 Hydrogen and Density: What the Plasma Sees

For undoped films the open rate in oxygen chemistry tracks two properties. Hydrogen terminates carbon bonds, so each at% of hydrogen makes the film etch faster. Density sets how many carbon atoms must be removed per unit volume, and the rate falls as a power of it:

```
Relative open rate (undoped films, O₂-based plasma):
  R/R_ACL ≈ [1 + 0.03 (H − 17)] × (1.80/ρ)²        H in at%, ρ in g/cm³

  PECVD ACL    H 17, ρ 1.80:   1.00 × 1.00           = 1.00
  HD-ACL       H 12, ρ 1.95:   0.85 × 0.852          = 0.72
  SOC          H 35, ρ 1.35:   1.54 × 1.778          = 2.74
```

The same factor applies to the bare lateral rate of the wall (Chapter 3), so a softer film does not merely open faster: it bows faster. In M1 a switch to HD-ACL would cut ER₀ from 730 to 525 nm/min and lengthen the main etch from 144 s to 200 s, while reducing the bare lateral rate to 0.39 nm/s. A switch to SOC would do the reverse, tripling the bow. The film cannot be chosen for rate alone.

```
Variation inside a film (illustrative):
  Hydrogen ±1 at% (wafer to wafer)           ±3.0% in rate   → ±4.3 s of the 144 s main etch
  Temperature ±3 °C across the wafer
   (0.08 at%/°C × 3 = ±0.24 at%)             ±0.7% in rate   → ±1.0 s within the wafer
  Thickness ±14 nm (3σ)                      ±14 / 8.0 nm/s  → ±1.75 s
```

The wafer-to-wafer hydrogen term is the largest, and it is invisible to a thickness monitor. Chapter 15 feeds it forward from the deposition chamber's log.

---

## 2.2 The Cap

### 2.2.1 What the Cap Does

The 40 nm SiON cap does two jobs. It is an antireflective layer for the 193 nm lithography (n ≈ 1.9, k ≈ 0.4 at 193 nm). And it is the **hard mask of the carbon open**: after the SiON open removes the cap from the hole, the cap on the webs shields the carbon while the oxygen cuts it.

Oxygen plasma barely etches an oxide-like film. The cap erodes by ion sputtering and by the sulfur and fluorine in the gas, at 0.237 nm/s in M1 against 12.2 nm/s for the carbon at the top surface, a selectivity of 51. That sounds enormous. It is the thinnest margin in the module, because the carbon takes 162 s to open and the cap lasts only 169 s on a flat surface (and, as Section 2.2.3 shows, less on a 14 nm web).

### 2.2.2 Cap Materials

```
Cap options (illustrative; M1-type O₂/COS chemistry; ceiling from Section 2.2.3):
Cap                  ACL:cap   Open chemistry          Ceiling at     Notes
                     blanket                           this cap
──────────────────────────────────────────────────────────────────────────────────────────────
SiON, 40 nm (ref.)   51        CF₄/CHF₃/Ar             1353 nm        ARC and mask; reference
SiN, 40 nm           38        CF₄/CH₂F₂               1038 nm        stress; fluorine-sensitive
SiO₂, 40 nm          90        CF₄/CHF₃/Ar             2154 nm        best passivant source; no ARC
Poly-Si, 25 nm       150       Cl₂/HBr (then SiON)     2224 nm        thin; adds a Si open and strip
TiN, 15 nm           250       Cl₂/BCl₃                2224 nm        metal contamination
```

The ceilings assume the 1b-class etch law; at taller masks and a 37 nm pitch the aspect ratio and the ARDE change (Chapter 14). They are meant to show the scale, not the final answer: **a 25 nm silicon cap supports a mask 64% taller than a 40 nm SiON cap.**

### 2.2.3 Why the Cap Is a Cliff

The 14 nm web is too narrow to have a flat top. The cap on it is a ridge, and the ridge's two shoulders erode faster than a flat surface (the sputter yield peaks near 45° incidence; the model uses a factor of 1.15). Chapter 11 develops the model. Its result, for M1, is:

```
Cap life on the web:      t₀ = (40 nm / 0.237 nm/s) / 1.15 = 146.7 s
Open time (ME + OE):      T  = 144.4 + 18 = 162.4 s
Exposed time of the carbon top at the end:  x = T − t₀ = 15.7 s
Top loss  L = ER_top x² / (2 τ_w) = 12.17 × 15.7² / 60 = 50 nm     (τ_w = 30 s)

Sensitivity:  1 nm of cap  = 3.7 s of cap life = −21 nm of top loss (+1 nm: 50 → 29 nm)
              1 s of overetch  = +6.4 nm of top loss
```

The top loss grows as the square of the time the cap has failed, so the carbon below the cap is safe until it suddenly is not. What the mask open delivers is therefore not "thickness minus a constant" but a quantity that peaks, as the carbon is made taller, and then falls:

```
Mask height after the open versus carbon deposited (M1, 40 nm SiON cap):

  ACL dep.   ME (s)   T (s)   Cap failed   Top loss   After open
  (nm)                        for x (s)    (nm)       (nm)
  ──────────────────────────────────────────────────────────────
  1300       132.1    150.1      3.4          2          1298
  1350       138.2    156.2      9.5         18          1332
  1400       144.4    162.4     15.7         50          1350
  1450       150.7    168.7     21.9         98          1352
  1500       157.1    175.1     28.3        162          1338
  1600       170.0    188.0     41.2        319          1281

Ceiling by cap thickness (maximum height after the open):
  Cap (nm)     30     35     40     45     50     60
  Ceiling (nm) 1051   1205   1353   1497   1636   1901
```

**The cap sets a ceiling on the mask.** For a 40 nm cap the ceiling is 1353 nm. The reference 1400 nm of carbon sits just below the maximum, at the point where an extra nanometre of carbon costs about as much top loss as it adds. Every nanometre of cap adds about 29 nm to the ceiling. A taller mask without a thicker cap is no taller. The cap, and the uniformity of the cap, is the first thing to specify.

---

## 2.3 Resist, Underlayer & the SiON Open

### 2.3.1 The Short Etch Before the Long One

Before the carbon can be opened the pattern must be moved through the resist's underlayer and the cap. This is the SiON open, the first step of every route, a conventional fluorocarbon etch:

```
SiON open (ST1, M0 and M1; CF₄ 80 / CHF₃ 20 / Ar 300 sccm, 20 mTorr, 400 eV):
  BARC / underlayer, 25 nm, 190 nm/min       8 s
  SiON cap, 40 nm, 200 nm/min               12 s
  Overetch (clear the bottom, close the CD)  2 s
  ──────────────────────────────────────────────
  Total                                     22 s

  Resist consumed: 150 nm/min × 22 s = 55 nm
  ArF-i resist 80 nm:  25 nm remains
  Cap CD at the bottom of the SiON: 32.0 nm; at its top 33.0 nm (taper 89.3°)
```

The resist that remains is a convenience, not a requirement. It is carbon-like and goes in the first seconds of the main etch (Chapter 3). The cap CD of 32.0 nm is the CD the main etch inherits, and the hole's profile (Chapter 10) is measured from it.

### 2.3.2 EUV and the Thin Resist

An EUV resist of 35–40 nm does not survive 55 nm of consumption. EUV flows insert a 20 nm spin-on hard mask under the resist and open it in a short descum etch, or use a metal-oxide resist that is itself the mask. These routes change the shape and roughness of the cap opening (Chapter 4) but not the chemistry of the carbon open that follows. The book takes the ArF-immersion stack as the reference.

---

## 2.4 The Thickness Budget

### 2.4.1 Why 1400 nm

```
Mask thickness budget, from the capacitor etch backwards (M1):

  Mold etch consumption (Book #29, 305 s)                 576 nm
  Facet allowance                                          40 nm
  Remaining mask, minimum                                 500 nm
  ──────────────────────────────────────────────────────────────
  Required at the start of the mold etch (floor)         1116 nm
  Margin carried by Book #29's specification              214 nm
    (mold thickness, longer overetch, facet tails)
  After-open specification, 3σ lower bound               1330 nm

  Mean after the open                                    1350 nm   (3σ: ± 18 nm)
  Top loss in the open                                     50 nm
  ──────────────────────────────────────────────────────────────
  Carbon to deposit                                      1400 nm   (± 14 nm, 3σ)
```

The 3σ of the after-open height is the root-sum-square of the film (±14 nm) and the top loss (±12 nm, from a cap uniform to 1.0% in thickness and 0.8% in erosion rate; Chapter 11): √(14² + 12²) = 18.4 nm. The lower bound is 1350 − 18 = 1332 nm, above the 1330 nm specification by 2 nm. The margin is thin.

### 2.4.2 A Thicker Mask Eats Itself

```
Carbon-height cost of the open (M1):
  Open time per 100 nm of carbon          G′(h)/ER₀ = 1.517 / 12.17 nm/s × 100 nm = 12.5 s
  Cap needed to hold a 15.7 s exposure:   40.0 nm at 1400;  43.4 nm at 1500;  47.0 nm at 1600
  Cap per carbon:                         3.4 nm per 100 nm
```

Each added 100 nm of carbon lengthens the open by 12.5 s, and the extra time all lands on a cap with the same life. A 100 nm gain in carbon at 1400 nm yields a net **loss** of 13 nm of mask (1500 nm deposited gives 1338 nm against 1350 nm). A taller mask is bought with cap, at 3.4 nm per 100 nm, and with a longer open.

---

## 2.5 Film Variation, Stress & Bow

```
Incoming variation and what it does to the open (M1):
                                    3σ            Effect
  ACL thickness                     ±14 nm        ±1.75 s of main etch; ±14 nm of mask height
  Cap thickness                     ±0.4 nm       ±1.5 s of cap life; ±9.3 nm of top loss
  Cap erosion rate (chamber)        ±0.8%         ±1.2 s of cap life; ±7.4 nm of top loss
  Cap life, combined                              ±1.9 s → top loss ±11.9 nm
  ACL hydrogen (wafer to wafer)     ±1 at%        ±3.0% in rate: fed forward (Chapter 15)
```

The film stress bends the wafer. Using Stoney's relation with the parameters of Book #29, 1.4 µm of carbon at −300 MPa on a 775 µm silicon wafer gives a curvature of 0.0232 m⁻¹ and a sag across 300 mm of 261 µm, which backside films reduce to a net bow below 120 µm before clamping. The open changes the balance:

```
Force in the carbon:  σ t × (solid fraction)
  Array fraction of the wafer     37.9%
  Carbon removed in the array     43.5%
  Force removed                   0.379 × 0.435 = 16.5% of the film's total
  Change in the film's bow         0.165 × 261 µm ≈ 43 µm (261 → 218 µm, before backside films)
```

The wafer arrives at the capacitor etch with a different bow than the one at the open, which shifts the edge temperature through the helium gap (Book #29, Chapter 8) and, by a small in-plane strain, the hole positions. Chapter 12 returns to the in-plane part.

---

## 2.6 The Incoming Surface & Specification

```
Incoming specification for the hard mask open (reference, illustrative)

Carbon
  Thickness                        1400 ± 14 nm (3σ); within wafer ≤ 0.8%
  Density / hydrogen               1.80 ± 0.02 g/cm³ / 17 ± 1 at%
  Stress                           −300 ± 30 MPa
  Particles on the surface         ≤ 0.02 per cm² at ≥ 40 nm (before the cap)

Cap
  SiON thickness                   40.0 ± 0.4 nm (3σ); within wafer ≤ 0.7%
  Refractive index n (193 nm)      1.90 ± 0.02; k 0.40 ± 0.02
  Surface roughness                ≤ 0.4 nm rms
  Queue, carbon to cap             ≤ 8 h

Pattern (Chapter 4)
  Cap CD at the bottom             32.0 ± 1.0 nm; family offset ≤ 1.0 nm
  LCDU (3σ)                        ≤ 2.4 nm;  edge roughness ≤ 2.5 nm
  Overlay to the landing pads      ≤ 5 nm (mean + 3σ)

Wafer
  Bow before clamp                 ≤ 120 µm
  Backside particles               ≤ 30 (≥ 0.2 µm)
  Queue, pattern to open           ≤ 24 h
```

The most unusual line is the cap: **40.0 ± 0.4 nm**. It is the tightest film-thickness specification in the module, because a 1.0% error in cap life is worth 9 nm of mask height. A deposition that cannot hold it, and a metrology that cannot see ±0.4 nm, move the problem into the open as an inexplicable spread in mask height (Chapter 11).

---

## Summary and Key Takeaways

1. **The carbon's hydrogen and density set the rate and the bow.** Rate ∝ [1 + 0.03 (H − 17)] (1.8/ρ)²: HD-ACL is 0.72, SOC 2.7. The lateral rate follows, so a faster film bows faster.

2. **The cap is a clock, not a mask.** A 14 nm web carries a ridge whose shoulders erode first. At 40 nm of SiON the carbon is exposed for 15.7 s at the end of the open, and the top loss grows as the square of that time.

3. **The cap sets a ceiling on the mask.** At 40 nm of SiON the highest mask after the open is 1353 nm; more carbon gives less. Each nanometre of cap adds about 29 nm of ceiling.

4. **The thickness is budgeted backwards.** 1116 nm floor + 214 nm margin = 1330 nm at 3σ; plus 50 nm of top loss and 20 nm of spread: 1400 nm of carbon.

5. **Film variation enters as time.** ±14 nm of carbon is ±1.75 s; ±1 at% of hydrogen is ±4.3 s; the cap, at ±0.4 nm, is ±1.5 s of cap life and ±9 nm of top loss.

6. **The open changes the bow.** Removing 43.5% of the carbon from 38% of the wafer removes 16.5% of the film force, a change of about 43 µm in bow.

---

## Study Questions

1. Using the rate model of Section 2.1.3, find the relative open rate of a film with H = 14 at% and ρ = 1.88 g/cm³. By what time does M1's main etch lengthen if that film replaces the reference ACL (the carbon is 1400 nm and the rate ER₀ falls in proportion)?

2. A hot deposition raises the hydrogen content from 17 to 15 at% on one wafer. Estimate the change in main-etch time and in top loss, using ∂L/∂T = 6.4 nm/s.

3. The cap is thinned to 39.0 nm by a CMP-like deposition error. Using Section 2.2.3, find the new cap life, the exposed time x, and the top loss. Does the wafer meet the 1330 nm specification?

4. Using the ceiling table of Section 2.2.3, interpolate the cap thickness whose ceiling is 1450 nm. How much more cap than the 40 nm reference is needed to support a 1500 nm mask at the reference top loss (Section 2.4.2)? Compare the two answers.

5. The array fraction of a new product is 45% and its open fraction is 40%. Compute the change in wafer bow from the open, using a carbon sag of 261 µm.

6. Show that the 3σ lower bound of the after-open height is 1332 nm when the carbon and the top loss each vary independently, and find the cap uniformity (3σ, in nm) at which the lower bound falls to 1330 nm.

---

**Next Chapter:** [Chapter 3: Plasma Chemistry of the Carbon Open](./03-carbon-open-plasma-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
