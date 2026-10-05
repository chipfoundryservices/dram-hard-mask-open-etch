# Appendix G: Troubleshooting Guide

Symptom-driven guide for hard mask open excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics. Reference values are those of route M1.

---

## G.1 Bow High (Above 1.0 nm; Reference 0.67 nm)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Wafer warm (ESC offset, helium leak)    Thermocouple wafer; backside He flow     Recalibrate the ESC; fix the leak;
   0.04 nm per K: +5 K → 0.90 nm           and pressure (15 Torr); edge zone        correct the edge zone
   (Ch. 6.4.1, 10.3)
2. First wafer after an NF₃ clean, season  Bow against wafer number since the       Restore the season (12 s); bow of
   skipped or short: 1.34 nm at n = 0      clean; season log                        wafer 0 ≤ 0.85 nm   (Ch. 5.3.2)
3. COS flow low: −5 sccm → +0.06 nm        SO/Ar emission; MFC response             Recalibrate the MFC; compare with
   (Ch. 6.5)                                                                        the flow in the recipe
4. Electrode aged: x₀ × 1.14 at 1,500      RF-hours of the electrode; bow trend     Replace at 1,500 RF-h (bow 0.76 nm);
   RF-h → bow 0.76 nm (Ch. 5.3.3, 5.5.1)   with the age                              APC trims T
5. Duty or pulse change: duty +0.1 at      Recipe revision; delivered power         Restore 5 kHz, 70%, constant mean
   constant flux → +0.03 nm (Ch. 6.3.1)    and pulse shape                          ion flux
6. Wall film changed: the cap-sourced      SiOₓ on the wall (nm); cap thickness     Check the NF₃ interval (25 wafers);
   SiOₓ (s = 0.13, top ~60 nm) is short    and v_cap                                restore the cap (Ch. 3.4, 5.3.1)
   of supply
```

Note: raising COS to cut the bow costs 54 nm of mask per 5 sccm for 0.04 nm of bow (Ch. 6.5); use temperature first (0.04 nm per K, ± 3 K from APC).

---

## G.2 Top Loss High (After-Open Height Below 1342 nm; Reference 50 nm)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────
1. COS flow high: +5 sccm → +54 nm         MFC log; SO/Ar; APC feed-forward         Correct the MFC; check the APC sign:
   (10.8 nm per sccm)  (Ch. 6.5, 15.4)     correction history                       ΔCOS = +2.9 ΔH − 0.085 Δh_ACL + 2.5 Δh_cap
2. Cap thin or erodes fast: 1 nm of cap    Cap ellipsometry map; blanket SiON       Re-qualify the cap deposition; consider
   = 21 nm of loss; v_cap + 1% = 9 nm      witness (v_cap 0.237 nm/s)               M1-c (42 nm cap; L 14 nm)  (Ch. 11)
3. Open too long: ER₀ low (source −10% →   EP time against 144.4 s; blanket ACL    Retune the power; recheck the pulse;
   L 68), cold wafer (−5 K → 61)           witness; ESC temperature                 feed forward the film H
   (Ch. 6.6, 8)
4. Overetch too long: +3 s → +21 nm        Step log; trigger jitter; EP time-out    Repair the trigger logic; check the
   (Ch. 8.5)                               (175 s) hits                             time-out and fallback
5. Ion energy high: +20 eV → +15 nm,       V_dc; delivered bias power               Restore the set-point (± 5 eV band)
   spec reached at 610 eV (Ch. 6.2)
6. Film harder than nominal: H −1 at% →    Deposition log; incoming density and H   Feed forward H (COS −2.9 sccm per −1 at%);
   open +4.3 s, loss 27 → 80 nm (Ch. 2.1.3)                                           tighten the deposition (± 1 at%)
7. Radial pattern: cap thickness map       Ellipsometry map of the cap              Correct the cap deposition profile
```

---

## G.3 Exit CD Off Target (31.0 ± 1.0 nm) or Family Offset Above 1.2 nm

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Cap CD out (litho or ST1)               CD-SEM cap CD (32.0 ± 1.0); ST1 taper    ST1 CHF₃ trim: 0.066 nm per sccm
   (Ch. 10.5, 2.3.1)                              (89.3°)                                  (± 5 sccm = ± 0.33 nm); litho
2. Foot changed: ion energy or the         HV-SEM exit CD with XTEM foot (f₀ 0.60   Restore bias and ST3a time; check
   overetch (Ch. 10.4)                     nm, λ 49 nm)                              V_dc
3. Radial: edge flux (+0.40 nm at          Exit CD vs radius; ion-flux probe at     Replace the ring (25 µm); check the
   147 mm)  (Ch. 10.6.1, 5.5.2)            the ring; ring wear                      edge zone
4. Array-edge rows: stress relaxation,     CD and ellipticity against row from the  Litho compensation (80%); dummy rows
   ellipticity (Ch. 10.6.2, 12.2, 12.5.1)  array edge                               do not cure it
5. Family offset (1:2:1 pattern):          HV-SEM per family (A, B, C)              Check the gain; litho families;
   G 1.10 → 1.30 (Ch. 4.2)                                                         the recipe
```

The exit CD is insensitive to the passivation levers (temperature, COS): it follows the cap CD, the foot, and the edge, not the bow (Ch. 10.5.2).

---

## G.4 Holes Not Open (Dark Exits in HV-SEM) or Large-Area Defect Rate High

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. ST3a short or endpoint early            CO drop and trigger time vs 144.4 s;     Restore OE-clear 11 s (≥ 10.6 s);
   (OE-clear must clear 85 nm)  (Ch. 8)    plateau level                            check trigger logic
2. SiON survivors: ST1 short, cap thick    ST1 SiF marker (12 + 2 s); cap           Lengthen ST1 within 21–25 s; check
   (e^(−0.5 t) per second of overetch)     thickness (40.0 ± 0.4 nm)                the SiON rate (200 nm/min)
   (Ch. 13.2)
3. Pinch-off: Δ₀ up (exit CD low, bow)     Exit CD and foot; tail scale: −4.9% of   Restore the foot and the profile;
   (Ch. 13.3)                              Δ₀ halves the rate                       check energy, tilt, temperature
4. Micromask or particle (killer 81 nm)    Particle scan; wall SiOₓ (≥ 140 nm → 10   NF₃ clean on time; check flaking;
   (Ch. 9.2, 13.4)                         adders)                                  replace the liner if needed
5. Residue or moisture at the exit         XPS/EELS for S at the exit; hold time    Degas 150 °C, 30 s; hold ≤ 4 h air,
   (Ch. 9.3.1, 9.5)                                                                 ≤ 12 h nitrogen FOUP
6. Missing opening from litho              Optical inspection after litho           Rework the litho layer (once)
   (Ch. 13.1–13.2)
```

---

## G.5 Endpoint Signal Weak, Late, Early, or Noisy

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Viewport fouling (2% per 100 wafers)    Ar 750.4 nm absolute intensity trend     Clean the window at the PM;
   (Ch. 8.5.2)                                                                      normalize CO to Ar
2. Array efficiency of a new product:      CO plateau and drop (40% at 0.379;       Qualify per product; set the product
   drop 40% → 44% at 0.45  (Ch. 8.1.2, 10.6.3)44% at 0.45)                             constant in the APC
3. Bevel / edge CO: wafer share only 40%   CO budget: 21.6 wafer + 2.3 bevel +      Check the edge-ring exclusion; bevel
   (Ch. 8.1.1)                             30 COS sccm                              film (3 mm ring → 6.75 sccm, drop 37%)
4. Wall state shifted the baseline         CO/Ar plateau (± 5%) before and after    Season; recheck NF₃ interval
   (Ch. 9.1)                               a clean
5. Algorithm settings                      Arm 120 s; pre 60–110 s; post 0.60 ×    Restore: trigger 50%, 3 consecutive;
   (Ch. 8.5.1)                             pre; time-out 175 s; fallback 150 s      jitter ≤ 0.1 s
6. Transition wide (> 13 s): rate          Large-area structure; rate map; thickness Fix the film or the plasma
   non-uniformity, edge, LCDU              map                                      uniformity (σ_t 1.84 s)
```

---

## G.6 First-Wafer Effect After a Clean

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. No season or season short               Season step log (12 s, COS-rich, cover   Restore the season; verify with
   (Ch. 5.3.2)                             wafer); bow of wafers 0–7                 Appendix C.4
2. NF₃ clean too long or too frequent      NF₃ log; interval (25 wafers)             60 s; interval 25
3. Waferless clean skipped                 Clean log; carbon-rich film (0.3 nm per   Restore 14 s every wafer
   (Ch. 9.1)                               wafer)
4. Wall temperature drifted (60 °C)        Wall thermocouples                        Restore (55–65 °C); 4 h bake after a
                                                                                    wet clean
```

Reference: x₀(n) = x₀ [1 + a e^(−n/2.5)], a = 1.0 without the season (bow 1.34, 1.12, 0.97 nm for n = 0, 1, 2) and 0.15 with it (0.77, 0.74, 0.72 nm).

---

## G.7 Edge Shift or Radial Placement Error (Above 1.2 nm at 147 mm)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Edge-ring wear: tilt 0.03° new +         Ring RF-hours (4,070 wafers = 25 µm);   Replace the ring at 25 µm; tilt test
   0.08° per 100 µm  (Ch. 5.5.2)           edge-tilt test structure (Appendix C.8)  after each change
2. Ring seating or height error            Ring height; shift in 8 azimuths         Reseat; check the lift pins
3. Edge-zone ESC temperature off           Radial bow and exit CD profile (+1 K →   Retune the zone; ± 3 K from APC
   (+0.04 nm bow per K)  (Ch. 10.6.1)       0.04 nm)
4. Array-edge stress relaxation (not       Offset against row (0.55 nm at row 1,    Litho compensation (80%); do not
   the wafer edge)  (Ch. 12.2)             15–30 rows)                               expect dummy rows to cure it
```

Shift table: 0.02° / 0.03° / 0.05° / 0.07° / 0.10° = 0.5 / 0.7 / 1.2 / 1.6 / 2.4 nm over 1350 nm.

---

## G.8 Particles Above Limit (More Than 10 Adders ≥ 30 nm per Wafer)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Wall SiOₓ too thick (limit 140 nm;      Count against wafers since the NF₃       NF₃ clean now; confirm the interval
   1.9 nm per wafer)  (Ch. 9.1.2, 9.2)     clean; coupon thickness                  of 25 wafers
2. Flaking after a thermal excursion       Chamber temperature log; adders against  Bake; wet clean if persistent
   or a pressure transient                 wafer count
3. Edge ring or electrode erosion          Parts RF-hours; visual                   Replace the part; requalify (C.1)
4. Wafer-handling or backside particles    Backside scan (≤ 30); load-lock          Clean the handling path; check the
   (Ch. 2.6, 16.1)                         particle count                            FOUP
5. Sulfur or S–C flakes in the exhaust     Foreline particle counter                Waferless clean time (12–18 s); check
                                                                                    the ESC
```

---

## G.9 Merged Holes, Twist, or Wiggling (Mechanics)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Web thin at the bow (bow high)          CD-SAXS bow; web at 12.2 nm (M0:         Fix the bow (G.1); web ≥ 11.0 nm
   (Ch. 4.5, 10.3)                         10.5 nm)
2. Film stress high (−300 ± 30 MPa)        Wafer bow gauge before and after;        Tighten the deposition; check the
   (Ch. 2.5, 12.1)                         film stress                              stress log
3. Face asymmetry (bimorph): wiggle        XTEM of the webs; tilt of the            Reduce the asymmetry; lower the
   0.70 nm (3σ) in M1; M0 1.07 fails       passivation; temperature uniformity      energy; check the chamber match
   (Ch. 12.3)
4. Hydrogen or density spread in the       Incoming H and density                   Deposition control (H ± 1 at%,
   film                                                                              ρ ± 0.02 g/cm³)
5. Array-edge ellipticity (row 1: 0.027)   HV-SEM ellipticity against row           Litho compensation; check the stress
   (Ch. 12.5.1)
```

---

## G.10 Residue, Sulfur or Moisture at the Exit

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Overetch short (foot not cleared)       Cross-section at the exit; EP and OE      Check ST3a (≥ 10.6 s); trigger
   (Ch. 9.3.1)                             times                                    timing
2. Sulfur film at the exit above 10¹⁴      XPS/EELS on cleaved walls; SO/Ar          Lower COS in the overetch (20 → 8
   cm⁻² (0.1 ML)                                                                   sccm in ST3b); degas
3. Moisture after a long queue             Thermal desorption; hold time             Degas 150 °C, 30 s; ≤ 4 h in air
   (Ch. 9.5)                               (0.35 mg at 8 h)                          (≤ 12 h in a nitrogen FOUP)
4. No wet clean available (by design)      —                                        Strip only by O₂ ash and rework once
```

---

## G.11 Blanket Rates Drifting (ER₀ or ACL:SiON)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Source power or ion flux drift          Delivered power; V_dc; ion-flux probe    Recalibrate; check the matching network
2. Wafer temperature offset                ESC log; thermocouple wafer              ER₀ +0.3% per K; recalibrate
3. Electrode / ring wear                   RF-hours; silicon supply                 Replace at 1,500 RF-h / 25 µm
4. Gas flow error (O₂, COS)                MFC verification; SO/Ar and O/Ar         Recalibrate; v_cap + 1% per sccm COS
5. Incoming film change (H, density)       Deposition logs                          Feed forward; recheck monitors
```

Quantities: ER₀ ± 3% (± 22 nm/min); ACL:SiON 51 ± 1.5; SiON v_cap ± 0.8% (daily monitor, Appendix C.2).

---

## G.12 Exhaust Alarms (CO, COS, SO₂)

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Abatement efficiency drop               Thermal oxidizer temperature; scrubber   Service the abatement; reduce load;
                                           pH; foreline analysers                    stop the lot at the alarm
2. Leak in the foreline or the chamber     Helium leak check; pressure rise         Isolate; leak-check before
                                           rate                                     restart
3. COS flow above recipe                   MFC flow vs set-point                    Close the COS valve; check the MFC
4. CO above 25 ppm at the exhaust          Foreline CO sensor                       Alarm; stop; verify abatement
   (steady state 2,600 ppm in the foreline,
   before dilution and abatement)
```

COS is toxic and flammable (Appendix A.6): 3.4 mmol per wafer, 31 kg per month at 150,000 wafers; the abatement costs $0.30 per wafer.

---

## G.13 Lot-to-Lot Shifts and APC Oscillation

```
Likely causes                              Checks                                   Actions
────────────────────────────────────────────────────────────────────────────────────────────────────────────────
1. Incoming film shift (H, thickness)      Deposition and ellipsometry logs         Feed forward H and cap (not carbon
   (Ch. 15.4)                                                                       thickness)
2. Queue time exceeded (8 h ACL → cap;     Queue log                                Enforce the queue; rework once
   24 h to open)  (Ch. 16.1)
3. EWMA gain too high: oscillation of      EWMA history; λ = 0.3; σ_rr 0.25 nm;     Restore λ = 0.3; limits ± 0.315 nm;
   the exit CD                              limits ± 0.315 nm                        check measurement noise (0.05 nm)
4. Metrology offset between tools          Matching of CD-SEM, HV-SEM, CD-SAXS      XTEM calibration (Appendix C.5)
5. Virtual-metrology model stale           VM residuals (top loss 6 nm, exit CD     Retrain on the latest HV-SEM and
                                           0.20 nm, bow 0.06 nm)                    CD-SAXS data
```

---

**Appendix G Version:** 1.0  
**Last Updated:** 2026-10-05
