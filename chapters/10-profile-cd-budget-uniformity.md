# Chapter 10: Mask Profile, CD Budget & Uniformity

## Overview

The profile of an opened hole is a curve, and a specification has to be a few numbers. The sidewall angle, the usual summary, is the wrong number for a mask 1350 nm tall with 31 nm holes: a change of 0.02° moves the CD by a nanometre, and no cross-section measures an angle to that precision. This chapter replaces the angle with three heights: the **top CD**, which sets the web where the cap sits; the **bow**, which sets the thinnest web; and the **exit CD**, which sets the aperture through which the capacitor etch's ions enter. It gives the three for the three routes and says what each one is for.

It then builds the CD budget from the cap to the exit, with the root-sum-square that meets the ±1.0 nm of Book #29, and turns to uniformity: the radial profile of the wafer, the **array-edge effect** on the outermost rows of every cell block, and the loading that a change of product puts on the chamber. Every item in the chapter is a place where the open's error becomes the capacitor etch's input with a gain of one or more.

**Learning Objectives:**
- Specify a mask profile at three heights and say what each is for
- Explain why the sidewall angle cannot be a specification for a 44:1 mask
- Compute the minimum web from the bow and the pitch
- Build the exit-CD budget as a root-sum-square and verify it against the ±1.0 nm specification
- Describe the radial profile and the array-edge effect, and the dummy rows that control the second
- Estimate the change in chemical load for a product with a different array efficiency

---

## 10.1 The Column at Three Heights

### 10.1.1 The Profile of Each Route

```
Mask profile after the open (illustrative; models of Chapters 3 and 7):
                                    M0 (1b)    M1 (1b)    M2 (1d)
  Cap CD (bottom of the SiON)       32.0       32.0       27.0 nm
  Top CD (just below the cap)       32.5       32.1       27.1 nm
  Depth of the bow                  450        370        340 nm
  CD at the bow (maximum)           34.5       32.8       27.5 nm
  Bow (maximum − top CD)            2.0        0.7        0.46 nm
  CD at 700 nm                      34.3       32.7       27.5 nm
  CD at 1000 nm                     33.7       32.5       27.4 nm
  Exit CD                           31.0       31.0       26.0 nm
  Mean CD over the depth            33.7       32.5       27.3 nm
  Pitch                             45         45         37 nm
  Minimum web (pitch − maximum CD)  10.5       12.2       9.5 nm
  Local foot angle (last 50 nm)     89.1°      89.3°      89.3°
  Average angle over the full depth 89.97°     89.98°     89.98°
```

M0's profile is a bowed barrel: 32.5 nm at the top, 34.5 nm at 450 nm, and 31.0 nm at the exit. M1's is nearly straight, with a hump of 0.7 nm at 370 nm and a foot at the exit. M2's, at a smaller scale, is the same shape as M1's.

### 10.1.2 What Each Height Is For

```
Height           Quantity               What it sets                                         Controlled by
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Top (z = 0)      Top CD, 32.1 nm        Web under the cap (12.9 nm); width of the cap's      Cap CD; passivation by the cap's
                                        ridge; the top CD of the capacitor mold hole         own SiOₓ (Chapter 3)
Bow (z*)         CD at the bow, 32.8    Minimum web (12.2 nm); mask integrity; mask          Temperature, COS flow (Chapter 6)
                                        bridging; the web's margin to merging (17σ)
Exit (z = h)     Exit CD, 31.0 nm       Aperture for the capacitor etch's ions and           Ion flux, overetch, foot (Chapters 3, 6)
                                        neutrals; top CD of the mold hole; ∂h/∂CD = 15
```

**The exit is the quantity that the capacitor etch inherits.** The ions of the mold etch see the narrowest aperture, which is the foot. A hole bowed to 34.5 nm above a 31.0 nm exit presents the same aperture as one bowed to 32.8 nm above the same exit; what the bow changes is the web, and with it the mask's integrity and the odds of merging, not the aperture.

---

## 10.2 The Angle Is the Wrong Number

A sidewall angle of 89.98° over 1350 nm describes a taper of 0.38 nm per side. Specifying it to a precision that bears on the CD means:

```
Angle precision needed to hold the CD change over the full height to 1 nm (0.5 nm per side):
  Δθ = atan(0.5 nm / 1350 nm) = 0.021°
Precision of an angle measured by XTEM or CD-SAXS:   ≈ 0.1°
```

The measurement is five times too coarse to enforce the specification. And an angle averaged over the whole wall hides what matters: the bow, which adds and subtracts as it goes, and the foot, which closes in the last 50 nm and changes the exit by 1.2 nm. Book #29's 89.3° is, as Chapter 1 explained, the local angle of the foot. **A profile specification for a 44:1 mask is three CDs at three heights, plus the local foot angle, plus the thickness.**

---

## 10.3 The Bow and the Web

### 10.3.1 The Web at the Bow

The web is the narrowest wall between two neighbouring holes. At the bow:

```
t_web = p − CD_bow         (hexagonal nearest neighbours, p = 45 nm)
  M0: 45 − 34.5 = 10.5 nm      M1: 45 − 32.8 = 12.2 nm      M2: 37 − 27.5 = 9.5 nm

Web as a fraction of the nominal (p − exit CD):
  M0: 10.5 / 14.0 = 75%        M1: 12.2 / 14.0 = 87%        M2: 9.5 / 11.0 = 86%
```

M0's web is a quarter thinner than the nominal; M1's, an eighth. The consequence that is not obvious is that the **stiffness of the mask is set at the bow**: a web of 10.5 nm is 25% thinner than one of 14 nm and, since the bending stiffness goes as the cube of the thickness, has only 0.75³ = 0.42 of its stiffness. Chapter 12 uses it.

### 10.3.2 The Bow Specification

The specification of Chapter 1 is a bow of at most 1.0 nm and a minimum web of at least 11.0 nm. They are linked: a bow of 1.0 nm over a top CD of 32.1 nm is a CD of 33.1 nm and a web of 11.9 nm; the web limit of 11.0 nm allows a bow of 1.9 nm from the same top. The web limit is the wider of the two; the bow limit is the one that bites, because it protects the capacitor etch from a hole whose top is narrower than its middle, and from a mask whose cap is undercut.

---

## 10.4 The Foot and the Exit

### 10.4.1 The Exit

```
Foot model (Chapter 3):  CD(z) = CD_wall(z) − 2 f₀ exp[−(h − z)/λ_f]
  M1:  f₀ = 0.60 nm, λ_f = 49 nm     local angle at the exit atan(0.60/49) → 89.3°
  M0:  f₀ = 0.88 nm, λ_f = 56 nm     89.1°
  M2:  f₀ = 0.56 nm, λ_f = 46 nm     89.3°

  Exit CD = cap CD + 2 (wall movement at the exit) − 2 f₀ :
                                    M1: 32.0 + 2 × 0.10 − 2 × 0.60 = 31.0
```

The foot is a film of redeposited fragments that thickens toward the front of the etch. It is the one part of the hole that no passivation controls and that all of the next etch's ions see first. Its width at the exit sets the aperture, and the aperture sets two things: the top CD of the mold hole, and the ion acceptance of the capacitor etch's tube.

### 10.4.2 The Exit and the Mold Hole

```
Book #29: exit CD 31.0 nm → mold hole top CD 31.0 nm at the start; 32.0 nm at the mold top at the end of the etch
          depth sensitivity ∂h/∂CD = 15.2 nm per nm
Exit CD error of 1.0 nm (3σ)  →  15 nm of depth lag in the mold hole at fixed time
```

---

## 10.5 The CD Budget

### 10.5.1 From the Cap to the Exit

The exit CD must be 31.0 ± 1.0 nm (3σ, site means, per family). The contributors, each as a 3σ spread in nm of site-mean exit CD:

```
Exit CD budget (M1; site means, 3σ):
  Contributor                                            3σ (nm)
  ───────────────────────────────────────────────────────────────
  Cap CD from lithography (site mean 0.60 nm × G = 1.10)   0.66
  SiON open: bias, resist remaining, 2 s overetch          0.30
  Foot and redeposition: flux at the exit, wall state      0.30
  Within-wafer uniformity (radial, Section 10.6)           0.35
  Chamber to chamber (after matching, Chapter 5)           0.40
  Wafer to wafer (drift; APC residual, Chapter 15)         0.30
  ───────────────────────────────────────────────────────────────
  RSS                                                      0.99 nm      specification ±1.0 nm
```

The budget is met with 0.01 nm to spare. The largest term is the lithography, which the open amplifies by its gain of 1.10 (1.30 in M0). The two terms the open controls, the SiON bias and the foot, are the smallest. What the open does about the largest term is nothing: it transfers it. What it does about the others is the subject of the previous seven chapters.

### 10.5.2 CD and the Cap

The cap CD and the exit are linked by the net bias of −1.0 nm. A change of recipe that changes the bias, a trim at the cap level or a longer SiON overetch, shifts the whole budget:

```
Shifts of the exit CD (M1):
  SiON overetch +1 s       cap CD +0.1 nm → exit +0.11 nm
  Wafer temperature +1 K   foot unchanged; bow +0.04 nm; exit unchanged (±0.02)
  COS flow +5 sccm         bow −0.04 nm; exit unchanged
  Ion flux (source power) +10%   exit +0.05 nm  (thinner foot; illustrative)
```

The exit CD is **insensitive to the passivation levers** that set the bow. That separation is what allows the bow and the exit to be controlled by different knobs.

---

## 10.6 Uniformity

### 10.6.1 Across the Wafer

```
Radial profile of the exit CD (M1, site means, relative to the centre; illustrative):
  r (mm)          0      50     100    130    147
  Exit CD (nm)    0.00   −0.05  −0.10  +0.12  +0.40
  Bow (nm)        0.67   0.66   0.66   0.70   0.76
  Edge-zone temperature +1 K accounts for 0.04 nm of the bow; the rest is edge tilt and ring
```

The exit CD rises toward the edge by 0.4 nm: the sheath bends over the step at the edge ring, more ions arrive at the periphery of the hole, and the foot is thinner. The ESC's edge zone is trimmed, and the ring is replaced at 25 µm of wear. The within-wafer 3σ of site means is 0.35 nm, as in the budget.

### 10.6.2 The Array Edge

Each die has several blocks of cells with a periphery around them that is covered and not opened. The holes at the edge of a block see a different environment from the holes in the middle: more oxygen (no neighbours to compete), and passivant from the cap of the periphery:

```
Exit CD offset of row n from the edge of an array block (M1; illustrative):
  Row n                         1       2       3       4       5
  Offset (nm)                   +0.55   +0.27   +0.13   +0.07   +0.03     (0.55 e^−(n−1)/1.4)
  With 2 dummy rows
  (functional row 1 = row 3)    —       —       +0.13   +0.07   +0.03
```

The offset decays with a length of 1.4 rows. Two **dummy rows** of holes around every block, patterned and opened but not connected, move the functional edge to row 3, where the offset is 0.13 nm, within an edge-effect budget of 0.2 nm. The cost is area: two rows around a block of 1000 × 1000 cells are 0.8% of its area, around a block of 32 × 32 cells, 27%.

A second, slower edge effect comes from the film's stress: at the free edge of a block the carbon relaxes by a few nanometres, and the displacement decays over about the film thickness, tens of rows. Dummy rows do not cure it. Chapter 12 treats it.

### 10.6.3 Loading and the Product Change

The chemical load of the open depends on the open area (Chapter 1). A product with a different array efficiency has a different load:

```
Oxygen consumed by the wafer (O₂ equivalent, M1 main etch, 150 sccm O₂ supplied):
  Array efficiency (array area / die area)     0.30      0.379 (reference)     0.45
  Consumed (sccm)                              8.5       10.8                  12.8
  Fraction of the oxygen supply                5.7%      7.2%                  8.5%
```

A change of ±0.07 in array efficiency changes the consumption by ±2 sccm, ±1.3% of the supply. The effect on the bow and the exit is smaller than the matching (±0.15 nm), but the endpoint's baseline changes (Chapter 8: the CO drop is 40% at 0.379 and 44% at 0.45), and the recipe is **qualified per product**: APC carries a product constant for the array efficiency, as Book #29 does for the capacitor etch.

---

## Summary and Key Takeaways

1. **Specify three CDs and a foot angle.** Top (the web under the cap), bow (the minimum web), exit (the aperture); the foot angle is local and the full-height angle is 89.98°.

2. **The angle is unmeasurable at the precision that matters.** 0.021° moves the CD 1 nm; XTEM gives 0.1°.

3. **The exit is the aperture the capacitor etch sees.** A bow of 34.5 nm above a 31.0 nm exit presents the same aperture as one of 32.8 nm; the bow changes the web, not the aperture.

4. **M1's web is 87% of nominal, M0's 75%.** A web 25% thinner is 58% less stiff in bending.

5. **The exit-CD budget is 0.99 nm.** The lithography (0.66 nm) is the largest term; the two terms the open controls, SiON bias and foot, are 0.30 nm each.

6. **The exit CD is insensitive to the passivation levers.** The bow and the exit are controlled by different knobs.

7. **The array edge is +0.55 nm at row 1.** The offset decays with 1.4 rows; two dummy rows leave 0.13 nm at the first functional row; the stress edge effect is not cured by them.

---

## Study Questions

1. A 1d-class product has a pitch of 37 nm, a top CD of 27.1 nm, and a bow of 0.9 nm. Find the minimum web, its fraction of the nominal web (exit CD 26.0 nm), and the loss of bending stiffness relative to the nominal web.

2. Show that the full-height angle of a 1450 nm mask changes by 0.02° when the top-to-exit CD difference changes by 1 nm. How does that compare with the measurement precision of 0.1°?

3. The lithography site-mean 3σ rises from 0.60 to 0.75 nm. Recompute the exit-CD budget and say whether it still meets ±1.0 nm. By how much would the foot term have to fall to restore it?

4. Using the array-edge law 0.55 e^−(n−1)/1.4, find the offset at row 2, and the number of dummy rows needed to keep the first functional row below 0.05 nm. What fraction of the area of a block of 32 × 32 cells do they add?

5. The wafer-edge exit CD rises by 0.40 nm at 147 mm. If the ESC edge zone is cooled by 2 K, what happens to the bow at the edge (0.04 nm per K) and, if the 0.40 nm were purely a flux effect, to the exit CD?

6. Compute the oxygen consumed (sccm O₂-equivalent) for an array efficiency of 0.50, and the CO drop at clearing, using the budget of Chapter 8 (COS 30 sccm; bevel 2.3 sccm; wafer carbon proportional to array efficiency).

---

**Next Chapter:** [Chapter 11: Top Loss, Facets & Cap Consumption](./11-cap-top-loss-facets.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
