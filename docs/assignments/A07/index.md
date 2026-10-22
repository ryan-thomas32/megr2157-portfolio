# A7 – FEA

## Objective
The assignment for this week is running FEA (finite element analysis) on the bracket I have been designing the past two assignments. We must run a minimum of three simulations, and record what design changes are made to the bracket between each simulation. The goal is a bracket that is stiffer, stronger, and lighter than the previous version, using FEA results to drive each geometry change.

### Process
The work follows two loops:
- **Inner loop (validation):** run a static stress analysis, then refine the mesh until max stress, displacement, and safety factor converge within **7%**. If they haven't converged after three attempts, use the finest mesh results and move on.
- **Outer loop (design optimization):** use the converged results to add or remove material, then repeat the inner loop on the new geometry. This is done a minimum of three times (Design 1, II, III).

### CAD Download
[Download CAD files](TBD – link)

## Analyze

### Preprocessing (same for all designs)
- **Software:** SOLIDWORKS Simulation, static study
- **Material:** Ti-6Al-4V, solution treated and aged (yield strength 1.200e5 psi; material not changed between designs)
- **Design load:** TBD lbf (allowed range 500–800 lbf), applied symmetrically by the polyester strap
- **Required safety factor:** 4 (allowable stress = 120,000 / 4 = 30,000 psi)
- **Fixtures:** TBD – faces where the bracket attaches to the rigid T beam
- **Mesh:** blended curvature-based solid mesh, high quality (16 Jacobian points)

TBD – screenshot of fixtures and loads

### Design 1

#### Attempt 1 – Coarse Mesh
*1,643 elements · 3,220 nodes · element size 0.1589–0.3026 in*

**Von Mises Stress**
<img width="1160" height="682" alt="Design 1 coarse – von Mises stress" src="https://github.com/user-attachments/assets/f42bc376-9775-4ede-aa16-3d7ee5fd0bbe" />

**Displacement (URES)**
<img width="1146" height="682" alt="Design 1 coarse – displacement" src="https://github.com/user-attachments/assets/79d9dd2f-ff2d-46d4-a37c-f1348b24c3e6" />

**Factor of Safety**
<img width="1087" height="665" alt="Design 1 coarse – factor of safety" src="https://github.com/user-attachments/assets/db51a228-bd37-4e35-91a4-2b2c5991bd39" />

#### Attempt 2 – Standard Mesh
*7,146 elements · 12,478 nodes · element size 0.1702 in*

**Von Mises Stress**
<img width="1027" height="700" alt="Design 1 standard – von Mises stress" src="https://github.com/user-attachments/assets/832c79b5-62d3-4ea8-a6ce-069c193bfd46" />

**Displacement (URES)**
<img width="1017" height="712" alt="Design 1 standard – displacement" src="https://github.com/user-attachments/assets/6edc0eb0-d264-445d-a007-78258faeb9fa" />

**Factor of Safety**
<img width="1032" height="692" alt="Design 1 standard – factor of safety" src="https://github.com/user-attachments/assets/c232b7a3-a8d3-4e5d-bbd9-833b177f8bef" />

#### Attempt 3 – Fine Mesh
*68,990 elements · 106,118 nodes · element size 0.0757 in*

**Von Mises Stress**
<img width="1061" height="722" alt="Design 1 fine – von Mises stress" src="https://github.com/user-attachments/assets/5722ae1d-52e0-4a6e-afb7-fd984090d431" />

**Displacement (URES)**
<img width="1088" height="746" alt="Design 1 fine – displacement" src="https://github.com/user-attachments/assets/6dbdc595-e3af-4317-8989-523868646144" />

**Factor of Safety**
<img width="1086" height="685" alt="Design 1 fine – factor of safety" src="https://github.com/user-attachments/assets/69330485-1c39-4008-8d38-04cb4d6776c7" />

#### Design 1 – Convergence

| Attempt | Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Change in Stress | % Change in Deflection |
|---------|----------|----------|---------|------------------|---------------------|---------------|--------------------|------------------------|
| 1       | Coarse   | 1,643    | 3,220   | 1.941e6          | 3.111               | 0.0618        | —                  | —                      |
| 2       | Standard | 7,146    | 12,478  | 4.801e6          | 7.673               | 0.0250        | +147.3%            | +146.6%                |
| 3       | Fine     | 68,990   | 106,118 | 5.898e6          | 9.082               | 0.0203        | +22.8%             | +18.4%                 |

- **Max stress location:** mid-neck in Attempts 1–2; moved to the sharp corner where the neck meets the cylinder in Attempt 3
- **Max deflection location:** free end of the cylinder
- **Min FOS location:** same spot as max stress

**Result:** The changes between attempts dropped from about 147% to about 20%, but did not reach the 7% target within three attempts. Per the assignment, the fine mesh results (Attempt 3) are used for Design 1.

**Interpretation:** Design 1 fails at every mesh level, with a safety factor of 0.0203 (max stress is about 49 times the yield strength). Almost all of the stress is concentrated in the thin neck between the frame and the cylinder, while the frame itself stays near zero stress. The frame has material to spare, and the neck needs more.

#### Changes for Design II
Design 1 failed with a minimum safety factor of 0.0203, and nearly all of the stress was concentrated in one thin section while the rest of the bracket stayed close to zero stress. Two geometry changes were made to address this:

1. **Tripled the thickness of feature b.** The thin section was carrying the full strap load in bending, so increasing its thickness raises its moment of inertia and lowers the bending stress. Because bending stiffness scales with thickness cubed, tripling the thickness increases that section's stiffness by roughly 27 times, which directly reduces deflection. The extrude depth was set with the equation `= 3 * "t B"`, so it stays linked to the original thickness variable and updates automatically if `t B` changes.

<img width="875" height="367" alt="Design II – extrude depth set to 3 times t B" src="https://github.com/user-attachments/assets/b5baf5f0-c501-4c72-9f85-c6a6316f0e29" />

*Extrude feature with depth driven by the equation 3 × t B*

2. **Mirrored the geometry across feature a.** Design 1 supported the load from one side only, which put the whole bracket in an offset, unbalanced load path. Mirroring it makes the bracket symmetric, so the strap load is split evenly between both sides instead of being carried by one. This also matches the assignment's note that a symmetric design reduces the analysis work.

<img width="640" height="742" alt="Design II – mirror feature" src="https://github.com/user-attachments/assets/32f27564-2a16-40a0-b142-4fb581d6b8d2" />

*Mirror feature making the bracket symmetric*

**Effect (coarse mesh):** max stress dropped from 1.941e6 psi to 2.732e4 psi, max deflection dropped from 3.111 in to 6.740e-3 in, and the minimum safety factor rose from 0.0618 to 4.39.

### Design II

#### Attempt 1 – Coarse Mesh
*1,863 elements · 3,606 nodes · element size 0.1531–0.2986 in*

**Von Mises Stress**
<img width="1307" height="760" alt="Design II coarse – von Mises stress" src="https://github.com/user-attachments/assets/32d62369-e216-4b67-ac35-01480dd84297" />

**Displacement (URES)**
<img width="1242" height="782" alt="Design II coarse – displacement" src="https://github.com/user-attachments/assets/e21d67ee-58de-4ac8-b3f8-9d95bccd753e" />

**Factor of Safety**
<img width="1197" height="777" alt="Design II coarse – factor of safety" src="https://github.com/user-attachments/assets/d8f54aff-2342-4581-a384-4f1d5b1e4764" />

#### Attempt 2 – Standard Mesh
*8,989 elements · 15,529 nodes · element size 0.1569 in*

**Von Mises Stress**
<img width="1112" height="737" alt="Design II standard – von Mises stress" src="https://github.com/user-attachments/assets/278a8ad8-b0fd-49f5-bf1c-e180d79c78ef" />

**Displacement (URES)**
<img width="1190" height="758" alt="Design II standard – displacement" src="https://github.com/user-attachments/assets/956a6e32-d257-454e-9dc4-2c6e0144cdb8" />

**Factor of Safety**
<img width="965" height="687" alt="Design II standard – factor of safety" src="https://github.com/user-attachments/assets/bcba91ce-ac58-4aae-b393-506013ef2765" />

#### Attempt 3 – Fine Mesh
*68,130 elements · 104,910 nodes · element size 0.0766 in*

**Von Mises Stress**
<img width="1066" height="722" alt="Design II fine – von Mises stress" src="https://github.com/user-attachments/assets/51eb318e-d7af-47bd-b6e0-f6e607ec0ed5" />

**Displacement (URES)**
<img width="1021" height="721" alt="Design II fine – displacement" src="https://github.com/user-attachments/assets/a8646ecc-e803-4c61-b4aa-c12bf840c6d9" />

**Factor of Safety**
<img width="1056" height="677" alt="Design II fine – factor of safety" src="https://github.com/user-attachments/assets/9574ed07-3943-4dec-93f1-08487c4d3d64" />

#### Design II – Convergence

| Attempt | Mesh     | Elements | Nodes   | Max Stress (psi) | Max Deflection (in) | Safety Factor | % Change in Stress | % Change in Deflection |
|---------|----------|----------|---------|------------------|---------------------|---------------|--------------------|------------------------|
| 1       | Coarse   | 1,863    | 3,606   | 2.732e4          | 6.740e-3            | 4.39          | —                  | —                      |
| 2       | Standard | 8,989    | 15,529  | 3.943e4          | 6.921e-3            | 3.04          | +44.3%             | +2.7%                  |
| 3       | Fine     | 68,130   | 104,910 | 5.615e4          | 6.977e-3            | 2.14          | +42.4%             | +0.8%                  |

- **Max stress location:** sharp inside corner where the lower lug leg joins the bottom plate
- **Max deflection location:** middle of the crossbar where the strap wraps
- **Min FOS location:** same spot as max stress
- **Mesh note:** elements above an aspect ratio of 10 dropped from 2.74% (coarse) to 0.2% (fine)

**Result:** Deflection converged, changing only 2.7% and then 0.8%, both under the 7% target. Stress did not converge: it rose about 43% with each refinement, always at the same sharp inside corner. This pattern is a stress singularity. A sharp corner has zero radius, so the theoretical stress there is infinite, and each smaller element captures a higher peak. Per the assignment, the fine mesh results (Attempt 3) are used for Design II.

**Interpretation:** Design II is a large improvement over Design 1. Max stress dropped from 5.898e6 psi to 5.615e4 psi, and max deflection dropped from 9.082 in to 6.977e-3 in. However, the minimum FOS of 2.14 is still below the required 4. The coarse mesh showed a passing FOS of 4.39, which shows that a coarse mesh can hide a failure. The upper frame stays at low stress, which means material can be removed there to reduce mass.

#### Changes for Design III
TBD

### Design III

#### Attempt 1 – Coarse Mesh
<img width="1020" height="717" alt="Screenshot 2026-10-22 013948" src="https://github.com/user-attachments/assets/3a3b62e5-60d9-4291-bf22-64d29a3498f4" />

<img width="1040" height="672" alt="Screenshot 2026-10-22 013955" src="https://github.com/user-attachments/assets/43cfcf80-7764-4ed7-97fd-a743c866ab06" />

<img width="1040" height="737" alt="Screenshot 2026-10-22 014018" src="https://github.com/user-attachments/assets/3c1cb6fd-d9c8-41de-96a8-55b684a1fd79" />



#### Attempt 2 – Standard Mesh
<img width="1085" height="642" alt="Screenshot 2026-10-22 013813" src="https://github.com/user-attachments/assets/24d540c5-fbcc-4f85-bf05-8d1c474f673d" />

<img width="1006" height="647" alt="Screenshot 2026-10-22 013821" src="https://github.com/user-attachments/assets/b39159d3-c87a-4114-bdad-ac92e6384e2d" />

<img width="1031" height="653" alt="Screenshot 2026-10-22 013838" src="https://github.com/user-attachments/assets/19718f8f-5e81-4eed-bbc6-c5b8450cd82b" />



#### Attempt 3 – Fine Mesh
<img width="1227" height="697" alt="Screenshot 2026-10-22 013447" src="https://github.com/user-attachments/assets/45fd916d-d318-4090-b1ad-4cc0c54d1d02" />

<img width="1005" height="662" alt="Screenshot 2026-10-22 013527" src="https://github.com/user-attachments/assets/92974975-6eb7-4c8b-959d-ceb5b28f0b5e" />

<img width="1076" height="687" alt="Screenshot 2026-10-22 013551" src="https://github.com/user-attachments/assets/e663c9f0-c080-40fb-9fd3-31c7c2ee9761" />



#### Design III – Convergence

## Decide

### Results After Convergence

|                              | Design 1                              | Design II                                  | Design III |
|------------------------------|---------------------------------------|--------------------------------------------|------------|
| Max Stress and location      | 5.898e6 psi, neck–cylinder junction   | 5.615e4 psi, lug leg–bottom plate corner   |            |
| Max deflection and location  | 9.082 in, free end of cylinder        | 6.977e-3 in, center of crossbar            |            |
| Mass                         | TBD                                   | TBD                                        |            |
| Safety Factor                | 0.0203                                | 2.14                                       |            |
| Number of elements           | 68,990                                | 68,130                                     |            |

### Final Design Choice
TBD – which design performed best and why, comparing stress, stiffness, and mass.

## Communicate

### Mistakes
- TBD – e.g., the first coarse run (2,180 elements) was redone; explain why

### Lessons Learned
- TBD – be specific, and avoid words like "good" and "bad" (the instructions call this out)

### Time Spent
| Task | Time |
|------|------|
| Reading and setup | TBD |
| Design 1 simulations | TBD |
| Design II simulations | TBD |
| Design III simulations | TBD |
| Documentation | TBD |
| **Total** | **TBD** |
