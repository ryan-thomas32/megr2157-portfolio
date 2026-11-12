# A10 – Lead Screw Translating System


## Objective:

Design and build a mechanically driven tensile tester capable of applying up to 2 kN axial tensile load with a controllable crosshead speed from 1 to 50 mm/min. Each team is responsible for the mechanical components outlined below. The system will provide consistent, well-aligned loading for polymers and light metals, suitable for instructional use and basic materials evaluation.

Relevant Example Figures:

<img width="726" height="778" alt="Figure 1 Concept of Tensile Tester" src="https://github.com/user-attachments/assets/ab0eb70e-f2b4-464b-bc3c-611c4b7f3536" />

[Figure 1: Tensile Tester Concept]

<img width="560" height="407" alt="image" src="https://github.com/user-attachments/assets/3c3506c1-dddb-444b-814e-323babdee42b" />

[Figure 2: Tensile Tester Diagram found on page 15 of [this](https://repositum.tuwien.at/bitstream/20.500.12708/200949/1/Demmel%20Stella%20-%202024%20-%20Design%20manufacturing%20and%20testing%20of%20an%20open-source...pdf) reference document]

Part 1 Scope of Work
Develop a lead-screw–driven crosshead 
Ensure accurate, repeatable load application to 2 kN with minimal crosshead deflection and misalignment.
Provide robust specimen gripping, simple calibration provisions (mechanical), and safe, ergonomic operation.

Key Constraints
No electronics, no software: purely mechanical.
Load capacity: 2 kN (with appropriate safety factor in structure and drivetrain).
Speed range: 1–50 mm/min (achieved via screw lead selection).
Form factor: bench-top footprint favored; manageable overall height; 18-inch leadscrew minimum.
Safety Factor: 4


## Analyze:


### Leadscrew design (35pts): Misha

ASTM A193 Grade B7 steel (alloy steel) is used for the leadscrew material in order to minimize the necessary dimensions. ASTM A193 Grade B7 steel has a tensile yield strength of 125000 Psi.

To select a leadscrew, the team must determine the minimum diameter, rotational speed range, and maximum torque.


#### Minimum diameter:

Choosing the smallest available lead screw (1/4" major diameter) from McMaster-Carr is more than adequate, as proven by the following formula that calculates the minor diameter of a 1/4" screw and compares it to our calculated minimum diameter of .0957". Therefore, recalculating stress values for our chosen 3/8"-12 lead screw is unnecessary, as it is even more capable of sustaining the applied forces.

This calculation proves that a 1/4"-16 screw has a minor diameter larger than our minimum calculated diameter: $d_r = d - p = 0.2500'' - 0.0625'' = 0.1875'' > 0.0957''$

<img width="2554" height="3295" alt="Min D" src="https://github.com/user-attachments/assets/038ba5b0-b299-46f9-b838-fcc27ffc2559" />
[Minimum diameter of lead screw]


#### Range of rotational speed given the linear speed:

Initially assumed a lead of .063" to match the smallest diameter alloy steel lead screw sizes provided by McMaster-Carr. After re-designing around a 3/8"-12 lead screw, our actual, final RPM ranges from .47 to 23.62.

<img width="2185" height="2926" alt="RPM" src="https://github.com/user-attachments/assets/d57c89f6-d824-45c4-95c5-2e5fd8db85f2" />
[Rotational speed of 1/4"-16 lead screw]

<img width="1971" height="1684" alt="Rpm recalc" src="https://github.com/user-attachments/assets/5c8e7f07-94e7-4421-9128-7257371db3c4" />
[Rotational speed of 3/8"-12 lead screw]


#### Select a lead screw by determining max torque

Determine the torque required to create 1 kN axial force per lead screw. The "Extra" note at the bottom uses the calculated torque value to determine the resultant shear, demonstrating that it is far below the typical shear yield threshold of steel (~35,000 psi). Friction was excluded from these calculations, as it was not stressed in the lecture or in the provided formulas.

<img width="1108" height="1419" alt="Torque og" src="https://github.com/user-attachments/assets/f6cdf30d-6ec6-42de-a814-bc77cf21105e" />
[Torque of 1/4"-16 lead screw]

<img width="1550" height="2658" alt="Torque recalc" src="https://github.com/user-attachments/assets/0151fb5c-f237-44b9-98d8-2afed25c62ea" />
[Torque of 3/8"-12 lead screw]

 
#### Select the leadscrew from the resources section on Leadscrews. 

Selected: Alloy Steel Acme Lead Screw, Right Hand, 3/8"-12 Thread Size, 12" Long, 93410A916

After conducting the aforementioned calculations, we initially selected the smallest leadscrew (alloy steel) offered by McMaster-Carr. It was the Alloy Steel Acme Lead Screw, Right-Hand, 1/4"-16 Thread Size. Although that specific lead screw was capable of withstanding the applied load, the 1/4-16 nut that McMaster-Carr has available did not, so we had to recalculate our lead screw measurements. After recalculating, we chose to use an ACME 3/8"-12 lead screw, which has a larger diameter and therefore a larger inner thread bearing area. The required length will be determined by overall tensile tester geometry and possibly deflection calculations. We did not choose the ACME stub-thread design because those threads are meant for applications in which maintaining the wall thickness of a thin-walled sleeve is necessary (not relevant to our design). It is also important to note that the portion of the screw that is secured in the lower portion on the tensile tester must be able to spin freely; otherwise, the design will not function correctly.

Any of the lead screws in the following figure are possible choices:
<img width="1129" height="86" alt="list of compatible 38_12 lead screws" src="https://github.com/user-attachments/assets/e8453bc0-88b1-4297-93be-fd3b45e1084d" />
[3/8"-12 lead screws of varying lengths]

<img width="905" height="382" alt="38 Lead Screw Diagram" src="https://github.com/user-attachments/assets/0e868820-c0f6-45ab-91df-aa4e4dd5037b" />
[3/8"-12 lead screw dimensions drawing sourced from [site](https://www.mcmaster.com/93420A882/)]

For the sake of the cost tabulation detailed later in the project, we will assume that a lead screw length of 12in will be sufficient for our tensile tester design, as the next size up (24in) will most likely be overkill. 


### Nut and Flange Design (10pts): Misha

Selected: 932 Bearing Bronze Acme Flange Nut, Right-Hand, 3/8"-12 Thread Size, (7/8" height), 95120A592

Analyze the internal threads of the nut to select a proper bronze nut/flange. Verify the internal threads support the load using the thread-bearing bending stress analysis in lecture notes and a safety factor.

This section of the project is where our design had to be altered, and calculations had to be redone. Our initial choice of the 1/4-16 lead screw was valid in terms of axial load, but the nuts available to us were incapable of sustaining our safety factor of 4.0. Therefore, we went back and decided to use a 3/8"-12 lead screw, allowing us to employ a taller nut that had more thread engagement, better distributing the applied loads.

Before redesign (using the 1/4"-16 screw), our safety factor was too low:$SF_{\text{actual}} = \frac{\sigma_{B,\text{allow}}}{\sigma_B} = \frac{2,500\text{ psi}}{1,046.8\text{ psi}} = \mathbf{2.39}$

After redesign (using the 3/8"-12 screw), our safety factor was more than adequate:$SF_{\text{actual}} = \frac{\sigma_{B,\text{allow}}}{\sigma_B} = \frac{2,500\text{ psi}}{490.7\text{ psi}} = \mathbf{5.10}$

<img width="2326" height="3007" alt="Nut stress" src="https://github.com/user-attachments/assets/9681a223-ac52-4a6d-8462-e97a776f9057" />
[Nut bearing stress calculation and recalculation]

The final flange nut we selected, based on its resultant safety factor, was the 932 Bearing Bronze Acme Flange Nut, Right-Hand, 3/8"-12 Thread Size (7/8" height), which has a serial number of 95120A592.

<img width="1002" height="766" alt="38 lead nut" src="https://github.com/user-attachments/assets/929b9d45-375a-47c6-aa74-52afe7c0b39b" />
[3/8"-12 lead nut dimensions drawing sourced from [site]([https://www.mcmaster.com/93420A882/](https://www.mcmaster.com/95120A592/))]


### Design the Crosshead (25 pts): Misha

Analyze the minimum strength required for the load and the maximum deflection of .1 mm. There is much freedom to design the crosshead to determine the size and material. Use research to determine an appropriate length of the crosshead. Use the nut flange to determine the minimum base.

To keep hand calculations relatively straightforward, we used a rectangular cross-section for our crosshead. 1060-H12 aluminum is to be the crosshead material, due to its high strength-to-weight ratio.

For length, engineering reasoning was used to determine a valid dimension. We needed our tensile tester to have a small enough footprint to sit on a regularly sized desk, but we also required a width with enough to allow adequate room for our dogbone test specimen and our lead screws, plus any additional clearance between components. The following diagram details the general measurements used to find our overall length, and the shear and moment diagrams that outline the behavior of the beam under loading.

<img width="2484" height="3203" alt="Crosshead general dimensions" src="https://github.com/user-attachments/assets/334f4b2e-e78b-4d69-aaa7-2d50676d283b" />
[General crosshead structure]

Although the overall length of the crosshead is 11in (updated from the initial length estimate of 10in found in figure "General crosshead structure"), only the middle 6in portion of it is affected by the applied forces, and therefore is the section analyzed in our calculations.


#### Use stress/strength analysis to determine the size and material of the crosshead.

<img width="2319" height="2995" alt="Crosshead beam stress" src="https://github.com/user-attachments/assets/eebdeaf4-97a8-4675-852e-734a373ace0a" />
[Height calculations from stress analysis]


#### Use deflection analysis to determine the size and material of the crosshead.

<img width="2607" height="3418" alt="Crosshead beam defl" src="https://github.com/user-attachments/assets/c40f0e88-c11d-41e5-898e-cfdaae2f8c59" />
[Height calculations from deflection analysis]

#### Crosshead final dimensions: 11in long, 1.25in x 1.25in cross section

Based on an assumed base dimension of 1.25in, our crosshead needs to have a height of 1.091in to resist the stress created by the applied loads. However, since this height is not limited by our design constraints, using a 11in long, 1.25in x 1.25in piece of aluminum bar stock will simplify any further calculations, and ensure that sourcing components will be a simple process.


#### Generate a multiview paper sketch of the crosshead. 

The sketch should be neatly presented with appropriate views (front, top, side) and sufficient annotations to communicate geometry, proportions, and nut/flange mounting intent.

For this multiview sketch, the overhanging portions of the crosshead that mate with the alignment columns on the outside of the tester have been increased to 2in past each flange. This may be altered once we create the overall structure of the tensile tester in CAD, but the overhanging portion of the structure is totally unaffected by the applied forces regardless.

<img width="2913" height="2244" alt="Crosshead multiview" src="https://github.com/user-attachments/assets/2380c523-ff05-4904-b8c5-30f4c9d2d843" />
[Crosshead multiview sketch]


### T-slot Frame Selection (as per crosshead constraints)

Selected: 40 SERIES, 40mm x 40mm Mono Slot T Slot Aluminum Framing Extrusion

The T-slot frame column we selected to design our crosshead around was an E40-4001-C – 40mm x 40mm MONO SLOT ALUMINUM EXTRUSION from parco-inc. We couldn't find the full technical drawings of the T-slot framing available at Grainger, so we chose a different supplier. The T-frame can be accessed at this [link](https://parco-inc.com/product/40mm-x-40mm-mono-slot-t-slotted-extrusion/). For our theoretical design and cost table, a length of 24" should be adequate. If the overall design changes, we can easily alter both our frame design and our cost table.


### Tabulating Costs (10 pts): Misha
In order to get credit for this portion of the assignment, you must not use an image for the table, and it needs to have functional links. The crosshead will not be factored into the table.


| Item Number | Quantity | Name | Cost/Item | Cost | Purchase Link |
| :---: | :-: | :--- | :-: | :-: | :---: |
| 1 | 2 | 40mm x 40mm Mono Slot T-Slotted Extrusion, 24" Long | $21.32 | $42.64 | [Parco Inc](https://parco-inc.com/product/40mm-x-40mm-mono-slot-t-slotted-extrusion/) |
| 2 | 2 | Alloy Steel Acme Lead Screw, Right Hand, 3/8"-12 Thread, 12" Long | $31.13 | $62.26 | [McMaster-Carr](https://www.mcmaster.com/93410A916/) |
| 3 | 2 | 932 Bearing Bronze Acme Flange Nut, Right Hand, 3/8"-12 Thread | $111.78 | $223.56 | [McMaster-Carr](https://www.mcmaster.com/95120A592/) |
| | | | **Total Cost** | **$328.46** | |



### Parametric Modeling (20 pts): Ryan
Download/create 3D models. Assemble the components in CAD. Do not create from scratch items you can download.

#### Equations:

The hand calculations were entered as global variables in the SolidWorks Equations Manager to drive the model.

<img width="1316" height="846" alt="image" src="https://github.com/user-attachments/assets/35e517e4-3073-44ab-8356-5f38d63096dd" />


[SolidWorks equations]

#### Crosshead (designed):

11in x 1.25in x 1.25in, 1060-H12 aluminum.

<img width="1836" height="793" alt="Screenshot 2026-11-12 001057" src="https://github.com/user-attachments/assets/070a3eac-a194-4ee1-a1d4-55bfd99d12ff" />
<img width="1422" height="635" alt="Screenshot 2026-11-12 001113" src="https://github.com/user-attachments/assets/4281ec33-2728-4b1a-861b-355eca461bd7" />


<img width="1327" height="756" alt="image" src="https://github.com/user-attachments/assets/3d20ae3e-0f13-41f1-b642-492b28f0f82c" />

[Crosshead model]

#### Leadscrew (downloaded):

[McMaster-Carr 93410A916](https://www.mcmaster.com/93410A916/)

<img width="1342" height="676" alt="image" src="https://github.com/user-attachments/assets/94e101c2-8617-4b1a-b058-5055b4b71751" />

[Lead screw model]

#### Nut/Flange (downloaded):

[McMaster-Carr 95120A592](https://www.mcmaster.com/95120A592/)

<img width="1006" height="847" alt="image" src="https://github.com/user-attachments/assets/54824ea2-996d-4b22-bff5-17578dbf9d6d" />

[Flange nut model]

#### Frame (parts downloaded):

[Parco E40-4001-C](https://parco-inc.com/product/40mm-x-40mm-mono-slot-t-slotted-extrusion/)

SS

[T-slot frame model]

#### Assembly:

SS

[Full assembly]


### 2157 Addition: Use Finite Element Analysis (FEA) on the crosshead (20 pts): Ryan

#### Model Setup:

- Material: 1060-H12 aluminum
- Fixtures: lead screw holes
- Load: 2 kN at center of crosshead

<img width="1110" height="701" alt="Screenshot 2026-11-12 011127" src="https://github.com/user-attachments/assets/a8624988-8543-4a5f-ba14-c663a1d1c4b3" />

[Fixtures and load]

Decided to add a puck similar to the load device onto the bottom of the crosshead to FEA test my part in an assembly, treating the puck rigidly in an attempt to make the FEA results more realistic.

#### Meshing & Verification:

##### Mesh 1 – Coarse (2,804 elements)

<img width="1257" height="820" alt="Screenshot 2026-11-12 062342" src="https://github.com/user-attachments/assets/b5c5d384-4b6e-44b0-91b5-1962c2d88dcd" />


[Mesh 1 von Mises]

<img width="1365" height="757" alt="Screenshot 2026-11-12 062136" src="https://github.com/user-attachments/assets/6f31f6e5-b6b4-4241-ac9c-3ea210d6f11b" />

[Mesh 1 URES]

##### Mesh 2 – Refinement 1 (12,524 elements)

<img width="1195" height="727" alt="Screenshot 2026-11-12 062553" src="https://github.com/user-attachments/assets/62f1caf8-854c-4b06-b8bf-3b64bf55fe75" />

[Mesh 2 von Mises]

<img width="1232" height="737" alt="Screenshot 2026-11-12 062606" src="https://github.com/user-attachments/assets/d8230d6c-0ee7-402a-b8cb-f4955ff555cd" />

[Mesh 2 URES]

##### Mesh 3 – Refinement 2 (77,155 elements)

<img width="1242" height="832" alt="Screenshot 2026-11-12 062907" src="https://github.com/user-attachments/assets/be2888b8-a86f-4669-a856-f1b28911fd9e" />

[Mesh 3 von Mises]

<img width="1201" height="767" alt="Screenshot 2026-11-12 062918" src="https://github.com/user-attachments/assets/840d0612-0111-40cf-badd-ff9ddb8ffd30" />

[Mesh 3 URES]

##### Convergence Results

| Mesh | Elements | Nodes | Min / Max Element Size (in) | Max von Mises (psi) | Change | Max Displacement (in) | Change |
| :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 1 – Coarse | 2,804 | 4,818 | 0.169 / 0.506 | 2,096 | — | 0.000333 | — |
| 2 – Refinement 1 | 12,524 | 19,662 | 0.084 / 0.253 | 2,398 | +14.4% | 0.000344 | +3.2% |
| 3 – Refinement 2 | 77,155 | 113,462 | 0.042 / 0.126 | 3,196 | +33.3% | 0.000349 | +1.5% |
#### Optimization Pass:

____

<img width="657" height="546" alt="Screenshot 2026-11-12 065036" src="https://github.com/user-attachments/assets/6bb83e4c-2acb-4b8e-93dc-63301b56c781" />

<img width="1368" height="718" alt="image" src="https://github.com/user-attachments/assets/1fe0e58f-1afb-4de0-8794-0495a1700346" />


[Optimized crosshead]

#### Optimized Crosshead:

A pocket was cut through the web of the crosshead to reduce weight. The same fixtures, load and mesh convergence procedure were used.

##### Coarse Mesh (2,890 elements)

<img width="1235" height="635" alt="Screenshot 2026-11-12 070341" src="https://github.com/user-attachments/assets/5a31b879-4852-41ae-9653-f15b632543c4" />

[Coarse von Mises]

<img width="1305" height="662" alt="Screenshot 2026-11-12 070352" src="https://github.com/user-attachments/assets/88992767-dfd4-416e-9390-43af649edca7" />

[Coarse URES]

##### Mid Mesh (11,309 elements)

<img width="1235" height="740" alt="Screenshot 2026-11-12 070001" src="https://github.com/user-attachments/assets/4a22dff8-98de-4c30-945a-724171d273f7" />

[Mid von Mises]

<img width="1263" height="623" alt="Screenshot 2026-11-12 070013" src="https://github.com/user-attachments/assets/546410a9-5cdb-4ccd-9351-c120fdbd3e53" />

[Mid URES]

##### Fine Mesh (69,226 elements)

<img width="1258" height="747" alt="Screenshot 2026-11-12 065436" src="https://github.com/user-attachments/assets/fcadcef9-4836-430d-81e2-07aca1b47405" />

[Fine von Mises]

<img width="1283" height="747" alt="Screenshot 2026-11-12 065446" src="https://github.com/user-attachments/assets/6def4b78-76b0-48ac-8c58-60206848785f" />

[Fine URES]

##### Convergence Results

| Mesh | Elements | Nodes | Min / Max Element Size (in) | Max von Mises (psi) | Change | Max Displacement (in) | Change |
| :--- | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Coarse | 2,890 | 5,126 | 0.164 / 0.492 | 2,239 | — | 0.000389 | — |
| Mid | 11,309 | 18,336 | 0.082 / 0.246 | 2,527 | +12.9% | 0.000402 | +3.6% |
| Fine | 69,226 | 104,098 | 0.041 / 0.123 | 3,158 | +25.0% | 0.000412 | +2.3% |

The displacement converged, with the change dropping from 3.6% to 2.3%. As with the original crosshead, the peak stress moved to the sharp cylinder–crosshead edge on the fine mesh, a singularity that grows as the elements get smaller. The real peak stress is at the lead screw holes (2,527 psi).

| Result | Original | Optimized | Requirement | Pass? |
| :--- | :-: | :-: | :-: | :-: |
| Max von Mises (at lead screw holes) | 2,398 psi | 2,527 psi | ≤ 2,720 psi (Sy / 4) | Yes |
| Factor of safety | 4.54 | 4.31 | ≥ 4 | Yes |
| Max displacement | 0.000349 in (0.0089 mm) | 0.000412 in (0.0105 mm) | ≤ 0.1 mm | Yes |
| Volume | 16.17 in³ | 14.90 in³ | — | −7.9% |
| Mass | 1.58 lb | 1.46 lb | — | −7.9% |

The pocket cut mass by 7.9% (1.58 lb → 1.46 lb). Hole stress rose about 5% and deflection about 18%, but both still pass: FoS = 4.31 and deflection is about 10% of the 0.1 mm limit.

### 2157 Addition: Create a detailed drawing of the crosshead with a proper title block (20 pts): Ryan

SS

[Crosshead drawing]


## Decide


We decided that Misha would complete the hand calculation portion of this project, while Ryan would complete the 3D modelling and assembly sections. 



## Communicate


Lessons learned: 

To maximize efficiency and sanity, it is important to consider components that are most likely to fail, such as smaller fasteners. If I had considered how small the flange nut would have to be when using a 1/4"-16 lead screw, I would have instantly chosen a larger diameter screw and saved myself the trouble of all my extra calculations. - Misha

Time Spent
Misha: 10 hours
Ryan:
