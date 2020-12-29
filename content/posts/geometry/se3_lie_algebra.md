---
title: "Properties of the SE(3) Lie Algebra"
date: 2020-12-28T14:20:12-08:00
draft: true
---
This is a companion pose to [the post about cross-product matrices]({{< ref "posts/geometry/cross_product.md" >}}).
In that post we explored the matrices
$$[v]_\times = \begin{bmatrix} 0 & -v_z & v_y \\\\ v_z & 0 & -v_x \\\\ -v_y & v_x & 0\end{bmatrix}$$
which where interesting due to their connection to $SO(3)$ via:
$$R(\theta, a) = \exp([\theta a]\_\times) = I + \sin(\theta) [a]\_\times + (1 - \cos(\theta))[a]\_\times^2$$

This post will go over some properties of the family of matrices:
$$\begin{bmatrix} [\theta a]\_\times & v \\\\ 0 & 0\end{bmatrix}$$
which have a similar relationship to the matrix group $SE(3)$:
$$\begin{bmatrix} R(\theta, a) & t \\\\ 0 & 1 \end{bmatrix} = \exp\left(\begin{bmatrix} [\theta a]\_\times & v \\\\ 0 & 0\end{bmatrix}\right)$$

# Power Series


$$\begin{align}
\begin{bmatrix}[v]\_\times & t \\\\ 0 & 0\end{bmatrix}^2 &= \begin{bmatrix}[v]\_\times^2 & [v]\_\times t \\\\ 0 & 0\end{bmatrix}\\\\
\begin{bmatrix}[v]\_\times & t \\\\ 0 & 0\end{bmatrix}^3
&= \begin{bmatrix}[v]\_\times^3 & [v]\_\times^2 t \\\\ 0 & 0\end{bmatrix}
= \begin{bmatrix}-\\|v\\|^2 [v]\_\times & [v]\_\times^2 t \\\\ 0 & 0\end{bmatrix}\\\\
\begin{bmatrix}[v]\_\times & t \\\\ 0 & 0\end{bmatrix}^4
&= \begin{bmatrix}[v]\_\times^4 & [v]\_\times^3 t \\\\ 0 & 0\end{bmatrix}
= \begin{bmatrix}-\\|v\\|^2 [v]\_\times^2 & -\\|v\\|^2[v]\_\times t \\\\ 0 & 0\end{bmatrix}
\end{align}$$

From this we see that any power series in the above matrix can be rewritten in the form:
$$
a I + b \begin{bmatrix}[v ]\_\times & v\end{bmatrix}
$$
