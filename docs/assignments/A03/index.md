# A3 – Parametric Design & FEA Analysis

## Objective
The objectives of this assignment were to design a solid circular cross-section aluminum beam with a Young's modulus between 8.5-11.5 x 10^6 psi under an applied distributed load on the end of the bar between 300lbf and 500 lbf. After selecting a cross-sectional dimension, we need to use parametric design concepts to determine the minimum bar length, since the instructions and design limitations require that the maximum axial deflection be 0.009 inches. Here is a basic diagram of the objective below.<img width="458" height="55" alt="download" src="https://github.com/user-attachments/assets/450a0c18-4750-4ee0-936b-c2879ee9753a" />

After designing the Bar with all its dimensions, we need to create and analyze it in CAD, then run an FEA simulation to verify our final findings.

## Analyze
#### Applied Force, Aluminum, and Dimension Selection
For deciding the chosen dimensions for my bar, I took an engineer's approach to this by asking one of my friends overseas for a value for the force being applied, then followed that up with asking one of my parent for a goal diameter for my bar, and then finally having my uncle choose an aluminum type that fits the requirements of the assignment. The goal of my trying this is to challenge myself and, most importantly, to simulate the requirements a consumer or customer would set for a product. The results of this gave me a Force of 372lbf being applied to the end of the bar, a chosen diameter of 3 3/8" or 3.375", and finally a chosen aluminum type, which is 3003 H12, with a Young's modulus value of around 10.0 x 10^6 psi seen below, but for the calculations of this assignment, I will use the full Young's modulus including each digit, to keep my percent error and calculations as accurate as possible.

<img width="660" height="530" alt="Screenshot 2026-09-08 163115" src="https://github.com/user-attachments/assets/cb37bcb6-1829-47e6-991e-baea442f0a01" />

### Calculations
#### Listing Chosen Variables & Diagrams
I first started out by listing my chosen dimensions at the top of the page, listing out my F, d, and E variables with their respective values:

F = 372 lbf

d = 3.375"

E = 10007603.9 psi

I then followed that part up by drawing out diagrams of the front and side views of the bar I have created for ease of understanding for a viewer of my assignment and for quick reference during my calculations if needed, labeling them according to their view:

Bar Diagram (Front View), Cross Section (Right View)

<img width="1686" height="718" alt="CamScanner 9-8-26 16 56n" src="https://github.com/user-attachments/assets/30e27de9-6f97-4ebf-a9a5-a0af62c5e342" />

After drawing out and representing my problem for better comprehension and understanding. I then listed the final variable given:

max axial deflection = .009"

#### Direct Tension Elongation Equation

Next, I included the direct tension elongation equation from the machinery handbook, with an adjustment made to include my listed variables:

<img width="1524" height="735" alt="CamScanner 9-8-26 17 06n" src="https://github.com/user-attachments/assets/65ab1426-3335-4e82-b84a-4e83c416a7c8" />

#### Finding Bar Area

After listing our direct tension-elongation equation, we next need to solve for the beam's cross-sectional area. Here, I again did not round any digits, and I calculated the Bar Area to be:

A = 8.946175955 in^2

#### Adjusting Direct Tension Elongation Equation to find Length(L)

Now that we have each variable except the length, we can rearrange the Direct Tension Elongation Equation to find L, which will be the maximum length for our bar, as anything shorter would yield a deflection of less than .009 inch. After that, I continued calculating the length by plugging in all the variables. Doing this, I was able to calculate a Length of:

L = 2166.043195"

This was an interesting answer. I initially went back through my work and did not see any glaring errors, so I decided to trust my value for the moment, as it would be cleared up in the next step.

### Solidworks
#### Part Creation
After my calculation, I followed up in SolidWorks, following the instructions
I set and defined all my equations and variables from my hand calculations in the global equations tab and got the same result for the length as before
<img width="921" height="416" alt="Screenshot 2026-09-08 175116" src="https://github.com/user-attachments/assets/c70332e3-7de1-465e-9bc7-8bce448ca07a" />

Once the equations section was complete, I drew a circle on the right plane and dimensioned it to the diameter defined in the global equations tab.

<img width="807" height="690" alt="Screenshot 2026-09-08 203038" src="https://github.com/user-attachments/assets/5f4f5283-74d1-45ce-a6e8-4f5b3996e4b5" />

Following that, I extruded the circle, setting the bar's extrusion length to the L variable I found in my calculations and in the global equations tab.

<img width="1261" height="857" alt="Screenshot 2026-09-08 184357" src="https://github.com/user-attachments/assets/0a706168-7d71-4163-ab73-2a6f7a00107c" />

Then I applied a force to the surface at the end of the bar using the simulation tools, and I also fixed the bar on the left face to represent the bar being fixed to a rigid wall in SolidWorks.

Adding Force to the Right Face
<img width="1278" height="726" alt="Screenshot 2026-09-08 174021" src="https://github.com/user-attachments/assets/bb20d18e-a3f7-4170-bfbe-97d141fe745f" />

Adding Fixture to the Left Face
<img width="1312" height="827" alt="Screenshot 2026-09-08 174154" src="https://github.com/user-attachments/assets/e07e571c-04a4-4b4c-9750-d4dca60f2fcf" />

#### Bar Views

Front View:

<img width="1652" height="631" alt="Screenshot 2026-09-08 202839" src="https://github.com/user-attachments/assets/34bba638-d78d-43a7-939a-45f790cd1217" />


Right View:

<img width="763" height="462" alt="Screenshot 2026-09-08 203043" src="https://github.com/user-attachments/assets/cefba663-0383-41cf-a3a8-beea150de486" />

#### Finite Element Analysis
 After assigning the fixtures and the Forces to the Bar, I then created a mesh and began running my simulations

 Von Mises Map:

 <img width="1345" height="757" alt="Screenshot 2026-09-08 200726" src="https://github.com/user-attachments/assets/73be17c0-8238-40f1-a7b7-fcbe36f2f3c2" />

 Deflection/ Displacement Map:

 <img width="1521" height="827" alt="Screenshot 2026-09-08 200803" src="https://github.com/user-attachments/assets/f588067d-b7c3-48dc-b099-a793f1ee71de" />


Using the Probe tool in my stress analysis, I found the Max Stress value and location, as shown in the attachment below.

<img width="1242" height="786" alt="Screenshot 2026-09-08 210613" src="https://github.com/user-attachments/assets/0926bc23-ba54-4637-83ae-27bdb1af9431" />


According to my FEA simulation, the maximum stress is 44.11 psi, which converts to 0.04411 ksi. This is significantly below the 40 ksi limit for Aluminum strength.  
We can also find the safety factor with a quick calculation:

SF = 40 ksi / 0.04411 ksi = 907

This is a very large safety factor I calculated, which surprised me and, once again, prompted me to review my calculations for errors, though I found none. All my units are converted correctly. This is a good example for me of how, in the future, I should get much closer to the safety factor and leave less leeway than is represented here.
### Design Reflection
#### Percent Difference Calculations
I assumed this part of the assignment referred to length rather than deflection, but I solved and calculated both just to be sure. Deflection is given within the parameters of the assignment: "The max axial deflection of the bar is .009 inches.", and remains constant, which means, in theory, its percent change must automatically be zero.

From the hand calculations, I obtained a length of 2166.043195", which, when rounded down to the 2nd decimal place, matches the result from the global equation. In SolidWorks, the length is 2166.04", indicating that the hand calculation and the FEA percent change result in  0% for this section.

When it comes down to doing this for deflection, using the given maximum axial deflection value for the problem of .009" and FEA in SolidWorks of .009078", which rounded to the same digits as our given maximum axial deflection, gives .009" also, which means the percent change will again be 0% for this example.

<img width="715" height="491" alt="Screenshot 2026-09-09 175358" src="https://github.com/user-attachments/assets/ecf99e55-6cc8-42f1-a972-4bb0e1d9671e" />


This was my goal: not to round any digits throughout my calculation, as I was trying to keep the percent change to the SolidWorks calculation as minimal as possible; in engineering, small differences can have extreme consequences in certain applications.

#### Pin Hole Stress Concentration Calculations
Imagining a substantial pinhole in the side of my bar, I first used the machinery handbook to find that the stress concentration factor Kt for a flat bar in tension is:

Kt = 3

Then, following the finding of the stress concentration, I created the equation to be used to calculate the peak stress at the hole, which is included in my calculation below

Using these calculations, I found a maximum stress of 132.33 psi (0.13233 ksi) at the hole. This is about 3 times higher than the previous stress, which makes sense since our stress concentration is 3. In line with this finding, I also found my new safety factor, including the pinhole, to be 302, about a third of the 907 safety factor I had before. This safety factor is still high; the design is viable for the objective required but is not nearly as optimized as it realistically should be.

IMAGE
















 





## Communicate

