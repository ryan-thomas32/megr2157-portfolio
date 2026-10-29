# A8 – Gearbox Design

## Objective:

- Design a gearbox that can be assembled and disassembled.
- Analyze and size input and output shafts for strength.
- Design journal bearings to support shafts.
- Create a gearbox housing with proper clearance and fastening.
- Use parametric CAD modeling to generate a final design.
- Document calculations, sketches, and lessons learned.

For Assignment A8, I designed a single-reduction spur gearbox around the McMaster-Carr pinion and gear. TODO: one or two sentences in your own words on what you did. I checked the shafts with hand calculations, sized and selected the journal bearings, sketched a two-piece housing, and built the parts in SolidWorks using global variables.

### Design Requirements (from the assignment)

- **Gear ratio:** 24:9
- **Output gear:** 1.25 in-lbf at 1100 rpm
- **Input (pinion) shaft:** 0.125 in diameter, 1 in long
- **Output (gear) shaft:** 0.25 in diameter, 1 in long
- **Gears:** McMaster-Carr spur gears (pinion 7880K19), press fit on the shafts
- **Shaft bearing fit:** running sliding fit
- **Housing:** two pieces, assembled and disassembled with fasteners

## Analyze: Shafts and Journal Bearings:

### Step 1: Shaft Calculations and Design Alterations:

- Both shafts are checked in pure torsion, using AISI 1020 steel (Sy = 50,800 psi). Material data source: TODO (paste link, for example MatWeb).
- The safety factor is the yield strength divided by the shear stress: SF = Sy / τ.
- The input shaft carries T = 0.469 in-lbf and the output shaft carries T = 1.25 in-lbf.

#### Input Shaft (Power Transmission):

**Knowns:** gear ratio 24:9, n_out = 1100 rpm, T_out = 1.25 in-lbf, d = 0.125 in, L = 1 in, AISI 1020 steel with Sy = 50,800 psi

**Unknowns:** T_in, J, τ, SF

<!-- IMAGE: input shaft hand calculations (knowns, unknowns, FBD, symbolic and numerical solution) -->

**Symbolic solution:** T_in = T_out / G, J = π d⁴ / 32, τ = T_in c / J, SF = Sy / τ

**Numerical solution:**

- T_in = 1.25 (9/24) = 0.469 in-lbf
- J = (π/32)(0.125)⁴ = π/131,072 in⁴
- c = 0.125 / 2 = 0.0625 in
- τ = (0.469)(0.0625) / (π/131,072) = 1,222.96 ≈ **1,223 psi**
- SF = 50,800 / 1,222.96 = **41.54**

**Result:** The safety factor is 41.54, so the 0.125 in diameter is sufficient.

#### Output Shaft (Short Shaft):

**Knowns:** gear ratio 24:9, n_out = 1100 rpm, T_out = 1.25 in-lbf, d = 0.25 in, L = 1 in, AISI 1020 steel with Sy = 50,800 psi

**Unknowns:** J, τ, SF

<!-- IMAGE: output shaft hand calculations (knowns, unknowns, FBD, symbolic and numerical solution) -->

**Symbolic solution:** J = π d⁴ / 32, τ = T_out c / J, SF = Sy / τ

**Numerical solution:**

- J = (π/32)(0.25)⁴ = π/8,192 in⁴
- c = 0.25 / 2 = 0.125 in
- τ = (1.25)(0.125) / (π/8,192) = **407.44 psi**
- SF = 50,800 / 407.44 = **124.68**

**Result:** The safety factor is 124.68, so the 0.25 in diameter is sufficient.

| Shaft  | d (in) | T (in-lbf) | Stress (psi) | Safety Factor (Sy / τ) | Sufficient? |
|--------|--------|------------|--------------|------------------------|-------------|
| Input  | 0.125  | 0.469      | 1,223        | 41.54                  | Yes         |
| Output | 0.250  | 1.250      | 407.44       | 124.68                 | Yes         |

### Step 2: Design Journal Bearings:

#### Journal Bearing Sizing:

- I used two bearings per shaft, with the gear at the middle, so each bearing carries half of the gear force.
- I chose the bearing length equal to the shaft diameter (L/D = 1), so L = 0.125 in for the input bearing and L = 0.25 in for the output bearing.
- The gear pitch diameter is D_g = 1.25 in. TODO: confirm against the McMaster gear listing.

**Knowns:** T_out = 1.25 in-lbf, n_out = 1100 rpm, G = 24/9, d_in = 0.125 in, d_out = 0.25 in, D_g = 1.25 in

**Unknowns:** n_in, W_t, R, L, P, V, PV

<!-- IMAGE: journal bearing FBD (shaft with W_t at the gear and R at each bearing) -->

<!-- IMAGE: journal bearing hand calculations (knowns, unknowns, symbolic and numerical solution) -->

**Symbolic solution:**

- n_in = n_out G
- ΣF = 0: R_A + R_B = W_t, and by symmetry R_A = R_B = R
- W_t = T_out / (D_g/2) = 2 T_out / D_g
- R = W_t / 2 = T_out / D_g
- L = d (L/D = 1)
- P = R / (d L) = T_out / (D_g d L)
- V = π d n / 12 (ft/min)
- PV = P × V

**Numerical solution:**

- n_in = 1100 (24/9) = 2,933 rpm
- Input bearing: P = 1.25 / ((1.25)(0.125)(0.125)) = **64 psi**, V = π(0.125)(24/9)(1100)/12 = 275π/9 ≈ **95.99 ft/min**, PV = 64 × 95.99 = **6,143.6 psi·ft/min**
- Output bearing: P = 1.25 / ((1.25)(0.25)(0.25)) = **16 psi**, V = π(0.25)(1100)/12 = 275π/12 ≈ **72 ft/min**, PV = 16 × 71.99 = **1,151.92 psi·ft/min**

| | d (in) | L (in) | P (psi) | V (ft/min) | PV (psi·ft/min) |
|---|---|---|---|---|---|
| Input bearing  | 0.125 | 0.125 | 64 | 95.99 | 6,143.6 |
| Output bearing | 0.250 | 0.250 | 16 | 72 | 1,151.92 |

#### Bearing Material:

I picked **porous bronze with graphite lubricant**. The graphite resists wear better than oil. The bearings pass the limits for both lecture table rows:

| Lecture table row | Load (psi) | Speed (ft/min) | PV limit | Input bearing (P / V / PV) | Output bearing (P / V / PV) |
|---|---|---|---|---|---|
| Porous bronze | 4,500 | 1,500 | 50,000 | 64 / 96 / 6,144 | 16 / 72 / 1,152 |
| Graphite (lubricated) | 600 | 2,500 | 150,000 | 64 / 96 / 6,144 | 16 / 72 / 1,152 |

Both bearings are under every limit. The PV margin on porous bronze is 50,000 / 6,144 ≈ 8.1 for the input bearing and 50,000 / 1,152 ≈ 43.4 for the output bearing.

<!-- IMAGE: lecture bearing material table with the circled columns -->

#### Journal Bearing Thickness:

<!-- IMAGE: bearing thickness knowns and unknowns -->

<!-- IMAGE: bearing thickness FBD -->

<!-- IMAGE: bearing thickness equations and calculations -->

**Result:** the minimum thickness is 0.0009 in (input) and 0.0004 in (output). Strength doesn't set the wall, so the press fit and machining do. The selected bearings have walls of 1/16 in (input) and 1/32 in (output), which are more than enough. TODO: update with your hand-calculated values.

#### McMaster-Carr Bearings:

| | Part Number | ID | OD | Length | Qty |
|---|---|---|---|---|---|
| Input bearing  | 9368T95 | 1/8"  | 1/4"  | 1/8" | 2 |
| Output bearing | 9368T11 | 1/4"  | 5/16" | 1/4" | 2 |

Both are 841 Bearing Bronze sleeve bearings (TODO: copy the exact product name. If you add graphite lubricant, check that the part number matches the graphite version).

<!-- IMAGE: McMaster bearing table with the selected rows -->

### Step 3: Gearbox Sketch:

The housing is two pieces, a box and a cover, held together with M2 × 0.4 bolts into tapped holes in the box wall. Each half has bearing bores, 1/4" for the input bearing and 5/16" for the output bearing, so each shaft is supported at both ends.

<!-- IMAGE: housing sketch -->

<!-- IMAGE: sketch of how the two halves fit together -->

### Step 4: Gearbox 3D Model:

- I built the model parametrically as much as possible, starting from the known gear and bearing dimensions.
- Gears were downloaded from McMaster-Carr. The shafts, housing, bearings, and screws were modeled from my own sketches.

#### Fit Selection:

- **Gear to shaft (press fit):** ANSI/ASME B4.1 Class FN 1, since the shafts are press fit through the gear hubs. Hole H6, shaft per the FN 1 column.
- **Shaft to bearing (running sliding fit):** ANSI/ASME B4.1 Class RC 4, as the assignment requires. Hole H8, shaft f7.
- The 0.125 in shaft uses the 0.12–0.24 in row, and the 0.25 in shaft uses the 0.24–0.40 in row.

<!-- IMAGE: FN 1 table with the circled rows (both images) -->

<!-- IMAGE: RC 4 table with the circled rows (both images) -->

| | Input (0.125 in) | Output (0.25 in) |
|---|---|---|
| Gear bore, H6 | 0.1250 – 0.1253 | 0.2500 – 0.2504 |
| Shaft at gear seat | 0.1254 – 0.1256 | 0.2505 – 0.25075 |
| Interference | 0.0001 – 0.0006 | 0.0001 – 0.00075 |
| Bearing bore, H8 | 0.1250 – 0.1257 | 0.2500 – 0.2509 |
| Shaft at bearing, f7 | 0.1241 – 0.1246 | 0.2489 – 0.2495 |
| Clearance | 0.0004 – 0.0016 | 0.0005 – 0.0020 |

Each shaft is dimensioned with a larger diameter at the gear seat and a smaller diameter in the bearing.

#### Box:

The box is the back half of the gearbox, and it holds the gears. It is made of cast alloy steel. I chose it for its high load capacity, based on what automotive gearbox housings use. The gearbox loads are very small (tangential force about 2 lbf, bearing pressures 16 to 64 psi), so the steel is much stronger than it needs to be.

<img width="945" height="731" alt="image" src="https://github.com/user-attachments/assets/02fb7aa4-614f-4069-8194-9cbced409cd3" />

#### Cover:

The cover is the front half of the gearbox. It has holes for the bolts that fasten it to the box, and two bores for the bearings. It is made of cast alloy steel for the same reasons as above.

<img width="1072" height="732" alt="image" src="https://github.com/user-attachments/assets/b6a7e955-7aa5-4a19-a697-3dbbcc1b310d" />

#### Shafts, Gears, and Bearings:

Input bearing, 9368T95
<img width="1037" height="610" alt="image" src="https://github.com/user-attachments/assets/5ceb9368-b22c-4a0d-bb96-e1c2446a696b" />

Output bearing, 9368T11
<img width="1018" height="700" alt="image" src="https://github.com/user-attachments/assets/211e5693-14bd-4c14-9259-646041e43851" />

Input Shaft
<img width="1202" height="533" alt="image" src="https://github.com/user-attachments/assets/5c04c80f-73dc-4bd2-94e6-ba7111bfc26c" />

Output Shaft
<img width="1075" height="722" alt="image" src="https://github.com/user-attachments/assets/8c446245-669f-4e45-bd0a-7fbb31164d52" />

M2 x 10mm Bolt
<img width="766" height="742" alt="image" src="https://github.com/user-attachments/assets/01ae05c6-acb8-44e9-a57f-4b0d839f3f07" />

#### Assembly:

The gearbox goes together in this order: press the bearings into the box and cover, press the gears onto the shafts, slide the shafts into the back bearings and mesh the gears, fit the cover, and bolt it down.

<img width="1277" height="572" alt="image" src="https://github.com/user-attachments/assets/456071cc-4d83-48ab-9a7d-60117b732c15" />

<img width="1043" height="717" alt="image" src="https://github.com/user-attachments/assets/c5233a53-f36c-429d-a037-f6abf683ca7f" />

<!-- IMAGE: section view, caption: [Section view showing the gear mesh and bearings] -->

### MEGR 2157 Addition:

- Six multi-view CAD drawings and one assembly drawing with complete dimensioning and proper tolerancing, in third-angle projection (ASME Y14.5).
- Tolerance block: X.X ± .02, X.XX ± .01, and X.XXX ± .005.
- Two different tolerance callouts on critical features: the gear seat on each shaft (FN 1 press fit) and the bearing journal on each shaft (RC 4 running fit).

<img width="953" height="697" alt="Screenshot 2026-10-29 061412" src="https://github.com/user-attachments/assets/3e1c0497-ac94-4a97-ba32-6647c1274ceb" />

<img width="837" height="651" alt="image" src="https://github.com/user-attachments/assets/ee6f34bc-1abe-49da-aa3f-4a7b9cc3f099" />

<img width="837" height="646" alt="image" src="https://github.com/user-attachments/assets/b04172ee-40ba-412b-8211-a40363de5362" />

<img width="935" height="696" alt="image" src="https://github.com/user-attachments/assets/5af84832-0300-4757-b874-11d620ca850b" />

<img width="977" height="752" alt="image" src="https://github.com/user-attachments/assets/24efa880-27cc-42a2-9d29-ad62f94de09d" />

<img width="988" height="762" alt="image" src="https://github.com/user-attachments/assets/9505e38d-2fe6-4c71-afae-082775ec9208" />

<img width="1021" height="660" alt="Screenshot 2026-10-29 061001" src="https://github.com/user-attachments/assets/d4a7acb9-c9ef-40e7-885c-f99c8d2e8785" />
## Decide

- **Housing material:** cast alloy steel. I based the choice on what automotive gearbox housings use for high load capacity. The gearbox loads are very small, so the steel is much stronger than it needs to be. The trade-off is extra weight and machining effort compared with aluminum, which would also work.
- **Shaft material:** AISI 1020 steel, because the stresses are far below its strength (safety factors of 41.54 and 124.68) and it is easy to machine.
- **Bearing material:** porous bronze with graphite lubricant, because it passes the load, speed, and PV limits with a wide margin and the graphite resists wear better than oil.
- **Bearing length:** equal to the shaft diameter (L/D = 1), which keeps the pressure low and matches stocked McMaster sizes.
- **Fastening:** M2 bolts into tapped holes, so the box can be taken apart.
- **Fits:** FN 1 for the gear on the shaft and RC 4 for the shaft in the bearing, as the assignment requires a running sliding fit at the bearings.

## Communicate

**Mistakes**

- TODO: a real mistake you made, what caused it, and how you fixed it.

**Lessons learned**

- Torque and speed trade off through the gear ratio. The faster input shaft carries less torque.
- The shaft stresses are very low, so the given diameters, not strength, set the shaft design.
- The tangential force at the mesh is what loads the bearings, so the gear pitch diameter drives the bearing numbers.
- The bearing wall thickness is set by manufacturing and the press fit, not by stress.
- TODO: more lessons (no lesson too small).

## CAD Files:

[Download CAD files](PASTE-DOWNLOAD-LINK-HERE)

Includes the box, cover, shafts, gears, bearings, assembly, and drawings.

## Time Spent:


