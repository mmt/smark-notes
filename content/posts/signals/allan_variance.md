---
title: "Allan Variance of a Markov Process"
date: 2020-12-28T23:17:26-08:00
draft: true
---

The [Allan Variance](https://en.wikipedia.org/wiki/Allan_variance) (AV) is
a set of descriptive statistics useful for characterizing the drift of
a signal.  It is commonly employed to demonstrate the noise and bias
characteristics of gyroscope and accelerometers, and I ran into
a
[great survey article](https://escholarship.org/content/qt1vf7j52p/qt1vf7j52p_noSplash_750bb4e8a68d04f2d577450b1bf56572.pdf?t=qe8g5u) recently.
That article included an explicit formula for the AV of a first-order Markov Process, i.e.:
$$
\frac{d}{dt} x(t) = -\frac{1}{\tau} x(t) + w(t), \qquad \tau > 0.
$$

Here we interpret $w(t)$ as a process such that
$\mathbb{E}[w(t)w(\tau)] = Q\delta(t-\tau)$ where $\delta$ is the Dirac
delta function and $Q$ is a positive constant[^1]

While the AV for white-noise and pure random walks can be easily
obtained, this formula seemed a bit mysterious, so I set out to derive
it and got a chance to try out some contour integration.

# Allan Variance Definition

## Time Domain Analysis
### White Noise
### Random Walk
## Frequency Domain Analysis

# Contour Integral Review
## Integral of $\frac{\sin(\omega)}{\omega}$
## Integral of $\frac{1}{\omega^2 + a^2}$
## Integral of $\frac{\sin(\omega)^4}{\omega^2} \frac{1}{\omega^2 + a^2}$

[^1]: There's nothing like expository writing to help you realize you
    don't really know something -- I can only write about stochastic
    ODEs like this in a very naïve way. I hope to revisit this later.
