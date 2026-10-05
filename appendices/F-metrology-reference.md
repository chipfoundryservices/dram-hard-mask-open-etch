# Appendix F: Metrology Reference

The measurements that qualify and control the hard mask open: what each measures, how well, how often, and where. Methods and precisions are those of Chapter 15; values are illustrative.

---

## F.1 Dimensional Metrology

```
Quantity                        Method                           Precision (3σ)   Sampling per lot (25 wafers)         Where
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Cap CD, families, LCDU, LER     CD-SEM (top-down)                0.15 nm          5 wafers × 9 sites × 3 families      after litho
Exit CD, families, ellipticity  HV-SEM (30–50 keV, top-down)     0.30 nm          2 wafers × 9 sites                   after open
Top CD, bow, depth, exit        CD-SAXS (X-ray scattering)       0.15 nm          1 wafer × 5 sites                    after open
Profile, foot, residue          XTEM / STEM                      0.3 nm           1 per week per chamber (destructive) calibration
Top loss, edge height           IR scatterometry (ridge test)    3 nm             1 wafer × 5 sites                    after open
Tilt, edge placement            test-structure shift, HV-SEM     0.2 nm           1 wafer per week per chamber         chamber qual.
Overlay (cap level, buried)     optical overlay marks            —                per litho plan                       after litho
Wafer bow                       capacitive gauge                 5 µm             all wafers                           incoming / outgoing
```

```
What each method sees in the 1350 nm × 31 nm tube:
  CD-SEM (top-down, low voltage)   the cap and the resist; not the carbon below it
  HV-SEM at 30–50 keV              electrons penetrate the carbon: the exit of every hole (a closed exit is dark);
                                    exit CD and ellipticity; centroid placement
  CD-SAXS                          the average CD at 30 depths over a 10 × 10 µm block: top CD, bow, bow depth,
                                    exit, family offset (second harmonic), 0.15 nm, no cutting
  Visible scatterometry            fails: penetration depth 126 nm at 633 nm in ACL (k = 0.40)
  IR scatterometry (1.3–1.7 µm)    heights and loss on a test structure; cannot resolve a 0.7 nm bow in a 31 nm hole
  XTEM / STEM                      the calibration of all of them: profile, foot, residue, sulfur (EELS)
```

```
Specification and measurement:
  Quantity                    Specification            Method                     Measurement precision / margin
  Exit CD (mean)              31.0 ± 1.0 nm            HV-SEM                     0.30 nm
  Family offset               ≤ 1.2 nm                 HV-SEM                     0.30 nm
  LCDU (3σ)                   ≤ 2.4 nm                 HV-SEM, CD-SEM             0.15–0.30 nm
  LER (3σ)                    ≤ 2.5 nm (1.95 after ST3b)   CD-SEM                 0.15 nm
  Bow                         ≤ 1.0 nm                 CD-SAXS                    0.15 nm (reference 0.67)
  Minimum web                 ≥ 11.0 nm                derived: 45 − CD_bow       0.15 nm (reference 12.2)
  Mask height after open      ≥ 1330 nm (3σ bound)     ellipsometry + IR ridge    3 nm (reference 1350; bound 1340)
  Top loss                    ≤ 58 nm (mean)           IR scatterometry, VM       3 nm; VM residual 6 nm
  Foot angle (local)          89.3° (last 50 nm)       XTEM                       0.3°
  Residue at the exit         none ≥ 2 nm              XTEM, HV-SEM               —
  Ellipticity (edge rows)     ≤ 0.03                   HV-SEM                     —
  Placement (mask-open)       ≤ 1.5 nm                 test structure, HV-SEM     0.2 nm (reference 1.4 nm RSS)
```

---

## F.2 Thickness, Chemistry, and Surface

```
Quantity                        Method                           Precision (3σ)        Sampling                           Where
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
ACL thickness, density          ellipsometry + deposition log    0.2 nm; ± 0.2 at% H   all wafers, 49 sites               incoming
Cap thickness, index            ellipsometry (193 nm)            0.10 nm               all wafers, 49 sites               incoming
Cap flat erosion rate (v_cap)   blanket SiON witness             0.8% (0.002 nm/s)     daily per chamber                  chamber monitor
ACL rate (ER₀), ARDE k          blanket ACL witness              ± 3%                  daily per chamber                  chamber monitor
Film stress                     wafer bow gauge                  ± 10 MPa              incoming (stress −300 ± 30 MPa)    incoming
Sulfur on the wall / exit       XPS, EELS on cleaved walls       10¹⁴ cm⁻²             weekly; after PM                   qualification
Water on the wall               thermal desorption / load-lock   0.02 mg               qualification                      after the hold
Oxide in the chamber (SiOₓ)     witness coupon, ellipsometry     2 nm                  per NF₃ interval                   chamber
```

---

## F.3 Defect Inspection

```
Large-area HV-SEM inspection (hard mask open):
  Defect rate (not open + merged + closed)   3 × 10⁻⁹ per hole = 52 per die
  One defect per                              3.3 × 10⁸ holes = 0.0058 cm² of array
  To see 30 defects                           0.17 cm² of array (0.57 dies);  precision 1/√30 = 18% (1σ)
  Throughput of a large-field e-beam          ≈ 0.8 cm²/h → 13 min for 0.17 cm²
  Sampling                                    1 wafer per 5 lots (125 wafers)
  Role                                        monitor and budget confirmation, not a control signal;  pooled over lots
  To separate lines of the budget (pinch-off 0.7 × 10⁻⁹ …)   about 1 cm² of array per wafer
Particles ≥ 30 nm:   unpatterned-wafer scan, 30 nm sensitivity, daily per chamber, ≤ 10 adders; ≥ 80 nm ≤ 0.5
Optical inspection after litho:  missing openings at cap level (before the open)
```

---

## F.4 Electrical Monitors and the Bitmap

The only measurement that resolves the lines of the not-open budget is the fail bitmap of the finished die (Chapter 16). Signatures of the hard mask open:

```
Signature                                           Cause in the open                          Chapter   Action
─────────────────────────────────────────────────────────────────────────────────────────────────────────────
Weak cells on the 1:2:1 family pattern (C weakest), family offset grows (G 1.10 → 1.30);      4, 10     check the gain; litho families; recipe
 worse at the edge                                   exit CD low
Pairs of failing cells along the webs, three         merged holes (web broken); bow high         4, 13     bow, temperature, COS; chamber matching
 orientations
Random isolated dead cells, step change at a PM      pinch-off, micromask: tail scale Δ₀,        13, 9     wall state; season; electrode age
                                                      silicon supply
Radial pattern in capacitance / mask-height trend    top loss varies with cap thickness          11        cap map; COS feed-forward
Weak rows along the edge of every array block,       stress relaxation of the carbon;            12        litho compensation; film stress
 decaying over 15–30 rows                            uncompensated displacement
Weak cells at the wafer edge along the radius,       edge tilt (ring wear)                       5, 12     ring replacement
 shifted radially
Random weak cells in the interior of blocks          wiggle (face asymmetry); thin web           12        film, energy, passivation
Lot-to-lot shift of the whole distribution           film hydrogen, cap thickness, queue         2, 9, 15  APC; queue discipline
```

```
Repair and yield (M1, Chapter 16):
  51.5 events per die; 600 sub-arrays of 28 Mb, spares for 4 defects each → 0.086 events per sub-array
  P(> 4 in one sub-array) 3.6 × 10⁻⁸ → loss 2.2 × 10⁻⁵ per die (M0: 1.4 × 10⁻⁴)
  Unrepairable fraction f_u = 2 × 10⁻⁴ (illustrative): loss 1 − exp(−N f_u) = 1.02% (M1), 1.50% (M0): difference 0.48%
```

---

## F.5 In-Situ and FDC Signals

```
Signal                          Source                     Use                                                       Alarm
────────────────────────────────────────────────────────────────────────────────────────────────────────────
CO 483.5 nm / Ar 750.4 nm       OES                        endpoint (drop of 40% at clearing); plateau level          ± 5% plateau
SO / Ar                         OES                        COS flow and the sulfur state of the wall                  ± 5%
O / Ar                          OES                        oxygen supply; wall loss                                   ± 5%
CN 388 nm; SiF 440 nm / Ar      OES in ST1                 BARC clear (8 s), SiON clear (12 + 2 s)                    time-out
SiN exposure (CN + 2–3%)        OES                        monitor of the stop (SiN loss ≤ 3 nm)                      —
Resist burn-off burst           OES at the start of ST2    2 s transient; confirms ST1 passed                         —
V_dc, delivered bias power      RF sensor                  ion energy (± 5 eV); exit CD and bow VM features           ± 15 eV
Reflected power / matching      RF sensor                  plasma stability; re-ignition at 5 kHz                     > 2%
ESC and backside temperature    ESC sensors                wafer temperature (10 ± 1 K); bow VM                       ± 3 K
Helium backside flow            mass flow                  thermal contact (h_He 0.07 W/cm² K at 15 Torr)             + 20%
Ion-flux probe at the edge ring probe                      edge flux and the exit CD at 147 mm; ring wear             ± 5%
Exhaust CO, COS, SO₂            FTIR / sensor              abatement; CO alarm 25 ppm; COS 1,500 ppm, CO 2,600 ppm   25 ppm CO
Window fouling                  OES intensity              2% per 100 wafers (clean at the PM)                        —
```

---

## F.6 Sampling Plan and Cost

```
Per lot of 25 wafers (M1):
  Incoming films (ellipsometry, all wafers, 49 sites)         all
  CD-SEM (cap CD, families)                                    5 wafers (9 sites × 3 families)
  HV-SEM (exit CD, ellipticity)                                2 wafers (9 sites) + test structures
  CD-SAXS (bow, profile)                                       1 wafer (5 sites)
  IR scatterometry (ridge, top loss)                           1 wafer (5 sites)
  Large-area inspection                                        1 wafer per 5 lots
  Virtual metrology (top loss 6 nm, exit CD 0.20 nm, bow 0.06 nm)   every wafer
Per chamber:  daily monitor (ACL, SiON, SiN blankets; particle scan);  weekly fleet-matching wafer;
  XTEM weekly;  after a part change: qualification of Appendix C.1

Metrology cost per wafer (M1):
  Incoming films $0.25 + CD-SEM $0.25 + HV-SEM $0.30 + CD-SAXS $0.20 + large-area inspection $0.10 = $1.10
  (M0 $0.80; M2 $1.60; M3 $1.80)
```

---

**Appendix F Version:** 1.0  
**Last Updated:** 2026-10-05
