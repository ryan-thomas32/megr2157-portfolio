# A4 – Motor Mount

## Objective

Design a motor mount using the (Brushed 24V DC Gear Motor 3.6Kg.cm/46RPM w/ 99.5:1 Planetary Gearbox) that attaches to a rigid wall. A load is applied to the tip of the motor shaft. The mount is split into two features, each analyzed as a cantilever beam for stress and deflection, then modeled parametrically in SolidWorks.

<img width="738" height="594" alt="download (2)" src="https://github.com/user-attachments/assets/58f49c7e-7c99-4ff1-b8a6-d89453fcf776" />

| Requirement | Value |
|---|---|
| Load at shaft tip | P = 300 N |
| Safety factor | SF = 3 |
| Material options | ABS, PETG, or PLA |
| Motor weight | Neglected |
| Max deflection at shaft | 0.30 mm |

### Motor Dimensions

<img width="1917" height="708" alt="image" src="https://github.com/user-attachments/assets/764524d2-815e-4c26-88e8-a76c5b001845" />

| Feature | Dimension |
|---|---|
| Body diameter | Ø28 mm |
| Mounting boss | Ø18 mm × 2 mm |
| Shaft length from motor face | 18mm |
| Screw pattern | 4 M3 screws, 11 mm from center (22 mm spacing) |

### Research
<img width="700" height="700" alt="Simucube Mount_02" src="https://github.com/user-attachments/assets/abea8800-ea03-494d-8f5b-72e7a55ec062" />

<img width="700" height="700" alt="pro_white_2_square" src="https://github.com/user-attachments/assets/ca34aee4-2187-4079-8b8b-aa8c1922a86b" />


## Analyze
For this section, instead of including the lists of knowns and unknowns I did on paper, I experimented with making tables in GitHub to organize the data better, since I know my handwriting isn't the best. It's hard to understand on paper; this took time at first. Still, you get the hang of it. It was pretty simple to do. I listed all the material property values for the material I chose, which was ABS plastic. Then I listed the knowns and unknowns, including the quantity symbol and value, and for the knowns, I listed the source where it was given.
### Material Properties (ABS)

| Property | Value |
|---|---|
| Elastic modulus, $E$ | 2000 MPa |
| Tensile strength, $S$ | 30 MPa |
### Feature 1 – Front Plate (Attached to Motor)

#### 1. Knowns and Unknowns

**Knowns**

| Quantity | Symbol | Value | Source |
|---|---|---|---|
| Applied load | $P$ | 300 N | Assignment |
| Safety factor | $SF$ | 3 | Assignment |
| Lever arm (shaft length) | $L_{S}$ | 18 mm | Motor drawing |
| Plate width | $b$ | 40 mm | Chosen |
| Fixed edge to shaft axis | $L$ | 20 mm | Half of b |
| Tensile strength | $S$ | 30 MPa | Material |
| Elastic modulus | $E$ | 2000 MPa | Material |
| Allowable deflection | $\delta_{max}$ | 0.30 mm | Assignment |

**Unknowns**

| Variable | Symbol | Value |
|---|---|---|
| Plate thickness | $t$ | ? |
| Reaction force | $R_A$ | ? |
| Reaction moment | $M_A$ | ? |
| Bending moment | $M$ | ? |
| Moment of inertia | $I$ | ? |
| Neutral Axis | $c$ | ? |
| Maximum stress | $\sigma$ | ? |
| Deflection | $\delta$ | ? |
| Slope | $\theta$ | ? |

#### Free Body Diagram and Calculations
The image link below shows my process of calculations for finding all the values and unknowns for feature 1

I first wrote all of my equations out symbolically before plugging in any numbers. My work on paper was somewhat unorganized, which is something I can improve in the future, then followed with the numerical calculations
<>
| Variable | Value |
|---|---|
| Thickness | $t$ = 11.74 mm |
| Deflection | $\delta$ = 0.281 mm |
| Maximum stress | $\sigma$ = 26.7 Mpa |
Following these calculations for my design I then choose a thickness of 12mm for my  front face of my design



## Decide


## Communicate

