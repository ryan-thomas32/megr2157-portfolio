# A2 – Truss Stress Analysis

## Objective
For this assignment, we were tasked with designing a lightweight basic truss out of A500 steel that would meet the design constraints below.

<img width="600" height="262" alt="643664648-39cb4bb8-64b9-476e-9e04-75f2db54fd79" src="https://github.com/user-attachments/assets/4acb32b4-0775-4a2a-9e74-8f801831636e" />

At point A we have a pin, and at point B we have a Roller. The distances for a are each 0.4 m, with the vertical measurement for b being 0.3 m. I was given the option of choosing a force P value between 20 kN and 30 kN. I decided to meet in the middle and go with 25 kN for my P value's.

Quick Rundown:  
a=0.4m  
b=0.3m  
P=25kN  

## Decide  
<img width="2556" height="1603" alt="CamScanner 9-3-26 02 51n" src="https://github.com/user-attachments/assets/3f3fe491-8d37-4733-a27d-e8a24b44dc1d" />

#### Introduction

I laid out an initial plan to design a truss system that would be as simple as possible, both in terms of effective use of materials and ease of analysis. In my truss drafting phase, I settled on one main design, which was a Warren-style truss with 9 members and 6 joints. During the planning and brainstorming phase of this assignment, I found this truss style very beneficial, as the inclusion of 90-degree angles makes calculating internal forces within the beams less complex and improves workflow efficiency during the calculations. This design style also makes it easy to include zero-force members, which are useful as a backup within the structure if any of the main load-bearing beams undergo critical failure.

## Analyze 
### Finding Global Equilibrium and Member Internal Forces.
The first step I took was to calculate the global equilibrium. I calculated all the reaction forces on the roller and pin supports of the truss. Then, after calculating the global equilibrium, I began drawing the Free-Body Diagrams for each joint to calculate the internal forces, as we are required to draw each joint for this assignment; it makes the most sense to use the method of sections for this part. Following the instructions, I first performed all these calculations symbolically. For my section on finding the internal forces in the joints, I show the symbolic calculations, where I normally solve the equilibrium equations for each joint, followed by the numerical calculations below. In hindsight, this was not the best choice in hindsight, as it makes the symbolic and numerical calculations hard to distinguish, which I noticed after completing the entire calculation for this part. Below are the calculations I made for this part.
<img width="2136" height="1201" alt="CamScanner 9-3-26 02 52n" src="https://github.com/user-attachments/assets/13056a23-58d5-43d7-8136-25d233f24f92" />
<img width="2368" height="2782" alt="CamScanner 9-3-26 03 20n" src="https://github.com/user-attachments/assets/4e5e6d42-2e00-42c8-bf68-8df13628747e" />
<img width="1968" height="2175" alt="CamScanner 9-3-26 03 21n" src="https://github.com/user-attachments/assets/c5c41532-e25c-43a8-be6e-02e1d409d956" />
<img width="1112" height="1474" alt="CamScanner 9-3-26 03 21n (1)" src="https://github.com/user-attachments/assets/1a5b63c3-18be-426a-a245-7c623e3c5fd0" />

### Cross-Sectional Area and Truss Weight Estimate  
After finding the support reaction forces and internal loads of the beam, I moved on to determining the beam's cross-section again, first symbolically, then numerically. This calculation included information from the last part, which required using the highest internal load to determine the minimum beam area needed to withstand that force with a safety factor of 3.5. I chose to assume the use of grade B A500 steel because after a quick search, I found accessible information on its yield strength and density, which can be found [Here.](https://eaglesteel.com/wp-content/uploads/2025/01/ASTM_A500_Grade_B.pdf) This section was challenging but not impossible to work through, as I am currently taking solids, so a lot of this information is very relevant to what I have been doing. 
<img width="2464" height="3144" alt="CamScanner 9-3-26 03 43n" src="https://github.com/user-attachments/assets/b2969321-0e9e-43c8-8854-d816be233891" />

Based on my calculations, the required area to meet the assignment's specifications is 308.44 mm^2. The weight I estimate for my truss design with this cross-sectional area is 8.959kg.
###  Cross-Sectional Area and Pin Weight Estimate  
After finding the beam's cross-section and approximate weight, I moved on to determining the pin's cross-section again, first symbolically and then numerically. For Ksi, I looked up the conversion factors and then did the calculation manually. For converting lb/in^3 to kg/m^3, I used this calculator: (https://www.unitconverters.net/density/pound-cubic-inch-to-kilogram-cubic-meter.htm). This Section of the Assignment took a lot of time and effort for me, as this material is very new to me, as we have not covered it in our solids class yet. I have a basic understanding of shear force and how it works, which was enough to help me work through the problem. For the Free-Body diagram and pin load calculation, I predicted D would have the highest internal force because so many different forces are pushing and pulling at the point I assumed for the pin. I assumed the highest internal load would equal the maximum load on the pin. The photos below show my calculations for the pin cross-section and diameter, as well as the pins' weight.
<img width="2376" height="3029" alt="CamScanner 9-3-26 04 02n" src="https://github.com/user-attachments/assets/bc156abe-bd7b-412f-9754-7718bb473471" />
<img width="2120" height="1061" alt="CamScanner 9-3-26 04 03n (1)" src="https://github.com/user-attachments/assets/7e8ad896-9db1-4590-863e-fbf15498a91f" />
### CAD Representation  
After completing the calculations above, the next task was to model my truss in CAD software, which I did in SolidWorks 2026. I decided to represent the pin and truss as two separate files. In SolidWorks, I chose AISI 1020 steel to best represent the A500 steel we were tasked with using for the truss, and ended up using AISI Type A2 Tool Steel for the pin, as it was the only tool steel I could find in SolidWorks.
#### Truss Creation
To create my truss, I first drew the outer frame and dimensioned it to the problem specification on the front plane. I then drew a center-point square to create my beam cross-section and used the Swept Boss Base tool to extrude a basic outer frame. Then I drew the inner beam lines inside the pre-created outer frame and used the Swept Boss Base feature again to extrude the bar along the traced line.
<img width="1433" height="632" alt="Screenshot 2026-09-03 005251" src="https://github.com/user-attachments/assets/efded9f9-8ef3-491c-bb72-107c5c8de893" />
<img width="1112" height="877" alt="Screenshot 2026-09-03 011915" src="https://github.com/user-attachments/assets/369e7269-1428-4aeb-b7b8-babccd106ee0" />

After creating my solid truss, I sketched 11 mm-diameter circles at each joint to represent the holes the pins would slide into. For this, I selected the Extruded Cut feature for each hole, cutting to the next face, which easily created the holes in the truss.

<img width="1522" height="937" alt="Screenshot 2026-09-03 021252" src="https://github.com/user-attachments/assets/8f6cd0ff-34cd-4d2b-ae0c-3bfcc156d8d9" />
<img width="1341" height="865" alt="Screenshot 2026-09-03 041641" src="https://github.com/user-attachments/assets/fc941e14-c328-4f0a-b353-28e3b227caae" />

My truss weighs 8.788kg according to the SolidWorks model, which is only about a tenth off from my calculations above. Doing percent error calculations.  
Percent Error = |8.788 − 8.959| / |8.959| × 100%  
Percent Error = 1.909%  
From this percent error, we can confirm and validate our earlier calculations and approximate estimates above. 
#### Pin Creation
To create the pin shown below, we sketched a circle on the front plane with the correct diameter of 11mm and extruded it to the calculated length of 17.6mm.
<img width="1442" height="907" alt="Screenshot 2026-09-03 051952" src="https://github.com/user-attachments/assets/14609251-9ab5-48fb-9ac4-2eb41a1e1a0d" />  
<img width="1093" height="925" alt="Screenshot 2026-09-03 052449" src="https://github.com/user-attachments/assets/6fa82438-3338-469a-b6f8-2e073d9fbd3a" />
Solving for Percent Error  
Percent Error = |0.0789 − 0.077| / 0.077 × 100%   
Percent Error = 2.468%  
Like the truss percent error, this is an acceptable percent error for an assignment like this; it ensures my calculations are correct and validates my data and calculations for the pin.
### Lessons
The lessons I learned from this assignment include many things like going about brainstorming out different designs going through the validation and deciding which one to push through with and in addition with thgat learning how to calculate all the internal forces, the minimum areas, The shear forces in the pin Are all very helpful lessons I learned throughout this assignment there's multiple things from this assignment that I will be able to take and learn to apply to my future classes or am taking currently. It was also a good refresher for Solidworks as I haven't used in over a year It was also a good assignment for teaching me how to think out of the box and think of different ways to make the equations work for the problems and crossing it with solid works to validate your answers was very helpful and gives you a lot of confidence as an engineer to see your work done right.



## Communicate

