# A6 – [Topic]

## Analyze

### Reviewing Previous Calculations
I carried all dimensions for this section over from my stress calculations in A5. I chose the stress-based values over the deflection-based ones because stress required larger dimensions in most segments and features, and those dimensions were a better, more accurate fit for my bracket based on a quick run-through.

<img width="2000" height="2600" alt="CamScanner 9-24-26 07 55n" src="https://github.com/user-attachments/assets/0d594c4b-f6f6-4d64-999e-13e3251cdd87" />

### First Attempt – Hard-Coded Dimensions
<!-- Explain why the first equation table wasn't truly parametric -->

![First Attempt](images/equations_v1.png)

### Final Parametric Equation Table
<!-- Explain inputs (F, Sy, E, def, SF, beam dims, clearances) and how each feature is derived -->

![Parametric Table](images/equations_v2.png)

### Linking Variables to Dimensions
<!-- Show dimensions linked to global variables, e.g. "D1@Sketch1" = "tC" -->

![Linked Dimensions](images/linked_dims.png)

### Parametric Test
<!-- Change an input and show that the model updates -->

![Before](images/param_before.png)
![After](images/param_after.png)

---

## Decide

### Governing Criteria
- Feature A: stress governs
- Feature B: stress governs
- Feature C: stress governs
- Feature D: deformation governs
- Feature E: stress governs

### Fit Selection (RC7)
- Beam width (3.000 in): clearance ___ to ___
- Flange width (0.498 in): clearance ___ to ___
- Top thickness (1.000 in): clearance ___ to ___

### Tolerance Block
- X.X ± .02
- X.XX ± .01

### Projection
- Third-angle projection (symbol in title block)

---

## Communicate

### Final Model

![Isometric View](images/model_iso.png)

### Engineering Drawing

![Drawing](images/drawing.png)

[View Drawing PDF](PASTE-LINK-HERE)



## Analyze


## Decide


## Communicate

