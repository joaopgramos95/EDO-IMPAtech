# Prompt sketch: ODE/variational lecture notes on the 1D Wirtinger inequality

## Goal

Create short lecture notes for a gifted 2nd-year undergraduate ODE course. The notes should prove the one-dimensional periodic Poincaré-Wirtinger / Wirtinger inequality using a variational argument, not Fourier series, and then use it in Hurwitz's proof of the planar isoperimetric inequality.

The style should match an ODE course: assume an extremizer exists, derive an Euler-Lagrange equation, solve the resulting second-order ODE, identify the extremals, and conclude the sharp inequality.

## Target theorem

Let (u) be a (C^1), (2\pi)-periodic real-valued function with mean zero:

[
\int_0^{2\pi}u(t),dt=0.
]

Then

[
\int_0^{2\pi}u(t)^2,dt\leq \int_0^{2\pi}u'(t)^2,dt.
]

Equality holds exactly for

[
u(t)=a\cos t+b\sin t.
]

Also include the rescaled form: if (u) is (L)-periodic and has mean zero, then

[
\int_0^L u(x)^2,dx\leq \frac{L^2}{4\pi^2}\int_0^L u'(x)^2,dx.
]

## Proof strategy

Use the Rayleigh quotient

[
Q[u]=\frac{\int_0^{2\pi}u^2}{\int_0^{2\pi}(u')^2}
]

on the class of nonzero mean-zero periodic functions. State explicitly that, for this lecture, we assume a maximizer exists.

Let (u) be a maximizer and normalize by

[
\int_0^{2\pi}(u')^2=1.
]

Then (u) maximizes (\int u^2) subject to

[
\int_0^{2\pi}(u')^2=1,\qquad \int_0^{2\pi}u=0.
]

Use Lagrange multipliers. For every smooth periodic variation (v), impose stationarity of

[
\int u^2-\lambda\left(\int (u')^2-1\right)-\mu\int u.
]

This gives

[
2\int uv-2\lambda\int u'v'-\mu\int v=0.
]

Integrating by parts, with the boundary term vanishing by periodicity, gives

[
u+\lambda u''=\mu/2.
]

Integrate over ([0,2\pi]). Since (u) has mean zero and (u') is periodic, (\mu=0). Therefore

[
u+\lambda u''=0,
]

or

[
u''+\omega^2u=0,\qquad \omega^2=1/\lambda.
]

Solving the ODE gives

[
u(t)=A\cos(\omega t)+B\sin(\omega t).
]

The (2\pi)-periodicity forces (\omega=k) for some positive integer (k). Hence every extremal candidate has the form

[
u(t)=A\cos kt+B\sin kt.
]

For such a function,

[
Q[u]=\frac{1}{k^2}.
]

The maximum occurs at (k=1). Therefore the sharp constant is (1), and equality occurs exactly for

[
u(t)=a\cos t+b\sin t.
]

## Application to isoperimetric inequality

Let a simple closed plane curve be parametrized with constant speed on ([0,2\pi]):

[
\gamma(t)=(f(t),g(t)),\qquad (f')^2+(g')^2=\frac{L^2}{4\pi^2}.
]

Translate the curve so that (f) has mean zero. Translation does not change area or length.

Using Green's theorem,

[
A=\int_0^{2\pi}f(t)g'(t),dt.
]

Then

[
2A=2\int fg'
=\int \big(f^2+(g')^2-(f-g')^2\big)
\leq \int f^2+\int (g')^2.
]

By Wirtinger,

[
\int f^2\leq \int (f')^2.
]

Therefore

[
2A\leq \int_0^{2\pi}\big((f')^2+(g')^2\big),dt
=\int_0^{2\pi}\frac{L^2}{4\pi^2},dt
=\frac{L^2}{2\pi}.
]

Hence

[
4\pi A\leq L^2.
]

Discuss equality: equality in Wirtinger forces (f=a\cos t+b\sin t), and equality in the square term forces (g'=f). Hence (g) is also a first harmonic, so the curve is a circle.

## Style requirements

Write as lecture notes, not as a research paper. Keep the proof ODE-centered. Avoid Sobolev-space technicalities except for a brief caveat about the assumed existence of a maximizer. Include short student questions such as:

* Why does the mean-zero condition eliminate constants?
* Where do periodic boundary conditions enter?
* Why must the frequency be an integer?
* Which step produces the sharp constant?

