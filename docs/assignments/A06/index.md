<img width="857" height="292" alt="image" src="https://github.com/user-attachments/assets/9b65d98c-8336-47dc-99c0-ec5d961f1ebf" /># A6 – [Topic]

## Analyze

### Reviewing Previous Calculations
I carried all dimensions for this section over from my stress calculations in A5. I chose the stress-based values over the deflection-based ones because stress required larger dimensions in most segments and features, and those dimensions were a better, more accurate fit for my bracket based on a quick run-through.

<img width="2000" height="2600" alt="CamScanner 9-24-26 07 55n" src="https://github.com/user-attachments/assets/0d594c4b-f6f6-4d64-999e-13e3251cdd87" />

### First Attempt – Hard-Coded Dimensions
My first attempt at my parametric table went well. I got all the correct numbers that matched each dimension I calculated from my stress analysis. Still, during my calculations, I noticed a small error in the height of feature 4: I forgot to include W in my height equation, so I updated my parametric equation table and got a new result.

### Final Parametric Equation Table

<img width="1327" height="452" alt="Screenshot 2026-09-30 224709" src="https://github.com/user-attachments/assets/618a2662-7006-4a24-9354-080436b1f0e8" />

### Starting CAD Drawing and Linking Variables to Dimensions

I started by sketching the rough shape of the bracket's front feature on the front plane. At this point, I was not worried about exact sizes; I just wanted the general basic profile down, with the T-beam and the overall outer shape .

<img width="915" height="466" alt="Screenshot 2026-09-30 220053" src="https://github.com/user-attachments/assets/e0c461af-7280-4da9-bc2e-89b4acbce0e9" />

Then I added the basic sketch relations seen to make the shape symmetrical as required

<img width="892" height="470" alt="Screenshot 2026-09-30 220233" src="https://github.com/user-attachments/assets/9fe6c605-33c6-422c-a330-ac744d676aa3" />

Once the sketch had its general shape, I linked each dimension to my global variables. The sketch then updated to the correct geometry based on my calculations, and for each linked dimension, I made sure it displayed the Σ symbol to indicate that an equation drove it.

<img width="1172" height="767" alt="Screenshot 2026-09-30 220748" src="https://github.com/user-attachments/assets/025ddd6d-b92e-4698-b10f-58b03cc681ef" />

Then I extruded the sketch to the calculated length. This yielded the 3D shape for the upper part of the bracket, featuring C, D, and E.

<img width="1695" height="852" alt="Screenshot 2026-09-30 220812" src="https://github.com/user-attachments/assets/be193d50-2c57-4d39-a6ac-c41f4a81a216" />

<img width="832" height="710" alt="Screenshot 2026-09-30 220833" src="https://github.com/user-attachments/assets/577bc885-9dc8-45ac-8f5b-19359e51e2ea" />

Then I started a sketch of the bottom face to create the 3d structure for feature B, including more sketch relations and linking my variables to the sketch and the extrusion.

<img width="1208" height="826" alt="Screenshot 2026-09-30 221005" src="https://github.com/user-attachments/assets/b45d3edb-1118-43fd-a3f6-5bf478eb7d11" />

<img width="705" height="457" alt="Screenshot 2026-09-30 221122" src="https://github.com/user-attachments/assets/77d2fe1b-6f93-484d-ba55-5071444292ba" />

<img width="977" height="637" alt="Screenshot 2026-09-30 221400" src="https://github.com/user-attachments/assets/9b07e5f5-03ce-4443-a1d5-4fec79cb8132" />

Next is a sketch on the front face of feature B: the circle cross-section for feature A, again linking the sketch dimensions to the dimensions and the extrusion.

<img width="1058" height="717" alt="Screenshot 2026-09-30 221934" src="https://github.com/user-attachments/assets/13404034-62d5-4591-a634-a6ff3094106b" />

### Final Solid Model

<img width="457" height="467" alt="Screenshot 2026-09-30 224653" src="https://github.com/user-attachments/assets/d8cf6228-e830-4ba7-9afe-cb9f6006983c" />

## Link Design (2157 Students Only)

For this part, I designed a link that connects to the bracket I modeled in Part 1. I also created an engineering drawing with complete dimensioning and GD&T per ASME Y14.5 so the link can be fabricated and assembled accurately.

<img width="2208" height="2808" alt="CamScanner 9-24-26 06 14n" src="https://github.com/user-attachments/assets/a9db8dcb-281c-480c-a0a8-0bf61e215f88" />

### Parametric Equation Table

<img width="1315" height="573" alt="Screenshot 2026-10-01 025719" src="https://github.com/user-attachments/assets/a1911410-a1a0-4fab-bd96-f64bc653de18" />

### SolidWorks Sketch With Linked Variables to Dimensions

<img width="907" height="681" alt="Screenshot 2026-10-01 025558" src="https://github.com/user-attachments/assets/c2fe77a6-5334-4029-82bc-ed9b6b231c49" />

Once the sketch had its shape, I linked each dimension to my global variables. I made sure each linked dimension showed the Σ symbol so I knew it was being driven by an equation.

### Extruding the Link

Then I extruded the sketch to the thickness driven by "T 1", which gave me the 3D shape of the link.

<img width="1726" height="775" alt="Screenshot 2026-10-01 025638" src="https://github.com/user-attachments/assets/5475bb2c-ef28-484d-97ee-2c72a415e8fc" />

### Final Solid Model

<img width="515" height="857" alt="Screenshot 2026-10-01 025705" src="https://github.com/user-attachments/assets/b4a01a17-336f-4210-bc63-44f2da9f80df" />

### Mistakes 

One mistake from the first part of the assignment in A5 that I needed to address was that feature B was too short to fit the cross-section of feature A. I went back to my calculations and decided to set a specific height instead of a specific thickness so feature A's cross-section would fit with the link and the strap. I set the height of feature B to 1 inch, which automatically updated the thickness of feature B in the SolidWorks equation

## Communicate

### Engineering Drawing Bracket

<img width="1635" height="972" alt="A6 Bracket RT" src="https://github.com/user-attachments/assets/6f1a61ba-5a01-4f34-8c27-7aa8700f1f95" />

### Engineering Drawing 2157 Link

<img width="1610" height="947" alt="A6 Link RT" src="https://github.com/user-attachments/assets/589c1917-fa19-4e57-9d1f-888ae3955c28" />


## Decide


## Communicate

## Appendix

[A6 Downloads Folder(4 Items)](https://drive.google.com/drive/folders/1YsM7HtLYIG-uyTXa7ah0Mi5yEQOvlUZQ?usp=sharing)
