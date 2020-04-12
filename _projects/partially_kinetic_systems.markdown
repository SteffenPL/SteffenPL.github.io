---
layout: page
title: Partially Kinetic Systems
description: Coupling between micro and macro models.
img: /assets/img/partially_kinetic_systems_example.svg
tag: [current]
---

Under the supervision of Bernd Simeon, I investigated mathematical aspects of skeletal muscle models.

The long term aim is to develop geometric numerical methods
for a muscle model which combines the macroscopic scale (muscle tissue as an elastic solid) and the microscopic scale (muscle cells and their cross-bridge cycling).

<div class="center">
    <img class="col three" src="{{ site.baseurl }}/assets/img/discrete_muscle.png">
</div>

It turns out that the mean-field limit provides a rigorous link between various scales. The mean-field limit relates the dynamics of individual actin-myosin cross-bridges [^1] to a transport equation for a statistical ensemble[^2] of cross-bridges.



Currently, we only have rigorous results for the linear case published
and a article with results for the nonlinear case is in progress.

---

[^1]: Actin-myosin filaments are the molecules which pull in muscles
[^2]: The statistical ensemble is described by a probability measure for the cross-bridge positions.
