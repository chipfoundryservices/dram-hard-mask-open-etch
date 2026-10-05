# Appendix A: Material Properties

Properties of the carbon masks, the cap, the films around them, the chamber materials, the wall films, and the process gases used in this book. Values are representative of the films described in Chapter 2; bulk values are given where a film value is not well defined. All values are illustrative.

---

## A.1 Carbon Mask Films

```
Property                    PECVD ACL    HD-ACL      SOC         B-ACL        W-ACL
                            (reference)  (550 °C)    (spin-on)   (B 40 at%)   (W 10 at%)
────────────────────────────────────────────────────────────────────────────────────────────
Reference use               1b mask      taller      comparison  1d mask      extreme mask
                            (Book #29)   masks       only        (Book #31)
Deposition                  PECVD,       PECVD,      spin, bake  PECVD with   PECVD / PVD
                            C₃H₆, 450 °C 550 °C      400 °C      B₂H₆ or BCl₃
Density (g/cm³)             1.80         1.95        1.35        2.05         2.60
Hydrogen (at%)              17           12          35          8            10
Young's modulus (GPa)       75           100         12          105          130
Stress (MPa)                −300         −500        +20         −250         −450
Extinction coefficient k    0.40 (633)   0.45 (633)  0.05 (633)  0.50 (633)   0.9 (633)
  at 1550 nm                0.05         0.06        0.01        0.07         0.20
Water contact angle         95°          98°         75°         90°          85°
Rate vs ACL (O₂/COS, M1)    1.00         0.72        2.74        0.77 (F)     0.45
Blanket selectivity to      5.5          7           2.5         8–9          11–12
 oxide (mold etch)
Effective selectivity       2.3–2.6      —           —           3.5          4.8
 (Book #31)
Open chemistry              O₂/COS       O₂/COS,     O₂/N₂       O₂/COS +     O₂ + Cl₂ /
                                         higher bias             CF₄ 3%       CF₄
Strip                       O₂ ash       O₂ ash      O₂ ash      O₂ ash, F    wet + dry
```

```
Reference ACL, after the open (M1):
  Thickness (mean; 3σ lower bound)   1350 nm; 1340 nm (Chapter 15 policy)
  Top loss                           50 nm mean; shoulder 190 nm below the 1400 nm crest
  Exit CD / top CD / bow             31.0 / 32.1 / 0.67 nm
  Mean web / minimum web             14.0 / 12.2 nm
  Sulfur on the wall                 0.4 monolayer at the bow zone, 0.1 at the exit (≈ 10¹⁵ cm⁻² per monolayer)
  Wall area per wafer                2.03 m²
```

```
Rate model for undoped films (O₂ plasma):  R/R_ACL = [1 + 0.03 (H − 17)] × (1.8/ρ)²   (H in at%, ρ in g/cm³)
  H ± 1 at% → ± 3.0% in rate;  deposition temperature: H falls 0.08 at% per °C (20 at% at 450 °C, 12 at% at 550 °C)
```

---

## A.2 Cap, Underlayer, Resist, Support

```
Property                  SiON cap      BARC / UL   ArF-i resist   Poly-Si cap   Top SiN support
──────────────────────────────────────────────────────────────────────────────────────────────────
Reference use             ACL mask      under       pattern        hybrid cap    stop of the open
Thickness (nm)            40 (60 in     25          80 (40, EUV)   25            120
                          M2; 42 M1-c)
Deposition                PECVD 400 °C  spin        spin           LPCVD / PECVD PECVD, low H
Density (g/cm³)           2.3           1.3         1.2            2.33          2.95
Refractive index (193)    1.90          1.70        1.70           —             —
Extinction coeff. (193)   0.40          0.30        0.02           —             —
Stress (MPa)              −50           —           —              ±200          +250
Etch in CF₄/CHF₃ (nm/min) 200           190         150            —             —
Etch in O₂/COS 600 eV     0.237 nm/s    fast        fast           0.08–0.12 nm/s  8 nm/min
 (v_cap = v_phys + v_chem)
ACL:cap blanket           51 (M1)       —           —              ≥ 100 (target) —
                          64 (M0), 38 (M2)
```

```
SiON cap erosion (M1, 600 eV, duty 0.70, COS 30 sccm):
  v_cap = v_phys + v_chem = 0.166 (√E − √90)/(√600 − √90) + 0.071 (COS/30)    nm/s
  Facet factor ρ = 1 + 0.75 × 10⁻³ (E − 400)   (E > 400 eV; 1.15 at 600 eV, 1.30 at 800 eV)
  M0 (CW, 800 eV, COS 6): v_cap 0.216 nm/s, ρ 1.30        M2 (B-ACL, F 3%): v_cap 0.245 nm/s, ρ 1.15
```

---

## A.3 The Mold Beneath the Mask

```
Reference mold (Book #29):
  Top SiN support     120 nm   PECVD low-H       stop of the open
  Upper PE-TEOS       650 nm
  Middle SiN support   50 nm
  Lower BPSG          760 nm
  Bottom SiN stop      20 nm   LPCVD
  Total               1.60 µm
  ACL consumption in the mold etch (Book #29)      576 nm in 305 s (+ 40 nm facet allowance)
  1d mold (Book #31)                                2.10 µm; B-ACL consumption 600 nm
  4F² mold (Book #31)                               1.82 µm; hole aspect ratio ≈ 100
```

---

## A.4 Chamber Materials

```
Material                    Use                          Behaviour in the M1 plasma
─────────────────────────────────────────────────────────────────────────────────────────────────
Silicon                     upper electrode, edge ring   sputters slowly; oxidizes at once; source of SiOₓ
                                                         passivant; wear 0.12 µm per RF-hour (ring)
Silicon carbide             alternative ring             lower SiOₓ supply; slower wear
Quartz                      cover ring, liners           inert; SiOₓ film adherent
Aluminium oxide / Y₂O₃      chamber liner                inert to O₂, COS; attacked by NF₃ clean slowly
Anodized aluminium          walls                        covered by wall film
Alumina ESC surface         wafer chuck                  helium backside 15 Torr; zones −14 °C
```

---

## A.5 Wall Films

```
Film             Source                          Growth (per wafer, 8000 cm² wall)   Removed by
────────────────────────────────────────────────────────────────────────────────────────────
SiOₓ             SiON cap erosion; Si parts      1.9 nm                              NF₃ clean (every 25 wafers)
Carbon-rich      redeposited carbon              0.3 nm                              O₂/Ar waferless clean (every wafer)
S–C, SOₓ         COS                             9 nm, loosely bound                 O₂ (as SO₂)
Particle adders ≥ 30 nm: 1.5 / 2.5 / 5 / 12 / 45 per wafer at SiOₓ 20 / 50 / 100 / 150 / 200 nm
```

---

## A.6 Process Gases

```
Gas      Formula     M (g/mol)   Boiling point (°C)   Role                         Hazard
────────────────────────────────────────────────────────────────────────────────────────────────────
Oxygen   O₂          32.0        −183                 carbon removal               oxidizer
COS      OCS         60.1        −50                  passivant (S–C); CO source   toxic, flammable
SO₂      SO₂         64.1        −10                  passivant (cyclic deposition) toxic, corrosive
Nitrogen N₂          28.0        −196                 diluent; N₂/H₂ chemistry     asphyxiant
Argon    Ar          39.9        −186                 diluent; actinometer         asphyxiant
CF₄      CF₄         88.0        −128                 SiON open; boron removal     greenhouse gas
CHF₃     CHF₃        70.0        −82                  SiON open (taper)            —
NF₃      NF₃         71.0        −129                 wall clean                   toxic oxidizer
CO       CO          28.0        −191                 product                      toxic, flammable
CO₂      CO₂         44.0        −78 (sublimes)       product                      —
SiCl₄    SiCl₄       169.9       57                   Si passivant (alternative)   corrosive
Cl₂, HBr Cl₂, HBr    71.0, 80.9  −34, −67             Si cap open; W-ACL          toxic, corrosive
BCl₃     BCl₃        117.2       12.5                 B-ACL alternative            toxic, corrosive
```

---

## A.7 Water and Wetting

```
Water on the walls:
  Monolayer (10¹⁵ molecules/cm²) on 2.03 m²     2.0 × 10¹⁹ molecules = 0.61 mg
  Hole volume                                   1.0 × 10⁻¹⁵ cm³; 16 mg per wafer if every hole filled
  Contact angle: ACL 95°; S–C wall 100°; after O₂ plasma 45°
  Laplace pressure, d = 31 nm, γ = 0.072 N/m:   θ = 95° −0.8 MPa;  θ = 60° +4.6 MPa;  θ = 45° +6.6 MPa
```

---

**Appendix A Version:** 1.0  
**Last Updated:** 2026-10-05
