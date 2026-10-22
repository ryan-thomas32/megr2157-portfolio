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
- **Material:** TBD (yield strength 1.200e5 psi; material not changed between designs)
- **Fixtures:** TBD – which faces are fixed and why
- **Loads:** TBD – magnitude, direction, and which face
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
TBD – what geometry was changed and why, based on the Design 1 results (e.g., thicken/widen the neck, add a fillet at the neck–cylinder corner, remove material from the low-stress frame)

### Design II

#### Attempt 1 – Coarse Mesh

#### Attempt 2 – Standard Mesh

#### Attempt 3 – Fine Mesh

#### Design II – Convergence

#### Changes for Design III
TBD

### Design III

#### Attempt 1 – Coarse Mesh

#### Attempt 2 – Standard Mesh

#### Attempt 3 – Fine Mesh

#### Design III – Convergence

## Decide

### Results After Convergence

|                              | Design 1                              | Design II | Design III |
|------------------------------|---------------------------------------|-----------|------------|
| Max Stress and location      | 5.898e6 psi, neck–cylinder junction   |           |            |
| Max deflection and location  | 9.082 in, free end of cylinder        |           |            |
| Mass                         | TBD                                   |           |            |
| Safety Factor                | 0.0203                                |           |            |
| Number of elements           | 68,990                                |           |            |

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
