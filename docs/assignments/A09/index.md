# A9 – Pulleys
## Objective
Design a pulley system to transfer power between two parallel axes separated by a center distance of 4–6 inches. The system must meet the following requirements:

Pulley Diameter: Both pulleys shall have a diameter of 3 inches. - Rotational Speed: Select an operating speed between 1000–2000 rpm. - Belt Tension (Static): Select a belt tension between 4–6 lbf under stationary conditions. - Material: Pulleys may be made from aluminum, ABS, or steel, and may include a groove and shaft diameter of your choosing (within reasonable manufacturing limits). - Safety Factor: The design must satisfy a minimum safety factor of 3.

<img width="295" height="100" alt="image" src="https://github.com/user-attachments/assets/e557e4de-b342-459e-9395-e3dce67f7a3c" />

## Analyze: Belt, Shafts, and Journal Bearings:

For each part, I listed my knowns and unknowns, drew an FBD, solved symbolically, and then solved numerically.

### Step 1: Belt Design:

The belt is sized from the tight-side force F₁, since that side carries the most stress. I used the lecture equations: F₁ + F₂ = 2t, F₁/F₂ = e^(μϴ), P = ωr(F₁ − F₂), and Fc = ρA(ωr)². I assumed μ = 0.4 for polyurethane on aluminum and a wrap angle of ϴ = π, since both pulleys are the same size.

#### Belt Calculations (Knowns/Unknowns, FBD, Symbolic, and Numerical):

<img width="2284" height="2892" alt="CamScanner 11-5-26 07 56n" src="https://github.com/user-attachments/assets/c3003f8c-9d45-4d54-9aed-7bf27d93d272" />


#### Belt Choice:

My minimum belt diameter came out to 0.225 in, so I rounded up to a standard 1/4 in polyurethane round belt. Even with centrifugal force added at 1500 rpm, it holds a safety factor of 3.54. To reach 4 lbf of tension, the belt stretches about 3.5% onto the pulleys, so I need one that is about 20.7 in long unstretched.

<img width="1465" height="733" alt="image" src="https://github.com/user-attachments/assets/51c60334-e5aa-4367-9340-c11167e4dfae" />


### Step 2: Shaft Design:

For the shaft I followed the same workflow. The shaft is checked in pure torsion using τ = Tc/J = 16T/(πD³), with the allowable shear stress set to Ssy / SF.

#### Shaft Calculations (Knowns/Unknowns, FBD, Symbolic, and Numerical):

<img width="2092" height="2540" alt="CamScanner 11-5-26 07 56n (1)" src="https://github.com/user-attachments/assets/38367926-a439-4109-9179-d9cdde6c1a05" />


The minimum diameter was only 0.101 in, but I chose a 1/4 in shaft. A 0.1 in shaft is too thin to hold a pulley hub or press into a bushing, and 1/4 in is a stock size that fits standard bearings.

### Step 3: Journal Bearing Design:

I used the same workflow again for the journal bearing. Each shaft is supported by two bearings with the pulley centered between them, so each bearing carries half of the 8 lbf belt load.

#### Bearing Calculations (Knowns/Unknowns, FBD, Symbolic, and Numerical):

<img width="2368" height="2980" alt="CamScanner 11-5-26 07 59n" src="https://github.com/user-attachments/assets/45aac21d-6c1f-4928-9ab9-0ee0ea8bfe15" />


#### Material Selection:

<img width="636" height="465" alt="image" src="https://github.com/user-attachments/assets/cadfa0be-4ca6-4675-b293-22e2dba99691" />


Each material has to pass three checks: load (P_r = 42.7 psi), surface speed (V = 98.6 fpm), and PV with a safety factor of at least 3.

I chose porous bronze. It has a PV safety factor of  around 12, a load safety factor of around 105, and a speed safety factor of around 15, and it lubricates itself.

## Design: Frame:

<img width="1367" height="248" alt="image" src="https://github.com/user-attachments/assets/882715ec-4876-43fb-ace1-5c3503ba3874" />


<img width="1237" height="602" alt="image" src="https://github.com/user-attachments/assets/793053e2-28ff-4ae6-b469-2115c4ea4da1" />


<img width="1342" height="740" alt="image" src="https://github.com/user-attachments/assets/873266a1-04d7-4ed0-9f15-308cc0e601e9" />

## Lessons Learned:

- I learned to do multiple calculations in the material before I start because I tried to do ABS, which was a mistake, as I could not find any friction coefficient, so I had to restart all my work from the beginning. Because I couldn't find a friction coefficient, I switched to aluminum instead, which had an available friction coefficient to use
- I really learned how pulleys and keys work. Before this week, I had really no clue what the heck we were going over in class, so this time it really gave me a strong understanding of how to use it possibly in the future or on the exam, and it was an interesting concept
- A bearing has to pass load speed and PV separately

## Time:

This assignment took me about 3-4 hours from start to finish.

# Appendix
[A9_Frame_Design](https://drive.google.com/file/d/1axsle3hlkngnl6SjzV4hwrK1DUXhn4xR/view?usp=sharing)
