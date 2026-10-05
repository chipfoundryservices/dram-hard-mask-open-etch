# Appendix D: Process Windows

Reference windows for the hard mask open module. "Target" is the reference process (M1); "window" is the range within which the specification of Chapter 1 is met with the other parameters at target. The specification used throughout is: ACL after open ≥ 1342 nm in the mean (top loss ≤ 58 nm, so that the 3σ lower bound of 12.3 nm reaches 1330 nm), bow ≤ 1.0 nm, minimum web ≥ 11.0 nm, exit CD 31.0 ± 1.0 nm. Windows for the temperature, energy, COS flow, power, duty, and overetch are read from the sensitivity table of Chapter 6; the others are starting points for a design of experiments. All values are illustrative.

---

## D.1 ST1: BARC and SiON Open

```
Parameter                 Target                   Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────────────
Gases CF₄ / CHF₃ / Ar     80 / 20 / 300 sccm       CHF₃ ± 5 sccm       exit CD 0.066 nm/sccm (APC knob, ± 0.33 nm);
                                                                       cap taper 89.3°
Pressure                  20 mTorr                 18–22 mTorr         cap CD uniformity
Source power (60 MHz)     1.2 kW                   1.1–1.3 kW          BARC / SiON rate (190 / 200 nm/min)
Bias (2 MHz), CW          400 eV                   350–450 eV          resist burn-off (high); SiON residue (low)
Wafer temperature         4 °C (ESC −14 °C)        1–7 °C              cap CD taper; ST2 start temperature
Time                      22 s                     21–25 s             SiON clear: BARC 8 s + SiON 12 s + 2 s over-
                                                                       etch (low); resist 25 nm left at 22 s,
                                                                       2.5 nm lost per extra second (high)
Cap CD (bottom / top)     32.0 / 33.0 nm           32.0 ± 1.0 nm       exit CD 31.0 ± 1.0 nm (Chapter 10)
Family offset             ≤ 1.0 nm                 —                   litho; ≤ 1.2 nm at the exit
Endpoint markers          BARC CN 388 falls (8 s); SiON SiF 440/Ar falls 3% (12 + 2 s)
```

---

## D.2 ST2: ACL Main Etch

```
Parameter                 Target                   Window                Limited by
────────────────────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature         10 °C (ESC −14 °C)       6.5–16.5 °C           top loss 58 nm at 6.5 °C (cold, +2.2 nm/K);
                                                                         bow 1.0 nm at 16.5 °C (warm, 0.04 nm/K)
Pressure                  12 mTorr                 11–13 mTorr           ER₀ uniformity (≤ 2.5%, 3σ); ion angle;
                                                                         not varied in the profile model
Source power (60 MHz)     1.5 kW                   1.43–1.65 kW          top loss at −5% (main etch lengthens);
                                                                         ion heating and ESC load at +10%
Bias, pulsed 5 kHz, 70%   600 eV (on-phase)        540–610 eV            top loss 58 nm at 610 eV (high);
                                                                         time +2.5 s per −20 eV (low; no quality limit)
Pulse frequency           5 kHz                    2–10 kHz              x₀ factor 1.03–0.99, bow ± 0.02 nm
Duty at constant mean     0.70                     0.60–0.80             bow 0.64–0.70 nm; on-phase bias power
 ion flux                                                                3.2–2.4 kW (2.7 kW at 0.70)
Gas O₂                    150 sccm                 140–160 sccm          O flux ± 7% → bow ± 0.05 nm (v_b ∝ Γ_O);
                                                                         ER₀ is ion-limited (± 0.5%)
Gas COS                   30 sccm                  20–30.7 sccm          top loss 58 nm at 30.7 sccm (10.8 nm per sccm);
                                                                         qualified range 20–40 sccm; bow 0.67–0.81 nm
Gas N₂ / Ar               60 / 300 sccm            ± 10%               wall chemistry; OES normalization (Ar)
Time                      to endpoint (144 s)      arm 120 s;            time-out 175 s; fallback 150 s timed
                                                   time-out 175 s
ER₀ (blanket ACL)         730 nm/min               ± 3% (± 22)           fleet matching; ACL:SiON 51 (≥ 48 to match)
Bow / minimum web         0.67 / 12.2 nm           ≤ 1.0 / ≥ 11.0 nm     bow bites before the web (Chapter 10)
Top loss                  50 nm                    ≤ 58 nm               mask height ≥ 1342 nm (3σ bound 1330 nm)
```

---

## D.3 ST3a: Overetch, Clear

```
Parameter                 Target                   Window                Limited by
────────────────────────────────────────────────────────────────────────────────────────────────────────
Gases O₂ / COS / N₂ / Ar  150 / 20 / 60 / 300      COS ± 3 sccm          v_cap 0.213 nm/s at 20 sccm; foot clear
Pressure / source / bias  12 mTorr / 1.5 kW / 5 kHz, 70%, 600 eV (as ST2)    same as ST2: the overetch cannot be run
                                                                         at 250 eV (ion transmission halves; 33 s)
Wafer temperature         10 °C (ESC −14 °C)       as ST2                bow evolves little; cap clock runs
Time after endpoint       11 s                     10.6–12.3 s           clear 85 nm at 8.0 nm/s (≥ 10.6 s) (low);
                                                                         top loss 6.3 nm per s (high)
ER at the exit            481 nm/min (8.0 nm/s)    ± 5%                  clear margin: 5.5 s (3σ) + 5 s
SiN loss at the stop      2.4 nm (18 s)            ≤ 3 nm               S = ACL:SiN 60 (8 nm/min SiN at 600 eV)
```

---

## D.4 ST3b: Overetch, Smooth

```
Parameter                 Target                   Window                Limited by
────────────────────────────────────────────────────────────────────────────────────────────────────────
Gases O₂ / COS / N₂ / Ar  200 / 8 / 30 / 300       COS 6–10 sccm         passivant in the concave parts of the wall;
                                                                         sulfur at the exit ≤ 10¹⁴ cm⁻²
Pressure                  25 mTorr                 23–27 mTorr           ion energy (≈ 500 eV at 600 V set-point)
Source / bias             1.0 kW / 5 kHz, 70%, 600 V set-point    —       CD change < 0.1 nm
Wafer temperature         10 °C (ESC −3 °C)        ± 3 K                 heating 0.66 kW → +13 K
Time                      7 s                      6–8 s                 LER gain 0.55 nm (low); top loss (high)
Total overetch            ST3a + ST3b = 18 s       ≤ 19.3 s              top loss +6.3 nm per s: +1.3 s reaches 58 nm
LER (3σ) after ST3b       1.95 nm (from 2.5)       ≤ 2.0 nm              striation ≤ 2 nm at the mold etch (Book #29)
```

---

## D.5 Chamber Cleans and Season

```
Parameter                 Target                   Window                Limited by
────────────────────────────────────────────────────────────────────────────────────────────────────────
Waferless clean O₂/Ar     14 s, every wafer        12–18 s               carbon-rich film 0.3 nm per wafer;
                                                                         S–C film 9 nm removed as SO₂
NF₃ clean                 60 s every 25 wafers     every 15–50 wafers    first-wafer effect (low interval: more
                                                                         resets); wall SiOₓ 93 nm at 50 wafers;
                                                                         particle limit 140 nm (75 wafers)
Season (COS-rich, cover   12 s after each NF₃      10–15 s               first-wafer bow: 0.77 nm (wafer 0) against
 wafer)                                                                  1.34 nm without; ≤ 0.85 nm required
Chamber wall temperature  60 °C                    55–65 °C              wall film adhesion; particles
Edge ring (Si)            25 µm wear (4,070 w)     ≤ 25 µm               tilt 0.05° (1.2 nm shift at r = 147 mm)
Upper electrode (Si)      1,500 RF-h (29,300 w)    ≤ 1,500 RF-h          x₀ factor 1.14 at the end (bow 0.76 nm)
```

---

## D.6 M2: Cyclic Deposition–Etch (1d-Class, −25 °C)

```
Parameter                 Target                   Window                Limited by
────────────────────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature         −25 °C                   ± 2 K                 v_b: 7.9% per K at −25 °C (E_a/kT²), ± 16% over ± 2 K
Deposition step           1.5 s: SO₂ / COS / Ar,   1.2–2.0 s             coverage restored at every depth (low);
                           no bias, 40 mTorr                             etch share, time (high)
Etch step                 4.5 s: O₂ / COS / CF₄ 3% / Ar, 5 kHz  4.0–5.0 s  ripple < 0.02 nm; coverage thinning
CF₄ fraction              3%                       2–4%                  boron removal as BF₃ (low); x₀ ×5 (high)
Cycles                    35 (209 s main etch)     —                     time-averaged ER₀ 560 nm/min
Cap (B-ACL 1500 nm)       60 nm SiON               ≥ 60 nm              holds a top-loss exposure of 17.9 s (Chapter 14);
                                                                         a 56 nm cap holds it for undoped ACL only
Bow / web                 0.46 nm / 9.5 nm         ≤ 0.8 / ≥ 9.0 nm     continuous plasma gives 0.95 / 8.9 (fails)
```

---

## D.7 Incoming Film and Pattern Windows

```
Parameter                      Target          Window               Limited by
────────────────────────────────────────────────────────────────────────────────────────────────
ACL thickness                  1400 nm         ± 14 nm (3σ)         after-open height; net slope 0.21 nm/nm
ACL density / hydrogen         1.80 / 17 at%   ± 0.02 / ± 1 at%     rate ± 3.0% per at% H; APC feed-forward
ACL stress                     −300 MPa        ± 30 MPa             wafer bow ≤ 120 µm; array-edge relaxation
SiON cap thickness             40.0 nm         ± 0.4 nm (1.0%)      top loss: 1 nm of cap = 21 nm of loss
SiON refractive index (193)    1.90            ± 0.02               etch rate; ellipsometry thickness model
Queue ACL → cap                ≤ 8 h           —                    film absorption; cap adhesion
Queue pattern → open           ≤ 24 h          —                    resist and BARC condition
Cap CD (resist after ST1)      32.0 nm         ± 1.0 nm             exit CD 31.0 ± 1.0 nm
Family offset                  ≤ 1.0 nm        —                    ≤ 1.2 nm at the exit
LCDU / LER (litho)             ≤ 2.4 / ≤ 2.5 nm (3σ)   —            stochastic merging and not-open (Chapter 13)
Overlay                        ≤ 5 nm          —                    placement budget 1.4 of 1.5 nm RSS
Wafer bow                      ≤ 120 µm        —                    chuck; ion tilt; backside particles
Backside particles             ≤ 30             —                    chuck flatness, helium leak
```

---

## D.8 Control and Alarm Bands

```
Parameter                      Control band             Alarm                Action
────────────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature (ST2)        ± 1 K                    ± 3 K                bow ± 0.04 nm per K; hold the lot at ± 3 K
COS flow                       ± 0.3 sccm               ± 1 sccm             1 sccm = 1.47 s of cap clock = 9.3 nm of loss
Ion energy (V_dc)              ± 5 eV                   ± 15 eV              20 eV = 2.5 s and 15 nm of mask
OES CO/Ar plateau (before)     ± 5%                     ± 8%                 chamber match; window fouling 2% per 100 wafers
Endpoint time                  within ± 1.5 s of fleet  ± 4 s                time-out 175 s; fall back to 150 s timed
Exit CD (EWMA, λ = 0.3)        ± 0.315 nm               —                    CHF₃ in ST1 (0.066 nm/sccm, ± 5 sccm)
Mask height (VM)               ≥ 1342 nm                < 1335 nm            feed forward H and cap, not carbon thickness
Moisture hold (air / N₂ FOUP)  ≤ 4 h / ≤ 12 h           —                    degas 150 °C, 30 s (−90% water)
```

---

**Appendix D Version:** 1.0  
**Last Updated:** 2026-10-05
