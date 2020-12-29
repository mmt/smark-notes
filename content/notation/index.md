---
title: "Notation"
date: 2020-12-28T15:44:59-08:00
pdraft: False
---

This page covers the mathematical notation used in a number of the posts on this blog.

# Linear Algebra
## Components and Unit Vectors
We write $I$ for the identity matrix when its dimensions can be inferred.
When discussing a vector $v \in \mathbb{R}^n$ we denote its $i$-th
component by $v[i]$.  When discussing $\mathbb{R}^n$ we define $e_i$ via:

$$
e_i[j] := \begin{cases} 1 & i = j \\\\ 0 & \textrm{o.w.}\end{cases}
$$

for $i \in \{1, \ldots, n\}$.  This is equivalent to saying $e_i$ is
the $i$-th column of the identity matrix.  With this choice we can write:

$$
v[j] = e_j^T v
$$


For $\mathbb{R}^3$ we write the standard unit vectors as:
$$
e_x := e_1, \qquad e_y := e_2, \qquad e_z := e_3
$$

For $v \in \mathbb{R}^3$ we write its components as:
$$
v_x := e_x^T v, \qquad v_y := e_y^T v, \qquad v_z := e_z^T v
$$

# Geometry
## Cross product matrix
For a vector $u \in \mathbb{R}^3$ we'll write $$[u]_\times = \begin{bmatrix} 0 & -u_z & u_y \\\\ u_z & 0 & -u_x \\\\ -u_y & u_x & 0\end{bmatrix}$$ to mean the $3\times 3$ matrix such that $[u]\_\times v = u \times v$ for a all $v \in \mathbb{R}^3$.

## Reference Frames
A reference frame will be a point in space and an associated set of
right-handed axes.  We denote reference frames with capital letters.

### Rotations
- For a vector $v$ in three-dimensional space we write $v^A$ to denote $v$ *resolved* in the axes of the reference frame A.

- The symbol $C_A^B$ denotes the rotation matrix rotating vectors expressed in the coordinates of the $A$ frame to be represented in the coordinates of the $B$ frame, i.e. $v^B = C_A^B v^A$ for all $v$.

With these definitions we some simple rules:
$$
C_B^C C_A^B = C_A^C
$$

### Positions
- The symbol $p_{AB}$  denotes the vector connecting the origin of the $A$ frame to the origin of the $B$ frame.
With these definitions we some simple rules:

$$
p_{AB}^D + p_{BC}^D = p_{AC}^D
$$

### Time-varying Reference Frames
If two reference frames $A$ and $B$ vary with respect to time, we define:

$$
v_{AB}^A(t) := \frac{d}{dt} p_{AB}^A(t), \qquad a_{AB}^A(t) := \left(\frac{d}{dt}\right)^2 p_{AB}^A(t)
$$

When resolving velocity or acceleration in another frame we write:
$$
v_{AB}^C(t) := C_A^C v_{AB}^A(t), \qquad a_{AB}^C := C_A^C a_{AB}^A(t).
$$
