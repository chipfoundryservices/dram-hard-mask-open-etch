# Appendix E: Geometry, Transport & Statistics Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions. Areas use the 6F² cell of 1734 nm² (as Book #29 does) and linear distances use the 45 nm nominal pitch; the two differ by 1.1%.

---

## E.1 Counts and Areas (Ch. 1)

```
holes per die = bits;   holes per wafer = bits × gross dies;   array area = bits × A_cell

Reference: 16 Gb = 16 × 2³⁰ = 1.718 × 10¹⁰ holes per die;  900 dies → 1.546 × 10¹³ per wafer
  A_cell = 6 F² = 6 × 17² = 1734 nm²;   array per die = 1.718 × 10¹⁰ × 1734 nm² = 0.298 cm²
  Hole at 31.0 nm:  A = π d²/4 = 754.8 nm²;   open fraction = 754.8/1734 = 43.5%
  Hole at 32 / 33 nm:  46.4% / 49.3%       (1 nm of CD is 2.9 points of open fraction)
  Aspect ratio:  hole 1350/31 = 43.5 (≈ 44);   web 1350/14 = 96
  Wall area per hole:  π d h = π × 31 × 1350 = 1.31 × 10⁵ nm²;   per wafer 2.03 m²
```

```
Carbon removed:
  Volume per die  = N A h = 1.718 × 10¹⁰ × 754.8 nm² × 1350 nm = 1.75 × 10⁻⁵ cm³
  Mass per wafer  = 1.75 × 10⁻⁵ cm³ × 900 × 1.80 g/cm³ = 28.4 mg
  Atoms per wafer = 28.4 mg / (10.14 g/mol, C₁H₀.₂₀ average) = 1.40 × 10²¹ C atoms (2.32 mmol)
  n_C = 1.80 g/cm³ / 10.14 g/mol × N_A = 1.069 × 10²³ atoms/cm³ (8.87 × 10²² C atoms/cm³ at 17 at% H)
```

---

## E.2 Web Geometry (Ch. 1, 4, 10, 12)

```
Hexagonal lattice, pitch p:   A_cell = (√3/2) p²;   web (nearest neighbours) = p − CD
  Reference: p = 45 nm: (√3/2) 45² = 1753.8 nm² (+1.1% above 1734; counting uses 1734)
  Web at the top / bow / exit (M1):  45 − 32.1 = 12.9;  45 − 32.8 = 12.2;  45 − 31.0 = 14.0 nm
  M0: bow 34.5 nm → web 10.5 nm (25% thinner than 14 nm; bending stiffness × 0.75³ = 0.42)

Bow and web:   t_web = p − CD_bow;   1 nm of bow on both neighbours takes 1 nm (7%) of the web

Square (4F²) lattice, pitch p:   web (axis) = p − CD;   diagonal web = p√2 − CD
  M3: p = 30 nm, CD 21 nm → axis web 9 nm, diagonal 21.4 nm;  open fraction π 21²/4 / 900 = 38.5%
1d array (F = 14 nm, 6F² cell 1176 nm², pitch 37 nm, exit 26 nm):  web 11 nm; B-ACL 1450 nm → 132:1
```

---

## E.3 Chemical Load and Gas Budget (Ch. 3, 5, 8)

```
Wafer's carbon release (main etch):  1.40 × 10²¹ atoms / 144.4 s = 9.7 × 10¹⁸ s⁻¹
  1 sccm = 4.48 × 10¹⁷ molecules/s  →  21.6 sccm of carbon, leaving as CO
  Oxygen consumed 10.8 sccm O₂-equivalent of 150 sccm O₂ (7.2%) at array efficiency 0.379
  CO budget:  wafer holes 21.6 + bevel ring (1 mm, 9.4 cm²) 2.3 + COS 30 = 53.9 sccm;  wafer share 40%
  COS per wafer:  30 sccm × 144 s + 20 sccm × 11 s + 8 sccm × 7 s + season = 4,608 sccm·s = 3.43 mmol
  Exhaust (20 slm N₂ foreline):  CO 52 sccm → 2,600 ppm;  COS 1,500 ppm;  SO₂ 1,500 ppm
  Array efficiency 0.30 / 0.379 / 0.45 → 8.5 / 10.8 / 12.8 sccm O₂-equivalent;  CO drop 40% at 0.379, 44% at 0.45
```

---

## E.4 Ion-Limited Rate and Yield (Ch. 3, 6)

```
Y(E) = 0.355 (√E − 5)  carbons per ion (E in eV;  E_th 25 eV)
ER₀ = Y Γ_i (duty) / n_C

  M1, 600 eV:  Y = 0.355 (24.49 − 5) = 6.92;   Γ_i = 2.2 × 10¹⁶ cm⁻² s⁻¹ (3.5 mA/cm², on-phase), duty 0.70
               ER₀ = 6.92 × 2.2 × 10¹⁶ × 0.70 / 8.87 × 10²² = 1.20 × 10⁻⁶ cm/s = 12.0 nm/s = 721 nm/min
               (730 nm/min at the fitted value; within 1.2%)
  M0, 800 eV:  Y = 8.27;  Γ_i = 1.5 × 10¹⁶, CW:  ER₀ = 830 nm/min

Energy sweep (M1): 250 / 400 / 600 / 800 / 1000 eV → ER₀ 405 / 562 / 730 / 872 / 997 nm/min
  Each −20 eV near 600 eV lengthens the main etch by 2.5 s and saves 15 nm of top loss
Mean ion energy and set-point:  600 V on 2 MHz bias ≈ 500 eV at 25 mTorr (collisions in the sheath)
```

---

## E.5 Arrhenius and Wafer Temperature (Ch. 3, 6)

```
γ_C(T) = γ_0 exp(−E_a / kT),   E_a = 0.42 eV
  d ln γ/dT = E_a/(k T²):   6.1% per K at 283 K;   7.9% per K at 248 K
  Ratios:  20 → 10 °C  exp(−(0.42/8.617 × 10⁻⁵)(1/283 − 1/293)) = 0.556
           10 → 0 °C   0.532;    10 → −25 °C 0.088;    10 → −40 °C 0.025;   10 → −60 °C 0.0035

Bare lateral rate  v_b = γ_C Γ_O / n_C:
  M1:  6.56 × 10⁻⁴ × 7.3 × 10¹⁸ / 8.87 × 10²² = 5.4 × 10⁻⁵ cm/s = 0.54 nm/s (32 nm/min at 10 °C)
  M0:  1.18 × 10⁻³ × 5.76 × 10¹⁸ / 8.87 × 10²² = 0.77 nm/s (20 °C)
  M2:  0.54 × 0.088 = 0.048 nm/s (−25 °C)

Wafer heating:  ion power 1.04 kW + 15% = 1.2 kW over 706.9 cm² = 1.7 W/cm²
  h_He = 0.07 W/cm² K (15 Torr) → ΔT = 1.7 / 0.07 = 24 K;   ESC −14 °C → 10 °C;   time constant 1.8 s
  A change of 1% of ion power moves the wafer 0.24 K and the bow 0.01 nm (compensated by the ESC)
```

---

## E.6 Passivation Coverage and Bow (Ch. 3, 6, 7, 10)

```
Attenuation length of a species along a hole of diameter d with wall sticking s:
    ℓ = d / √(2 s)         s = d² / (2 ℓ²)
  O:        s_w = 1.0 × 10⁻⁴ → ℓ_O = 31/√(2 × 10⁻⁴) = 2192 ≈ 2200 nm    (A_w = 1/√(2 s_w) = 71 aspect ratios)
  S–C film: s_p = 7.5 × 10⁻⁴ → ℓ_p = 800 nm (low-sticking precursor);   cap-sourced SiOₓ: s_c = 0.13 → ℓ_c = 60 nm

Passivation coverage and lateral rate:
  θ(z) = 1/(1 + x(z)),     x(z) = x₀ e^(−z/ℓ_O) / [ e^(−z/ℓ_p) + c e^(−z/ℓ_c) ]
  v_lat(z) = v_b e^(−z/ℓ_O) x/(1 + x),    wall movement Δ(z) = v_lat(z) t_exp(z)
  CD(z) = CD_cap + 2 Δ(z) − 2 f₀ e^(−(h − z)/λ_f)       (foot: f₀ per side, length λ_f)

M1:  x₀ = 0.005, c = 8;   bow +0.67 nm at z = 370 nm (27% of depth);   θ = 99.35% at the bow
M0:  x₀ = 0.0118, c = 5;  bow +2.0 nm at 450 nm;   θ = 98.2%
Requirement: θ ≥ 99% at the bow depth.   Bow ∝ v_b (T lever: v_b × 0.556 → bow 2.01 → 1.12)
Foot (M1): f₀ = 0.60 nm, λ_f = 49 nm → exit CD 31.0 against 32.1 at the top;   local angle 89.3°
  Local angle of the foot = 90° − atan(f₀/λ_f) = 90° − atan(0.60/49) = 89.30°;  the average over 1350 nm is 89.98°

Sulfur on the wall:  monolayer = 10¹⁵ cm⁻²;  bow zone 0.4 ML, exit 0.1 ML;  6 × 10¹⁸ atoms (0.3 mg) per wafer
  against 3.6 mmol (116 mg) supplied: 0.3% ends on the wall
First-wafer effect:  x₀(n) = x₀ [1 + a e^(−n/2.5)],  a = 1.0 (no season), 0.15 (season)
  bow n = 0, 1, 2, 5, 8:  1.34, 1.12, 0.97, 0.76, 0.70 (no season);  0.77, 0.74, 0.72, 0.68, 0.67 (season)
Cyclic scheme (M2):  x₀ = 0.075 continuous → 0.0265 cyclic (× 0.35);  bow 0.95 → 0.46
```

---

## E.7 ARDE, Clausing and the Width Sensitivity (Ch. 3, 4, 8, 10)

```
ER(A) = ER₀ / (1 + k A + k₂ A²)    A = h/w      (aspect ratio)
Time to depth:  t(h) = [ h + k h²/(2w) + k₂ h³/(3w²) ] / ER₀
Width sensitivity:  ∂h/∂w = (k A²/2 + 2 k₂ A³/3) / (1 + k A + k₂ A²)    (depth difference per nm of CD at fixed time)
χ = 4k/3     (Clausing-limited neutral term)

M1  (k = 0.011, k₂ = 1 × 10⁻⁵, ER₀ = 730 nm/min, w = 31 nm):
  h (nm)       200    500    800    1000   1200   1400
  t (s)        17.0   44.8   75.2   97.1   120.1  144.4
  ER/ER₀       0.933  0.847  0.775  0.732  0.694  0.659   (ER 681 … 481 nm/min)
  A = 45.2 at 1400 nm:  1 + 0.497 + 0.020 = 1.517;   ER/ER₀ = 0.659;   ∂h/∂w = 7.8 nm per nm
M0  (k = 0.016, k₂ = 2 × 10⁻⁵):  main etch 139.1 s;  ER/ER₀ at 1400 = 0.567;  ∂h/∂w = 9.95;  χ = 0.0213
M2  (k = 0.010, k₂ = 8 × 10⁻⁶, w = 26):  main etch 208.5 s;  ER_bottom 349 nm/min;  ∂h/∂w = 11.0

Clausing (long tube):  K ≈ 1/(1 + 3L/(4d)) = 1/(1 + 3A/4):
  A = 10 / 20 / 30 / 43.5:  K = 0.118 / 0.0625 / 0.0426 / 0.0297
Coburn–Winters bottom-to-top flux:  Γ_b/Γ_t = K / (K + β (1 − K))   (β = reaction probability at the bottom)
  Oxygen at the exit:  Γ_O = Γ_O,0 × CW(β = 0.05) × exp(−1350/2200) = 0.371 × 0.541 = 0.20 Γ_O,0
                       = 1.47 × 10¹⁸ cm⁻² s⁻¹, 20.6 times the carbon removal rate at the exit (7.1 × 10¹⁶)
  Ion transmission to the exit ≈ 0.70 including forward reflection
  Exit rate:  1/ER = 1/(f_i ER₀) + 1/Γ_O,exit   (f_i = 0.70) → 0.666 ER₀ (fitted 0.659)
Overetch at the foot:  clear 85 nm at 8.0 nm/s needs 10.6 s;   trigger scatter 5.5 s (3σ) → ST3a 11 s
Ion acceptance:  f_i(exit w) 31/26/20/16/12/10/8 nm = 0.65/0.52/0.35/0.24/0.145/0.10/0.07 (AR 44 … 169)
Mask-open tilt at the edge:  shift = h tan(θ) = 1350 × tan 0.05° = 1.18 nm   (0.03° → 0.7, 0.10° → 2.4 nm)
```

---

## E.8 Cap Erosion and Top Loss (Ch. 11)

```
Cap erosion rate:  v_cap = v_phys + v_chem
  v_phys = 0.166 (√E − √90)/(√600 − √90),    v_chem = 0.071 (COS/30)           (nm/s, M1)
  600 eV, COS 30:  v_phys 0.166 + v_chem 0.071 = 0.237 nm/s;    ACL:SiON = 12.17/0.237 = 51.3
  Facet factor  ρ = 1 + 0.75 × 10⁻³ (E − 400):   1.15 at 600 eV, 1.30 at 800 eV

Ridge life of the cap:   t₀ = (h_cap / v_cap) / ρ = (40/0.237)/1.15 = 146.8 s
  Flat life 40/0.237 = 168.8 s;  the ridge (web top) is exposed earlier by the facet
Time on the exposed web:   x = T_ACL − t₀ = 162.4 − 146.8 = 15.6 s
Web top goes from capped to exposed over   τ_w = (W/2)/v_h = 6.45 / 0.215 = 30.0 s (W = 12.9 nm)
Top loss:   L = ER_top x² / (2 τ_w)     for x ≤ τ_w
            L = ER_top (x − τ_w/2)       for x > τ_w
  ER_top = 12.17 nm/s:  L = 12.17 × 15.6² / 60 = 49.6 ≈ 50 nm        dL/dT = ER_top x/τ_w = 6.3 nm/s
  x = 5 / 10 / 15.6 / 20 / 25 / 30 / 40 s → L = 5 / 20 / 50 / 81 / 127 / 183 / 304 nm
  1 nm of cap = 1/(v_cap ρ) = 3.67 s of clock;  40 → 41 nm takes L from 50 to 29 nm (−21 nm; the tangent at 40 nm is 6.3 × 3.67 = 23)
  1 sccm COS = 1.0% of v_cap = 1.47 s of cap clock = 9.3 nm of loss
Fixes:  cap 42 nm → L 14 nm (+0.6 s);   E 540 eV → L 12.5 nm (+8.0 s);   COS 26 → L 19 nm (bow 0.72)

Shoulder / crest picture (edge loss 190 nm, edge height 1210, margin 94 nm):  see Chapter 11
Cap-limited mask-height ceiling:  40 nm cap → 1353 nm after open;  a thicker mask gains nothing
```

---

## E.9 After-Open Height and Its Statistics (Ch. 2, 11, 15)

```
After-open height  H = h_ACL − L(h_cap, v_cap, T, ...)
Carbon thickness enters twice: a taller film takes 0.125 s per nm longer to open, and the cap gives back
  6.3 nm/s:   net slope = 1 − 6.3 × 0.125 = 0.21 nm of mask per nm of carbon
  ±14 nm of carbon → ± 3.0 nm of mask
Cap terms:  thickness 1.0%, rate 0.8% → ± 11.9 nm of top loss
3σ of H = √(3.0² + 11.9²) = 12.3 nm → lower bound 1350 − 12 = 1338 nm (specification 1330 nm)
Mean specification:  H ≥ 1342 nm (top loss ≤ 58 nm) so that the bound reaches 1330 nm
With feed-forward of H and cap (Chapter 15):  top loss ± 14.3 nm, height ± 9.6 nm, lower bound 1340 nm
```

---

## E.10 Endpoint and Overetch Statistics (Ch. 8)

```
Arrival-time spread (3σ terms, s):  thickness 1.4 (within wafer), rate uniformity 3.6, edge 3.0,
  LCDU tail 2.3, family 1.1
  RSS = √(1.4² + 3.6² + 3.0² + 2.3² + 1.1²) = 5.5 s (3σ),  σ_t = 5.5/3 = 1.84 s;  transition 11 s (±3σ)
Signal:  CO 483.5 nm normalized to Ar 750.4 nm;  1 s average;  arm 120 s;  pre-level 60–110 s;
  post-level 0.60 × pre;  trigger at 50% of the drop, 3 consecutive;  time-out 175 s;  fallback 150 s;  jitter 0.03 s
  Maximum slope 8.7% per s of the total;  EP = median hole = 144.4 s
OE-clear:  5.5 s (3σ scatter) + 5 s (margin) → 11 s, which clears 88 nm at 8.0 nm/s against the 85 nm needed (10.6 s minimum)
Endpoint against timed etch (film rate ± 3%):
  EP:    nominal L 50, fast film 28 (−22), slow film 80 (+30) nm
  Timed (ME fixed 144.4 s, OE 20.3 s, total 164.7 s):  nominal L 66 nm, ± 2 nm with the film;  fails 1348 at 66 nm
Interferometry fails:  penetration depth at 633 nm = 126 nm in ACL (k = 0.40) → the 1350 nm film is opaque
Large-area HV-SEM:  0.17 cm² per wafer, 1 wafer per 5 lots; 13 min at 0.8 cm²/h; 18% precision
COS feed-forward:  ΔCOS = +2.9 ΔH − 0.085 Δh_ACL + 2.5 Δh_cap  (sccm; H in at%, thicknesses in nm)
  H + 1 at% → COS 32.9;  ACL + 14 nm → 28.8;  cap + 0.4 nm → 31.0
  EWMA (λ = 0.3, σ_rr = 0.25 nm) limits ± 0.315 nm;  ΔCHF₃ 0.066 nm/sccm in ST1, ± 5 sccm = ± 0.33 nm
```

---

## E.11 Web Mechanics and Wiggling (Ch. 12)

```
Ligament efficiency:  η = (p − d)/p;   effective modulus  E* = η E
  nominal  14/45 = 0.311 → 23.3 GPa;  M1 (bow, 12.2/45 = 0.271) → 20.3 GPa;  M0 0.233 → 17.5 GPa;
  M2 (B-ACL, 105 GPa) 0.257 → 27.0 GPa
Web bending stress per MPa of applied stress:  2.6 / 3.4 / 4.6 for t = 14 / 12.2 / 10.5 nm;  buckling σcr ~ 50 GPa
Stiffness of a web goes as t³:  (10.5/14)³ = 0.42
Edge relaxation of film stress:   ε = σ (1 − ν) / E:   ACL 300 MPa × 0.75 / 75 GPa = 0.30%;   B-ACL 0.18%
  u₀ = ε × 0.7 h = 0.0030 × 0.7 × 1350 = 2.8 nm (B-ACL, 1450 nm: 1.8 nm);   decay length h/2 = 15 rows (19.6)
  u(n) at rows 1 / 3 / 5 / 10 / 15 / 30:  2.65 / 2.32 / 2.03 / 1.46 / 1.04 / 0.38 nm;  exit shift u/2
  Lean 0.11° at row 1;  80% litho compensation → residual 0.27 / 0.23 / 0.15 / 0.04 nm at rows 1 / 3 / 10 / 30
  Dummy rows do not cure it (stress relaxation reaches 15 rows)
Ellipticity near the array edge:  e(n) = 0.012 + 0.015 e^(−(n − 1)/3):  row 1 0.027, row 10 0.013 (spec ≤ 0.03)
Wiggle (bimorph) 3σ:  M1 0.70 nm;  M0 1.07 ✗ (limit 1.0);  M2 B-ACL ≤ 0.67;  M3 0.90 ✗ (limit 0.67)
Wafer bow:  film sag 261 µm; the open removes 16.5% of the force → −43 µm (261 → 218 before backside films)
```

---

## E.12 Defect Statistics (Ch. 4, 13)

```
Budget:  not-open 3.0 × 10⁻⁹ per hole = 51.5 per die (mask-open share of 8 × 10⁻⁹ = 137 per die)
Merging (web 12.2 nm, σ_t = 0.54 nm; 3 nm = 17σ):  2 × 10⁻¹⁰ per hole (M1);  M0 (10.5 nm, 14σ) 4 × 10⁻¹⁰
SiON overetch survivors:  fraction ≈ e^(−0.5 t_OE) for t_OE seconds beyond the clear (Chapter 13)
Pinch-off tail:  P(narrowing > δ) = P₀ exp(−δ/Δ₀),   P₀ = 10⁻³,  δ_c = 31 − 12 = 19 nm (critical web 12 nm)
  M1:  Δ₀ = 1.34 nm → 10⁻³ e^(−19/1.34) = 7.0 × 10⁻¹⁰;   M0 Δ₀ = 1.42 → 1.5 × 10⁻⁹
  d ln p/dΔ₀ = 19/Δ₀² = 10.6 per nm;   Δ₀ × 0.90 / 0.95 / 1.05 / 1.10 → p × 0.21 / 0.47 / 2.0 / 3.6;  −4.9% halves p
Particle footprint:  killer adder 81 nm;  adders ≥ 30 nm  1.5 / 2.5 / 5 / 12 / 45 per wafer at wall SiOₓ 20 / 50 / 100 / 150 / 200 nm
Wall film growth:  SiON cap 38.5 nm × 590 cm² = 1.6 × 10²⁰ atoms; 60% to walls → 1.9 nm per wafer per 8000 cm²
  SiOₓ at wafers 0 / 10 / 25 / 50 / 75:  0 / 19 / 46 / 93 / 140 nm;  limit 10 adders at 140 nm (75 wafers)
Moisture:  θ_w(t) = 0.9 (1 − e^(−t/8 h));  1 / 4 / 8 / 12 / 24 h → 0.06 / 0.21 / 0.35 / 0.42 / 0.52 mg;
  nitrogen FOUP (τ = 40 h):  0.02 / 0.09 / 0.16 / 0.23 / 0.41 mg;   degas −90%
Wetting:  Laplace pressure P = 4 γ cos θ / d:  d = 31 nm, γ = 0.072 N/m:  θ = 95° → −0.8 MPa;  60° → +4.6;  45° → +6.6 MPa
```

---

## E.13 Placement Budget (Ch. 4, 10, 12)

```
Placement budget (mask-open shift + tilt):  1.5 nm;  M1 uses 1.4 nm (RSS)
  Tilt:  0.05° at r = 147 mm → 1.2 nm;   ring tilt 0.03° new + 0.08° per 100 µm of wear → 25 µm of wear reaches 0.05°
  Ring life:  25 µm / 0.12 µm per RF-h = 208 RF-h = 4,070 wafers at 0.0512 RF-h per wafer
  Radial exit CD relative to centre, r = 0 / 50 / 100 / 130 / 147 mm:  0 / −0.05 / −0.10 / +0.12 / +0.40 nm
  Array-edge offset:  0.55 e^(−(n − 1)/1.4) nm at row n:  0.55 / 0.27 / 0.13 / 0.07 / 0.03; two dummy rows → row 3 (0.13 nm)
    area cost of 2 dummy rows: 0.8% (1000 × 1000 cells), 27% (32 × 32)
```

---

## E.14 Throughput, Fleet and Cost (Ch. 5, 16)

```
Throughput:  plasma 184 s + wafer handling and cleans;  66.1 wafers per hour (platform 65.2 with cleans)
  Cleans:  waferless 14 s/wafer;  NF₃ 60 s per 25 wafers (2.4 s per wafer);  season 12 s per 25 wafers (0.5 s per wafer)
Fleet at 85% utilization:  wafers per chamber per month = 730 h × 3600 × 0.85 / cycle time
  M1:  2,233,800 s / 218 s = 10,247;    150,000 / 10,247 = 14.6 chambers → 4 four-chamber platforms
  M0 215 s: 10,390 (14.4);  M2 299 s: 7,471 (20.1 → 6 platforms);  M3 314 s: 7,114 (21.1 → 6 platforms)
Fixed cost per wafer:  (capital charge 24.8% + maintenance 6%) × $9.0 M + facility $0.15 M = $2.92 M per year
  per platform;  wafers per platform per year = 4 × 10,247 × 12 = 491,856 → $5.94 per wafer
Cost of a second of chamber time (M1):  $7.90 / 218 s = $0.0362
Module (M1):  tool $5.94 + consumables $1.96 + deposition $6.10 + metrology $1.10 = $15.1
Break-even yield gain:  ΔC / value of wafer = $0.73 / $1,400 = 0.052%  (yield gain 0.48%: nine times)
Consumables:  Si edge ring $1,500 / 4,070 wafers = $0.37;  upper electrode $12,000 / 29,300 = $0.41;  other $0.27
  → parts $1.05 per wafer;  abatement $0.30;  COS 3.4 mmol per wafer = 31 kg per month at 150,000 wafers
```

---

**Appendix E Version:** 1.0  
**Last Updated:** 2026-10-05
