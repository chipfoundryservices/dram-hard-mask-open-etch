# Index: Book #35 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 16–24 hours for the complete book (about 15.5 hours of text, more with the study questions); 5–8 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the role of the hard mask, the carbon films and the cap, carbon-open plasma chemistry and the passivation model, honeycomb patterning and hole statistics |
| II | 5–9 | Hardware: CCP chambers, profile levers, passivation engineering and cyclic processes, endpoint, walls, residue and the post-open hold |
| III | 10–14 | Phenomena: profile and CD budget, top loss and the cap, web mechanics and wiggling, not-open and stochastic defects, advanced mask schemes |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Hard Mask & Why It Must Be Opened](./chapters/01-hard-mask-role.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** What is cut in the carbon before the mold is touched, how many holes, and what must the open deliver?

**Key Topics:**
- 1.718 × 10¹⁰ holes per die and 1.546 × 10¹³ per wafer; 31 nm holes at 45 nm pitch: 43.5% open, 14 nm webs, hole aspect ratio 44, web aspect ratio 96
- 2.03 m² of carbon wall and 1.40 × 10²¹ carbon atoms (28.4 mg) removed per wafer
- Oxygen has no native passivation: the wall must be more than 99% protected by a film the etch supplies
- Book #29's 89.3° is the angle of the foot (the last 50 nm); the full-height angle is 89.98°
- Routes M0 (baseline), M1 (reference), M2 (1d array, boron-doped carbon); the specification sheet

**Critical Equations:** holes = bits; open fraction = π d²/(4 A_cell); wall area = π d h; web = p − CD  
**Study Questions:** 6

---

### Chapter 2: [The Mask Stack — Carbon Films, Cap, Resist & the Incoming Surface](./chapters/02-mask-stack-carbon-films.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What film does the open cut, and why is a 40 nm cap a clock rather than a mask?

**Key Topics:**
- Carbon families (ACL, HD-ACL, SOC, B-ACL, W-ACL): hydrogen and density set the rate and the bow
- The cap as a cliff: ridge life 146.8 s, exposure of 15.6 s, 1 nm of cap = 21 nm of mask; a ceiling of 1353 nm at 40 nm of SiON
- The thickness budget: 1116 nm floor + 214 nm margin = 1330 nm at 3σ → 1400 nm of carbon; a thicker mask eats itself
- ST1 (BARC and SiON open, 22 s); film variation as time; the open changes the wafer bow by 43 µm

**Critical Equations:** R/R_ACL = [1 + 0.03 (H − 17)] (1.8/ρ)²; t₀ = (h_cap/v_cap)/ρ; net slope of carbon thickness = 1 − 6.3 × 0.125 = 0.21  
**Study Questions:** 6

---

### Chapter 3: [Plasma Chemistry of the Carbon Open](./chapters/03-carbon-open-plasma-chemistry.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** How does a plasma cut 1350 nm of carbon in a 31 nm hole without bowing it?

**Key Topics:**
- Every route to carbon removal is exothermic by hundreds of kJ/mol; selectivity and protection come from kinetics and volatility
- Ion-assisted oxidation at the bottom: Y(E) = 0.355 (√E − 5), 6.9 carbon atoms per 600 eV ion, 12 nm/s at the top
- The bare wall is attacked at 0.54 nm/s; the five-parameter passivation model (x₀, ℓ_O, ℓ_p, c, ℓ_c)
- ARDE: k = 0.011, k₂ = 10⁻⁵; main etch 144.4 s; the tube is neutral-rich and ion-limited
- COS buys passivation at 20% of the cap selectivity; the hydrogen alternative

**Critical Equations:** Y(E); v_b = γΓ_O/n_C; θ = 1/(1 + x); ℓ = d/√(2s); ER = ER₀/(1 + kA + k₂A²); ∂h/∂w  
**Study Questions:** 6

---

### Chapter 4: [Honeycomb Patterning, Pattern Transfer & Hole Statistics](./chapters/04-honeycomb-pattern-transfer-statistics.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** What does the open transfer from the cap, and how many holes may fail?

**Key Topics:**
- SADP × 2 at 60° and EUV; the three families (1:2:1) and the family offset
- Transfer coefficients: exit CD = 31.0 + G (cap CD − 32.0), G = 1.10 (M1), 1.30 (M0); LCDU, LER (2.5 → 1.95 nm), ellipticity
- Placement budget 1.4 of 1.5 nm
- The hole count as a specification: 3 × 10⁻⁹ per hole, 52 per die, and the budget by line
- A web 17σ thick is not safe: tails set the rate

**Critical Equations:** Exit CD = 31.0 + G (cap CD − 32.0); defects per die = N × rate; web = p − CD_bow; σ_t  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [CCP Chambers for the Carbon Open](./chapters/05-ccp-chambers-carbon-open.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Focus:** What does a 44:1 carbon open ask of a chamber built for oxide?

**Key Topics:**
- 60/2 MHz CCP; sheath and ion transit (154 ns); ion angle 0.91°; pulsing at 5 kHz, 70%
- Chamber memory: first-wafer bow 1.34 nm (no season), 0.77 nm with the season; NF₃ clean every 25 wafers
- The full M1 recipe (ST1 + ST2 + ST3a + ST3b = 184 s); M0 for comparison
- Silicon parts; edge ring tilt 0.08° per 100 µm (4,070 wafers); wafer heating 24 K
- Throughput 66 wafers per hour; matching; exhaust: CO, COS, SO₂ and abatement

**Critical Equations:** τ_i; x₀(n) = x₀ [1 + a e^(−n/2.5)]; shift = h tan θ; ΔT = q/h_He  
**Study Questions:** 6

---

### Chapter 6: [Ion Energy, Bias Pulsing & Temperature — The Profile Levers](./chapters/06-ion-energy-pulsing-temperature.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment  
**Focus:** Which knobs move the bow, which move the top loss, and where is the window?

**Key Topics:**
- The energy sweep; 600 eV is the fastest energy that meets the mask specification; the margin-seeking variant at 540 eV
- Pulsing at constant ion flux; frequency; the pulse as the smallest bow lever
- Wafer temperature: 0.04 nm of bow per K; cooling works only if the cap grows with it
- COS as passivant and cap etchant: 0.04 nm of bow for 54 nm of mask
- The sensitivity table and the (energy, COS) window; where M1's bow came from (T −0.89, COS −0.58 nm)

**Critical Equations:** d ln γ/dT = E_a/kT²; x₀ ∝ COS^(−0.46); sensitivity table  
**Study Questions:** 6

---

### Chapter 7: [Passivation Engineering, Cyclic Processes, Trim & Atomic-Layer Carbon Etch](./chapters/07-passivation-cyclic-trim-ale.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Equipment/Research  
**Focus:** What can be added to the main etch, and how far does each film or tool reach?

**Key Topics:**
- Reach ℓ = d/√(2s); two species do two jobs (SiOₓ for the top, S–C for the depth)
- Sulfur: 0.4 monolayer at the bow zone, 0.3% of the COS ends on the wall
- Cyclic deposition–etch (1.5 s / 4.5 s): x₀ × 0.35, bow 0.95 → 0.46 nm for 52 s; the ripple
- Radical trim and atomic-layer carbon etch: both reach the top, not the foot; ion starvation (6% at 35 eV)
- Matching tools to jobs

**Critical Equations:** ℓ = d/√(2s); s = d²/(2ℓ²); cyclic x₀; trim dose = exp(−z/ℓ)  
**Study Questions:** 6

---

### Chapter 8: [Endpoint & In-Situ Monitoring of a Carbon Open](./chapters/08-endpoint-in-situ-monitoring.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Process  
**Focus:** How does the chamber know the carbon has cleared, and what can it not know?

**Key Topics:**
- CO emission at 483.5 nm; only 40% of the CO comes from the wafer; the clear is a population event (σ_t = 1.84 s, 11 s ±3σ)
- The endpoint measures the median hole; the 11 s overetch (5.5 s of 3σ + 5 s of margin) clears 85 nm
- Visible interferometry is blind (126 nm penetration at 633 nm)
- The endpoint cannot see the mask height: EP buys the clear and gives up the top loss (−22 / +30 nm for ±3% in film rate)
- Endpoint logic and failure modes; the cure is a feed-forward to the COS flow

**Critical Equations:** σ_t = RSS/3; CO budget = wafer + bevel + COS; ΔL = 6.3 nm/s × Δt; 1 sccm COS = 1.47 s of cap clock  
**Study Questions:** 6

---

### Chapter 9: [Walls, Residue, Particles & the Post-Open Hold](./chapters/09-walls-residue-particles-post-open.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Equipment  
**Focus:** What is left behind in the chamber, in the hole, and on the wafer until the capacitor etch?

**Key Topics:**
- Wall films: SiOₓ grows 1.9 nm per wafer (46 nm at 25 wafers); the clean interval is set by the first wafer, not by particles (the limit would allow 75)
- Particles: footprint of a particle, the 81 nm killer, adders ≥ 30 nm and ≥ 80 nm
- Residues: sulfur and carbon films, the micromask as a count of rare events
- No wet clean (contact angle 95°, 6.6 MPa Laplace pressure in a wetted hole)
- The hold: 0.2 mg of water in 4 h; 150 °C, 30 s degas removes 90%

**Critical Equations:** film growth per wafer; adders vs film thickness; P = 4γ cos θ/d; θ_w = 0.9 (1 − e^(−t/8 h))  
**Study Questions:** 6

---

## Part III: Phenomena (Chapters 10–14)

### Chapter 10: [Mask Profile, CD Budget & Uniformity](./chapters/10-profile-cd-budget-uniformity.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What three numbers describe a 1350 nm column, and what does each one do?

**Key Topics:**
- The column at three heights: top 32.1, bow 32.8 (+0.67 nm at 370 nm), exit 31.0 nm; the foot angle is local
- Why the angle is the wrong number (0.021° moves the CD 1 nm); the exit is the aperture the capacitor etch sees
- The bow and the web (12.2 nm for M1, 10.5 nm for M0); stiffness goes as t³
- The CD budget from cap to exit (0.99 nm); the exit CD is insensitive to the passivation levers
- Uniformity: across the wafer (+0.40 nm at 147 mm), the array edge (0.55 nm at row 1), loading and the product change

**Critical Equations:** t_web = p − CD_bow; exit CD budget (RSS); offset(n) = 0.55 e^(−(n − 1)/1.4)  
**Study Questions:** 6

---

### Chapter 11: [Top Loss, Facets & Cap Consumption](./chapters/11-cap-top-loss-facets.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** Why does the mask lose 50 nm from the top, and why is the mean the wrong number?

**Key Topics:**
- The cap on a 14 nm web is a ridge; shoulders retreat at 0.215 nm/s; ridge life 146.8 s
- The top-loss law L = ER_top x²/(2τ_w); 6.3 nm per second of overetch
- The shoulder and the crest: edge height 1210 nm, margin 94 nm
- Sensitivities: 1 nm of cap = 21 nm of mask; energy and COS trade loss for time and bow
- Removing the cliff: cap 42 nm (M1-c), 540 eV, COS 26; the cap specification; what the capacitor etch inherits; M2's 60 nm cap

**Critical Equations:** L = ER_top x²/(2τ_w); x = T − t₀; τ_w = (W/2)/v_h  
**Study Questions:** 6

---

### Chapter 12: [The Webs — Mechanics, Wiggling, Twist & Distortion](./chapters/12-webs-mechanics-wiggling-distortion.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Does a mask of 14 nm webs 1350 nm tall hold its shape, and where does it move?

**Key Topics:**
- The honeycomb as a structure: E* = ηE (20 GPa for M1), the web does not buckle or collapse
- Stress relaxation at every array edge: ε = 0.30%, 2.7 nm of shift, 15 rows; 80% litho compensation
- Wiggling: the bimorph model; 0.70 nm (M1), 1.07 nm (M0, fails)
- Tilt, twist and the steered hole; ellipticity near the edge and the hexagonal distortion
- The placement budget: 1.4 of 1.5 nm

**Critical Equations:** E* = ηE; ε = σ (1 − ν)/E; κ = 6 (1 − ν) a_f σ_s t_s/(E t²)  
**Study Questions:** 6

---

### Chapter 13: [Residue, Not-Open Holes & Stochastic Defects](./chapters/13-residue-not-open-stochastic-defects.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** What fills the 3 × 10⁻⁹ budget, and which lines can be moved?

**Key Topics:**
- The defect classes; litho-origin defects and the SiON overetch (e^(−0.5 t)); EUV partial opens
- Pinch-off: closure below 12 nm, tail scale Δ₀ = 1.34 nm; a 5% change in Δ₀ is a factor of 2
- Micromasks and footing; merged holes (17σ on the Gaussian, 2 × 10⁻¹⁰ in practice)
- What a defect becomes (open, short, cluster) and how it is detected
- Where to spend effort: the largest levers sit in exponents or on another tool

**Critical Equations:** P(narrowing > δ) = P₀ exp(−δ/Δ₀); d ln p/dΔ₀ = δ_c/Δ₀²; defects per die = N × rate  
**Study Questions:** 6

---

### Chapter 14: [Advanced Schemes — Boron-Doped Carbon, Taller Masks, Metal-Containing Masks, Hybrid Caps & 4F² / 3D DRAM](./chapters/14-advanced-mask-schemes.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** What changes when the pitch falls to 37 nm, the array turns square, or the mask is replaced?

**Key Topics:**
- Boron-doped carbon and the 1d-class open (M2): CF₄ 3%, −25 °C, cyclic; 259 s; bow 0.46 nm, web 9.5 nm
- Three masks for the 1d array: undoped ACL, B-ACL, W-ACL; the module cannot be optimized alone
- Hybrid (silicon) caps remove the cliff; colder wafers (−60 °C) and what they cost
- 4F² vertical-channel DRAM (M3): square mesh, axis web 7.4 nm, wiggle 0.90 nm (fails 0.67); the fixes
- 3D DRAM; all the routes on one page

**Critical Equations:** cap for x = 17.9 s; ARDE time to depth for 26 nm; cyclic x₀; web (axis, diagonal)  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** All roles  
**Focus:** Measuring a mask that cannot be seen from above, and holding the cap's clock

**Key Topics:**
- The measurands and the ladder: CD-SAXS, HV-SEM at 30–50 keV, IR scatterometry on a ridge test structure
- Scribe test structures; large-area inspection: 0.17 cm² to see 30 events, 18% precision
- COS feed-forward ΔCOS = 2.9 ΔH − 0.085 Δh_ACL + 2.5 Δh_cap; do not feed forward the carbon thickness
- EWMA on the exit CD (λ = 0.3, limits ±0.315 nm); bow control; virtual metrology (top loss 6 nm)
- Matching and qualification; metrology cost $1.10 per wafer

**Critical Equations:** ΔCOS = 2.9 ΔH − 0.085 Δh_ACL + 2.5 Δh_cap; z_k = λ x_k + (1 − λ) z_{k−1}; limit = Lσ √(λ/(2 − λ))  
**Study Questions:** 6

---

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Focus:** Which route, at what cost, for what yield?

**Key Topics:**
- Customers of the open; queue times (8 h, 24 h, 4 h in air / 12 h in a nitrogen FOUP); the open can be reworked once
- Yield signatures in the bitmap; the yield model: repair absorbs isolated defects (2 × 10⁻⁵ per die); 1.02% loss from the unrepairable
- Equipment for 150,000 starts a month: 14.6 chambers (4 platforms) for M1; six platforms for M2 and M3; 31 kg of COS per month
- Module cost: $14.4 / $15.1 / $15.2 / $24.0 / $24.9 for M0 / M1 / M1-c / M2 / M3; $0.036 per second
- Break-even yield gain: M1 over M0 0.052%; new-product checklist; the handoff sheet

**Critical Equations:** chambers = starts/(wafers per chamber per month); fixed cost = (0.248 + 0.06) × tool + facility, per wafer; break-even = Δcost/wafer value  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Geometry, Transport & Statistics Calculations](./appendices/E-geometry-transport-statistics-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 6 → 7 → 10 → 11 → 13 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 8 → 9 → 15 → App. C, F  
**Integration Engineer (6 h):** Ch. 1 → 2 → 4 → 10 → 14 → 16  
**Device / Design Engineer (5 h):** Ch. 1 → 4 → 10 → 12 → 16  
**Researcher (9 h):** Ch. 3 → 4 → 7 → 11 → 12 → 13 → App. B, E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Hole counts, open fraction and web geometry, carbon load and gas budget, hydrogen and density rate scaling, ridge life and top loss, thickness budget, ion yield and ER₀, bare lateral rate and Arrhenius factors, passivation coverage and bow, ARDE and time to depth, Clausing and Coburn–Winters transport, family offset and transfer gain, LCDU and edge roughness, placement budget, sheath and ion transit, first-wafer effect, edge-ring tilt, wafer heating, sensitivity tables and windows, cyclic deposition–etch, trim dose and ALE cycles, CO budget and endpoint statistics, feed-forward arithmetic, wall film growth and particle adders, wetting pressure and moisture uptake, CD budget, web stiffness, array-edge relaxation, ligament modulus and the wiggle, pinch-off tail statistics, micromask counts, boron and BF₃ chemistry, 1d and 4F² mask options, large-area inspection, EWMA control, virtual metrology, repair and yield, equipment sizing, cost of ownership, break-even yield

Examples:
- Compute the holes per die and the carbon removed per wafer for a new array
- Find the main-etch time for a 26 nm hole from the ARDE law
- Predict the top loss for a cap that is 2 nm thicker, and find the COS flow that restores it
- Find the bow of the first wafer after an NF₃ clean with a shortened season
- Find the wafers at which the SiOₓ film reaches the particle limit
- Compute the Laplace pressure of a wetted hole at a new contact angle
- Compute the edge relaxation for a film with half the stress
- Find the change in pinch-off rate for a 3% change in the tail scale
- Design an EWMA chart for the exit CD and compute its limits
- Size the equipment and compute the module cost and the break-even yield for a route

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-05  
**Next:** Begin [Chapter 1: The Hard Mask & Why It Must Be Opened](./chapters/01-hard-mask-role.md)
