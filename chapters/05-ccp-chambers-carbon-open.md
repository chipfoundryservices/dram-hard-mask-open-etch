# Chapter 5: CCP Chambers for the Carbon Open

## Overview

A chamber for the carbon open is judged by three things that most etch chambers do not have to hold: a **passivant supply** that has to be steady from wafer to wafer, a **bias that can be pulsed** with clean edges, and a **wafer temperature** that sets the lateral rate of oxygen on carbon at 6% per kelvin. The chamber is a conventional dual-frequency capacitively coupled reactor, a 60 MHz source on the upper electrode and a 2 MHz bias on the lower, much like the one that cuts the mold in Book #29. What differs is what its walls, its silicon parts, and its gas panel are asked to do. The walls store sulfur and silicon oxide that the wafer will need on its next visit. The silicon ring that is a focus ring in an oxide chamber is also a passivant source and the tilt of the wafer edge. The gas panel carries carbonyl sulfide, which is toxic and flammable, and the exhaust carries 2600 ppm of carbon monoxide.

This chapter describes the chamber as the carbon open uses it: the requirements the three steps add, the sheath and the ion transit that fix the choice of frequency, the angular spread of the ions that reach a 44:1 tube, the chamber's memory of the previous wafer and the first-wafer bow it produces, the full M1 recipe, the consumables that wear and the tilt that wears with them, the temperature control, and the throughput, matching, and exhaust.

**Learning Objectives:**
- List the requirements the carbon open places on the chamber, step by step
- Compute the sheath, the ion transit time, and the transit ratio for a given frequency
- Estimate the angular spread of ions at 600 eV and why it does not limit the open
- Explain the first-wafer effect and quantify the benefit of a season step
- Read the full M1 recipe and the role of each step
- Relate edge-ring wear to ion tilt and to the placement budget
- Compute wafer heating and the sensitivity of the lateral rate to temperature
- Compute per-chamber time, platform throughput, and the exhaust load of COS and CO

---

## 5.1 Requirements the Carbon Open Adds

```
Hard mask open, chamber requirements (reference; M1):

                        SiON open (ST1)      Main etch (ST2)         OE-clear / OE-smooth (ST3)
  Ion energy            400 eV, CW           600 eV, 5 kHz, 70%      600 eV, 5 kHz, 70% / ≈ 500 eV at 25 mTorr
  Gas switching in/out  ≥ 2 s settle         once, then steady        ≤ 1 s between ST3a and ST3b
  Wafer temperature     ± 2 K                ± 1 K                    ± 1 K (ESC set-point stepped into ST3b)
  Process variable      cap CD, resist       passivant coverage       CD change ≤ 0.1 nm in ST3b
  Wall state            non-critical         memory of S and SiOₓ     as ST2
  Uniformity driver     CD ± 0.4 nm          rate ± 2.5% (3σ)         clear time at the edge
```

Four requirements go beyond those of a conventional chamber:

1. **A steady passivant supply.** The bow is proportional to x₀, the ratio of passivant removal to supply (Chapter 3). A 20% change in the supply is a 0.14 nm change in the bow. The chamber has to hold the COS flow, the silicon source, and the wall state to a few percent.
2. **A pulsed bias with sharp edges.** A 5 kHz, 70% pulse has an off-time of 60 µs. The bias must turn off in a few microseconds and the plasma must follow it down.
3. **Temperature within 1 K.** The lateral rate of the bare wall moves 6.1% per kelvin (Chapter 3). A 3 K error moves it 18%, and the bow by 0.12 nm.
4. **A chamber state that survives a clean.** The first wafer after a clean sees a different wall (Section 5.3).

---

## 5.2 Sheath, Ion Transit & the Choice of Frequency

### 5.2.1 Why Two Frequencies

```
Plasma and sheath (illustrative, O₂-dominated, 12 mTorr, M1 at 1.5 kW source):
  Electron temperature             T_e = 3 eV
  Ion density                      n_i = 2 × 10¹¹ cm⁻³
  Debye length                     λ_D = 7430 √(T_e/n) m = 29 µm
  Sheath thickness at 600 V        s ≈ 1.2 λ_D (2V/T_e)^¾ = 3.1 mm
  Ion transit time (O₂⁺)           τ_i = 3 s √(m/(2eV)) = 154 ns
```

The ratio of the ion transit time to the RF period decides how the ions respond:

```
Frequency    Period    τ_i/τ_RF    Ion response               IEDF (at 600 eV mean)
60 MHz       16.7 ns   9.2         ions see the mean field    narrow; source only
13.56 MHz    73.7 ns   2.1         ions see the mean field    narrow, but couples to the source
2 MHz        500 ns    0.31        partly follow the field    bimodal, ± 30%
400 kHz      2.5 µs    0.062       follow the field           very broad
```

A 60 MHz source makes density with little ion energy; a 2 MHz bias delivers energy with a bimodal distribution of ± 30%. Thirteen megahertz would give a narrower distribution, but it couples to the source and removes the independence of ion flux from energy that the pulsing relies on. The reference keeps the 60/2 MHz pair of the capacitor etch chamber, which has the practical benefit that the mask-open chamber and the mold-etch chamber are the same hardware with different gases and consumables, and match each other's tilt more easily (Chapter 4).

### 5.2.2 Ion Angle and a 44:1 Tube

```
Angular spread of the ions at the wafer (T_i = 0.15 eV):   σ_θ = √(T_i/E)
  E = 390 eV (low side of the IEDF)    σ_θ = 1.12°
  E = 600 eV (mean)                    σ_θ = 0.91°
  E = 810 eV (high side)               σ_θ = 0.78°
Geometric acceptance of the tube       atan(d/L) = atan(31/1350) = 1.3°  (edge to opposite edge)
```

The angular spread is about the same as the acceptance. Without the forward reflection of grazing ions from the wall (Chapter 3) only a fraction of the ions would reach the exit, and the etch would be limited by the ion flux at depth, not by the oxygen. With it, the transmission is about 0.70. The distribution matters less than its **centre**: an edge tilt of 0.05° is small against a spread of 0.9°, but it moves the exit by 1.2 nm, and it is the mean direction, not the width, that enters the placement budget.

### 5.2.3 Pulsing

```
Bias pulse (M1):   5 kHz  (period 200 µs),  duty 70%  (on 140 µs, off 60 µs)
  On-phase           600 eV mean ion energy, 2.7 kW bias (1.9 kW time-averaged)
  Off-phase          ion flux decays within ≈ 20 µs; the film grows with little bombardment
  Ion flux (on)      2.2 × 10¹⁶ cm⁻² s⁻¹  (3.5 mA/cm²) at a 1.5 kW source, against 1.5 × 10¹⁶ at 1.0 kW (M0)
  Time-averaged ER₀  730 nm/min  (M0, CW: 830)
```

Pulsing does two things. It lowers the ion bombardment of the sidewall during the off-time, when the passivant arrives without being sputtered, and it reduces the removal term x₀. And it costs rate: the open is 5.3 s longer than M0's in the main etch even with the extra source power. Chapter 6 gives the trade quantitatively.

---

## 5.3 Chamber Memory: The Walls as a Passivant Source

### 5.3.1 What the Walls Hold

Every wafer leaves a film on the chamber walls: sulfur and carbon from the COS, silicon oxide from the SiON cap and from the silicon parts. The film is thick (tens of nanometres after a few dozen wafers) and it is in contact with the plasma, so the wall exchanges species with it. A fresh wall absorbs passivant that would otherwise reach the wafer. A seasoned wall returns what it has stored.

```
Wafer cycle (M1):
  every wafer:   waferless clean (O₂/Ar, 14 s, cover wafer)
  every 25:      NF₃ clean (60 s) to remove the SiOₓ build-up, then a season step
  season:        COS/O₂-rich, 12 s, with a cover wafer
```

### 5.3.2 The First-Wafer Effect

The bow is proportional to x₀ (Chapter 3), and x₀ is higher on a wall with no memory. After the NF₃ clean the wall holds no sulfur and no oxide, and the first wafer has to build the film as it goes:

```
First-wafer effect on the bow (M1; x₀(n) = x₀ [1 + a e^(−n/2.5)], n = wafers since the NF₃ clean):

  Wafer n                 0      1      2      3      5      8
  Without season (a = 1.00)
    x₀ factor             2.00   1.67   1.45   1.30   1.14   1.04
    Bow (nm)              1.34   1.12   0.97   0.87   0.76   0.70
  With 12 s season (a = 0.15)
    x₀ factor             1.15   1.10   1.07   1.05   1.02   1.01
    Bow (nm)              0.77   0.74   0.72   0.70   0.68   0.67
```

Without a season the first two wafers fail the 1.0 nm specification and the bow takes eight wafers to settle. With the season only the first wafer is a little worse. The season costs 12 s of chamber time every 25 wafers (0.5 s per wafer, 0.2%); the three wafers it saves are worth far more. **The first wafer is the process variable of the NF₃ clean.**

### 5.3.3 The Silicon Parts

The silicon upper electrode and the silicon edge ring sputter slowly in the oxygen plasma and oxidize at once; the oxide that they release is part of the passivant supply of the middle of the hole (Chapter 3), and when they wear the supply falls:

```
Effect of upper-electrode age on the bow (illustrative):
  RF-hours of the electrode      0       500     1000    1500 (end of life)
  x₀ factor                      0.95    1.00    1.06    1.14
  Bow (nm)                       0.64    0.67    0.71    0.76
```

The bow stays inside the specification through the electrode's life. What fails first is not the bow but the matching of tilt (Section 5.5), and the cap selectivity (the silicon source is also a minor part of the chemical term).

---

## 5.4 The Full M1 Recipe

```
M1 (reference), 300 mm dual-frequency CCP, 60 MHz source / 2 MHz bias
                ST1: SiON open     ST2: ACL main etch    ST3a: OE-clear     ST3b: OE-smooth
Time            22 s               144 s (to endpoint)   11 s               7 s
Pressure        20 mTorr           12 mTorr              12 mTorr           25 mTorr
Source (60 MHz) 1.2 kW             1.5 kW                1.5 kW             1.0 kW
Bias (2 MHz)    CW, 400 eV         5 kHz, 70%, 600 eV    5 kHz, 70%, 600 eV 5 kHz, 70%, 600 V set-point
                                                                            (≈ 500 eV at 25 mTorr)
Gas (sccm)      CF₄ 80 / CHF₃ 20  O₂ 150 / COS 30 /      O₂ 150 / COS 20 /  O₂ 200 / COS 8 /
                / Ar 300           N₂ 60 / Ar 300        N₂ 60 / Ar 300     N₂ 30 / Ar 300
Wafer           4 °C (ESC −14)     10 °C (ESC −14)       10 °C (ESC −14)    10 °C (ESC −3)
ER (top)        BARC 190 nm/min,   730 nm/min            730 nm/min         ≈ 650 nm/min
                SiON 200 nm/min
Endpoint        time               CO emission falls     time               time
                                                         (11 s after EP)
Total           22 + 144 + 11 + 7 = 184 s

M0 (baseline):
  ST1 22 s (as above) | ST2 139 s: O₂ 180 / COS 6 / N₂ 60 / Ar 300, 12 mTorr, 1.0 kW,
  CW bias 800 eV (2.4 kW), 20 °C | ST3 20 s: same gases and bias         = 181 s
```

ST3a is the main etch continued at the same bias with a lower COS flow: the overetch cannot be run at low energy, because at 250 eV the ion transmission of a 44:1 tube falls to half and the 85 nm that Chapter 8 requires to be cleared would take 33 s. ST3b, the smoothing step, is balanced: at 25 mTorr and about 500 eV with 8 sccm of COS the passivant deposits in the concave parts of the rough wall and the oxygen removes it from the convex parts. It changes the CD by less than 0.1 nm and the edge roughness by 0.55 nm (Chapter 4). It is the only step that is run for the roughness and nothing else.

---

## 5.5 Consumables, Edge Ring & Ion Tilt

### 5.5.1 What Wears

```
Consumables (M1, illustrative):
                          Cost      Life                    Per wafer
  Edge ring (Si)          $1,500    4,070 wafers (208 RF-h) $0.37     limit: tilt
  Upper electrode (Si)    $12,000   29,300 wafers (1500 RF-h) $0.41   limit: x₀ and particles
  Cover ring, liners,
   gas plate, other       —         —                       $0.27
  Parts total                                               $1.05
```

(RF-hours per wafer: 184.4 s / 3600 = 0.0512.)

### 5.5.2 Edge Ring and Ion Tilt

At the edge of the wafer the sheath bends over the step between the wafer and the ring. When the ring wears the step grows and the ions arrive tilted, 0.08° for every 100 µm of wear (Book #31). Over the 1350 nm of the mask the tilt moves the exit:

```
Tilt at r = 147 mm and the shift over the mask (1350 nm):
  θ        0.02°    0.03° (new ring)   0.05° (limit)   0.07°    0.10°
  shift    0.5 nm   0.7 nm             1.2 nm          1.6 nm   2.4 nm

Ring wear and tilt (0.08° per 100 µm):
  Wear     0 µm     12 µm    25 µm    40 µm
  Tilt     0.03°    0.04°    0.05°    0.06°
  Wafers   0        2,000    4,070    6,500
```

A new ring starts at 0.03°. It reaches the limit of 0.05° at 25 µm of wear, at 4,070 wafers, and is replaced there. The ring's life is **set by the tilt budget, not by a visible fault**: a ring that looks fine at 6,500 wafers has moved the exit 0.3 nm further than the budget allows, and the mold etch has its own 0.8 nm to add (Chapter 4).

---

## 5.6 Temperature Control

```
Wafer temperature budget (illustrative, M1 main etch):
  Ion heating               2.5 A × 600 V × 0.70 duty = 1.04 kW
  With recombination, radiation (+15%)    1.2 kW → 1.7 W/cm² on the 707 cm² wafer
  Backside He conductance   0.07 W cm⁻² K⁻¹ (15 Torr)
  Temperature rise          1.7 / 0.07 = 24 K
  ESC setpoint              −14 °C  →  wafer 10 °C, ± 1 K
  Wafer thermal time constant   90 J/K / (0.07 × 707 W/K) = 1.8 s
  OE-clear                      as the main etch (ESC −14 °C)
  OE-smooth (≈ 500 eV, 1.0 kW source)   0.66 kW → rise 13 K; the ESC is stepped to −3 °C to hold 10 °C
  SiON open (400 eV, CW)        0.91 kW → rise 18 K → wafer 4 °C
```

Plasma heating is the larger part of the wafer's temperature, so the wafer is cold at the start of each step and warms in about two seconds; every ACL step holds the wafer at 10 ± 1 K, with a step of the ESC set-point into the smoothing step, because the bare lateral rate moves 6.1% per kelvin and a step that ran 13 K cold or hot would change the film it is smoothing.

```
Sensitivities to wafer temperature (M1):
  Bare lateral rate γ_C    +6.1% per K       (E_a = 0.42 eV at 283 K)
  Bow                      +0.04 nm per K    (proportional to γ_C)
  ER₀                      +0.3% per K       (weakly activated; the term is ion-driven)
  Uniformity requirement   ± 1 K across the wafer  →  bow ± 0.04 nm
```

---

## 5.7 Throughput, Matching & Exhaust

### 5.7.1 Throughput

```
Per-wafer chamber time (reference):
  Plasma                       M0 181 s       M1 184 s       M2 259 s
  Overhead                     34 s           34 s           40 s
    (wafer exchange 20 s, waferless clean 14 s; M2: clean 20 s)
  Per-chamber time             215 s          218 s          299 s
  4-chamber platform           67.0 wafers/h  66.1 wafers/h  48.2 wafers/h
```

The specification of Chapter 1 asks for at least 60 wafers per hour. M1 gives 66.1, 10% above it. The season steps (0.5 s per wafer) and the NF₃ cleans (60 s per 25 wafers, 2.4 s per wafer) together cost 2.9 s per wafer, 1.3% of the chamber time, and bring the platform to 65.2 wafers per hour.

### 5.7.2 Matching

```
Chamber matching criteria (M1):
  ACL rate, blanket (ER₀)             ± 3%  across chambers
  ACL:SiON selectivity                ≥ 48 on a blanket SiON witness (reference 51)
  Exit CD of a test structure         ± 0.4 nm from the fleet mean
  Bow (XTEM or CD-SAXS)               ± 0.15 nm
  Edge tilt (shift over the mask)     ≤ 1.2 nm at 147 mm radius; fleet spread ≤ 0.4 nm
  OES ratio CO/Ar at ME               ± 5%
  Particle adders ≥ 30 nm             ≤ 10 per wafer
```

### 5.7.3 Exhaust: COS, CO, and SO₂

The carbon open puts more combustible and toxic gas into the foreline than any other etch in the module. Per wafer:

```
Gas load (M1 main etch), on a 20 slm nitrogen foreline dilution:
  COS (30 sccm, if undecomposed)         1500 ppm
  CO from the wafer (22 sccm C) + from COS (30 sccm)      52 sccm → 2600 ppm
  SO₂ if all sulfur is oxidized          1500 ppm
  HF and SiF₄ from the SiON open         tens of ppm
```

```
Installation requirements:
  Abatement          thermal oxidizer on every foreline: CO → CO₂, COS → CO₂ + SO₂; wet scrubber for SO₂
                     and HF (≥ 99%); abatement cost $0.30 per wafer (M1)
  Gas monitoring     COS and H₂S (from moisture hydrolysis of COS) in the gas cabinet and exhaust;
                     CO in the exhaust, alarm at 25 ppm
  Cabinets           COS is toxic and flammable: leak-checked, excess-flow shut-off, flammable-gas detection
  Purge              inert purge on the foreline to keep sulfur from accumulating in the pump
```

---

## Summary and Key Takeaways

1. **The carbon open runs in an oxide-etch chamber with different gases and walls.** The 60/2 MHz CCP is the same hardware as the capacitor etch, which helps matching of tilt.

2. **Ion transit decides the frequency.** τ_i = 154 ns; the transit ratio at 2 MHz is 0.31; the IEDF is ± 30%. The ion angular spread, 0.9° at 600 eV, is about the same as the tube's geometric acceptance (1.3°).

3. **Pulsing at 5 kHz, 70% lets the film grow in the off-time.** It costs rate and needs a higher source power, and it reduces x₀.

4. **The first wafer after the NF₃ clean doubles x₀.** Bow 1.34 nm on wafer 0, 0.70 nm by wafer 8; a 12 s season keeps it at 0.77 nm.

5. **The ring sets the tilt, and the tilt sets the ring's life.** 0.08° per 100 µm; the 0.05° limit at 25 µm and 4,070 wafers; the shift is 1.2 nm of the 1.5 nm budget.

6. **The wafer heats by 24 K.** The lateral rate rises 6.1% per kelvin and the bow 0.04 nm per kelvin; every ACL step holds the wafer at 10 ± 1 K.

7. **The exhaust is the cost of the chemistry.** 2600 ppm of CO and 1500 ppm of S-compounds on a 20 slm foreline; abatement is $0.30 per wafer.

---

## Study Questions

1. Compute the Debye length, sheath thickness, ion transit time, and transit ratio at 2 MHz for a plasma with T_e = 3.5 eV, n_i = 1.5 × 10¹¹ cm⁻³, and a sheath voltage of 800 V (O₂⁺, 32 amu). Which way does the IEDF width move?

2. The ion angular spread is σ_θ = √(T_i/E). At what mean energy is the spread 0.65° if T_i = 0.15 eV? What fraction of the geometric acceptance (1.3°) is that spread?

3. A season step is skipped for one NF₃ clean. Using Section 5.3.2, estimate the number of wafers that exceed the 1.0 nm bow specification and the number of dies affected (900 per wafer). What does a 12 s season cost in chamber time per 25 wafers, as a fraction?

4. The ring wears at 0.12 µm per RF-hour. What ring life does the 0.05° limit allow at 184 s per wafer? If the limit is tightened to 0.04°, find the new life and the extra cost per wafer of the ring ($1,500).

5. For M1 find the wafer temperature rise if the helium conductance degrades to 0.05 W cm⁻² K⁻¹ (a worn ESC). By how much does the bow rise, assuming ±0.04 nm/K?

6. Compute the foreline concentration of CO and COS if the nitrogen dilution is reduced from 20 to 10 slm. Is a 25 ppm CO alarm at the facility exhaust (diluted 100:1 more) still sufficient?

---

**Next Chapter:** [Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Profile Levers](./06-ion-energy-pulsing-temperature.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
