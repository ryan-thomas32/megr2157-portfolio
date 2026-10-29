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

- Both shafts are checked in pure torsion, using AISI 1018 cold-drawn steel (Sy = 54,000 psi). Material data source: TODO (paste link, for example MatWeb).
- The input shaft carries T = 0.469 in-lbf and the output shaft carries T = 1.25 in-lbf.

#### Input Shaft (Power Transmission):

<!-- IMAGE: input shaft knowns and unknowns -->

<!-- IMAGE: input shaft FBD -->

<!-- IMAGE: input shaft equations and calculations -->

**Result:** shear stress = **1,220 psi**, safety factor ≈ 25.5. The 0.125 in diameter is sufficient.

#### Output Shaft (Short Shaft):

<!-- IMAGE: output shaft knowns and unknowns -->

<!-- IMAGE: output shaft FBD -->

<!-- IMAGE: output shaft equations and calculations -->

**Result:** shear stress = **407 psi**, safety factor ≈ 76.5. The 0.25 in diameter is sufficient.

| Shaft  | d (in) | T (in-lbf) | Stress (psi) | Safety Factor | Sufficient? |
|--------|--------|------------|--------------|---------------|-------------|
| Input  | 0.125  | 0.469      | 1,220        | 25.5          | Yes         |
| Output | 0.250  | 1.250      | 407          | 76.5          | Yes         |

### Step 2: Design Journal Bearings:

#### Journal Bearing Sizing:

- I used two bearings per shaft, with the gear at the middle, so each bearing carries half of the gear force.
- The bearing length comes from the layout inside the gearbox: shaft sticking out of the housing (TODO in) + bearing contact length (TODO in) + gear face width and clearance (TODO in) = TODO in total. I chose the McMaster bearing closest to that length.
- The gear pitch diameter is TODO in, so the tangential force is TODO lbf and each bearing carries TODO lbf. (My first estimate used a 1.25 in placeholder pitch diameter. TODO: update with the real value.)

<!-- IMAGE: bearing knowns and unknowns -->

<!-- IMAGE: journal bearing FBD -->

<!-- IMAGE: bearing equations and calculations -->

**Result:** (TODO: update with the real values)

| | d (in) | L (in) | P (psi) | V (fpm) | PV (psi·fpm) |
|---|---|---|---|---|---|
| Input bearing  | 0.125 | TODO | TODO | 96 | TODO |
| Output bearing | 0.250 | TODO | TODO | 72 | TODO |

*(Placeholder results with L = d: input P = 64 psi, PV ≈ 6,100; output P = 16 psi, PV ≈ 1,150.)*

#### Bearing Material:

I picked **porous bronze** from the lecture table, which allows 4,500 psi, 1,500 fpm, and a PV of 50,000 psi·fpm. Both bearings are well under all three limits.

<!-- IMAGE: lecture bearing material table with the circled columns -->

#### Journal Bearing Thickness:

<!-- IMAGE: bearing thickness knowns and unknowns -->

<!-- IMAGE: bearing thickness FBD -->

<!-- IMAGE: bearing thickness equations and calculations -->

**Result:** the minimum thickness is 0.0009 in (input) and 0.0004 in (output). Strength doesn't set the wall, so the press fit and machining do. The selected bearings have walls of 1/16 in (input) and 1/32 in (output), which are more than enough.

#### McMaster-Carr Bearings:

| | Part Number | ID | OD | Length | Qty |
|---|---|---|---|---|---|
| Input bearing  | 9368T95 | 1/8"  | 1/4"  | 1/8" | 2 |
| Output bearing | 9368T11 | 1/4"  | 5/16" | 1/4" | 2 |

Both are 841 Bearing Bronze sleeve bearings (TODO: copy the exact product name, and update the part numbers if your length budget picks different sizes).

<!-- IMAGE: McMaster bearing table with the selected rows -->

### Step 3: Gearbox Sketch:

The housing is two pieces, a box and a cover, held together with M3 × 0.5 bolts into tapped holes in the box wall (TODO: change if you use a different fastener). Each half has bearing bores, 1/4" for the input bearing and 5/16" for the output bearing, so each shaft is supported at both ends.

<!-- IMAGE: housing sketch -->

<!-- IMAGE: sketch of how the two halves fit together -->

### Step 4: Gearbox 3D Model:

- I built the model parametrically, starting from the known gear and bearing dimensions as global variables and finishing with the housing dimensions and material.
- Gears and bearings were downloaded from McMaster-Carr. The shafts and housing were modeled from my own sketches.

#### Box:

The box is the back half of the gearbox, and it holds the gears. It is made of cast alloy steel. I chose it for its high load capacity, based on what automotive gearbox housings use. The gearbox loads are very small (tangential force about 2 lbf, bearing pressures 16 to 64 psi), so the steel is much stronger than it needs to be. TODO: housing mass from SolidWorks, and the trade-off against aluminum (more weight and machining effort, and why I accepted it).

##### 1.

TODO: why you started here. For example: how you sized the cavity from the real gear diameters, the clearance on every inner face, and the wall thickness you assumed.

<!-- IMAGE: box step 1, caption: [Initial box sketch using global variables] -->

##### 2.

TODO: how you decided the extrusion depths, and any sketch on paper that helped.

<!-- IMAGE: box step 2a, caption: [Back wall extrusion] -->

<!-- IMAGE: box step 2b, caption: [Side wall extrusion] -->

##### 3.

TODO: tapped bolt holes for the cover (size, pitch, depth, and why).

<!-- IMAGE: box step 3, caption: [Tapped holes for M3 x 0.5 bolts] -->

##### 4.

TODO: bearing bores in the back wall (diameters, depth, positions, and how you located them).

<!-- IMAGE: box step 4a, caption: [Sketch for bearing bore positions] -->

<!-- IMAGE: box step 4b, caption: [Bearing bores in the back wall] -->

##### 5.

Final product and global variables.

<!-- IMAGE: final box, caption: [Final box] -->

<!-- IMAGE: box global equations, caption: [Global equations] -->

#### Cover:

The cover is the front half of the gearbox. It has holes for the bolts that fasten it to the box, and two bores for the bearings. It is made of TODO (material, and why).

##### 1.

TODO: how you started the cover (for example, from the box outline so the halves match).

<!-- IMAGE: cover step 1, caption: [Cover sketch] -->

##### 2.

TODO: bearing bores in the cover (sizes and positions, matching the box).

<!-- IMAGE: cover step 2, caption: [Bearing bores in the cover] -->

##### 3.

TODO: bolt holes in the cover, and any problem you noticed with the fit.

<!-- IMAGE: cover step 3, caption: [Bolt holes in the cover] -->

##### 4.

Final product and global equations.

<!-- IMAGE: final cover, caption: [Final cover] -->

<!-- IMAGE: cover global equations, caption: [Global equations] -->

#### Shafts, Gears, and Bearings:

TODO: how you made or downloaded each part.

<!-- IMAGE: shafts, caption: [Input and output shafts] -->

<!-- IMAGE: McMaster parts in SolidWorks, caption: [Gears and bearings from McMaster-Carr] -->

#### Assembly:

The gearbox goes together in this order: press the bearings into the box and cover, press the gears onto the shafts, slide the shafts into the back bearings and mesh the gears, fit the cover, and bolt it down.

**Clearance check:** TODO (gear to wall, gear face to wall).

<!-- IMAGE: exploded assembly, caption: [Exploded view] -->

<!-- IMAGE: assembled gearbox, caption: [Assembled gearbox] -->

<!-- IMAGE: section view, caption: [Section view showing the gear mesh and bearings] -->

### MEGR 2157 Addition:

- Six multi-view CAD drawings and one assembly drawing with complete dimensioning and proper tolerancing, in third-angle projection (ASME Y14.5).
- Tolerance block: X.X ± .02, X.XX ± .01, and X.XXX ± .005.
- At least two callouts with different tolerances on critical features: TODO (for example, the bearing bore fit and the shaft diameter).

<!-- IMAGE: input shaft drawing -->

<!-- IMAGE: output shaft drawing -->

<!-- IMAGE: box drawing -->

<!-- IMAGE: cover drawing -->

<!-- IMAGE: input bearing drawing -->

<!-- IMAGE: output bearing drawing -->

<!-- IMAGE: assembly drawing with bill of materials -->

## Decide

- **Housing material:** cast alloy steel. I based the choice on what automotive gearbox housings use for high load capacity. The gearbox loads are very small, so the steel is much stronger than it needs to be. The trade-off is extra weight and machining effort compared with aluminum, which would also work. I chose steel because TODO (for example, stiffness for bearing alignment, strong M3 threads, or a conservative first design).
- **Shaft material:** AISI 1018 steel, because the stresses are far below its strength and it is easy to machine. TODO: confirm.
- **Bearing material:** porous bronze, because it passes the load, speed, and PV limits with a wide margin. TODO: confirm.
- **Fastening:** M3 bolts into tapped holes, so the box can be taken apart. TODO: confirm.

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

| Task | Time (hours) |
|---|---|
| Reading and planning | TODO |
| Shaft calculations | TODO |
| Journal bearing calculations | TODO |
| McMaster selection | TODO |
|
