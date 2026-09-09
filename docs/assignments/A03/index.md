# A3 – Parametric Design & FEA Analysis

## Objective
The objectives of this assignment were to design a solid circular cross-section aluminum beam with a Young's modulus between 8.5-11.5 x 10^6 psi under an applied distributed load on the end of the bar between 300lbf and 500 lbf. After selecting a self-selected cross-sectional dimension, we need to use parametric design concepts to determine the bars' minimum length, as the instructions and design limitations state that the maximum axial deflection must be 0.009 inches. Here is a basic diagram of the objective below.<img width="458" height="55" alt="download" src="https://github.com/user-attachments/assets/450a0c18-4750-4ee0-936b-c2879ee9753a" />

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

L = 2166.043195in 

This was an interesting answer. I initially went back through my work and did not see any glaring errors, so I decided to trust my value for the moment, as it would be cleared up in the next step.

### Solidworks
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


 









 



## Decide


## Communicate

