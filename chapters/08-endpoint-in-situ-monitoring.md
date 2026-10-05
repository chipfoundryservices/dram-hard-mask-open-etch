# Chapter 8: Endpoint & In-Situ Monitoring of a Carbon Open

## Overview

The main etch must stop when the carbon has cleared, and not before. Too early and the holes are blind; too late and the cap is gone, the mask is short, and the nitride is eaten. The window is narrow: 11 s of overetch, with the top loss growing at 6.4 nm for every second of it, and at the end of it a stop layer that takes 8 nm per minute. The decision has to be made on a signal from a plasma whose gas contains the same product the wafer makes.

This chapter describes that signal and what it can tell. The clearing of 17 billion holes is a **population event**: each hole clears at its own time, the carbon monoxide the wafer releases falls as they do, and the emission that is measured is the fraction of the plasma's CO that comes from the wafer, which is 40%. The endpoint detects the median hole. What the overetch must cover is the tail. The chapter shows why interferometry, the usual tool for a film, fails here, how the endpoint logic works, what an endpoint is worth against a timed etch, and what the endpoint cannot do: it cannot tell the mask how tall it is.

**Learning Objectives:**
- Compute the fraction of the CO emission that comes from the wafer, and the signal that drops at clearing
- Relate the width of the clearing transition to the distribution of hole clearing times
- Explain why the endpoint measures the median hole and why the overetch is set by the tail
- Show why visible interferometry is blind and infrared interferometry is impractical for the carbon open
- Describe the endpoint logic, its arming window, and its fall-back
- Compare an endpoint-based etch with a timed etch, in time, top loss, and risk
- List the in-situ signals used beyond the endpoint

---

## 8.1 The Signal

### 8.1.1 What Emits

```
Emission lines used (illustrative):
  CO (Ångström bands)      483.5 nm       carbon removal; falls at clearing
  CN (violet)              388.3 nm       N₂ chemistry; BARC and SiON open
  SiF                      440 nm         SiON open
  O                        777.4 nm       oxygen density
  Ar                       750.4 nm       actinometer: normalizes electron density and window
```

During the main etch carbon monoxide is made in two places. The wafer's carbon leaves as CO (and some CO₂), and the COS in the gas also dissociates to CO and sulfur. The CO emission is the sum, and only the wafer's part changes when the holes clear:

```
CO budget of the main etch (M1, 600 eV):
  Carbon released by the holes      1.40 × 10²¹ atoms / 144.4 s = 9.7 × 10¹⁸ s⁻¹ = 21.6 sccm
  Carbon released at the bevel      the 1 mm ring that the cap does not cover:
                                    π (150² − 149²) mm² = 9.4 cm²  ×  1.08 × 10¹⁷ cm⁻² s⁻¹ = 2.3 sccm
  CO from the COS (if all dissociated)    30 sccm
  Total CO source                   21.6 + 2.3 + 30 = 53.9 sccm

  Fraction from the holes           21.6 / 53.9 = 40%       ← the signal that falls at clearing
  Remaining after clearing          60%
```

The bevel is a small baseline (4% of the total), but an unprotected edge of 3 mm instead of 1 mm would raise it to 12% and cut the drop at clearing from 40% to 37%. The cap and the resist are edge-bead-removed to 1 mm for this reason.

### 8.1.2 The Transition

Holes do not clear together. The clearing times are spread by every variation that Chapters 2 and 4 listed, each of which becomes a spread in seconds:

```
Within-wafer contributions to the clearing time (3σ, in seconds of main etch at the exit rate of 8.0 nm/s):
  ACL thickness (0.8%, 11 nm)       1.4 s
  Rate uniformity (2.5%)            3.6 s
  Wafer-edge lag                    3.0 s
  LCDU tail (2.4 nm, 18.7 nm)       2.3 s
  Family offset (1.1 nm, 8.6 nm)    1.1 s
  ──────────────────────────────────────────
  RSS (3σ)                          5.5 s          σ_t = 1.84 s
```

The fraction of cleared holes rises as the cumulative normal of the clearing times: from 0 to 100% over ±3σ = **11 s**. The CO emission falls by 40% of its pre-clearing value over the same 11 s, at a maximum rate of 0.40 / (σ √(2π)) = 8.7% of the signal per second at the 50% point.

---

## 8.2 What the Endpoint Measures

### 8.2.1 The Median Hole

The endpoint is declared when the CO has fallen to 50% of its drop: when half the holes have cleared. That is the **median clearing time**, which in M1 is 144.4 s, the time of Chapter 3 for the mean hole. The endpoint therefore tracks everything that moves the whole population together (the thickness of the carbon, its hydrogen content, the rate of the chamber), and says nothing about the spread, which is the tail the overetch must cover:

```
Endpoint and overetch:
  EP at 50% cleared                              t_EP  (144.4 s in M1)
  Holes cleared by EP + 5.5 s (3σ)               99.9%
  Margin (5 s, rate drift and the slowest tail)  5 s
  ──────────────────────────────────────────────────────
  OE-clear after EP                              5.5 + 5 ≈ 11 s       (85 nm of carbon at the exit rate of 8.0 nm/s)
```

The 85 nm covers the 45 nm (RSS) of the five terms and the 40 nm of margin. It is the budget of Chapter 5 expressed in nanometres.

### 8.2.2 What It Cannot Measure

The CO signal has no memory of the mask's height. It falls when the holes clear, whatever the mask has lost at the top. **Top loss is invisible to the endpoint.** A mask that has lost 30 nm too much at the top, because the cap was 0.5 nm thin or the cap erosion was 1% fast, ends the main etch at the same time as one that has lost none. The only time-keeper that knows is the cap itself, and nothing in the plasma reports its death (the SiON cleared on the web is 1.5 nm, 0.4% of the area, an emission too small to see). Section 8.6 returns to what that implies.

---

## 8.3 Why Interferometry Fails

For films, the standard endpoint is interferometry: light reflected from the top of the film and from its bottom interfere, and the fringes count the thickness removed. For the carbon open:

```
Visible light (633 nm):
  Extinction coefficient of ACL    k ≈ 0.4
  Penetration depth                λ / (4πk) = 633 / (4π × 0.4) = 126 nm
  Round trip through 1350 nm       exp(−2 × 1350 / 126) = 5 × 10⁻¹⁰
  → the front of the etch is invisible; the carbon is opaque.

Infrared (1550 nm):
  k ≈ 0.05; penetration depth      2.5 µm;   round trip through the array 0.33–0.73
  Effective medium of the array    ε = 0.565 × 4.0 + 0.435 × 1 = 2.70,  n_eff = 1.64
  Fringe period                    1550 / (2 × 1.64) = 470 nm of carbon removed
  Fringes in the 1350 nm mask      2.9
```

Infrared interferometry could see through the array, and it would count three fringes in the main etch. It is not used, for three reasons. First, it needs a large block of array under the beam (a spot of 100 µm, an array block of 1 mm), which a product wafer has and a scribe does not, and gives the median over that block and not the wafer. Second, the buried mold, oxide, nitride, tungsten, and the silicon beneath them (transparent at 1.55 µm) reflect with fringes ten times stronger than the etch front's, so the front is a small modulation on a large changing background. Third, a count of fringes from the start of the etch is the only way to know which fringe is the last, and a missed or phantom fringe is an endpoint error of 470 nm of carbon: 59 s. The OES is cruder and has none of these problems.

---

## 8.4 The Signals at the Steps

```
Endpoint and monitoring by step (M1):
  Step            Marker                          Used as         Notes
  ──────────────────────────────────────────────────────────────────────────────────────────────────
  ST1 BARC open   CN 388 nm falls                 time (8 s)      the BARC covers the whole wafer
  ST1 SiON open   SiF 440 nm / Ar falls (3%)      time (12 + 2 s) SiON is etched only in the holes (16.5%)
  ST2 start       CO, CN burst for 2 s            not used        resist burn-off: 25 nm at 12 nm/s
  ST2 clearing    CO 483.5 nm falls 40%           ENDPOINT        median hole; 50% point
  ST3a OE-clear   —                               time (11 s)     after EP
  ST3b OE-smooth  —                               time (7 s)      
  SiN exposed     CN rises ≈ 2–3%                 monitor only    SiN at 8 nm/min releases little N
```

Two of these deserve a comment. The SiON open does not have a useful endpoint, because the SiON on the web is protected by resist and only the holes (16.5% of the wafer) contribute: the SiF line falls by 3% and the step is run on time, with the OES used to flag a drift of the rate. And the nitride at the bottom of the holes gives almost no signal on its own: at 8 nm per minute over 16.5% of the wafer it releases perhaps a part in a hundred of the nitrogen the 60 sccm of N₂ already supplies. The carbon's clearing is the only usable edge.

---

## 8.5 Endpoint Logic

### 8.5.1 The Algorithm

```
Endpoint logic (illustrative):
  Normalize           CO 483.5 / Ar 750.4  (removes electron density and window transmission)
  Smooth              1 s moving average
  Arm                 120 s after the plasma is struck (earliest clear ≈ 139 s)
  Pre-clearing level  mean of the signal from 60 s to 110 s
  Post-clearing level the pre-clearing level × 0.60 (expected plateau); updated from the run-to-run history
  Trigger             signal = pre − 0.5 × (pre − post), confirmed on 3 consecutive 1 s samples
  Time-out            175 s: end the main etch, flag the wafer
  Fall-back           if no trigger by 175 s, or a plateau change < 15% (sensor fouled): time-based, 150 s
```

The timing jitter of the trigger is set by the noise on the slope: with a noise of 0.3% on the 1 s average and a slope of 8.7% per second, 0.03 s. **The trigger is far more precise than the hole population is narrow.** What limits the endpoint is not the sensor but the 1.84 s standard deviation of the thing it measures.

### 8.5.2 Failure Modes

```
Failure                              Signature                          Control
──────────────────────────────────────────────────────────────────────────────────────────────────────
Window fouled by sulfur              pre-clearing plateau falls (2% per 100 wafers)   Ar normalization; window clean on
                                                                                      the waferless clean; replace at 20% loss
False early trigger                  a flow or power transient before 120 s            arming window; 3-sample confirmation
Plateau change from COS drift        post/pre ratio ≠ 0.60 ± 0.05                      COS flow check from the SO or CO baseline
Bevel carbon larger than designed    post/pre ratio > 0.66                             edge-bead-removal check; wafer-edge CD map
Early plasma arc                     CO and Ar both drop                               arc detector on the bias; flag
```

---

## 8.6 What an Endpoint Is Worth

An endpoint does one job a timed etch cannot: it guarantees the holes clear however fast or slow the film opens. It does not do the job a reader might hope, which is to protect the mask height. The comparison, for a film that opens 3% faster or slower than nominal (hydrogen ±1 at%, Chapter 2):

```
Endpoint-based (M1) and timed etches (ME fixed at 144.4 s) for a film rate error of ±3%:

                                         Endpoint (EP + OE 18 s)       Timed (ME 144.4 s + OE 20.3 s)
  OE-clear needed after the median       11 s                          13.3 s  (8.3 s RSS incl. wafer-to-wafer, + 5 s)
  Plasma time, nominal film (T)          162.4 s                       164.7 s
  Top loss, nominal film                 50 nm                         66 nm        (+2.3 s)
  Film opens 3% faster:  clears at       140.2 s → T 158.2 s           144.4 s: clears 4.2 s early (extra overetch)
    top loss                             28 nm  (−22)                  66 nm  (±2)
  Film opens 3% slower:  clears at       148.9 s → T 166.9 s           144.4 s: clears 4.5 s late (inside the OE margin)
    top loss                             80 nm  (+30)                  66 nm  (±2)
```

The endpoint puts the **clear** under control and gives up the top loss: a 3% error in the film's rate becomes −22 or +30 nm of mask, because the cap's life is fixed in seconds and the open is not. The timed etch does the opposite, protecting the top loss from the film's rate and making the clear depend on a longer overetch, which costs 16 nm of mean top loss and fails the 1342 nm requirement for the mean mask height (top loss at most 58 nm, Chapter 6) at 66 nm. Neither is acceptable alone. The solution is the one that Chapter 15 describes:

```
Endpoint + feed-forward of the film's rate to the COS flow:
  1 sccm of COS = 1% of the cap's erosion rate (0.071/30 = 0.0024 nm/s) = 1.5 s of the cap's clock
  Film hydrogen +1 at% → rate +3.0% → open time −4.3 s → COS +2.9 sccm restores the clock (and the reverse for −1 at%)
  Residual (hydrogen known to ±0.3 at%):   ±0.9% in rate → ±1.3 s → ±8 nm of top loss
```

COS is the right knob because it moves the cap's clock without moving the carbon's rate (the chemical term of Chapter 3 is independent of the ion-driven rate); trimming the source power instead would move both, and would leave most of the top loss error in place. The endpoint guarantees the clear; the feed-forward keeps the clock steady; and the thickness of the cap sets the cliff on which the clock runs (Chapter 11).

---

## 8.7 Other In-Situ Signals

```
In-situ signals beyond the endpoint (M1, logged per wafer):
  Signal                         Used for
  ───────────────────────────────────────────────────────────────────────────────────────────
  RF voltage and current (V/I)   ion energy (DC bias, V_pp); sheath state; bias waveform
  Source and bias power          delivered power; matching
  Impedance, reflected power     chamber state; wall film; arcing
  OES CO/Ar, O/Ar, CN/Ar         gas composition; rate; endpoint time
  SO emission (≈ 300 nm)         COS flow and sulfur chemistry
  Wafer temperature (backside)   ESC and He flow; heating per step
  Ion flux probe (edge ring)     ion flux at the wafer edge; ring wear
  Pressure and gas flows         flow errors
```

None of these is a measurement of the hole. Each is a feature, and Chapter 15 combines them into a virtual metrology of the quantities the hole carries: bottom CD, bow, and top loss.

---

## Summary and Key Takeaways

1. **Only 40% of the CO emission comes from the wafer.** The holes release 21.6 sccm of carbon; the COS supplies 30 sccm of CO and the bevel 2.3; the signal falls 40% at clearing.

2. **Clearing is a population event.** The holes clear over 11 s (±3σ, σ = 1.84 s); the signal falls at 8.7% per second at the 50% point.

3. **The endpoint measures the median hole.** The 11 s overetch covers the tail: 5.5 s of 3σ and 5 s of margin, 85 nm of carbon.

4. **Visible interferometry is blind; infrared interferometry is impractical.** The penetration depth at 633 nm is 126 nm; at 1550 nm the fringe period is 470 nm and the buried films swamp it.

5. **The endpoint cannot see the mask height.** The top loss is set by the cap's life and the open's duration, neither of which the CO signal reports.

6. **An endpoint buys the clear and gives up the top loss.** A film that opens 3% faster or slower changes the top loss by −22 or +30 nm at the endpoint; a timed etch has to pay 16 nm for its margin.

7. **The cure is a feed-forward to the COS flow.** 1 sccm of COS is 1.5 s of the cap's clock; with the film's hydrogen known to ±0.3 at%, the residual top loss is ±8 nm.

---

## Study Questions

1. Recompute the fraction of the CO signal that comes from the holes for a COS flow of 40 sccm and the same wafer. By how much does the drop at clearing change, and what happens to the slope at the 50% point?

2. The wafer-edge lag rises from 3.0 to 5.0 s (3σ). Find the new RSS of the five terms, the new width of the transition (±3σ), and the OE-clear needed with the 5 s margin.

3. Compute the fringe period and the number of fringes in a 1500 nm B-ACL mask at 1550 nm for the 1d array (open fraction π × 26² / 4 / 1176 = 45%; use ε = 0.55 × 4.2 + 0.45 × 1, with B-ACL n = 2.05).

4. The window loses 2% of its transmission per 100 wafers. After how many wafers does the pre-clearing level, un-normalized, fall by 20%? If the Ar actinometer sees the same loss, what is the loss of the normalized signal?

5. A film opens 2% slower than nominal. Using the endpoint, find the main-etch time and the top loss (cap life 146.7 s, ER_top 12.17 nm/s, τ_w = 30 s; the rate in the exposed phase falls 2% as well). Compare with the timed etch.

6. The hydrogen content of a wafer is known to ±0.3 at% after feed-forward. Convert to a rate error and a time error, and to a top loss error using 6.4 nm/s. Is the result within the ±12 nm budget of Chapter 2?

---

**Next Chapter:** [Chapter 9: Walls, Residue, Particles & the Post-Open Hold](./09-walls-residue-particles-post-open.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
