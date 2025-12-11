---
layout: project
title: Torque Wrench
description: MAE 3270 Final project 
technologies: [Autodesk Fusion]
image: /assets/images/pfp_torque wrench.jpg
---

For MAE 3270 Final Project, This assignment pulled together several topics such as materials seletion, fracture, fatigue, strain gauges, stress analysis, and finite element analysis. Given a basic elements for dimensions, I designed a torque wrench.

The objective of this project was to design a non-ratcheting, 3/8 inch drive instrucmented torque wrench rated for 600in-lbf. A bare bones geometry was given and a basic hand calculation for the design was performed through Python. 

![Shaded rendering of earlier version]({{ "/assets/images/full_torque wrench.png" | relative_url }}){: .inline-image-r style="width: 400px"}

The requirements for the design was the following:
- attain at least 1.0 mV/V output at the rated torque of 600 in-lbf.
- safety factor of Xo = 4 for yield or brittle failure (you pick which criterion based on
whether you are using a brittle or ductile material)
- safety factor of XK = 2 for crack growth from an assumed crack of depth 0.04 inches
(1 mm).
- fatigue stress safety factor of XS = 1.5.
- material must be a steel, aluminum or titanium alloy

The dimensions are included in the following pictures:
 
![Shaded rendering of earlier version]({{ "/assets/images/top pfp_torque wrench.png" | relative_url }}){: .inline-image-r style="width: 500px"}

![Shaded rendering of earlier version]({{ "/assets/images/side pfp_torque wrench.png" | relative_url }}){: .inline-image-l style="width: 150px"}

<br><br><br><br><br><br><br><br>
Following are the relevent properties of Ti-6Al-4V that were used in the project.

Modulus of Elasticity: E = 16.7E6  psi
<br>Poisson’s Ratio: = 0.349
<br>Tensile Yield Strength: y = 126E6 psi
<br>Fracture Toughness: KIC = 94.2E3 psi-in^1/2
<br>Fatigue Strength for 107 Cycles: f' = 92E3 psi

Diagram communicating how loads and boundary conditions were applied to my FEM model

![Shaded rendering of earlier version]({{ "/assets/images/boundary condition.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Normal strain contours (in the strain gauge direction) from FEM

![Shaded rendering of earlier version]({{ "/assets/images/normal elastic strain.png" | relative_url }}){: .inline-image-c style="width: 500px"}

Contour plot of maximum principal stress from FEM

![Shaded rendering of earlier version]({{ "/assets/images/max principal stress.png" | relative_url }}){: .inline-image-c style="width: 500px"}


<br><br>Summary of FEM calculations:

max = 10,713 psi
<br>Strain @ Gauge = 956.37 microstrain
<br>Load Point  = 0.0743 in

Torque wrench sensitivity: 0.956 mV/V

Unfortunetly, the FEM analysis results were different from the expected value of an output that was calculated to meet one of the design requirements where the output should be at least 1 mV/V.

Selected Strain Gauge: SGD-2/350-LY11
<br>Carrier Length: 7.6mm
<br>Carrier Width: 5.8mm
<br>Grid Width: 2.5mm
<br>Grid Length: 2mm





