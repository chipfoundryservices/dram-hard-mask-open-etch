# Chapter 1: The Hard Mask & Why It Must Be Opened

## Overview

Every hole in the capacitor mold is cut through another hole. Before the oxide etch of Book #29 can start, a 1.40 µm film of amorphous carbon must be perforated with the same honeycomb: about seventeen billion holes on a 16 Gb die, each 31 nm wide at its exit, on a 45 nm hexagonal pitch. The carbon is the **hard mask**, the plasma that perforates it is the **hard mask open**, and its result is the only thing the capacitor etch ever sees of the lithography.

A photoresist could not survive the 5-minute fluorocarbon etch that follows, so the pattern is moved into carbon first. That makes the mask open an etch of its own, and a hard one. The holes are 44:1 tubes, deeper for their width than most contact etches, cut in a material that has no native sidewall protection, whose product (carbon monoxide) leaves every surface it forms on, and whose reagent (atomic oxygen) attacks the wall of the hole it is cutting. Between the holes stand **webs of carbon 14 nm thick and 1.35 µm tall**, an aspect ratio of 96, with nothing to hold them but their own stiffness and the film beneath.

Book #29 (*DRAM Capacitor Hole Etch*) states what the mask open must deliver (a 31.0 nm exit, a wall that is straight, a mask 1350 nm tall) and refers the how to the companion volumes. Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) needs the same mask taller and harder, a 56:1 opening in boron-doped carbon. This book is the how. It treats the hard mask open as **the first etch of the capacitor module, and the one whose errors no later etch can remove**: the exit CD becomes the top CD of the mold hole, the family offset becomes a difference in depth, the tilt and the ellipticity become placement and twist, and the thickness left over becomes the clock of the mold etch.

This chapter explains what the mask does, counts what must be cut, traces what the open hands to the capacitor etch, places the open in the flow, defines the three routes (M0, M1, M2) the book follows, and gives the specification sheet the rest of the book works against.

**Learning Objectives:**
- Describe the hard mask stack and explain why the pattern is moved into carbon before the mold is etched
- Count the holes, the carbon, and the wall area per die and per wafer, and the chemical load of one wafer
- Compute the open fraction, web width, and web aspect ratio of the perforated mask
- Trace each output of the open to what the capacitor etch makes of it
- Distinguish the routes M0, M1, and M2 and say what each gives and costs
- Read the specification sheet and the failure each line protects against

---

## 1.1 What the Hard Mask Does

### 1.1.1 The Reference Stack

```
Reference mask stack (Books #29, #30; top to bottom, as deposited):

  Photoresist          ArF-immersion (≈ 80 nm) or EUV (≈ 40 nm)
  BARC / underlayer    25 nm
  SiON cap             40 nm      masks the ACL open; antireflective layer
  ACL                  1400 nm    PECVD amorphous carbon, 400–600 °C
                                  density 1.8 g/cm³, H 15–20 at%, stress −300 MPa
  ─────────────────────────────────────────────────────────────────────
  Top SiN support      120 nm     the first film of the mold; the stop of the open
  Upper PE-TEOS        650 nm
  Middle SiN support    50 nm
  Lower BPSG           760 nm
  Bottom SiN stop       20 nm
```

The mask open stops on the 120 nm top nitride support. Carbon etches in oxygen at several hundred nanometres per minute and silicon nitride at a few, so the stop is a selectivity of about 60 at the exit of a 44:1 hole, and the open can be extended (overetched) generously without cutting into the mold.

### 1.1.2 Why Carbon, and Why Open It Separately

The mold is 1.6 µm of oxide and nitride, etched in fluorocarbon plasma at ion energies of several kilovolts. Photoresist would be gone in seconds. The mask must survive 616 nm of its own erosion (Book #29: 576 nm in the five mold steps plus a 40 nm allowance for the facet) and still stand at least 500 nm tall at the end. Carbon is the material that does this: dense, sp³-rich, and chemically inert to fluorocarbons, yet removable at the end in an oxygen ash.

Carbon cannot be opened in the oxide-etch chamber. Fluorocarbon chemistry does not remove it; oxygen chemistry does, and oxygen is the one reagent a capacitor-hole chamber is built to keep out. The mask open runs in a chamber of its own, with its own gases, wall conditions, and consumables, and it hands the wafer to the capacitor etch with 1.35 µm of carbon, perforated.

### 1.1.3 The Mask as a Perforated Plate

After the open, the mask is a plate with seventeen billion holes in it. Areas use the 6F² cell of 1734 nm² (as Book #29 does) and linear distances use the 45 nm nominal pitch; the two differ by 1.1%, the rounding of the nominal pitch.

```
The perforated mask (reference exit CD 31 nm):

  Hole area (31 nm circle)         π × 31² / 4 = 754.8 nm²
  Open fraction                    754.8 / 1734 = 43.5%
  Solid fraction                   56.5%
  Web width (nearest neighbours)   45 − 31 = 14.0 nm
  Web height                       1350 nm
  Web aspect ratio                 1350 / 14 = 96
  Web length (node to node)        45/√3 = 26.0 nm
  Node (inscribed circle between
   three holes)                    2 × (26.0 − 15.5) = 21.0 nm
  Hole aspect ratio                1350 / 31 = 43.5 (≈ 44)
```

The mask is not a field of slender posts but a **honeycomb of short thin walls joined at stiff nodes**. Chapter 12 treats its mechanics. Two facts matter now. First, 43.5% of the carbon in the array is gone, so the open exposes a great deal of carbon to the plasma at once. Second, the webs are thin enough that a bow of one nanometre on each of two neighbouring holes takes 14% of the web away.

---

## 1.2 Counting the Holes

### 1.2.1 Holes and Carbon

```
Reference array, 16 Gb die:
  Cells (= holes) per die           16 × 2³⁰ = 1.718 × 10¹⁰
  Gross dies per 300 mm wafer       900
  Holes per wafer                   1.546 × 10¹³
  Array area per die                1.718 × 10¹⁰ × 1734 nm² = 0.298 cm²
  Die area (900 per wafer)          0.785 cm²   (array 37.9% of the wafer)
  Open area per die                 1.718 × 10¹⁰ × 754.8 nm² = 0.1297 cm²
  Open area of the wafer            16.5% (the periphery is covered, and is not opened)

Carbon removed (hole depth 1350 nm):
  Volume per die                    0.1297 cm² × 1.35 × 10⁻⁴ cm = 1.75 × 10⁻⁵ cm³
  Mass per wafer                    1.75 × 10⁻⁵ × 900 × 1.8 g/cm³ = 28.4 mg
  Carbon atom density (ρ 1.8, H 17 at%)   8.87 × 10²² cm⁻³
  Carbon atoms per wafer            1.4 × 10²¹   (2.3 mmol)
```

A wafer's worth of mask is 28 mg. That is little to remove, and it is removed at a rate that matters. Over the 144 s main etch (Chapter 3) the wafer releases 9.7 × 10¹⁸ carbon atoms per second. In the language of gas flow, one standard cubic centimetre per minute is 4.48 × 10¹⁷ molecules per second, so the wafer releases the equivalent of **22 sccm of carbon, 11 sccm of O₂-equivalent consumed as CO, out of 150 sccm of O₂ supplied**. About 7% of the oxygen is spent on the wafer. This is the chemical load of the open, and it is why a product with a different array efficiency needs its recipe checked (Chapter 10).

### 1.2.2 The Wall Area

```
Wall area of one hole           π × 31 nm × 1350 nm = 1.31 × 10⁵ nm²
Wall area per wafer             1.31 × 10⁵ nm² × 1.546 × 10¹³ = 2.03 m²
```

Every wafer leaves the mask-open chamber with **two square metres of carbon wall**, most of it at the bottom of a 44:1 tube. That wall holds adsorbed water, whatever sulfur or silicon oxide the passivation put on it, and whatever the strip cannot reach. It is the reason the mask is not wet-cleaned, the reason queue time to the capacitor etch is limited (Chapter 9), and the reason the sidewall is an engineering problem and not a detail.

---

## 1.3 What the Open Delivers

The mask open is not judged by itself. Each of its outputs becomes an input of the capacitor etch, usually with a gain:

```
Output of the mask open        What the capacitor etch makes of it                   Gain / consequence
─────────────────────────────────────────────────────────────────────────────────────────────────────────────
Exit CD (bottom of the ACL)    Top CD of the mold hole; depth reached at fixed time   ∂h/∂CD = 15 nm per nm (Book #29)
Family offset (SADP×2)         One family of holes reaches the bottom stop later      1.2 nm → 18 nm of depth lag
Exit position and tilt         Position of the hole bottom on the pad                 1 : 1; 0.05° at the edge → 1.2 nm
Ellipticity of the exit        Bottom ellipticity; seeds the twist                    × 2–3; twist variance ∝ e² (Book #31)
Line-edge roughness            Striation on the mold wall                             2–3 nm (3σ) in; spec ≤ 2.0 nm out
ACL height and corner state    Mask budget, facet margin                              1330 nm in; 616 nm consumed
Web width at the bow           Mask integrity, wiggling, mask-hole bridging           1 nm of bow on two holes = 14% of web
Residue at the exit            Blocked hole (not-open)                                3 × 10⁻⁹ per hole of the 8 × 10⁻⁹ budget
Sulfur, moisture on the walls  Contamination and outgassing in the capacitor chamber  2 m² of wall per wafer
```

Where Book #29 states the incoming specification (Section 2.5 of that book), this book derives it from the open's side. The two must agree, and where they do not, the difference is noted in the text.

---

## 1.4 Where the Etch Sits in the Flow

### 1.4.1 The Capacitor Flow

```
Capacitor module (reference), with the books that treat each step:

  Landing-pad module; mold deposition (SiN / PE-TEOS / SiN / BPSG / SiN)    Book #29
  ACL (1.40 µm), SiON cap (40 nm), BARC, resist                              Ch. 2
  Honeycomb patterning (SADP×2 at 60° or EUV)                                Ch. 4; Book #29
  ► HARD MASK OPEN (SiON open, ACL main etch, overetch) ◄                    this book
  Capacitor hole etch (57:1; 91:1 in Book #31)                               Books #29, #31
  ACL strip; clean; TiN fill; top isolation                                  Book #32 (module 1)
  Support-open mask and support layer etch                                   Book #34
  HF dip-out; rinse; dry                                                     Book #30
  ZAZ ALD; top electrode; plate etch; dielectric clear                       Books #32, #33
```

The mask open has two neighbours that set its terms. Upstream is the lithography: a cap with openings of a given CD, shape, family spread, roughness, and overlay (Chapter 4), on an ACL of a given thickness and uniformity (Chapter 2). Downstream is the capacitor etch, which takes a wafer with open, dry, carbon-walled holes and starts cutting within hours (Chapter 9).

### 1.4.2 Book #29's Mask Open and This Book

| | Books #29, #31 | Book #35 |
|---|---|---|
| Treat the mask open as | an input, one paragraph | a module of its own |
| Mask seen as | the clock of the mold etch | a perforated plate that is etched, and then eroded |
| Specification | exit CD, angle, bow, thickness, residue | derived from the plasma, the film, and the statistics |
| Sidewall angle | 89.3° (Book #29) | local angle of the foot; the full-height angle is 89.98° |
| Bow | "no bow > 1 nm" | a depth profile with a model, and a web that thins at the bow |
| Failure modes | not-open, tilt, striation | pinch-off, closure, wiggling, footing, residue, and their statistics |
| Mask materials | selectivity table | opened with different chemistries (B-ACL, W-ACL), each with a cost |

Book #29 quotes a sidewall angle of 89.3° for the opened ACL. Read over the full 1350 nm of wall, that angle would make the top of each hole 16.5 nm wider per side than the exit, 64 nm across against a 31 nm exit, wider than the 45 nm pitch. It cannot be a full-height angle. It is the **local angle of the foot**, the last 50 nm above the exit, where the wall closes by about one nanometre. The angle averaged over the full height, from a 32.1 nm top to a 31.0 nm exit, is 89.98°. Chapter 10 specifies the profile at three heights, which says what an angle cannot.

---

## 1.5 The Routes

### 1.5.1 Three Processes

```
Route  How                                                                Where treated
────────────────────────────────────────────────────────────────────────────────────────────
M0     Baseline: SiON open, then ACL in a continuous (CW) O₂ plasma       Ch. 3, 6, 10, 11
       with a trace of COS; 20 °C; one overetch
M1     Reference: pulsed bias, COS-rich passivation, 10 °C, and an        Ch. 3, 5–13
       overetch whose last 7 s smooths the wall
M2     1d-class extension: B-ACL, 56:1, wafer at −25 °C, cyclic            Ch. 7, 14
       deposition and etch
```

M0 is the recipe most fabs start from. It cuts the carbon quickly and leaves a bowed hole, a mask that runs short at the top, and a family offset above specification. M1 adds a sulfur passivant to the sidewall, pulses the bias so the passivation can recover, and finishes with a smoothing overetch. M2 takes the same ideas to the 37 nm pitch of Book #31 and the boron-doped carbon that array needs.

### 1.5.2 What Each Gives and Costs

```
Route comparison (illustrative; derived in Ch. 3, 6, 10, 11, 14, 16):
                              M0            M1            M2
Array                         1b, 45 nm     1b, 45 nm     1d, 37 nm
Mask as deposited             1400 ACL      1400 ACL      1500 B-ACL
Cap                           40 nm SiON    40 nm SiON    60 nm SiON
Total plasma time             181 s         184 s         259 s
Wafer temperature             20 °C         10 °C         −25 °C
Bias                          CW, 800 eV    5 kHz, 70%,   pulsed, cyclic
                                            600 eV
Exit CD                       31.0 nm       31.0 nm       26.0 nm
Bow (maximum − top CD)        2.0 nm        0.7 nm        0.5 nm
Minimum web                   10.5 nm       12.2 nm       9.5 nm
Top loss                      62 nm         50 nm         50 nm
Mask after open               1338 nm       1350 nm       1450 nm
Hole aspect ratio at exit     44            44            56
Family offset                 1.3 nm        1.1 nm        0.9 nm
Module cost per wafer         $14.4         $15.1         $24.0
```

M0 fails the specification of Section 1.7 on four lines: bow, minimum web, family offset, and the mask height at 3σ. The extra 70 cents of M1, almost all in consumables and abatement, buys a mask the capacitor etch can use. Chapter 16 computes the yield gain at which it pays (0.05%) and shows that it is crossed easily.

---

## 1.6 Why a Carbon Open Is Hard Here

Opening 1.4 µm of carbon is routine at large dimensions. Four conditions make it hard at 31 nm:

```
1. No native passivation    Oxygen removes carbon as CO, which is volatile on every surface.
                            A fluorocarbon etch grows a polymer film that protects its sidewall.
                            An oxygen etch grows nothing. Atomic oxygen attacks the wall at about
                            0.5 nm per second (Chapter 3). To bow by less than 1 nm in 160 s, the wall
                            must be more than 99% passivated, by a film the etch must supply.
2. A 44:1 tube              Radicals reach the exit only if the wall consumes few of them. A wall
                            reaction probability of 10⁻⁴ costs 46% of the oxygen flux at the exit.
                            The etch runs 34% slower at the exit than at the top (ARDE).
3. Thin, tall webs          14 nm × 1350 nm, aspect ratio 96. A bow takes web away, a stress
                            distorts it, a wet process cannot be used to clean it.
4. A very large count       1.5 × 10¹³ holes per wafer. A defect rate of 10⁻⁹ per hole is 15,000 holes
                            on every wafer. The question is not whether the open works on average
                            but whether the tails (pinch-off, residue, merged holes) are small enough.
```

The first condition is Chapters 3, 6, and 7. The second is Chapters 3, 5, and 10. The third is Chapters 10, 12, and 14. The fourth is Chapters 4, 9, and 13, and, with its metrology, Chapter 15.

---

## 1.7 The Specification Sheet

```
Hard mask open specification (reference, illustrative):

Parameter                                  Target                   Protects against
─────────────────────────────────────────────────────────────────────────────────────────────
Exit CD, ACL bottom, all families          31.0 ± 1.0 nm (3σ)       depth lag; small top CD in the mold
Family offset (means)                      ≤ 1.2 nm                 depth lag of one family (15 nm/nm)
Top CD (just below the cap)                32.1 ± 1.0 nm            mold top CD; web at the top
Bow (maximum CD − top CD)                  ≤ 1.0 nm                 web thinning, mask bridging
Minimum web                                ≥ 11.0 nm                mask integrity, bridges
Foot angle (last 50 nm)                    ≥ 89.0°                  exit closing; Book #29 specification
Average angle over full height             ≥ 89.9°                  profile drift at depth
Ellipticity of the exit                    e ≤ 0.03                 twist in the mold hole
Local displacement (twist and wiggle)      ≤ 1.0 nm (3σ)            placement budget
Edge tilt at r = 147 mm                    ≤ 0.05° (1.2 nm)         placement budget (1.5 nm, Book #31)
ACL after open                             1350 nm mean;            mask budget of the capacitor etch
                                           ≥ 1330 nm at 3σ
Top loss                                   50 ± 12 nm (3σ)          mask budget
Top SiN support loss in the overetch       ≤ 3 nm                   top-support thickness
Residue at the exit                        none ≥ 2 nm              not-open holes
Defects from the open (missing, closed,    ≤ 3 × 10⁻⁹ per hole      not-open budget (8 × 10⁻⁹)
 merged, pinched)
Local CD uniformity (3σ)                   ≤ 2.4 nm                 depth lag tail
Edge roughness after the open (3σ)         ≤ 2.0 nm                 striation in the mold hole
Particle adders (≥ 30 nm)                  ≤ 10 per wafer           blocked holes
Throughput (4-chamber CCP platform)        ≥ 60 wafers/h            cost
```

---

## 1.8 The Reference Process

The reference array, mold, and mask are those of Book #29. What this book adds is the open in detail, one improvement of it (M1), and an extension to the 1d-class array of Book #31 (M2).

```
Reference array (Book #29):
  1b-class 6F², F = 17 nm, cell 1734 nm², 45 nm hexagonal pitch, 16 Gb die
  Mold: SiN 120 | PE-TEOS 650 | SiN 50 | BPSG 760 | SiN 20 (1.60 µm)
  Hole etch: 57:1, 5.1 min, ACL consumption 576 nm (+ 40 nm facet allowance)

Mask stack: resist / BARC 25 nm / SiON 40 nm / ACL 1400 ± 14 nm (3σ)
  Cap CD 32.0 ± 1.0 nm; family offset (litho) 1.0 nm; LCDU 2.4 nm (3σ);
  edge roughness 2.5 nm (3σ)

Tool: 300 mm dual-frequency CCP, 60 MHz source / 2 MHz bias

M0 (baseline):
  SiON open (CF₄/CHF₃/Ar) 22 s | ACL ME 139 s | OE 20 s = 181 s
  CW bias, 800 eV; O₂ 180 / COS 6 / N₂ 60 / Ar 300 sccm; 20 °C
  Bow 2.0 nm; top loss 62 nm; ACL after open 1338 nm

M1 (reference):
  SiON open 22 s | ACL ME 144 s | OE 18 s (11 s clear + 7 s smoothing) = 184 s
  5 kHz, 70% duty, 600 eV on-phase; O₂ 150 / COS 30 / N₂ 60 / Ar 300 sccm; 10 °C
  Bow 0.7 nm; top loss 50 nm; ACL after open 1350 nm

M2 (1d-class, Book #31 array):
  Cap 60 nm SiON; B-ACL 1500 nm; pitch 37 nm; exit CD 26.0 nm
  Cap open 28 s | ME 209 s | OE 22 s = 259 s; −25 °C; cyclic passivation
  Bow 0.5 nm; ACL after open 1450 nm
```

---

## Summary and Key Takeaways

1. **The mask is the first hole.** Seventeen billion holes, 31 nm wide and 44:1 deep, are cut in 1.4 µm of carbon before the mold is touched. The exit CD, the families, the tilt, and the thickness left are the capacitor etch's inputs, and most carry a gain.

2. **The mask is a honeycomb of 14 nm webs 1.35 µm tall.** Half the carbon is gone, the webs have an aspect ratio of 96, and a nanometre of bow on two neighbours takes 14% of the web.

3. **A wafer carries 2 m² of carbon wall and consumes 22 sccm of carbon.** Seven percent of the oxygen is spent on the wafer, and the wall that remains must be kept dry, clean, and free of sulfur.

4. **Oxygen has no native passivation.** To bow by less than 1 nm the wall must be more than 99% protected by a film the etch itself supplies.

5. **Book #29's 89.3° is the foot, not the wall.** The full-height angle is 89.98°. A specification on angle says little about a 44:1 wall; one on CD at three heights says more.

6. **Three routes frame the book.** M0 is the baseline, M1 passivates and smooths, and M2 carries the method to boron-doped carbon at a 37 nm pitch.

---

## Study Questions

1. A 1c-class array has F = 15 nm, a cell of 1350 nm², and a 16 Gb die. How many holes per die, and how much array area? With a 27 nm exit CD and the same 1350 nm hole depth, find the open fraction and the carbon mass removed per wafer (900 dies).

2. Recompute the wall area per wafer for a 33 nm average CD and a 1400 nm hole. What mass of water, at one monolayer (10¹⁵ molecules/cm²), could that wall hold?

3. Using Section 1.1.3, find the web width, web aspect ratio, and node diameter for the 1d array (37 nm pitch, 26 nm exit CD, 1450 nm mask). By what fraction does a 0.5 nm bow on each of two neighbours thin the web?

4. The capacitor etch has ∂h/∂CD = 15 nm per nm. A family offset of 1.3 nm (M0) and one of 1.1 nm (M1): how much depth lag does each leave, and by how many nanometres of overetch must the capacitor etch compensate the difference?

5. A product has an array efficiency 10% higher than the reference at the same die size. Estimate the change in oxygen consumed by the wafer in sccm O₂-equivalent, and say which way the bow will move if the recipe is unchanged and why (Section 1.6).

6. Book #29 quotes a sidewall angle of 89.3°. Show that this cannot be the full-height angle of a 1350 nm wall at a 45 nm pitch, and find the angle that corresponds to a 1.1 nm change in CD from top to exit.

---

**Next Chapter:** [Chapter 2: The Mask Stack — Carbon Films, Cap, Resist & the Incoming Surface](./02-mask-stack-carbon-films.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
