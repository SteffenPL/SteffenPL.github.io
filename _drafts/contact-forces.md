---
layout: post
title: Contact forces

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

Contact forces appear naturally between 

