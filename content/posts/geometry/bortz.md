---
title: "Derivation of the Bortz Equation"
date: 2020-12-29T10:59:21-08:00
draft: true
tags: ["geometry", "navigation"]
---
We know that any $C \in SO(3)$ you can find a $\phi \in \mathbb{R}^3$ such that:
$$
C = \exp([\phi]\_\times).
$$
For a smoothly time-varying $C(t)$ we can also write:
$$
\begin{equation}
\dot C(t) = C(t) [\omega(t)]\_\times.
\end{equation}
$$
where $\omega(t) \in \mathbb{R}^3$ is the *angular rate vector*.
A natural question is:

>*If we define $\phi(t)$ so that[^1] $C(t) = \exp([\phi(t)]\_\times)$, what is the time derivative of $\phi(t)$?*

The answer to this question is useful in a number of applications such as improving the accuracy of integration schemes for Equation (1), and is given by the [Bortz Equation](https://ntrs.nasa.gov/citations/19700013316):
$$
\begin{align}
\dot \phi(t) &= \omega(t) + \frac{1}{2} [\phi(t)]\_\times \omega(t) +\frac{1}{\\|\phi(t)\\|^2}
\left(
1 -\frac{\\|\phi(t)\\|\sin(\\|\phi(t)\\|)}{2(1 - \cos(\\| \phi(t) \\|))}
\right) [\phi(t)]\_\times^2.
\end{align}
$$

A good direct derivation of this equation is given in [On the rotation vector differential equation](https://ieeexplore.ieee.org/document/68165/).
This post will give a different (and somewhat informal) derivation based on  the following simple observations.

>*Proof Sketch*: From the post on [the Jacobian of SO(3)]({{< ref "posts/geometry/so3_sensitivity.md" >}}) we have:
$$
\begin{align}
C(t+dt) &= \exp([\phi(t + dt)]\_\times) \\\\
 &\approx \exp([\phi(t) + dt \dot \phi(t)]\_\times) \\\\
 &\approx C(t)(I + [dt \Xi(\phi(t))\dot \phi(t)]\_\times) \\\\
\end{align}
$$
where
$$
\Xi(\phi) := \sin(\theta) I + (1-\cos(\theta)) [u]\_\times + (\theta - \sin(\theta)) uu^T
$$
with $\theta = \\|\phi\\|, u = \phi / \\|\phi\\|$.
We also know:
$$
\begin{align}
C(t+dt) &\approx C(t)(I + [dt \omega(t)]\_\times).
\end{align}
$$
So we have $\dot \phi(t) = \Xi(\phi(t))^{-1} \omega(t)$.
From [the post on cross product relationships]({{< ref "posts/geometry/cross_product.md" >}}) we have:
$$
\Xi(\phi)^{-1} := d I + e [u]\_\times + f uu^T
$$
with
$$
\begin{align}
\begin{bmatrix}d \\\\ e \\\\ f\end{bmatrix}
=& \frac{1}{\sin(\theta)^2+(1-\cos(\theta))^2}\begin{bmatrix}\sin(\theta) \\\\ \cos(\theta)-1 \\\\ \frac{(1-\cos(\theta))^2-(\theta-\sin(\theta))\sin(\theta)}{\theta}\end{bmatrix}, \\\\
=& \frac{1}{2(1 - \cos(\theta))}\begin{bmatrix}\sin(\theta) \\\\ \cos(\theta)-1 \\\\ \frac{2(1-\cos(\theta))-\theta\sin(\theta)}{\theta}\end{bmatrix}.
\end{align}
$$
$$
\begin{align}
\dot \phi(t) &= \Xi(\phi(t))^{-1}\omega(t) \\
&= (d I + e [u]\_\times + f uu^T) \omega(t).
\end{align}
$$

[^1]: It's worth pointing out that this isn't exactly how this question should be put as $\phi(t)$ is generally not unique and may be have discontinuously if $\\|\phi(t)\\|$ approaches a multiple of $2\pi$.
