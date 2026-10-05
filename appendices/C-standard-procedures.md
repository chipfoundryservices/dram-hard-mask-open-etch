# Appendix C: Standard Procedures

Step-by-step procedures for qualifying and monitoring the hard mask open module (route M1). Each procedure lists purpose, materials, steps, and acceptance criteria. Values are illustrative.

---

## C.1 M1 Chamber Qualification

**Purpose:** Qualify a hard mask open chamber after installation, wet clean, or a change of the upper electrode or edge ring.

**Materials:** 30 seasoning wafers (blanket ACL 1400 nm + SiON 40 nm, no pattern); monitor wafers: blanket SiON (40 nm on oxide), blanket ACL (1400 nm), blanket SiN (120 nm); 3 full-structure wafers (stack of Chapter 1 with the scribe test structures of Chapter 15); 1 unpatterned particle wafer; 1 thermocouple wafer.

**Steps:**
1. Bake the chamber at wall temperature (60 °C) for 4 h after pump-down. Verify the ESC zones at −14 °C setpoint and the wafer temperature of 10 ± 1 K under the M1 main-etch plasma (thermocouple wafer), and 10 ± 1 K in ST3b with the ESC stepped to −3 °C.
2. Run the waferless clean, the NF₃ clean, and the season step (COS-rich, 12 s, cover wafer). Then 6 seasoning wafers through the full recipe until the CO/Ar plateau and the SiON rate on two consecutive wafers are within 2% of the fleet reference.
3. Measure blanket rates at 49 sites in the ST2 chemistry (30 s): ACL (ER₀), SiON (v_cap), SiN.
4. Run the particle wafer through the full recipe.
5. Run 3 structure wafers. Record OES (CO/Ar, O/Ar, SO/Ar), V_dc, delivered power, wafer temperature, EP time, step times.
6. On the structure wafers: CD-SEM (cap CD, 9 sites), HV-SEM (exit CD and ellipticity by family, 9 sites), CD-SAXS (top CD, bow, depth, exit CD; 5 sites), IR scatterometry and XTEM on the ridge test structure (top loss), XTEM at centre and edge (profile, foot, residue), the edge-tilt structure, and the large-area endpoint structure.
7. Compare with the fleet reference.

**Acceptance:**
```
ACL rate ER₀ 730 ± 22 nm/min (±3%); within-wafer uniformity ≤ 2.5% (3σ)
SiON v_cap 0.237 nm/s (ACL:SiON 51; matching limit ≥ 48, daily band ± 1.5); SiN rate 8 ± 1 nm/min
Wafer temperature 10 ± 1 K across the wafer, in ST2 and ST3b
CO/Ar plateau ratio after/before clearing 0.60 ± 0.05; EP time within ± 1.5 s of the fleet median
Exit CD 31.0 ± 0.4 nm (site mean, fleet); family offset ≤ 1.2 nm; LCDU ≤ 2.4 nm (3σ)
Bow 0.67 ± 0.15 nm; top CD 32.1 ± 0.3 nm; minimum web ≥ 11.0 nm
Foot angle 89.3 ± 0.3°; no residue ≥ 2 nm at the exit; sulfur at the exit ≤ 10¹⁴ cm⁻²
Top loss (ridge structure) 50 ± 8 nm; top SiN loss ≤ 3 nm
Edge shift at r = 147 mm ≤ 1.2 nm; fleet spread ≤ 0.4 nm
Particle adders ≥ 30 nm ≤ 10 per wafer; adders ≥ 80 nm ≤ 0.5 per wafer
```

---

## C.2 Daily Monitor

**Purpose:** Detect drift in the carbon rate, the cap erosion, the nitride rate, and the plasma.

**Steps:**
1. Run one blanket ACL, one blanket SiON, and one blanket SiN monitor in the ST2 chemistry for 30 s.
2. Measure 49 sites by ellipsometry. Log OES CO/Ar, SO/Ar, and O/Ar.
3. Run the unpatterned particle wafer through the full recipe (weekly: after every PM).

**Acceptance:**
```
ACL rate within ± 3% of the chamber baseline; uniformity ≤ 2.5% (3σ)
SiON v_cap within ± 0.8% of the baseline  (a 1% shift is 1.5 s of the cap's clock and 9 nm of top loss)
SiN rate 8 ± 1 nm/min;  ACL:SiON 51 ± 1.5
SO/Ar within ± 5% of the baseline (COS flow and the sulfur state of the wall)
```

---

## C.3 Weekly Fleet-Matching Test

**Purpose:** Hold the fleet matched on the quantities that the capacitor etch inherits.

**Steps:**
1. Run one wafer with the dense-array, ridge, and edge-tilt test structures in every chamber of the fleet.
2. Measure exit CD (HV-SEM), bow and profile (CD-SAXS), top loss (IR scatterometry), and the edge shift.
3. Compare each chamber with the fleet mean.

**Acceptance:**
```
Exit CD within ± 0.4 nm of the fleet mean;  bow within ± 0.15 nm
Top loss (ridge) within ± 8 nm;  edge shift ≤ 1.2 nm and the fleet spread ≤ 0.4 nm
```

---

## C.4 First-Wafer and Season Test

**Purpose:** Verify that the season step controls the first-wafer bow after an NF₃ clean (Chapter 5).

**Steps:**
1. After an NF₃ clean and the season, run 8 structure wafers in sequence (n = 0 to 7).
2. Measure the bow of wafers 0, 1, 2, 5, and 7 by CD-SAXS.

**Acceptance:**
```
Bow of wafer 0 ≤ 0.85 nm;  wafer 1 ≤ 0.80 nm;  all wafers ≤ 1.0 nm;  wafer 7 within 0.05 nm of 0.67 nm
Without the season (diagnostic only): wafer 0 about 1.34 nm, wafer 1 about 1.12 nm
```

---

## C.5 Cross-Section Protocol

**Purpose:** Calibrate CD-SAXS and HV-SEM against the true profile.

**Steps:**
1. Cleave or FIB at three sites (centre, middle, edge) through a row of holes, on each of the two structure wafers.
2. Image by XTEM/STEM at 3 depths per hole and extract CD(z) at 10 heights: top, bow depth (370 nm), 750, 1000, 1250, 1300, 1350 nm, and the foot (last 50 nm).
3. Fit the profile model of Chapter 3: bow, foot, top CD, exit CD, minimum web; and the local angle of the foot.
4. Measure the sulfur and oxygen profile along the wall by EELS (10 holes).

**Acceptance:**
```
Repeatability: CD ± 0.3 nm (3σ), bow ± 0.15 nm, foot angle ± 0.3°
CD-SAXS agrees with the cross-sections to ± 0.2 nm in bow and exit CD
```

---

## C.6 CD-SAXS and HV-SEM Recipes

```
CD-SAXS:   transmission small-angle X-ray scattering of the dense array block (10 × 10 µm);
           angular range ± 60° in 1° steps; model: stack of 30 elliptical slices for the profile;
           outputs: CD(z) at 30 depths, top CD, bow, depth, family offset (second harmonic of the pattern)
HV-SEM:    landing energy 30–50 keV, secondary + backscatter; field 2 × 2 µm;
           outputs: exit CD (through-hole contrast), ellipticity, hole centroid (placement), closed-hole count
           (dark holes); 9 sites per wafer, 3 per family
```

---

## C.7 Particle and Killer-Particle Test

**Purpose:** Verify the particle budget (Chapter 9).

**Steps:**
1. Scan an unpatterned wafer before and after the full recipe at 30 nm sensitivity.
2. Count adders ≥ 30 nm and ≥ 80 nm.
3. Repeat at wafers 1, 10, and 25 after the NF₃ clean.

**Acceptance:**
```
Adders ≥ 30 nm ≤ 10 per wafer; ≥ 80 nm ≤ 0.5 per wafer
At wafer 25 after the clean (SiOₓ on the walls 46 nm): ≤ 3 adders ≥ 30 nm per wafer
```

---

## C.8 Edge-Tilt Test

**Purpose:** Measure the shift of the exit at the wafer edge (Chapters 4, 5).

**Steps:**
1. On the edge-tilt test structure, measure by HV-SEM the displacement of the exit centroid relative to the top, at r = 147 mm, in 8 azimuths.
2. Fit the radial component.

**Acceptance:**
```
Radial shift ≤ 1.2 nm (0.05°); fleet spread ≤ 0.4 nm; replace the ring at 25 µm of wear (tilt 0.05°)
```

---

## C.9 Endpoint Calibration

**Purpose:** Calibrate the clearing signal and the trigger (Chapter 8).

**Steps:**
1. On the large open-area structure, run the main etch, logging CO 483.5 nm and Ar 750.4 nm at 10 Hz.
2. Stop the etch at the trigger and at the trigger + 5.5 s on two wafers; cross-section the array to find the fraction of cleared holes.
3. Compute the drop at clearing, the transition width, and the trigger delay.

**Acceptance:**
```
Drop at clearing 40 ± 4% (post/pre = 0.60 ± 0.05); transition (±3σ) 11 ± 2 s
At the trigger 50 ± 10% of the holes are cleared; at trigger + 5.5 s ≥ 99.5%
Trigger jitter ≤ 0.1 s
```

---

## C.10 Moisture and Degas Test

**Purpose:** Verify the post-open hold (Chapter 9).

**Steps:**
1. Hold two post-open wafers 4 h in air and 12 h in a nitrogen-purged FOUP.
2. Measure the water by thermal desorption (or load-lock pressure rise) before and after the degas (150 °C, 30 s).

**Acceptance:**
```
After 4 h in air ≤ 0.25 mg; after the degas ≤ 0.03 mg; after 12 h in the FOUP ≤ 0.25 mg
Sulfur at the exit (XPS on a cleaved wall) ≤ 10¹⁴ cm⁻² after the degas
```

---

## C.11 Ridge Test Structure and Cap Witness

**Purpose:** Measure the top loss and the cap erosion, which the endpoint cannot see (Chapters 11, 15).

**Steps:**
1. Ellipsometry of the blanket SiON witness before and after the full recipe (49 sites): v_cap and ACL:SiON.
2. IR scatterometry (1.55 µm) of the 14 nm line–space ridge structure before and after: the loss of height, 5 sites; confirm by XTEM on one site.

**Acceptance:**
```
v_cap 0.237 ± 0.002 nm/s;  ACL:SiON 51 ± 1.5
Ridge top loss 50 ± 8 nm (M1), 14 ± 6 nm (M1-c);  IR scatterometry within ± 3 nm of XTEM
```

---

**Appendix C Version:** 1.0  
**Last Updated:** 2026-10-05
