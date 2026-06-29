# Agent Guide: Producing Lecture Notes on Linear Systems of ODEs

## Goal

Produce elementary lecture notes on **linear autonomous systems of ordinary differential equations** of the form

\[
  x'(t)=Ax(t), \qquad A\in M_n(\mathbb C)
\]

or, when appropriate, \(A\in M_n(\mathbb R)\). The notes should closely follow the program described by the instructor:

1. Introduce and develop the **matrix exponential**.
2. Prove its basic properties.
3. Use it to solve linear systems of ODE.
4. Develop **Jordan canonical form** in enough detail to compute \(e^{tA}\).
5. Include the generalized-eigenvector **chain decomposition** argument, not merely the final block-diagonal statement.
6. Emphasize the decomposition of a matrix into Jordan blocks
   \[
     M_i=\lambda_i I+N_i,
   \]
   where \(N_i\) is nilpotent.
7. Compute the exponential of a Jordan block explicitly.

The intended audience is students who have seen basic linear algebra and elementary ODEs, but who may not have seen Jordan form in a proof-oriented way.

---

## Tone and Style

Write the notes in a clear, elementary, theorem-proof style.

The exposition should be:

- self-contained where reasonable;
- friendly but mathematically precise;
- proof-oriented, not just computational;
- explicit about which field is being used, usually \(\mathbb C\), with comments about real systems when useful;
- careful about the distinction between diagonalizable and non-diagonalizable matrices;
- rich in examples, especially \(2\times 2\) and \(3\times 3\) matrices.

Avoid assuming the reader already knows Jordan canonical form. Build it gradually from generalized eigenspaces and chains.

---

## Suggested Structure

### 1. Motivation: Why Linear Systems Matter

Begin with first-order systems

\[
  x'(t)=Ax(t), \qquad x(0)=x_0.
\]

Explain that for scalar equations \(x'=ax\), the solution is \(x(t)=e^{at}x_0\), and that the matrix exponential is designed so that the same formula remains true:

\[
  x(t)=e^{tA}x_0.
\]

Mention that the main technical questions are:

- What is \(e^{tA}\)?
- Why does it solve the system?
- How can one compute it?
- What happens when \(A\) is not diagonalizable?

---

### 2. The Matrix Exponential

Define, for \(A\in M_n(\mathbb C)\),

\[
  e^A = \sum_{m=0}^\infty \frac{A^m}{m!}.
\]

Also define

\[
  e^{tA} = \sum_{m=0}^\infty \frac{t^mA^m}{m!}.
\]

Include a short proof of convergence, for instance using any matrix norm satisfying

\[
  \|AB\|\leq \|A\|\|B\|.
\]

Show that

\[
  \left\|\frac{A^m}{m!}\right\|\leq \frac{\|A\|^m}{m!},
\]

so the matrix series converges absolutely.

#### Properties to Prove

Prove the following carefully:

1. \(e^0=I\).
2. If \(A\) and \(B\) commute, then
   \[
     e^{A+B}=e^Ae^B.
   \]
3. In particular,
   \[
     e^{sA}e^{tA}=e^{(s+t)A}.
   \]
4. \(e^{tA}\) is always invertible, with inverse
   \[
     e^{-tA}.
   \]
5. Similarity invariance:
   if \(A=PBP^{-1}\), then
   \[
     e^A=Pe^BP^{-1}.
   \]
6. Differentiation rule:
   \[
     \frac{d}{dt}e^{tA}=Ae^{tA}=e^{tA}A.
   \]

For the differentiation rule, justify termwise differentiation either by uniform convergence on compact intervals or by appealing to standard facts about power series with matrix coefficients.

---

### 3. Solving the Linear System \(x'=Ax\)

State and prove:

**Theorem.** For every \(x_0\in\mathbb C^n\), the unique solution of

\[
  x'(t)=Ax(t), \qquad x(0)=x_0,
\]

is

\[
  x(t)=e^{tA}x_0.
\]

The proof should have two parts.

#### Existence

Use the differentiation rule:

\[
  \frac{d}{dt}e^{tA}x_0=Ae^{tA}x_0.
\]

Also check the initial condition:

\[
  e^{0A}x_0=Ix_0=x_0.
\]

#### Uniqueness

Give an elementary uniqueness proof. For example, if \(x(t)\) is any solution, define

\[
  y(t)=e^{-tA}x(t).
\]

Then

\[
  y'(t)= -Ae^{-tA}x(t)+e^{-tA}x'(t)= -Ae^{-tA}x(t)+e^{-tA}Ax(t)=0,
\]

using the fact that \(A\) commutes with \(e^{-tA}\). Hence \(y(t)=y(0)=x_0\), so

\[
  x(t)=e^{tA}x_0.
\]

---

### 4. First Computations

Before introducing Jordan form, include several basic cases.

#### Diagonal Matrices

If

\[
  D=\operatorname{diag}(\lambda_1,\dots,\lambda_n),
\]

then

\[
  e^{tD}=\operatorname{diag}(e^{\lambda_1t},\dots,e^{\lambda_nt}).
\]

#### Diagonalizable Matrices

If

\[
  A=PDP^{-1},
\]

then

\[
  e^{tA}=Pe^{tD}P^{-1}.
\]

Explain that if \(A\) has a basis of eigenvectors, then solutions are linear combinations of

\[
  e^{\lambda t}v,
\]

where \(Av=\lambda v\).

#### Nilpotent Matrices

If \(N^r=0\), then

\[
  e^{tN}=I+tN+\frac{t^2N^2}{2!}+\cdots+\frac{t^{r-1}N^{r-1}}{(r-1)!}.
\]

This should be presented as the key idea behind Jordan blocks.

---

### 5. Generalized Eigenvectors and Jordan Chains

This section should be the heart of the linear algebra part.

Work over \(\mathbb C\), so that the characteristic polynomial splits.

For an eigenvalue \(\lambda\), define the generalized eigenspaces

\[
  E_\lambda^{(m)}=\ker(A-\lambda I)^m.
\]

The generalized eigenspace is

\[
  E_\lambda=\ker(A-\lambda I)^N
\]

for \(N\) large enough, for instance \(N=n\).

A nonzero vector \(v\) is a generalized eigenvector of rank/order \(r\) if

\[
  (A-\lambda I)^rv=0,
  \qquad
  (A-\lambda I)^{r-1}v\neq 0.
\]

#### Jordan Chains

If \(v\) has order \(r\), define the chain

\[
  v,
  (A-\lambda I)v,
  \dots,
  (A-\lambda I)^{r-1}v.
\]

Depending on convention, the chain may be ordered in reverse. Be explicit.

A convenient Jordan basis order is

\[
  w_1=(A-\lambda I)^{r-1}v,
  \quad
  w_2=(A-\lambda I)^{r-2}v,
  \quad \dots, \quad
  w_r=v.
\]

Then

\[
  Aw_1=\lambda w_1,
\]

and for \(j\geq 2\),

\[
  Aw_j=\lambda w_j+w_{j-1}.
\]

In this basis, the matrix of \(A\) on the span of the chain is a Jordan block.

#### What Must Be Proved

The notes should prove or at least carefully explain the following facts:

1. The spaces \(E_\lambda^{(m)}\) form an increasing sequence:
   \[
     E_\lambda^{(1)}\subseteq E_\lambda^{(2)}\subseteq \cdots.
   \]
2. The sequence stabilizes.
3. The generalized eigenspace \(E_\lambda\) is invariant under \(A\).
4. Generalized eigenspaces for distinct eigenvalues are linearly independent.
5. The whole space decomposes as a direct sum
   \[
     \mathbb C^n=\bigoplus_\lambda E_\lambda.
   \]
6. Each generalized eigenspace admits a basis consisting of Jordan chains.
7. Therefore there is a basis in which \(A\) is block diagonal with Jordan blocks.

The chain decomposition argument should not be skipped. At minimum, give a clear proof sketch using the filtration

\[
  0\subseteq \ker(A-\lambda I)
  \subseteq \ker(A-\lambda I)^2
  \subseteq \cdots
  \subseteq E_\lambda.
\]

One acceptable elementary approach is:

- Let \(T=A-\lambda I\) restricted to \(E_\lambda\), so \(T\) is nilpotent.
- Prove Jordan form first for nilpotent operators.
- Choose vectors of maximal possible height whose images generate the lower layers of the filtration.
- Extend these choices inductively so that chains project to bases of successive quotients
  \[
    \ker T^j / (\ker T^{j-1}+T\ker T^{j+1}).
  \]
- The resulting chains form a basis of \(E_\lambda\).
- Adding \(\lambda I\) to the nilpotent Jordan form gives the Jordan form for \(A\) on \(E_\lambda\).

If this quotient-based proof is too long for the intended notes, provide a detailed proof sketch and state clearly which linear algebra lemma is being used.

---

### 6. Jordan Canonical Form

State the theorem clearly.

**Jordan Canonical Form Theorem.** Let \(A\in M_n(\mathbb C)\). Then there exists an invertible matrix \(P\) such that

\[
  P^{-1}AP=J,
\]

where \(J\) is block diagonal:

\[
  J=\operatorname{diag}(J_1,\dots,J_k),
\]

and each block has the form

\[
  J_i=\lambda_i I+N_i,
\]

where

\[
  N_i=
  \begin{pmatrix}
  0 & 1 & 0 & \cdots & 0\\
  0 & 0 & 1 & \cdots & 0\\
  \vdots & \vdots & \vdots & \ddots & \vdots\\
  0 & 0 & 0 & \cdots & 1\\
  0 & 0 & 0 & \cdots & 0
  \end{pmatrix}
\]

or the transpose of this matrix, depending on the chosen chain convention.

Be consistent about whether the ones appear on the superdiagonal or subdiagonal.

Explain that \(N_i\) is nilpotent, and if the block has size \(r\), then

\[
  N_i^r=0.
\]

---

### 7. Exponential of a Jordan Block

Let

\[
  J=\lambda I+N,
\]

where \(N^r=0\). Since \(\lambda I\) commutes with \(N\),

\[
  e^{tJ}=e^{t(\lambda I+N)}=e^{\lambda t}e^{tN}.
\]

Because \(N\) is nilpotent,

\[
  e^{tN}=I+tN+\frac{t^2N^2}{2!}+\cdots+\frac{t^{r-1}N^{r-1}}{(r-1)!}.
\]

Therefore

\[
  e^{tJ}=e^{\lambda t}
  \left(
    I+tN+\frac{t^2N^2}{2!}+\cdots+\frac{t^{r-1}N^{r-1}}{(r-1)!}
  \right).
\]

For a Jordan block with ones on the superdiagonal, write the explicit matrix:

\[
  e^{tJ}=e^{\lambda t}
  \begin{pmatrix}
  1 & t & \frac{t^2}{2!} & \cdots & \frac{t^{r-1}}{(r-1)!}\\
  0 & 1 & t & \cdots & \frac{t^{r-2}}{(r-2)!}\\
  0 & 0 & 1 & \cdots & \frac{t^{r-3}}{(r-3)!}\\
  \vdots & \vdots & \vdots & \ddots & \vdots\\
  0 & 0 & 0 & \cdots & 1
  \end{pmatrix}.
\]

Conclude that solutions corresponding to a Jordan chain are combinations of terms of the form

\[
  e^{\lambda t}p(t),
\]

where \(p(t)\) is vector-valued polynomial.

---

### 8. General Formula for \(e^{tA}\)

If

\[
  A=PJP^{-1},
\]

then

\[
  e^{tA}=Pe^{tJ}P^{-1}.
\]

Since \(J\) is block diagonal,

\[
  e^{tJ}=\operatorname{diag}(e^{tJ_1},\dots,e^{tJ_k}).
\]

Each block is computed by the nilpotent formula above.

This gives a complete method for solving

\[
  x'=Ax.
\]

---

### 9. Real Systems and Complex Eigenvalues

If the notes are aimed at a real ODE class, include a short section explaining what happens when \(A\in M_n(\mathbb R)\) has complex eigenvalues.

Keep this section secondary if the instructor's main goal is matrix exponentials and Jordan form over \(\mathbb C\).

Possible points:

- Complex eigenvalues of real matrices occur in conjugate pairs.
- Complex-valued solutions can be converted into real-valued solutions by taking real and imaginary parts.
- For a pair \(\alpha\pm i\beta\), the real solutions involve
  \[
    e^{\alpha t}\cos(\beta t),
    \qquad
    e^{\alpha t}\sin(\beta t).
  \]
- Do not let this section distract from the main Jordan-block computation.

---

### 10. Examples to Include

Include several worked examples.

#### Example 1: Diagonal Matrix

\[
A=\begin{pmatrix}
2&0\\
0&-1
\end{pmatrix}.
\]

Compute \(e^{tA}\) and solve \(x'=Ax\).

#### Example 2: Diagonalizable but Not Diagonal

Choose a \(2\times2\) matrix with two distinct eigenvalues. Diagonalize it and compute \(e^{tA}\).

#### Example 3: A Single Jordan Block

\[
A=\begin{pmatrix}
\lambda&1\\
0&\lambda
\end{pmatrix}.
\]

Then

\[
 e^{tA}=e^{\lambda t}\begin{pmatrix}1&t\\0&1\end{pmatrix}.
\]

#### Example 4: A \(3\times3\) Jordan Block

\[
A=\begin{pmatrix}
\lambda&1&0\\
0&\lambda&1\\
0&0&\lambda
\end{pmatrix}.
\]

Then

\[
 e^{tA}=e^{\lambda t}
 \begin{pmatrix}
 1&t&t^2/2\\
 0&1&t\\
 0&0&1
 \end{pmatrix}.
\]

#### Example 5: Finding a Jordan Chain

Use a matrix with one eigenvalue and one eigenvector, such as

\[
A=\begin{pmatrix}
1&1&0\\
0&1&1\\
0&0&1
\end{pmatrix}
\]

or a non-obvious similar matrix. Show how to find a generalized eigenvector \(v\) satisfying

\[
(A-I)^3v=0,
\qquad
(A-I)^2v\neq 0.
\]

Then build the chain and compute \(e^{tA}\).

#### Example 6: Real Matrix with Complex Eigenvalues

Use

\[
A=\begin{pmatrix}
0&-1\\
1&0
\end{pmatrix}
\]

and show that

\[
 e^{tA}=\begin{pmatrix}
 \cos t&-\sin t\\
 \sin t&\cos t
 \end{pmatrix}.
\]

---

## Pedagogical Priorities

When writing the notes, keep the following priorities in mind.

### Emphasize the Matrix Exponential as the Main Object

The notes should not present Jordan form as an isolated linear algebra topic. Jordan form should be motivated by the need to compute \(e^{tA}\).

### Do Not Hide Nilpotence

The conceptual point is that every Jordan block is

\[
  \lambda I+N,
\]

where \(N\) is nilpotent. This explains why solutions contain polynomial factors multiplying exponentials.

### Include the Chain Argument

The instructor specifically wants the reference/notes to include the Jordan chain decomposition argument. Do not simply state that Jordan form exists. The notes should show how generalized eigenvectors assemble into chains and how chains give Jordan blocks.

### Be Explicit About Conventions

Different authors order Jordan chains differently. State clearly whether chains are ordered so that the nilpotent part has ones on the superdiagonal or subdiagonal.

### Separate the Main Line from Optional Material

The main line should be:

\[
\text{matrix exponential}
\longrightarrow
\text{solution formula}
\longrightarrow
\text{Jordan form}
\longrightarrow
\text{explicit computation of }e^{tA}.
\]

Real canonical form, stability theory, phase portraits, and nonautonomous systems may be mentioned, but they should not dominate these notes.

---

## Suggested Theorem-Proof Order

A good final set of notes may follow this theorem order:

1. Definition and convergence of \(e^A\).
2. Algebraic properties of \(e^A\).
3. Differentiability of \(e^{tA}\).
4. Fundamental solution theorem for \(x'=Ax\).
5. Computation for diagonal and diagonalizable matrices.
6. Computation for nilpotent matrices.
7. Generalized eigenspaces and chains.
8. Jordan canonical form theorem.
9. Exponential of a Jordan block.
10. General solution via \(A=PJP^{-1}\).

---

## Suggested Exercises

Include exercises of increasing difficulty.

### Basic Exercises

1. Prove that \(e^{tA}\) commutes with \(A\).
2. Prove that \(e^{sA}e^{tA}=e^{(s+t)A}\).
3. Compute \(e^{tA}\) for a diagonal matrix.
4. Compute \(e^{tN}\) for a nilpotent \(2\times2\) matrix.

### Intermediate Exercises

5. Diagonalize a given \(2\times2\) matrix and solve \(x'=Ax\).
6. Compute \(e^{tA}\) for a \(2\times2\) Jordan block.
7. Compute \(e^{tA}\) for a \(3\times3\) Jordan block.
8. Find a Jordan chain for a given defective matrix.

### Conceptual Exercises

9. Explain why polynomial factors appear in solutions when \(A\) is not diagonalizable.
10. Show that if \(A=PJP^{-1}\), then \(e^{tA}=Pe^{tJ}P^{-1}\).
11. Prove that generalized eigenspaces for distinct eigenvalues are linearly independent.
12. Prove Jordan form for a nilpotent operator in a low-dimensional case.

---

## Common Pitfalls to Avoid

- Do not write \(e^{A+B}=e^Ae^B\) without assuming \(AB=BA\).
- Do not assume every matrix is diagonalizable.
- Do not skip the proof that \(e^{tA}\) solves the ODE.
- Do not confuse algebraic multiplicity with geometric multiplicity.
- Do not state Jordan form over \(\mathbb R\) without qualification. The ordinary Jordan form is naturally over \(\mathbb C\).
- Do not change the Jordan chain ordering halfway through the notes.
- Do not hide the fact that a Jordan block is \(\lambda I+N\) with \(N\) nilpotent.

---

## Reference Anchors

The notes may use the following references as anchors.

### Primary Unified Reference

Gerald Teschl, *Ordinary Differential Equations and Dynamical Systems*, especially Chapter 3:

- matrix exponential;
- autonomous linear systems;
- Jordan canonical form appendix;
- generalized eigenvectors and chains.

This is the closest match to the intended program.

### More Elementary ODE-Oriented Supplement

Boyce and DiPrima, *Elementary Differential Equations and Boundary Value Problems*, section on linear systems with repeated eigenvalues.

Use this mainly for student-friendly examples and ODE motivation, not for a complete Jordan-form proof.

### Focused Supplement on Jordan Form and ODE

Steven Weintraub, *Jordan Canonical Form: Application to Differential Equations*.

Use this for extra examples and conceptual motivation connecting Jordan blocks to systems of ODE. Be aware that it may not contain a complete proof of Jordan canonical form.

---

## Expected Output Format for the Lecture Notes

When an agent produces the final notes, ask it to organize them as follows:

```markdown
# Linear Systems of ODEs and the Matrix Exponential

## 1. Introduction
## 2. The Matrix Exponential
## 3. Properties of the Matrix Exponential
## 4. Solving x' = Ax
## 5. Diagonalizable Systems
## 6. Nilpotent Matrices
## 7. Generalized Eigenvectors
## 8. Jordan Chains
## 9. Jordan Canonical Form
## 10. Exponentials of Jordan Blocks
## 11. General Solution Formula
## 12. Real Systems and Complex Eigenvalues
## 13. Examples
## 14. Exercises
## References
```

The notes should include displayed formulas, theorem/proof environments or clearly labeled theorem/proof blocks, and worked examples.

---

## Minimal Acceptable Coverage

A set of notes is acceptable only if it contains:

- the definition of \(e^A\) by power series;
- convergence of the matrix exponential;
- the commuting property \(e^{A+B}=e^Ae^B\) under \(AB=BA\);
- the derivative formula for \(e^{tA}\);
- the solution formula \(x(t)=e^{tA}x_0\);
- diagonalizable case;
- nilpotent case;
- generalized eigenspaces;
- Jordan chains;
- a clear statement of Jordan canonical form;
- explicit computation of \(e^{t(\lambda I+N)}\);
- at least one defective-matrix example.

---

## Preferred Level of Detail

The notes should be detailed enough that a student could reconstruct the proofs after lecture. The chain decomposition proof may be presented as a slightly more advanced subsection, but it should not be omitted. If the full proof is long, include a complete proof for nilpotent operators and then derive Jordan form for a general matrix from the generalized eigenspace decomposition.

