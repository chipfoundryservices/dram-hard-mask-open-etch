# Chapter 4: Honeycomb Patterning, Pattern Transfer & Hole Statistics

## Overview

The mask open does not draw a pattern. It receives one, in a 40 nm cap, from the patterning module, and transfers it through 1.35 µm of carbon. What it can change is limited: it adds or removes a few tenths of a nanometre of CD, smooths some of the roughness, leaves most of the family structure alone, and adds a small tilt of its own. What it cannot do is make a hole that was not printed, round a corner that arrives sharp, or repair a closed opening. This chapter describes what arrives, what the open does to it, and the one specification of the book that is a count and not a dimension: **at most three failed holes in every billion**.

The chapter treats the two patterning routes of Book #29 (self-aligned double patterning at 60° and EUV) and what each delivers, derives the transfer coefficients for CD, family offset, local CD uniformity, edge roughness, and ellipticity for M0 and M1, adds the placement the open contributes, and builds the defect budget of the open: seven contributors, a total of 3.0 × 10⁻⁹ per hole, 52 holes per die, 46,000 per wafer. It ends on the web between two holes, whose Gaussian margin is seventeen standard deviations and whose real margin is set by the tail.

**Learning Objectives:**
- Describe the two honeycomb patterning routes and the pattern each delivers to the open
- Compute the mean CD of each hole family at the exit from the cap CD and the transfer slope
- Compute the local CD uniformity, edge roughness, and ellipticity that leave the open
- Add the tilt and displacement the open contributes to the placement budget
- Build a per-hole defect budget and convert it to holes per die and per wafer
- Explain why Gaussian statistics say nothing about the failure rate of the web

---

## 4.1 The Two Routes and What They Deliver

### 4.1.1 SADP×2 at 60°

A hexagonal array at a 45 nm pitch is below the single-exposure limit of 193 nm immersion lithography. In the SADP×2 route two sets of lines are printed by self-aligned double patterning, one rotated 60° from the other, and the holes are the crossings of the two sets of gaps. Each crossing is a rhombus:

```
Rhombic crossing of two gaps at 60° (equal area to a 32 nm circle, 804 nm²):
  Gap width                     26.4 nm
  Rhombus side                  30.5 nm
  Long diagonal (60° corners)   52.8 nm
  Short diagonal                30.5 nm
```

A rhombus with a 52.8 nm diagonal does not belong in a 45 nm pitch. The 60° corners are rounded upstream, by the spacer and cut etches of the patterning module, to a radius of about 10 nm; what arrives at the mask open has an ellipticity of about 0.028 (axes differing by 1.7 nm). Book #29 says the crossings are rounded by the subsequent etches. In the carbon the lateral movement of the wall is at most 0.4 nm (Chapter 3), so the open **transfers** the rounding it is given and cannot finish it.

The three kinds of crossing give three **families** of hole. A hole between two core lines (A), between a core and a gap (B), or between two gaps (C) differs slightly in size, and the four combinations of two line sets give the families in the ratio 1 : 2 : 1:

```
Families at the bottom of the cap (SADP×2):
  Family   Crossing          Share   Cap CD
  A        core–core         25%     32.5 nm
  B        core–gap          50%     32.0 nm
  C        gap–gap           25%     31.5 nm
  Mean 32.0 nm; offset A − C = 1.0 nm; σ between families 0.35 nm
```

### 4.1.2 EUV

A single EUV exposure prints the holes directly. There are no families, and the shape is closer to round, but the hole-to-hole variation is larger and stochastic: partially open holes, closed holes, and oversize holes appear at rates that fall steeply with dose (Book #31, Chapter 13).

```
Pattern arriving at the mask open (reference, illustrative):
                              SADP×2 (reference)     EUV, single exposure
  Cap CD (mean, bottom)       32.0 nm                32.0 nm
  Families                    A, B, C (1 : 2 : 1)    none
  Family offset               1.0 nm                 —
  LCDU (3σ, hole to hole)     2.4 nm                 3.0 nm
  Edge roughness (3σ)         2.5 nm                 3.0 nm
  Ellipticity                 0.028                  0.020 (σ 0.015)
  Missing or closed           ≈ 10⁻¹¹ per hole       ≈ 10⁻¹⁰
  Partially open (scum)       ≈ 10⁻⁸                 ≈ 5 × 10⁻⁸       (before the SiON overetch)
  Overlay (mean + 3σ)         5 nm                   4 nm
```

The reference is SADP×2. The EUV route changes the numbers of Section 4.2 as noted there, and adds 5 s of smoothing to the open (Section 4.2.4).

---

## 4.2 Transfer Coefficients

### 4.2.1 CD and Families

The exit CD is a function of the cap CD. Over a series of test structures with different cap CDs the exit changes by more than the cap does, because a narrower hole has a higher aspect ratio, a lower oxygen and ion flux at its exit, and a thicker foot film relative to its width:

```
Exit CD = 31.0 + G × (cap CD − 32.0)          G = 1.10 (M1),  1.30 (M0)    (measured slope)

                    M1                         M0
  Family   cap CD   exit CD      cap CD   exit CD
  A        32.5     31.55        32.5     31.65
  B        32.0     31.00        32.0     31.00
  C        31.5     30.45        31.5     30.35
  Offset (A − C)    1.10 nm                    1.30 nm
  Mean (1 : 2 : 1)  31.0 nm                    31.0 nm
```

The net etch bias is −1.0 nm (32.0 in, 31.0 out) for both. At the exit the wall has moved out by 0.2 nm (M1; 0.8 nm in M0) and the foot has taken 1.2 nm (M1; 1.8 nm) back. The family offset **grows** in the open, by 10% in M1 and 30% in M0. M1 meets the specification of 1.2 nm. M0 does not.

The offset becomes depth lag in the carbon open and, with a gain of 15 nm per nm, in the capacitor etch:

```
Depth lag of family C behind A:
                                    M1          M0
  In the carbon open (7.8, 10.0 nm/nm)   8.6 nm (1.1 s)   13.0 nm (1.7 s)
  In the capacitor etch (15.2 nm/nm)     16.7 nm          19.8 nm
```

M1 saves the capacitor etch 3 nm of overetch on the slowest family. It is not the largest term in the budget, but it is systematic: unlike a random tail it must be covered for a whole family, every hole.

### 4.2.2 Local CD Uniformity

Hole-to-hole variation within a family has a different transfer coefficient from the systematic family term. In M1 the smoothing overetch and the pulsed passivation act as negative feedback on random size differences. In M0 they do not:

```
σ_out = √[ (g_L σ_in)² + σ_etch² ]

  M1:   g_L = 0.85, σ_etch = 0.25 nm      σ_in = 0.80 nm (LCDU 2.4 nm, 3σ)
        σ_out = √(0.462 + 0.0625) = 0.72 nm    →  LCDU 2.2 nm (3σ)         ✓ (≤ 2.4)
  M0:   g_L = 1.30, σ_etch = 0.30 nm
        σ_out = √(1.082 + 0.09) = 1.08 nm      →  LCDU 3.2 nm (3σ)         ✗
  EUV, M1:  σ_in = 1.0 nm   →  0.89 nm → 2.7 nm ✗
  EUV, M1 with +5 s of smoothing (g_L = 0.75):  0.79 nm → 2.4 nm  ✓
```

The CD specification of the open (31.0 ± 1.0 nm, Chapter 1) is read as Book #29 reads its bow limit: a limit on the **site mean** per family, measured across the wafer. The hole-to-hole spread is the LCDU. With the family spread of 0.39 nm added in quadrature, the total hole-to-hole 3σ of M1 is 2.5 nm.

### 4.2.3 Edge Roughness

The roughness of the cap opening, 2.5 nm (3σ) around the perimeter, is transferred into the carbon with an attenuation that depends on the spatial period. Short wavelengths are smoothed by the lateral etch and the redeposition; long wavelengths pass. For M1:

```
Roughness transfer:   T(ξ) = 1 − 0.85 exp(−ξ/13 nm)          (ξ: correlation length)

  ξ (nm)    5      10     20     30     40
  T         0.42   0.61   0.82   0.92   0.96

Correlation lengths of the incoming roughness (Book #31: 10–30 nm):
  10 nm 30%, 20 nm 45%, 30 nm 25%    →   T_avg = 0.78
  LER (3σ):   2.5 nm → 1.95 nm (M1)           2.5 nm → 2.5 nm (M0, no smoothing)
```

The 0.55 nm gained is the smoothing step Book #29 lists as the most effective fix for striation (−0.5 nm). It is also a cost: the 7 s of smoothing adds 7 s to a 184 s process.

### 4.2.4 Ellipticity

```
e_out = √[ (g_e e_in)² + e_etch² ]
  M1:  g_e = 0.90, e_etch = 0.012    →  √(0.000635 + 0.000144) = 0.028       ✓ (≤ 0.03)
  M0:  g_e = 1.00, e_etch = 0.016    →  √(0.000784 + 0.000256) = 0.032       ✗
```

An ellipticity of 0.028 is a difference of 1.7 nm between the axes of a 31 nm hole. The capacitor etch multiplies it by two to three at its bottom and, through the twist model of Book #31, by its square in variance. The open's own contribution (e_etch) comes mostly from a small asymmetry of the ion angular distribution at the wafer edge (Chapter 5).

---

## 4.3 Placement, Overlay & Tilt

The open inherits the overlay of the lithography (5 nm, mean + 3σ, to the landing pads) and adds two terms of its own, a systematic tilt and a random local displacement:

```
Tilt:       an edge tilt of 0.05° at r = 147 mm (Book #29, Chapter 11)
            shift over the 1350 nm of the mask   1350 × tan(0.05°) = 1.2 nm
            θ(r) = θ_edge exp[−(R_w − r)/λ_e], λ_e = 5 mm → θ_edge = 0.09° at r = 150 mm
Random:     local displacement of the exit (wiggle, twist) ≈ 0.7 nm (3σ)
Open's total (RSS)    √(1.2² + 0.7²) = 1.4 nm      (budget of Book #31: 1.5 nm)
```

The margin is 0.1 nm. A change in the edge ring (Chapter 5) that adds 0.02° of tilt adds 0.5 nm and takes the open out of its budget; the mold etch has its own tilt (0.8 nm over 1600 nm), and the two add. **Both etches must be matched together** (Book #29).

---

## 4.4 The Hole Count as a Statistical Specification

### 4.4.1 What a Rate of 3 × 10⁻⁹ Means

```
Specification (Chapter 1): defects from the mask open ≤ 3 × 10⁻⁹ per hole

  Holes per die                 1.718 × 10¹⁰    → 51.5 defective holes per die
  Holes per wafer               1.546 × 10¹³    → 46,400 per wafer
  One defective hole per        3.3 × 10⁸ holes → 0.0058 cm² of array (a 0.76 × 0.76 mm square)
  To see 30 of them             0.17 cm² of array, 58% of one die's array
```

Every die carries about fifty holes that do not open, and they are repaired like any failing bit (row and column redundancy). The specification is not "no defects" but "not many more than Book #29's not-open budget can absorb": the open's share is 3.0 × 10⁻⁹ of the total budget of 8 × 10⁻⁹ (137 per die).

### 4.4.2 The Budget

```
Defects from the hard mask open (illustrative, per hole):
                                              M1            M0
  Closed or missing cap opening (litho)       0.9 × 10⁻⁹    0.9 × 10⁻⁹
  Cap-open residue (BARC, SiON plugs)         0.5           0.5
  Pinch-off in the carbon (closure tail)      0.7           1.5
  Micromask / footing at the exit             0.5           0.8
  Merged holes (web broken through)           0.2           0.4
  Particles on the cap                        0.1           0.1
  Displaced or twisted beyond tolerance       0.1           0.2
  ────────────────────────────────────────────────────────────────────
  Total                                       3.0 × 10⁻⁹    4.4 × 10⁻⁹
  Per die                                     52            76
```

M0's extra 1.4 × 10⁻⁹ comes from the three rows that depend on the sidewall: pinch-off, because the coverage is lower and the passivant film closes the hole where it is thickest; footing, because M0 has no smoothing overetch; and merging, because its minimum web is 10.5 nm and not 12.2 nm.

```
Contribution of each row to the budget (M1):
  litho 30%  |  cap-open residue 17%  |  pinch-off 23%  |  footing 17%  |  merged 7%  |  particles 3%  |  displaced 3%
```

Particles are the smallest row. A wafer with ten adders of 30 nm or more blocks perhaps twenty holes, 1.3 × 10⁻¹² per hole. What fills the budget is not dirt but the **tails** of processes that are fine on average: a litho opening that failed to print, a spot where the passivant thickens, a scum that the SiON overetch did not clear.

### 4.4.3 The Overetch Trade of the Cap Open

The SiON open of Chapter 2 ends with a 2 s overetch that clears scum from the bottoms of the openings. Longer clears more, and costs width:

```
Each second of SiON overetch:   clears about 40% of the remaining partial openings
                                widens the cap CD by 0.1 nm
Survivors after t seconds:      exp(−0.5 t):  2 s → 37%;  4 s → 14%;  6 s → 5%
```

The reference uses 2 s because every second widens the cap CD by 0.1 nm, which the CD budget (Chapter 10) spends elsewhere. A litho process with fewer partial opens permits a shorter overetch; a litho process with more (EUV) buys closure with CD and takes the loss in the next line of the CD budget (Chapter 10). The trade between lithography dose and etch tolerance is the one Book #31 describes for the capacitor etch, and it has the same form here.

---

## 4.5 The Web Between Two Holes

The web at the bow is the thinnest wall in the mask. Its width between two neighbouring holes is the pitch minus the half-sum of their CDs, minus the relative displacement of their axes:

```
t_web = p − (b₁ + b₂)/2 − |Δ|

M1:  mean bow CD 32.8 nm → t_web = 45 − 32.8 = 12.2 nm
     σ of bow CD 0.30 nm;  σ of relative displacement 0.5 nm
     σ_t = √(0.30²/2 + 0.5²) = 0.54 nm
     Margin to merging (web < 3 nm): (12.2 − 3) / 0.54 = 17σ
M0:  t_web = 45 − 34.5 = 10.5 nm;  margin (10.5 − 3)/0.54 = 14σ
```

On Gaussian statistics merging would never occur. In practice it occurs at about 2 × 10⁻¹⁰ per hole in M1 (the 0.2 × 10⁻⁹ of the budget) and twice that in M0, for the reason Book #29 gives for the mold: the tails are not Gaussian. A bridge comes from a printed-large opening, a particle, a local failure of the passivation that lets the wall bow by a few nanometres, or a pair of holes that happen to be displaced toward each other. **The web margin in sigmas is a measure of how much room is left for the non-Gaussian causes, not of how often the web fails.**

---

## Summary and Key Takeaways

1. **The open transfers; it does not draw.** The shape, the families, and the roughness arrive in the cap. The open adds a net −1.0 nm of CD, a few tenths of a nanometre of bow, and a small tilt.

2. **The family offset grows.** Exit CD = 31.0 + G (cap CD − 32.0), with G = 1.10 (M1) and 1.30 (M0). The offset becomes 1.10 and 1.30 nm, and 16.7 and 19.8 nm of depth lag in the capacitor etch.

3. **Smoothing reduces random spread, not systematic offsets.** LCDU 2.4 → 2.2 nm (M1) against 3.2 nm (M0); edge roughness 2.5 → 1.95 nm (M1).

4. **The open's placement is 1.4 nm of a 1.5 nm budget.** 1.2 nm of tilt and 0.7 nm of random displacement; the margin is a tenth of a nanometre.

5. **The specification is a count.** 3 × 10⁻⁹ per hole is 52 per die and 46,000 per wafer; the budget is filled by tails, not by particles.

6. **A web 17σ thick is not safe.** The Gaussian margin measures the room left for the tail causes, which set the real rate.

---

## Study Questions

1. A gap of width g crossing another gap at 60° makes a rhombus of area g²/sin 60°. Find g for an area equal to a 31 nm circle, the long diagonal, and the number of nanometres by which each 60° corner must be rounded to reach an ellipticity of 0.028.

2. The SADP×2 families have cap CDs of 32.5, 32.0, and 31.5 nm (1 : 2 : 1). With G = 1.15 find the exit CDs, the offset, and the depth lag of family C behind A in the carbon open (use 7.8 nm/nm and an exit rate of 8.0 nm/s).

3. Using σ_out = √[(g_L σ_in)² + σ_etch²], find g_L at which the EUV route (σ_in = 1.0 nm, σ_etch = 0.25 nm) meets an LCDU of 2.4 nm (3σ). How much additional smoothing, if each second lowers g_L by 0.02, does that take?

4. Transfer the edge roughness for correlation lengths of 10 nm (40%), 20 nm (40%), and 30 nm (20%) through T(ξ) = 1 − 0.85 exp(−ξ/13). Find the output LER for an input of 3.0 nm (3σ).

5. The tilt at r = 147 mm rises from 0.05° to 0.07°. Find the new shift over 1350 nm, the RSS with the 0.7 nm random term, and whether the 1.5 nm budget is met.

6. The pinch-off row of M0 (1.5 × 10⁻⁹) is brought to M1's 0.7 × 10⁻⁹ by a change of recipe. Find the number of holes per die saved, and the saving as a fraction of Book #29's not-open budget (8 × 10⁻⁹).

---

**Next Chapter:** [Chapter 5: CCP Chambers for the Carbon Open](./05-ccp-chambers-carbon-open.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
