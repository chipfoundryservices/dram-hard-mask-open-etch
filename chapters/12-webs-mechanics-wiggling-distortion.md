# Chapter 12: The Webs — Mechanics, Wiggling, Twist & Distortion

## Overview

The carbon mask is a perforated plate whose solid part is a honeycomb of walls 12 to 14 nm thick and 1.35 µm tall. It is a structure, and like any structure it carries stress and bends under asymmetry. Book #31 speaks of mask wiggling: the walls between the holes buckle slightly under the film's stress and the heat of the etch, and the openings distort. This chapter puts mechanics under that statement. It finds that the web does not buckle (its spans are too short), that it does not collapse (nothing loads it enough), and that the displacements of the holes come from two quieter sources: the **relaxation of the film's stress** at the edge of every array block, which moves the top of the outermost rows by up to 2.7 nm, and a **bimorph effect** in which a thin skin on the two faces of a web, hardened and stressed by the ions, bends the web if the two skins differ by as little as one part in a hundred.

The chapter derives the stiffness of the perforated mask, the edge relaxation and the compensation for it, the bimorph model of the wiggle and its scaling across M0, M1, and M2, the ellipticity gradient at the array edge, and the placement budget that collects them. The results explain why the stiffer boron-doped carbon, a lower film stress, and a lower ion energy all help, and why the dummy rows that cure the CD edge effect (Chapter 10) do not cure the stress.

**Learning Objectives:**
- Estimate the in-plane stiffness of the perforated mask from the ligament efficiency
- Show that web bending and buckling are not failure modes of the carbon mask
- Compute the relaxation of the film's stress at a free edge and its decay into the array
- State the pre-compensation that holds the edge placement within its budget
- Apply the bimorph model to the wiggle and scale it with modulus, web thickness, height, and skin depth
- Compute the ellipticity near the array edge and the effect of dummy rows
- Assemble the open's placement budget from tilt, wiggle, and edge relaxation

---

## 12.1 The Honeycomb as a Structure

### 12.1.1 Stiffness of the Perforated Mask

A plate perforated by a triangular array of holes has an in-plane modulus below that of the solid. To first order the loss follows the **ligament efficiency**, η = (p − d)/p, the fraction of the pitch that is solid between neighbours:

```
In-plane modulus of the perforated mask, E* ≈ η E:
                      Pitch   CD (bow)   η       E (film)    E*
  M1 (ACL)            45      32.8       0.271   75 GPa      20 GPa
  M0 (ACL)            45      34.5       0.233   75 GPa      17.5 GPa
  M2 (B-ACL)          37      27.5       0.257   105 GPa     27 GPa
  Nominal 1b (exit)   45      31.0       0.311   75 GPa      23 GPa
```

The mask at its bow is about a quarter as stiff as the film. M2's boron-doped carbon, 40% stiffer in the film, gives a perforated mask a third stiffer than M1's, even with its thinner web.

### 12.1.2 Why the Web Does Not Fail

Two failure modes come to mind for a wall 12 nm thick and 1350 nm high. Neither occurs:

```
Buckling under the film stress:
  The web is a wall whose span between nodes is 26 nm, only 2.1 times its thickness (12.2 nm);
  its critical stress k π² E/(12(1 − ν²)) (t/a)² is of the order of 50 GPa,
  against a film stress of 0.3 GPa.  → no buckling

Bending under a pressure difference between neighbouring holes (Chapter 9):
  σ = ¾ p (a/t)²:  for p = 1 MPa
     t = 14 nm    2.6 MPa      t = 12.2 nm   3.4 MPa      t = 10.5 nm   4.6 MPa
  The strength of the carbon is of order GPa.  → no collapse
```

The web is stout because its spans are short. Its failure modes are not mechanical; they are the ones of Chapters 4 and 13, a thin web that merges with its neighbour, and the ones of this chapter, the small displacements that stress and asymmetry impose on a structure that never fails.

---

## 12.2 Stress Relaxation at the Array Edge

### 12.2.1 What Happens

The ACL is deposited with a compressive stress of −300 MPa. Bonded to the substrate it cannot expand. When the open perforates it, the carbon at a free surface is no longer constrained, and relaxes. In the interior of a block, the neighbouring holes relax against each other and their displacements cancel by symmetry. At the edge of a block, where there is a periphery of unperforated carbon on one side, they do not.

```
Relief strain (biaxial)             ε = σ (1 − ν) / E
  ACL:    300 MPa × 0.75 / 75 GPa    = 0.30%
  B-ACL:  250 MPa × 0.75 / 105 GPa   = 0.18%

Displacement of the top at a free edge   u₀ ≈ ε × 0.7 h
  ACL, h = 1350 nm        u₀ = 0.0030 × 945 nm = 2.8 nm
  B-ACL, h = 1450 nm      u₀ = 0.0018 × 1015 nm = 1.8 nm

Decay into the array (length ≈ h/2):  u(n) = u₀ exp(−n p / (h/2))
  ACL:    15 rows        B-ACL:  19.6 rows
```

```
Top displacement of the outermost rows (ACL, M1):
  Row n                     1      3      5      10     15     30
  Top displacement (nm)     2.65   2.32   2.03   1.46   1.04   0.38
  Effective shift of the exit (u/2)       1.33   1.16   1.01   0.73   0.52   0.19
```

The top moves; the bottom, bonded, does not. The hole leans by u/h, 0.11° at row 1, and the ions of the capacitor etch, which see a tube whose axis is tilted, are steered by its centroid. The effective shift of the exit, taken as half the top displacement, is 1.3 nm at row 1, and it extends tens of rows into the array. **Dummy rows do not help**: they move the functional edge by two rows out of thirty.

### 12.2.2 The Compensation

Because the displacement is deterministic and smooth, it can be predicted from a model with the film's stress and thickness and subtracted in the lithography: the cap openings are printed shifted by the predicted displacement, in the direction that the relaxation will undo. A calibrated model removes about 80% of it:

```
Edge placement error from stress relaxation, with and without compensation:
  Row n                     1      3      10     30
  Uncompensated (nm)        1.33   1.16   0.73   0.19
  After 80% compensation    0.27   0.23   0.15   0.04
```

The residual, 0.27 nm at row 1, goes into the placement budget of Section 12.6. A film with a lower stress needs less compensation: halving the stress halves the relief strain, the displacement, and the residual.

---

## 12.3 Wiggling: The Bimorph Model

### 12.3.1 Mechanism

A web is a plate with two faces, one on each neighbouring hole. The ions that cut each hole harden a thin skin on the face they strike, to a depth of about 1.5 nm at 600 eV, and put it in a stress σ_s of about 0.5 GPa. If the skin on the two faces is identical the web stays straight. If one face has a skin stronger by the fraction a_f than the other, the web bends like a bimetallic strip:

```
Curvature of the web         κ = 6 (1 − ν) a_f σ_s t_s / (E t²)
Displacement of the top relative to the bottom (clamped at the foot, with a constraint factor c_c = 0.3
  for the coupling of the web to its neighbours at the nodes):
                             δ = c_c κ H² / 2

M1:  E = 75 GPa, t = 12.5 nm (mean web), H = 1350 nm, t_s = 1.5 nm, σ_s = 0.5 GPa
     κ = 6 × 0.75 × 0.5 × 10⁹ × 1.5 × 10⁻⁹ a_f / (75 × 10⁹ × (12.5 × 10⁻⁹)²) = 2.88 × 10⁵ a_f  m⁻¹
     δ = 0.3 × 2.88 × 10⁵ × (1350 × 10⁻⁹)² / 2 a_f = 79 nm per unit a_f
```

The curvature is large per unit asymmetry and the web would curl by 79 nm for a 100% difference between the two skins. For it to be less than a nanometre the faces must match to a part in a hundred, and that is what a symmetric hexagonal environment, six identical neighbours with the same flux, provides in the interior of a block.

### 12.3.2 Calibration and Scaling

The random asymmetry between the faces of neighbouring holes comes from the roughness, the local flux, and the neighbours' differences (family offsets, pitch walking). Take σ_a = 0.30% (a 3σ asymmetry of 0.9%); then M1's wiggle is 0.7 nm (3σ), the value of Chapter 4. The same σ_a and the other materials and geometries give:

```
Wiggle (3σ) of the mask top relative to the exit:
                       E (GPa)   t (nm)   H (nm)   t_s (nm)   δ per a_f    3σ wiggle
  M1 (ACL, 600 eV)     75        12.5     1350     1.5        79 nm        0.70 nm
  M0 (ACL, 800 eV)     75        11.3     1338     1.9        120 nm       1.07 nm     ✗ (≤ 1.0)
  M2 (B-ACL, 600 eV)   105       9.7      1450     1.2        86 nm        0.77 nm     (≤ 0.82 at the 37 nm pitch)
```

M0 is out of its specification by 0.07 nm for two reasons that multiply: its web is thinner by 10% (a factor of 1.22 in 1/t²), and its ion energy is higher, which deepens the skin (1.9 nm against 1.5); its height is the same to 1%. M2's boron-doped carbon is stiffer (a factor of 0.71) and has a thinner skin at the same energy (B–C bonds are harder to damage, 1.2 nm), which together cancel the penalty of its taller, thinner web.

### 12.3.3 What Reduces It

```
Sensitivity of the wiggle (M1, 0.70 nm):
  Modulus + 20% (HD-ACL)                     0.58 nm     (δ ∝ 1/E)
  Web thickness − 1 nm (12.5 → 11.5)         0.83 nm     (δ ∝ 1/t²)
  Ion energy 600 → 800 eV (skin 1.5 → 1.9)   0.89 nm     (δ ∝ t_s)
  Mask height +10%                           0.85 nm     (δ ∝ H²)
  Face asymmetry σ_a 0.30% → 0.20%           0.47 nm     (δ ∝ a_f)
```

The wiggle favours a stiffer film, a thicker web (hence a smaller bow), a lower energy, and a lower asymmetry. The first is a material choice, the second and the third are the passivation and the energy (Chapter 6), and the last is the uniformity of the neighbours' environment: families, roughness, pitch walking.

---

## 12.4 Tilt, Twist & the Steered Hole

Two more displacements are plasma effects, not mechanics. The edge tilt of the ions at the wafer edge (0.05° at 147 mm, 1.2 nm over the mask) was derived in Chapter 4 and traced to the ring in Chapter 5. And the random walk of a hole's axis in the plasma, the twist of Book #31, exists in the carbon open as well, at a much lower level: for the mask's wide holes (31 nm against the ion angular spread of 0.9° and a walk that begins at the depth where the hole's aspect ratio passes about 10), the twist contributes 0.2 nm (3σ) to the displacement, a third of the wiggle in amplitude and a tenth in variance. The local displacement of Chapter 1 (≤ 1.0 nm, 3σ) is the quadrature sum of the two: for M1, √(0.70² + 0.2²) = 0.73 nm, which is quoted as 0.7 nm.

A tilted mask hole steers the ions that enter the mold, so that the mold hole continues in the direction of the mask for a time (Book #29). The mold etch then adds its own tilt, and the two add (Chapter 4): this is the reason the open and the mold etch are matched together.

---

## 12.5 Ellipticity and Hexagonal Distortion

### 12.5.1 Near the Array Edge

In the interior of a block each hole has six neighbours and no preferred direction. At the edge, the symmetry is broken, and the hole becomes slightly elliptical along the direction of the edge: the neighbour flux, the stress relaxation, and the bimorph bending all have a preferred direction there. The ellipticity of the exit near an edge:

```
Ellipticity of the exit by row from the array edge (M1):
  e(n) = 0.012 + 0.015 exp[−(n − 1)/3]
  Row n                   1       2       3       4       6       10
  e                       0.027   0.023   0.020   0.018   0.015   0.013
  Specification           e ≤ 0.03
```

All rows meet the specification, but the edge rows are twice the interior's ellipticity, and with the capacitor etch's amplification of two to three, they reach 0.054–0.08 at the bottom of the mold hole. The dummy rows are effective here (functional row 3 has e = 0.020), because the ellipticity decays with a length of three rows and not fifteen.

### 12.5.2 The Lattice

The relaxation of Section 12.2 is a strain, 0.28% at row 1, that stretches the lattice at the top of a block edge. A strain of 0.28% on a 45 nm pitch changes it by 0.13 nm, and the angles of the hexagonal cell by a fraction of that. It is smaller than any other lattice error in the mask (pitch walking in SADP, overlay) and is not tracked separately.

---

## 12.6 The Placement Budget

The open's contributions to the placement of the hole at the exit add in quadrature:

```
Placement budget of the open (M1; 3σ, nm):
                                          Edge row 1      Edge row 3      Interior, wafer edge
  Edge tilt (r = 147 mm, 0.05°)           1.2             1.2             1.2
  Local displacement (wiggle + twist)     0.7             0.7             0.7
  Edge relaxation, uncompensated          1.33            1.16            —
  Edge relaxation, 80% compensated        0.27            0.23            —
  RSS, compensated                        1.42            1.41            1.39
  RSS, uncompensated                      1.92            1.81            1.39
  Budget (Book #31)                       1.5             1.5             1.5
```

The edge tilt and the edge relaxation do not necessarily coincide (the tilt is largest at the wafer edge; the relaxation, at every block edge on the wafer), but the worst case, a block edge near the wafer edge, is the one in the table. **Without compensation the open exceeds its placement budget at every block edge; with it, by 0.1 nm of margin.** The margin is thin for the same reason as everywhere else in the book: the open's inputs are the capacitor etch's inputs, and the capacitor etch has its own budget.

---

## Summary and Key Takeaways

1. **The perforated mask is a quarter as stiff as the film.** E* = ηE: 20 GPa for M1, 17.5 for M0, 27 for M2; the web does not buckle or collapse (3.4 MPa under 1 MPa of pressure).

2. **Stress relaxes at every array edge.** ε = σ(1 − ν)/E = 0.30%; the top of the outermost row moves 2.7 nm and the effect extends 15 rows; dummy rows do not cure it.

3. **The relaxation is compensated in the lithography.** 80% removed: 1.33 → 0.27 nm at row 1; a film with half the stress needs half the compensation.

4. **Wiggling is a bimorph effect.** κ = 6(1 − ν)a_f σ_s t_s/(E t²); 79 nm per unit asymmetry; 0.7 nm at σ_a = 0.30%.

5. **The wiggle favours a stiff film, a thick web, a low energy.** M0 fails (1.07 nm, thinner web and deeper skin); M2's stiffer B-ACL offsets its taller, thinner web (0.77 nm).

6. **Ellipticity decays in three rows.** e = 0.027 at row 1 and 0.020 at row 3; dummy rows work for it.

7. **The placement budget is 1.4 of 1.5 nm.** Tilt 1.2, wiggle 0.7, compensated relaxation 0.27; without compensation 1.9 nm.

---

## Study Questions

1. Compute the in-plane modulus of the perforated mask for a pitch of 45 nm and a bow CD of 33.5 nm and a film modulus of 100 GPa (HD-ACL). By what factor does the bimorph wiggle fall relative to M1 for the same σ_a, with the web thickness of 11.5 nm?

2. For the 1d array find the relief strain, u₀, and the decay length in rows, for B-ACL with σ = −250 MPa, E = 105 GPa, ν = 0.25, h = 1450 nm, pitch 37 nm. Compute the effective shift of the exit at rows 1 and 10, with and without 80% compensation.

3. A film with half the stress (−150 MPa) is used for M1. Recompute u₀ and the compensated residual at row 1. What does this do to the RSS of Section 12.6?

4. Show that the bimorph curvature scales as 1/t². If the minimum web is 10.5 nm and the mean 11.3 nm, compare the wiggle of the thinnest web with that of the mean.

5. The ellipticity at the exit at row 1 is 0.027. If the capacitor etch multiplies it by 2.5, find the bottom ellipticity and the difference between the axes of a 24 nm bottom, and say whether it is within 0.05.

6. A block of 200 × 200 cells has two dummy rows around it. Find the area added, and the fraction of the functional cells that lie in the rows where the edge relaxation is above 2.0 nm (rows 1 to 5, counted from the edge of the functional block).

---

**Next Chapter:** [Chapter 13: Residue, Not-Open Holes & Stochastic Defects](./13-residue-not-open-stochastic-defects.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
