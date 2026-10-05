# Chapter 11: Top Loss, Facets & Cap Consumption

## Overview

The mask loses height in the open, and the loss does not behave like an erosion. A film that erodes at a steady rate loses a steady thickness. The carbon under a SiON cap loses nothing until the cap fails, and then loses at the full rate of the plasma, 12 nm every second. On a 14 nm web the cap is a ridge, not a plate, and it fails from its two shoulders inward; the carbon under the failed part is cut at once, and the part that is still covered stands up as a crest. The mean loss of 50 nm that Chapter 2 budgeted is the average of a covered crest and shoulders that have been cut down by 190 nm.

This chapter develops that picture. It states the top-loss law and its table, shows the shape the mean hides (a crest 6 nm wide with shoulders 190 nm lower), puts numbers on the sensitivity that Chapters 2 and 6 hinted at (1 nm of cap is 21 nm of mask), compares the ways to remove the cliff, and finds that the cheapest is a cap 2 nm thicker. It closes with what the capacitor etch inherits from the shoulder, and the cap of M2.

**Learning Objectives:**
- Describe the SiON cap on a 14 nm web as a ridge and explain why it fails from the shoulders
- State and apply the top-loss law for x ≤ τ_w and x > τ_w
- Compute the shoulder loss, the crest width, and the edge height of the mask after the open
- Compute the sensitivity of the top loss to the cap's thickness, erosion rate, and the overetch
- Compare four ways to reduce the top loss by their cost and side effects
- Compute the specification of the cap and the margin of the capacitor etch's mask budget
- Compute the cap and the top loss of M2

---

## 11.1 The Ridge on the Web

The web between two holes is 12.9 nm wide at the top (the pitch of 45 nm minus the 32.1 nm top CD). The cap on it is a layer 40 nm thick and 12.9 nm wide, a ridge in cross-section, whose top is flat and whose sides are the walls of the two neighbouring holes. Ions strike the sides at grazing and oblique incidence, where the sputter yield peaks, and the shoulders retreat faster than a flat surface would erode:

```
Cap erosion (M1, 600 eV):
  Flat surface        v_cap = 0.237 nm/s       life of a flat 40 nm cap   40 / 0.237 = 169 s
  Shoulder factor     ρ = 1.15 (at 600 eV)      life of the ridge          t₀ = 169 / 1.15 = 146.8 s
  Lateral retreat of each shoulder   v_h = 0.215 nm/s
  Time for the two shoulders to close on the 12.9 nm web   τ_w = (12.9/2) / 0.215 = 30.0 s
```

There are therefore two clocks. The first, t₀, is the time at which the cap fails at the hole edge and the carbon beneath it is first exposed. The second, τ_w, is the time the failure takes to spread across the web: from t₀, the exposed width grows at v_h on each side, and the whole web top is exposed 30 s later. The model of Chapters 2 and 6 is the integral of these two clocks.

---

## 11.2 The Top-Loss Law

### 11.2.1 The Law

Let T be the total time the carbon top is exposed to the plasma (main etch plus overetch), and x = T − t₀ the time since the cap first failed. The carbon at the hole edge has been exposed for x seconds and has lost ER_top × x. The carbon at a distance y from the hole edge has been exposed for x − y/v_h seconds. The mean loss over the web is:

```
L = ER_top x² / (2 τ_w)          for 0 ≤ x ≤ τ_w      (the exposed strip is not yet the whole web)
L = ER_top (x − τ_w/2)           for x > τ_w          (the whole web is exposed)
L = 0                            for x ≤ 0

M1:  ER_top = 12.17 nm/s,  τ_w = 30 s,  t₀ = 146.8 s,  T = 162.4 s
     x = 15.6 s;   L = 12.17 × 15.6² / 60 = 49.6 nm
```

### 11.2.2 The Table

```
Top loss L versus the time x since the cap failed (M1; ER_top = 12.17 nm/s):
  x (s)          0     5     10     15.6    20     25     30     40
  L (nm)         0     5     20     50      81     127    183    304
  After open     1400  1395  1380   1350    1319   1273   1217   1096
```

The loss grows as x² until the whole web is exposed, at which point it grows linearly at the full rate of 12.17 nm/s. M1 runs at x = 15.6 s, just over half of τ_w, where each second of overetch costs 6.3 nm. At x = 30 s each costs 12.2 nm; below x = 5 s, less than 2 nm.

---

## 11.3 The Shoulder and the Crest

The mean hides a profile. At the end of the open the web top is not flat:

```
Web top after the open (M1, x = 15.6 s):
  Exposed strip on each side          v_h x = 0.215 × 15.6 = 3.4 nm
  Covered crest in the middle         12.9 − 2 × 3.4 = 6.2 nm wide, at the full height of 1400 nm
  Loss at the hole edge               ER_top x = 12.17 × 15.6 = 190 nm
  Mean loss over the web              (190 × 3.4 / 6.45) / 2 = 50 nm  ✓
  Height at the hole edge (shoulder)  1400 − 190 = 1210 nm
```

The shoulder is the part of the mask that faces the capacitor etch's ions. The facet that grows at the hole edge in Book #29 starts from the shoulder, not from the crest, which is 190 nm higher and 3.4 nm further out, and which is consumed in the first part of the mold etch. The mask budget that matters to the facet is therefore the **edge height** and not the mean:

```
Mask budget by the measure the facet sees (illustrative; mold etch consumption 616 nm, Book #29):
                               M0        M1        M1-c (cap 42)    M2 (1d)
  Mean loss L (nm)             62        50        14               50
  Exposed time x (s)           16.4      15.6      8.3              17.9
  Loss at the hole edge (nm)   227       190       101              167
  Crest width (nm)             5.7       6.2       9.3              4.0
  Edge height (nm)             1173      1210      1299             1333
  Consumed by the mold etch    616       616       616              600
  Edge height at the end       557       594       683              733
  Margin over 500 nm           57        94        183              233
```

For M1 the margin by the edge height is 94 nm, not the 234 nm that the mean (1350 − 616 − 500) suggests. The two agree only when the cap has not failed. **The mean is the quantity the specification is written on; the edge is the quantity the capacitor etch's facet is made on; the cliff is the difference between them.**

---

## 11.4 Sensitivities

### 11.4.1 To the Cap

```
Top loss and its sensitivity versus the cap thickness (M1; ER_top 12.17 nm/s, v_cap 0.237 nm/s, T = 162.4 s):
  Cap (nm)            40      41      42      43      44
  Ridge life t₀ (s)   146.8   150.4   154.1   157.8   161.4
  x (s)               15.6    12.0    8.3     4.6     1.0
  L (nm)              50      29      14      4       0.2
  dL/dT (nm/s)        6.3     4.9     3.4     1.9     0.4
```

One nanometre of cap shifts the failure by 3.7 s and the mean loss by 21 nm (40 → 41); the next nanometre by 15 nm; the fifth by 4 nm. The sensitivity falls as the cap thickens, because the exposed time x falls and with it the slope of the loss, ER_top x/τ_w.

### 11.4.2 To the Other Quantities

```
  Overetch ± 3 s                    +21 / −17 nm        (6.3 nm/s at x = 15.6 s)
  Cap erosion rate ± 1%             ± 1.5 s of t₀ → ± 9 nm
  Film rate ± 3% (hydrogen ± 1 at%) −22 / +30 nm        (the clock T moves; the cap's does not)
  Cap thickness ± 0.4 nm            ± 1.5 s → ± 9 nm
  Carbon thickness ± 14 nm          ± 1.75 s of T → ± 11 nm of loss: 79% of the carbon error is returned as top loss (M1-c: 42%)
  Ion energy +20 eV                 −2.5 s of T, ρ + 0.015, v_cap + 4% → + 17 nm
  COS +1 sccm                       v_cap + 1% → − 1.5 s of t₀ → + 9 nm
```

Every line is either a clock on the carbon's side (T) or a clock on the cap's side (t₀). The top loss is the quantity that sees their difference squared.

---

## 11.5 Removing the Cliff

The cliff can be moved by changing either clock. Four ways to bring the loss from 50 nm to about 15 nm:

```
Ways to reduce the top loss (M1 as the starting point):
  Change                         L after    Bow      Time        Cost per wafer     Notes
  ───────────────────────────────────────────────────────────────────────────────────────────────
  Cap 40 → 42 nm (M1-c)          14 nm      0.67     +0.6 s      +$0.08             SiON deposition +5% ($0.055);
                                                                                      SiON open +0.6 s ($0.022)
  Ion energy 600 → 540 eV        12 nm      0.69     +8.0 s      +$0.29             ER₀ 730 → 683 nm/min
  COS 30 → 26 sccm               19 nm      0.72     none        −$0.02             +0.05 nm of bow; ACL:SiON 51 → 54
  Overetch 18 → 15 s             33 nm      0.66     −3 s        −$0.11             the clear is cut to 8 s: not allowed
```

The overetch cannot be shortened below the 11 s of the clear (Chapter 8). The COS and the energy trade the loss against the bow and the time. **The cap is the cheapest way, and the only one that costs nothing in the profile or the throughput.** The reference process of this book keeps the 40 nm cap that Book #29 specifies, so that the numbers of Chapters 1 to 10 are consistent with it; a product that can adopt M1-c should.

```
M1-c (cap 42 nm), margin in the mean:
  L = 14 nm;  after open 1386 nm;  flat SiON left 3.5 nm (against 1.5)
  dL/dT = 3.4 nm/s;  cap life ± 1.9 s (3σ) → L ± 6.4 nm
  Carbon thickness ±14 nm enters the mask height with slope 1 − 3.4 × 0.125 = 0.58 → ±8.1 nm   (M1: 0.21 → ±3.0 nm)
  After-open height at 3σ: 1386 − √(8.1² + 6.4²) = 1386 − 10.3 = 1376 nm     (specification 1330: margin 46 nm; M1: 8 nm)
```

The spread of the loss falls from ±11.9 nm to ±6.4 nm, because the slope falls from 6.3 to 3.4 nm/s. Thickening the cap does two things: it moves the mean, and it flattens the curve that carries the variation. One thing it gives back: the open now returns only 42% of a carbon thickness error as top loss (79% in M1), so the carbon's own variation passes through to the mask height almost undiminished.

---

## 11.6 The Cap Specification

```
SiON cap (M1 and M1-c):
                               M1            M1-c
  Thickness                    40.0 ± 0.4    42.0 ± 0.42 nm (3σ, 1.0%)
  Within wafer                 ≤ 0.7%        ≤ 0.7%
  Erosion rate (chamber to chamber, ±) 0.8%   0.8%
  Erosion rate vs a witness    ACL:SiON 51 ± 1.5  (blanket SiON in the ME chemistry)
  Remaining flat SiON (after the open)  1.5 nm   3.5 nm
```

Thickness is a measurement that has to be accurate to 0.1 nm to be useful, and ellipsometry on a SiON film that thin does that (repeatability 0.03 nm), but accuracy against the process is another matter: the cap thickness must be measured on the same wafer at the same site as the carbon thickness (Chapter 15). The erosion rate, a ±0.8% quantity of a chamber, is checked daily on a blanket SiON witness (Appendix C).

---

## 11.7 What the Capacitor Etch Inherits

The mold etch begins on a mask whose web tops are the shoulder and the crest. The sequence of events in its first minute:

```
First 60 s of the capacitor etch on the M1 mask:
  Remaining SiON (1.5 nm flat) removed in the first second by the fluorocarbon plasma (SiON etches like oxide)
  Crest (6 nm wide, 190 nm above the shoulder) attacked on both sides by ions at grazing angle;
    lateral erosion of ≈ 0.05 nm/s per side → lifetime ≈ 3 nm / 0.05 nm/s = 60 s
  Shoulder at 1210 nm; facet grows from the hole edge (Book #29: ≈ 8° at 110 s, 14° at 215 s, 20° at 305 s)
  Top CD of the mold hole: 31.0 nm at the start, 32.0 nm at the end (Book #29), partly the facet and partly
    the mask CD profile arriving at the top as the mask thins
```

A mask with a wider crest (M1-c, 9.3 nm) lasts about half again as long as M1's (93 s against 62 s) before the shoulder is exposed to the full ion flux, and a mask with a narrower one (M2, 4.0 nm) about two-thirds as long (40 s). The behaviour is not a prediction of Book #29's facet timeline, which was written on the mean; it is a refinement of its starting point.

---

## 11.8 The Cap of M2

M2 opens B-ACL, which needs a few percent of CF₄ to carry boron off as BF₃ (Chapter 14). The fluorine attacks the cap, and the blanket selectivity falls from 51 to 38:

```
M2 (1d-class, B-ACL, 1500 nm; −25 °C, cyclic):
  Process time T = 208.5 + 22 = 230.5 s;  ER_top = 9.33 nm/s (B-ACL, 560 nm/min time-averaged)
  Cap 60 nm SiON; v_cap = 0.245 nm/s;  ACL:SiON = 9.33 / 0.245 = 38;  ρ = 1.15
  t₀ = 60 / 0.245 / 1.15 = 212.6 s;  x = 17.9 s;  τ_w = (9.9/2)/v_h = 30 s (web top 37 − 27.1 = 9.9 nm)
  L = 9.33 × 17.9² / 60 = 50 nm;  after open = 1500 − 50 = 1450 nm  (Book #31)
  Loss at the hole edge 9.33 × 17.9 = 167 nm;  edge height 1333 nm;  crest 4.0 nm wide
```

M2 needs a 60 nm cap against M1's 40 nm, for a mask 7% taller and a process 42% longer, a tool that attacks the cap 35% faster in relative terms (selectivity 38 against 51), and a wafer at −25 °C that opens more slowly. The cap-to-carbon ratio is 4.0%, against M1's 2.9%.

---

## Summary and Key Takeaways

1. **The cap on a 14 nm web is a ridge.** Its shoulders retreat at 0.215 nm/s; the ridge fails at the hole edge at t₀ = 146.8 s and across the web 30 s later.

2. **Top loss is L = ER_top x²/(2τ_w).** x = T − t₀ is the time since the cap failed; M1 is at x = 15.6 s, L = 50 nm, 6.3 nm per second of overetch.

3. **The mean hides a crest and shoulders.** A 6.2 nm crest at 1400 nm and shoulders at 1210 nm; the edge height, not the mean, is what the facet is made on; the margin is 94 nm, not 234.

4. **One nanometre of cap is 21 nm of mask.** 40 → 41 nm: 50 → 29 nm; 42 nm: 14 nm. The sensitivity falls as the cap thickens.

5. **The cheapest cure is a thicker cap.** 2 nm costs $0.08 and nothing in profile or time; it raises the edge margin from 94 to 183 nm and halves the spread of the loss.

6. **Energy and COS trade the loss for time and bow.** 540 eV: +8 s, $0.29; 26 sccm COS: +0.05 nm of bow.

7. **M2 needs a 60 nm cap.** Selectivity 38, x = 17.9 s, L = 50 nm; the cap is 4.0% of the carbon height against M1's 2.9%.

---

## Study Questions

1. For M1 compute the loss at the hole edge, the strip exposed on each side, and the crest, if the overetch is lengthened by 4 s. What fraction of the web is exposed?

2. For a cap of 41.0 nm find t₀, x, L, and dL/dT. If the cap thickness varies by ±0.4 nm (3σ) and the rate by ±0.8%, find the 3σ of L.

3. Show that the mean loss is the integral of the loss over the half-web divided by its width, L = ER_top x²/(2τ_w), by integrating ER_top (x − y/v_h) over y from 0 to v_h x on the half-web of width v_h τ_w.

4. A product has a web top of 11.0 nm (a smaller pitch). Find τ_w at the same v_h and the exposure x at which the whole web is exposed. Does the loss at x = 15.6 s change?

5. At 700 eV the facet factor is ρ = 1.23 and the cap rate 0.259 nm/s. Find t₀ for a 40 nm cap, x for T = 152 s, and L with ER_top = 13.4 nm/s. Compare with the table of Chapter 6 (147 nm).

6. The edge height of a mask must be at least 1150 nm for a mold etch that consumes 650 nm and leaves 500 nm. Find the maximum loss at the edge, and the maximum x for ER_top = 12.17 nm/s. Which of the cap thicknesses of Section 11.4.1 meet it?

---

**Next Chapter:** [Chapter 12: The Webs — Mechanics, Wiggling, Twist & Distortion](./12-webs-mechanics-wiggling-distortion.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
