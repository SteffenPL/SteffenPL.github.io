---
layout: post
title: How to compute contact forces?

---
A few days ago, I noticed that I know numerics for differential equations with equallity constraints, like

$$  
m \\ddot x = f(x) - \\lambda \\frac{\\partial g}{\\partial x} \\quad \\text{with} \\quad g(x) = 0,  
$$

however, I had no clue how to deal with inequallity constraints like

$$  
\\quad c(x) \\geq 0
$$

in this context. Let's dive into it.

### The physics of contact forces

Contact forces appear naturally between rigid bodies.

There are two components:

* the contact force in **normal** direction $$f_N$$,
* contact force in **tangential** direction, also called kinetic contact force $$f_T$$.

#### Normal forces via Lagrangian multipliers

The force in normal direction is essential to avoid that two rigid bodies overlap.

We choose $$c(x)$$ such that the non-overlapping condition
reads

$$
c(x) \\geq 0.
$$

We can think of $$c(x)$$ as the distance to a forbidden region.

The normal force is then given by
$$
f_N = \\lambda \\frac{\\partial c}{\\partial x}.
$$

But we do not know it's strength! Our next goal is to find equiations for the multiplier $$\\lambda$$!

If there is no overlap, we don't want any contact forces which means $$\\lambda = 0$$. Easy.

If there is an overlap in configuration $$x$$, then $$\\frac{\\partial g}{\\partial x}$$ points out of this overlap.
The Lagrangian multiplier must be positive $$\\lambda > 0$$.

$$ \\lambda \\geq 0 \\quad \\text{and} \\quad \\lambda \\cdot c(x) = 0$$.

The trick is

#### Tangential forces (brief)