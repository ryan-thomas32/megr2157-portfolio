# A9 – Pulleys

# A4 – Motor Mount

## Objective

Design a 3D-printed motor mount that holds a DC gearmotor while a load is applied to the tip of the motor shaft. The mount is split into two features that are each analyzed as cantilever beams for **stress** and **deflection**, then modeled parametrically in SolidWorks.

<!-- Assignment diagram image goes here -->

| Requirement | Value |
|---|---|
| Load at shaft tip | P = 300 N |
| Safety factor | n = 3 |
| Material options | ABS, PETG, or PLA |
| Motor weight | Neglected |
| Max deflection at shaft | 0.30 mm |
| Holes | Clearance holes for shaft and screws |

### Motor Dimensions

<!-- Motor drawing image goes here -->

| Feature | Dimension |
|---|---|
| Body diameter | Ø28 mm |
| Mounting boss | Ø18 mm × 2 mm |
| Shaft diameter | Ø6 mm (D-flat) |
| Shaft length from motor face | 18 ± 1 mm |
| Screw pattern | 4 screws, 11 mm from center (22 mm spacing) |

### Research

<!-- Research images go here -->

Commercial motor mounts were reviewed for design ideas:

- **Face (flange) mounting:** the motor bolts flat to a plate through its front screw pattern, with a clearance bore for the mounting boss.
- **L-bracket construction:** a face plate joined to an arm or base that bolts to a fixed surface.
- **Ribs and gussets:** used to stiffen the corner between the face plate and the base, which carries the highest load.
- **Fillets and edge distance:** material is kept around holes to prevent cracking.

---

## Analyze

### Material Properties (ABS)

| Property | Table Value | Converted |
|---|---|---|
| Elastic modulus, $E$ | 290,075 psi | 2000 MPa |
| Tensile strength, $S$ | 4351 psi | 30 MPa |

Conversion: 1 psi = 0.006895 MPa. No yield strength is listed for ABS, so tensile strength is used as the failure stress.

---

### Feature 1 – Front Plate (Attached to Motor)

#### 1. Knowns and Unknowns

**Knowns**

| Quantity | Symbol | Value | Source |
|---|---|---|---|
| Applied load | $P$ | 300 N | Assignment |
| Safety factor | $n$ | 3 | Assignment |
| Design load | $nP$ | 900 N | $n \times P$ |
| Lever arm (shaft length) | $\ell$ | 18 mm | Motor drawing |
| Plate width | $b$ | 40 mm | CAD |
| Fixed edge to shaft axis | $L$ | 20 mm | Half of 40 mm plate |
| Tensile strength | $S$ | 30 MPa | Material table |
| Elastic modulus | $E$ | 2000 MPa | Material table |
| Allowable deflection | $\delta_{allow}$ | 0.30 mm | Design requirement |
| Boundary conditions | $v(0),\ v'(0)$ | 0, 0 | Cantilever |

**Unknowns**

- Plate thickness, $t$
- Reactions, $R_A$ and $M_A$
- Bending moment, $M$
- Moment of inertia, $I$, and outer fiber distance, $c$
- Maximum stress, $\sigma$
- Deflection, $\delta$, and slope, $\theta$

**Assumptions**

1. The plate is a cantilever fixed where it joins the wall feature ($v = 0$, $v' = 0$).
2. $P$ acts vertically at the tip of the 18 mm shaft. The full shaft length is used as the lever arm, which is conservative.
3. The safety factor accounts for the shaft and screw holes, so the gross width $b$ is used in the main calculation. The cut is checked separately.
4. The motor weight is neglected.

#### 2. Free Body Diagram

<!-- FBD image goes here -->

```
        ///////////////////////////   fixed edge (joint with arm), x = 0
        ┌─────┐    R_A = 900 N  (down)
        │     │    M_A = 16,200 N·mm  (clockwise)
        │     │
  L =   │     │
 20 mm  │     │
        │     │
        │     ├ ─ ─ ─ ─ ─ ─ ─ ─ ●   shaft tip (rigid shaft)
        │     │                 ↑
        │     │                 nP = 900 N
        │     │◄── ℓ = 18 mm ──►
        │     │
        └─────┘
     Plate: b = 40 mm, thickness t
     x measured downward from the fixed edge
```

- **Support:** fixed at the top edge where the plate meets the arm.
- **Applied load:** $nP = 900$ N upward at the shaft tip, a horizontal distance $\ell = 18$ mm from the plate.
- **Reactions:** $R_A = 900$ N and $M_A = 16{,}200$ N·mm.
- **Moment diagram:** constant, $M = 16{,}200$ N·mm, from the fixed edge to the shaft.

#### 3. Equations (Symbolic)

**Equilibrium**

$$\sum F_y = 0: \quad R_A - nP = 0 \quad\Rightarrow\quad R_A = nP$$

$$\sum M_A = 0: \quad M_A - nP\,\ell = 0 \quad\Rightarrow\quad M_A = nP\,\ell$$

**Internal Moment**

$P$ is vertical, so only its horizontal offset $\ell$ creates a moment. The moment is the same at every section between the fixed edge and the shaft:

$$M = nP\,\ell$$

**Section Properties**

$$I = \frac{bt^3}{12}, \qquad c = \frac{t}{2}$$

**Stress**

$$\sigma = \frac{Mc}{I} = \frac{M\left(\frac{t}{2}\right)}{\frac{bt^3}{12}} = \frac{6M}{bt^2} \le S$$

$$Z_{req} = \frac{I}{c} = \frac{M}{S}$$

$$\boxed{t_\sigma = \sqrt{\frac{6M}{bS}}}$$

**Deflection**

Integrate the elastic curve and apply the boundary conditions:

$$EI\,v'' = M$$

$$EI\,v' = Mx + C_1, \quad v'(0) = 0 \;\Rightarrow\; C_1 = 0$$

$$EI\,v = \frac{Mx^2}{2} + C_2, \quad v(0) = 0 \;\Rightarrow\; C_2 = 0$$

At the shaft, $x = L$:

$$\delta = \frac{ML^2}{2EI}, \qquad \theta = \frac{ML}{EI}$$

Solve for the required moment of inertia, then the thickness:

$$I_{req} = \frac{ML^2}{2E\,\delta_{allow}}$$

$$\boxed{t_\delta = \sqrt[3]{\frac{12\,I_{req}}{b}} = \sqrt[3]{\frac{6ML^2}{Eb\,\delta_{allow}}}}$$

**Including the Front Cut**

The cut is included by multiplying the load terms by cut factors. Below the top screw, the screws transfer load into the plate, so the moment decreases:

$$\frac{M_x}{M} = \frac{x_b - x}{s}$$

The stress cut factor is taken at the worst section. The deflection cut factor is a weighted sum over zones along the plate:

$$K_\sigma = \frac{b}{b_{net}} \cdot \frac{M_x}{M}, \qquad K_\delta = \sum w_i \cdot \frac{b}{b_i} \cdot \frac{M_i}{M}, \qquad w_i = \frac{\Delta G_i}{L^2/2}, \qquad G(x) = Lx - \frac{x^2}{2}$$

$$\boxed{t_\sigma = \sqrt{\frac{6MK_\sigma}{bS}}} \qquad \boxed{t_\delta = \sqrt[3]{\frac{6ML^2K_\delta}{Eb\,\delta_{allow}}}}$$

**Design Rule**

$$t = \max(t_\sigma,\ t_\delta)$$

#### 4. Numerical Solution

**Moment**

$$M = nP\,\ell = (900)(18) = 16{,}200\ \text{N·mm}$$

**Stress (no cut)**

$$Z_{req} = \frac{16{,}200}{30} = 540\ \text{mm}^3$$

$$t_\sigma = \sqrt{\frac{6(16{,}200)}{(40)(30)}} = \sqrt{81} = 9.00\ \text{mm}$$

**Deflection (no cut)**

$$I_{req} = \frac{(16{,}200)(20)^2}{2(2000)(0.30)} = 5400\ \text{mm}^4$$

$$t_\delta = \sqrt[3]{\frac{12(5400)}{40}} = \sqrt[3]{1620} = 11.74\ \text{mm}$$

**Cut Geometry**

The cut is a Ø18.4 mm bore joined to four Ø3.4 mm screw slots at 11 mm from center, arranged in a plus pattern. The screws are located at $x_t = 9$ mm, $x = 20$ mm (side pair), and $x_b = 31$ mm, so $s = 22$ mm.

| Zone | x (mm) | $b_{net}$ (mm) |
|---|---|---|
| Solid | 0 – 7.3 | 40.0 |
| Top screw slot | 7.3 – 10.96 | 40 − 3.4 = 36.6 |
| Bore + side slots (average) | 10.96 – 20 | 24.0 |
| Narrowest (beside side slots) | 18.3 – 20 | 40 − 2(11 + 1.7) = 14.6 |

**Stress Cut Factor**

The worst section is beside the side slots:

$$K_\sigma = \frac{40}{14.6} \times \frac{31 - 18.3}{22} = 2.740 \times 0.577 = 1.581$$

**Deflection Cut Factor**

| Zone | x (mm) | $w_i$ | $b/b_i$ | $M_i/M$ | Product |
|---|---|---|---|---|---|
| Solid | 0 – 7.3 | 0.597 | 1.000 | 1.000 | 0.597 |
| Top slot | 7.3 – 10.96 | 0.199 | 1.093 | 0.994 | 0.216 |
| Bore + side slots | 10.96 – 20 | 0.204 | 1.669 | 0.706 | 0.241 |
| | | **1.000** | | $K_\delta$ | **1.054** |

**Thickness With Cut**

$$t_\sigma = \sqrt{\frac{6(16{,}200)(1.581)}{(40)(30)}} = \sqrt{128.1} = 11.32\ \text{mm}$$

$$t_\delta = \sqrt[3]{\frac{6(16{,}200)(20)^2(1.054)}{(2000)(40)(0.30)}} = \sqrt[3]{1707.5} = 11.95\ \text{mm}$$

$$t = \max(11.32,\ 11.95) = 11.95\ \text{mm} \;\rightarrow\; \textbf{t = 12 mm}$$

**Check at t = 12 mm**

$$I = \frac{(40)(12)^3}{12} = 5760\ \text{mm}^4$$

| Check | No Cut | With Full Cut | Limit | Status |
|---|---|---|---|---|
| Required thickness | 11.74 mm | 11.95 mm | — | — |
| Stress | $\frac{(16{,}200)(6)}{5760} = 16.9$ MPa | $16.9 \times 1.581 = 26.7$ MPa | 30 MPa | ✓ |
| Deflection | $\frac{(16{,}200)(20)^2}{2(2000)(5760)} = 0.281$ mm | $0.281 \times 1.054 = 0.296$ mm | 0.30 mm | ✓ |
| Slope | 0.028 rad (1.6°) | — | — | — |
| Actual safety factor (300 N) | $30 / (16.9/3) = 5.3$ | $30 / (26.7/3) = 3.4$ | ≥ 3 | ✓ |

**Result:** a 40 × 40 × 12 mm ABS plate. Deflection governs. The weakest section is beside the side screw slots.

> **Hole Orientation Check:** Rotating the screw pattern 45° puts both upper slots at x = 12.2 mm, where nearly the full moment acts ($b_{net} = 22.0$ mm). This raises the stress to 30.7 MPa and the deflection to 0.333 mm at t = 12 mm, which fails. The standard plus orientation was kept.

---

### Feature 2 – Arm (Attached to Wall)

#### 1. Knowns and Unknowns

**Knowns**

| Quantity | Symbol | Value | Source |
|---|---|---|---|
| Design load | $nP$ | 900 N | Feature 1 |
| Shaft offset from plate back face | $\ell$ | 18 mm | Motor drawing |
| Arm length (plate to wall bolts) | $a$ | ___ mm | CAD |
| Arm width | $b_{arm}$ | ___ mm | CAD |
| Tensile strength | $S$ | 30 MPa | Material table |
| Elastic modulus | $E$ | 2000 MPa | Material table |
| Allowable deflection | $\delta_{allow}$ | ___ mm | Design requirement |
| Boundary conditions at wall | $v(a),\ v'(a)$ | 0, 0 | Cantilever |

**Unknowns**

- Arm thickness, $t_{arm}$
- Wall reactions, $R_W$ and $M_W$
- Maximum moment, $M_{max}$
- Stress, $\sigma$
- Deflection, $\delta$, and slope, $\theta$, at the plate end

#### 2. Free Body Diagram

<!-- FBD image goes here -->

```
  WALL
  ////┌──────────────────────────────┐
  ////│            arm               │─┐  plate (Feature 1, rigid)
  ////└──────────────────────────────┘ │
  ////  R_W = nP                        │ ─ ─ ─ ─ ●  shaft tip
  ////  M_W = nP(a + ℓ)                 │         ↑ nP = 900 N
      ◄──────────── a ───────────────►◄─── ℓ ───►
      z = a (wall)                  z = 0 (plate)
```

- **Support:** fixed at the wall.
- **Load at the plate end of the arm:** force $nP$ plus moment $nP\,\ell$, transferred from Feature 1.

#### 3. Equations (Symbolic)

**Equilibrium**

$$R_W = nP, \qquad M_W = nP\,(a + \ell)$$

**Internal Moment**

Measure $z$ from the plate toward the wall. The moment increases toward the wall:

$$M(z) = nP\,(z + \ell), \qquad M_{max} = nP\,(a + \ell)$$

**Stress**

$$\sigma = \frac{6M_{max}}{b_{arm}\,t_{arm}^2} \le S \quad\Rightarrow\quad \boxed{t_{arm,\sigma} = \sqrt{\frac{6\,nP\,(a + \ell)}{b_{arm}\,S}}}$$

**Deflection**

Superpose the end force $nP$ and the end moment $nP\,\ell$:

$$\delta = \frac{nP\,a^3}{3EI} + \frac{nP\,\ell\,a^2}{2EI} = \frac{nP\,a^2\,(2a + 3\ell)}{6EI}$$

$$\theta = \frac{nP\,a^2}{2EI} + \frac{nP\,\ell\,a}{EI}$$

Substitute $I = b_{arm}t_{arm}^3/12$:

$$\boxed{t_{arm,\delta} = \sqrt[3]{\frac{2\,nP\,a^2\,(2a + 3\ell)}{E\,b_{arm}\,\delta_{allow}}}}$$

**Design Rule**

$$t_{arm} = \max(t_{arm,\sigma},\ t_{arm,\delta})$$

#### 4. Numerical Solution

**Moment**

$$M_{max} = (900)(\_\_\_ + 18) = \_\_\_\ \text{N·mm}$$

**Stress**

$$t_{arm,\sigma} = \sqrt{\frac{6(900)(\_\_\_ + 18)}{(\_\_\_)(30)}} = \_\_\_\ \text{mm}$$

**Deflection**

$$t_{arm,\delta} = \sqrt[3]{\frac{2(900)(\_\_\_)^2\,(2(\_\_\_) + 54)}{(2000)(\_\_\_)(\_\_\_)}} = \_\_\_\ \text{mm}$$

**Selected thickness:** $t_{arm}$ = ___ mm

| Check | Result | Limit | Status |
|---|---|---|---|
| Stress | ___ MPa | 30 MPa | |
| Deflection | ___ mm | ___ mm | |

---

## Decide

### Material Selection

**ABS** was selected:
- Its property data was available from the SolidWorks material library.
- It is tougher and less brittle than PLA, which matters under a shock load on the shaft.
- It has better heat resistance than PLA near a running motor.

### Final Geometry

| Parameter | Value |
|---|---|
| Front plate | 40 × 40 × **12 mm** |
| Shaft exposed past plate | 18 − 12 = 6 mm |
| Motor boss bore | Ø18.4 mm |
| Screw slots | Ø3.4 mm at 11 mm from center, plus pattern |
| Arm | ___ × ___ × ___ mm |

### Features to Minimize Deflection

| Feature | Purpose |
|---|---|
| Straight gussets (2 ribs, 4 mm thick, 20 mm along arm × 30 mm down plate) | Stiffen the plate–arm corner. They run past the side screw slots to reinforce the weakest section. They are not counted in the Feature 1 calculation, so they add extra margin. |
| Gusset toe near the bottom screw | Ends the rib where the moment is nearly zero, which reduces stress concentration. |
| Fillets at the plate–arm corner and gusset toe | Reduce stress concentrations. |
| Plus hole orientation | Keeps the narrowest net section where the moment is lowest. |
| Print orientation | Layers run along the plate and gussets, so bending tension is not across layer lines. |

### Clearance Holes

| Hole | Nominal | Designed | Reason |
|---|---|---|---|
| Motor boss | Ø18 (−0.1) mm | Ø18.4 mm | 0.4 mm clearance; printed holes shrink |
| Mounting screws | M3 | Ø3.4 mm | Standard M3 normal clearance |
| Shaft | Ø6 mm | Passes through the boss bore | No contact with the plate |
| Wall bolts | ___ | ___ | |

---

## Communicate

### Isometric Sketch

<!-- Isometric sketch image goes here -->

### CAD Model

<!-- CAD screenshots go here -->

### Parametric Modeling

The model is driven by global variables (Tools → Equations), so changing a value updates the full part.

| Global Variable | Value | Drives |
|---|---|---|
| `Plate_b` | 40 mm | Plate width and height |
| `Plate_t` | 12 mm | Plate thickness |
| `Boss_d` | 18 mm | Motor boss diameter |
| `Clearance` | 0.4 mm | Hole clearance |
| `Bore_d` | `Boss_d + Clearance` | Center bore |
| `Screw_offset` | 11 mm | Screw slot distance from center |
| `Screw_clear` | 3.4 mm | Screw slot width |
| `Pattern_angle` | 0° | Hole pattern rotation |
| `Gusset_w` | 4 mm | Rib thickness |
| `Gusset_D` | 20 mm | Rib leg along arm |
| `Gusset_H` | 30 mm | Rib leg down plate |
| `Arm_t` | ___ mm | Arm thickness |
| `Arm_length` | ___ mm | Arm length |

**Design Intent**

- Sketches are fully defined and symmetric about the origin.
- The cut is centered on the motor axis, so the bore and slots stay aligned with the motor.
- Gussets are mirrored about the plate centerline.
- Screw slots use a circular pattern driven by `Pattern_angle`.

<!-- Equations dialog screenshot goes here -->

### Summary

| Feature | Thickness | Stress | Deflection | Governs | Status |
|---|---|---|---|---|---|
| Feature 1 – Front plate (with cut) | 12 mm | 26.7 MPa | 0.296 mm | Deflection | ✓ |
| Feature 2 – Arm | ___ mm | ___ MPa | ___ mm | ___ | |

### Reflection

- **Deflection governed the plate.** Stress required only 9 mm, but keeping deflection under 0.30 mm required 12 mm.
- **The front cut mattered most beside the side screw slots,** where the net width drops to 14.6 mm. Because the screws carry part of the load, the moment there is only about 58% of the maximum, so the plate still passed.
- **Hole orientation affects strength.** Rotating the pattern 45° would have placed a large cut where the full moment acts and required a thicker plate.
- **Using the full 18 mm shaft length as the lever arm was conservative.** Measuring to the plate mid-plane would reduce the moment.
