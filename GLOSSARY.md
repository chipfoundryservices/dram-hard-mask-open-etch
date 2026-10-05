# Glossary: DRAM Hard Mask Open Etch

Terms are defined as they are used in this book. Chapter references point to the main discussion. Values are those of the reference process (route M1) unless stated.

---

## A

**ACL (amorphous carbon layer):** The PECVD carbon hard mask of the capacitor etch: 1400 nm deposited (± 14 nm, 3σ), density 1.80 g/cm³, 17 at% hydrogen, stress −300 MPa; 1350 nm remain after the open. (Ch. 1.1.1, 2.1.1)

**ACL:SiON selectivity:** The ratio of the carbon rate to the cap's flat erosion rate in the main-etch plasma; 51 for M1 (730 nm/min against 0.237 nm/s), 57 for M0, 38 for M2. (Ch. 3.6.1, 11.8)

**Actinometry:** Normalizing an emission line by the Ar 750.4 nm line to remove changes in electron density and window transmission; the CO 483.5 nm signal of the endpoint is normalized this way. (Ch. 8.1.1, 8.5.1)

**ALE (atomic-layer carbon etch):** Etching by alternating oxygen modification and low-energy ion removal; ion-starved at depth (6% of the ions at 35 eV reach the exit), so it can machine the top and not the foot. (Ch. 7.5)

**Array edge:** The boundary of a cell array block, where the film stress relaxes, the ellipticity rises, and the exit CD offset is +0.55 nm at row 1, decaying over 1.4 rows. (Ch. 10.6.2, 12.2, 12.5.1)

**Array efficiency:** The array area divided by the die area (0.379 for the reference die); sets the chemical load and the CO drop at clearing. (Ch. 10.6.3)

**ARDE (aspect-ratio-dependent etching):** Fall of the etch rate with aspect ratio, ER = ER₀/(1 + kA + k₂A²); M1: k = 0.011, k₂ = 10⁻⁵; the rate at the exit is 0.659 ER₀. (Ch. 3.5.2)

**Aspect ratio:** The depth divided by the width; the hole is 44:1 (1350/31), the web 96:1 (1350/14). (Ch. 1.1.3)

---

## B

**B-ACL (boron-doped ACL):** Carbon with about 40 at% boron, a mask of the 1d-class array; stiffer (105 GPa), more selective (ACL:oxide 8–9), and opened with CF₄ 3% to carry boron off as BF₃; 1500 nm deposited. (Ch. 2.1.2, 14.1)

**Bare lateral rate (v_b):** The rate at which oxygen radicals attack an unprotected carbon wall, v_b = γ_C Γ_O/n_C; 0.54 nm/s for M1 at 10 °C, 0.77 nm/s for M0 at 20 °C. (Ch. 3.3.1)

**BARC:** The bottom anti-reflective coating under the resist, 25 nm, opened in ST1 in 8 s. (Ch. 2.3.1)

**Bevel:** The outer 1–3 mm ring of the wafer, which contributes 2.3 sccm of CO (1 mm) to the endpoint signal. (Ch. 8.1.1)

**BF₃:** The volatile product (b.p. −100 °C) by which fluorine carries boron off the B-ACL; B₂O₃ is involatile and stays. (Ch. 14.1.1)

**Bimorph model:** The model of wiggling in which the asymmetric faces of a web have different stress and bend it, κ = 6(1 − ν) a_f σ_s t_s/(E t²). (Ch. 12.3)

**Bow:** The maximum of the CD above the top CD: +0.67 nm for M1 at 370 nm depth (27% of the depth), +2.0 nm for M0 at 450 nm; specification ≤ 1.0 nm. (Ch. 3.4.2, 10.3)

---

## C

**Cap:** The 40 nm SiON layer (60 nm in M2) on top of the carbon, which carries the pattern; for a 14 nm web it is a ridge whose shoulders erode first. (Ch. 2.2, 11.1)

**Cap CD:** The CD of the opening in the cap after ST1: 32.0 nm (bottom), 33.0 nm (top), taper 89.3°. (Ch. 2.3.1, 10.5.1)

**Cap clock:** The time at which the cap fails on the web, t₀ = h_cap/(ρ v_cap) = 146.8 s; the carbon's clock is the open time T; their difference squared is the top loss. 1 sccm of COS is 1.47 s of it. (Ch. 8.6, 11.2, 15.4.1)

**CCP (capacitively coupled plasma):** The dual-frequency chamber (60 MHz source, 2 MHz bias, 300 mm) that opens the carbon, the same family as the capacitor etch. (Ch. 5.1, 5.2)

**CD-SAXS:** Critical-dimension small-angle X-ray scattering; the average CD at each depth of the array without cutting the wafer, 0.15 nm precision. (Ch. 15.1)

**Chamber memory:** The influence of the wall's film state on the next wafer's passivant supply; resets with the NF₃ clean and the season. (Ch. 5.3)

**Clausing factor:** The transmission probability of a long tube, K ≈ 1/(1 + 3A/4); 0.0297 at A = 43.5. (Ch. 3.5.1)

**Cliff:** The steep dependence of the top loss on the cap thickness: 1 nm of cap (40 → 41 nm) is 21 nm of mask (50 → 29 nm). (Ch. 2.2.3, 11.4.1)

**Closure threshold:** The exit width below which a hole stops etching (12 nm, ion transmission 0.145); a deviation of 19 nm from the 31 nm exit. (Ch. 13.3.1)

**Coburn–Winters relation:** The bottom-to-top flux ratio of a reactive species in a tube, Γ_b/Γ_t = K/(K + β(1 − K)). (Ch. 3.5.1)

**COS (carbonyl sulfide):** The sulfur passivant and CO source; 30 sccm in M1's main etch (3.43 mmol per wafer), a knob on the cap clock; toxic and flammable. (Ch. 3.4, 6.5, 7.2.1)

**Crest:** The highest part of the cap ridge after the open: a crest 6.2 nm wide at 1400 nm with shoulders at 1210 nm. (Ch. 11.3)

**Cyclic deposition–etch:** Alternating a bias-free deposition (SO₂/COS, 1.5 s) with an etch (4.5 s); cuts x₀ to 0.35 of its continuous value in M2 and the bow from 0.95 to 0.46 nm. (Ch. 7.3)

---

## D

**Degas:** A 150 °C, 30 s step in the load lock that removes 90% of the water taken up during the hold. (Ch. 9.5.2)

**Duty:** The fraction of the pulse period in which the bias is on: 0.70 in M1. At constant mean ion flux a change of 0.1 moves the bow by 0.03 nm. (Ch. 5.2.3, 6.3.1)

**Dummy rows:** Extra rows of holes outside the functional array; they cure the edge CD and the ellipticity but not the stress relaxation. (Ch. 10.6.2, 12.2.2)

---

## E

**Edge height:** The height of the shoulders of the ridge after the open (1210 nm in M1), against the crest at 1400 nm; the margin to the specification is 94 nm. (Ch. 11.3)

**Edge ring:** The silicon ring around the wafer; wears 0.12 µm per RF-hour; tilts the ions by 0.03° new plus 0.08° per 100 µm; limit 0.05° at 25 µm and 4,070 wafers. (Ch. 5.5.2)

**Ellipticity:** The difference between the two axes of the hole divided by the mean; 0.012 at the array interior, 0.027 at row 1; specification ≤ 0.03. (Ch. 4.2.4, 12.5.1)

**Endpoint (EP):** The decision to stop the main etch from the fall of the CO emission; measures the median hole at 144.4 s; the overetch of 11 s follows. (Ch. 8.2, 8.5)

**ER₀:** The time-averaged etch rate of the carbon at the top of an open area: 730 nm/min for M1, 830 for M0, 560 for M2 (time-averaged). (Ch. 3.2.1, 3.5.2)

**EUV:** Extreme-ultraviolet lithography, an alternative to SADP × 2 for the cap pattern; needs a thin resist and a litho specification on partial opens. (Ch. 4.1.2, 13.2.2)

**EWMA (exponentially weighted moving average):** The feedback filter on the exit CD (λ = 0.3, limits ± 0.315 nm) with the ST1 CHF₃ flow as the knob (0.066 nm/sccm). (Ch. 15.4.3)

**Exit CD:** The CD at the bottom of the carbon, 31.0 nm; the aperture through which the capacitor etch's ions enter; 31.0 + G (cap CD − 32.0). (Ch. 4.2.1, 10.4.1)

---

## F

**Facet factor (ρ):** The ratio by which the ridge of the cap fails earlier than a flat film because its edge erodes by ion-induced faceting; 1 + 0.75 × 10⁻³ (E − 400) → 1.15 at 600 eV. (Ch. 3.6.1, 11.1)

**Family (A, B, C):** One of the three sub-lattices (1:2:1) of the SADP × 2 pattern, each with its own cap CD; the exit CD inherits their offsets with gain 1.10. (Ch. 4.1.1, 4.2.1)

**Family offset:** The difference of CD between families after the open; ≤ 1.2 nm at the exit (≤ 1.0 nm in the cap). (Ch. 4.2.1)

**FDC (fault detection and classification):** Monitoring of the in-situ signals (OES, V_dc, temperatures, flows) for excursions and for virtual metrology. (Ch. 8.7, 15.5)

**First-wafer effect:** The higher passivant removal of the first wafers after an NF₃ clean; bow 1.34 nm on wafer 0 without a season, 0.77 nm with it. (Ch. 5.3.2)

**Foot:** The narrowing of the hole in the last ~50 nm (f₀ = 0.60 nm per side, λ = 49 nm); sets the exit CD 1.1 nm below the top and the local angle of 89.3°. (Ch. 1.4.2, 10.4)

---

## G

**Gain (G):** The coefficient of the transfer of CD error from the cap to the exit: 1.10 for M1, 1.30 for M0. (Ch. 4.2.1)

---

## H

**Hard mask:** A film harder than the resist that carries a pattern through a deep etch; here the 1.4 µm carbon, patterned by a thin cap. (Ch. 1.1)

**HD-ACL:** High-density ACL deposited at 550 °C (1.95 g/cm³, 12 at% H); opens at 0.72 of the ACL rate. (Ch. 2.1.2)

**Honeycomb:** The perforated mask after the open: holes on a hexagonal lattice, 43.5% open, joined by 14 nm webs and stiff nodes. (Ch. 1.1.3, 12.1)

**HV-SEM:** High-voltage SEM at 30–50 keV, whose electrons pass through the carbon and show the exit of each hole (closed exits are dark). (Ch. 15.1)

**Hybrid cap:** A cap with a silicon film (ACL:Si ≥ 100) that outlasts the open and removes the cliff: L = 0, mask 1500 nm in M2, for +$1.6. (Ch. 11.5, 14.3)

**Hydrogen content:** The at% of H in the carbon; rate ∝ 1 + 0.03 (H − 17); 1 at% is ±3.0% in rate and ±4.3 s of open time. (Ch. 2.1.3)

---

## I

**IEDF (ion energy distribution function):** The spread of ion energies at the wafer; ± 30% at 2 MHz for M1. (Ch. 5.2.1)

**Interferometry:** Optical endpoint by film-thickness fringes; blind at 633 nm (penetration 126 nm in ACL) and impractical at 1550 nm. (Ch. 8.3)

**Ion yield (Y):** Carbon atoms removed per ion, Y(E) = 0.355 (√E − 5); 6.92 at 600 eV. (Ch. 3.2.1)

**IR scatterometry:** Optical profile measurement at 1.3–1.7 µm; used on the ridge test structure to measure the top loss (3 nm). (Ch. 15.1, 15.2)

---

## K

**Killer particle:** A particle of 81 nm or more that blocks a cluster of holes; specification ≤ 0.5 adders ≥ 80 nm per wafer. (Ch. 9.2.2)

---

## L

**Laplace pressure:** The capillary pressure in a wetted hole, P = 4γ cos θ/d; +6.6 MPa at 45°, −0.8 MPa at 95°; the reason the mask is not wet-cleaned. (Ch. 9.4)

**LCDU (local CD uniformity):** The 3σ spread of CD within a small group of holes; 2.4 nm → 2.2 nm (M1), 3.2 nm (M0). (Ch. 4.2.2)

**LER (line-edge roughness):** The 3σ roughness of the hole edge; 2.5 nm → 1.95 nm after the smoothing step. (Ch. 4.2.3)

**Ligament efficiency (η):** (p − d)/p, the stiffness of a perforated plate relative to the solid film; 0.311 nominal, 0.271 at M1's bow. (Ch. 12.1.1)

**Local angle:** The slope of the wall over the last 50 nm (89.3°), not the full-height average (89.98°); Book #29's "89.3°". (Ch. 1.4.2, 10.2)

---

## M

**M0 / M1 / M1-c / M2 / M3:** The routes of this book: M0 the CW 800 eV baseline at 20 °C; M1 the pulsed, sulfur-passivated, smoothed reference; M1-c M1 with a 42 nm cap; M2 the 1d-class B-ACL open at −25 °C; M3 the 4F² square-lattice open. (Ch. 1.5.1, 14.7)

**Main etch (ST2):** The step that cuts the carbon to the endpoint: 144.4 s, 12 mTorr, O₂/COS/N₂/Ar. (Ch. 5.4)

**Merged holes:** Neighbouring holes whose web has broken: a short, not an open; 2 × 10⁻¹⁰ per hole (17σ on the Gaussian). (Ch. 4.5, 13.5)

**Micromask:** A small involatile island (SiOₓ, B₂O₃) that blocks the carbon beneath it and leaves a pillar or a closed hole. (Ch. 9.3.2, 13.4)

**Minimum web:** The thinnest wall between two holes, at the bow: 45 − 32.8 = 12.2 nm (M1), 10.5 nm (M0); specification ≥ 11.0 nm. (Ch. 10.3.1)

**Mold:** The 1.60 µm oxide-nitride stack that the carbon masks; etched next, in Book #29. (Ch. 1.1.1)

---

## N

**NF₃ clean:** A 60 s fluorine clean every 25 wafers that removes the SiOₓ build-up; resets the wall and is followed by a 12 s season. (Ch. 5.3.2, 9.1.2)

**Not-open hole:** A hole whose exit does not reach the stop; the main line of the 3 × 10⁻⁹ per-hole budget. (Ch. 4.4, 13.1)

---

## O

**OES (optical emission spectroscopy):** The in-situ signal source of the endpoint: CO 483.5 nm, Ar 750.4 nm, SO, CN, SiF. (Ch. 8.1)

**Overetch (OE):** The time after the endpoint: ST3a (11 s, clears 85 nm) and ST3b (7 s, smooths); 18 s in M1. (Ch. 5.4, 8.2.1)

---

## P

**Passivation:** The protection of the carbon wall against lateral attack by a film supplied by the etch (S–C and cap-sourced SiOₓ); coverage θ = 1/(1 + x). (Ch. 3.4, 7.1)

**Pinch-off:** The closure of a hole by a narrowing larger than the closure threshold; a tail event with scale Δ₀ = 1.34 nm and rate 0.7 × 10⁻⁹. (Ch. 13.3)

**Placement budget:** The allowance of 1.5 nm for the mask-open shift and tilt; M1 uses 1.4 nm (tilt 1.2, wiggle 0.7, compensated relaxation 0.27). (Ch. 12.6)

**Pulsing:** Modulating the 2 MHz bias at 5 kHz with a 70% duty; lets the film grow in the off-time, reduces x₀ by 11%. (Ch. 5.2.3, 6.3)

---

## R

**Radical trim:** An isotropic or near-isotropic removal of carbon by neutrals; 0.5 nm per side at the top and 0.1 nm at the exit after 22 s. (Ch. 7.4)

**Ridge test structure:** Line–space ridges, 14 nm at 45 nm pitch, in the scribe; fail like the web and give the top loss by IR scatterometry. (Ch. 11.1, 15.2)

**Rework:** Stripping the mask, redepositing, re-patterning and repeating the open; allowed once. (Ch. 16.1.2)

---

## S

**SADP × 2 (self-aligned double patterning, twice):** The route that produces the 60° hexagonal hole pattern in the cap, with three families. (Ch. 4.1.1)

**Season:** A 12 s COS-rich step with a cover wafer after an NF₃ clean that rebuilds the sulfur on the wall and holds the first-wafer bow to 0.77 nm. (Ch. 5.3.2)

**Shoulder:** The part of the web top where the cap has failed and the carbon erodes (190 nm below the crest in M1). (Ch. 11.3)

**SiON cap:** The PECVD silicon oxynitride cap, n = 1.90 at 193 nm; 40 nm; v_cap = 0.237 nm/s. (Ch. 2.2.2)

**SOC (spin-on carbon):** A low-density carbon (1.35 g/cm³, 35 at% H); opens 2.7 times faster than ACL; shown only for comparison. (Ch. 2.1.2)

**Stress relaxation:** The relaxation of the film stress at the edge of an array block, ε = σ(1 − ν)/E = 0.30%; shifts the top of the outer row by 2.7 nm over 15 rows. (Ch. 12.2)

**Sulfur film (S–C):** The loosely bound film from COS that passivates the wall at depth; 0.4 monolayer at the bow zone, 0.1 at the exit. (Ch. 7.2.1)

---

## T

**Tilt (ion):** The angle of the ion trajectory from the vertical at the wafer edge, set by the ring's wear; 0.05° shifts the exit by 1.2 nm at 147 mm. (Ch. 4.3, 5.5.2, 12.4)

**Top CD:** The CD just below the cap, 32.1 nm; sets the web under the cap. (Ch. 10.1.1)

**Top loss:** The height of carbon removed from the top of the web during the open, 50 nm in M1; L = ER_top x²/(2τ_w). (Ch. 11.2)

**Transfer coefficient:** The fraction of a cap error that reaches the exit (CD, LCDU, LER). (Ch. 4.2)

---

## V

**Virtual metrology:** Prediction of the top loss (6 nm), the exit CD (0.20 nm) and the bow (0.06 nm) from tool signals. (Ch. 15.5)

**Volatility rule:** Products must leave and passivants must stay: CO, CO₂, HCN leave; SiOₓ, S–C and C–N films stay. (Ch. 3.1.2)

---

## W

**W-ACL (tungsten-doped ACL):** An extreme carbon mask (2.6 g/cm³, W 10 at%); ACL:oxide 11–12; opened at 0.45 of the ACL rate; 1150 nm. (Ch. 2.1.2, 14.2)

**Web:** The wall between two holes: 45 − 31 = 14.0 nm at the exit, 12.2 nm at the bow in M1. (Ch. 1.1.3, 4.5)

**Wiggling:** The tilt or bend of a web by an asymmetric stress; 0.70 nm (3σ) for M1, 1.07 nm for M0 (fails the 1.0 nm limit). (Ch. 12.3)

**Window (process):** The range of a parameter within which the specification is met. (Ch. 6.6.1; Appendix D)

---

## Y

**Yield (die):** The fraction of die that function; the open's contribution is the unrepairable fraction, 1.02% for M1 and 1.50% for M0. (Ch. 16.3)

---

**Glossary Version:** 1.0  
**Last Updated:** 2026-10-05
