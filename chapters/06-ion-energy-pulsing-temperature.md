# Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Profile Levers

## Overview

An engineer who sets out to improve the carbon open has five obvious controls: the ion energy, the pulse of the bias, the temperature of the wafer, the flow of COS, and the source power. Each moves several outputs at once, and the outputs do not move together. The bow responds to temperature and, a little, to COS. The top loss responds to nearly everything, hugely. The open time responds to energy, power, and temperature. A lever that cures one defect usually costs another.

This chapter measures the levers one at a time on the M1 reference, using the model of Chapter 3 extended with the cap model of Chapter 2, and puts the results in one table. It then rebuilds M1 from M0 step by step to show where its bow came from. Two results stand out. First, **the bow is a temperature and passivation problem; energy, duty, and power barely touch it**. Second, **the top loss is a cap-timing problem on which every lever acts**, and M1 sits at the fast edge of its specification, where one second of overetch costs 6 nm of mask.

**Learning Objectives:**
- State which outputs each lever (energy, duty, frequency, temperature, COS, power) moves, and in which direction
- Use the energy sweep to find the fastest energy that meets the mask-height specification, and the cost of a margin
- Compute the effect of duty at constant time-averaged ion flux on the bow
- Compute the effect of wafer temperature on the lateral rate, the bow, the open time, and the cap budget
- Explain why COS is a poor lever for the bow and a bad one for the top loss
- Read the sensitivity table and the (energy, COS) window
- Account for the bow gained from M0 to M1 step by step

---

## 6.1 What Each Lever Moves

```
Mapping from controls to model parameters (M1 centre: 600 eV, 70% duty, 10 °C, COS 30 sccm, 1.5 kW):

  Control          Acts on                                                       Dependence used
  ───────────────────────────────────────────────────────────────────────────────────────────────────
  Ion energy E     ER₀, cap rate (v_phys), facet factor ρ, passivant removal x₀    ER₀ ∝ (√E − 5);  v_phys ∝ (√E − √90);
                                                                                   ρ = 1 + 0.75×10⁻³ (E − 400);
                                                                                   x₀ ∝ 0.7 + 0.3 (√E − √50)/(√600 − √50)
  Duty             x₀ (at constant time-averaged ion flux)                       x₀ ∝ 1 − 0.4 (1 − duty)
  Temperature      bare lateral rate v_b; ER₀                                    v_b ∝ exp(−0.42 eV/kT);  ER₀ +0.3%/K
  COS flow         passivant supply (x₀), chemical cap rate v_chem               x₀ ∝ COS^−0.46;  v_chem ∝ COS
  Source power     ion flux (ER₀, v_phys), O flux (v_b, χ)                       Γ_i ∝ P;  Γ_O ∝ P^0.6
  Overetch time    exposure; cap exposure                                         adds to T
```

The mapping is a fit to the model of Chapter 3, not a derivation. It reproduces the M1 centre exactly (ER₀ 730 nm/min, main etch 144.4 s, top loss 50 nm, bow 0.67 nm), and the departures from it are the content of this chapter.

---

## 6.2 Ion Energy

### 6.2.1 The Energy Sweep

```
M1 at other ion energies (all else fixed; the main etch runs to the same endpoint):

  E (eV)           250    400    500    600    700    800    1000
  ER₀ (nm/min)     405    562    650    730    803    872    997
  Main etch (s)    237    179    159    144    134    126    114
  Total ACL (s)    255    197    177    162    152    144    132
  ACL:SiON         47.9   50.0   50.8   51.3   51.8   52.1   52.6
  Facet factor ρ   1.00   1.00   1.07   1.15   1.23   1.30   1.45
  Cap life t₀ (s)  284    214    174    147    126    110    87
  Exposed x (s)    —      —      2      16     26     33     44
  Top loss (nm)    0      0      1      50     147    267    487
  After open (nm)  1400   1400   1399   1350   1253   1133   913
  Bow (nm)         0.87   0.74   0.70   0.67   0.65   0.64   0.63
```

Two things stand out. The bow hardly moves (0.63 to 0.87 nm over a factor of four in energy): a higher energy shortens the open and the wall sees less of the oxygen, while lowering the sputter removal of the passivant, and the two nearly cancel. And the top loss moves enormously. At about 500 eV and below the cap outlasts the open and the carbon top is hardly touched. At 600 eV it is exposed for 16 s; at 700 eV, for 26 s, and the mask comes out 97 nm shorter than at 600 eV, 77 nm below the specification.

### 6.2.2 The Fastest Energy That Meets the Mask

```
Fine sweep near the reference:
  E (eV)             500     520     540     560     580     600     620     640
  Main etch (s)      158.6   155.4   152.4   149.6   146.9   144.4   142.1   139.9
  Top loss (nm)      0.9     5.1     12.5    22.6    35.1    49.8    66.4    84.6
  After open (nm)    1399    1395    1388    1377    1365    1350    1334    1315
```

Each 20 eV costs 2.5 s of open time and 15 nm of mask, near 600 eV. The after-open height must be at least 1348 nm for the 3σ lower bound to reach 1330 nm (Chapter 2); the reference energy of 600 eV is the highest, and therefore **fastest**, that does. It is also at the edge of the specification, with 2 nm of margin. A fab that wanted margin would take a lower energy:

```
M1 at 540 eV (a margin-seeking variant, "M1-m"):
  Main etch      152.4 s   (+8.0 s)
  Top loss       12.5 nm   (−37 nm)        After open 1388 nm (+38 nm of margin)
  Cost           8.0 s × $0.036/s = $0.29 per wafer   (cycle time 218 → 226 s, 66.1 → 63.7 wafers/h)
  Bow            0.69 nm   (+0.02)
```

The extra 38 nm of mask is worth about 38 / 1.9 nm/s = 20 s of mold-etch time (Book #29: 576 nm in 305 s), and a 20 s buffer costs 8 s here. Chapter 11 shows that a 2 nm thicker cap does the same job at lower cost, by moving the cliff and not the clock.

---

## 6.3 Bias Pulsing

### 6.3.1 Duty at Constant Ion Flux

Pulsed bias is not a free lever: lowering the duty at fixed power lowers the time-averaged ion flux, slows the etch, and moves the cap's life. The comparison that isolates the effect of the pulse is at **constant time-averaged ion flux**, where the source (and the on-phase flux) is raised to compensate. The ER₀, the open time, and the cap's life are then fixed, and only the passivant balance changes:

```
x₀ ∝ 1 − 0.4 (1 − duty)       (the removal of the film falls in the off-phase, when the ions are gone)

  Duty              0.5     0.6     0.7     0.8     0.9     1.0 (CW)
  x₀ factor         0.91    0.96    1.00    1.05    1.09    1.14
  Bow (nm)          0.61    0.64    0.67    0.70    0.73    0.76
```

The effect is 0.03 nm per 0.1 of duty. The pulse is the **smallest** of the bow levers (Section 6.6). Its value is elsewhere: it relaxes the charge on the floor of the tube between pulses (Book #29, Chapter 13), and, in M2, it is what lets the cyclic scheme alternate deposition and etch (Chapter 7).

### 6.3.2 Frequency

```
Pulse frequency (70% duty), effect on x₀ (illustrative):
  f (kHz)        1       2       5       10      20
  Period (µs)    1000    500     200     100     50
  Off-time (µs)  300     150     60      30      15
  x₀ factor      1.08    1.03    1.00    0.99    1.02
  Limit          wall bows between pulses   —   edges (≈ 8 µs) eat the off-time
```

The curve is flat between 2 and 10 kHz. Below 2 kHz the on-phase is long enough for the wall to lose coverage between pulses; above 10 kHz the 8 µs rise and fall times of the bias reduce the effective off-time and the effective duty. The reference of 5 kHz is mid-plateau. The edges of the bias must be sharp, and the plasma must follow, but the exact frequency is not critical.

---

## 6.4 Wafer Temperature

### 6.4.1 The Strongest Lever on the Bow

The bare lateral rate is activated (E_a = 0.42 eV), and the bow is proportional to it. Temperature is the only control that acts on the oxygen's attack on the wall directly:

```
Wafer temperature (M1, main etch):

  T (°C)                  −25     0       5       10      15      20
  v_b factor (vs 10 °C)   0.088   0.532   0.74    1.00    1.35    1.80
  ER₀ (nm/min)            653     708     719     730     741     752
  Main etch (s)           157.9   148.0   146.2   144.4   142.7   141.1
  Bow (nm)                0.06    0.37    0.50    0.67    0.90    1.19
  Minimum web (nm)        12.9    12.6    12.4    12.2    12.0    11.6
  Top loss (nm)           154     73      61      50      40      32
  After open (nm)         1246    1327    1339    1350    1360    1368
```

At 20 °C the bow of the M1 recipe would already exceed the 1.0 nm limit. Each kelvin moves the bow by 0.04 nm, the bare lateral rate by 6.1%, and the open by 0.3 s. Cooling the wafer reduces the bow to almost nothing at −25 °C, but a cold wafer opens more slowly (ER₀ −0.3% per K), and, with the cap's life fixed, a longer open means more top loss: at −25 °C the mask comes out 104 nm shorter than at 10 °C. **The temperature gain is real only if the cap is thickened to match**, which is why M2, at −25 °C, carries a 60 nm cap (Chapter 14).

### 6.4.2 Limits

A cold wafer adsorbs. Carbonyl sulfide boils at −50 °C and SO₂ at −10 °C, so at −25 °C the SO₂ formed in the plasma physisorbs on the wall of the tube and the passivant film becomes a condensate that thickens at the cold bottom. The foot gets thicker, the exit narrower, and the closure tail (Chapter 4) heavier. The reference at 10 °C stays well above these limits. The electrostatic chuck needs a coolant at −20 °C to hold the wafer at 10 °C under 1.2 kW of plasma heating (Chapter 5).

---

## 6.5 COS: Passivant and Cap Etchant

COS is the source of the low-sticking passivant, and also of the chemical attack on the cap. Both scale with the flow:

```
COS flow (M1, 600 eV):
  COS (sccm)            20      25      30      35      40
  x₀ factor             1.20    1.09    1.00    0.93    0.88        (x₀ ∝ COS^−0.46)
  v_chem (nm/s)         0.047   0.059   0.071   0.083   0.095
  v_cap (nm/s)          0.213   0.225   0.237   0.249   0.261
  ACL:SiON              57      54      51      49      47
  Cap life t₀ (s)       163     155     147     140     133
  Top loss (nm)         0       13      50      104     171
  After open (nm)       1400    1387    1350    1296    1230
  Bow (nm)              0.81    0.73    0.67    0.63    0.59
```

Five sccm of COS lowers the bow by **0.04 nm** and costs **54 nm of mask**. It is a poor lever for the bow and a dangerous one for the cap. The reference flow of 30 sccm is chosen for the passivant coverage it brings against M0's 6 sccm (x₀ down by a factor of 2.1), and it is already the upper limit for the mask. A recipe that needs more passivant must get it from a lower temperature, a cleaner wall, or a thicker cap.

---

## 6.6 The Sensitivity Table

```
One-at-a-time response of M1 (centre: ER₀ 730 nm/min, main etch 144.4 s, top loss 50 nm, bow 0.67 nm):

  Lever                         ER₀    Main    Top loss   After open   Bow     Min web   ACL:SiON
                                       etch    (nm)       (nm)         (nm)    (nm)
  ─────────────────────────────────────────────────────────────────────────────────────────────────
  Ion energy +100 eV            803    133.9   147        1253         0.65    12.3      51.8
  Ion energy −100 eV            650    158.6   1          1399         0.70    12.2      50.8
  Duty +0.1 (const. avg flux)   730    144.4   50         1350         0.70    12.2      51.3
  Duty −0.1 (const. avg flux)   730    144.4   50         1350         0.64    12.2      51.3
  Wafer temperature +5 K        741    142.7   40         1360         0.90    12.0      52.1
  Wafer temperature −5 K        719    146.2   61         1339         0.50    12.4      50.6
  COS +5 sccm                   730    144.4   104        1296         0.63    12.3      48.9
  COS −5 sccm                   730    144.4   13         1387         0.73    12.2      54.0
  Source power +10%             803    132.3   39         1361         0.66    12.2      52.8
  Source power −10%             657    159.1   68         1332         0.69    12.2      49.7
  Overetch +3 s                 730    144.4   71         1329         0.69    12.2      51.3
  Overetch −3 s                 730    144.4   33         1367         0.66    12.3      51.3
```

Reading the table:

1. **The bow lives on one axis.** Only temperature moves it by more than 0.1 nm for a reasonable change (±5 K: +0.23 / −0.17 nm). COS moves it by 0.04–0.06 nm, everything else by less.
2. **The top loss lives on all of them.** Every lever shifts it by tens of nanometres. The mask height is the output with no margin.
3. **Time cuts both ways.** A longer main etch (lower power, lower energy, lower temperature) lengthens the exposure of the cap and the wall. The first is far more costly than the second.
4. **The web follows the bow.** The minimum web varies from 12.0 to 12.4 nm across the table, 0.7 σ_t in the units of Chapter 4.

### 6.6.1 The (Energy, COS) Window

```
Top loss (nm) / bow (nm) over energy and COS flow (other parameters as M1):
              500 eV     550 eV     600 eV     650 eV     700 eV
  COS 20      0 / 0.84   0 / 0.82   0 / 0.81   10 / 0.80  38 / 0.79
  COS 25      0 / 0.76   0 / 0.74   13 / 0.73  43 / 0.72  86 / 0.71
  COS 30      1 / 0.70   17 / 0.69  50 / 0.67  94 / 0.66  147 / 0.65
  COS 35      23 / 0.65  58 / 0.64  104 / 0.63 158 / 0.62 217 / 0.61
  COS 40      69 / 0.61  116 / 0.60 170 / 0.59 228 / 0.58 285 / 0.57
```

The specification needs a top loss of at most 50 nm (after-open height at least 1348 nm for a 3σ bound of 1330 nm). Every cell in the upper left meets it and has a bow between 0.65 and 0.85 nm, inside the 1.0 nm limit. The window is not narrow in bow but one-sided in mask height, and its boundary runs along the diagonal from (500 eV, 35 sccm) to (700 eV, 20 sccm). The reference lies on the boundary.

---

## 6.7 Where M1's Bow Came From

M1 is M0 with five changes. Applying them in order to the model of Chapter 3 gives the bow after each:

```
Waterfall from M0 to M1 (maximum CD − top CD):
  Step                                                            Bow (nm)    Change
  M0 (CW 800 eV, 20 °C, COS 6, 1.0 kW)                            2.01
  1  Wafer 20 → 10 °C  (v_b × 0.556)                              1.12        −0.89
  2  COS 6 → 30 sccm  (x₀ × 0.476)                                0.54        −0.58
  3  5 kHz, 70% pulse at constant avg. flux (x₀ × 0.89)           0.48        −0.06
  4  Source +50%, 600 eV: O flux × 1.27, ER₀ 830 → 730            0.61        +0.13
  5  Cleaner wall (ℓ_O 2200, ℓ_p 800, c 8, ℓ_c 60), OE 18 s       0.67        +0.06
  M1                                                              0.67
```

The two big steps are the temperature (−0.89 nm, 44% of M0's bow) and the COS (−0.58 nm, 29%). The pulse gives only 0.06 nm. Steps 4 and 5 give some of the gain back: more oxygen (from the extra source power) attacks the wall faster, and the wall parameters that go with M1's recipe are not as good as the ideal one. **M1's bow is bought with a cold chuck and a sulfur-rich gas**, and each is paid for elsewhere: the cold chuck in a longer open and a harder temperature control; the sulfur in a cap that is attacked 20% faster and in abatement.

---

## Summary and Key Takeaways

1. **The bow lives on temperature and passivation.** ±5 K moves it +0.23 / −0.17 nm; 5 sccm of COS moves it 0.04–0.06 nm; ±100 eV moves it 0.02–0.03 nm.

2. **The top loss lives on everything.** 100 eV is 97 nm (49 → 147); 5 sccm of COS is 54 nm; 3 s of overetch is 21 nm. Mask height is the output with no margin.

3. **M1 runs at the fast edge of the mask specification.** 600 eV is the highest energy that meets it; 540 eV buys 38 nm of margin for 8 s and $0.29 a wafer; a thicker cap buys it cheaper (Chapter 11).

4. **The pulse is the smallest bow lever.** At constant ion flux it moves x₀ by 4.5% per 0.1 of duty and the bow by 0.03 nm; its value is in charging relief and in the cyclic scheme, not in the profile.

5. **Cooling works only if the cap grows with it.** −25 °C gives a bow of 0.06 nm and costs 104 nm of mask at a fixed cap.

6. **COS is a trade, not a dial.** More COS lowers the bow slightly and shortens the cap's life: 0.04 nm of bow for 54 nm of mask.

7. **M1's bow was bought with a cold chuck and sulfur.** Temperature −0.89 nm, COS −0.58 nm, pulse −0.06 nm, against +0.19 nm given back by the extra source power and the wall.

---

## Study Questions

1. Using ER₀ ∝ (√E − 5), find ER₀ at 540 eV. Scale k and k₂ in proportion to ER₀ and find the main-etch time to depth 1400 nm (w = 31 nm), and compare it with 152.4 s.

2. The wafer temperature of one chamber is 3 K above the others. Estimate the change in bare lateral rate, in bow (0.04 nm per K), and in the specification margin (bow limit 1.0 nm).

3. Using x₀ ∝ COS^−0.46, find x₀ for a COS flow of 36 sccm, and the new cap rate v_cap = 0.166 + 0.071 (COS/30). With ρ = 1.15 and τ_w = 30 s, find the cap life t₀ and the top loss for a total ACL time of 162.4 s.

4. At constant time-averaged ion flux, find x₀ and the bow for a duty of 0.45. If the on-phase flux must rise to keep the average, by what factor does it rise relative to 70% duty?

5. An 8 s lengthening of the cycle time costs $0.29 per wafer. Find the cost per second used in the text, and the yearly cost for a fab running 150,000 wafers a month.

6. If the ESC cannot reach −14 °C and the wafer runs at 15 °C, which of the five steps of Section 6.7 would you restore to recover the bow, and by how much, using the figures of the sensitivity table?

---

**Next Chapter:** [Chapter 7: Passivation Engineering, Cyclic Processes, Trim & Atomic-Layer Carbon Etch](./07-passivation-cyclic-trim-ale.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
