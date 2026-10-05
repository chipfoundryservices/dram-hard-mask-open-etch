# Appendix B: Chemistry & Thermochemistry Data

Thermodynamic and kinetic data used in Chapters 3, 7, 9, 13, and 14. Enthalpies are standard values at 298 K, rounded; kinetic parameters are model values calibrated to the reference process. All are illustrative.

---

## B.1 Standard Enthalpies of Formation

```
Species          State   ΔH_f (kJ/mol)        Species          State   ΔH_f (kJ/mol)
─────────────────────────────────────────────────────────────────────────────────────────
O                g       +249                 CO               g       −111
H                g       +218                 CO₂              g       −394
N                g       +473                 CH₄              g       −75
S                g       +277                 HCN              g       +135
SO₂              g       −297                 (CN)₂            g       +309
COS              g       ≈ −142               CS₂              g       +117
BF₃              g       −1137                B₂O₃             s       −1274
SiO₂             s       −910                 SiF₄             g       −1615
```

---

## B.2 Reactions

```
Reaction                                           ΔH (kJ per mol of carbon)
────────────────────────────────────────────────────────────────────────────────────
C(s) + O → CO                                      −360
C(s) + 2 O → CO₂                                   −892
CO + O → CO₂                                       −532
C(s) + H + N → HCN                                 −556
C(s) + 4 H → CH₄                                   −947
2 C(s) + 2 N → (CN)₂                               −636
S + O → SO                                         −521
C(s) + 2 S → CS₂                                   −437
```

Every route to carbon removal is exothermic by hundreds of kilojoules; selectivity and sidewall protection come from kinetics and volatility, not thermodynamics (Chapter 3).

---

## B.3 Bond Energies and Product Volatility

```
Bond (kJ/mol):  C–C 346;  C=C 602;  C–H 411;  C–O 358;  C≡O 1076;  C–S 272;  C–N 305;  S–O 522;
                Si–O 800;  B–O 806;  B–F 613 (mean in BF₃);  Si–Cl 381

Product volatility at 10 °C (wall):
  CO, CO₂, CH₄               gases                       the products of the oxygen and hydrogen routes
  HCN (b.p. 26 °C), (CN)₂    gases / volatile            N₂/H₂ chemistry
  CS₂ (b.p. 46 °C)           liquid; pumped              from COS
  SO₂ (b.p. −10 °C)          gas                         the sulfur film's oxidation product
  BF₃ (b.p. −100 °C)         gas                         the route for boron
  B₂O₃ (m.p. 450 °C)         involatile                  stays on the wall and floor
  SiOₓ                       involatile                  the best passivant; also the micromask
  S₈ (vapour pressure ≈ 10⁻⁵ Pa at 20 °C)   involatile at 10 °C; removed by O as SO₂
```

---

## B.4 Kinetic Parameters of the Model

```
Parameter                                    M1                M0                M2 / M3
────────────────────────────────────────────────────────────────────────────────────────────────────
Carbon density n_C (cm⁻³)                    8.87 × 10²² (ρ 1.8 g/cm³, H 17 at%)
Ion flux Γ_i, on-phase (cm⁻² s⁻¹)            2.2 × 10¹⁶        1.5 × 10¹⁶        —
Duty                                         0.70              1.0 (CW)          0.70
Yield Y(E) = 0.355 (√E − 5), E in eV         6.92 at 600 eV    8.27 at 800 eV    6.92
Oxygen flux Γ_O,0 (cm⁻² s⁻¹)                 7.3 × 10¹⁸        5.8 × 10¹⁸        7.3 × 10¹⁸
O reaction probability γ_C (bare carbon)     6.6 × 10⁻⁴ (10 °C) 1.2 × 10⁻³ (20 °C)  6.6 × 10⁻⁴ × 0.088 (−25 °C)
Activation energy of γ_C                     0.42 eV
Bare lateral rate v_b = γ Γ/n_C (nm/s)       0.54              0.77              0.048
Passivation parameters x₀, c                 0.005, 8          0.0118, 5         0.0265 (cyclic), 8
Decay lengths (nm): ℓ_O / ℓ_p / ℓ_c           2200/800/60       1550/600/80       d = 26: 1838/671/50
  corresponding sticking s_O / s_p / s_c     1.0×10⁻⁴ / 7.5×10⁻⁴ / 0.13   2×10⁻⁴ / 1.3×10⁻³ / 0.075
Foot (f₀ per side, λ_f)                      0.60 nm, 49 nm    0.88 nm, 56 nm    0.56 nm, 46 nm
ARDE k, k₂ (ER = ER₀/(1 + kA + k₂A²))        0.011, 1×10⁻⁵     0.016, 2×10⁻⁵     0.010, 8×10⁻⁶
ER₀ (nm/min, time-averaged)                  730               830               560
χ = 4k/3                                     0.0147            0.0213            0.0133
```

```
Relations:
  ℓ = d/√(2 s)                       s = d²/(2 ℓ²)                  d = hole diameter (31 nm)
  Passivation coverage θ(z) = 1/(1 + x(z)),   x(z) = x₀ e^(−z/ℓ_O) / [e^(−z/ℓ_p) + c e^(−z/ℓ_c)]
  Lateral rate v_lat(z) = v_b e^(−z/ℓ_O) x/(1 + x);   wall movement Δ(z) = v_lat t_exp(z)
  Wall-loss attenuation of the neutral flux at the exit: exp(−A/A_w), A_w = 1/√(2 s_w)  (s_w = 10⁻⁴: 0.54 at A = 43.5)
```

---

## B.5 Arrhenius and Energy Factors

```
Temperature factor of γ_C (E_a = 0.42 eV), relative to the starting point:
  20 → 10 °C    × 0.556        10 → 0 °C     × 0.532       10 → −25 °C    × 0.088
  10 → −40 °C   × 0.025        10 → −60 °C   × 0.0035      −25 → −60 °C   × 0.040
  dlnγ/dT at 283 K = E_a/(kT²) = 6.1% per K

Energy factors (relative to 600 eV; M1 conditions):
  E (eV)               250     400     600     800     1000
  Y                    3.84    5.32    6.92    8.27    9.45
  ER₀ (nm/min)         405     562     730     872     997
  v_cap (nm/s)         0.141   0.187   0.237   0.279   0.316
  ACL:SiON             47.9    50.0    51.3    52.1    52.6
  Facet factor ρ       1.00    1.00    1.15    1.30    1.45
```

---

## B.6 Conversions

```
  1 sccm = 4.48 × 10¹⁷ molecules/s = 1 cm³/min at STP
  Wafer's carbon release (M1 main etch)   1.40 × 10²¹ atoms / 144.4 s = 9.7 × 10¹⁸ s⁻¹ = 21.6 sccm
  Oxygen consumed (as CO)                 10.8 sccm O₂-equivalent of 150 sccm (7.2%)
  COS supplied                            4,608 sccm·s = 76.8 cm³ = 3.43 mmol per wafer
  Wafer area 706.9 cm²; array area per die 0.298 cm² (1b); die 0.785 cm²; 900 dies
  1 monolayer = 10¹⁵ cm⁻²;   wall area per wafer 2.03 m² (31 nm × 1350 nm per hole)
```

---

**Appendix B Version:** 1.0  
**Last Updated:** 2026-10-05
