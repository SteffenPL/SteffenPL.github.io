---
layout: post
title: Contact forces

---
A few days ago, I noticed that I know numerics for differential equations with equallity constraints, like

$$  
m \ddot x = f(x) - \lambda \frac{\partial g}{\partial x} \quad \text{with} \quad g(x) = 0,  
$$

but I had no clue how to deal with inequallity constraints

$$  
m \ddot x = f(x) - \lambda \frac{\partial c}{\partial x} \quad \text{with} \quad c(x) \leq 0.
$$


## The physics of contact forces

To start somewhere, let's talk about physics.
