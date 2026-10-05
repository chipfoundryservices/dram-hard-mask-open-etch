# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

The hard mask open is cheap compared with what rides on it. It costs $15 a wafer, and the wafer at this point in the module has already cost about a hundred times that. A mask that is wrong in a way that the capacitor etch cannot cover costs not $15 but the wafer; a lot of them costs the lot; and a systematic error, one that every wafer carries, costs a signature in the bitmap that takes months to arrive. The economics of the open are therefore not the economics of a cheap step. They are the economics of **an inexpensive step with a large downside, where the leverage is in the margin and not in the unit cost**.

This chapter closes the book by putting the open in the module: what it receives from upstream and hands to downstream, how long each may wait, what each failure looks like in the bitmap when it finally arrives, how the open's defect budget becomes a yield, how many chambers 150,000 wafer starts a month require, what each route costs and where the cost sits, and when the extra dollar of M1 or M1-c pays. It ends with a checklist for a new product and the handoff sheet that the open gives to the capacitor etch.

**Learning Objectives:**
- State the queue limits and the rework rule of the open
- Read a bitmap signature and trace it to a failure of the open
- Compute the yield effect of the open's defect budget with a repair model
- Size the chamber fleet for a monthly start rate and compute the monthly consumption
- Decompose the module cost and find the cost per second of chamber time and the effect of utilization
- Compute the break-even yield gain of M1 over M0 and of M1-c over M1
- Apply the new-product checklist and fill the handoff sheet

---

## 16.1 Customers, Queues & Rework

### 16.1.1 The Neighbours

```
What the open receives, and what it hands on:
  From the lithography and the film deposition      cap with openings (CD, families, LCDU, LER, overlay);
                                                      carbon (thickness, hydrogen, stress) and cap (thickness)
  To the capacitor etch (Books #29, #31)             a perforated mask: exit CD, bow, foot, height, shoulder,
                                                      tilt, residue, sulfur, moisture
  To the metrology and APC (Chapter 15)              HV-SEM, CD-SAXS, ridge structure; feed-forward of hydrogen
                                                      and cap to the COS flow
```

### 16.1.2 Queue Times and Rework

```
Queue limits (M1):
  ACL deposition → cap deposition         ≤ 8 h       (surface and moisture)
  Cap → lithography → open                ≤ 24 h      (pattern and resist)
  Open → capacitor etch                   ≤ 4 h in air; ≤ 12 h in a nitrogen-purged FOUP; load-lock degas 150 °C, 30 s
```

**The open cannot be reworked.** The carbon that is gone is gone. A wafer whose open is out of specification can be stripped (O₂ ash), the mask redeposited and re-patterned, and the module repeated, at the cost of the module ($15.1 for M1) and the lithography layer, once. A second rework is not allowed: the mask film's stress history, the cap's thickness, and the wafer's bow accumulate. A lot that fails the open's measurements after the first rework is scrapped.

---

## 16.2 Yield Signatures

The defect lines of Chapter 13 and the dimensional errors of Chapters 10 to 12 leave different patterns in the fail bitmap:

```
Bitmap signatures of the hard mask open (illustrative):
  Signature                                           Cause in the open                         Chapter   Action
  ─────────────────────────────────────────────────────────────────────────────────────────────────────────────────
  Weak cells on the 1:2:1 family pattern (family C     family offset grows (G = 1.10 → 1.30);    4, 10     check the gain; litho families;
   weakest), worse at the wafer edge                    exit CD low                                          recipe
  Pairs of failing cells, three orientations           merged holes (web broken through);        4, 13     bow, temperature, COS; chamber
   along the webs                                       bow high                                            matching
  Random isolated dead cells, step change at a PM      pinch-off, micromask: tail scale Δ₀,      13, 9     wall state; season; electrode age
                                                        silicon supply
  Radial pattern in capacitance, a mask-height trend   top loss varies with the cap's thickness  11       cap map; COS feed-forward
   across the wafer                                     and erosion
  Weak rows along the edge of every array block,       stress relaxation of the carbon;          12       litho compensation; film stress
   decaying over 15–30 rows                             uncompensated displacement
  Weak cells at the wafer edge along the radius,       edge tilt (ring wear)                     5, 12     ring replacement
   shifted in the radial direction
  Random weak cells in the interior of blocks          wiggle (face asymmetry); thin web         12        film, energy, passivation
  Lot-to-lot shift of the whole distribution           film hydrogen, cap thickness, queue       2, 9, 15  APC; queue discipline
```

Most of these are visible only as statistics: the signature of any one dead cell is a dead cell. What the bitmap gives is the **spatial and temporal organization** of the dead cells, and the open's lines are organized differently from the capacitor etch's.

---

## 16.3 The Yield Model

### 16.3.1 Repair

The open makes 52 defective holes per die, a defect that is a failing bit, and it is repaired in the way any failing bit is: by a spare row or column in the sub-array that contains it. A die has about 600 sub-arrays of 28 Mb, each with spares for four defects:

```
Repair of the open's defects (M1; 51.5 events per die; M0: 75.6):
  Events per sub-array              51.5 / 600 = 0.086          (M0: 0.126)
  P(more than 4 in one sub-array)   3.6 × 10⁻⁸                  (M0: 2.4 × 10⁻⁷)
  Die yield loss from unrepaired sub-arrays   600 × 3.6 × 10⁻⁸ = 2.2 × 10⁻⁵   (M0: 1.4 × 10⁻⁴)
```

Repair absorbs the open's isolated defects almost completely. The sub-array arithmetic makes the isolated dead cell nearly free; what costs yield is the part that cannot be repaired.

### 16.3.2 What Cannot Be Repaired

A merged pair is a short, not an open. A cluster of dead cells (a particle of 81 nm or more) can exhaust the spares of a sub-array. And a defect at a critical place, in the sense amplifier's path, or on a word line shared with others, cannot be repaired at the same cost. Take a fraction f_u = 2 × 10⁻⁴ of the open's events as unrepairable (illustrative):

```
Yield loss from unrepairable events:   1 − exp(−N f_u)
  M1:  N = 51.5 per die:   λ = 0.0103     loss 1.02%
  M0:  N = 75.6 per die:   λ = 0.0151     loss 1.50%
  Difference                              0.48%
```

The yield cost of the open is about 1% in M1. The 24 extra events of M0 cost it a further half a percent.

---

## 16.4 Equipment for 150,000 Wafer Starts a Month

```
Chamber fleet at 85% utilization (8,760 h/year):
  Route                      M0       M1       M1-c     M2       M3 (4F²)
  Cycle time per wafer (s)   215      218      219      299      314
  Wafers/chamber/month       10,390   10,247   10,219   7,471    7,114
  Chambers for 150,000       14.4     14.6     14.7     20.1     21.1
  Four-chamber platforms     4        4        4        6        6
```

M0 and M1 fit in four platforms (16 chambers, a spare of 1.4), M2 and M3 need six (24 chambers, a spare of 3.9 and 2.9). The M2 and M3 fleets are 50% larger because their cycle is 37–44% longer, and they cost 17% more per tool because of the cryogenic chucks.

```
Monthly consumption (M1, 150,000 wafers):
  COS               3.4 mmol per wafer (4,608 sccm·s)  →  514 mol = 31 kg per month
  Silicon edge rings    37 per month ($1,500)  $55,000      Upper electrodes   5.1 per month ($12,000)  $61,000
  Abatement         thermal oxidizer and scrubber on every foreline: $0.30 per wafer = $45,000
```

---

## 16.5 Cost of Ownership

### 16.5.1 The Module

```
Module cost per wafer (illustrative; Chapter 1, 14):
                         M0       M1       M1-c     M2       M3
  Tool (fixed)           $5.86    $5.94    $5.96    $9.44    $9.91
  Consumables            $1.61    $1.96    $1.96    $3.12    $3.28
   (gas, power, parts, abatement)
  Etch step              $7.47    $7.90    $7.92    $12.56   $13.19
  ACL and cap deposition $6.10    $6.10    $6.16    $9.80    $9.90
  Metrology              $0.80    $1.10    $1.10    $1.60    $1.80
  ─────────────────────────────────────────────────────────────────
  Module                 $14.4    $15.1    $15.2    $24.0    $24.9
```

For M1 the module splits into 39% tool, 13% consumables, 40% deposition, and 7% metrology. The etch itself is half the cost; the film that is etched is the other 40%.

### 16.5.2 The Cost of a Second and of a Point of Utilization

```
Cost per second of chamber time (M1):   $7.90 / 218 s = $0.036 per second

Utilization and the fixed cost per wafer (M1):
  Utilization        80%      85%      90%
  Fixed cost         $6.31    $5.94    $5.61
```

A second of cycle time costs 3.6 cents; the 8 s of the margin-seeking variant of Chapter 6 costs $0.29. A point of utilization is worth 7 cents per wafer, as much as the cap that makes M1-c. These are the units the choices of the book trade in.

---

## 16.6 When the Extra Dollar Pays

### 16.6.1 M1 over M0

```
M1 costs $0.73 more per wafer than M0 ($15.10 − $14.37).
  Value of a processed wafer at this point (illustrative)            $1,400
  Break-even yield gain                                              0.73 / 1,400 = 0.052%
  Yield difference from the open's events (Section 16.3.2)           0.48%       9 times the break-even
  M0 also fails the specification on four lines (Chapter 1), so the comparison is a floor, not a ceiling.
```

### 16.6.2 M1-c over M1

```
M1-c costs $0.07 more per wafer (a 2 nm thicker cap).
  Break-even yield gain                              0.07 / 1,400 = 0.005%
  Mean margin to the mask-height specification       M1: 8 nm;  M1-c: 46 nm   (Chapter 11)
  Probability of a lot-level mask-height excursion   M1: 10⁻³ per lot;  M1-c: 10⁻⁵ per lot   (illustrative)
  Expected scrap cost per wafer (25 wafers, $1,400)  M1: $1.40;  M1-c: $0.014
```

The saving is $1.39 per wafer for an outlay of $0.07: twenty to one. The probabilities are illustrative, and it is the ratio that matters: **the cap is cheap insurance against an event the margin of 8 nm does not exclude**.

### 16.6.3 M2 and M3

M2 and M3 cost 60% more than M1 and are not alternatives to it: they are what a smaller pitch requires. The relevant comparison is within each array, and the answers are in Chapter 14: for the 1d array the cost of the mask-open module is the smaller part of the decision, and the mold etch's costs, in Book #31, decide it.

---

## 16.7 New-Product Checklist

```
New-product checklist for the hard mask open:
  1. Array: pitch, exit CD, hole depth (→ aspect ratio, web, bow limit, wiggle limit; Ch. 10, 12)
  2. Mask: material (E, stress, hydrogen), thickness, cap thickness and uniformity (→ ceiling, top loss; Ch. 2, 11)
  3. Pattern: SADP×2 or EUV (→ families, LCDU, LER, partial-open rate, SiON overetch; Ch. 4, 13)
  4. Array efficiency and the CO baseline (→ O₂ load, endpoint; Ch. 1, 8, 10)
  5. Chemistry: passivation (COS, temperature, cyclic), fluorine content (→ x₀, cap selectivity; Ch. 3, 6, 7, 14)
  6. Tilt and edge: ring, dummy rows, litho compensation of the stress relaxation (Ch. 5, 10, 12)
  7. Chamber state: season, NF₃ interval, parts life (Ch. 5, 9)
  8. Metrology: CD-SAXS recipe, HV-SEM, ridge and witness structures; APC models (Ch. 15)
  9. Queue and hold: degas, FOUP purge (Ch. 9)
 10. Cost and sizing: cycle time, chambers, abatement, COS supply (Ch. 16)
```

---

## 16.8 The Handoff Sheet

What the open gives the capacitor etch, for the reference process M1 (the numbers on which Book #29's incoming specification can be checked):

```
Handoff from the hard mask open (M1; per wafer, 3σ unless stated):
  Exit CD, all families (site mean)         31.0 ± 1.0 nm; family offset 1.10 nm; LCDU 2.2 nm; edge roughness 1.95 nm
  Top CD / bow / minimum web                32.1 nm / 0.67 nm / 12.2 nm
  Foot                                      0.60 nm per side; local angle 89.3°; average angle 89.98°
  Ellipticity of the exit                   0.028
  Mask height, mean and lower bound         1350 nm; 1340 nm (Chapter 15 policy)   edge (shoulder) height 1210 nm
  Placement of the exit                     tilt 1.2 nm, wiggle 0.7 nm, relaxation 0.27 nm (compensated)   RSS 1.4 nm
  Defects from the open                     3.0 × 10⁻⁹ per hole (52 per die)
  Residue at the exit                       none ≥ 2 nm; sulfur ≤ 10¹⁴ cm⁻²; moisture ≤ 0.2 mg after a 4 h hold
  Top SiN support loss                      ≤ 2.4 nm
```

These are the numbers that the capacitor etch inherits: an exit that sets its top CD and its depth lag, a bow that sets the web it cannot see, a foot that sets its aperture, a height that sets its clock, and a count that sets the floor under its own not-open budget.

---

## Summary and Key Takeaways

1. **The open is cheap and the downside is large.** $15 a wafer under a wafer worth about a hundred times more; the leverage is in the margin.

2. **The open cannot be reworked more than once.** Strip, redeposit, and re-pattern once; a second rework is not allowed.

3. **Each failure has a signature in the bitmap.** Family pattern, pairs, step-change dead cells, radial and block-edge patterns; they arrive months late.

4. **Repair absorbs the isolated defects.** 0.086 events per sub-array; 2 × 10⁻⁵ of a die; what costs yield is the unrepairable 2 × 10⁻⁴ of them: 1.0% in M1, 1.5% in M0.

5. **Fifteen chambers cover 150,000 wafers a month for M1.** Four platforms; M2 and M3 need six; 31 kg of COS a month.

6. **The module costs $15.1; the etch is half.** 39% tool, 13% consumables, 40% deposition, 7% metrology; a second of chamber time is 3.6 cents and a point of utilization 7 cents a wafer.

7. **The extra dollar pays.** M1 over M0: 0.052% needed against 0.48% gained; M1-c over M1: 0.005% needed, and a scrap probability a hundred times smaller.

---

## Study Questions

1. Compute the sub-array repair loss for a product with 60 events per die, 800 sub-arrays, and 6 spares per sub-array (Poisson). Compare it with 4 spares.

2. A new array has f_u = 5 × 10⁻⁴ and 52 events per die. Find the yield loss and the extra loss relative to M1's 1.0% (f_u = 2 × 10⁻⁴).

3. For 100,000 wafer starts per month and M2 (cycle 299 s, 85% utilization), find the number of chambers and the number of four-chamber platforms. For 150,000, find the utilization at which five platforms (20 chambers) suffice.

4. A process change lengthens the cycle of M1 by 6 s and raises the tool cost by 3%. Compute the new fixed cost per wafer, using the model of Chapter 1: capital charge 24.8%, maintenance 6%, facility $0.15 M, 85% utilization, $9.0 M for the tool.

5. With the value of the wafer at $2,000 instead of $1,400, find the break-even yield gain of M1 over M0 and of M1-c over M1.

6. An M1 lot arrives at the capacitor etch after a 9 h wait in air. Using the moisture model of Chapter 9, estimate the water on each wafer, and say what the policy requires.

---

**Back to:** [README](../README.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
