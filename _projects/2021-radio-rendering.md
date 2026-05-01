---
layout: project
title: Stanley Tumbler
description: Consumer Product Reverse Engineering & CAD Modeling
technologies: Fusion 360 
image: /assets/images/stanley cup.jpg
---

I did a reverse-engineering project where I recreated a Stanley tumbler in Fusion 360. Instead of just modeling it, I approached it like a product teardown - trying to understand how the geometry, materials, and assembly decisions support its function.

<br> 
I broke the product into key components: the body, lid, handle, and sipper/straw. Each part serves a distinct purpose such as thermal insulation, structural integrity, fluid containment, and user interaction. 
<br>
The lid and body interface relies on precise tolerancing and a threading to prevent leakage, allowing repeated assembly by the user. I noticed consistent fillets and smooth transitions, which are typical manufacturable designs and are likely driven by metal forming/molding processes. 

![Shaded rendering of earlier version]({{ "/assets/images/lid assembly.png" | relative_url }}){: .inline-image-r style="width: 200px"}
![Shaded rendering of earlier version]({{ "/assets/images/sipper sketch.png" | relative_url }}){: .inline-image-r style="width: 200px"}
![Shaded rendering of earlier version]({{ "/assets/images/sipper lift.png" | relative_url }}){: .inline-image-r style="width: 200px"}

<br><br><br>
Rendering 
<br>
Body: used stainless steel due to its impact-resistant, non-porous, subtly-reflective nature
<br>
Handle & Lid: used polypropylene due to its high melting point and light weight 
<br>
Sipper/Straw: used silicone due to its flexibility, softness on lips/teeth, and safety in dishwashers 
<br>
Some geometries that look simpler are actually complex to model, which gave me insight into how design intent and manufacturability influences final form. As I was exploring deeper into the tumbler model itself, I realized I missed a huge component: double-wall structure. Known as one of Stanley's selling points, thermal design was a cruicial factor in designing the body, with its internal wall and external wall. On top of the insulation of the tumbler, a ring of silicone around the threading of the lid would have perfectly prevented any leakage. 
<br>
Capturing the geometry of user's product gave me deep insights in designing and manufacturing that designing doesn't always equal efficiency. A products optimization is rooted and developed based on user's experience and preference. Despite Stanley's smooth finish and revolving sipper, I figured optimizing the lid assembly into a simpler straw design to improve ease of cleaning might better consumer's experience. 
<br>
This project helped me shift from just modeling geometry to thinking about why products are designed the way they are - balancing performance, manufacturability, and most importantly, user iteraction.


