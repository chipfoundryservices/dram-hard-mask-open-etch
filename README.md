# Book #35: DRAM Hard Mask Open Etch — Cutting Seventeen Billion Holes in 1.4 µm of Amorphous Carbon, Sidewall Passivation Without Polymer, and the 14 nm Webs the Capacitor Etch Inherits

## Overview

**Book #35** is a technical reference on **DRAM hard mask open etch**: the plasma etch that perforates the amorphous-carbon hard mask of the capacitor module. Before the oxide etch of the mold can start, a 1.40 µm film of carbon (ACL) under a 40 nm SiON cap must be cut with the same honeycomb as the capacitor itself: about **17 billion holes on a 16 Gb die**, each **31 nm** wide at its exit, on a **45 nm hexagonal pitch**. They are tubes at aspect ratio **44:1**, separated by carbon **webs 14 nm thick and 1.35 µm tall** (aspect ratio 96). The carbon is the hard mask, the plasma that perforates it is the hard mask open, and its result is the only thing the capacitor etch ever sees of the lithography.

Book #29 (*DRAM Capacitor Hole Etch*) states what the mask open must deliver (a 31.0 nm exit, a straight wall, a mask 1350 nm tall) and refers the how to the companion volumes. Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) needs the same mask taller and harder, a 56:1 opening in boron-doped carbon. This book is the how. It treats the mask open as **the first etch of the capacitor module, and the one whose errors no later etch can remove**: the exit CD becomes the top CD of the mold hole, the web becomes the mask that stands in the mold etch, and every defect of the open is a failing bit.

Four things make the etch hard. **Oxygen has no native passivation**: the reagent that cuts the bottom of the hole attacks its wall at 0.54 nm/s, so the wall must stay more than 99% protected by a film the etch itself supplies, and there is no polymer to do it. **The wall is large and the load is real**: a wafer carries 2.03 m² of carbon wall and releases 1.40 × 10²¹ carbon atoms (22 sccm) into the plasma. **The cap is a clock, not a mask**: on a 14 nm web it is a ridge whose shoulders fail first, and 1 nm of SiON is 21 nm of mask. **The mask cannot be seen from above**: light does not reach the bottom, and the endpoint measures the median hole and not the height.

**Cut seventeen billion straight 31 nm holes in 1.4 µm of carbon, leave 14 nm webs standing 1350 nm tall, and lose no more than 58 nm from the top.** This book covers the chemistry, equipment, process phenomena, and production engineering of doing that.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing carbon opens with sulfur passivation and a smoothing overetch; controlling bow, exit CD, foot, top loss, web, and residue; running the (energy, COS, temperature) window
- **Equipment Engineers**: specifying CCP chambers for the carbon open, pulsed bias, cold chucks, seasoning, endpoint on a population of holes, and COS, CO, and SO₂ abatement
- **Integration Engineers**: choosing the mask (ACL, boron-doped, tungsten-doped, hybrid cap), the cap thickness, and the open route for the 1b, 1d, and 4F² arrays; setting queue times and rework rules
- **Device Engineers**: understanding how the open's exit, web, top loss, and defects become capacitor CD, weak cells, and failing bits, and how repair absorbs them
- **Researchers**: studying passivation-film models of lateral etching, the top-loss law of a thin ridge, bimorph wiggling of perforated masks, and pinch-off tail statistics

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). **Book #29 (*DRAM Capacitor Hole Etch*)** is the direct customer of this book: it defines the reference array, the mold, and the exit CD, and treats the mask open as an input. Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) defines the 1d-class array and the boron-doped mask. Books #30 (*Mold Etch*), #32 (*Electrode Etch*), #33 (*Dielectric Etch*), and #34 (*Support Layer Etch*) follow in the capacitor flow. The companion volume *Carbon Hard Mask Etch* covers carbon masks in more general settings.

---

## Technical Scope

### Core Concepts Covered

**Function & Films:**
- What the hard mask does and why it is opened by a separate plasma; the count of holes, carbon, and wall per die and per wafer
- The carbon film families (ACL, HD-ACL, SOC, B-ACL, W-ACL): hydrogen, density, stress, and what the plasma sees
- The SiON cap as a clock; the thickness budget; the ST1 open of the cap and the resist
- The honeycomb as a structure: webs, nodes, and the 14 nm of carbon the capacitor etch inherits

**Etch Chemistry:**
- Carbon removal: oxygen, hydrogen, and nitrogen routes; the volatility rule (products must leave, passivants must stay)
- Ion-assisted oxidation at the bottom: Y(E) = 0.355 (√E − 5), 12 nm/s at the top, 0.659 of that at the exit
- The bare lateral rate (0.54 nm/s) and the passivation-film model with five parameters; the bow as a measurement of coverage
- Sulfur from COS and silicon oxide from the cap: two species with two reaches, ℓ = d/√(2s)
- Cyclic deposition–etch, radical trim, and atomic-layer carbon etch: what each reaches in a 44:1 tube

**Equipment Design:**
- CCP chambers: dual frequency, sheath, ion transit, pulsing, and the choice of 600 eV at 5 kHz, 70% duty
- Chamber memory: the first-wafer effect, the season, and the NF₃ clean interval; edge-ring tilt and wafer heating
- Endpoint on a population of 17 billion holes: the CO emission, the median hole, and what an endpoint cannot see
- Walls, particles, micromasks, the post-open hold, and the reason there is no wet clean

**Process Phenomena:**
- The profile as three CDs and a foot angle: top, bow, and exit; the CD budget and its uniformity
- Top loss: the ridge law L = ER_top x²/(2τ_w), the shoulder and the crest, and the cheapest cure
- Web mechanics: stress relaxation at array edges, bimorph wiggling, ellipticity, and the placement budget
- Not-open holes and stochastic defects: litho-origin plugs, pinch-off as a tail, micromasks, merged holes

**Production Integration:**
- Boron-doped and tungsten-doped masks, hybrid caps, colder wafers, 4F² square lattices, and 3D DRAM
- Metrology: CD-SAXS, high-voltage SEM, IR scatterometry on a ridge structure, scribe test structures
- COS feed-forward to hold the cap's clock, EWMA on the exit CD, virtual metrology
- Yield signatures, repair, equipment for 150,000 wafer starts per month, cost of ownership, break-even yield

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1d generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Mask stacks:** 1.4 µm ACL under a 40 nm SiON cap (primary focus); 1.5 µm boron-doped carbon under a 60 nm cap at the 1d array; tungsten-doped and hybrid-cap variants
- **Process sequence:** The mask open follows the cap and resist patterning (SADP × 2 or EUV) and precedes the mold etch (Book #29), the support open and dip-out (Book #30, #34), the electrode (Book #32), and the dielectric (Book #33)
- **Manufacturing scale:** 300 mm wafers; one open of 184 s of plasma per wafer in M1; 15 chambers for 150,000 wafer starts a month

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Hard Mask & Why It Must Be Opened**
- What the mask does; 1.718 × 10¹⁰ holes per die; the honeycomb of 14 nm webs
- 2.03 m² of wall and 22 sccm of carbon per wafer; the oxygen problem
- What the open delivers to the capacitor etch; Book #29's 89.3° is the foot
- The routes M0, M1, M2; the specification sheet

**Chapter 2: The Mask Stack — Carbon Films, Cap, Resist & the Incoming Surface**
- ACL, HD-ACL, SOC, B-ACL, W-ACL; hydrogen and density
- The cap as a cliff; the thickness budget; a thicker mask eats itself
- The short ST1 etch before the long one; film stress and wafer bow

**Chapter 3: Plasma Chemistry of the Carbon Open**
- Bonds, products, and the volatility rule
- Ion-assisted oxidation; the bare wall; the passivation-film model
- Transport, ARDE, and time to depth; selectivity to the cap and the stop

**Chapter 4: Honeycomb Patterning, Pattern Transfer & Hole Statistics**
- SADP × 2 and EUV; families; transfer coefficients for CD, LCDU, and LER
- Placement, overlay, and tilt
- The hole count as a statistical specification; the web as a Gaussian margin and a tail

### Part II: Hardware Design (5 Chapters)

**Chapter 5: CCP Chambers for the Carbon Open**
- Sheath, ion transit, and pulsing; chamber memory and the first-wafer effect
- The full M1 recipe; consumables, edge ring, and ion tilt
- Temperature control; throughput, matching, and exhaust

**Chapter 6: Ion Energy, Bias Pulsing & Temperature — The Profile Levers**
- Energy sweep and the fastest energy that meets the mask
- Duty and frequency; wafer temperature; COS as a trade
- The sensitivity table and the (energy, COS) window; where M1's bow came from

**Chapter 7: Passivation Engineering, Cyclic Processes, Trim & Atomic-Layer Carbon Etch**
- The passivation menu; sulfur as the M1 choice; carry-over
- Cyclic deposition–etch and its ripple; radical trim; carbon ALE
- Matching tools to jobs

**Chapter 8: Endpoint & In-Situ Monitoring of a Carbon Open**
- CO emission, the transition, and the median hole
- Why interferometry fails; signals at the steps; endpoint logic
- What an endpoint is worth; the feed-forward to the COS flow

**Chapter 9: Walls, Residue, Particles & the Post-Open Hold**
- Wall films, particle limit, and the clean interval
- Particles and the killer footprint; residues and the micromask
- Why the mask is not wet-cleaned; moisture uptake and the degas

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Mask Profile, CD Budget & Uniformity**
- The column at three heights; the angle is the wrong number
- The bow and the web; the foot and the exit
- The CD budget; uniformity across the wafer, at the array edge, and with loading

**Chapter 11: Top Loss, Facets & Cap Consumption**
- The ridge on the web; the top-loss law and its table
- The shoulder and the crest; sensitivities; removing the cliff
- The cap specification; what the capacitor etch inherits; the cap of M2

**Chapter 12: The Webs — Mechanics, Wiggling, Twist & Distortion**
- The honeycomb as a structure; stress relaxation at the array edge
- Wiggling: the bimorph model; tilt, twist, and the steered hole
- Ellipticity, hexagonal distortion, and the placement budget

**Chapter 13: Residue, Not-Open Holes & Stochastic Defects**
- The defect classes; litho-origin defects and the SiON overetch; EUV
- Pinch-off as a tail event; micromasks and footing; merged holes
- What a defect becomes; detection; where to spend effort

**Chapter 14: Advanced Schemes — Boron-Doped Carbon, Taller Masks, Metal-Containing Masks, Hybrid Caps & 4F² / 3D DRAM**
- Boron-doped carbon and the 1d-class open (M2); three masks for the 1d array
- Hybrid caps; colder wafers
- 4F² vertical-channel DRAM (M3); 3D DRAM; all the routes on one page

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- The measurands and the ladder; scribe test structures
- Large-area inspection and the bitmap
- Feed-forward, feedback, and virtual metrology; matching and qualification

**Chapter 16: Integration, Yield & Cost of Ownership**
- Customers, queues, and rework; yield signatures and the yield model
- Equipment for 150,000 wafer starts per month; cost of ownership
- When the extra dollar pays; the new-product checklist and the handoff sheet

---

## Key Technical Themes

1. **The mask is the first hole.** Seventeen billion holes, 31 nm wide and 44:1 deep, are cut in 1.4 µm of carbon before the mold is touched. The exit is the aperture the capacitor etch sees, and nothing downstream repairs the open.
2. **Oxygen has no native passivation.** The bare wall is attacked at 0.54 nm/s. To bow by less than 1 nm the wall must be more than 99% covered by a film the etch supplies: sulfur from COS for the depth, silicon oxide from the cap for the top.
3. **The cap is a clock.** On a 14 nm web the SiON is a ridge whose shoulders erode first; the top loss is L = ER_top x²/(2τ_w), 6.3 nm for every second of overetch, and 1 nm of cap is 21 nm of mask.
4. **The webs are the mask the capacitor etch stands behind.** A web of 12.2 nm at the bow is 87% of nominal and a web of 10.5 nm is 75%; stiffness goes as the cube of thickness, and stress relaxes at every array edge.
5. **The endpoint cannot see the height.** It measures the median hole; the open buys the clear and gives up the top loss, and the COS flow is the one knob that moves the cap's clock without moving the carbon's.
6. **The specification is a count.** 3 × 10⁻⁹ per hole is 52 per die; repair absorbs the isolated defects, and the budget is filled by tails (pinch-off, micromasks, litho plugs), not by particles.
7. **The open cannot be optimized alone.** An undoped 1.8 µm mask is the cheapest to open and the most expensive to etch through; every scheme pays in cap or in time.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): fluorocarbon open of the SiON cap and the mold
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, chucks, endpoint, chamber matching
- **Book #29** (DRAM Capacitor Hole Etch): the customer of this book; the reference array (6F², 45 nm pitch, 16 Gb), the mold, the mask specification; the SADP × 2 pattern
- **Book #30** (DRAM Capacitor Mold Etch) and **Book #34** (DRAM Capacitor Support Layer Etch): the support open and dip-out downstream
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): the 1d-class array, the boron-doped mask taken here as M2
- **Book #32** (DRAM Capacitor Electrode Etch): the stage that follows the mold in the capacitor flow
- **Book #33** (DRAM Capacitor Dielectric Etch): the dielectric whose coverage inherits the hole's profile
- **Companion volume:** *Carbon Hard Mask Etch* (carbon masks in general)

Book #29 treated the carbon open as an input. This book asks what the open does to the carbon, and what the carbon now asks of everything that follows.

---

## File Organization

```
dram-hard-mask-open-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-hard-mask-role.md
│   ├── 02-mask-stack-carbon-films.md
│   ├── 03-carbon-open-plasma-chemistry.md
│   ├── 04-honeycomb-pattern-transfer-statistics.md
│   ├── 05-ccp-chambers-carbon-open.md
│   ├── 06-ion-energy-pulsing-temperature.md
│   ├── 07-passivation-cyclic-trim-ale.md
│   ├── 08-endpoint-in-situ-monitoring.md
│   ├── 09-walls-residue-particles-post-open.md
│   ├── 10-profile-cd-budget-uniformity.md
│   ├── 11-cap-top-loss-facets.md
│   ├── 12-webs-mechanics-wiggling-distortion.md
│   ├── 13-residue-not-open-stochastic-defects.md
│   ├── 14-advanced-mask-schemes.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-geometry-transport-statistics-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Plasma etching of the amorphous-carbon hard mask of a DRAM capacitor module: the 6F² reference route (M0, M1, M1-c) and the 1d-class (M2) and 4F² (M3) extensions  
✅ The carbon films, the SiON cap, and the resist stack; the ST1 open and the incoming surface  
✅ Oxygen/COS carbon chemistry with sulfur and silicon-oxide passivation; cyclic, radical, and ALE finishing  
✅ Chamber design, pulsing, temperature, chamber memory, endpoint, wall and particle management, and the post-open hold  
✅ Profile, CD budget, top loss, web mechanics, wiggling, residue, and stochastic defects  
✅ Boron- and tungsten-doped masks, hybrid caps, colder wafers, 4F² and 3D DRAM  
✅ Metrology, APC, yield, equipment sizing, and cost of ownership  

### What This Book Does NOT Cover
❌ The capacitor hole etch through the oxide-nitride mold (see Books #29 and #31)  
❌ The support open, HF dip-out, and drying (see Books #30 and #34); the electrode and dielectric (see Books #32 and #33)  
❌ The deposition of the carbon and the cap in detail, and the lithography (cap CD, overlay, and EUV are inputs here)  
❌ Mask strip after the capacitor etch  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate and literature trends, simple closed-form models of transport, passivation, mechanics, and statistics, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array and mold of Book #29: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal pitch, a 16 Gb die with 900 dies per wafer, and a 1.60 µm mold. The mask is ArF-immersion resist over a 25 nm BARC, a 40 nm SiON cap, and 1400 nm of ACL (1350 nm after the open, exit CD 31.0 nm). Three open processes are carried through the book. **M0** is the baseline: continuous 800 eV bias, 20 °C, 6 sccm of COS, 181 s, a bow of 2.0 nm, a minimum web of 10.5 nm, and a top loss of 62 nm; it fails four lines of the specification on purpose. **M1** is the reference: 5 kHz pulsed bias at 70% duty and 600 eV, 30 sccm of COS, a 10 °C wafer, and a two-part overetch (11 s clear and 7 s smoothing); 184 s, a bow of 0.67 nm, a web of 12.2 nm, and a top loss of 50 nm. **M2** is the 1d-class open in boron-doped carbon at −25 °C with a cyclic 1.5 s / 4.5 s scheme: 259 s, a bow of 0.46 nm. **M1-c** (a 42 nm cap) and **M3** (a 4F² square lattice) are variants. Models are written out in Appendix E. Where this book's number differs from a sibling's, the difference is noted in the text (for example, the 89.3° of Book #29 is the angle of the foot, not of the wall). Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #35 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-hard-mask-role.md)**: The Hard Mask & Why It Must Be Opened

---

**Book #35 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
