# A6 – Bracket Drawing
## Objective
For Assignment A6, we are continuing the bracket design by creating a parametric CAD model and a detailed engineering drawing, following up on our previous assignment, which covered tolerances and sliding fits. We will reuse the calculations from Assignment 5 to drive the parametric design, so every dimension in the model is linked to my equations and updates automatically if an input changes. We will also cover ASME  standards and use CAD to design both a bracket that slides over the T-beam and a link that fits onto Feature A, then create fully dimensioned multiview drawings with engineered tolerances for each. I am using titanium again, since that is what I chose for Assignment 5.

<img width="323" height="238" alt="image" src="https://github.com/user-attachments/assets/bf7b3517-d4e4-4b81-9b17-3f7bf08610c0" />

## Analyze

### Reviewing Previous Calculations
I carried all dimensions for this section over from my stress calculations in A5. I chose the stress-based values over the deflection-based ones because stress required larger dimensions in most segments and features, and those dimensions were a better, more accurate fit for my bracket based on a quick run-through.

<img width="2000" height="2600" alt="CamScanner 9-24-26 07 55n" src="https://github.com/user-attachments/assets/0d594c4b-f6f6-4d64-999e-13e3251cdd87" />

### First Attempt – Hard-Coded Dimensions
My first attempt at my parametric table went well. I got all the correct numbers that matched each dimension I calculated from my stress analysis. Still, during my calculations, I noticed a small error in the height of feature C, I had forgotten to include W in my height equation, so I updated my parametric equation table and obtained a new result.

### Final Parametric Equation Table

<img width="1327" height="452" alt="Screenshot 2026-09-30 224709" src="https://github.com/user-attachments/assets/618a2662-7006-4a24-9354-080436b1f0e8" />

### Starting CAD Drawing and Linking Variables to Dimensions

I started by sketching the rough shape of the bracket's front feature on the front plane. At this point, I was not worried about exact sizes; I just wanted the general basic profile down, with the T-beam and the overall outer shape .

<img width="915" height="466" alt="Screenshot 2026-09-30 220053" src="https://github.com/user-attachments/assets/e0c461af-7280-4da9-bc2e-89b4acbce0e9" />

Then I added the basic sketch relations seen to make the shape symmetrical, as required

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


### Engineering Drawing Bracket

Fits  
a -> RC7  
b -> RC3  
c -> RC4

<img width="1237" height="797" alt="image" src="https://github.com/user-attachments/assets/a8261f04-ed56-4e78-9c22-3a7a090254b2" />


### Engineering Drawing 2157 Link
Fits  
Hole A -> RC6  
Hole 1in -> FN1

<img width="1355" height="875" alt="image" src="https://github.com/user-attachments/assets/093ed658-e1bd-4208-8fdd-f5128849cbf7" />

## Communication

### Reflections

I used one analytical equation for stress to drive at least one other dimension in my parametric model, which controlled Feature C's height. Feature C was also linked to Feature E's height. I linked the heights of Feature C and Feature E into part of the equation for the height of Feature D. When I realized I had made a calculation error in Feature C in the first part, in a 5, I changed the value in the equation to the correct one. That adjustment updated each parameter for features E, D, and C, which helped a lot because I otherwise would have had to rework my work manually. The models were able to calculate on their own from the equations that I had input into SolidWorks.

One place where I used a tighter tolerance was the B slots that slide along the T-beam flange overhangs, which I held at X.XXX ± .005. This surface is an important part of the sliding assembly, and it handles much of the bracket alignment. The chosen material needs to support that fit, since a looser material choice could let the bracket wiggle on the beam under the strap load, and over time that movement could wear down the slots. Keeping it at three decimal places keeps the gap within my RC3 limit, so the part can still slide along the beam without extra play. Another place where I used a looser tolerance was the overall length of the bracket, which I held at X.X ± 0.02. This feature does not significantly affect how it mates with the T-beam, the link, or the strap, so the material choice is less critical. The length comes from the given value we determined, but being off by a couple of hundredths will not matter much, since the part's strength isn't affected and it doesn't affect how it slides or fits together. With the looser tolerance, we can cut the part to length and check it with a caliper without any special setup. If we used the tightest tolerance for every dimension, machining time would increase, as would the cost and difficulty of production, so it would not improve anything.

### 2157 Reflections

The biggest thing I learned is that the link cannot be sized on its own. It has to be built around a feature on the bracket, so I based the whole size on feature A and assumed it could not be adjusted. Then I applied my RC6 fit that way, so there is always clearance between the two parts even if the hole comes out small within its tolerance. It will still work the same way and slide, but not let the parts go too far either way. If I had matched the hole to feature A exactly, the parts might not fit together and would need to be press-fit. I also learned how to apply different fits, because different parts require different fits and clearances to rotate or to have a slight interference fit, since the connection is not supposed to move in some scenarios. My mistake with feature B also showed me why you have to check compatibility early. Feature B was originally too short for the cross-section of feature A, the link, and the strap. Each part looked fine on its own with the numbers I calculated, but they would never have worked together. I thought of ways to make it work, but I ended up changing one variable in the equation to get a different answer, and now I have to rework it by hand. If material choice affects the fit, I need to account for it earlier too.

When it comes to dimensions and tolerances, they tell machinists what matters in the design without needing lots of words on the drawings. Tolerances and callouts are applied to surfaces that mate with other parts, such as the slots or the T-beam, while features that don't contact anything are left looser to make machining easier. The fit codes also show the functional requirements directly. An RC fit indicates that parts need to move relative to each other, and an FN fit indicates that the parts need to stay locked together. The interface on the link drawing makes it clear which surfaces must align between the link and the bracket, but overall I learned that a drawing is more than just a picture of the part. It shows how the part needs to be made, including how the choice of material can affect the fit.

### Mistakes 

One mistake from the first part of the assignment in A5 that I needed to address was that feature B was too short to fit the cross-section of feature A. I went back to my calculations and decided to set a specific height rather than a specific thickness, so that feature A's cross-section would fit with the link and the strap. I set the height of feature B to 1 inch, which automatically updated the thickness of feature B in the SolidWorks equation to the correct value according to the changed parameter

Another mistake I noticed while reviewing my calculations for my link for a 5 is that I used the wrong forces in both equations. For the stress calculation, I should have used 750 lbf instead of 1500 lbf as the applied force. For my deflection calculation, where I had 1500 written down for my total F, I may have mistaken it for 1200 lbf. If it were 1200/2, it would be 600, and 600 is what I wrote down for the applied force in the deflection calculation, but it should be 750 lbf. So I plugged those into my parametric equation for my length design, got the new values, and used those for my design. The final values should have been 750 lbf for both the stress and deflection calculations.

### Time Spent

I spent a total of 10 hours on this assignment, which I felt was a bit quicker than I expected, and I feel I put a quality effort into it.

## Appendix

[A6 Downloads Folder(4 Items)](https://drive.google.com/drive/folders/1YsM7HtLYIG-uyTXa7ah0Mi5yEQOvlUZQ?usp=sharing)
