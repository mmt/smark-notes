---
title: "Matrix Exponential Jacobians"
date: 2020-12-28T10:45:34-08:00
draft: True
tags: ["SO(3)", "SE(3)", "Lie"]
---

This note is going to go over some math that's useful for deriving the linearization
of equations like:

$$
\exp(A + \Delta)
$$

with respect to $\Delta$ where $A, \Delta \in \mathbb{R}^{n
\times n}$ and $\exp$ is the matrix exponential.  W.o.l.g. we
will only be interested in the derivative at $\delta = 0$.

The route I will take will be to look at each component of $\Delta$ one at a time writing
$$
\Delta = \sum_{i=1}^n \sum_{j=1}^n \Delta(i, j) e_i e_j^T.
$$

We look at the following function of a "time" parameter $t$ and a scalar parameter $\delta$:
$$
\Phi(t, \delta) = \exp(t(A + \delta B))
$$

evaluated at $t = 1$.  We know that $\Phi$ satisfies the differential equation:

$$
\frac{d}{dt} \Phi(t, \delta) = (A + \delta B) \Phi(t, \delta), \qquad \Phi(0, \delta) = I.
$$

The idea to proceed is to find a differential equation for $\frac{\partial}{\partial \delta} \Phi(t, \delta)$.

$$
\begin{align}
\left . \frac{d}{dt} \frac{\partial}{\partial \delta} \Phi(t, \delta)\right |\_{\delta=0} &=
 \left . \frac{\partial}{\partial \delta} \left(\frac{d}{dt} \Phi(t, \delta)\right) \right |\_{\delta=0}\\\\
 &=
 \left . \frac{\partial}{\partial \delta} \left((A + \delta B)\Phi(t, \delta)\right) \right |\_{\delta=0}\\\\
&=
 A \left . \frac{\partial}{\partial \delta} \Phi(t, \delta)\right|_{\delta=0} + B \Phi(t, 0).
\end{align}
$$
This is combined with an initial condition of $\frac{\partial}{\partial \delta} \Phi(0, \delta) = \frac{\partial}{\partial \delta} I = 0$.

This linear-time-invariant ODE has the solution:
$$
\begin{align}
\left . \frac{\partial}{\partial \delta} \Phi(1, \delta) \right |_{\delta=0}
&= \int_0^1 \exp((1-s)A) B \Phi(s, 0) \\;ds \\\\
&= \exp(A)\int_0^1 \exp(-sA) B \exp(As) \\;ds \\\\
\end{align}
$$


As an example we can take:
$$
\exp\left([v + \xi]\_\times\right)
\approx \exp([v]\_\times)( I + \int_0^1 \exp(-s[v]\_\times) [
$$
