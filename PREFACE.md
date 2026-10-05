# Preface: Cutting the Mask That Cuts the Capacitor

## Why This Book Exists

Most etches are judged by what they leave in the film. The hard mask open is judged by what it hands to the next etch. A 1.4 µm film of amorphous carbon is deposited on the mold of a DRAM capacitor, capped with 40 nm of silicon oxynitride, and patterned by lithography into seventeen billion openings. Then the pattern has to be moved down through the carbon, and what comes out at the bottom is the aperture through which the five-minute mold etch will cut. Its width is the capacitor's top CD. Its walls are the mask the oxide etch stands behind. Its failures are bits that do not work. After the mask open nothing corrects it.

The previous books of this series treated the mask open as an input. *DRAM Capacitor Hole Etch* stated what the open must deliver, a 31.0 nm exit, a straight wall, a mask 1350 nm tall, and left the how to companion volumes. That was the right division for a book about the oxide etch. This book is written from the other side. The questions change. How can a plasma cut carbon, whose only reagent is oxygen, and spare the wall of a 31 nm hole that oxygen attacks at half a nanometre a second? How can a cap 40 nm thick protect 1.4 µm of carbon, and why does one nanometre of it decide 21 nm of the mask? What happens to a wall of carbon 14 nm thick and 1350 nm tall when half of its neighbours are removed? How would anyone know, from above, that it is standing?

Six facts make the hard mask open a subject of its own:

1. **The holes are deep and the walls are thin.** 44:1 tubes, 31 nm wide, separated by webs of 14 nm and 96:1. A bow of one nanometre on each of two neighbouring holes takes 14% of the web away.

2. **Oxygen has no native passivation.** A fluorocarbon plasma lays a polymer on the wall as it cuts. An oxygen plasma that cuts carbon lays down nothing, and what it makes (carbon monoxide) leaves every surface it forms on. Whatever protects the wall must be supplied on purpose, and must not itself block the hole.

3. **The cap is a clock, not a mask.** On a ridge 14 nm wide the cap fails at the shoulders first, and the carbon beneath is eaten at 12 nm a second from the moment it is exposed. The top loss is quadratic in the time since the cap failed, and the cheapest lever in the module is a cap two nanometres thicker.

4. **The wafer is a large wall.** 2.03 m² of carbon face per wafer, 1.4 × 10²¹ carbon atoms removed, 22 sccm of carbon monoxide in a flow whose other sources are as large. The endpoint sees the median of a population, and the mask height is something it cannot see at all.

5. **The specification is a count.** Three failures in every billion holes is 52 per die. Repair absorbs the isolated ones. What costs yield is the tail: a hole whose exit narrows below 12 nm, an inorganic plug left from the cap open, a particle of 81 nm.

6. **A mask cannot be made well and cheaply in isolation.** An undoped 1.8 µm carbon is the cheapest to open and the most expensive to etch through. The open's modules, cap, carbon, and chemistry, trade among themselves and with the etch that follows.

This book treats the hard mask open as **the perforation of a 1.4 µm carbon film by oxygen chemistry, with a statistical specification, a sacrificial cap that behaves like a clock, and walls that carry the mold etch**, and not as a short preparatory step before the capacitor etch.

---

## Unique Aspects of DRAM Hard Mask Open Etch

### 1. The Wall Is Protected by What the Etch Makes

Sulfur from carbonyl sulfide forms a thin film on the carbon, and silicon oxide arrives from the cap. Each reaches a different depth, ℓ = d/√(2s), and between them they hold the wall at better than 99% coverage over 1350 nm. The bow is not a profile error to be tuned out; it is a measurement of coverage. The cold chuck and the sulfur account for most of the improvement from the baseline process to the reference.

### 2. The Cap Is Paid for in Seconds

The mask height after the open is set by how many seconds the carbon is exposed after the cap fails, not by how long the etch ran. COS flow, ion energy, wafer temperature, and the film's hydrogen all move that clock. Control reduces to a feed-forward on the COS flow, a knob that moves the cap's clock without moving the carbon's, and a policy of what not to feed forward.

### 3. The Mask Is a Perforated Plate

At 43.5% open the carbon has a quarter of the stiffness of the solid film. It relaxes at every array edge over fifteen rows, it can bend as a bimorph when its faces are asymmetric, and its thinnest webs are the ones the capacitor etch needs most. The mechanics are small numbers (a nanometre of wiggle, a tenth of a degree of lean) and the budget for them is 1.5 nm of placement.

### 4. The Open Cannot Be Seen From Above

Visible light penetrates 126 nm into the carbon. The profile is measured by X-ray scattering, the exit by high-voltage electrons, and the top loss by a test structure whose 14 nm ridges fail as the web does. The endpoint is a population event, 11 s wide, that the CO emission reports with a median.

### 5. The Open Cannot Be Reworked More Than Once

A wafer whose open is out of specification can be stripped and patterned again, once. The mask film's stress history, the cap's thickness, and the wafer's bow accumulate. The first open has to be right, and the module that does it costs $15 a wafer under a wafer worth about a hundred times more.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–3 for the mask, the cap, and the passivation model, Chapter 6 for the levers and the window, Chapter 7 for finishing tools, and Chapters 10, 11, and 13 for the profile, the top loss, and the defects. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5, 6, 8, and 9 for the chamber, the levers, the endpoint, and the walls. Chapter 15 covers the metrology that judges your tool, and Chapter 16 the equipment counts. Appendix C holds the qualification procedures.

### For Integration Engineers
Read Chapters 1–2 for the stack and the budget, Chapters 4 and 10 for the transfer and the CD budget, Chapter 14 for the 1d, 4F², and 3D routes, and Chapter 16 for the cost model and the handoff sheet.

### For Device Engineers
Read Chapter 1, Chapter 4 for the hole count, Chapter 10 for what the exit and web do to the capacitor, Chapter 12 for the webs, and Chapter 16 for yield signatures and repair.

### For Researchers
Read Chapters 3, 4, 7, 11, 12, and 13. The passivation-film model of Chapter 3, the top-loss law of Chapter 11, the bimorph model of Chapter 12, and the pinch-off tail model of Chapter 13 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array and mold of Book #29: a 1b-class 6F² cell on a 45 nm hexagonal pitch, a 16 Gb die with 900 dies on a 300 mm wafer, and a 1.60 µm mold. The mask is ArF-immersion resist over 25 nm of BARC, a 40 nm SiON cap, and 1400 nm of ACL, with an exit CD of 31.0 nm and 1350 nm of carbon remaining after the open. Three open processes follow. **M0**, the baseline, runs a continuous 800 eV bias at 20 °C with 6 sccm of COS in 181 s; it bows 2.0 nm, leaves a 10.5 nm web, loses 62 nm from the top, and fails four lines of the specification, deliberately. **M1**, the reference, pulses the bias at 5 kHz and 70%, adds 30 sccm of COS and a cold chuck, and ends with a smoothing overetch; it takes 184 s, bows 0.67 nm, leaves a 12.2 nm web, and loses 50 nm. **M2** carries the method to a boron-doped mask at the 37 nm pitch of the 1d array, at −25 °C with a cyclic scheme, in 259 s. A thicker cap (M1-c) and the 4F² square lattice (M3) appear as variants. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work on carbon and photoresist plasma etching, passivation by sulfur and silicon oxide, the transport of neutrals and ions in high-aspect-ratio features, the mechanics of perforated and stressed films, optical-emission endpoint, and the shared experience of the engineers who have kept the first etch of the capacitor straight, open, and standing through every node.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
