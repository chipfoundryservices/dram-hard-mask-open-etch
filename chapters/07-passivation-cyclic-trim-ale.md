# Chapter 7: Passivation Engineering, Cyclic Processes, Trim & Atomic-Layer Carbon Etch

## Overview

The model of Chapter 3 says what a good sidewall film must do: cover more than 99% of the wall, over the whole depth where oxygen can reach it, and not close the hole. The levers of Chapter 6 say how far the standard controls can push a continuous plasma toward that: a cold chuck and a sulfur-rich gas bring the bow from 2.0 to 0.7 nm, and then each one begins to cost more than it gains. This chapter is about what lies beyond: other passivants and their reach, a cyclic scheme that rebuilds the film at every depth, a radical trim that corrects the top of the hole after the fact, and an atomic-layer etch that corrects it with precision and, for a reason that is a fact of geometry, cannot reach the bottom.

The theme is **reach**. A species that sticks on its first collision coats the top of the tube and never visits the bottom; a species that does not stick may coat everything and clog nothing. The reach of every film, every trim, and every ion in this chapter is set by one length, ℓ = d/√(2s), and the choice of tools for the carbon open is a matching of reach to job.

**Learning Objectives:**
- Compare passivant routes by sticking probability, reach at the bow zone and at the exit, residue, and cost to the cap
- Explain why a two-species passivation (a short-reach film for the top and a long-reach film for the depth) matches the model
- Quantify the sulfur inventory and carry-over of the COS route
- Describe the cyclic deposition–etch scheme of M2 and compute its gain in x₀, bow, and web and its cost in time
- Compute the reach and the dose profile of a radical trim in a 31 nm tube
- Compute the ion transmission at low energy and show why atomic-layer etching of carbon cannot reach the bottom of a 44:1 hole
- Choose the tool for a given correction (top CD, bow, exit CD, roughness, residue)

---

## 7.1 The Passivation Menu

### 7.1.1 Candidates

Every passivant on the menu arrives as a gas-phase species that sticks on the wall with some probability s. Its reach into the tube follows from s (Chapter 3):

```
Passivant routes for the carbon open (illustrative; d = 31 nm, ℓ = d/√(2s)):

  Route               Wall film        s        ℓ (nm)   Reach at    Reach at    Residue risk                  Cost to the cap
                                                         370 nm      the exit
  ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
  COS (M1)            S–C, SOₓ         7.5e-4   800      0.63        0.19        sulfur on walls, carry-over   ACL:SiON −20%
  SO₂                 SOₓ              3e-3     400      0.40        0.034       as COS, less carbon           −10%
  N₂ (with H₂)        C–N polymer      2e-3     490      0.47        0.064       ammonium salts, C–N clogging  none (selectivity ≈ 80)
  SiCl₄ / SiF₄        SiOₓ, SiOCl      0.05     98       0.023       10⁻⁶        oxide micromasks at the exit  none; adds oxide
  Cap-sourced SiOₓ    SiOₓ             0.13     60       0.002       ≈ 0         none (own the cap)            the cap erodes
  CH₄ / CO            C-rich redeposit 0.02     155      0.092       10⁻⁴        carbon micromasks             lowers selectivity of the ACL
```

(The reach is the fraction of the top flux that arrives at the depth: e^(−z/ℓ).)

Three classes follow. **Short-reach films** (SiOₓ, s > 0.05) coat the top of the tube and nothing below 300 nm. They are the best films, hard and non-volatile, but they are a supply for the first 100 to 200 nm only; M1 gets its SiOₓ free from the cap, and adding more from SiCl₄ would raise the risk of oxide micromasks at the exit. **Medium-reach films** (S–C, C–N; s ≈ 10⁻³) arrive at the bow zone at 40–60% of the top flux and at the exit at 3–20%; they are what passivates the middle of the hole. **No film reaches the exit.** The foot at the exit is not passivation; it is redeposition (Chapter 3).

### 7.1.2 Why Two Species

The model of Chapter 3 has exactly this structure: x(z) = x₀ e^(−z/ℓ_O) / [e^(−z/ℓ_p) + c e^(−z/ℓ_c)], with a long-reach species (ℓ_p = 800 nm, the COS film) and a short-reach species (ℓ_c = 60 nm, the cap's SiOₓ, with strength c = 8). Remove the short one (c = 0), and the top of the hole is covered to 99.5% instead of 99.94%, the bow zone disappears into a wall that is 0.8 nm wider from the top down (32.9 nm), and the top CD grows by 0.8 nm. Cut the long one to a twentieth, and the middle of the hole bows by 12 nm and the neighbours merge. **The two do different jobs and neither can replace the other.** The reference gets one for free from the cap and buys the other with 30 sccm of COS.

---

## 7.2 Sulfur: The M1 Choice

### 7.2.1 What the Film Is

In the M1 plasma the COS dissociates to CO and sulfur-bearing species. Sulfur reacts with carbon on the wall to form a thin S–C film and with oxygen to form SO and SO₂, which leave. The film is therefore a balance of deposition and oxidation, and its coverage is set by the ratio x. At the bow zone, with coverage of 99.35% and a film that is a fraction of a monolayer thick in most places, the film is closer to a **decoration** of the wall (a sulfur atom on a carbon dangling bond, protecting its site from oxygen) than to a layer:

```
Sulfur on the wall (M1, illustrative):
  Monolayer equivalent                      ≈ 10¹⁵ atoms/cm²
  Sulfur at the bow zone (XPS on a cleaved wall)    ≈ 4 × 10¹⁴ cm⁻²  (0.4 ML)
  Sulfur at the exit                        ≈ 1 × 10¹⁴ cm⁻²
  Sulfur on the wall of the whole wafer     ≈ 2.03 m² × 3 × 10¹⁴ cm⁻² ≈ 6 × 10¹⁸ atoms  (0.3 mg)
  Sulfur supplied                           30 sccm × 162 s, i.e. 3.6 mmol = 116 mg of sulfur
  Fraction of the COS that ends on the wall 0.3 / 116 = 0.3%
```

### 7.2.2 Carry-Over

The wafer leaves with 2 m² of wall carrying a few times 10¹⁴ sulfur atoms per square centimetre. In the capacitor etch chamber, a few hours later, the sulfur is removed by the fluorocarbon plasma as SF₆ and SO₂F₂, and part of it settles on the mold-etch chamber's walls. It does not damage the hole, but it adds to the wall inventory of that chamber and to its first-wafer effect (Book #29, Chapter 9). Two controls limit it: the post-open degas (Chapter 9) and the queue time. A fab that cannot accept any sulfur in the capacitor chamber has to leave COS for a different passivant, SiCl₄ and the N₂/H₂ route of Section 3.7, and pay in micromasks, in time, or both.

---

## 7.3 Cyclic Deposition–Etch

### 7.3.1 The Idea

A continuous plasma holds the wall's coverage at a steady state set by x. A cyclic scheme alternates the steps: a **deposition step** with no bias, in which low-sticking passivant fills the tube by isotropic diffusion and rebuilds the film to full coverage at every depth, and an **etch step** with the bias on, in which the carbon is cut while the film is thinning. The average bare fraction is lower than the steady one because every etch step begins with a restored wall:

```
M2 cycle (1d-class, B-ACL, −25 °C, 26 nm exit):
  Deposition   1.5 s    SO₂ / COS / Ar, no bias, 40 mTorr
  Etch         4.5 s    O₂ / COS / CF₄ 3% / Ar, 5 kHz bias
  Cycle        6 s;  duty 0.75;  ≈ 35 cycles in the 209 s main etch
  Instantaneous rate during the etch step    560 / 0.75 = 747 nm/min  (time-averaged 560)
```

### 7.3.2 What It Buys and What It Costs

The B-ACL of M2 needs a few percent of CF₄ to carry boron off as BF₃ (Chapter 14), and the fluorine removes the S–C film far faster than oxygen alone: the passivant removal x₀ at −25 °C is 0.075 in a continuous plasma, 15 times M1's 0.005. The cyclic scheme restores most of the coverage:

```
M2 continuous and cyclic, at −25 °C:
                                  Continuous         Cyclic (1.5 s / 4.5 s)
  x₀                              0.075              0.0265  (× 0.35)
  Main etch (s)                   156                209
  Bow (nm)                        0.95               0.46
  Minimum web (nm)                8.9                9.5
  Specification (bow ≤ 0.8, web ≥ 9.0)    ✗ ✗         ✓ ✓
  Total plasma time                206 s              259 s
```

The cyclic scheme buys 0.49 nm of bow and 0.6 nm of web for 52 s of main etch (25% of the total) and an extra module cost of about $1.9 a wafer. It makes M2 meet a specification that the continuous plasma cannot.

### 7.3.3 The Ripple

A cyclic etch leaves a ripple on the wall at the period of the cycle. In a continuous model the wall moves at a steady rate; here the film is thickest at the end of each deposition and thinnest at the end of each etch, and the lateral rate varies in phase:

```
Wall movement in one etch step (M2, bow zone):  v_lat × t_etch = 0.0013 nm/s × 4.5 s ≈ 0.006 nm
Ripple period     (etch per cycle)                        ≈ 35 nm at the exit (5.8 nm/s × 6 s), 56 nm at the top
Ripple amplitude  < 0.02 nm   (specification ≤ 0.2 nm)
```

At −25 °C the ripple is negligible, a hundredth of the roughness budget. The limit on the cycle time is not the ripple but the gas switching: a deposition step shorter than 1 s is half spent settling, and a cycle shorter than 4 s makes the switching time a quarter of the process.

---

## 7.4 Radical Trim

### 7.4.1 A Correction After the Fact

A radical trim is an isotropic, low-energy exposure to oxygen or nitrogen radicals, applied after the main etch, which removes a fixed thickness from the wall. In a 31 nm hole at 44:1 its job is limited by the same transport that limits everything else in this book:

```
Radical trim (remote O/N₂ source, 10 °C, no bias, bare wall):
  Radical flux Γ                  3 × 10¹⁷ cm⁻² s⁻¹
  Reaction probability γ_C        6.6 × 10⁻⁴
  Lateral rate                    v = γ Γ / n_C = 6.6 × 10⁻⁴ × 3 × 10¹⁷ / 8.87 × 10²² = 0.022 nm/s
  Time for 0.5 nm per side at the top    22 s
  Reach (wall loss s = γ_C)       ℓ = 31 / √(2 × 6.6 × 10⁻⁴) = 853 nm

Removal per side after a 22 s trim:
  Depth (nm)          0      200    400    800    1000   1350
  Removal (nm)        0.50   0.40   0.31   0.20   0.16   0.10
```

The trim removes 0.5 nm per side at the top and 0.1 nm at the exit. It **changes the taper**: a 22 s trim that is meant to widen the top by 1.0 nm widens the exit by 0.2 nm and leaves the foot where it was. It is a tool for the top 400 nm (where it does 60% or more of its full dose) and not for the exit CD, which is set by the flux of ions at the bottom of the tube (Chapter 6).

### 7.4.2 Uses

```
Trim (22 s) as a corrective tool:
  Correct a cap CD that arrives 1 nm small          widens the top by 1.0 nm; exit by 0.2 nm
  Smooth the top of the roughness                   T(ξ) at the top improves by ≈ 0.05 (Chapter 4)
  Does not correct                                  exit CD, family offset, bow, residue at the exit
  Cost                                              22 s plus a remote-plasma chamber, $0.8 per wafer
```

The reference process does not use a trim. A product whose lithography has a fixed CD error at the top could use one; the exit still has to be corrected by the main etch.

---

## 7.5 Atomic-Layer Carbon Etch

### 7.5.1 The Cycle

Atomic-layer etching (ALE) of carbon separates the two steps that a continuous etch performs at once: an oxidation step, in which atomic oxygen from a downstream plasma adsorbs on the carbon surface until the sites are full, and a removal step, in which argon ions with an energy below the sputter threshold of unoxidized carbon remove the oxidized layer and nothing else:

```
Carbon ALE cycle:
  Adsorb       O₂ plasma, no bias                          3 s
  Purge                                                    1 s
  Remove       Ar⁺ at 35 eV (bias only)                    3 s
  Purge                                                    1 s
  Cycle        8 s      Etch per cycle (EPC)  0.42 nm      Rate  3.15 nm/min
  Time for the 1350 nm mask               1350 / 3.15 = 430 min = 7.1 h
```

It is far too slow to cut the mask. It is attractive for small, precise corrections: removing 1 nm of foot, or trimming 0.3 nm of the cap-sourced SiOₓ. The correction needs the ions to reach it.

### 7.5.2 Ion Starvation

A low-energy ion has a wide angular distribution, √(T_i/E), and a 44:1 tube accepts only a narrow cone. The fraction of the ions that arrive within the geometric acceptance of 1.3°, for a Gaussian distribution with T_i = 0.15 eV, is:

```
f_i = 1 − exp[ −α² / (2σ_θ²) ],   α = 1.3°,   σ_θ = √(T_i/E)

  E (eV)            35       60       100      250      600
  σ_θ (°)           3.75     2.86     2.22     1.40     0.91
  f_i               0.058    0.098    0.158    0.349    0.643
```

At 35 eV, 6% of the ions reach the exit; ALE at the exit proceeds at 6% of its rate at the top, an EPC of 0.024 nm:

```
ALE at the exit (35 eV):  EPC 0.42 × 0.058 = 0.024 nm per cycle
  Removal of 1 nm        41 cycles = 5.4 min
```

Five minutes to remove one nanometre of foot is not a process. And the top of the tube would be etched to 1 nm in 2.4 cycles, so an ALE correction to the exit would machine the top by 17 nm before it reached 1 nm at the bottom. **Atomic-layer etching of carbon cannot reach the bottom of a 44:1 hole.** It is a tool for the first few hundred nanometres, where the ion transmission is high. (The 250 eV row also shows why the overetch is not run at low energy: f_i falls from 0.64 at 600 eV to 0.35.)

---

## 7.6 Matching Tools to Jobs

```
Correction                     Tool                       Reach            Verdict
──────────────────────────────────────────────────────────────────────────────────────────────────────
Bow (0.7 nm)                   passivation, temperature   whole depth      main etch (Chapters 3, 6)
Bow, extreme (1d, −25 °C)      cyclic deposition–etch     whole depth      M2: +25% time
Top CD (cap arrives small)     radical trim               top 400 nm       22 s; widens the top 5× more than the exit
Exit CD                        ion flux and OE            at the bottom    ME and OE only; no tool beyond them
Foot and residue at exit       OE-clear, ions at 600 eV   at the bottom    OE-clear (11 s)
Edge roughness (LER)           smoothing step ST3b        whole wall       −0.55 nm
Fine correction, top           ALE                        top ≈ 300 nm     7.1 h per mask; ion-starved below 400 nm
Family offset                  none                       —                lithography
```

The distinction is the one the Overview made: **what reaches the bottom is the ion, and the passivation is what keeps the wall from being cut on the way.** Every other tool in this chapter is a tool for the top of the hole.

---

## Summary and Key Takeaways

1. **Reach is ℓ = d/√(2s).** A species that sticks at 0.1 reaches 70 nm; one that sticks at 10⁻³ reaches 700 nm. The reach of every film, trim, and ion is the same length with a different s.

2. **Two species do two jobs.** A short-reach SiOₓ for the top (free from the cap) and a medium-reach S–C film for the depth (30 sccm of COS). No film reaches the exit; the foot is redeposition.

3. **Sulfur is a decoration, not a layer.** About 0.4 monolayers at the bow zone; 0.3% of the COS ends on the wall; the wafer carries 6 × 10¹⁸ sulfur atoms to the next chamber.

4. **Cyclic deposition–etch cuts x₀ by a factor of 2.8.** For M2 it takes the bow from 0.95 to 0.46 nm and the web from 8.9 to 9.5 nm, for 52 s; the ripple is below 0.02 nm.

5. **A radical trim is a top tool.** 0.5 nm per side at the top, 0.1 nm at the exit after 22 s; it changes the taper and cannot correct the exit.

6. **Carbon ALE is ion-starved at depth.** 6% of the ions at 35 eV reach the exit; 1 nm of foot takes 41 cycles; the top would be machined away first.

7. **The ion is what reaches the bottom.** Every correction other than the main etch and the overetch is a correction to the top.

---

## Study Questions

1. A passivant sticks with s = 5 × 10⁻³ in a 26 nm tube (M2). Find its decay length, and its reach at 400 nm and at 1450 nm. Is it a candidate for the bow zone?

2. The cyclic scheme of M2 is changed to 1.0 s deposition and 5.0 s etch. If x₀ rises from 0.0265 to 0.032, find the new bow (use the proportionality of bow to x₀ for small x, 0.46 nm at 0.0265) and the effect on the web. What happens to the duty and to the time of the main etch?

3. A radical trim of 15 s at a flux of 4 × 10¹⁷ cm⁻² s⁻¹ and γ_C = 6.6 × 10⁻⁴ is applied to M1. Find the lateral rate, the removal at the top, at 400 nm, and at the exit.

4. Compute f_i for a 20 eV ion (T_i = 0.15 eV, acceptance 1.3°) and the EPC at the exit. How many cycles does 1 nm take, and how long at 8 s per cycle?

5. The sulfur at the bow zone is 4 × 10¹⁴ cm⁻² and at the exit 1 × 10¹⁴ cm⁻². If the sulfur varies exponentially with depth between the two, find the length constant, and compare it with ℓ_p = 800 nm.

6. M2 without the cyclic scheme costs 206 s and with it 259 s. At $0.036 per second of cycle time, find the extra cost per wafer, and at 150,000 wafers a month the annual cost of the scheme.

---

**Next Chapter:** [Chapter 8: Endpoint & In-Situ Monitoring of a Carbon Open](./08-endpoint-in-situ-monitoring.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
