# Chapter 9: Walls, Residue, Particles & the Post-Open Hold

## Overview

When the open is over, the wafer carries two square metres of carbon wall, and the chamber carries a few nanometres of silicon oxide more than it did. Both are products of the same process, and both have to be managed before the next wafer arrives. The chamber's walls grow a film that must be removed before it flakes. The hole's walls carry sulfur, silicon oxide, and adsorbed water that must not travel to the next chamber. The floor of each hole, at the foot of a 44:1 tube, may carry a speck of residue that blocks it. And between the open and the capacitor etch the wafer waits, and in its waiting takes up a few tenths of a milligram of water.

This chapter treats these in order: the growth of films on the chamber walls and the cadence of the cleans that remove them, the particles that the films and the handling produce and the footprint of each on a hexagonal array, the residues of the open and where they form, the reason the mask is never wet-cleaned, and the post-open hold: the moisture the wall takes up, the queue time that limits it, and the degas that removes it.

**Learning Objectives:**
- Estimate the film growth on the chamber walls per wafer, and set the clean interval from the particle limit
- Compute the number of holes a particle of a given size blocks, and the critical size for a cluster of three
- Convert a particle adder specification into a yield loss per die
- List the residues of the open, their origin, and their detection and removal
- Explain with numbers why a wet clean is not used after the open
- Estimate the moisture uptake of the carbon wall and set the queue time and the degas

---

## 9.1 The Chamber Walls

### 9.1.1 What Grows

Each wafer leaves a film on the walls of the chamber. Its composition follows the sources of the open:

```
Film growth on the chamber walls per wafer (M1, 8000 cm² of wall; illustrative):
  Source                              Released per wafer              Deposits on the walls         Growth per wafer
  ──────────────────────────────────────────────────────────────────────────────────────────────────────────────
  SiON cap (38.5 nm on 590 cm²)       1.6 × 10²⁰ atoms (Si, O, N)     60%                           1.9 nm SiOₓ
  Redeposited carbon (1.5% of the     2.1 × 10¹⁹ atoms                100%                          0.3 nm C-rich
   21.6 sccm removed)
  Sulfur (5% of the 3.6 mmol COS)     1.1 × 10²⁰ atoms                100%                          9 nm S–C (loosely bound)
```

The silicon oxide is the film that accumulates. The carbon-rich film is removed every wafer by the 14 s O₂/Ar waferless clean. The sulfur film is thick, soft, and also removed by the oxygen of that clean (as SO₂). What is left on the walls is silicon oxide, which oxygen does not remove:

```
SiOₓ on the walls between NF₃ cleans:
  Wafers since the NF₃ clean    0     10     25     50     75
  SiOₓ thickness (nm)           0     19     46     93     140
```

### 9.1.2 The Particle Limit and the Clean Interval

A film on the wall carries stress, and it flakes when it is thick. The flakes are particles. The adders per wafer rise steeply with the thickness:

```
Particle adders (≥ 30 nm) per wafer versus the SiOₓ film on the walls (illustrative):
  Film (nm)          20     50     100    150    200
  Adders per wafer   1.5    2.5    5      12     45
  Specification      ≤ 10 per wafer  →  film ≤ 140 nm
```

The specification of 10 adders per wafer is met up to about 140 nm. The reference interval of 25 wafers (46 nm, 2.5 adders) is chosen not by the particles, which would allow 75 wafers, but by the first-wafer effect of Chapter 5: the NF₃ clean resets the wall's memory, and a longer interval would defer the loss. The particle limit leaves a factor of three in reserve against a missed clean.

```
Cleans (M1):
  Every wafer       waferless O₂/Ar, 14 s          removes the carbon film and the sulfur film
  Every 25 wafers   NF₃ clean, 60 s; season 12 s   removes SiOₓ; resets the wall; season rebuilds the sulfur
  Every 4,070       edge ring replaced (tilt)
  Every 29,300      upper electrode replaced
  PM (wet)          at the electrode change; all parts and liners
```

---

## 9.2 Particles

### 9.2.1 Sources

```
Particle sources (M1, adders ≥ 30 nm per wafer; illustrative):
  Wall film flaking (46 nm, end of interval)  2.5
  Edge ring and electrode (wear)            1.5
  Wafer handling and ESC backside           1.0
  Elemental sulfur flakes (gas lines, foreline)   1.0
  Gas, pump, and other                      0.5
  ───────────────────────────────────────────────
  Total                                     6.5       (specification ≤ 10)
```

Sulfur is the unusual source. COS decomposes on warm surfaces and leaves elemental sulfur on gas lines and in the foreline, and a flake from the gas panel can reach the wafer. The foreline is heated to 120 °C, above the melting point of sulfur (115 °C), so that it reaches the scrubber as a liquid and a vapour and not as flakes, and the gas lines are purged with nitrogen after the last wafer of a lot.

### 9.2.2 The Footprint of a Particle

A particle on the cap shields the holes beneath it from the plasma, and a hole that is shadowed is not opened. On the hexagonal array each hole occupies 1734 nm²; a particle of diameter D shadows about πD²/(4 × 1734) holes:

```
Holes shadowed by a particle of diameter D (hexagonal array, 1734 nm² per hole):
  D (nm)           30     45     60     80     100    200
  Holes shadowed   0.41   0.92   1.6    2.9    4.5    18
  Critical size for a cluster of three adjacent holes:  D = √(3 × 4 × 1734 / π) = 81 nm
```

An isolated dead hole is a failing bit and is repaired. A cluster of three or more is a different failure: a **killer** that redundancy may not absorb. The critical size is 81 nm, and the specification is written on that size:

```
Particle specification and its yield cost:
  Adders ≥ 30 nm                           ≤ 10 per wafer     → ≤ 10 × 1 hole = 10 isolated dead holes per wafer
                                                              (a rate of 6 × 10⁻¹³ per hole)
  Adders ≥ 80 nm (killers)                 ≤ 0.5 per wafer
  Array area per wafer                     0.298 cm² × 900 = 268 cm²
  Killer density                           0.5 / 268 = 1.9 × 10⁻³ cm⁻²
  Yield loss per die                       1 − exp(−1.9 × 10⁻³ × 0.298) = 0.056%
```

The isolated dead holes contribute 6 × 10⁻¹³ per hole, a part in 5000 of the 3 × 10⁻⁹ budget of Chapter 4: the particles that matter are the large ones, not the many small ones.

---

## 9.3 Residues

### 9.3.1 What Is Left, and Where

```
Residues of the carbon open (M1; illustrative):

  Residue          Where                  Origin                         Removal / control
  ────────────────────────────────────────────────────────────────────────────────────────────────────────
  Polymer (CFₓ)    exit and walls from    ST1 (CF₄/CHF₃ plasma)          removed by the first 2–3 s of the main
                   the cap open                                           etch (O₂); only a closure risk if the
                                                                          main etch starts with the oxygen low
  Cap remnant      web top                1.5 nm of SiON on the flat     left; consumed in the capacitor etch
  SiOₓ crowns      cap corners            redeposited cap material       controlled by the cap's life; not an
                                                                          issue after the cap fails
  Sulfur           walls, 0.4 ML at the   COS passivation                degas (Section 9.5); fluorocarbon plasma
                   bow zone, 0.1 ML at                                    of the capacitor etch
                   the exit
  Carbon footing   foot at the exit,      redeposition of carbon-rich    OE-clear and the smoothing step; ion
                   0.6 nm per side        fragments                      flux at the exit (Chapter 6)
  SiOₓ micromasks  exit floor             Si-bearing species that reach  low Si supply at the exit (reach 10⁻¹⁰
                                          the foot of the tube           of the top flux); 0.5 × 10⁻⁹ per hole
  Moisture         all walls              queue and handling             hold ≤ 4 h and degas (Section 9.5)
```

### 9.3.2 The Micromask

The residue that fills the budget of Chapter 4 is the micromask: a speck of involatile material, typically silicon oxide, that stays on the floor of a hole and shades the carbon beneath it, so that the etch leaves a stub or a pillar. The cap-sourced silicon oxide, which provides the top of the hole with its passivation, has a reach of ℓ_c = 60 nm, so that its flux at the exit of the 1350 nm tube is e^(−1350/60) = 1.8 × 10⁻¹⁰ of its flux at the top. Almost none of it arrives. **The micromask rate of 0.5 × 10⁻⁹ per hole is a count of rare events at the very bottom of the tube, and it scales with the silicon supply at the top**: more cap erosion, or a worn silicon electrode that sputters more, raises the supply and with it the tail. The control is on the supply (Chapter 5, electrode age) and on the clear that removes what has arrived (ST3a, 11 s, ions at 600 eV).

---

## 9.4 Why the Mask Is Not Wet-Cleaned

A post-etch wet clean (an aqueous rinse, or an SC1 clean) is standard after many etches. It is not used after the carbon open, for four reasons that can be put in numbers:

```
1. The walls are hydrophobic and the water does not enter.
   Contact angle of water on ACL (as deposited)         95°     (S–C passivated wall: 100°)
   Laplace pressure p = 4γ cos θ / d, γ = 0.072 N/m, d = 31 nm (positive draws the water in):
     θ = 95°     p = −0.8 MPa  (opposes entry: the water stays out of the hole)
     θ = 45°     p = +6.6 MPa  (draws the water in)
   Oxygen plasma oxidizes the carbon surface and lowers θ to about 45°, so a surface that has seen the
   open could be drawn in; the sulfur film restores the hydrophobicity. Which one a given wall is
   cannot be controlled at the level of 17 billion holes.

2. A wetted hole cannot be dried.
   Hole volume    π (15.5 nm)² × 1350 nm = 1.0 × 10⁻¹⁵ cm³
   Per wafer      1.0 × 10⁻¹⁵ × 1.55 × 10¹³ = 0.016 cm³ = 16 mg of water if every hole filled
   Monolayer on the 2.03 m² of wall: 10¹⁵ cm⁻² × 2.03 × 10⁴ cm² = 2.0 × 10¹⁹ molecules = 0.6 mg
   The filled holes hold 26 times the monolayer, and the capillary pressure of 6.6 MPa holds them in.

3. The web does not collapse, but nothing is gained.
   Plate bending stress of a 14 nm web with a span of 26 nm under 6.6 MPa:
     σ = ¾ p (L/t)² = 0.75 × 6.6 MPa × (26/14)² = 17 MPa, far below the strength of carbon
   The web is safe because its spans are short. A wet clean is not rejected for fear of collapse.

4. Water on the walls is carried into the next chamber.
   The wafer enters the capacitor etch within hours. Water and the hydrogen it brings change the
   polymer balance of the first seconds (Book #29, Chapter 9).
```

The open is followed by a dry degas, not a wet clean. What the walls carry that matters, sulfur and water, is volatile or removable by the plasma of the capacitor etch, and what the floor carries that matters, a micromask, is removed by the ST3a clear before the wafer leaves.

---

## 9.5 The Post-Open Hold

### 9.5.1 Moisture Uptake

The carbon wall is hydrophobic, and it takes up water slowly. A model of the adsorbed coverage θ_w(t) = 0.9 (1 − e^(−t/τ)), with τ = 8 h in cleanroom air at 45% relative humidity, gives:

```
Moisture on the wall after the open (illustrative):
  Hold (h)                    1      4      8      12     24
  Coverage (monolayers)       0.11   0.35   0.57   0.70   0.86
  Water on the wafer (mg)     0.06   0.21   0.35   0.42   0.52
  In a nitrogen-purged FOUP
   (τ × 5)                    0.02   0.09   0.16   0.23   0.41
```

The 0.2 mg that a wafer carries after four hours is small, but it is released all at once, in the first seconds of the capacitor etch, when it meets a plasma that has been seasoned with a dry polymer, and in the pump-down, where it sets the time to base pressure. The queue limit is set at **4 hours** in air.

### 9.5.2 The Degas

```
Post-open hold and degas (M1):
  Queue, open → capacitor etch               ≤ 4 h in air;  ≤ 12 h in a nitrogen-purged FOUP
  Load-lock degas (N₂, 150 °C, 30 s)         removes 90% of the adsorbed water and part of the sulfur
  Moisture after degas (4 h hold)            0.02 mg
  Sulfur at the exit after degas             ≤ 10¹⁴ cm⁻² (unchanged: sulfur is bound)
```

The degas is a hot plate in the load lock of the capacitor etch tool, not part of the open. It costs 30 s of a load lock's time, which is not on the critical path.

---

## Summary and Key Takeaways

1. **The silicon oxide is the film that accumulates.** 1.9 nm per wafer, 46 nm in 25 wafers; the carbon and sulfur films are removed by the 14 s oxygen clean. Particles stay within 10 per wafer up to 140 nm.

2. **The clean interval is set by the first wafer, not the particles.** The NF₃ clean every 25 wafers is chosen for the memory of the wall; the particle limit would allow 75.

3. **A particle of 81 nm kills a cluster.** The footprint is πD²/(4 × 1734) holes; the killer specification is ≤ 0.5 adders ≥ 80 nm per wafer, a yield loss of 0.056% per die.

4. **The large particles matter, not the many small ones.** 10 small adders are 6 × 10⁻¹³ per hole, a five-thousandth of the defect budget.

5. **The micromask is a count of rare events.** At the exit the cap-sourced silicon oxide arrives at 1.8 × 10⁻¹⁰ of its top flux; the budget of 0.5 × 10⁻⁹ per hole scales with the silicon supply.

6. **There is no wet clean.** The wall is hydrophobic (95°), a wetted hole holds 26 monolayers of water at 6.6 MPa, and the carried water spoils the next chamber; the web would survive (17 MPa) but nothing would be gained.

7. **The hold is limited to four hours.** The wall takes up 0.2 mg of water in four hours; a 150 °C, 30 s degas in the load lock removes 90%.

---

## Study Questions

1. A product has a die with 1.5 times the array area of the reference. Find the killer particle density that gives the same yield loss per die (0.056%) and the number of ≥ 80 nm adders per wafer that is allowed if the dies per wafer fall to 600.

2. The NF₃ clean interval is extended from 25 to 60 wafers. Find the SiOₓ thickness at the end of the interval and the particle adders from the table, and decide whether the specification is met.

3. A particle of 150 nm sits on the cap. Find the number of holes it shadows, and whether it is a killer. If it lifts off during the open after 20 s, what fraction of those holes have opened by the end of the main etch?

4. Using the Laplace pressure at θ = 60° and d = 31 nm, find the pressure that draws water into the hole. Why does the sign change at 90°?

5. Compute the water on the wafer after 6 h in air and after 6 h in a nitrogen-purged FOUP (τ = 8 h and 40 h). Which is within a limit of 0.25 mg?

6. The cap erosion falls 10% (a thicker, more uniform cap). Estimate the change in the SiOₓ growth per wafer and in the micromask rate, assuming the micromask rate is proportional to the silicon supply.

---

**Next Chapter:** [Chapter 10: Mask Profile, CD Budget & Uniformity](./10-profile-cd-budget-uniformity.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
