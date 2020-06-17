---
layout: post
title: How to compute contact forces?

---
A few days ago, I noticed that I know numerics for differential equations with equallity constraints, like

$$  
m \ddot x = f(x) - \lambda \frac{\partial g}{\partial x} \quad \text{with} \quad g(x) = 0,  
$$

however, I had no clue how to deal with inequallity constraints like[^3]

$$  
\quad c_i(x) \geq 0
$$

in this context. Let's dive into it.

### The physics of contact forces

Contact forces appear naturally between rigid bodies.

There are two components:

* the contact force in **normal** direction $$f_N$$,
* the kinetic contact force in **tangential** direction $$f_K$$. This force is active if objects slide alongside each other.

#### Normal forces via Lagrangian multipliers

The force in normal direction is essential to avoid that two rigid bodies overlap.
We choose $$c_i(x)$$ such that the non-overlapping condition
reads
$$
c_i(x) \geq 0.
$$
We can think of $$c_i(x)$$ as the distance to a forbidden region.

At a first tought, we might expect the normal force to only depend on the configuration $$x$$ and the velocity $$\dot x$$.
However, if we stack boxes onto each other, the contact forces on the bottom one increases with each new box. This shows that the contact force between two rigid objects is not a local property but depends on all contacts! [^2]

<img class="col three" src="{{ site.baseurl }}/assets/boxes.png"/>

The forces are as big as needed to ensure that all constraints are satisfied.
If there is more pressure from other boxes, also the normal contact forces will increase.
As in fluid mechanics, pressure is a Lagrangian multiplier.

Using multipliers, the normal force takes the form

$$
f_{N,i} = \lambda_i \frac{\partial c_i}{\partial x}.
$$

But we do not know the value of the multipliers $$\lambda_i$$ yet! 
Our next goal is to find equiations for $$\lambda$$!
- If there is no overlap, we don't want any contact forces which means $$\lambda_i = 0$$. The multiplier is inactive.
- If there is an overlap in configuration $$x$$, then $$\frac{\partial g}{\partial x}$$ points out of this overlap. The Lagrangian multiplier must be positive $$\lambda_i > 0$$.

In summary, we have

$$ \lambda_i \geq 0 \quad \text{and} \quad \lambda_i \cdot c_i(x) = 0$$.

- The first condition is called the dual feasibility, since it makes sure that the multiplier push into the feasible region.  
- The second condition is a complementary slackness conditions, which ensures that the normal forces are only non-zero at the moment of contact. [^1]

#### Static case.

In the static case, we can make explicit computations. If $$f(x)$$ denotes the forces acting on our system, we have to solve
 
$$
0 = f(x) + \sum_i \lambda_i \frac{\partial c_i}{\partial x} 
$$ <br/>
$$ \lambda_i \geq 0 $$ <br/>
$$ \lambda_i \cdot c_i(x) = 0 $$ <br/>
$$ c_i(x) \geq 0 $$

It is a good excercise to solve these equations for the example of stacked boxes from above.

#### Equations of motion with frictionless contact forces

In a nutshell, the equations of motion are
$$
m \ddot x = f(x) + \sum_i \lambda_i \frac{\partial c_i}{\partial x} 
$$ <br/>
$$ \lambda_i \geq 0 $$ <br/>
$$ \lambda_i \cdot c_i(x) = 0 $$ <br/>
$$ c_i(x) \geq 0 $$

For a fixed state $$x$$ at time $$t$$, we can determine the set of active multipliers $$J_{active}$$ by the condition $$c_j(x) = 0$$ for $$j \in J_{active}$$
and solve the corresponding nonlinear system. However, it is important to take the force balance into account to obtain a closed set of equations. The numerical implementation requires some extra thoughts and will be subject for another post!

Here is a small teaser:

<img class="col two" src="{{ site.baseurl }}/assets/3_spheres.gif"/>

#### Coulomb friction model for kinetic forces (= tangential forces) 

Our model so far has not tangential forces. Hence, objects slide along each other.
Since I am not interested in tangential forces for my particular application, I just read the basics.

Modelling friction in detail is a very difficult tasks. In most cases, only simplified friction models are used, such a the Coulomb friction model.
It asserts a **bounded** ration between tangetial and normal forces
 
$$
\Vert f_K \Vert \leq \mu_k \Vert f_N \Vert.
$$

The direction of the tangential friction is opposite to the slipping direction.
One possible choice is to assume equallity in the above friction law.

I'm lazy... for more details, I just refer to 
[https://en.wikipedia.org/wiki/Friction#Dry_friction](Wikipedia --> Dry friction).


***

[^1]: The naming is inherited from the [neccesary KKT conditions](https://en.wikipedia.org/wiki/Karush%E2%80%93Kuhn%E2%80%93Tucker_conditions#Necessary_conditions).
[^2]: This might not be true in a strict sense, most contact forces are a consequence of the electicmagnetic forces between atoms. Hence, the force increases locally because atoms are pushed closer together than they prefer. However, under the assumption of rigidity the forces are non-local.
[^3]: All equations with indices $$i$$ should be read as "for all $$i$$ ...".