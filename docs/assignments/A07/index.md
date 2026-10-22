# A7 – FEA on Bracket

## Objective:

- Use Finite Element Analysis (FEA) to improve the bracket design from previous assignments.
- Ensure high stiffness, strength, and lightweight optimization through iterative design.
- Conduct multiple FEA simulations, refining geometry based on results.
- Perform static stress analysis, including constraints, loading, and meshing selection.
- Interpret data by identifying max stress, displacement, and safety factors.
- Optimize the design by modifying geometry to enhance performance.
- Document the entire process with images, calculations, and insights.
- Reflect on key engineering lessons learned and time spent.

For Assignment A7, I am continuing the bracket design from A5 and A6. In A5, I sized each feature of the bracket with hand calculations for stress and deflection, and in A6, I built a parametric SolidWorks model where every dimension is driven by global variables from those calculations. In this assignment, I use FEA to check that design and improve it through three design iterations, making it stronger, stiffer, and lighter each time.

### Design Requirements (from A5)

- **Material:** Ti-6Al-4V, Material is not changed between designs.
- **Applied load:** 750 lbf
- **Required safety factor:** 4 (allowable stress = 120,000 / 4 = 30,000 psi)
- **Maximum deflection target:** 0.005 in (from the A5 deflection analysis)
- **Software:** SOLIDWORKS Simulation, static study, blended curvature-based solid mesh (high quality, 16 Jacobian points)

## Analyze and Optimize: Bracket:

### Overall FEA Setup

<img width="470" height="547" alt="Screenshot 2026-10-21 235017" src="https://github.com/user-attachments/assets/9422e5b8-112c-4f8e-922f-0f1f7e784169" />


### Step 2: Design 1 FEA:

Design 1 is the parametric model from A6 with no changes. FEA is run first to find where the stress and displacement maximums occur, so the next design can address them.

#### 1. Coarse Mesh FEA:
*1,643 elements, 3,220 nodes, element size 0.1589–0.3026 in*

<img width="1160" height="682" alt="Design 1 coarse – von Mises stress" src="https://github.com/user-attachments/assets/f42bc376-9775-4ede-aa16-3d7ee5fd0bbe" />


<img width="1146" height="682" alt="Design 1 coarse – displacement" src="https://github.com/user-attachments/assets/79d9dd2f-ff2d-46d4-a37c-f1348b24c3e6" />


<img width="1087" height="665" alt="Design 1 coarse – factor of safety" src="https://github.com/user-attachments/assets/db51a228-bd37-4e35-91a4-2b2c5991bd39" />


#### 2. Standard Mesh FEA:
*7,146 elements, 12,478 nodes, element size 0.1702 in*

<img width="1027" height="700" alt="Design 1 standard – von Mises stress" src="https://github.com/user-attachments/assets/832c79b5-62d3-4ea8-a6ce-069c193bfd46" />


<img width="1017" height="712" alt="Design 1 standard – displacement" src="https://github.com/user-attachments/assets/6edc0eb0-d264-445d-a007-78258faeb9fa" />


<img width="1032" height="692" alt="Design 1 standard – factor of safety" src="https://github.com/user-attachments/assets/c232b7a3-a8d3-4e5d-bbd9-833b177f8bef" />


#### 3. Fine Mesh FEA:
*68,990 elements, 106,118 nodes, element size 0.0757 in*

A fine mesh is required because the coarse vs. standard stress difference is larger than 7%:

Percent Difference = |(4,801,000 − 1,941,000) / 1,941,000| × 100% = |2,860,000 / 1,941,000| × 100% = **147.35%**

<img width="1061" height="722" alt="Design 1 fine – von Mises stress" src="https://github.com/user-attachments/assets/5722ae1d-52e0-4a6e-afb7-fd984090d431" />


<img width="1088" height="746" alt="Design 1 fine – displacement" src="https://github.com/user-attachments/assets/6dbdc595-e3af-4317-8989-523868646144" />


<img width="1086" height="685" alt="Design 1 fine – factor of safety" src="https://github.com/user-attachments/assets/69330485-1c39-4008-8d38-04cb4d6776c7" />


The standard vs. fine stress difference is still above 7%:

Percent Difference = |(5,898,000 − 4,801,000) / 4,801,000| × 100% = |1,097,000 / 4,801,000| × 100% = **22.85%**

This is the third attempt, so per the assignment the fine mesh results are used for Design 1.

#### 4. Design 1 Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 1,643    | 3,220   | 1,941,000        | 3.111               | 0.0618        | —             | —                 |
| Standard | 7,146    | 12,478  | 4,801,000        | 7.673               | 0.0250        | 147.35%       | 146.64%           |
| Fine     | 68,990   | 106,118 | 5,898,000        | 9.082               | 0.0203        | 22.85%        | 18.36%            |

- **Max stress location:** middle of feature B on the coarse and standard meshes and moved to the sharp corner where feature B meets feature A on the fine mesh
- **Max deflection location:** free end of feature A
- **Min SF location:** same spot as max stress

From my FEA simulations, design 1 fails at every mesh level. The safety factor is around 0.02, and Max stress is about 49 times the yield strength. Feature B attaches to only one end of feature A, so feature A hangs off feature B like a cantilever, and the strap is fully supported by A. So, for this design, all the forces are being loaded through feature B and not the rest of the features, like C, D, and E, which have near-zero stress

### Step 3: Design II FEA and Alterations:

#### 1. Design Alterations:

After looking at my Design 1 results, I made two changes to the bracket. First, I tripled the thickness of feature B. Since feature B was taking all of the bending from the strap, making it thicker increases its moment of inertia, which lowers the bending stress. Stiffness goes up with thickness cubed, so tripling it makes feature B about 27 times stiffer. I set the extrude depth to the equation = 3 * "t B", so it's still linked to my global variable from A6, and I didn't have to redraw anything.

Second, I mirrored feature B to the other end of feature A. In Design 1, feature A was only held up on one side, which is why it acted like a cantilever. With a second feature B on the opposite end, feature A is now supported on both sides, and the strap load gets split between the two plates instead of one plate carrying everything. I kept all of my changes away from the T-beam slot, so the fits from A6 don't change, and the bracket can still slide on the beam.

<img width="875" height="367" alt="Design II – extrude depth set to 3 times t B" src="https://github.com/user-attachments/assets/b5baf5f0-c501-4c72-9f85-c6a6316f0e29" />

<img width="640" height="742" alt="Design II – mirror feature" src="https://github.com/user-attachments/assets/32f27564-2a16-40a0-b142-4fb581d6b8d2" />

#### 2. Design II FEA:

##### 1. Coarse Mesh FEA:
*1,863 elements, 3,606 nodes, element size 0.1531–0.2986 in*

<img width="1307" height="760" alt="Design II coarse – von Mises stress" src="https://github.com/user-attachments/assets/32d62369-e216-4b67-ac35-01480dd84297" />

<img width="1242" height="782" alt="Design II coarse – displacement" src="https://github.com/user-attachments/assets/e21d67ee-58de-4ac8-b3f8-9d95bccd753e" />

<img width="1197" height="777" alt="Design II coarse – factor of safety" src="https://github.com/user-attachments/assets/d8f54aff-2342-4581-a384-4f1d5b1e4764" />

##### 2. Standard Mesh FEA:
*8,989 elements, 15,529 nodes, element size 0.1569 in*

<img width="1112" height="737" alt="Design II standard – von Mises stress" src="https://github.com/user-attachments/assets/278a8ad8-b0fd-49f5-bf1c-e180d79c78ef" />

<img width="1190" height="758" alt="Design II standard – displacement" src="https://github.com/user-attachments/assets/956a6e32-d257-454e-9dc4-2c6e0144cdb8" />

<img width="965" height="687" alt="Design II standard – factor of safety" src="https://github.com/user-attachments/assets/bcba91ce-ac58-4aae-b393-506013ef2765" />

##### 3. Fine Mesh FEA:
*68,130 elements, 104,910 nodes, element size 0.0766 in*

I had to run a fine mesh because the stress difference between coarse and standard was way over 7%:

Percent Difference = |(39,430 − 27,320) / 27,320| × 100% = |12,110 / 27,320| × 100% = **44.33%**

<img width="1066" height="722" alt="Design II fine – von Mises stress" src="https://github.com/user-attachments/assets/51eb318e-d7af-47bd-b6e0-f6e607ec0ed5" />

<img width="1021" height="721" alt="Design II fine – displacement" src="https://github.com/user-attachments/assets/a8646ecc-e803-4c61-b4aa-c12bf840c6d9" />

<img width="1056" height="677" alt="Design II fine – factor of safety" src="https://github.com/user-attachments/assets/9574ed07-3943-4dec-93f1-08487c4d3d64" />

The stress between standard and fine was still over 7%:

Percent Difference = |(56,150 − 39,430) / 39,430| × 100% = |16,720 / 39,430| × 100% = **42.40%**

The deflection did converge 2.69%, then 0.81%, but the stress didn't. Since this was my third attempt, I used the fine mesh results for Design II like the assignment says again.

##### 4. Design II Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 1,863    | 3,606   | 27,320           | 0.006740            | 4.39          | —             | —                 |
| Standard | 8,989    | 15,529  | 39,430           | 0.006921            | 3.04          | 44.33%        | 2.69%             |
| Fine     | 68,130   | 104,910 | 56,150           | 0.006977            | 2.14          | 42.40%        | 0.81%             |

- **Max stress location:** sharp inside corner where feature B joins feature C
- **Max deflection location:** middle of feature A where the strap wraps
- **Min SF location:** same spot as max stress

Design II was a huge improvement over Design 1, but it still doesn't pass. The stress kept going up about 43% every time I refined the mesh, and it was always at the same sharp corner where feature B meets feature C. What surprised me is that the coarse mesh showed a safety factor of 4.39, which would have passed, but the fine mesh dropped it to 2.14. The max deflection of 0.006977 in is also over the 0.005 in target from A5. Features C, D, and E are still at low stress, so I again have some wiggle room to take material out of there.

### Step 4: Design III FEA and Alterations:

#### 1. Design Alterations:

After looking at my Design II results, I made three changes to the bracket. First, I brought the thickness of feature B on each side down from 3 times to 2 times `t B`. In Design II, feature A is supported on both ends now, so each feature B only carries half of the strap load, and I didn't need it to be as thick as I made it. Dropping it to = 2 * "t B" takes weight off the bracket.

Second, I added a 1 in radius fillet between feature B and feature C. In Design II, the stress kept piling up at that sharp corner no matter how fine I made the mesh. The fillet gets rid of the sharp corner and spreads the stress out over a curve instead of a single edge, which should help lower the max stress.

Third, I cut the height of feature E by 3/4 . In Design II, features C, D, and E stayed at really low stress, so feature E had way more material than it needed. Halving it is an easy way to cut more weight without hurting the strength of the bracket. Again like before, I kept all of my changes away from the T-beam slot so the fits from A6 still hold.

#### 2. Design III FEA:

##### 1. Coarse Mesh FEA:
*2,366 elements, 4,675 nodes, element size 0.1372–0.2538 in*

<img width="1020" height="717" alt="Design III coarse – von Mises stress" src="https://github.com/user-attachments/assets/3a3b62e5-60d9-4291-bf22-64d29a3498f4" />

<img width="1040" height="672" alt="Design III coarse – displacement" src="https://github.com/user-attachments/assets/43cfcf80-7764-4ed7-97fd-a743c866ab06" />

<img width="1040" height="737" alt="Design III coarse – factor of safety" src="https://github.com/user-attachments/assets/3c1cb6fd-d9c8-41de-96a8-55b684a1fd79" />

##### 2. Standard Mesh FEA:
*9,647 elements, 17,219 nodes, element size 0.1372 in*

<img width="1085" height="642" alt="Design III standard – von Mises stress" src="https://github.com/user-attachments/assets/24d540c5-fbcc-4f85-bf05-8d1c474f673d" />

<img width="1006" height="647" alt="Design III standard – displacement" src="https://github.com/user-attachments/assets/b39159d3-c87a-4114-bdad-ac92e6384e2d" />

<img width="1031" height="653" alt="Design III standard – factor of safety" src="https://github.com/user-attachments/assets/19718f8f-5e81-4eed-bbc6-c5b8450cd82b" />

##### 3. Fine Mesh FEA:
*123,525 elements, 189,889 nodes, element size 0.0549 in*

The coarse vs. standard stress difference was already under 7%:

Percent Difference = |(29,690 − 28,770) / 28,770| × 100% = |920 / 28,770| × 100% = **3.20%**

I still ran a fine mesh just to make sure the results held up:

<img width="1227" height="697" alt="Design III fine – von Mises stress" src="https://github.com/user-attachments/assets/45fd916d-d318-4090-b1ad-4cc0c54d1d02" />

<img width="1005" height="662" alt="Design III fine – displacement" src="https://github.com/user-attachments/assets/92974975-6eb7-4c8b-959d-ceb5b28f0b5e" />

<img width="1076" height="687" alt="Design III fine – factor of safety" src="https://github.com/user-attachments/assets/e663c9f0-c080-40fb-9fd3-31c7c2ee9761" />

Percent Difference = |(29,830 − 29,690) / 29,690| × 100% = |140 / 29,690| × 100% = **0.47%**

Design III converged, so I'm using the fine mesh results as my final values.

##### 4. Design III Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 2,366    | 4,675   | 28,770           | 0.004723            | 4.17          | —             | —                 |
| Standard | 9,647    | 17,219  | 29,690           | 0.004793            | 4.04          | 3.20%         | 1.48%             |
| Fine     | 123,525  | 189,889 | 29,830           | 0.004825            | 4.02          | 0.47%         | 0.67%             |

- **Max stress location:** on the 1 in fillet between feature B and feature C
- **Max deflection location:** feature A where the strap wraps
- **Min SF location:** same spot as max stress

Design III finally passes. The safety factor stays above 4 at every mesh level, and the max deflection of 0.004825 in is under my 0.005 in target from A5. The max stress is now on the smooth fillet instead of a sharp corner, so it stopped climbing every time I refined the mesh. Compared to Design II, the max stress dropped 47% and the deflection dropped 31%. What stood out to me is that feature B is actually thinner in Design III than in Design II, and the stress still went down. That shows how that sharp corner was causing problems.

### Step 5: Final Design Iteration Table and Lessons Learned

#### 1. Design Table:

|                              | Design 1                                  | Design II                                 | Design III                               |
|------------------------------|-------------------------------------------|-------------------------------------------|------------------------------------------|
| Max Stress and location      | 5,898,000 psi, feature B–feature A corner | 56,150 psi, feature B–feature C corner    | 29,830 psi, feature B–feature C fillet   |
| Max deflection and location  | 9.082 in, free end of feature A           | 0.006977 in, middle of feature A          | 0.004825 in, feature A                   |
| Mass                         | 0.55 lb                                   | 0.57 lb                                   | 0.41 lb                                  |
| Safety Factor                | 0.0203                                    | 2.14                                      | 4.02                                     |
| Number of elements           | 68,990                                    | 68,130                                    | 123,525                                  |

#### 2. Lessons Learned:

One of the biggest things I learned is how much sharp corners mess with the FEA results. In Design II, the stress went up about 43% every time I refined the mesh, and it was always at the same sharp corner is the analysis. Once I added the 1 in fillet in Design III, the stress only changed by less than 1% between the standard and fine meshes. A sharp corner has zero radius, so there is nowhere for the stress to settle regardless of elements.

I also learned that adding material doesn't always work for different applications. In Design III, I made feature B thinner than it was in Design II, and the max stress still dropped 47% because the fillet was solving the actual problem. how the material is being shaped mean much more than the pure amount of material

A coarse mesh can also make a failing design look like it passes. Design II's coarse mesh gave me a safety factor of 4.39, but the fine mesh dropped it to 2.14. If I had stopped at the coarse mesh, I would have thought Design II was done when it actually didn't meet the requirement.

How a part is supported matters as much as how thick it is. In Design 1, feature A was only held on one side like a cantilever. Supporting it on both ends in Design II, along with thickening feature B, dropped the max stress by about 70 times on the coarse mesh for example.

FEA also showed me where my hand calculations were off. In A5, my stress and deflection calculations for feature B didn't match, and I couldn't figure out why. The Design 1 FEA showed feature B was the weakest part of the whole bracket, which confirmed my hand calc for feature B didn't match how it actually was going to be loaded.

## Decide:

For Designs 1 and II, the stress never converged within three attempts, so I used the fine mesh results like the assignment says. For Design II, I figured out that the stress wasn't converging because of the sharp corner, not because I set something up wrong, and that pointed me straight to the fix for Design III.

I also kept all of my changes away from the T-beam slot, so the RC fits from A6 still hold and the bracket can still slide on the beam.

## Communicate:

### Reflections

TBD – your own reflection on the assignment. The instructions say to be specific and avoid words like "good" and "bad."

### Mistakes

One mistake that carried over from A5 was feature B being undersized. My stress and deflection calculations for feature B didn't agree, and I let it ride instead of figuring out why. The Design 1 FEA showed feature B failing with a safety factor of 0.0203, so that unresolved calculation ended up in my CAD model.

TBD – any other mistakes.

### Time Spent

This assignment took me about TBD hours from start to finish.

## Appendix

[A7 Downloads Folder](TBD – link)
