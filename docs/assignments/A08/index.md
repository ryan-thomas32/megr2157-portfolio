# A8 – Gearbox Design

## Objective:

- Design a gearbox that can be assembled and disassembled.
- Analyze and size input and output shafts for strength.
- Design journal bearings to support shafts.
- Create a gearbox housing with proper clearance and fastening.
- Use parametric CAD modeling to generate a final design.
- Document calculations, sketches, and lessons learned.

For Assignment A8, I designed a single-reduction spur gearbox around the McMaster-Carr pinion and gear. I checked the shafts with hand calculations, sized and selected the journal bearings, sketched a two-piece housing, and built the parts in SolidWorks using global variables.

### Design Requirements (from the assignment)

- **Gear ratio:** 24:9
- **Output gear:** 1.25 in-lbf at 1100 rpm
- **Input (pinion) shaft:** 0.125 in diameter, 1 in long
- **Output (gear) shaft:** 0.25 in diameter, 1 in long
- **Gears:** McMaster-Carr spur gears (pinion 7880K19), press fit on the shafts
- **Shaft bearing fit:** running sliding fit
- **Housing:** two pieces, assembled and disassembled with fasteners

## Analyze: Shafts and Journal Bearings:

### Step 1: Shaft Calculations and Design Alterations:

Both shafts are checked in pure torsion, using AISI 1020 steel (Sy = 50,800 psi). Safety factor is SF = Sy / τ.

#### Input Shaft (Power Transmission):

<img width="1960" height="2524" alt="CamScanner 10-29-26 07 28n_3" src="https://github.com/user-attachments/assets/cc3b0ba1-f23b-4f3d-9db7-364ef1092c98" />

#### Output Shaft (Short Shaft):

<img width="1836" height="2424"

