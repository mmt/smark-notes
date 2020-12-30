---
title: "Matrix Exponential Directional Derivative"
date: 2020-12-28T10:45:34-08:00
draft: False
tags: ["linear-systems"]
---

We can find a general expression for the derivative:

$$
\left . \frac{\partial}{\partial \lambda} \exp(A + \lambda \Delta) \right |_{\lambda = 0}
$$

where $A, \Delta \in \mathbb{R}^{n \times n}$ using some linear systems theory.  We will show that:

$$
\begin{align}
\left . \frac{\partial}{\partial \lambda} \exp(A + \lambda \Delta) \right |_{\lambda = 0}
&= \exp(A)\int_0^1 \exp(-sA) \Delta \exp(As) \\;ds \\\\
\end{align}
$$

>*Proof Sketch*:
Consider the function:
$$
\Phi(t, \lambda) = \exp(t(A + \lambda B)).
$$
We are looking to find
$\left . \frac{\partial}{\partial \lambda} \Phi(1, \lambda) \right |_{\lambda = 0}$.
>
>We know that $\Phi$ is given by a family of solutions of Linear ODEs:
$$
\frac{d}{dt} \Phi(t, \lambda) = (A + \lambda \Delta) \Phi(t, \lambda), \qquad \Phi(0, \lambda) = I.
$$
The idea to proceed is to find a differential equation for $\frac{\partial}{\partial \lambda} \Phi(t, \lambda)$.
$$
\begin{align}
\left . \frac{d}{dt} \frac{\partial}{\partial \lambda} \Phi(t, \lambda)\right |\_{\lambda=0} &=
 \left . \frac{\partial}{\partial \lambda} \left(\frac{d}{dt} \Phi(t, \lambda)\right) \right |\_{\lambda=0}\\\\
 &=
 \left . \frac{\partial}{\partial \lambda} \left((A + \lambda B)\Phi(t, \lambda)\right) \right |\_{\lambda=0}\\\\
&=
 A \left . \frac{\partial}{\partial \lambda} \Phi(t, \lambda)\right|_{\lambda=0} + B \Phi(t, 0).
\end{align}
$$
The initial condition for this solution is $\frac{\partial}{\partial \lambda} \Phi(0, \lambda) = \frac{\partial}{\partial \lambda} I = 0$.
>
>This linear-time-invariant ODE has the solution:
$$
\begin{align}
\left . \frac{\partial}{\partial \lambda} \Phi(1, \lambda) \right |_{\lambda=0}
&= \int_0^1 \exp((1-s)A) \Delta \Phi(s, 0) \\;ds \\\\
&= \exp(A)\int_0^1 \exp(-sA) \Delta \exp(As) \\;ds \\\\
\end{align}
$$
as was to be shown.

There is an interesting connection here in to [a property of triangular transition matrices]({{< ref "posts/systems/transition_matrices.md#block_triangular" >}}) notes in another  post in that:
$$
\begin{bmatrix}
\Phi(1, 0) & \left . \frac{\partial}{\partial \lambda} \Phi(1, \lambda) \right |_{\lambda=0} \\\\
0 & \Phi(1, 0)
\end{bmatrix} = \exp\left(\begin{bmatrix} A & \Delta \\\\ 0 & A\end{bmatrix}\right).
$$
