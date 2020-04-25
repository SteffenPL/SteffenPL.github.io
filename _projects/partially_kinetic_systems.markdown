---
layout: page
title: Partially Kinetic Systems
description: Coupling between micro and macro models.
img: /assets/img/partially_kinetic_systems_example.svg
tag: [current]
---

<p style="color:red;">This post is based on ongoing work. The statements in the linear case are going to be published in {% cite plunder2020linearPartiallyKineticSystems %}. The nonlinear case is in progress.</p>


We study a framework to couple kinetic systems with other macroscopic components.
The challenge here is to impose a kinetic constraint onto the evolution of the particle measure of the
kinetic system. Out approach is to impose the constraint at the microscopic level instead.
Therefore, we have to adapt the mean-field limit onto a setting with holonomic constraints.

Under appropriate assumptions, **Dorbushin's stability estimate** {% cite golseDynamicsLargeParticle2016 %} generalises well to such constrained systems which yields a fundamental stability estimate and allows proving the mean-field limit.

On the other hand, there are singular examples for which the discrete dynamics are well-defined but the mean-field limit fails dramatically.


## The discrete particle system

In abstract terms, we consider the macroscopic system [^1]

$$
m_r \ddot r = F_r(r) - \sum_{j=1}^N \left( \frac{\partial g}{\partial r}(r,Q_j) \right)^T\lambda_j,
$$

a particle system with microscopic law

$$
m_q \ddot Q_i = F_q(Q_i) - \left(\frac{\partial g}{\partial Q_i}(r,Q_i)\right)^T \lambda_i
\quad \quad \text{for all } i \in \{1,\dots,N\}
$$

and a (holonomic[^3]) constraint

$$
g(r,Q_i) = g(r(0), Q_i(0))
\quad \quad \text{for all } i \in \{1,\dots,N\}.
$$

It is important that the constraint is uniform in $$i$$, which means that every particle is treated in the same way.

A toy example would be a large linear spring, which is uniformly coupled to numerous small springs, like in the image below.
<img class="col three" src="{{ site.baseurl }}/assets/img/partially_kinetic_systems_example.svg"/>


### Numerical examples

If we let particles to be one-dimensional and the macroscopic system also be one-dimensional, we can plot both into a 2D plot.

In the following two examples we plot the trajectories

$$
(Q_1(t),r(t)), (Q_2(t),r(t)), \dots, (Q_N(t),r(t))
$$
as blue dots.
The contour lines of the function $$g(r,Q_j)$$ are shown as green-ish lines.

**The particles $$Q_j(t)$$ have to stay onto the coloured contour lines of the constraint $$g(r,Q_j)$$.**

We consider free particles, i.e. $$F_q = 0$$, and a harmonic osscilator for the macroscopic system, i.e. $$F_r(r) = -r$$.
For the plots we used $N = 100$ particles.

#### Regular case

<video style="width:100%; height:auto" controls>
  <source src="{{ site.baseurl }}/assets/videos/onion_example.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

The constraint in this setting is given by the nonlinear function

$$
g(r,Q_j) = \sin(\frac{q}{10})/(1+r^2) + \frac{q}{10}.
$$

Near the plateau of the contour lines, the blue dots move very fast in $$r$$ direction and are almost constant in $$q$$ direction.
At this point all kinetic energy of the particles is transferred to the macroscopic system.
Later, the particles obtain kinetic energy again.

This behaviour is best understood with the notation of the mean-field mass, which we will develop below!




#### Singular case

<video style="width:100%; height:auto" controls>
  <source src="{{ site.baseurl }}/assets/videos/singular_example.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

In the same setting as above, but with the singular constraint function

$$
g(r,Q_j) = (r-0.5)^2 + Q_j^2.
$$

If $$r = 0$$ the constraint is not invertible with respect to $$Q_j$$, which implies
that $$\frac{\partial g}{\partial Q_j} \to \infty$$.
We obtain a system for which the mean-field limit will fail!

The time at which the particles change their direction is determined by the particle which hits the the singularity of $$\frac{\partial g}{\partial Q_j}$$ first.
Such a behaviour is problematic from a kinetic perspective, since a continious measure cannot detect this case well. This singular example demonstrates how important it is to include regularity conditions in the theory.


## Mean-field limit for partially kinetic systems

We are interested in the mean-field limit for $$N \to \infty$$.
Due to the constraint, classical theorems from kinetic theory are not directly applicable. However, the situation is also easier since we have no *direct* interaction between particles!
The mean-field limit replaces the discrete particle positions $$(Q_j)_{j=1,\dots,N}$$
by a particle measure $$f(q,t)$$ such that

$$\int_A f(q,t) \, \mathrm{d} q \approx ``\text{number of particles in region $A$ at time $t$}"$$.

To derive an equation for the particle measure, we have two options:
- either we are happy with a purely analytical expression. Then we can afford to carry the Lagrangian multipliers $$\lambda_j$$ with us and derive the constrained mean-field characteristic flow;
- or we eliminate the Lagrangian multipliers and apply the mean-field limit afterwards. This approach yields the mean-field PDE.

In fact, taking the mean-field limit and elimination of the Lagrangian multipliers commutes.

#### Mean-field forces and **mean-field mass**

When we compute a bit, we can reformulate the system above into

$$
\left( m_r + m_\text{mf}(r,Q_1,\dots,Q_N) \right) \ddot r = F(r) + F_\text{mf}(r,Q_1,\dots,Q_N)
$$

and

$$
\dot Q_j = v_\text{eff}(r,Q_j).
$$

where $$F_\text{mf}$$ denotes the mean-field force and $$m_\text{mf}$$ the mean-field mass; The effective velocity $$v_\text{eff}$$ is the unique velocity needed for the particles to satisfy the constraint.

The appearance of a mean-field mass is not typical for kinetic systems and a consequence of the constraint. The mean-field mass is also the only serious troublemaker, since it could go to infinity.

#### Partially kinetic mean-field PDE

If we apply the mean-field limit to the reformulated system, we get the following kinetic equations

$$
\left(m_r + m_\text{mf}(r,f)\right) \ddot r = F(r) + F_\text{mf}(r,f)
$$

and

$$
\frac{\partial f}{\partial t} + v_\text{eff}(r,q)
\frac{\partial f}{\partial q} = 0.
$$

The PDE is a first-order transport equation.


## Analytical results

<p style="color:red;">This section is based on ongoing work. The statements are not published yet.</p>

Following François Golse's lecture notes 'On the Dynamics of Large Particle Systems in the Mean Field Limit'
{% cite golseDynamicsLargeParticle2016 %}, we can show the mean-field limit.
For the linear case the result is going to be published in {% cite plunder2020linearPartiallyKineticSystems %},
for the nonlinear case the publication is in progress.

The aim is to prove a modified version of Dobrushin's stability estimate.
We consider two solutions with different initial conditions
$$(r(t),f(t))$$ and $$(\tilde{r}(t), \tilde{f}(t))$$.
Under some technical conditions, we aim at proving the estimate

$$
\Vert r(t) - \tilde{r}(t) \Vert
+
\Vert \dot r(t) - \tilde{\dot r}(t) \Vert
+
W^1(f(t), \tilde{f}(t))
$$

$$
\quad \quad \quad \quad \quad \quad \leq C e^{Lt}
(\Vert r(0) - \tilde{r}(0) \Vert
+
\Vert \dot r(0) - \tilde{\dot r}(0) \Vert
+
W^1(f(0), \tilde{f}(0)) )
$$

where $$W^1$$ denotes the Wasserstein distance with exponent 1 (see Monge-Kantorovich distance in {% cite golseDynamicsLargeParticle2016 %}).
The Wasserstein distance  provides an excellent metric to compare particle measures $$f(t)$$ and $$\tilde{f}(t)$$.

### Linear case

Since the Wasserstein metric is shift invariant,
we can use a classical stability estimate for ODEs to obtain Dobrushin's stability estimate for linear partially kinetic systems.

#### Central estimates in the linear case

If the mean-field force is linear, we obtain from Kantorovich's duality formula for the Wassertein distance an estimate of the form

$$
\Vert F_\text{mf}(r,f) - F_\text{mf}(r,\tilde f) \Vert \leq L(r) W_1(f,\tilde{f})
$$

where $$L(r)$$ is an appropriate Lipschitz constant.
This shows that if $$f_1$$ and $$f_2$$ are close to each other, also the resulting mean-field forces are close.

### Nonlinear case (work in progress!)

#### Energy conservation

Since not stochastic noise or friction is present, we can compute conservation of energy with the same steps as in the discrete case.
This is crucial for finding bounds of the effective mass.


#### Troublemaker

To get estimates for $$r(t)$$, we need to study the ODE

$$
\ddot r = \left( m_r + m_\text{mf}(r,f) \right)^{-1} ( F_r(r) + F_{\text{mf}}(r,f) ).
$$

This leads to the problem of estimating terms like

$$
\Vert \left( m_r + m_\text{mf}(r,f) \right)^{-1} ( F_r(r) + F_{\text{mf}}(r,f) )
$$
$$\quad -
\left( m_r + m_\text{mf}(\tilde{r},\tilde{f}) \right)^{-1} ( F_r(\tilde{r}) + F_{\text{mf}}(\tilde{r},\tilde{f}) )
\Vert.
$$

So far, I found no completely satisfying solutions.
Right now, a bootstrapping-like approach allows me to assume an upper bound for the mean-field mass. This allows to derive the nessecary estimates.
Then, I can arguee afterwards that the regions with problematic mass cannot be reached due to energy conservation.

However, the proof needs proper checks!


References
----------

{% bibliography --cited %}
