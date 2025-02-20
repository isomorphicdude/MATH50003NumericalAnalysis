# MATH50003 Numerical Analysis: Problem Sheet 9

This problem sheet explores Jacobi matrices, classical orthogonal polynomials, and interpolation.

Questions marked with a ⋆ are meant to be completed without using a computer.
Problems are denoted A/B/C to indicate their difficulty.


## 1. Jacobi matrices

**Problem 1.1 (C)** What are the upper 3x3 sub-block of the Jacobi matrix for the 
monic and orthonormal polynomials with respect to the following weights on
$[-1,1]$:
$$
1-x, \sqrt{1-x^2}, 1-x^2
$$

**SOLUTION**

##### Monic

We know that for monic ($b_n=1$) orthogonal polynomials we can write the upper 3x3 block in the form

$$X = \begin{bmatrix} a_0 & c_0 & 0 \\ 1 & a_1 & c_1 \\ 0 & 1 & a_2 \end{bmatrix}$$


1. $w(x) = 1-x$

Take $p_0(x) = 1$ (monic) and note
$$
\| p_0 \|^2 = \int_{-1}^1 (1-x) {\rm d}x = 2
$$
From
$$
xp_0(x) = a_0p_0(x) + p_1(x)
$$
we deduce
$$
a_0 = ⟨x p_0, p_0⟩/\|p_0\|^2 =  {\int_{-1}^1 (1-x) x {\rm d}x \over 2} =  -{1 \over 3}
$$
i.e.
$$
p_1(x) = (x-a_0) p_0(x) = x + 1/3.
$$
and note that
$$
\|p_1\|^2 = \int_{-1}^1 (1-x) (x+1/3)^2 {\rm d} x = 4/9.
$$
From
$$
xp_1(x) = c_0 p_0(x) + a_1 p_1(x) + p_2(x)
$$
we deduce
$$
c_0 = ⟨x p_1, p_0⟩/\|p_0\|^2 =  {\int_{-1}^1 (1-x) x (x+1/3) {\rm d}x \over 2} =  {2 \over 9}
$$
and
$$
a_1 = ⟨x p_1, p_1⟩/\|p_1\|^2 =  {9 \over 4} {\int_{-1}^1 (1-x) x (x+1/3)^2 {\rm d}x} =  -{1 \over 15}
$$
Thus
$$
p_2(x) = (x - a_1) p_1(x) - c_0 p_0(x) = (x+1/15) (x+1/3) - 2/9 = x^2 + 2x/5 -1/5.
$$
And once again as before:
$$
c_1=\frac{\langle p_1, xp_2\rangle}{\|p_1\|^2}= \frac{\int_{-1}^1 (x+\frac{1}{3})(x^2+\frac{1}{9}x- \frac{1}{5}) x(1-x) dx}{\int_{-1}^1 (x+\frac{1}{3})^2 (1-x) dx}= \frac{16}{45}$$
and
$$
a_2 = \frac{\langle p_2, xp_2\rangle}{\|p_2\|^2} = \frac{\int_{-1}^1 (x^2+\frac{1}{9}x- \frac{1}{5})^2 x(1-x) dx}{\int_{-1}^1 (x^2+\frac{1}{9}x- \frac{1}{5})^2 (1-x) dx}= \frac{2085}{3451}
$$


2. $w(x)=\sqrt{1-x^2}$

Take $p_0(x) = k_0 = 1$ (monic) so that
$$
\|p_0\|^2 = \int_{-1}^1 \sqrt{1-x^2} = {π \over 2}.
$$
From PS8, Problem 3.4 we know that $a_k = 0$. Thus
from the recurrence we have
$$
xp_0(x) =  p_1(x)
$$
and hence
$$
p_1(x) = x p_0(x) = x.
$$
Likewise for
$$
xp_1(x)= c_0p_0(x)+p_2(x)
$$
we have
$$
c_0=\frac{\langle p_0, xp_1\rangle}{\|p_0\|^2} \frac{\int_{-1}^1 x^2\sqrt{1-x^2} dx}{\pi/2}=\frac{\pi/8}{\pi/2}= \frac{1}{4}
$$
i.e.
$$
p_2(x) = xp_1(x) - c_0 = x^2 - {1 \over 4}.
$$
Finally:
$$
xp_2(x)= c_1p_1(x)p_3(x)
$$
and thus
$$
c_1=\frac{\langle p_1, xp_2\rangle}{\|p_1\|^2}= \frac{\int_{-1}^1 (x^2- \frac{1}{4}) x^2\sqrt{1-x^2} dx}{\int_{-1}^1 x^2 \sqrt{1-x^2} dx}= \frac{\pi/32}{\pi/8}=\frac{1}{4}
$$


3. $w(x)=1-x^2$

Take $p_0(x) = k_0 = 1$ (monic). Again due to $w(x) = w(-x)$
from recurrence we have
$$
xp_0(x) = p_1(x)
$$
Then from
$$xp_1(x)= c_0p_0(x)+p_2(x)$$
we find
$$c_0=\frac{\langle p_0, xp_1\rangle}{\|p_0\|^2} \frac{\int_{-1}^1 x^2(1-x^2) dx}{4/15}=\frac{4/15}{4/3}= \frac{1}{5}$$
Finally,
$$xp_2(x)= c_1p_1(x)+p_3(x)$$
and thus
$$c_1=\frac{\langle p_1, xp_2\rangle}{\|p_1\|^2}= \frac{\int_{-1}^1 (x^2- \frac{1}{5}) x^2(1-x^2) dx}{\int_{-1}^1 x^2 (1-x^2) dx}= \frac{32/525}{4/15}=\frac{8}{35}$$




##### Orthonormal

We know that for orthonormal ($b_n=c_n$) polynomials we can write the upper 3x3 block of the Jacobi matrix in the
form

$$X = \begin{bmatrix} a_0 & b_0 & 0 \\ b_0 & a_1 & b_1 \\ 0 & b_1 & a_2 \end{bmatrix}$$

We could proceed step by step as above to find the entries of the recurrences but we may also
take a short-cut since we already know the monic recurrence. Given any recurrence relationship
coefficients $a_n, b_n, c_n$ for orthogonal polynomials for a given weight, the(symmetric)
Jacobi matrix corresponding to the orthonormal polynomials for the same weight has entries $\hat
{b}_n = \sqrt{c_n b_n}$ and $\hat{a} _n = a_n$. Using this the $3 \times 3$ blocks of the
Jacobi matrices belonging to the orthonormal polynomials are straightforwardly computed from the above.

**Problem 1.2 (B)** Consider the _truncated Jacobi matrix_ associated
with orthonormal polynomials $q_n(x)$:
$$
X_n := \begin{bmatrix} a_0 & b_0 \\
                         b_0 & ⋱ & ⋱ \\
                         & ⋱ & a_{n-2} & b_{n-2} \\
                         && b_{n-2} & a_{n-1} \end{bmatrix} ∈ ℝ^{n × n}
$$
Show that
$$
x [q_0(x) | ⋯ | q_{n-1}(x)] = [q_0(x) | ⋯ | q_{n-1}(x)] X_n + b_{n-1} q_n(x) 𝐞_n^⊤.
$$

**SOLUTION**

We have that in the infinite form of $X$:
$$x[q_0,...,q_{n-1},...] = [q_0,...,q_{n-1},...]X$$

Thus, selecting just the first $n$ terms, we have
$$x[q_0,...,q_{n-1}] = \left[[q_0,...,q_{n-1} ,q_n]X\right]_{1,...,n}=\left[[q_0,...,q_{n-1},...]X_{n+1}\right]_{1,...,n}$$
considering that we don't need the terms after the $n+1$ since the relevant terms in the matrix $X$ would be 0s.

Writing the $n^{th}$ term explicitly we obtain
$$xq_{n-1} = [q_{n-2},q_{n-1},q_n]\{X_{n+1}\}_{n,n-1:n+1}= b_{n-2}q_{n-2} + a_{n-1} q_{n-1} + b_{n-1}q_n$$

While
$$[q_{n-2},q_{n-1},q_n]\{X_{n}\}_{n,n-1:n+1} = b_{n-2}q_{n-2} + a_{n-1} q_{n-1}$$

Thus, the only extra term that this form is missing is $b_{n-1}q_n$ in the $n^{th}$ term which can be added using the vector $e_n^T$, hence


$$
x [q_0(x) | ⋯ | q_{n-1}(x)] = [q_0(x) | ⋯ | q_{n-1}(x)] X_n + b_{n-1} q_n(x) 𝐞_n^⊤
$$

**Problem 1.3 (A)** Prove the _Christoffel-Darboux Formula_: orthonormal polyomials $q_k(x)$ satisfy
$$
∑_{k = 0}^n q_k(x) q_k(y) =  b_n {q_{n+1}(x) q_n(y) - q_n(x) q_{n+1}(y) \over x-y}
$$
Hint: Consider
$$
(x-y) [q_0(x) | ⋯ | q_n(x)] \begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix}.
$$

**SOLUTION**

We have to prove that
$$
(x-y) [q_0(x) | ⋯ | q_n(x)] \begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix} = (x-y)∑_{k = 0}^n q_k(x) q_k(y) = b_n ({q_{n+1}(x) q_n(y) - q_n(x) q_{n+1}(y))}
$$

Using 1.2 we have

$x[q_0(x) | ⋯ | q_n(x)] = [q_0(x) | ⋯ | q_n(x)] X_{n+1} + b_n q_{n+1}(x)e_{n+1}^T$

$y[q_0(y) | ⋯ | q_n(y)] = [q_0(y) | ⋯ | q_n(y)] Y_{n+1} + b_n q_{n+1}(y)e_{n+1}^T$


Right-multiplying these formulas respectively by $[q_0(y) | ⋯ | q_n(y)]^T$ and $[q_0(x) | ⋯ | q_n(x)]^T$ we obtain

$x[q_0(x) | ⋯ | q_n(x)][q_0(y) | ⋯ | q_n(y)]^T = [q_0(x) | ⋯ | q_n(x)] X_{n+1}[q_0(y) | ⋯ | q_n(y)]^T + b_n q_{n+1}(x)q_n(y)$

$y[q_0(y) | ⋯ | q_n(y)][q_0(x) | ⋯ | q_n(x)]^T = [q_0(y) | ⋯ | q_n(y)] Y_{n+1}[q_0(x) | ⋯ | q_n(x)]^T + b_n q_{n+1}(y)q_n(x)$

which (transposed of a number) corresponds to

$y[q_0(x) | ⋯ | q_n(x)][q_0(y) | ⋯ | q_n(y)]^T = [q_0(x) | ⋯ | q_n(x)] Y_{n+1}^T[q_0(y) | ⋯ | q_n(y)]^T + b_n q_n(x)q_{n+1}(y)$

Subtracting from the first equation the second (transposed) we get

$(x-y)[q_0(x) | ⋯ | q_n(x)]\begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix} = [q_0(x) | ⋯ | q_n(x)] (X_{n+1}-Y_{n+1}^T)\begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix} + b_n (q_{n+1}(x)q_n(y)-q_n(x)q_{n+1}(y))$

But since the matrices $X_{n+1}$ and $Y_{n+1}$ do not depend on the values of $x$ and $y$, but on the polynomials, then they are the same matrix.

In particular, they are symmetric matrices since the $q_k$s are orthonormal. Thus,
$X_{n+1}-Y_{n+1}^T=0$

Hence, 
$[q_0(x) | ⋯ | q_n(x)] (X_{n+1}-Y_{n+1}^T)\begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix}=0$, thus

$$∑_{k = 0}^n q_k(x) q_k(y) = [q_0(x) | ⋯ | q_n(x)]\begin{bmatrix} q_0(y) \\ ⋮ \\ q_n(y) \end{bmatrix} = { b_n (q_{n+1}(x)q_n(y)-q_n(x)q_{n+1}(y))\over x-y}$$


## 2. Chebyshev polynomials

**Problem 2.1 (C)** What is the Jacobi matrix for $T_n(x)$? What scaling
$q_n(x) = D_n T_n(x)$ gives us orthonormal polynomials?

**SOLUTION**

Let $w(x)=1/\sqrt{1-x^2}$ on $[-1,1]$ and $q_n(x)=D_nT_n(x)$. 

We know $T_0(x)=1$ and we want $\|q_0\|=1$

Thus,
$$1=\int_{-1}^1 D_0^2 w(x)dx = D_0^2\pi$$

Hence,
$D_0= \sqrt{\frac{1}{\pi}}$

Now let $\|q_1\|=1$

$$1=\int_{-1}^1 D_1^2 (\cos(acos(x)))^2 w(x)dx = D_1^2 \int_{-1}^1 \frac{x^2}{\sqrt{1-x^2}}dx = D_1^2\frac{\pi}{2}$$

Hence,
$D_1= \sqrt{\frac{2}{\pi}}$

In general we want $\|q_n\|=1$, thus

$$1=\int_{-1}^1 D_n^2 (\cos(n \times acos(x)))^2 w(x)dx = D_n^2\frac{\pi}{2}$$

Hence, $\forall n\ge 1$,
$$D_n= \sqrt{\frac{2}{\pi}}$$

**Problem 2.2 (B)** Consider the function
$$
f(x) = \sum_{k=0}^∞ {T_k(x) \over k!}
$$
For what coefficients $c_k$ does
$$
(x^2+1) f(x) = \sum_{k=0}^∞ c_k T_k(x)?
$$

**SOLUTION**

We need 

$$(x^2+1)\sum_{k=0}^∞ {T_k(x) \over k!} = \sum_{k=0}^∞ c_k T_k(x)$$

We can use the following to rewrite the LHS
$$xT_0(x)=T_1(x)$$

$$xT_n(x)=\frac{T_{n-1}(x)+T_{n+1}(x)}{2}$$

Indeed,

$$(x^2+1)\sum_{k=0}^∞ {T_k(x) \over k!} = \sum_{k=0}^∞ {x^2T_k(x) \over k!} + \sum_{k=0}^∞ {T_k(x) \over k!} = xT_1(x)+\sum_{k=1}^∞ {x\frac{T_{k-1}(x)+T_{k+1}(x)}{2 k!}} + \sum_{k=0}^∞ {T_k(x) \over k!} = $$

Using
$$x\frac{T_{0}(x)+T_{2}(x)}{2* 1!}= \frac{T_1(x)}{2} + \frac{T_{1}(x)+T_{3}(x)}{4}$$
and
$$\sum_{k=2}^∞ {x\frac{T_{k-1}(x)+T_{k+1}(x)}{2 k!}}= \sum_{k=2}^∞ \left(\frac{T_{k-2}(x)+T_{k}(x)}{4k!} + \frac{T_{k}(x)+T_{k+2}(x)}{4k!}\right)$$


we obtain

$$= \frac{T_{0}(x)+T_{2}(x)}{2} + \frac{T_1(x)}{2} + \frac{T_{1}(x)+T_{3}(x)}{4}+\sum_{k=2}^∞ \left(\frac{T_{k-2}(x)+T_{k}(x)}{4k!} + \frac{T_{k}(x)+T_{k+2}(x)}{4k!}\right) + \sum_{k=0}^∞ {T_k(x) \over k!}$$

So, we have 

$$c_0=\frac{1}{2}+\frac{1}{4*2!}+1= \frac{13}{8}$$

$$c_1=\frac{1}{2}+\frac{1}{4*1!}+\frac{1}{4*3!}+1=\frac{43}{24}$$

$$c_2=\frac{1}{2}+\frac{2}{4*2!}+\frac{1}{4*4!}+1$$

$$c_3=\frac{1}{4}+\frac{2}{4*3!}+\frac{1}{4*5!}+1$$

$$c_4=\frac{1}{4*2!}+\frac{2}{4*4!}+\frac{1}{4*6!}+1$$

For $n\ge3$ we have 
$$c_n=\frac{1}{4*(n-2)!}+\frac{1}{2*n!}+\frac{1}{4*(n+2)!}+1$$

**Problem 2.3 (B)**
Consider orthogonal polynomials with respect to $\sqrt{1-x^2}$ on $[-1,1]$ with the
normalisation
$$
U_n(x) = 2^n x^n + O(x^{n-1})
$$
Prove that
$$
U_n(\cos θ) = {\sin(n+1) θ \over \sin θ}
$$

**SOLUTION**

We need to verify:
1. graded polynomials
2. orthogonal w.r.t. $\sqrt{1-x^2}$ on $[-1,1]$, and
3. have the leading coefficient $2^n$.

(2) follows under a change of variables
$$\int_{-1}^1U_n(x)U_m(x)\sqrt{1-x^2}{\rm d}x=\int_0^{\pi}U_n(\cos\theta)U_m(\cos\theta)\sin^2\theta{\rm d}\theta=\int_0^{\pi}\sin(n+1)\theta\sin(m+1)\theta{\rm d}\theta=\frac{\pi}{2}\delta_{mn}$$
where the last step is a result from Fourier theories.

To see that they are graded we use the fact that
$$xU_n(x)=\frac{\cos\theta\sin(n+1)\theta}{\sin\theta}=\frac{\sin (n+2)\theta+\sin n\theta}{2\sin\theta}$$
In other words $2xU_n(x)=U_{n+1}(x)+U_{n-1}(x)$. Since each time we multiply by $2x$ and $U_0(x)=1$ we have
$$U_n(x) = 2^n x^n + O(x^{n-1})$$
which also proves (3).


**Problem 2.4 (B)** Show that
$$
\begin{align*}
x U_0(x) &= U_1(x)/2 \\
x U_n(x) &= {U_{n-1}(x) \over 2} + {U_{n+1}(x) \over 2}.
\end{align*}
$$

**SOLUTION**

The first result is trivial.

To get the second result, recall that
$$U_n(\cos\theta)=\cos\theta U_{n-1}(\cos\theta)+\cos n\theta$$
and
$$\cos n\theta=\cos\theta\cos(n-1)\theta-(1-\cos^2\theta)U_{n-2}(\cos\theta).$$

The first equation gives $\cos n\theta$ in terms of $U_n$ and $U_{n-1}$. Substitute the result into the second equation to get
$$U_n(x)-xU_{n-1}(x)=x(U_{n-1}(x)-xU_{n-2}(x))-(1-x^2)U_{n-2}(x)$$
which reduces to the desired recurrence.

**Problem 2.5 (C)** What is the Jacobi matrix for $U_n(x)$? What scaling
$q_n(x) = D_n U_n(x)$ gives us orthonormal polynomials?

**Solution**

Problem 2.4 gives the Jacobi matrix
$$\begin{bmatrix}
0 & 1/2 & \\
1/2 & \ddots & \ddots \\
 & \ddots &
\end{bmatrix}$$
From Problem 2.3 we know
$$
\|U_n\|=\int_{-1}^1U_n(x)^2 \sqrt{1-x^2}{\rm d}x=\int_0^{\pi}\sin^2(n+1)\theta\theta{\rm d}\theta=\frac{\pi}{2}
$$
so $D_n=\sqrt{2}{\pi}$.


## 3. Hermite polynomials

**Problem 3.1 (B)** Consider Hermite polynomials orthogonal with respect to the weight $\exp(-x^2)$ on $ℝ$
with the normalisation
$$
H_n(x) = 2^n x^n + O(x^{n-1}).
$$
Prove the Rodrigues formula
$$
H_n(x) = (-1)^n \exp(x^2) {{\rm d}^n \over {\rm d}x^n} \exp(-x^2)
$$

**SOLUTION**
Define
$$
p_n(x) := (-1)^n \exp(x^2) {{\rm d}^n \over {\rm d}x^n} \exp(-x^2)
$$

We need to verify that $p_n$
1. are graded polynomials
2. are orthogonal to all lower degree polynomials on $\mathbb{R}$, and
3. have the right leading coefficient $2^n$.

Comparing the Rodrigues formula for $n$ and $n-1$, we find that 
$$
(-1)^n\exp(-x^2)p_n(x)={{\rm d} \over {\rm d}x}\left((-1)^{n-1}\exp(-x^2)p_{n-1}(x)\right)
$$
which reduces to
$$p_n(x)=2xp_{n-1}(x)-p_{n-1}'(x).$$

(1) and (3) then follows from induction since $p_0(x)=1$.

(2) follows by integration by parts. If $r_m$ is any degree $m<n$ polynomial we have:
$$
\begin{align*}
\int_{-∞}^∞ p_n(x)r_m(x)\exp(-x^2){\rm d}x&=\int_{-∞}^∞{{\rm d}^n \over {\rm d}x^n} \exp(-x^2)r(x){\rm d}x = -\int_{-∞}^∞{{\rm d}^{n-1} \over {\rm d}x^{n-1}} \exp(-x^2)r'(x){\rm d}x\\
&=⋯\text{integration by parts $n$ times}…=(-1)^n\int_{-∞}^∞ \exp(-x^2)r_m^{(n)}(x)=0
\end{align*}
$$
Thus $p_n(x) = H_n(x)$ by uniqueness.

**Problem 3.2 (C)** What are $k_n^{(1)}$ and $k_n^{(2)}$ such that
$$
H_n(x) = 2^n x^n + k_n^{(1)} x^{n-1} + k_n^{(2)} x^{n-2} + O(x^{n-3})
$$

**SOLUTION**

From Problem 3.1,
$$H_n(x)=2xH_{n-1}(x)-H_{n-1}'(x).$$
Thus we have
$$k_n^{(1)}=2k_{n-1}^{(1)}$$
$$k_n^{(2)}=2k_{n-1}^{(2)}-(n-1)2^{n-1}$$

Since $k_0^{(1)}=0$, we have $k_n^{(1)}=0$. For the second recurrence, divide both sides by $2^n$:
$$2^{-n}k_n^{(2)}=2^{-(n-1)}k_{n-1}^{(2)}-\frac{n-1}{2}$$
Since $k_0^{(2)}=0$, we have $2^{-n}k_n^{(2)}=-\frac{1+\cdots+(n-1)}{2}=-\frac{n(n-1)}{4}$, so $k_n^{(2)}=-n(n-1)2^{n-2}$.

**Problem 3.3 (B)** Deduce the 3-term recurrence relationship for $H_n(x)$.

**SOLUTION**

Our goal is to find $a_n$, $b_n$ and $c_n$ such that
$$xH_n(x)=c_{n-1}H_{n-1}(x)+a_nH_n(x)+b_nH_{n+1}(x).$$
Compare the 3 leading coefficients on both sides and use the results from Problem 3.1 and Problem 3.2:
$$
2^n=0+0+b_n2^{n+1}
$$
$$
0=0+a_n2^n+0
$$
$$
n(n-1)2^{n-2}=c_{n-1}2^{n-1}+0+b_n(n+1)n2^{n-1}
$$
Thus we have $b_n=1/2$, $a_n=0$ and $c_{n-1}=n$.



## 4. Interpolation

**Problem 4.1 (C)** Use Lagrange interpolation to
interpolate the function $\cos x$ by a polynomial at the points
$[0,2,3,4]$ and evaluate at $x = 1$. 

**SOLUTION**

- $l_0(x)=\frac{(x-2)(x-3)(x-4)}{(0-2)(0-3)(0-4)}=-\frac{1}{24}(x-2)(x-3)(x-4)$
- $l_2(x)=\frac{(x-0)(x-3)(x-4)}{(2-0)(2-3)(2-4)}=\frac{1}{4}x(x-3)(x-4)$
- $l_3(x)=\frac{(x-0)(x-2)(x-4)}{(3-0)(3-2)(3-4)}=-\frac{1}{3}x(x-2)(x-4)$
- $l_4(x)=\frac{(x-0)(x-2)(x-3)}{(4-0)(4-2)(4-3)}=\frac{1}{8}x(x-2)(x-3)$

$p(x)=\cos(0)l_0(x)+\cos(2)l_2(x)+\cos(3)l_3(x)+\cos(4)l_4(x)$

$l_0(1)=1/4$, $l_2(1)=3/2$, $l_3(1)=-1$, $l_4(1)=1/4$, so $p(1)=1/4\cos(0)+3/2\cos(2)-\cos(3)+1/4\cos(4)$.