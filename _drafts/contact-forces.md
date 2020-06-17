---
layout: post
title: How to compute contact forces?

---
A few days ago, I noticed that I know numerics for differential equations with equallity constraints, like

$$  
m \ddot x = f(x) - \lambda \frac{\partial g}{\partial x} \quad \text{with} \quad g(x) = 0,  
$$

however, I had no clue how to deal with inequallity constraints like

$$  
\quad c(x) \leq 0
$$

in this context. Let's dive into it.

## The physics of contact forces

Contact forces appear naturally between rigid bodies.

There are two components:
- the contact force in **normal** direction $$f_N$$,
- contact force in **tangential** direction, also called kinetic contact force $$f_T$$.

The force in normal direction is essential, since 


