# A3 – Parametric Design & FEA Analysis

## Objective
The objectives of this assignment were to design a solid circular cross-section aluminum beam with a Young's modulus between 8.5-11.5 x 10^6 psi under an applied distributed load on the end of the bar between 300lbf and 500 lbf. After selecting a cross-sectional dimension, we need to use parametric design concepts to determine the minimum bar length, since the instructions and design limitations require that the maximum axial deflection be 0.009 inches. Here is a basic diagram of the objective below.<img width="458" height="55" alt="download" src="https://github.com/user-attachments/assets/450a0c18-4750-4ee0-936b-c2879ee9753a" />

After designing the Bar with all its dimensions, we need to model it in CAD and then run an FEA simulation to verify our findings.

## Analyze
#### Applied Force, Aluminum, and Dimension Selection
For deciding the chosen dimensions for my bar, I took an engineer's approach to this by asking one of my friends overseas for a value for the force being applied, then followed that up with asking one of my parent for a goal diameter for my bar, and then finally having my uncle choose an aluminum type that fits the requirements of the assignment. The goal of my trying this is to challenge myself further and, most importantly, to simulate the requirements a consumer or customer would set for a product. The results of this gave me a Force of 372lbf being applied to the end of the bar, a chosen diameter of 3 3/8" or 3.375", and finally a chosen aluminum type, which is 3003 H12, with a Young's modulus value of around 10.0 x 10^6 psi seen below, but for the calculations of this assignment, I will use the full Young's modulus including each digit, to keep my percent error and calculations as accurate as possible.

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

<img width="757" height="400" alt="CamScanner 9-9-26 23 46n" src="https://github.com/user-attachments/assets/2e7cbc65-a9ac-4217-bdef-3d8549e5cf6b" />

#### Adjusting Direct Tension Elongation Equation to find Length(L)

Now that we have each variable except the length, we can rearrange the Direct Tension Elongation Equation to find L, which will be the maximum length for our bar, as anything shorter would yield a deflection of less than .009 inch. After that, I continued calculating the length by plugging in all the variables. Doing this, I was able to calculate a Length of:

L = 2166.043195"

<img width="1818" height="652" alt="CamScanner 9-9-26 23 46n1" src="https://github.com/user-attachments/assets/ac29ff07-e322-4d4c-b1ca-9d334c0398dd" />


This was an interesting answer. I initially went back through my work and did not see any glaring errors, so I decided to trust my value for the moment, as it would be cleared up in the next step.

### Solidworks
#### Part Creation
After my calculation, I followed up in SolidWorks using the instructions

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

When it comes to deflection, we have the given maximum axial deflection of .009" and the FEA value in SolidWorks of .009078". When rounded to the same digits as the given value, the FEA result also reads .009", which would make the percent change look like it'd be 0%,  but carrying the full FEA number and digits instead gives:

(.009078 − .009) / .009 × 100 = 0.87%

<img width="715" height="491" alt="Screenshot 2026-09-09 175358" src="https://github.com/user-attachments/assets/ecf99e55-6cc8-42f1-a972-4bb0e1d9671e" />


This was my goal: not to round any digits throughout my calculation, in an attempt to keep the percent change to the SolidWorks calculation as minimal as possible; in engineering, small differences can have extreme consequences in certain applications.

#### Pin Hole Stress Concentration Calculations
Imagining a substantial pinhole in the side of my bar, I first used the machinery handbook to find that the stress concentration factor Kt for a flat bar in tension is:

Kt = 3

Then, following the finding of the stress concentration, I created the equation to be used to calculate the peak stress at the hole, which is included in my calculation below

Using these calculations, I found a maximum stress of 132.33 psi (0.13233 ksi) at the hole. This is about 3 times higher than the previous stress, which makes sense since our stress concentration is 3. In line with this finding, I also found my new safety factor, including the pinhole, to be 302, about a third of the previous safety factor of 907. This safety factor is still high; the design is viable for the objective required but is not nearly as optimized as it realistically should be.

<img width="1775" height="777" alt="CamScanner 9-9-26 18 25n" src="https://github.com/user-attachments/assets/d3488ce2-371f-4f54-abf9-12e7a906c14c" />

### 2157 Additional Analysis

#### Design Parameter Alterations
Following the calculations for our original bar above, we need to change each of the design parameters we chose for our first bar, including Load and cross-sectional dimensions, while keeping our aluminum type, fixture, and max axial deflection constant for both bars. I went searching around in public again, trying to find more fluid, non-preselected values to challenge myself.

Original Dimensions:
F = 372 lbf

d = 3.375"

E = 10007603.9 psi (Constant)

max axial deflection = .009" (Constant)


New Altered Dimensions:  

F = 300 lbf

d = 27.000"

E = 10007603.9 psi (Constant)

max axial deflection = .009" (Constant)

Based on these alterations, I believe the bar's overall length will increase significantly. As I mentioned before, with the surprising length of my first bar, I figured out and realized that the chosen area is so large that it will make the bar extremely long relative to the diameter and area, as the constant .009" limit for axial deflection does not scale with the dimensions of the bar, leaving me to theorize this throughout my work on this assignment.

For this calculation, we must again find the new cross-sectional area of the bar, then find the length using the equation we used before.

##### Alteration Hand Calculations
<img width="550" height="465" alt="CamScanner 9-9-26 23 34n" src="https://github.com/user-attachments/assets/3a3294d1-b718-44c4-ba27-8276a130288b" />

My assumption that the length would significantly increase was correct; the length increased by just below 80 times, and doing an additional quick head calculation to find ratios for diameter to length using the equation:

d/d : L/d

For both the original and the altered bar, I calculated the ratios, rounding to the next whole number, yielding 1:642 for the original and 1:6367 for the altered. This, I believe, is because, with so much area added, the bar must be much longer to achieve the required deflection.

#### Altered Bar Modeling and FEA in SolidWorks
After finding all the hand calculations, I created the new altered bar in SolidWorks using the same process I used to create my original bar. I ran into trouble because the length exceeded SolidWorks' limit, so I divided the diameter, force, and length by 6 to see whether it would yield the same result. After doing this, the numbers I got met the required limitations and supported my hypothesis.
Von Mises Map:
<img width="1508" height="822" alt="Screenshot 2026-09-10 012022" src="https://github.com/user-attachments/assets/c64584e6-2eb9-4c67-9b01-c552eb8b96be" />

Deflection/ Displacement Map(Scaled Up):

<img width="1490" height="703" alt="Screenshot 2026-09-10 011948" src="https://github.com/user-attachments/assets/871351fb-d02b-4508-8dbc-a16003bf377f" />


Using the Probe tool in my stress analysis, I found the Max Stress value and location, as shown in the attachment below.

<img width="946" height="642" alt="Screenshot 2026-09-10 012820" src="https://github.com/user-attachments/assets/615223e4-58d9-467b-ba17-bee783181b3f" />

According to my FEA simulation, the maximum stress is 3.274 psi (0.003274 ksi). This differs from what you would get with a hand calculation using the full-sized altered bar, which  yields a max stress of 0.524 psi (0.000524 ksi). This is even below the 40 ksi limit for Aluminum strength we found for our original bar.  
We can use both these values to find the safety factor with a quick calculation:

SF = 40 ksi / 0.003274 ksi = 12218 (Scaled Down Altered Bar)
SF = 40 ksi / 0.000524 ksi = 76336 (Full Size Altered Bar)

Both designs are very overdone based on the calculated safety factors. Still, even after scaling down to fit SolidWorks dimensions, the scaled-down bar does just as good a job as the full-size one at conveying what changed within the bar, such as the change in safety factor. One thing I notice is that the bigger the radius, the higher the safety factor throughout these beams, which makes me think I set my diameters way too high for this assignment.


## Communicate
### Lessons Learned and Review
The lessons I took from this assignment were key to becoming an engineer in the future. This was my first experience with FEA in SolidWorks CAD, programming global variables, and using a parametric design process. I see how this could be used in future tasks to improve workflow efficiency and reduce the time required to design and create parts. Throughout this assignment, I learned that sometimes you have to trust the answers, even when they seem incorrect at first. It took me around 8 1/2 hours to complete this assignment, and I split it up into several parts. This helped keep my mind on the right thing, but it also added time that could have been saved. Throughout the process, I also noticed a lack of detail in the documentation toward the end. I covered it back over to keep it consistent throughout my assignment.

## Appendix
[A3 Bar Solidworks Download](https://drive.google.com/file/d/1Qwii7tmqtb_z3lScQhf5fDMD6sxlzVTP/view?usp=sharing)  
[A3 Altered Bar Solidworks Download](https://drive.google.com/file/d/1OqFnuj-HjXRrHFQMzbUO9Czwrn8FKplh/view?usp=sharing)  
[A3 Bar Full Calculations Page](https://drive.google.com/file/d/1KOsLIL7nLaxN8topsVv0RCSaw7iOyg9J/view?usp=sharing)
