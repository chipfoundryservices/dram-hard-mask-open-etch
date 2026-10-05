# Chapter 13: Residue, Not-Open Holes & Stochastic Defects

## Overview

Chapter 4 gave the defect budget of the open as seven numbers adding to 3.0 × 10⁻⁹ per hole. This chapter opens them up. Each number is the rate of a rare event at the level of one hole in three hundred million, and none of them can be seen directly. Their mechanisms are what the engineer has to control, and each has a different kind of statistics: the **litho-origin** defects come from a population that the SiON open thins out by a known factor per second; the **pinch-off** of a hole in the carbon is a tail of a distribution with an exponential scale, and is so sensitive to that scale that a 5% change in it halves the rate; the **micromask** is a count of arrivals at the foot of a tube; the **merged hole** is the Gaussian margin of the web's thickness plus a non-Gaussian tail.

The chapter takes them in turn, builds the models, gives the amplification each defect receives in the capacitor etch, describes how any of this can be detected, and ends with the question of where an engineer should spend effort: the answer is on the quantities that sit in an exponent.

**Learning Objectives:**
- Describe each defect class of the open and the mechanism that makes it
- Model closure of a hole as a tail event and compute its sensitivity to the tail scale
- Reconcile the litho-origin populations with the SiON overetch and the oxygen of the main etch
- Convert a per-hole rate into events per area, per die, and per wafer, and into an inspection area
- State what each defect becomes in the capacitor etch
- Say what can be detected, by what method, and with what delay
- Rank the controls by their leverage on the defect rate

---

## 13.1 The Defect Classes

```
Defects of the hard mask open (M1; per hole; Chapter 4):
  Class                           Rate         Per die    Mechanism
  ──────────────────────────────────────────────────────────────────────────────────────────────────
  Closed or blocked cap opening   0.9 × 10⁻⁹   15.5       litho partial opens too thick to clear (§13.2)
  Cap-open residue                0.5          8.6        inorganic plugs in cap openings that survive the SiON overetch (§13.2)
  Pinch-off in the carbon         0.7          12.0       closure tail of the narrowing of the hole (§13.3)
  Micromask / footing at the exit 0.5          8.6        rare arrivals of involatile species at the foot (§13.4)
  Merged holes                    0.2          3.4        the web broken through (Chapter 4, §13.5)
  Particles                       0.1          1.7        shadowing by particles on the cap (Chapter 9)
  Displaced or twisted            0.1          1.7        beyond-tolerance placement (Chapter 12)
  ──────────────────────────────────────────────────────────────────────────────────────────────────
  Total                           3.0 × 10⁻⁹   51.5       (M0: 4.4 × 10⁻⁹, 76 per die)
```

---

## 13.2 Litho-Origin Defects and the SiON Overetch

### 13.2.1 Populations

The lithography leaves a small number of cap openings that are not clean. Before the SiON overetch the SADP×2 route has about 10⁻⁸ per hole that are partially open (a thin layer of scum in the bottom of the opening), and about 10⁻¹¹ that are missing or closed. The partially open openings are of two kinds:

```
Partially open cap openings (SADP×2: 10⁻⁸ per hole before the overetch):
  Organic scum (BARC, resist residue; 79%)         removed by the oxygen of the first seconds of the main etch
  Thick scum that remains blocked (9%)             0.9 × 10⁻⁹    → "closed or blocked" in the budget
  Inorganic plugs (SiON, SiOₓ; 12%)                1.2 × 10⁻⁹ before the overetch
```

The inorganic plugs are the problem. Oxygen does not remove them, and a plug on the foot of a cap opening blocks the carbon beneath it as completely as a missing opening. The SiON overetch clears them at the rate that Chapter 4 gave: the survivors after t seconds are exp(−0.5 t):

```
Cap-open residue after the SiON overetch (SADP×2, 12% inorganic):
  SiON overetch (s)         0       2       4       6
  Survivors                 1.00    0.37    0.14    0.05
  Rate (× 10⁻⁹ per hole)    1.20    0.44    0.16    0.06
  Budget line               —       0.5 ✓   —       —
```

### 13.2.2 EUV

The EUV route has more partially open openings, 5 × 10⁻⁸, because of its stochastic printing. The same fractions give a very different budget:

```
EUV, 5 × 10⁻⁸ partially open per hole:
  2 s overetch:   blocked 4.5 × 10⁻⁹   +  plugs 2.2 × 10⁻⁹     = 6.7 × 10⁻⁹   ✗ (budget 1.4 × 10⁻⁹)
  4 s overetch:   blocked 1.7 × 10⁻⁹   +  plugs 0.8 × 10⁻⁹     = 2.5 × 10⁻⁹   ✗
EUV at 2 × 10⁻⁸ and a 4 s overetch:                                1.0 × 10⁻⁹   ✓
```

The overetch widens the cap CD by 0.1 nm per second, so the extra 2 s costs 0.2 nm of CD; the EUV route's lithography also has to deliver a partially-open rate no worse than 2 × 10⁻⁸. **For EUV the stochastic defect rate is a litho specification, and the open can buy a factor of 2.7 per 2 s of overetch.** That is the litho–etch trade of Book #31, with the same form.

---

## 13.3 Pinch-Off

### 13.3.1 The Closure Threshold

A hole stops when its exit is narrower than a critical width. The reason is the ion acceptance: the tube accepts ions within atan(w/h) of its axis, and as w falls the fraction that arrive falls with it, while the supply of the redeposited fragments that build the foot does not:

```
Ion acceptance and transmission versus exit width (h = 1350 nm, σ_θ = 0.91°):
  w (nm)         31      26      20      16      12      10      8
  AR             44      52      68      84      112     135     169
  f_i            0.65    0.52    0.35    0.24    0.145   0.10    0.07
```

At 12 nm the ion transmission has fallen to 0.145, about a fifth of its value at 31 nm. The foot, which grows at a rate independent of the ion flux, overtakes the etch, narrows the exit further, and shuts it. The critical width is w_c = 12 nm, a narrowing of δ_c = 31 − 12 = 19 nm from the nominal exit.

### 13.3.2 The Tail Model

The distribution of the exit width has a Gaussian core (σ = 0.72 nm, Chapter 4) that cannot reach 19 nm. The tail comes from rare local events: a local failure of the passivation, a flake of wall film that lands in the hole and nucleates a plug, a volume of the wall where the film grows by runaway (more film, fewer ions, more film). Model them as an exponential tail on the narrowing δ:

```
P(narrowing > δ) = P₀ exp(−δ/Δ₀)       P₀ = 10⁻³ (fraction of holes with a runaway nucleus)
Closure rate  p = P₀ exp(−δ_c/Δ₀)       δ_c = 19 nm

  M1:  p = 0.7 × 10⁻⁹  →  Δ₀ = 19 / ln(10⁻³/0.7 × 10⁻⁹) = 1.34 nm
  M0:  p = 1.5 × 10⁻⁹  →  Δ₀ = 1.42 nm
```

M0's tail scale is only 6% larger than M1's, and its closure rate is 2.1 times higher. The closure rate is the exponential of a ratio of 14, and **every percent in the scale is a factor in the rate**:

```
Sensitivity of the closure rate to the tail scale Δ₀ (M1):
  d ln p / d Δ₀ = δ_c / Δ₀² = 19 / 1.34² = 10.6 per nm
  Δ₀ × 0.90   p × 0.21        Δ₀ × 0.95   p × 0.47        Δ₀ × 1.05   p × 2.0        Δ₀ × 1.10   p × 3.6
  A 4.9% reduction in Δ₀ halves the closure rate (0.7 → 0.35 × 10⁻⁹).
```

What sets Δ₀ is the roughness of the wall's film: the more uniform its coverage, the smaller the tail. It falls with the factors that raised the coverage (temperature, COS; Chapter 6), with the cleanliness of the wall (Chapter 9), and with the smoothing step (Chapter 7); it rises with the age of the chamber. The relation is not computed here; its logarithmic leverage is what matters.

---

## 13.4 Micromasks and Footing

The micromask, described in Chapter 9, is a speck of involatile material on the foot of the tube. Its rate of 0.5 × 10⁻⁹ per hole is a count of rare arrivals: the cap-sourced oxide reaches the exit at 1.8 × 10⁻¹⁰ of its top flux. Three conditions have to coincide for a micromask to block a hole:

```
Conditions for a micromask defect:
  1. A nucleus arrives at the foot.            rate set by the silicon supply at the top (cap erosion, electrode wear)
  2. It is not removed by the ions of the OE.  ST3a: 11 s at 600 eV clears all but the largest
  3. It is large enough to shade the carbon.   ≥ 40% of the exit area (≥ 300 nm²)
Controls:  the silicon supply (a 10% lower cap erosion lowers the rate by about 10%, Chapter 9);
           the OE-clear time (each second removes a fixed depth, 8 nm of carbon at the exit rate);
           the electrode age (Chapter 5): a worn electrode sputters less silicon but exposes more oxide.
```

The footing, in contrast, is not rare. The foot is 0.6 nm per side in every hole (Chapter 10), well below any harmful size. A footing defect is a foot of more than 3 nm, a hole in which the redeposition ran away but not as far as closure. It adds about 20% to the micromask line and is counted with it.

---

## 13.5 Merged Holes

The web between two holes is 12.2 nm at the bow, with a margin to merging of 17σ on Gaussian statistics (Chapter 4). It merges at 2 × 10⁻¹⁰ per hole in M1 and twice that in M0, because the tails are not Gaussian: a printed-large opening, a hole whose passivation failed locally so that it bowed by several nanometres, a pair of holes displaced toward each other. The merged pair is cut in the mold as a slot, which short-circuits two capacitors. Of the budget's seven lines this has the highest cost per event (a short, not an open) and the smallest rate.

---

## 13.6 What a Defect Becomes

The capacitor etch amplifies the defects of the open, with the gains of Books #29 and #31:

```
Defect of the open                     What the capacitor etch makes of it                          Consequence
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Blocked or closed opening              no hole: not-open from the start                             dead cell
Pinch-off (exit < 12 nm)               the hole starts and stalls, or never reaches the pad          dead cell, possibly partial
Narrow exit (CD deficit δ)             depth lag 15.2 nm per nm: 1 nm → 15 nm; 3 nm → 46 nm         inside the 29 s overetch of Book #29
                                                                                                    (183 nm; covers well beyond 4σ)
Merged pair                            a slot: two electrodes in one                                short
Micromask                              as pinch-off                                                  dead cell
Displaced exit (beyond 1.5 nm)         a hole that misses part of its pad                           weak or open cell
Oversize exit                          wide top; a thin wall                                         low yield tail (bridging)
```

A hole whose exit is 3 nm narrow, a 4σ event at σ = 0.72 nm, lags by 46 nm in the capacitor etch, 7 s at its bottom rate of about 6 nm/s, which the 29 s overetch of Book #29 covers. A hole whose exit is 19 nm narrow, which is a closure, lags by 290 nm: nothing covers it.

---

## 13.7 Detection

```
Detection of the defects of the open:
  Method                               What it sees                                  Area / sample             Delay
  ──────────────────────────────────────────────────────────────────────────────────────────────────────────────
  Optical / e-beam at the cap          missing and blocked cap openings (before the   0.17 cm² for 30 events    minutes
                                       open, §13.2)                                   (1 per 0.0058 cm²)
  HV-SEM (30–50 keV) after the open    holes whose exit is closed (no through-hole    same                      minutes–hours
                                       contrast)
  XTEM / FIB cross-sections            profile, foot, micromasks (a few holes)        10–100 holes              hours
  Not-open map after the mold etch     blind holes (voltage contrast, at the stop)    whole die                 hours–days
  Electrical test (bitmap)             dead cells by class                            all                       weeks–months
```

The rates of Section 13.1 are far below what a cross-section can see (one defect per 1.4 × 10⁹ holes for the pinch-off line, 0.025 cm² per event), and the one method that can see them in time to act on them is large-area HV-SEM, an inspection of tenths of a square centimetre of array per wafer at tens of seconds per field. Chapter 15 sizes the inspection and sets its sampling plan.

---

## 13.8 Where to Spend Effort

The leverage of each control on its defect line:

```
Leverage on the defect rate (M1, from the models above):
  Control                                    Change                       Effect on the budget
  ──────────────────────────────────────────────────────────────────────────────────────────────────
  Tail scale Δ₀ of the narrowing             −5%                          pinch-off ÷ 2:     −0.35 × 10⁻⁹
  SiON overetch                              +2 s (2 → 4 s)               cap-open residue × 0.37:  −0.28 × 10⁻⁹; CD +0.2 nm
  Litho partial-open rate                    −50%                         blocked and residue −50%: −0.7 × 10⁻⁹
  Silicon supply (cap erosion)               −10%                         micromask −10%:     −0.05 × 10⁻⁹
  Web at the bow                             +1 nm (via the bow)          merging × ~0.3:     −0.14 × 10⁻⁹
  Particles ≥ 30 nm                          10 → 5 per wafer             −3 × 10⁻¹³: negligible
```

The three largest are the **lithography's** rate (a specification on a different tool), the **tail scale** of the narrowing (a logarithmic lever), and the **overetch** of the cap open. The ranking is not what a cost-of-defects intuition would give: the many particles and the single-event spectacular failures of the chamber are the smallest lines, and the largest are the rates of events that look like noise.

---

## Summary and Key Takeaways

1. **The litho-origin defects are populations that the SiON overetch thins.** 79% organic scum is cleared by the oxygen; 9% stays blocked (0.9 × 10⁻⁹); 12% are inorganic plugs, cleared at exp(−0.5 t) per second (0.44 × 10⁻⁹ after 2 s).

2. **EUV needs a litho specification and a longer overetch.** 5 × 10⁻⁸ partial opens give 6.7 × 10⁻⁹; 2 × 10⁻⁸ with 4 s of overetch gives 1.0 × 10⁻⁹.

3. **Closure is a tail event.** A hole stops when its exit is below 12 nm (ion transmission 0.145); with an exponential tail scale of 1.34 nm the rate is 0.7 × 10⁻⁹.

4. **A 5% change in the tail scale is a factor of 2.** d ln p/dΔ₀ = 10.6 per nm; M0's tail is 6% larger and its rate 2.1 times higher.

5. **The micromask is a count of rare arrivals.** The silicon supply and the OE-clear time are the controls; the footing is a small addition.

6. **Merging is the Gaussian margin plus a tail.** 17σ on the Gaussian; 2 × 10⁻¹⁰ in practice; a short, not an open.

7. **The largest levers sit in exponents or on another tool.** The litho rate, the tail scale, and the cap overetch; particles are negligible.

---

## Study Questions

1. A SADP×2 flow has a partial-open rate of 1.5 × 10⁻⁸ per hole with the same organic/inorganic split. Find the blocked and plug lines for a 2 s and a 3 s SiON overetch, and the total litho-origin rate.

2. Compute the ion transmission for an exit width of 14 nm (σ_θ = 0.91°, h = 1350 nm). What narrowing from the nominal 31 nm does this correspond to, and what is the closure rate if the critical width is 14 nm and Δ₀ stays at 1.34 nm?

3. With P₀ = 10⁻³ and δ_c = 19 nm find the tail scale Δ₀ that gives a closure rate of 0.2 × 10⁻⁹. By how much does it differ from M1's 1.34 nm?

4. A pinch-off event rate of 0.7 × 10⁻⁹ is to be measured to ±30% (1σ). How many events must be seen, how many holes, and what area of array?

5. A hole is 3.5 nm narrower than nominal. Find its depth lag in the capacitor etch (15.2 nm per nm) and say whether the 29 s overetch of Book #29 covers it, if the bottom rate in BPSG is 6 nm/s.

6. The micromask rate is proportional to the silicon supply, which is proportional to the cap's erosion rate. A cap of 42 nm (M1-c) has the same erosion rate as one of 40 nm. What is the change in the micromask rate, and what changes instead (Chapter 11)?

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Boron-Doped Carbon, Taller Masks, Metal-Containing Masks, Hybrid Caps & 4F² / 3D DRAM](./14-advanced-mask-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
