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

### Step 3: Design 2 FEA and Alterations:

#### 1. Design Alterations:

After looking at my Design 1 results, I made two changes to the bracket. First, I tripled the thickness of feature B. Since feature B was taking all of the bending from the strap, making it thicker increases its moment of inertia, which lowers the bending stress. Stiffness goes up with thickness cubed, so tripling it makes feature B about 27 times stiffer. I set the extrude depth to the equation = 3 * "t B", so it's still linked to my global variable from A6, and I didn't have to redraw anything.

Second, I mirrored feature B to the other end of feature A. In Design 1, feature A was only held up on one side, which is why it acted like a cantilever. With a second feature B on the opposite end, feature A is now supported on both sides, and the strap load gets split between the two plates instead of one plate carrying everything. I kept all of my changes away from the T-beam slot, so the fits from A6 don't change, and the bracket can still slide on the beam.

<img width="875" height="367" alt="Design II – extrude depth set to 3 times t B" src="https://github.com/user-attachments/assets/b5baf5f0-c501-4c72-9f85-c6a6316f0e29" />

<img width="640" height="742" alt="Design II – mirror feature" src="https://github.com/user-attachments/assets/32f27564-2a16-40a0-b142-4fb581d6b8d2" />

#### 2. Design 2 FEA:

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

##### 4. Design 2 Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 1,863    | 3,606   | 27,320           | 0.006740            | 4.39          | —             | —                 |
| Standard | 8,989    | 15,529  | 39,430           | 0.006921            | 3.04          | 44.33%        | 2.69%             |
| Fine     | 68,130   | 104,910 | 56,150           | 0.006977            | 2.14          | 42.40%        | 0.81%             |

- **Max stress location:** sharp inside corner where feature B joins feature C
- **Max deflection location:** middle of feature A where the strap wraps
- **Min SF location:** same spot as max stress

Design 2 was a huge improvement over Design 1, but it still doesn't pass. The stress kept going up about 43% every time I refined the mesh, and it was always at the same sharp corner where feature B meets feature C. What surprised me is that the coarse mesh showed a safety factor of 4.39, which would have passed, but the fine mesh dropped it to 2.14. The max deflection of 0.006977 in is also over the 0.005 in target from A5. Features C, D, and E are still at low stress, so I again have some wiggle room to take material out of there.

### Step 4: Design 3 FEA and Alterations:

#### 1. Design Alterations:

After looking at my Design 2 results, I made three changes to the bracket. First, I brought the thickness of feature B on each side down from 3 times to 2 times `t B`. In Design 2, feature A is supported on both ends now, so each feature B only carries half of the strap load, and I didn't need it to be as thick as I made it. Dropping it to = 2 * "t B" takes weight off the bracket.

Second, I added a 1 in radius fillet between feature B and feature C. In Design 2, the stress kept piling up at that sharp corner no matter how fine I made the mesh. The fillet gets rid of the sharp corner and spreads the stress out over a curve instead of a single edge, which should help lower the max stress.

Third, I cut the height of feature E by 3/4 . In Design 2, features C, D, and E stayed at really low stress, so feature E had way more material than it needed. Halving it is an easy way to cut more weight without hurting the strength of the bracket. Again like before, I kept all of my changes away from the T-beam slot so the fits from A6 still hold.

#### 2. Design 3 FEA:

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

Design 3 converged, so I'm using the fine mesh results as my final values.

##### 4. Design 3 Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 2,366    | 4,675   | 28,770           | 0.004723            | 4.17          | —             | —                 |
| Standard | 9,647    | 17,219  | 29,690           | 0.004793            | 4.04          | 3.20%         | 1.48%             |
| Fine     | 123,525  | 189,889 | 29,830           | 0.004825            | 4.02          | 0.47%         | 0.67%             |

- **Max stress location:** on the 1 in fillet between feature B and feature C
- **Max deflection location:** feature A where the strap wraps
- **Min SF location:** same spot as max stress

Design 3 finally passes. The safety factor stays above 4 at every mesh level, and the max deflection of 0.004825 in is under my 0.005 in target from A5. The max stress is now on the smooth fillet instead of a sharp corner, so it stopped climbing every time I refined the mesh. Compared to Design II, the max stress dropped 47% and the deflection dropped 31%. What stood out to me is that feature B is actually thinner in Design III than in Design II, and the stress still went down. That shows how that sharp corner was causing problems.

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

One of the biggest things I learned is how much sharp corners mess with the FEA results. In Design 2, the stress went up about 43% every time I refined the mesh, and it was always at the same sharp corner is the analysis. Once I added the 1 in fillet in Design 3, the stress only changed by less than 1% between the standard and fine meshes. A sharp corner has zero radius, so there is nowhere for the stress to settle regardless of elements.

I also learned that adding material doesn't always work for different applications. In Design 3, I made feature B thinner than it was in Design 2, and the max stress still dropped 47% because the fillet was solving the actual problem. how the material is being shaped mean much more than the pure amount of material

A coarse mesh can also make a failing design look like it passes. Design 2's coarse mesh gave me a safety factor of 4.39, but the fine mesh dropped it to 2.14. If I had stopped at the coarse mesh, I would have thought Design 2 was done when it actually didn't meet the requirement.

How a part is supported matters as much as how thick it is. In Design 1, feature A was only held on one side like a cantilever. Supporting it on both ends in Design 2, along with thickening feature B, dropped the max stress by about 70 times on the coarse mesh for example.

FEA also showed me where my hand calculations were off. In A5, my stress and deflection calculations for feature B didn't match, and I couldn't figure out why. The Design 1 FEA showed feature B was the weakest part of the whole bracket, which confirmed my hand calc for feature B didn't match how it actually was going to be loaded.

### 2157 Extra
For the 2157 addition, I ran the same FEA process on the link I designed in A5 and A6. The link connects to feature A on the bracket and takes the full 1500 lbf from the strap, which is the total force I used in my A5 link calculations. Just like the bracket, I ran coarse, standard, and fine meshes on each design and checked that the results converged within 7% before making any changes.

#### Link Design Requirements (from A5 and A6)

- **Material:** Ti-6Al-4V, Material is not changed between designs.
- **Applied load:** 1500 lbf
- **Required safety factor:** 4 (allowable stress = 120,000 / 4 = 30,000 psi)
- **0.730 in hole:** RC6 fit onto feature A
- **1.000 in hole:** FN1 fit
- **Thickness:** driven by the global variable "T 1" from A6

#### Link Overall FEA Setup

<img width="667" height="766" alt="Screenshot 2026-10-22 032555" src="https://github.com/user-attachments/assets/28ba639e-95ee-4685-99a8-78840ecc3a32" />

I fixed the link at the small hole, and put the 1500 lbf load on the large hole. The fixture and load stay in the same spots for every link design and mesh below.

#### Link Design 1 FEA:

Design 1 is the link from A6 with no changes. FEA is run first to find where the stress and displacement maximums occur, so the next design can address them.

##### 1. Coarse Mesh FEA:
*1,377 elements, 2,638 nodes, element size 0.0934–0.1868 in*

<img width="955" height="757" alt="Screenshot 2026-10-22 034613" src="https://github.com/user-attachments/assets/88caf171-f767-4a89-9770-f7eca86fdc20" />

<img width="952" height="727" alt="Screenshot 2026-10-22 034605" src="https://github.com/user-attachments/assets/3276e063-dc16-46f0-bd41-709aa16206e2" />

<img width="943" height="731" alt="Screenshot 2026-10-22 034624" src="https://github.com/user-attachments/assets/c0c23e8d-066e-40bc-9369-f31bf7fb395a" />

##### 2. Standard Mesh FEA:
*8,249 elements, 13,675 nodes, element size 0.0934 in*

<img width="917" height="625" alt="Screenshot 2026-10-22 035945" src="https://github.com/user-attachments/assets/29d14cd2-cd41-4d16-ad37-5425534275f9" />

<img width="911" height="712" alt="Screenshot 2026-10-22 035951" src="https://github.com/user-attachments/assets/e75c3237-1ab1-4be6-8f1f-de0d65aabc22" />

<img width="835" height="597" alt="Screenshot 2026-10-22 040004" src="https://github.com/user-attachments/assets/998eff56-989c-4b06-bfdc-4461d7c91093" />

A fine mesh isn't required because the coarse vs. standard stress difference is already under 7%:

Percent Difference = |(45,040 − 43,370) / 43,370| × 100% = |1,670 / 43,370| × 100% = **3.85%**

Link Design 1 converged, so I'm using the standard mesh results as my final values.

##### 3. Link Design 1 Results:

| Mesh     | Elements | Nodes  | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|--------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 1,377    | 2,638  | 43,370           | 0.003467            | 2.77          | —             | —                 |
| Standard | 8,249    | 13,675 | 45,040           | 0.003509            | 2.66          | 3.85%         | 1.21%             |

- **Max stress location:** sides of the large hole, where the load is applied
- **Max deflection location:** bottom edge of the large hole
- **Min SF location:** same spot as max stress

Link Design 1 converged, but it doesn't pass. The safety factor is 2.66, which is under the 4 I need. The max stress is at the sides of the large hole where the load goes in, while the middle of the link and the area around the small hole stay at pretty low stress. The max deflection is 0.003509 in, so it's already under the 0.005 in target, which means stiffness isn't really the problem here, it's the strength around the large hole.

In A5, I sized the link with σ = F/A, which assumes the stress is spread out evenly across the whole cross-section. The FEA showed the max stress right at the sides of the large hole, because the hole concentrates the stress around its edges. That's why my link passed on paper but only got a safety factor of 2.66 in FEA.

#### Link Design 2 FEA and Alterations:

##### 1. Design Alterations:

TBD – what I changed from link Design 1 and why.

<img width="1030" height="882" alt="Screenshot 2026-10-22 040803" src="https://github.com/user-attachments/assets/5309d652-d5a8-4e35-9248-6329ff37f5b4" />

##### 2. Link Design 2 FEA:

###### 1. Coarse Mesh FEA:
*1,467 elements, 2,788 nodes, element size 0.0990–0.1981 in*

<img width="1023" height="813" alt="Screenshot 2026-10-22 040958" src="https://github.com/user-attachments/assets/9cc8e118-d15a-44f3-8222-9503d32b1045" />

<img width="1192" height="826" alt="Screenshot 2026-10-22 041017" src="https://github.com/user-attachments/assets/bbefa61a-da3b-4660-9bf1-e19b986a2a42" />

<img width="875" height="775" alt="Screenshot 2026-10-22 041030" src="https://github.com/user-attachments/assets/fca97f34-d185-4919-ba2e-cfeea9fdc086" />

###### 2. Standard Mesh FEA:
*8,973 elements, 14,794 nodes, element size 0.0990 in*

<img width="940" height="702" alt="Screenshot 2026-10-22 041302" src="https://github.com/user-attachments/assets/3a5a4289-7fe1-475e-870a-8f77baaf152a" />

<img width="931" height="636" alt="Screenshot 2026-10-22 041308" src="https://github.com/user-attachments/assets/0b85f756-d171-4727-b166-0ec8abc1bacc" />

<img width="917" height="648" alt="Screenshot 2026-10-22 041314" src="https://github.com/user-attachments/assets/7afb0ce2-1c8b-4672-a304-f21a66a86a77" />

I had to run a fine mesh because the stress difference between coarse and standard was way over 7%:

Percent Difference = |(39,330 − 30,380) / 30,380| × 100% = |8,950 / 30,380| × 100% = **29.46%**

###### 3. Fine Mesh FEA:
*69,238 elements, 103,293 nodes, element size 0.0495 in*

<img width="1077" height="692" alt="Screenshot 2026-10-22 041643" src="https://github.com/user-attachments/assets/b7da9193-aa8e-4445-8adb-3cefb1b95541" />

<img width="1057" height="656" alt="Screenshot 2026-10-22 041650" src="https://github.com/user-attachments/assets/78da4a45-05a9-47b0-8b9a-6405bf516ed5" />

<img width="1002" height="662" alt="Screenshot 2026-10-22 041704" src="https://github.com/user-attachments/assets/b8593150-516f-4c48-bc62-9315cd1ccf11" />

The stress between standard and fine was still over 7%:

Percent Difference = |(58,600 − 39,330) / 39,330| × 100% = |19,270 / 39,330| × 100% = **48.99%**

The deflection converged (1.07%, then 0.49%), but the stress didn't. Since this was my third attempt, I used the fine mesh results for link Design II like the assignment says.

###### 4. Link Design 2 Results:

| Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|---------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 1,467    | 2,788   | 30,380           | 0.002234            | 3.95          | —             | —                 |
| Standard | 8,973    | 14,794  | 39,330           | 0.002258            | 3.05          | 29.46%        | 1.07%             |
| Fine     | 69,238   | 103,293 | 58,600           | 0.002269            | 2.05          | 48.99%        | 0.49%             |

- **Max stress location:** sides of the large hole on the coarse mesh and moved to the edge of the small hole at the fixture on the standard and fine meshes
- **Max deflection location:** bottom edge of the large hole
- **Min SF location:** same spot as max stress

Link Design 2 made the link stiffer, the max deflection went from 0.003509 in down to 0.002269 in, but it still doesn't pass. On the coarse mesh the safety factor was 3.95, which was really close to 4, but once I refined the mesh the max stress moved to the edge of the small hole right where the fixture is, and it kept climbing every time. This is basically the same thing as the sharp corner on my bracket. A fixed restraint on a sharp edge is perfectly rigid, which doesn't happen in real life, so the stress there has nowhere to settle. The deflection only changed 0.49% between standard and fine, so the stiffness results are solid, but the safety factor of 2.05 is still under 4. The mass also went up from 0.13 lb to 0.16 lb.

#### Link Design 3 FEA and Alterations:

##### 1. Design Alterations:

After looking at my link Design 2 results, I made two changes. First, I doubled the thickness of the link. In Design 2, the safety factor dropped to 2.05 on the fine mesh, and the stress around both holes was way too high for the 1500 lbf load. Doubling the thickness gives the load twice as much material to spread through around each hole, which lowers the stress, and it also makes the link a lot stiffer.

Second, I added fillets to the outside edges of the link with a radius of 1/4 of the original link thickness ("T 1" / 4). The fillets take off the sharp outer edges, which cuts down some of the weight added by doubling the thickness and gets rid of sharp corners where stress could build up. Just like the bracket, I kept both hole diameters the same so the RC6 and FN1 fits from A5 still work.

##### 2. Link Design 3 FEA:

###### 1. Coarse Mesh FEA:
*6,596 elements, 10,859 nodes, element size 0.0427–0.2884 in*

<img width="1067" height="766" alt="Screenshot 2026-10-22 043508" src="https://github.com/user-attachments/assets/b72b1d03-45c7-407a-8925-00db50eabb21" />

<img width="1051" height="797" alt="Screenshot 2026-10-22 043514" src="https://github.com/user-attachments/assets/21c0c6d1-6a3f-4697-a4d1-444d4642840a" />

<img width="1030" height="728" alt="Screenshot 2026-10-22 043523" src="https://github.com/user-attachments/assets/9b987058-801d-40db-949c-95cc330992dd" />

###### 2. Standard Mesh FEA:
*11,466 elements, 17,966 nodes, element size 0.0418–0.1255 in*

<img width="1035" height="747" alt="Screenshot 2026-10-22 043803" src="https://github.com/user-attachments/assets/5b164d96-5fb2-4db8-9f00-0835f3d50f34" />

<img width="970" height="753" alt="Screenshot 2026-10-22 043814" src="https://github.com/user-attachments/assets/6a22712b-de60-424f-ba4d-045c822112bb" />

<img width="922" height="767" alt="Screenshot 2026-10-22 043822" src="https://github.com/user-attachments/assets/117fd059-1cd9-40ac-b57e-2b2234da8a13" />

I had to run a fine mesh because the stress difference between coarse and standard was over 7%:

Percent Difference = |(18,030 − 15,600) / 15,600| × 100% = |2,430 / 15,600| × 100% = **15.58%**

###### 3. Fine Mesh FEA:
*61,801 elements, 90,348 nodes, element size 0.0209–0.0628 in*

<img width="1008" height="763" alt="Screenshot 2026-10-22 044014" src="https://github.com/user-attachments/assets/1ec8922a-a312-466d-87f0-b85400155425" />

<img width="867" height="751" alt="Screenshot 2026-10-22 044027" src="https://github.com/user-attachments/assets/89611ba5-060a-4300-9faa-86ce5dec7445" />

<img width="957" height="780" alt="Screenshot 2026-10-22 044035" src="https://github.com/user-attachments/assets/2e5e888d-c7c9-429c-8763-e876a763c747" />

The stress between standard and fine was still over 7%:

Percent Difference = |(28,340 − 18,030) / 18,030| × 100% = |10,310 / 18,030| × 100% = **57.18%**

The deflection converged (0.86%, then 0.43%), but the stress didn't. Since this was my third attempt, I used the fine mesh results for link Design 3 like the assignment says.

###### 4. Link Design III Results:

| Mesh     | Elements | Nodes  | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Diff Stress | % Diff Deflection |
|----------|----------|--------|------------------|---------------------|---------------|---------------|-------------------|
| Coarse   | 6,596    | 10,859 | 15,600           | 0.001166            | 7.69          | —             | —                 |
| Standard | 11,466   | 17,966 | 18,030           | 0.001176            | 6.65          | 15.58%        | 0.86%             |
| Fine     | 61,801   | 90,348 | 28,340           | 0.001181            | 4.23          | 57.18%        | 0.43%             |

- **Max stress location:** inside surface of the large hole on the coarse mesh and moved to the inside surface of the small hole at the fixture on the standard and fine meshes
- **Max deflection location:** bottom edge of the large hole
- **Min SF location:** same spot as max stress

Link Design 3 finally passes. Even on the fine mesh, the safety factor is 4.23, which is above the 4 I need, and the max deflection of 0.001181 in is way under the 0.005 in target. The stress kept climbing at the fixture on the small hole every time I refined the mesh, just like in Design 2, but even with that the link still stays above a safety factor of 4. The deflection only changed 0.43% between standard and fine, so the stiffness results are solid. Compared to Design 2, the max stress dropped 52% and the deflection dropped 48%.

#### Link Final Design Iteration Table and Lessons Learned

##### 1. Link Design Table:

|                              | Design 1                          | Design 2                              | Design 3                         |
|------------------------------|-----------------------------------|----------------------------------------|------------------------------------|
| Max Stress and location      | 45,040 psi, sides of large hole   | 58,600 psi, small hole edge at fixture | 28,340 psi, small hole at fixture  |
| Max deflection and location  | 0.003509 in, bottom of large hole | 0.002269 in, bottom of large hole      | 0.001181 in, bottom of large hole  |
| Mass                         | 0.13 lb                           | 0.16 lb                                | 0.32                               |
| Safety Factor                | 2.66                              | 2.05                                   | 4.23                               |
| Number of elements           | 8,249                             | 69,238                                 | 61,801                             |

##### 2. Link Lessons Learned:

The biggest thing I learned from the link is that my hand calc from A5 were super far off and i mentioned this in A6 about my A5 work having to do the FEA on the parts makes it easy to verify any possible errors you made in your calculations along with the parametric equations.

Thickness made the biggest difference on the link. Doubling it in Design 3 took the safety factor from 2.05 up to 4.23 and cut the deflection almost in half. Since the thickness was linked to "T 1" from A6, I only had to change one value to update the whole link.

## Decide:

For Designs 1 and 2, the stress never converged within three attempts, so I used the fine mesh results like the assignment says. For Design 2, I figured out that the stress wasn't converging because of one of the corners, not because I set something up wrong which I had initially assumed, and that pointed me straight to the fix for Design 3 for the bracket.

I also again kept all of my changes away from the T-beam slot, so the RC fits from A6 still hold and the bracket can still slide on the beam.

### Mistakes

One mistake that carried over from A5 was feature B being undersized. My stress and deflection calculations for feature B didn't agree, and I let it ride instead of figuring out why. The Design 1 FEA showed feature B failing with a safety factor of 0.0203, so that unresolved calculation ended up in my CAD model.

### Time Spent

This assignment took me around 8 Hours to complete from start to finish

## Appendix

[A7 Parts Folder](https://drive.google.com/drive/folders/1YrD_X1NY8J8nvU5k1vPIMKFW72U5bTFp?usp=sharing)
