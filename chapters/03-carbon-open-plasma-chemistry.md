# Chapter 3: Plasma Chemistry of the Carbon Open

## Overview

Cutting carbon with oxygen is simple chemistry and difficult engineering. The bond energies are favourable at every step, the products are gases, and nothing grows on the wafer to slow the reaction. That is the difficulty. A fluorocarbon etch protects its own sidewall with the polymer it grows. An oxygen etch grows nothing, and the same atom that cuts the bottom of the hole cuts its wall. In M1, bare carbon at 10 °C is attacked at the top of the hole at 0.54 nm per second. Over the 162 s of the open that would remove 88 nm from each side of every hole, in a hole 31 nm wide. The sidewall survives because the plasma deposits something on it faster than the oxygen removes it.

This chapter builds the chemistry of the carbon open in the order the wafer meets it: the bonds and the volatility rule that decide what can be a product and what can be a passivant; the ion-assisted oxidation that cuts the bottom; the radical attack on the bare wall; a **passivation film model** that predicts the bow from five parameters; the transport of oxygen and ions down a 44:1 tube, which sets the aspect-ratio-dependent rate; the selectivity to the cap and to the nitride stop; and the hydrogen alternative. The model of Section 3.4 is the one the rest of the book uses.

**Learning Objectives:**
- Compute reaction enthalpies for carbon removal and for the formation of passivants
- State the volatility rule and use it to separate products from passivants
- Compute the etch rate of carbon from ion flux, yield, and energy
- Compute the bare lateral rate of the wall from the radical flux and reaction probability
- Use the passivation model to predict coverage, lateral rate, and bow as a function of depth
- Relate sticking probability to the decay length of a species in a 31 nm tube
- Compute ARDE, time to depth, and the depth sensitivity to CD for M0 and M1
- Compare the oxygen and hydrogen routes for the carbon open

---

## 3.1 Bonds, Products & the Volatility Rule

### 3.1.1 Reaction Enthalpies

```
Formation enthalpies (kJ/mol, gas unless noted; approximate):
  O +249    H +218    N +473    S +277    CO −111    CO₂ −394
  HCN +135  CH₄ −75   C₂N₂ +309  SO₂ −297  COS ≈ −142

Carbon removal (per mole of carbon, from C(s) and atoms):
  C(s) + O       → CO              −360
  C(s) + 2 O     → CO₂             −892
  CO + O         → CO₂             −532
  C(s) + H + N   → HCN             −556
  C(s) + 4 H     → CH₄             −947
  2 C(s) + 2 N   → C₂N₂            −636
  S + O          → SO              −521
```

Every route is exothermic by hundreds of kilojoules. There is no thermodynamic barrier to etching carbon with oxygen, nitrogen, or hydrogen atoms, and no thermodynamic protection for a wall that sees them. Selectivity and sidewall protection must come from kinetics (energy thresholds, sticking probabilities) and from products that do not leave.

### 3.1.2 The Volatility Rule

```
Products that must leave, and films that must stay (wall at 10 °C):

  Role           Species                  Volatility at 10 °C           Remarks
  ─────────────────────────────────────────────────────────────────────────────────────
  Product        CO, CO₂                  gases (CO₂ sublimes −78 °C)   the main products
  Product        HCN, C₂N₂, CH₄           gases (HCN bp 26 °C)          N₂/H₂ chemistry
  Product        CS₂                      liquid, bp 46 °C              pumped from the chamber
  Passivant      SiOₓ (from SiON, SiCl₄)  involatile                    best film; harms later steps
  Passivant      S / S–C films (from COS) vapour pressure ≈ 10⁻⁵ Pa    removed by O as SO₂, so a
                                          at 20 °C                      competition, not a seal
  Passivant      C–N films (from N₂)      involatile as a polymer       must not close the hole
  Product        BF₃ (B-ACL with CF₄)     gas                           B₂O₃ is involatile (Chapter 14)
```

The rule is the one a fluorocarbon etch obeys in reverse: **the species that remove the film must be volatile, and the species that protect the wall must not be.** A passivant that oxygen converts into a gas (sulfur to SO₂) is a sacrificial layer, thinned continuously, and must be resupplied faster than it is consumed. That competition is the model of Section 3.4.

---

## 3.2 Ion-Assisted Oxidation: The Bottom of the Hole

### 3.2.1 A Yield Model

At the bottom of the hole the carbon is removed by an ion-assisted reaction: an energetic ion breaks bonds in a surface layer on which atomic oxygen is adsorbed, and the carbon leaves as CO. The rate is the ion flux times a yield per ion, with the usual square-root dependence on energy above a threshold:

```
Rate:    ER₀ = Γ_i × d × Y(E) / n_C                        (flux in cm⁻² s⁻¹; n_C = 8.87 × 10²² cm⁻³)
Yield:   Y(E) = 0.355 (√E − √E_th),    E_th = 25 eV        (C atoms per ion; E in eV)

M1:  Γ_i = 2.2 × 10¹⁶ cm⁻² s⁻¹ (3.5 mA/cm²), duty d = 0.70, E = 600 eV
     Y(600) = 0.355 × (24.49 − 5) = 6.92
     ER₀ = 2.2 × 10¹⁶ × 0.70 × 6.92 / 8.87 × 10²² = 1.20 × 10⁻⁶ cm/s = 12.0 nm/s = 721 nm/min   (fitted: 730)
M0:  Γ_i = 1.5 × 10¹⁶ cm⁻² s⁻¹ (2.4 mA/cm²), CW, E = 800 eV
     Y(800) = 8.27;  ER₀ = 838 nm/min   (fitted: 830)
```

M0 is run CW at lower source power, so it has less ion flux and more ion energy. M1 recovers the flux with a 50% higher source power and gives some of it back in the duty cycle. About seven carbon atoms leave per ion at 600 eV: the ion is a trigger, not a reagent, and the oxygen arrives separately.

```
Energy dependence (M1 conditions, time-averaged):
  E (eV)            250    400    600    800    1000
  Y (C per ion)     3.84   5.32   6.92   8.27   9.45
  ER₀ (nm/min)      405    562    730    872    997
```

Chapter 6 uses this table with the cap's response to choose the energy.

---

## 3.3 Radicals and the Bare Wall

### 3.3.1 The Lateral Rate

Atomic oxygen also reaches the wall of the hole. The bare lateral rate is the radical flux times the reaction probability of oxygen on the carbon surface, divided by the carbon density:

```
v_b = γ_C Γ_O / n_C

M1 (10 °C):  Γ_O = 7.3 × 10¹⁸ cm⁻² s⁻¹,  γ_C = 6.6 × 10⁻⁴
             v_b = 6.6 × 10⁻⁴ × 7.3 × 10¹⁸ / 8.87 × 10²² = 5.4 × 10⁻⁸ cm/s = 0.54 nm/s
M0 (20 °C):  Γ_O = 5.8 × 10¹⁸ cm⁻² s⁻¹,  γ_C = 1.2 × 10⁻³
             v_b = 0.77 nm/s
```

M1 has more oxygen than M0 (more source power), and still attacks a bare wall less, because the reaction probability on carbon is thermally activated:

```
γ_C ∝ exp(−E_a / kT),  E_a = 0.42 eV (illustrative):
  20 → 10 °C   × 0.556        10 → 0 °C   × 0.532
  10 → −25 °C  × 0.088        10 → −40 °C × 0.025
Check: 0.556 × (7.3 / 5.8) = 0.70 = 0.54 / 0.77
```

The same exponential is why Chapter 14's wafer at −25 °C attacks bare carbon eleven times more slowly. Cooling the wafer reduces the lateral attack, but also, to a smaller degree, the vertical rate (the ion-driven term is not activated).

### 3.3.2 How Much Protection Is Needed

```
Budget for a bow of 0.7 nm (0.35 nm per side) accumulated over ≈ 130 s of exposure at the bow depth:
  required lateral rate        0.35 / 130 = 0.0027 nm/s
  as a fraction of bare        0.0027 / 0.54 = 0.5%
  with the oxygen's decay      the oxygen flux at 370 nm is 0.85 of its top value (e^(−370/2200)),
                               so the bare fraction allowed is 0.0027 / (0.54 × 0.85) = 0.6%
  required coverage            ≥ 99.4% in the bow zone;  ≥ 99% over the whole depth
```

**The wall must be more than 99% covered by something that oxygen does not remove.** That is the design target of every passivation scheme in this book, and the reason the bow, which looks like a small geometric error, is a measurement of coverage to a part in a hundred.

---

## 3.4 The Passivation Film Model

### 3.4.1 Supply, Removal, and Coverage

Let θ(z) be the fraction of the wall at depth z that is covered by a passivant. Passivant arrives at a rate Φ_p(z) and is removed by oxygen at a rate k_r(z), which is proportional to the oxygen flux at the wall. In steady state:

```
θ(z) = Φ_p / (Φ_p + k_r) = 1 / (1 + x),        x(z) = k_r(z) / Φ_p(z)
```

Both the oxygen flux and the passivant flux decay with depth, each as exp(−z/ℓ) with a decay length set by the species' sticking probability s on the wall of a tube of diameter d:

```
ℓ = d / √(2 s)           (d = 31 nm)          s = d² / (2 ℓ²)

  s        10⁻⁴   3 × 10⁻⁴   10⁻³   10⁻²   0.1   0.5
  ℓ (nm)   2192   1266       693    219    69    31
```

Three populations matter:

```
Species                         Sticking s     Decay length ℓ          Source
──────────────────────────────────────────────────────────────────────────────────────
O (loss to the passivated wall) 1.0 × 10⁻⁴     ℓ_O = 2200 nm (M1)      plasma;  2.0 × 10⁻⁴, 1550 nm (M0)
Low-sticking passivant (S–C,    7.5 × 10⁻⁴     ℓ_p = 800 nm (M1)       COS in the gas phase;
 SOₓ from COS and O₂)                                                  1.3 × 10⁻³, 600 nm (M0)
Cap-sourced SiOₓ                0.13           ℓ_c = 60 nm             sputtered from the SiON cap;
                                                                       0.075, 80 nm (M0)
```

Combining them:

```
x(z) = x₀ · e^(−z/ℓ_O) / [ e^(−z/ℓ_p) + c · e^(−z/ℓ_c) ]

Lateral rate:   v_lat(z) = v_b · e^(−z/ℓ_O) · x/(1 + x)
Wall movement:  Δ(z) = v_lat(z) × t_exp(z)        (t_exp: time the wall at depth z has been exposed)
```

The parameter x₀ is the ratio of removal to supply far from the cap; c is the strength of the cap source relative to the low-sticking supply at the top.

```
Parameters (reference):                x₀        ℓ_O     ℓ_p    c    ℓ_c
  M0   CW, 20 °C, COS/O₂ = 0.03        0.0118    1550    600    5    80
  M1   pulsed, 10 °C, COS/O₂ = 0.20    0.0050    2200    800    8    60
```

### 3.4.2 What the Model Says

```
M1 wall state versus depth (θ, lateral rate, exposure, wall movement per side):
  z (nm)    θ (%)    v_lat (nm/s)   t_exp (s)   Δ per side (nm)   CD (nm)
  ───────────────────────────────────────────────────────────────────────
     0      99.94      0.0003         162          0.05             32.1
   100      99.80      0.0010         154          0.16             32.3
   200      99.57      0.0021         145          0.31             32.6
   370      99.35      0.0030         130          0.39             32.8   ← bow
   500      99.26      0.0032         118          0.37             32.8
   750      99.10      0.0035          93          0.32             32.6
  1000      98.90      0.0038          65          0.25             32.5
  1250      98.67      0.0041          36          0.15             32.1
  1350      98.56      0.0042          24          0.10             31.0 (with foot)
```

Three things follow:

1. **The top is narrow because the cap protects it.** Within 100 nm of the cap the SiOₓ that sputters from the SiON coats the wall (s = 0.13: it lands where it is born). The first 100 nm are covered to 99.8% and are the narrowest part of the hole (32.1 nm at the top, 0.1 nm above the cap CD).

2. **The bow is where two curves cross.** The lateral rate grows with depth, because the cap source has died away and x has risen. The exposure time falls with depth, because the front passed that depth later. Their product peaks at 370 nm, 27% of the way down. Everything above it was protected by the cap, everything below it was exposed for too short a time.

3. **The bottom closes by redeposition, not by passivation.** The coverage at the exit is lower than anywhere else (98.6%) but the wall has only been exposed for 24 s. The narrowing of the last 50 nm (0.8 nm in CD), the foot, is a separate term (a film of sputtered and redeposited fragments that thickens close to the etch front) with an exponential form: 0.60 nm per side at the exit with a decay length of 49 nm. Its slope at the exit, tan⁻¹(0.60/49), is the **89.3°** of Book #29.

For M0 the numbers are worse at every depth: coverage at the bow depth (450 nm) is 98.2%, not 99.3%, the lateral rate is 3.3 times higher, and the bow is 2.0 nm instead of 0.7 nm (a maximum CD of 34.5 nm, a minimum web of 10.5 nm).

### 3.4.3 Sensitivities

```
Bow response of M1 (0.67 nm) to its parameters (illustrative, from the model):
  x₀  × 1.2 / × 0.8 / × 2.0           bow 0.81 / 0.54 / 1.34 nm     (bow ∝ x₀)
  ℓ_p  800 → 640 / → 960 nm           0.77 / 0.62 nm
  c    8 → 6 / → 10                   0.65 / 0.69 nm                (the cap source matters only at the top)
  v_b  × 1.1 / × 0.9                  0.74 / 0.61 nm
  Overetch ± 3 s                      ± 0.02 nm
  O wall loss × 2 (ℓ_O 1600)          0.59 nm                       (a dirtier wall depletes the oxygen)
```

The bow is proportional to x₀, the ratio of passivant removal to supply. Every control in Chapters 5 to 7 acts on it: the COS flow raises the supply, the pulse gives the film time to recover, the cold chuck cuts the removal. The one parameter that does **not** matter is the overetch: by the time it runs, the wall that was going to bow already has.

---

## 3.5 Transport and ARDE

### 3.5.1 The Tube

Oxygen has to reach the bottom of a 31 nm hole 1350 nm deep. The transmission of a long tube is the Clausing factor, K ≈ 4d/(3L) = 1/(1 + 3A/4), and the flux that reaches a reactive bottom is given by the Coburn–Winters expression (Book #31, Chapter 4):

```
Γ_bottom / Γ_top = K / [K + β (1 − K)]  ×  exp(−A/A_w),     A_w = 1/√(2 s_w)

At A = 43.5 (K = 0.0297), β = 0.05 for O at the bottom, s_w = 10⁻⁴ (A_w = 71):
  Coburn–Winters factor     0.0297 / (0.0297 + 0.05 × 0.970) = 0.380
  Wall-loss factor          exp(−43.5/71) = 0.54  (46% lost)
  Oxygen at the bottom      7.3 × 10¹⁸ × 0.380 × 0.54 = 1.5 × 10¹⁸ cm⁻² s⁻¹
```

The carbon at the exit is removed at 8.0 nm/s, which is 7.1 × 10¹⁶ atoms cm⁻² s⁻¹. The oxygen arriving is **twenty-one times** that. The etch is neutral-rich by a wide margin, which is the design rule of Book #31, and the reason the bottom is ion-limited, not oxygen-limited.

### 3.5.2 The ARDE Law

The rate falls with aspect ratio as in Book #31: ER = ER₀/(1 + kA + k₂A²) with k = (3/4)χ, where χ = ν ER₀/Γ_O,0 is the ratio of oxygen consumed at the open surface to oxygen supplied:

```
              M0 (CW, 20 °C)     M1 (pulsed, 10 °C)
  ER₀          830 nm/min         730 nm/min
  χ            0.021              0.0147
  k            0.016              0.011
  k₂           2 × 10⁻⁵           1 × 10⁻⁵
  ER/ER₀ at A = 45 (h = 1400 nm)   0.567     0.659
```

M1's lower k comes from less carbon to remove (ER₀ 12% lower) and more oxygen to remove it with (27% more), which gives χ = 0.0147 against 0.0213; its cleaner wall also halves the wall-loss term (k₂). The 34% fall of M1's rate at the exit has a second contribution: the ions. Ion transmission through a 44:1 tube, with forward reflection from the wall at grazing incidence, is about 0.70. The two series resistances give:

```
1/ER = 1/(f_i ER₀) + 1/Γ_O,bottom   (both in atoms cm⁻² s⁻¹, one oxygen per carbon)
          f_i = 0.70:  ER/ER₀ = 0.67   (fitted 0.66)
```

### 3.5.3 Time to Depth

```
t(h) = [h + k h²/(2w) + k₂ h³/(3w²)] / ER₀,   w = 31 nm

                    M0                       M1
  h (nm)    A      ER (nm/min)   t (s)     ER (nm/min)   t (s)
  ─────────────────────────────────────────────────────────────
    200     6.5      752          15.2        681          17.0
    500    16.1      657          40.9        619          44.8
    800    25.8      582          70.0        566          75.2
   1000    32.3      540          91.4        535          97.1
   1200    38.7      503         114.5        507         120.1
   1400    45.2      471         139.1        481         144.4
```

The last 400 nm of M1 (1000 to 1400 nm) takes 47 s, 49% of the first 1000 nm's 97 s: the last 29% of the depth takes 33% of the time. The carbon open is a mild ARDE etch.

### 3.5.4 Depth Sensitivity to CD

```
∂h/∂w = (k A²/2 + 2 k₂ A³/3) / (1 + k A + k₂ A²)

M1 at A = 45.2:   (0.011 × 2043 / 2 + 0.667 × 10⁻⁵ × 92,345) / 1.517 = (11.24 + 0.62) / 1.517 = 7.8 nm per nm
M0 at A = 45.2:   (0.016 × 2043 / 2 + 0.667 × 2 × 10⁻⁵ × 92,345) / 1.764 = (16.34 + 1.23) / 1.764 = 10.0 nm per nm
Book #29, capacitor etch (for comparison):  15.2 nm per nm
```

At the exit rate of 8.0 nm/s, one nanometre of CD is one second of open time. The carbon open is less sensitive to CD than the mold etch that follows, and its overetch (Chapter 8) is set by thickness and uniformity, not by the CD tail.

---

## 3.6 Selectivity to the Cap and the Stop

### 3.6.1 The Cap

The SiON cap is attacked in two ways: physically by the ions, with a threshold higher than carbon's, and chemically by the sulfur of the COS:

```
v_cap = v_phys + v_chem
  v_phys = 0.166 nm/s × (√E − √90)/(√600 − √90)      (M1, duty 0.70)
  v_chem = 0.071 nm/s  ∝ COS flow  (30 sccm)

                    250 eV   400    600    800    1000
  v_cap (nm/s)      0.141    0.187  0.237  0.279  0.316
  ACL:SiON          47.9     50.0   51.3   52.1   52.6
  Facet factor ρ    1.00     1.00   1.15   1.30   1.45
```

Energy is a weak lever on the blanket selectivity (±5% over a factor of four in energy), because the chemical term does not depend on it. The facet factor, which sets how much faster the shoulders of the cap ridge erode than a flat surface, rises with energy: ρ = 1 + 0.75 × 10⁻³ (E − 400 eV) above 400 eV. M0 has less sulfur (v_chem = 0.014 nm/s) and a blanket selectivity of 64; **M1's COS costs 20% of the selectivity (64 to 51)**, but M1 runs at 600 eV and ρ = 1.15, M0 at 800 eV and ρ = 1.30, and it is the facet factor that sets the top loss (Chapter 11).

### 3.6.2 The Stop

```
Overetch (M1 OE, same bias as the main etch):  ACL 730 nm/min at the top, 481 nm/min at the exit
                             SiN  8 nm/min (600 eV on-phase, time-averaged)
  Selectivity at the exit    481 / 8 = 60
  SiN loss in the 18 s OE    8 × 18/60 = 2.4 nm      (specification ≤ 3 nm)
```

The overetch cannot be run at a low energy to spare the nitride. At 250 eV the ion transmission of a 44:1 tube falls from 0.64 to 0.35 (Chapter 7), the ACL rate at the exit to about 150 nm/min, and clearing the 85 nm that the overetch budget requires (Chapter 8) would take 33 s instead of 11.

---

## 3.7 The Hydrogen Alternative

Nitrogen and hydrogen etch carbon too, as HCN and CH₄, and do so with almost no isotropic attack:

```
Oxygen and hydrogen chemistries for the 1400 nm carbon open (illustrative):
                                 O₂/COS (M1)       N₂/H₂
  ER₀ (nm/min)                   730               330
  ARDE k, k₂                     0.011, 1 × 10⁻⁵   0.018, 3 × 10⁻⁵   (H recombines on the wall)
  Main etch at 1400 nm           144 s             363 s
  Bare lateral rate (10 °C)      0.54 nm/s         0.03 nm/s
  Coverage needed for 0.7 nm bow ≥ 99%             ≥ 97%
  Blanket selectivity to SiON    51                ≈ 80
  Wall film                      S–C, SiOₓ         C–N polymer
  Residue                        S, SiOₓ           ammonium salts, C–N
```

N₂/H₂ cuts a straight, smooth hole with little passivation. It is also two and a half times slower, so a 1400 nm mask would take six minutes. It is used for thin masks, for the final clean-up step of B-ACL, and where sulfur cannot be tolerated; Chapter 14 returns to it.

---

## Summary and Key Takeaways

1. **Every route to carbon removal is exothermic by hundreds of kJ/mol.** Selectivity and sidewall protection come from kinetics and volatility, not from thermodynamics.

2. **Products must leave and passivants must stay.** CO, CO₂, HCN are volatile; SiOₓ, S–C and C–N films are not. A passivant that oxygen turns into a gas (S to SO₂) is sacrificial, and must be resupplied.

3. **The bottom is cut by an ion-assisted reaction.** Y(E) = 0.355 (√E − 5): 6.9 carbon atoms per 600 eV ion; 12 nm/s at the top in M1.

4. **Bare carbon is attacked at 0.54 nm/s.** To bow by less than 1 nm the wall must be more than 99% covered; the bow is a measurement of coverage.

5. **Five parameters predict the bow.** x₀, ℓ_O, ℓ_p, c, ℓ_c, with ℓ = d/√(2s). The bow is proportional to x₀ and sits at 27% of the depth in M1; the overetch hardly moves it.

6. **The tube is neutral-rich, and ion-limited.** Oxygen at the exit is 21 times what is consumed; M1 runs at 66% of ER₀ at the exit, M0 at 57%, and one nanometre of CD costs one second.

7. **COS buys passivation at 20% of the cap selectivity.** Energy is a weak lever on selectivity; the facet factor, which rises with energy, is what shortens the cap's life.

---

## Study Questions

1. Compute the reaction enthalpy per mole of carbon for the formation of CS₂ from C(s) and S(g) (ΔH_f CS₂ = +117 kJ/mol), and say whether sulfur can serve as a carbon-removing reagent as well as a passivant.

2. A 600 eV ion has Y = 6.92. Find ER₀ for an ion flux of 3.0 × 10¹⁶ cm⁻² s⁻¹ at a duty of 0.60. By what factor does the rate change if the energy is raised to 900 eV at the same flux?

3. The bare lateral rate at 10 °C is 0.54 nm/s. Find it at 0 °C and −25 °C using E_a = 0.42 eV, and the passivation coverage needed at each to keep the bow at 0.7 nm, if the exposure stays 130 s and the oxygen flux is unchanged.

4. Using ℓ = d/√(2s), find the sticking probability for which a species is down to 10% of its top flux at 300 nm. Is that species a candidate for passivating the bow zone?

5. For M1 find x(370 nm) and θ(370 nm), using the parameters of Section 3.4.1. Verify the lateral rate of 0.0030 nm/s.

6. Compute ∂h/∂w for a 1c-class mask (A = 52, k = 0.012, k₂ = 1.2 × 10⁻⁵), and the open time per nanometre of CD at an exit rate of 7 nm/s.

---

**Next Chapter:** [Chapter 4: Honeycomb Patterning, Pattern Transfer & Hole Statistics](./04-honeycomb-pattern-transfer-statistics.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
