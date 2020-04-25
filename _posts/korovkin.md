---
layout: post
title: Korovkin's theorems
description:
---

Since this is my first blog entry, a few words in advance. I want to collect notable theorems and small bits of mathematics which I come across during my PhD. The entries are neither complete and almost surely never free of errors. It's more like my personal notepad.

---

# Korovkin theorems

Pavel Krovkin's theorems are a bit surprising, since they allow to show pointwise convergence of a sequence of linear operators under very mild conditions. Most notably, the pointwise convergence of the operators at three points is enough!

The theorems are:

**Theorem 1** (Korovkin's first theorem)

Let $$(T_n)_{n}$$ be a sequence of bounded linear operators $$T_n : C[0,1] \to C[0,1]$$ be a bounded, linear operator which is also positive, i.e. for a function $$x \in C[0,1]$$ with $$x \geq 0$$ we have $$T_n x \geq 0$.
We define $x_i(t) = t^i$.

If

$$ T_n x_0 \to x_0, \quad
T_n x_1 \to x_1, \quad \text{and} \quad
T_n x_2 \to x_2, \quad \text{for } n \to \infty,
$$

then

$$
T_n x \to x, \quad \text{for all } x \in C[0,1].
$$
