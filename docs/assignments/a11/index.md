# A11 – Motor Selection


## Objectives


Part 2 Scope of Work:
Select a Motor
Design Motor Mounts
Select or design a coupler
Design a Frame to support crosshead stability and tensile load
Select or design a Clamp Analysis and Design
Provide a complete CAD model of the engineered parts of the Tensile Tester
Deliver a Bill of Materials and Engineering Cost


## Analyze


## Motor Selection and Attachments

## Motor Selection: Misha Likhtenbaum

(10pts) Use torque and speed requirements derived from the lead screw design to select an appropriate motor (DC, stepper, or gearmotor). Document all relevant motor parameters: rated torque, speed, efficiency, voltage/current, and mounting interface. Verify that:

A useful source for understanding how T-slot rail hardware functions can be found [here](https://8020.net/blog/guide-to-industrial-fasteners-for-t-slot-framing.html)

- The motor provides sufficient output torque to achieve the maximum 2 kN load across the entire speed range (1–50 mm/min).
- Provide a speed-torque curve showing the selected motor.

Based on the following hand calculations, the "Stepper Motor with Square Body, NEMA 23, 173.5 in.-oz. Maximum Holding Torque (SN: 6627T53)" from McMaster-Carr can provide an adequate amount of torque (when assuming an ACME lead screw efficiency of 30%) to create 1KN of force per lead screw. The motor specifications can be accessed at this [link](https://www.mcmaster.com/6627T53/)

<img width="2073" height="1634" alt="Motor Selection" src="https://github.com/user-attachments/assets/a30ff62f-08ef-40b5-bf3d-343fafbeb96d" />

[Hand calculations for torque conversion and thread efficiency]

<img width="627" height="477" alt="Stepper Motor Image" src="https://github.com/user-attachments/assets/63db5a08-6417-4a33-9222-4a95cd20463f" />

[Chosen stepper motor]

<img width="627" height="477" alt="Stepper Motor Drawing" src="https://github.com/user-attachments/assets/babe5154-d9ac-41ea-a854-e51e1fc14f1b" />

[Chosen stepper motor drawing]

<img width="1007" height="758" alt="Stepper Motor Speed Torque Curve" src="https://github.com/user-attachments/assets/178c7923-04f0-4e7b-b0d0-47e95ade5858" />

[Chosen stepper motor speed-torque curve]


## Motor Mount Bracket: Misha Likhtenbaum

(10pts) Design a motor mount bracket or housing to securely attach the motor to the tester frame. Use the mounting holes in the motor as a pattern for features in the bracket. Select a four-hole pattern to secure the mount to the top of the frame. The mount must: a.) Maintain precise alignment with the lead screw to prevent binding or eccentric loading. b.) Accommodate service access for assembly and maintenance. c.) Withstand both operational torque and reaction forces without excessive deflection.

The T-slot bolts we will use to couple the motor mount to the T-slot rails can be found [here](https://8020.net/3611.html)
The T-slot nuts we will use to couple the motor mount to the T-slot rails can be found [here](https://8020.net/40-3203.html).

An important consideration during this phase was ensuring the motor mounting bracket and load cell have enough clearance to fit within the constraints of our current frame setup. This check is detailed in the calculation: ((.5125 * 2) + 2.25) + 2.4, which adds up to 5.675 in (which is less than 6 in), meaning that the current motor mount design will work with our current frame spacing.

- List all the knowns and unknowns.
- Detail a FBD for the bearing stress.
- Model the equations to solve for thickness.
- Numerically solve for the minimum thickness.

When solving for tear-out thickness in the following calculations, L is simplified to be the distance from the edge of the hole to the nearest edge of the bracket, rather than the distance from the edge of the hole to the bracket edge along the path of the force vector. This aids in ease of calculation and increases the resultant safety factor of the design in vulnerable areas.

After conducting our calculations, a minimum thickness of .0054 in was determined. This dimension may resist the applied force on paper, but would not function in any real application; therefore, our bracket will be made of 1/16 in thick 6061-H12 Plate.

<img width="2086" height="2989" alt="Force Calculation" src="https://github.com/user-attachments/assets/403b2bcd-6180-44eb-84e1-82c859f5472a" />

[Motor mounting and motor hole force calculations]

<img width="2358" height="1530" alt="Thickness Determination" src="https://github.com/user-attachments/assets/7a324c7c-99c7-48fe-9242-773e1b4cfc24" />

[Resultant thickness calculations]


## Coupler Design: Misha Likhtenbaum

(10pts) Select/design a coupler to connect. Use shear stress torsion analysis to determine the inner and outer diameter of the coupler.

- List all the knowns and unknowns.
- Detail an FBD for the torsional stress
- Model the equations to solve for thickness.
- Numerically solve for the thickness.

ASTM A36 Steel was the material used to create the coupler. This is due to its high strength, which allows the component to be compact while experiencing minimal deformation. After hand calculations were conducted, a minimum outer diameter of .3944 in was determined for the coupler. This would result in a minute wall thickness of .0097 in, so a stock bar of 3/4 in ASTM A36 Steel, with a length of 1.5 in, will be more than sufficient for our design. This thickness will also allow us to use fairly substantial 1/8 x 3/16 in grub screws to ensure that the coupler will not slip on the motor or the lead screw.

Applicable coupler grub screws (Black-Oxide Alloy Steel Cone-Tip Set Screw 5-40 Thread Size, 3/16" Long) can be found [here](https://www.mcmaster.com/92695A126/)

<img width="150" height="211" alt="Grub Screw Example" src="https://github.com/user-attachments/assets/db25e66f-4654-49c3-aa1d-809d6e46048c" />

[1/8 x 3/16 (5-40 thread size) grub screw example (sourced from [this](https://www.ebay.co.uk/itm/187812375772) page]

<img width="2187" height="3125" alt="Coupler OD" src="https://github.com/user-attachments/assets/d14664f8-6d11-4e79-bc61-6c6d943d4cb1" />

[Hand calculations for outer diameter/coupler thickness]

## Analyze and Design a Frame

## Frame Connector Bracket (Motor Twist Analysis): Misha Likhtenbaum

(10pts) Analyze the applied twist by the motors to design a bracket to affix the vertical standoffs of the frame to the top of the frame. Select proper Connectors for T-Slot Framing using the resources.

- List all the knowns and unknowns.
- Detail an FBD for the top of the frame
- Symbolically represent the forces required to stabilize the top of the frame at the ends.
- Using the appropriate stress analysis, select the proper mounting from the top to the vertical frame.

An important point of our design is that our motors are mounted on the bottom portion of our tester, rather than the top, which means that they don't have to output the extra torque required to lift their own weight. Therefore, for this section of the project, we will be analyzing the necessary brackets to affix the vertical standoffs to the BOTTOM of the frame.

Another important note for this portion of the project is that we will have to change the type of T-slot rails that we use. For visual cleanliness on our base tensile tester design, we used T-slot rails that only had one "T-slot" on one side. This means that they cannot be used with plate connectors and will have to be switched out for regular, 4-sided T-slot rails.

Plate connectors are our T-slot rail connectors of choice, as they allow us to minimize the horizontal length of our tensile tester design, which provides 2 key advantages. Firstly, a shorter beam length lessens the amount of deflection caused by the application of a moment. Secondly, it minimizes the desk space required by the tester. We will use the same connectors throughout our design to keep it visually uniform.

The following hand calculations detail two problem-solving processes. Firstly, the bottom of the frame is modelled as a fixed-fixed beam to determine the values of its reaction moments. Secondly, each joint (where the L-plate connector juts out from the vertical column rail) is modelled as a cantilever beam that undergoes the applied moment that was determined in the previous calculation. The magnitude of the moment is halved in this calculation to account for there being a connector on both sides of the bottom beam. A maximum deflection of .002 in is assumed to be adequate.

After the aforementioned calculations were conducted, it was determined that each L-plate connector would experience a maximum deflection of .00150 in and a max bending stress of 348.8 psi, both of which lie within our deflection and stress allowances. If FEA results differ, design alterations can easily be made (thicker L-plate connectors, flanged L-plate connectors, and additional connectors could all be employed to further stiffen the design)

80-20 40-4481 40 Series 5 Hole - “L” Flat Plate connectors are viable for use in our design and can be accessed through [this](https://8020.net/40-4481.html) link. Grainger did not have L-shaped plate connectors available; all of theirs were flanged, which would require us to lengthen the horizontal footprint of our design.

<img width="2335" height="3207" alt="L Connector calc" src="https://github.com/user-attachments/assets/ab216209-a1de-4422-a28c-c451ac15d680" />

[Hand calculations for bottom tensile tester rail and joint connectors]


## CAD Assembly


<img width="833" height="873" alt="Screenshot 2026-11-19 072635" src="https://github.com/user-attachments/assets/69965588-2586-41d0-8871-6b76ecea5343" />


## Top Frame FEA: Ryan Thomas

(20 pts) Verify that the top of the frame constructed from heavy 40 Series will provide the strength necessary to hold the loads of the lead screw load and torque. Conduct an FEA using the proper constraints and loads.

**Model Setup:**

Because our motors are mounted on the bottom of the tester, the top rail carries the two floating flange bearings rather than the motors. Each bearing passes its lead screw's 1 kN (224.8 lbf) axial tension into the top rail. To stay conservative and satisfy the required load case, the full motor reaction torque was also applied at each bearing mount. 

The torque per lead screw is T = F·L / (2πη) = (224.8 lbf)(0.0833 in) / (2π · 0.30) ≈ 9.94 lbf·in (1.12 N·m), using the 3/8"-12 ACME lead screw at 30% efficiency. The motor's maximum holding torque of 173.5 oz·in (10.84 lbf·in, 1.23 N·m) was applied instead as an upper bound.

| Item | Value |
| :--- | :--- |
| Geometry | E40-4040 rail, 11" long, with L-plate connectors (40-4481) and flange bearing mounts |
| Material | 6061-T6 aluminum (E = 10,000 ksi / 68.9 GPa, ν = 0.33, Sy = 39.9 ksi / 275 MPa) |
| Fixtures | Fixed geometry on both rail end faces (connector interfaces), matching the fixed-fixed hand calculation model |
| Contacts | Global bonded (bolt preload not modeled) |
| Load 1 | 1,000 N (224.8 lbf) per bearing mount face, axial along lead screw (×2) |
| Load 2 | 1.23 N·m (10.84 lbf·in) torque per bearing mount about the lead screw axis (×2) |
| Mesh controls | Blended curvature-based mesh, which automatically refines at the T-slots, bolt holes, and plate edges (min element size = 1/20 of max) |

**Meshing & Verification:**

| Mesh | Element Size (global / local) | # Elements | # Nodes | Max von Mises (psi) | Max Vertical Deflection at Grip Line (in) | % Change (Stress / Deflection) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Standard | 0.537 / 0.0268 | 668,670 | 996,164 | 2,420 | 7.44e-4 | — |
| Fine | 0.268 / 0.0134 | 751,302 | 1,112,171 | 2,313 | 7.43e-4 | -4.4% / -0.1% |

Both meshes used the blended curvature-based mesher at high quality (16 Jacobian points). Halving the element size changed the maximum von Mises stress by 4.4% and the maximum deflection by 0.1%, both below the 5% convergence criterion, so the Fine mesh results are reported. Because the peak stress decreased with refinement rather than climbing, it is not a stress singularity.

**Results:**

| Result | Value | Location |
| :--- | :---: | :--- |
| Maximum von Mises stress | 2,313 psi (15.9 MPa) | Rail face at the edge of the bearing mount plate |
| Maximum vertical deflection at grip line | 7.43e-4 in (0.0189 mm) | Rail midspan, specimen centerline |
| Minimum Factor of Safety (Sy / σmax) | 17.2 | Rail face at the edge of the bearing mount plate |

**Standard Mesh Results:**

<img width="822" height="870" alt="Screenshot 2026-11-19 043827" src="https://github.com/user-attachments/assets/dbf7ebef-a8d7-4195-8bc6-0d4c9df8c35d" />

[Top rail von Mises stress plot, Standard mesh]

<img width="980" height="841" alt="Screenshot 2026-11-19 043845" src="https://github.com/user-attachments/assets/2b442f9d-65b0-4196-9abd-e6f43647528f" />

[Top rail resultant displacement (URES) plot, Standard mesh]

<img width="882" height="880" alt="Screenshot 2026-11-19 044046" src="https://github.com/user-attachments/assets/7a332bc9-0e06-454e-bad2-63c4352d2f55" />

[Top rail Factor of Safety plot, Standard mesh]

**Fine Mesh Results:**

<img width="816" height="857" alt="Screenshot 2026-11-19 044332" src="https://github.com/user-attachments/assets/c7925912-1b22-4c03-9f3f-d8f45af281b9" />

[Top rail von Mises stress plot, Fine mesh]

<img width="991" height="870" alt="Screenshot 2026-11-19 044345" src="https://github.com/user-attachments/assets/cc17cc3d-a33b-431b-a09b-c36d97fce1f7" />

[Top rail resultant displacement (URES) plot, Fine mesh]

<img width="841" height="862" alt="Screenshot 2026-11-19 044359" src="https://github.com/user-attachments/assets/b5fab2dd-6af4-4af0-9354-2641fb373fd0" />

[Top rail Factor of Safety plot, Fine mesh]

**Load Path and Twisting/Warping:**

The 2 kN specimen load travels from the crosshead nuts into our two lead screws, which are held in tension by the floating flange bearings on the top rail. Each bearing pulls down on the rail, bending it between the L-plate connectors, which then pass the load into the vertical rails as axial compression. The deformed shape matches the fixed-fixed model from our hand calculations, with the maximum deflection at midspan (the grip line) and the highest stresses at the edges of the bearing mount plates, where the stiff plates hand the load off to the rail. Some slight warping of the T-slot lips is visible next to the plates, but no significant twisting was observed, since the 10.84 lbf·in motor torques are small compared to the bending from the axial loads.

**Optimization Pass:**

Our top rail is already plenty strong FOS of 17.2, so we don need to make it stronger. The highest stress is at the sharp edges of the bearing mount plates. Rounding off those edges with a fillet would spread the load out more smoothly and lower that stress. After this change, the highest stress would most likely move to the ends of the rail where it connects to the frame.

## Vertical Frame FEA: Ryan Thomas

(20 pts) Verify that the vertical components of the frame constructed from heavy 40 Series will provide the strength necessary to hold the loads of the lead screw load and torque. Conduct an FEA using the proper constraints and loads. Note: there should be two forces, one axial compression and one transverse load.

**Model Setup:**

For this study, our full frame was modeled so the vertical rails are loaded and supported the same way they will be in the real tester. Each vertical rail carries 1 kN (224.8 lbf) of axial compression, which comes from the lead screws pulling down on the top rail at the two flange bearings. The transverse load represents the side force from the lead screw torque (10.84 lbf·in per motor), and it was applied at the top of the frame at the flange bearing mounts, where it pushes sideways on the tops of the vertical rails.

| Item | Value |
| :--- | :--- |
| Geometry | Full frame: E40-4040 rails (30" vertical, 11" horizontal), L-plate connectors (40-4481), and flange bearing mounts |
| Material | 6061-T6 aluminum (E = 10,000 ksi / 68.9 GPa, ν = 0.33, Sy = 39.9 ksi / 275 MPa) |
| Fixtures | Fixed geometry on the bottom faces of the frame, where it sits on the table |
| Contacts | Global bonded (bolt preload not modeled) |
| Load 1 | 1,000 N (224.8 lbf) downward at each flange bearing mount, putting each vertical rail in axial compression (×2) |
| Load 2 | ___ lbf transverse at each flange bearing mount (×2) |
| Mesh controls | Blended curvature-based mesh, which automatically refines at the T-slots, bolt holes, and plate edges (min element size = 1/20 of max) |

**Meshing & Verification:**

| Mesh | Element Size (global / local) | # Elements | # Nodes | Max von Mises (psi) | Max Displacement (in) | % Change (Stress / Displacement) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| Standard | 2.517 / 0.126 | 545,287 | 896,289 | 1,023 | 5.83e-4 | — |
| Fine | 1.481 / 0.074 | 1,361,628 | 2,152,405 | 935 | 5.84e-4 | -8.6% / +0.2% |

Both meshes used the blended curvature-based mesher at high quality (16 Jacobian points). Refining the mesh changed the maximum displacement by only 0.2%, so the deflection has converged. The maximum stress dropped by 8.6%, which is above our 5% target, because the peak sits at a sharp plate edge on the top rail where the stress is very sensitive to element size. Since the stress went down with refinement and the FOS is still about 35, this does not change our conclusion that the frame is safe.

**Results:**

| Result | Value | Location |
| :--- | :---: | :--- |
| Maximum von Mises stress | 935 psi (6.4 MPa) | Top rail, at the edge of the right bearing mount plate |
| Maximum stress in the vertical rails | Below ~200 psi | Near the L-plate connectors |
| Maximum displacement | 5.84e-4 in (0.0148 mm) | Top rail, at midspan |
| Minimum Factor of Safety | 35.0 | ___ |

**Standard Mesh Results:**

<img width="1005" height="842" alt="Screenshot 2026-11-19 063042" src="https://github.com/user-attachments/assets/6de5e432-cace-4c75-8835-a6b7d6223f2e" />

[Full frame von Mises stress plot, Standard mesh]

<img width="1006" height="867" alt="Screenshot 2026-11-19 063050" src="https://github.com/user-attachments/assets/b35a1451-c97b-4f56-9a2e-418603a9f8e9" />

[Full frame resultant displacement (URES) plot, Standard mesh]

<img width="1010" height="916" alt="Screenshot 2026-11-19 063102" src="https://github.com/user-attachments/assets/cbc683a8-7c07-43c7-a5d4-f6fa03ff5d76" />

[Full frame Factor of Safety plot, Standard mesh]

**Fine Mesh Results:**

<img width="965" height="827" alt="Screenshot 2026-11-19 064130" src="https://github.com/user-attachments/assets/051b403c-f5de-4877-a241-e12ad19ab346" />

[Full frame von Mises stress plot, Fine mesh]

<img width="973" height="827" alt="Screenshot 2026-11-19 064141" src="https://github.com/user-attachments/assets/e9a2ccb0-49d9-4f15-8d3d-6423abcd2fa9" />

[Full frame resultant displacement (URES) plot, Fine mesh]

<img width="985" height="886" alt="Screenshot 2026-11-19 064206" src="https://github.com/user-attachments/assets/d43730e9-58b6-4b3c-ac12-25b48bbfa49e" />

[Full frame Factor of Safety plot, Fine mesh]

**Load Path and Twisting/Warping:**

The lead screws pull down on our top rail, which sends the load through the L-plate connectors into the vertical rails as compression and down into the table. The vertical rails bow slightly outward but stay at very low stress, with the highest stress on the top rail at the bearing mount plate edge. No noticeable twisting was seen.

**Optimization Pass:**

Our vertical rails are very lightly loaded, so they do not need to be stronger. The best change would be adding a diagonal brace or gusset at the top corners, where the vertical rails meet the top rail. This would stop the frame from bowing outward. After this, the highest stress would most likely stay at the bearing mount plate edges.

## Floating Bearing Mount: Misha Likhtenbaum

(10pts) Design a mounting bearing that allows the end of the leadscrew to rotate using an RC3 Fit class and affix to the bottom of the frame. Clearance holes for bolts must be researched in the Machinery’s Handbook.

- Justify each size and location dimension of the mount.
- Note the functional tolerances for the appropriate dimensions.

Just like for our "Select/design a coupler to connect" subsection, our design is flipped when compared to that outlined in the base design of the tensile tester, meaning that our mounting bearing(s) will be mounted on the top section of our frame. The base geometry of our floating bearing mount will be similar to that of our motor mount, as they both perform similar functions. A relatively tall journal bearing will interface with the end threads of the lead screws to more evenly distribute the pressure and velocity output from the screw rotation.

An important note for this section is that I (Misha) initially misread the instructions for this portion of the project and thought that I was to select pre-made products from a catalogue to fulfill our design requirements. After realizing my error, I decided that our design would employ a flange-style bearing, as that would best fit our design needs.

The following hand calculations determined the required dimensions of the thrust portion of the flange bearing. In theory, there are no radially applied loads on the journal portion of the bearing, so engineering reasoning has been used to keep the bearing dimensions proportional. As another side note, in reality, a set of nuts would have to be locked together, or a collar clamp would have to be mounted on the lead screw to create a shoulder for the thrust bearing to interface with. An outer diameter of 3/4 in was initially estimated for the thrust portion of the flange bearing, but that measurement resulted in a pressure safety factor of 2.94 (while we are aiming for 4.0). Therefore, the outer diameter was bumped up to 7/8 in, which better distributes the applied stress and gives us a resultant safety factor right over 4.0.

Following the pressure and velocity analysis, the thrust element of the flange bearing is specified as SAE 841 bronze with a 3/8 in (0.375 in) inner diameter (+0.0006 in) and a 7/8 in (0.875 in) outer diameter (+0.0011/+0.0007 in). It has a thickness of 1/8 in. The journal portion of the flange bearing is specified in SAE 841 bronze with a 3/8 in (0.375 in) inner diameter (+0.0006 in) and an outer diameter of 5/8 in (+0.0009/+0.0006 in). It also has a thickness of 1/8 in.


<img width="2284" height="3271" alt="Axial force calc" src="https://github.com/user-attachments/assets/1372a499-c115-436d-895d-8aa4e78f576f" />

[Axial force calculations for thrust element design]

<img width="1589" height="1059" alt="Rc3 for bearing mount" src="https://github.com/user-attachments/assets/1c180be5-aad1-40fc-915e-12c5c9c0a5e2" />

[RC3 fit class used for 3/8 in lead screw hole]

<img width="1273" height="718" alt="FN1 for bearing mount" src="https://github.com/user-attachments/assets/fe3e8608-d95d-455e-91e4-a30fb6d59a4d" />

[FN1 fit class used for flange bearing dimensions]

<img width="1823" height="2707" alt="Floating bearing mount drawing" src="https://github.com/user-attachments/assets/34fef2ea-1b0d-4a0b-85f8-40acb4aa0d70" />

[Floating bearing mount hand drawing]

<img width="2426" height="1525" alt="Flange bearing drawing" src="https://github.com/user-attachments/assets/7e657f70-ad54-4a46-afa1-84644f6148eb" />

[Flange bearing hand drawing]


## Bill of Materials and Labor Costs: Misha Likhtenbaum

(10pt) Tabulate all the costs associated with both assignment parts. Use the following template to show the associated costs. You are to use an entry-level mechanical engineering designer cost per hour of $35/hour.

A10 (Initial Design BOM and Labor Costs):

| Item Number | Quantity | Name | Cost/Item | Cost | Purchase Link |
| :---: | :---: | :--- | :---: | :---: | :--- |
| 1 | 2 | 40mm x 40mm Mono Slot T-Slotted Extrusion, 11" Long | \$9.78 | \$19.56 | [Parco Inc](https://parco-inc.com/product/40mm-x-40mm-mono-slot-t-slotted-extrusion/) |
| 2 | 2 | 40mm x 40mm Mono Slot T-Slotted Extrusion, 30" Long | \$26.67 | \$53.34 | [Parco Inc](https://parco-inc.com/product/40mm-x-40mm-mono-slot-t-slotted-extrusion/) |
| 3 | 2 | Alloy Steel Acme Lead Screw, Right Hand, 3/8"-12 Thread, 2 Feet Long | \$57.73 | \$115.46 | [McMaster-Carr](https://www.mcmaster.com/93410A111/) |
| 4 | 2 | 932 Bearing Bronze Acme Flange Nut, Right Hand, 3/8"-12 Thread | \$111.78 | \$223.56 | [McMaster-Carr](https://www.mcmaster.com/95120A592/) |
| — | — | **Total Cost** | — | **\$411.92** | — |


A11 (Comprehensive Design BOM and Labor Costs) *As per last assignment's instructions, designed parts are not priced, neither in terms of raw material nor in machining time*:

Bought parts:

| Item Number | Quantity | Name | Cost/Item | Cost | Purchase Link |
| :---: | :---: | :--- | :---: | :---: | :--- |
| 1 | 2 | E40-4040-C – 40mm x 40mm T-SLOT ALUMINUM EXTRUSION (Cut To Length) 11" | \$10.92 | \$21.84 | [Parco Inc](https://parco-inc.com/product/40mm-x-40mm-t-slotted-extrusion-cut-to-length/) |
| 2 | 2 | E40-4040-C – 40mm x 40mm T-SLOT ALUMINUM EXTRUSION (Cut To Length) 30" | \$29.72 | \$59.44 | [Parco Inc](https://parco-inc.com/product/40mm-x-40mm-t-slotted-extrusion-cut-to-length/) |
| 3 | 2 | Stepper Motor with Square Body, NEMA 23, 173.5 in.-oz. Maximum Holding Torque (6627T53) | \$111.68 | \$223.36 | [McMaster-Carr](https://www.mcmaster.com/6627T53/) |
| 4 | 4 | 40-3203: 40 Series 5/16-18 Standard Slide-in T-Nut | \$1.30 | \$5.20 | [8020](https://8020.net/40-3203.html) |
| 5 | 4 | 3611: 5/16-18 x .625" Button Head Socket Cap Screw (BHSCS) | \$0.88 | \$3.52 | [8020](https://8020.net/3611.html) |
| 6 | 1 | Black-Oxide Alloy Steel Cone-Tip Set Screw, 5-40 Thread Size, 3/16" Long (92695A126, Pack of 50) | \$8.96 | \$8.96 | [McMaster-Carr](https://www.mcmaster.com/92695A126/) |
| 7 | 8 | 40-4481: 40 Series 5 Hole - “L” Flat Plate | \$13.12 | \$104.96 | [8020](https://8020.net/40-4481.html) |
| 8 | 40 | 75-3422: Bolt Assembly - M8 x 16.00mm Blue BHSCS with Slide-In Economy T-Nut - Offset Thread - Bright Zinc | \$1.14 | \$45.60 | [8020](https://8020.net/75-3422.html) |
| 9 | 2 | Alloy Steel Acme Lead Screw, Right Hand, 3/8"-12 Thread, 2 Feet Long | \$57.73 | \$115.46 | [McMaster-Carr](https://www.mcmaster.com/93410A111/) |
| 10 | 2 | 932 Bearing Bronze Acme Flange Nut, Right Hand, 3/8"-12 Thread | \$111.78 | \$223.56 | [McMaster-Carr](https://www.mcmaster.com/95120A592/) |
| — | — | **Total Cost** | — | **\$811.90** | — |

Design cost:

| Person | Phase | Hours Worked | Cost / Hour | Cost |
| :--- | :---: | :---: | :---: | :---: |
| Misha | A10 | 10 | \$35.00 | \$350.00 |
| Ryan | A10 | 6 | \$35.00 | \$210.00 |
| Misha | A11 | 7 | \$35.00 | \$245.00 |
| Ryan | A11 | 5 | \$35.00 | \$175.00 |
| — | **Total Design Cost** | **28** | — | **\$980.00** |


## 2157 Addition – Drawing Package: Ryan Thomas and Misha Likhtenbaum

(30pts) Create a drawing package that includes detailed drawings of the designed components, an assembly isometric drawing, and a Bill of Materials (BOM). Note: Include the crosshead drawing from the previous assignment.

- Each drawing has its proper title block.
- Apply ASME Y14.5 standards for dimensioning and tolerancing.
- Include the following:
  - Third-angle projection layout.
  - Tolerance block consistent with course standards:
    - X.X ± .02
    - X.XX ± .01
    - X.XXX ± .005
 
Drawings: 

<img width="1456" height="1124" alt="image" src="https://github.com/user-attachments/assets/4486a747-c36b-4971-90b1-b8ddff093311" />

[Flange/floating bearing drawing]

<img width="1468" height="1138" alt="image" src="https://github.com/user-attachments/assets/991665ec-8cad-4b50-87ba-6b470907f3bb" />

[Flange/floating bearing mount drawing]

<img width="1384" height="1068" alt="image" src="https://github.com/user-attachments/assets/15278620-4c1f-46d9-86ec-cd4ef8c92ba2" />

[Motor mount drawing]

<img width="997" height="768" alt="crosshead drawing" src="https://github.com/user-attachments/assets/2895315b-755a-4dbf-82f2-52be338dd307" />

[Crosshead drawing]

<img width="621" height="801" alt="Screenshot 2026-11-19 075714" src="https://github.com/user-attachments/assets/99d83e12-bbf5-456b-898c-60b31b0326f4" />

[Assembly drawing]

## Decide


We chose a stepper motor for our tensile tester because it can measure strain when connected to a microcontroller, allowing us to use Hooke's Law to determine the test material's modulus of elasticity.

As mentioned in the "Analyze the applied twist" subsection of the "Analyze and design a Frame" section, we chose to mount our motors on the bottom portion of our tensile tester, which reduces the torque output required to create the necessary tensile force, and lessens the buckling forces acting on our frame.


## Communicate

## Lessons Learned: Misha Likhtenbaum

This project took me about 7 hours. One important lesson I learned was the importance of using accurate simplifications for stress and deflection calculations, as making lazy assumptions that oversimplify the actual physics behind a design can be disastrous, leading to wasted time and numerous design iterations. However, it is vital to know when a simplification is valid, since it can make a design more comprehensible and aid in the ease of calculations.

## Lessons Learned: Ryan Thomas

This project took me 6 hours to complete one important lesson that I learned was being able to work with assemblies in more detail I made subassemblies which I use to test my FEA in a more realistic manner and using the creation of those subassemblies I added them right into the final assembly which made the workflow a lot quicker and more efficient throughout this assignment.

SolidWorks file downloads [here](https://drive.google.com/drive/folders/1IhMKdD6ZhvOsRu4-RQheC9PkQh70olW9?usp=sharing)
