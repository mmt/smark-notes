---
title: "State Transition Matrices"
date: 2020-12-28T23:38:22-08:00
draft: false
---

This post will eventually have a few tricks (just one for now) for
deriving
[state transitions matrices](https://en.wikipedia.org/wiki/State-transition_matrix) in
the context of inertial navigation.
These matrices arise when studying linear ODEs, for example:
$$
\dot x(t) = F(t)x(t) + G(t) u(t), \qquad x(t_0) = x_0
$$
where
- $F: [t_0, t_f] \rightarrow \mathbb{R}^{n\times n}$ is the state matrix,
- $G: [t_0, t_f] \rightarrow \mathbb{R}^{n \times m}$ is the input matrix,
- $u: [t_0, t_f] \rightarrow \mathbb{R}^m $ is the input,
- $x: [t_0, t_f] \rightarrow \mathbb{R}^n$ is the solution of the ODE.

The solution can be written as:
$$
x(t) = \Phi(t, t_0) x(t_0) + \int_{t_0}^t \Phi(t, s) G(s) u(s)\\; ds
$$

where $\Phi: [t_0, t_f] \times [t_0, t_f] \rightarrow \mathbb{R}^{n
\times n}$ is the state transition matrix.  This matrix itself is the
solution of the autonomous linear ODE:
$$
\dot \Phi(t, \tau) = F(t) \Phi(t, \tau), \qquad \Phi(\tau, \tau) = I.
$$

# Solution for Block Triangular $F$

Say $F$ is of the form:
$$F(t) = \begin{bmatrix} F_{11}(t) & F_{12}(t) \\\\ 0 & F_{22}(t)\end{bmatrix}.$$
Then $\Phi$ can also be written as:
$$\Phi(t, \tau) = \begin{bmatrix} \Phi_{11}(t, \tau) & \Phi_{12}(t, \tau) \\\\ 0 & \Phi_{22}(t, \tau)\end{bmatrix},$$
with $\Phi_{11}$ and $\Phi_{22}$ being the state-transition matrices associated with $F_{11}$ and $F_{22}$ independently:
$$
\begin{align}
\dot \Phi_{ii}(t, \tau) &= F_{ii}(t) \Phi_{ii}(t, \tau), \qquad \Phi_{ii}(\tau, \tau) = I \\qquad i \in \\{1, 2\\}. \\\\
\end{align}
$$
and
$$
\Phi_{12}(t, \tau) = \int_{\tau}^t \Phi_{11}(t, s) F_{12}(s) \Phi_{22}(s, \tau) \; ds.
$$

>*Proof*:
This result can be verified by noting that $\Phi(t, t) = I$ and differentiating $\Phi$:
$$
\frac{d}{dt} \Phi(t, \tau)
= \begin{bmatrix}
F_{11}(t) \Phi_{11}(t, \tau) & F_{12}(t)\Phi_{22}(t, \tau) + F_{11}(t) \Phi_{12}(t, \tau) \\\\
0 & F_{11}(t) \Phi_{22}(t, \tau)
\end{bmatrix} = F(t) \Phi(t, \tau).
$$
