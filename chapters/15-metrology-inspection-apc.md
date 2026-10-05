# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The quantities that matter at the end of the open are inside a mask: the CD at the bottom of a tube 44 times deeper than it is wide, the bulge of the wall 370 nm down, the height of a ridge 6 nm wide. None of them can be measured on a product wafer from above with a method that is fast, precise, and non-destructive. Light is absorbed by the carbon within 126 nm. The electron beam sees the top. What can be seen is the cap before the open, the exit of the hole through the carbon with a high-voltage beam, and a profile with X-rays, and the rest is inferred.

This chapter sets out the ladder from what can be seen to what must be inferred: the measurands and the methods, the test structures in the scribe that stand in for the ones that cannot be seen, the large-area inspection that finds a defect in three hundred million holes, and the process control that closes the loop. The control has three parts. A **feed-forward** of the film's hydrogen and the cap's thickness to the COS flow holds the cap's clock, and cuts the 3σ of the top loss from 31 to 14 nm; one input is deliberately left out, because the open already returns 79% of it. A **feedback** on the exit CD and the bow moves the CHF₃ flow and the wafer temperature. And a **virtual metrology** computes the top loss of every wafer from its endpoint time.

**Learning Objectives:**
- List the measurands of the open, the method for each, and its precision and sampling
- Explain why optical scatterometry fails on the carbon open and what replaces it
- Design the scribe test structures and say what each one stands in for
- Size the inspection area and the sampling for a defect of 10⁻⁹ per hole, and the precision it gives
- Derive the COS feed-forward and show which inputs should and should not be fed forward
- Design the EWMA controller for the exit CD and compute its limits
- Describe the virtual metrology of the top loss and its residual

---

## 15.1 The Measurands and the Ladder

```
Measurands of the hard mask open (illustrative):
  Quantity                       Method                           Precision (3σ)    Sampling per lot (25 wafers)   Where
  ──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
  ACL thickness, density         ellipsometry + deposition log    0.2 nm; ±0.2 at% H   all wafers, 49 sites        incoming
  Cap thickness                  ellipsometry                     0.10 nm           all wafers, 49 sites           incoming
  Cap CD, families, LCDU, LER    CD-SEM                           0.15 nm           5 wafers × 9 sites × 3 families after litho
  Exit CD, families, ellipticity HV-SEM (30–50 keV, top-down)     0.30 nm           2 wafers × 9 sites             after open
  Top CD, bow, depth, exit       CD-SAXS (X-ray scattering)       0.15 nm           1 wafer × 5 sites              after open
  Profile, foot, residue         XTEM / STEM                      0.3 nm            1 per week per chamber         destructive
  Top loss, edge height          IR scatterometry on a ridge test structure; XTEM   3 nm   1 wafer × 5 sites       after open
  Defects (blocked, closed)      HV-SEM large-area inspection     —                 1 wafer per 5 lots, 0.17 cm²   after open
  Particles ≥ 30 nm              unpatterned-wafer scan           30 nm             daily per chamber              chamber qual.
  Tilt, edge placement           test structure shift, HV-SEM     0.2 nm            1 wafer per week per chamber   chamber qual.
  Wafer bow                      capacitive gauge                 5 µm              all                            incoming/outgoing
```

**Scatterometry** (optical critical dimension), the usual tool for a profile, fails on the carbon open at visible wavelengths: the penetration depth is 126 nm at 633 nm (Chapter 8) and the light cannot see the bottom of a tube 1350 nm deep. At 1.3–1.7 µm the carbon is transparent enough, and IR scatterometry can measure heights and the depth of a feature, but it cannot resolve a bow of 0.7 nm in a hole 31 nm wide; its use is for the thickness and loss on a test structure. **CD-SAXS** is the method for the profile: a beam of X-rays that passes through the array at many angles gives the average CD at each depth of the holes, 0.15 nm in precision, without cutting the wafer. A high-voltage SEM at 30–50 keV, whose electrons penetrate the carbon, shows the exit of each hole (a hole whose exit is closed is dark) and measures its CD. And the XTEM calibrates both.

---

## 15.2 Scribe Test Structures

The test structures sit in the scribe lane, in every field, and are etched with the product. Each one stands in for something that cannot be measured on the array:

```
Scribe test structures for the open:
  Structure                                 Stands in for                                  Measured by
  ─────────────────────────────────────────────────────────────────────────────────────────────────────
  Dense hole array, 10 × 10 µm, 45 nm pitch exit CD, bow, profile, families, ellipticity     HV-SEM, CD-SAXS
  Isolated holes and sparse arrays          loading effects; the CD of an unloaded hole    HV-SEM
  Line–space ridges, 14 nm lines at 45 nm   top loss: the ridge's cap fails as on the web  IR scatterometry, XTEM
  Blanket SiON witness (flat)               the cap's flat erosion rate (v_cap, ACL:SiON)  ellipsometry
  Blanket ACL witness                       ER₀ and k (ARDE) at the actual chamber state   ellipsometry
  Array block with dummy rows               the edge profile: CD, ellipticity, relaxation  HV-SEM, test of the placement
  Overlay marks (cap level, buried)         placement to the pads                          optical overlay
  Large open area (1 × 1 mm)                the endpoint calibration (CO drop)             OES
```

The **ridge structure** is the one that is easy to omit and costly to lack. A flat witness measures the flat erosion rate of the cap and cannot report the time at which the cap fails on a 12.9 nm ridge, which is shorter by the factor ρ (Chapter 11); only a test structure of the same width has the same ridge. Its loss, measured by IR scatterometry (3 nm), is the direct measure of the top loss that the endpoint cannot see.

---

## 15.3 Inspection

### 15.3.1 The Area and the Sampling

The defect rate of the open is 3 × 10⁻⁹ per hole (Chapter 4), 52 per die. A defect inspection has to find enough of them to measure the rate:

```
Large-area HV-SEM inspection:
  One defect per                       3.3 × 10⁸ holes = 0.0058 cm² of array
  To see 30 defects                    0.17 cm² of array   (the array of 0.57 dies)
  Precision of the rate                1/√30 = 18% (1σ)
  Throughput of a large-field e-beam   ≈ 0.8 cm²/h  →  13 min for 0.17 cm²
  Sampling                             1 wafer per 5 lots (125 wafers) = 0.1 min per wafer on average
```

The rate is measured on one wafer in 125 and has a precision of 18% in a single measurement. It is not a control signal; it is a monitor that confirms the budget, and its results are pooled over lots. The defect lines of Chapter 13 have individual rates (pinch-off 0.7 × 10⁻⁹, one per 0.025 cm²) that cannot be separated by this inspection without an inspection area of about 1 cm² per wafer. The two lines that are measured separately are the largest: the cap-level defects (before the open, where an optical inspection can see a missing opening) and the sum of the others after it.

### 15.3.2 The Bitmap

The measurement that resolves the lines of the budget is not made at the open. It is the **fail bitmap** of the finished die, months later, in which every dead cell is placed in its family (A, B, C), its row from the array edge, its position in the wafer, and its neighbours. Chapter 16 reads the signatures.

---

## 15.4 Advanced Process Control

### 15.4.1 Feed-Forward: Holding the Cap's Clock

The cap's clock is its failure time t₀ = h_cap/(ρ v_cap). The carbon's clock is the open time T. Their difference, squared, is the top loss. Four inputs move the clocks, and COS is the one control that moves the cap's without moving the carbon's (Chapter 8). The feed-forward is a linear equation, whose coefficients follow from the model of Chapter 11 and have been checked against it:

```
ΔCOS (sccm) = + 2.9 ΔH  −  0.085 Δh_ACL  +  2.5 Δh_cap          (ΔH in at%, Δh in nm)

  Film hydrogen +1 at%      rate +3.0%, open −4.3 s          COS +2.9 sccm   (30 → 32.9; L 27 → 51 nm)
  Carbon thickness +14 nm   open +1.75 s                      COS −1.2 sccm   (30 → 28.8)
  Cap thickness +0.4 nm     cap life +1.5 s                   COS +1.0 sccm   (30 → 31.0)
  (1 sccm of COS = 1.47 s of the cap's clock = 9.3 nm of top loss at the reference)
```

### 15.4.2 What Not to Feed Forward

Chapter 11 showed that the open returns 79% of a carbon thickness error as top loss: a thicker film takes longer to open, and the cap's clock does not wait. The mask height after the open therefore varies with the carbon's thickness at only 0.21 of its value. A feed-forward of the carbon thickness removes this compensation and returns the full ±14 nm to the mask height:

```
Spread (3σ, nm) of the top loss and of the mask height after the open (M1):

                                      No feed-forward     FF: hydrogen, cap     FF: hydrogen, cap, carbon
  Cap thickness ±0.4 nm → loss        9.3                 2.3  (±0.1 nm measured)   2.3
  Cap erosion rate ±0.8% → loss       7.4                 3.7  (witness feedback)   3.7
  Film hydrogen ±1 at% → loss         26                  8    (H known ±0.3 at%)   8
  Carbon thickness ±14 nm → loss      11                  11   (not corrected)      0.2
  Top loss, RSS                       30.6                14.3                      9.1
  Carbon → mask height                3.0 (0.21 × 14)     3.0                       14
  Mask height after open, RSS         28.7                9.6                       16.7
  Lower bound 1350 − 3σ               1321  ✗             1340  ✓                   1333  ✓
```

The reference policy is the middle one: feed forward the hydrogen and the cap, and leave the carbon thickness alone. It meets the specification of the mask height (1340 against 1330 nm). The top-loss specification of Chapter 1, ±12 nm, is the root-sum-square of the cap-related terms (cap thickness, erosion rate, and hydrogen: ±9.1 nm after feed-forward): the carbon-thickness term, which is compensated in the height, is excluded from it. **The ranking of the specification should be made on the mask height, not on the top loss.**

### 15.4.3 Feedback on the Exit CD

The exit CD is controlled by a run-to-run feedback on the HV-SEM measurement. The knob is the CHF₃ flow in the SiON open (taper and cap CD), which has a range that does not conflict with the budget:

```
Exit CD controller (EWMA, per product and chamber):
  Target                      31.0 nm
  Knob                        CHF₃ in ST1:  0.066 nm of exit CD per sccm (0.06 of cap CD × G = 1.10); range ±5 sccm = ±0.33 nm
  Measurement noise           0.05 nm (1σ; HV-SEM, mean of 9 sites)
  Run-to-run variation        σ_rr = 0.25 nm (chamber drift, litho, film)
  EWMA weight λ               0.3
  Control limits              ±3 σ_rr √(λ/(2 − λ)) = ±3 × 0.25 × 0.42 = ±0.315 nm
  Action                      ΔCHF₃ = −λ (CD_EWMA − 31.0)/0.066
```

The SiON overetch is not used as the knob: each second of it moves the exit by 0.11 nm, and the budget of Chapter 13 gives it a range of ±1 s, on which the closure line depends.

### 15.4.4 Feedback on the Bow

The bow is measured by CD-SAXS, once a lot, and controlled by the wafer temperature:

```
Bow controller:   ΔT = −(bow − 0.67 nm) / 0.04 nm per K;  range ±3 K (bow ± 0.12 nm)
                  Window ±1 K across the wafer
```

---

## 15.5 Virtual Metrology

The tools log hundreds of signals per wafer (Chapter 8). A model that takes a few of them as features predicts the quantities that cannot be measured on every wafer:

```
Virtual metrology (illustrative, trained on the HV-SEM, CD-SAXS, and scatterometry data):
  Predicted quantity   Features                                                  Residual (1σ)
  ───────────────────────────────────────────────────────────────────────────────────────────────
  Top loss             EP time (→ T = EP + 18 s); cap thickness; v_cap from the   6 nm
                       blanket witness; ridge law L = ER_top x²/(2τ_w)
  Exit CD              OES CN/Ar in ST1; V_dc and delivered bias power in ST2;    0.20 nm
                       ion-flux probe at the edge ring; ESC temperature
  Bow                  wafer temperature trace (backside); V_dc; SO/Ar emission   0.06 nm
                       (the COS flow and the sulfur state of the wall)
```

The top-loss model is almost first-principles: the endpoint gives T, the ellipsometry gives the cap, the witness gives its erosion rate, and the law of Chapter 11 gives L. The residual of 6 nm is the uncertainty of the cap's clock (±0.4% in the erosion rate is 0.6 s and ±0.1 nm of cap is 0.4 s: ±0.7 s, or 4.4 nm at 6.3 nm/s) with the error of the ridge law itself. The predicted top loss triggers the COS correction of Section 15.4.1 on the next wafer.

---

## 15.6 Matching and Qualification

The metrics of Chapter 5 for a chamber's fleet matching are measured by the structures of Section 15.2:

```
Fleet-matching measurements (per chamber, weekly and after a part change):
  ER₀ (blanket ACL), ACL:SiON (blanket SiON)    ellipsometry on witness wafers
  Exit CD and bow of the dense array            HV-SEM, CD-SAXS
  Top loss on the ridge structure               IR scatterometry (3 nm)
  Edge tilt (shift at 147 mm)                   test structure, HV-SEM
  Particle adders                               unpatterned-wafer scan
```

### 15.6.1 The Cost

```
Metrology cost per wafer (M1, illustrative; $1.10 in the module cost of Chapter 1):
  Incoming films (ellipsometry, all wafers, 49 sites)       $0.25
  CD-SEM (5 of 25 wafers)                                   $0.25
  HV-SEM (2 of 25 wafers + test structures)                 $0.30
  CD-SAXS (1 of 25 wafers)                                  $0.20
  Large-area inspection (1 wafer of 125)                    $0.10
  Total                                                     $1.10
```

---

## Summary and Key Takeaways

1. **The mask cannot be seen from above.** Visible light penetrates 126 nm; the profile is measured by CD-SAXS, the exit by high-voltage SEM, and the rest by test structures and inference.

2. **A ridge test structure is the only way to see the top loss.** A flat witness reports the cap's flat erosion rate; the ridge fails sooner, by the factor ρ.

3. **A defect rate of 3 × 10⁻⁹ needs 0.17 cm² to see 30 events.** One wafer in 125 at 13 min; the precision is 18%; the budget's lines are resolved only by the bitmap.

4. **The COS feed-forward holds the cap's clock.** ΔCOS = 2.9 ΔH − 0.085 Δh_ACL + 2.5 Δh_cap; 1 sccm is 1.47 s or 9.3 nm of loss.

5. **Do not feed forward the carbon thickness.** The open returns 79% of the error as top loss, so the mask height varies at 0.21 of it; the full feed-forward raises the height spread from 9.6 to 16.7 nm.

6. **The reference policy is hydrogen and cap.** Top loss 14.3 nm (30.6 without), mask height 9.6 nm (28.7 without), lower bound 1340 nm.

7. **The controllers are modest.** EWMA with λ = 0.3, limits ±0.315 nm on the exit CD; ±1 K on the bow; virtual metrology of the top loss to 6 nm.

---

## Study Questions

1. A product has a die with an array of 0.45 cm². Find how many dies' worth of array must be inspected to see 30 defects at 3 × 10⁻⁹ per hole at the 1b hole density, and the inspection time per wafer at 0.8 cm²/h.

2. The film's hydrogen is measured on a wafer to be 1.6 at% above target. Compute the COS correction, and the top loss with and without it.

3. Using the dependence of the after-open height on the carbon thickness (slope 0.21 without feed-forward), find the height variation for ±20 nm of carbon (3σ) and the COS correction a full feed-forward would apply. What does it do to the height?

4. Design an EWMA with λ = 0.2 for σ_rr = 0.3 nm. Find the control limits. What is the delay (in runs) for the EWMA to reach 63% of a step change?

5. The ridge test structure reports a loss of 70 nm on a wafer whose flat witness shows the nominal erosion rate. Estimate the exposed time x (use ER_top = 12.17 nm/s, τ_w = 30 s), the cap life t₀ if T = 163 s, and the equivalent cap thickness error.

6. The CD-SAXS measures a bow of 0.82 nm. By how much should the wafer temperature be lowered, and what is the expected change in the minimum web?

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
