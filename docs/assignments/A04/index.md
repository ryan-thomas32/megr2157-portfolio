# A4 – Motor Mount

## Objective

Design a motor mount for a brushed 24 V DC Gear Motor (3.6 kg · cm/46 RPM with a 99.5:1 Planetary Gearbox) that attaches to a rigid wall. A load is applied to the tip of the motor shaft. The mount is split into two features, each analyzed as a cantilever beam for stress and deflection, then modeled parametrically in SolidWorks.

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
| Screw pattern | 4 M3 screws, 11 mm from center|

### Research
I did a little bit of research because I was looking for a specific design that I'd seen before. I use it to mount my direct-drive wheel to my sim racing cockpit, as shown in the picture below. Even at a different scale, that was the idea I first had using a rib style design to add structure and support. The only difficulty I had while researching it was that it is made of steel, so it can be much thinner than the plastics we are using for this assignment. That was the max extent of my research because that idea didn't really relate to what we are trying to do with the material and wouldn't translate well in theory.[Link](https://simucube.com/en-us/simucube-mount/?srsltid=AU7gw4WFyWLQzK47LTbxoz8Qmto5Bq2chDBEaHztHk5MBwLGY0fI1wCj)
<img width="700" height="700" alt="Simucube Mount_02" src="https://github.com/user-attachments/assets/abea8800-ea03-494d-8f5b-72e7a55ec062" />



## Analyze
For this section, instead of including the lists of knowns and unknowns I did on paper, I experimented with making tables in GitHub to organize the data better, since I know my handwriting isn't the best. It's hard to understand on paper; this took time at first. Still, you get the hang of it. It was pretty simple to do. I listed all the material property values for the material I chose, which was ABS plastic. Then I listed the knowns and unknowns, including the quantity symbol and value, and for the knowns, I listed the source where it was given.

### Feature 1
For my hand calculations for feature one, I made a few assumptions. First, I assumed the force is applied at the tip of the shaft, so I adjusted the moment equation by multiplying it by the shaft length. I then drafted a design for feature one and assumed that one end was rigid. Lastly, SolidWorks listed no yield strength for ABS plastic, so I used tensile strength for my calculation. I listed all my knowns and unknowns, then solved symbolically and numerically for thickness and determined the stress and deflection.

#### Material Properties (ABS)

| Property | Value |
|---|---|
| Elastic modulus, $E$ | 2000 MPa |
| Tensile strength, $S$ | 30 MPa |

#### Feature 1 – Front Plate (Attached to Motor)

##### Knowns and Unknowns

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
| Thickness from stress | $t_{\sigma}$ | ? |
| Thickness from deflection | $t_{\delta}$ | ? |
| Plate thickness | $t$ | ? |
| Reaction force | $R_A$ | ? |
| Bending moment | $M$ | ? |
| Moment of inertia | $I$ | ? |
| Neutral Axis | $c$ | ? |
| Maximum stress | $\sigma$ | ? |
| Deflection | $\delta$ | ? |

##### Free Body Diagram and Calculations
The image link below shows my process of calculations for finding all the values and unknowns for feature 1
I first wrote all of my equations out symbolically before plugging in any numbers. My work on paper was somewhat disorganized, which I can improve in the future, and then I completed it with the numerical calculations.
<img width="2444" height="3264" alt="CamScanner 9-17-26 03 16n" src="https://github.com/user-attachments/assets/114d9425-f240-414a-9710-afd3de0b4e4a" />


| Variable | Symbol | Value |
|---|---|---|
| Thickness from stress | $t_{\sigma}$ | 9.00 mm |
| Thickness from deflection | $t_{\delta}$ | 11.74 mm |
| Plate thickness | $t$ | 11.74 mm (use 12 mm) |
| Reaction force | $R_A$ | 900 N |
| Bending moment | $M$ | 16,200 N x mm |
| Moment of inertia | $I$ | 5760 mm^4 |
| Neutral Axis | $c$ | 6 mm |
| Maximum stress | $\sigma$ | 16.9 MPa |
| Deflection | $\delta$ | 0.281 mm |

### Feature 2
Feature two is a bit different from feature one, as it's the section of the mount that matches the wall. Still, I was able to repeat the same steps as feature one by creating F baby at the top of my. I also decided to show my cross-section, since I went a little different with my design and had two arms sticking out for my feature. I again listed all my knowns and unknowns, then symbolically and numerically calculated the thickness of my arms using stress and deflection, following all the calculations from this section. With those values, I'll be able to recreate my mount in CAD. 

#### Feature 2 – Bottom Arms (Attached to Wall)

##### Knowns and Unknowns

**Knowns**

| Quantity | Symbol | Value | Source |
|---|---|---|---|
| Applied load | $P$ | 300 N | Assignment |
| Safety factor | $SF$ | 3 | Assignment |
| Lever arm (shaft length) | $L_{S}$ | 18 mm | Motor drawing |
| Arm length (wall bolts to plate) | $L_{A}$ | 30 mm | Chosen |
| Width of one arm | $b_{1}$ | 12 mm | Chosen |
| Total arm width (2 arms) | $b_{arm}$ | 24 mm | 2 × $b_{1}$ |
| Tensile strength | $S$ | 30 MPa | Material |
| Elastic modulus | $E$ | 2000 MPa | Material |
| Allowable deflection | $\delta_{max}$ | 0.30 mm | Assignment |

**Unknowns**

| Variable | Symbol | Value |
|---|---|---|
| Thickness from stress | $t_{arm,\sigma}$ | ? |
| Thickness from deflection | $t_{arm,\delta}$ | ? |
| Arm thickness | $t_{arm}$ | ? |
| Reaction force | $R_W$ | ? |
| Bending moment | $M_{max}$ | ? |
| Moment of inertia | $I$ | ? |
| Neutral Axis | $c$ | ? |
| Maximum stress | $\sigma$ | ? |
| Deflection | $\delta$ | ? |

##### Free Body Diagram and Calculations
The image link below shows my process of calculations for finding all the values and unknowns for feature 2

I followed the same process as Feature 1, writing my equations out symbolically before plugging in any numbers. The main difference is that the bottom arms are fixed at the wall bolts, so the moment uses the arm length plus the shaft length. The end of the arms also carries both a force and a moment, so the deflection equation has two terms.
<img width="1704" height="2196" alt="CamScanner 9-17-26 03 18n" src="https://github.com/user-attachments/assets/01cb3e17-df9a-4138-8d62-2712aa6f7a6d" />


| Variable | Symbol | Value |
|---|---|---|
| Thickness from stress | $t_{arm,\sigma}$ | 18.97 mm |
| Thickness from deflection | $t_{arm,\delta}$ | 23.41 mm |
| Arm thickness | $t_{arm}$ | 23.41 mm (use 24 mm) |
| Reaction force | $R_W$ | 900 N |
| Bending moment | $M_{max}$ | 43,200 N x mm |
| Moment of inertia | $I$ | 27,648 mm^4 |
| Neutral Axis | $c$ | 12 mm |
| Maximum stress | $\sigma$ | 18.8 MPa |
| Deflection | $\delta$ | 0.278 mm |
### Isometric Sketch
<img width="1676" height="1956" alt="CamScanner 9-17-26 03 18n (1)" src="https://github.com/user-attachments/assets/12069504-4d1b-4f48-882e-fc6621583f4d" />

### SolidWorks Model
Moving on to SolidWorks 2025, I first drew a new sketch on the right plane. I drew an eighteen-millimeter-diameter circle in the center. Then I drew a 3.4 mm circle 11 mm above the origin. Then I used sketch relations to define the rest of my inner cut. I then used a center rectangle, starting at the origin of our cut, and extended it around the cut. Then I set all 4 sides to the same length, since we have a square cross section for the front of feature one. Then I set it to the 40 mm cross-section we decided to use. Then I used the Circular Sketch Pattern feature in SolidWorks to array four holes around the main center circle to create the bolt holes. Because there was very limited space between that 18 mm diameter cut and the holes for the screws, I ended up cutting out a rectangle between the two to prevent material from possibly failing. Then I extruded that out by the thickness we found in my calculations.
<img width="1110" height="547" alt="image" src="https://github.com/user-attachments/assets/042ff51a-4799-4f9e-abe1-804b64a919d2" />

<img width="1002" height="916" alt="image" src="https://github.com/user-attachments/assets/4fcd4db6-dd5f-4e76-bb31-77aa49f62b17" />

Then, on the underside of my first feature, I drew feature #2 for the two arms. First, I drew two rectangles from the front. Next, I made each side equal. Then, I used my global values and my hand calculations to set the arm base width, arm thickness, and arm length for feature 2. Then, I extruded it by the thickness I calculated. To make it easier, I included the wall and the holes to mount it to the wall. Again, those holes are 3.4 mm in diameter, and I placed four on each corner of feature 2.

<img width="1542" height="808" alt="image" src="https://github.com/user-attachments/assets/e7de7e14-8548-4fff-be7d-49c057406e42" />

And after all that is complete we should be left with the bracket we see below

<img width="1006" height="842" alt="image" src="https://github.com/user-attachments/assets/5e3d43d3-6c0c-465e-896c-0b6aa3d61133" />

After completing the main part of the mountain I designed for the assignment, I filleted the edge between the two features to reduce motor mount deflection. I set the fillets to a 12 mm radius so they do not interfere with the motor's radius when inserted into the bracket.

<img width="1077" height="836" alt="image" src="https://github.com/user-attachments/assets/212065ba-062f-489f-9c32-5bc071b2a6b2" />

### 2157 Drawing
This is my technical drawing that shows all the features and dimensions needed to replicate my motor mount design.
<img width="652" height="853" alt="image" src="https://github.com/user-attachments/assets/4c4ef45e-a528-4f99-a633-f10f72e99a5c" />

## Decide
My first decision when designing my motor mount was to make it from ABS plastic because its properties fit my design, and I know ABS is a very common printing filament in real-world use. Secondly, I chose a front feature plate width of 40mm for feature one. This fits the 28 mm motor body with room on each side and leaves space for the 22 mm screw pattern, plus plenty of space from the shaft to the edge. Thirdly, I used the full 18mm length of the motor shaft as the lever arm since the load is applied to the tip of the shaft. Lastly, I chose two arms for feature two instead of a solid bottom. A solid bottom would have been very thick and, in my view, would have bent more easily. This gave two arms that resist bending and use less filament.
## Communicate
This assignment was really fun and really challenging at the same time. I found it difficult because I hadn't done much with bending or moments of inertia, so getting up to speed was a bit of a challenge. After that, designing and drawing the mountain cat was really enjoyable, since we had a lot of freedom to do what we wanted and try different things to see how they worked. I ended up trying to have two arms as my fixed feature attaching to the wall, which I think worked out pretty well in the end. It might add extra complexity and time to complete this assignment, but overall it took me around 10 hours, which is about the same as the other assignments. So the difficulty felt about on par with the others too, but in the future I don't really think I need to worry too much about time management, since I feel like I did pretty well on this one even though I rushed at the last minute.
## Appendix
[A4 Mount Part Download](https://drive.google.com/file/d/1l49hy9svjd6-Eh4clh7wEz-ObnOedd52/view?usp=sharing)

[A4 Mount Drawing](https://drive.google.com/file/d/1MCdKcYyK6kO-5hSI201myPAMmzBwNGxl/view?usp=sharing)
