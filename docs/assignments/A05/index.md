# A5 – Bracket

## Objective
Our task for this project was to design a bracket to support a rope carrying between 500 and 900 pounds of force; I chose 880 lbf for F via a strap connected to the bracket, with the bracket resting on a T-beam. From there, we take the bracket apart piece by piece to determine the geometry through calculations based on the material, which, in my case, I chose as Titanium (Ti-6Al-V4), and the geometry we know. Using a safety factor of 4, we were given this diagram as the basis for our design.

<img width="453" height="303" alt="image" src="https://github.com/user-attachments/assets/cbd829de-5796-4668-9139-5af7696f1cf9" />

From here, I started by sketching a rough layout for my bracket and listing my material parameters to get a base idea of how I wanted to design each feature.

<img width="785" height="532" alt="image" src="https://github.com/user-attachments/assets/c72fd95c-1725-4994-87b3-ee7eb2b5f291" />

<img width="2276" height="3080" alt="CamScanner 9-24-26 00 37n" src="https://github.com/user-attachments/assets/835cf2ca-0dc2-47ef-9f3d-bf83aabb210a" />

## Analyze

### Calculating Dimensions from Stress Analysis

#### Feature A: Stress Analysis Calculations

<img width="2096" height="2704" alt="CamScanner 9-24-26 05 22n" src="https://github.com/user-attachments/assets/d2d27404-5f19-4e22-8065-8bd68fac80ec" />

#### Feature B: Stress Analysis Calculations

<img width="2348" height="2948" alt="CamScanner 9-24-26 05 22(1)n" src="https://github.com/user-attachments/assets/3e9cfc26-f1f9-4695-8861-32292cb63775" />

#### Feature C: Stress Analysis Calculations

<img width="2280" height="2860" alt="CamScanner 9-24-26 05 23n" src="https://github.com/user-attachments/assets/fe97358f-ba7b-42f0-9a91-f87454c758e2" />

#### Feature D: Stress Analysis Calculations

<img width="2212" height="2764" alt="CamScanner 9-24-26 05 23(1)n" src="https://github.com/user-attachments/assets/266a148d-3700-450e-aeed-bd6d69604a4c" />

#### Feature E: Stress Analysis Calculations

<img width="2396" height="2980" alt="CamScanner 9-24-26 05 24n" src="https://github.com/user-attachments/assets/7d7dfa96-1fd0-4fec-b82c-a8c95cf6a59b" />

### Calculating Dimensions from Deflection Analysis

This section details the symbolic formulas and numeric calculations used to determine necessary bracket dimensions based on a maximum deflection of .005".

#### Feature A: Deflection Analysis Calculations

<img width="2308" height="2988" alt="CamScanner 9-24-26 05 26n" src="https://github.com/user-attachments/assets/c85fa3d1-3456-42b0-8d49-3d4fb083050e" />

#### Feature B: Deflection Analysis Calculations

<img width="2004" height="2536" alt="CamScanner 9-24-26 05 26(1)n" src="https://github.com/user-attachments/assets/16f264e8-7d17-4238-9484-9e4d254e33b3" />

I think there has to be a mistake here somewhere. Spent 30 minutes to an hour retrying the number and trying different things, to no avail, so I just decided to let it ride.

#### Feature C: Deflection Analysis Calculations

<img width="1996" height="2448" alt="CamScanner 9-24-26 05 26(2)n" src="https://github.com/user-attachments/assets/84a5f590-ab25-43f3-8569-f9f7135b1c45" />

#### Feature D: Deflection Analysis Calculations

<img width="1744" height="2248" alt="CamScanner 9-24-26 05 27n" src="https://github.com/user-attachments/assets/e4b65b5c-2b29-4121-9284-91c25c38665e" />

#### Feature E: Deflection Analysis Calculations

<img width="1948" height="2460" alt="CamScanner 9-24-26 05 27(1)n" src="https://github.com/user-attachments/assets/33d54441-f1ea-4cb9-9197-ff72aa1a1c6e" />

## 2157 Addition
#### Task
"Design a link (Appendix E) that connects feature A to another cylindrical feature, such that the connection can hold using the same amount of force. The link is to be made from one of the three specified metals."

### Linkage Design Calculations

<img width="2208" height="2808" alt="CamScanner 9-24-26 06 14n" src="https://github.com/user-attachments/assets/60af7f20-1819-4450-ba6d-0fdce86369af" />

### .730" Hole Callout:
Based on these specifications, which require a running sliding fit for feature A, I have assumed that an RC6 fit is adequate for the job at hand. An RC6 fit dictates that the .730" diameter hole of the linkage must lie within a tolerance of +.002", -.000". Feature A, which interfaces with this hole, must be .730" and lie within a tolerance of −.0016" to −.0028" (.7272"–.7284"). This provides a clearance of 0.0016" to 0.0048". The RC6 hole can be manufactured by reaming.

<img width="1097" height="468" alt="image" src="https://github.com/user-attachments/assets/484d755f-6051-47c1-91a8-bf79da50511a" />
 Machinery's Handbook pg. 654

### 1.000" Hole Callout
Based on these specifications, which require a light assembly pressure fit for feature A, I have assumed that an FN1 (light drive) fit is adequate for the job at hand. An FN1 fit dictates that the 1.000" diameter hole of the linkage must lie within a tolerance of +.0005", −.000" (1.0000"–1.0005"). Feature A, which interfaces with this hole, must be 1.000" and lie within a tolerance of +.0008" to +.0012" (1.0008"–1.0012"). This provides an interference of 0.0003" to 0.0012". The FN1 hole is an H6 tolerance, so it requires precision reaming.
 <img width="525" height="40" alt="image" src="https://github.com/user-attachments/assets/6fa00427-0cb9-44f8-b913-2904b5d9f626" />
  Machinery's Handbook pg. 658

## Decide


## Communicate

