# A8 – Gearbox Design

## Objective:

- Design a gearbox that can be assembled and disassembled.
- Analyze and size input and output shafts for strength.
- Design journal bearings to support shafts.
- Create a gearbox housing with proper clearance and fastening.
- Use parametric CAD modeling to generate a final design.
- Document calculations, sketches, and lessons learned.

For Assignment A8, I designed a single-reduction spur gearbox around the McMaster-Carr pinion and gear. I checked the shafts with hand calculations, sized and selected the journal bearings, sketched a two-piece housing, and built the parts in SolidWorks using global variables.

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

Both shafts are checked in pure torsion, using AISI 1020 steel (Sy = 50,800 psi). Safety factor is SF = Sy / τ.

#### Input Shaft (Power Transmission):

<img width="1960" height="2524" alt="CamScanner 10-29-26 07 28n_3" src="https://github.com/user-attachments/assets/cc3b0ba1-f23b-4f3d-9db7-364ef1092c98" />

#### Output Shaft (Short Shaft):

<img width="1836" height="2424" alt="CamScanner 10-29-26 07 28n_2" src="https://github.com/user-attachments/assets/1dac8bd4-0907-48b1-8ea4-f2bade18be3e" />

#### Shaft Results:

| Shaft  | d (in) | L (in) | T (in-lbf) | J (in⁴) | τ (psi) | SF (Sy / τ) | Sufficient? |
|--------|--------|--------|------------|---------|---------|-------------|-------------|
| Input  | 0.125  | 1      | 0.469      | 2.397 × 10⁻⁵ | 1,223  | 41.54       | Yes         |
| Output | 0.250  | 1      | 1.250      | 3.835 × 10⁻⁴ | 407.44 | 124.68      | Yes         |

### Step 2: Design Journal Bearings:

#### Journal Bearing Sizing:

<img width="1616" height="2060" alt="CamScanner 10-29-26 07 28n_1" src="https://github.com/user-attachments/assets/b34e55df-8e69-4307-b581-45b2a5936781" />

Two bearings per shaft, with the gear at the middle, so each bearing carries half of the gear force. Bearing length equals shaft diameter (L/D = 1). The gear pitch diameter is D_g = 1.25 in.

| | n (rpm) | d (in) | L (in) | W_t (lbf) | R (lbf) | P (psi) | V (ft/min) | PV (psi·ft/min) |
|---|---|---|---|---|---|---|---|---|
| Input bearing  | 2,933 | 0.125 | 0.125 | 2.0 | 1.0 | 64 | 95.99 | 6,143.6 |
| Output bearing | 1,100 | 0.250 | 0.250 | 2.0 | 1.0 | 16 | 72 | 1,151.92 |

#### Bearing Material:

Porous bronze with graphite lubricant, because the graphite resists wear better than oil so better for a long term application.

| Lecture table row | Load (psi) | Speed (ft/min) | PV limit | Input bearing passes? | Output bearing passes? |
|---|---|---|---|---|---|
| Porous bronze | 4,500 | 1,500 | 50,000 | Yes (64 / 96 / 6,144) | Yes (16 / 72 / 1,152) |
| Graphite (lubricated) | 600 | 2,500 | 150,000 | Yes (64 / 96 / 6,144) | Yes (16 / 72 / 1,152) |

#### Journal Bearing Thickness:

<img width="2212" height="3264" alt="CamScanner 10-29-26 07 42n" src="https://github.com/user-attachments/assets/82c277e5-fd2f-4881-b8bc-103aa1b9ea67" />

| | Minimum thickness (in) | Selected bearing wall (in) | Sufficient? |
|---|---|---|---|
| Input bearing  | 0.0009 | 0.0625 (1/16") | Yes |
| Output bearing | 0.0004 | 0.03125 (1/32") | Yes |

Strength doesn't set the wall, so the press fit and machining do.

#### McMaster-Carr Bearings:

| | Part Number | ID | OD | Length | Qty |
|---|---|---|---|---|---|
| Input bearing  | 9368T95 | 1/8"  | 1/4"  | 1/8" | 2 |
| Output bearing | 9368T11 | 1/4"  | 5/16" | 1/4" | 2 |

Both are 841 bearing bronze sleeve bearings from McMaster-Carr.

### Step 3: Gearbox Sketch:

The housing is two pieces, a box and a cover, held together with M2 × 0.4 bolts into tapped holes in the box wall. Each half has bearing bores, 1/4" for the input bearing and 5/16" for the output bearing, so each shaft is supported at both ends.

<img width="2284" height="3264" alt="CamScanner 10-29-26 07 53n" src="https://github.com/user-attachments/assets/661662f6-282a-4baf-863e-ff0404552f3a" />

### Step 4: Gearbox 3D Model:

- I built the model parametrically as much as possible, starting from the known gear and bearing dimensions.
- Gears were downloaded from McMaster-Carr. The shafts, housing, bearings, and screws were modeled from my own sketches.

#### Fit Selection:

- **Gear to shaft (press fit):** ANSI/ASME B4.1 Class FN 1, since the shafts are press fit through the gear hubs. Hole H6, shaft per the FN 1 column.
- **Shaft to bearing (running sliding fit):** ANSI/ASME B4.1 Class RC 4, as the assignment requires. Hole H8, shaft f7.
- The 0.125 in shaft uses the 0.12–0.24 in row, and the 0.25 in shaft uses the 0.24–0.40 in row.

<img width="1279" height="728" alt="688443221-112e7bd0-92c0-48fc-b382-9119350eef29" src="https://github.com/user-attachments/assets/545dfbab-b9f9-4ba2-b5c0-5e2407450db5" />

<img width="1280" height="724" alt="688443218-0c30a2fd-ba71-4e85-a245-a3f1888eab9f" src="https://github.com/user-attachments/assets/3f569954-638e-47e3-ba65-bacab6d107bc" />

<img width="1286" height="783" alt="688443910-661c01eb-0fe3-4f26-8a29-ccd97a628aae" src="https://github.com/user-attachments/assets/e1fbc78c-5654-4a04-9139-78d7a7a36284" />

<img width="1287" height="783" alt="688443904-d42cdc2d-127d-4320-919b-7426fc02e18b" src="https://github.com/user-attachments/assets/46236313-13c6-4203-8cb7-b80c8029233e" />

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

**Lessons learned**

I figured out pretty early into this assignment that torque and speed basically trade off through the gear ratio, so the faster input shaft ends up carrying way less torque than the output. Both shafts had really low stress, so the diameters we were given were already plenty strong enough and strength was not what decided the design.

## Appendix

[A8 Parts Folder](https://drive.google.com/drive/folders/1bW6nyeQKVDkNSkEG4OWuLM6N5NtDFNYa?usp=sharing)
Includes the box, cover, shafts, gears, bearings, assembly, and drawings.

## Time Spent:

9 hours spent on this assignment

