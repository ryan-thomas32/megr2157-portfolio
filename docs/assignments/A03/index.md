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

After listing our Direct tension elongation equation, we next need to solve for the cross-sectional area of the beam. Here, I again did not round any digits, and I calculated the Bar Area to be:

A = 8.946175955 in^2

#### Adjusting Direct Tension Elongation Equation to find Length(L)

Now that we have each variable except the length, we can rearrange the Direct Tension Elongation Equation to find L, which will be the minimum length required for our bar.


 



## Decide


## Communicate

