---
title: Complex Numbers - Gaussian Integers, Gaussian Primes
auth: Julia Kozak
layout: post
categories: [Math, Number Theory]
image: /assets/img/gua.jpg
description: "Intro to Complex Numbers in problems, and applied Gaussian Integers"
published: true
---

Intro to Complex Numbers in problems, and applied Gaussian Integers.


#### Background/Definitions
 - The set of complex numbers $$ \mathbb{C}[i] $$ consists of all expressions $$\text{a} + \text{b}i$$ where $$\text{a, b}$$ are real numbers and $$ i $$ is the imaginary unit.
 - Every complex number $$z = \text{a} + \text{b}i$$ can be mapped to point $$(\text{a}, \text{b})$$ in the complex plane. Likewise, $$z$$ can be expressed in polar form $$ re^{i\theta} = r(\cos\theta + i \sin\theta)$$ or $$r\text{cis }\theta$$, where $$ (r, \theta)$$ is the polar form of $$(\text{a}, \text{b})$$.
 - $$r = \sqrt{a^2+b^2}$$ is called the **modulus** or norm of $$z$$, $$\lvert z \rvert$$. $$\theta$$, the angle that segment $$\text{OZ}$$ makes with the terminal position, is called the **argument**, $$\arg(z)$$.
 - The conjugate of $$z$$, $$\overline{z}$$, is the reflection of $$z$$ over the real axis, or $$\text{a} - \text{b}i$$.

*Exercises:*
 - Find $$r$$ and $$\theta$$ for $$z = \frac{-1+\sqrt{3}i}{4}$$.
 - Find all $$z$$ such that $$z^3 = \overline{z}$$.
 - Compute $$(1+i)^{132}$$.
 - Prove $$\lvert z \rvert\lvert w \rvert = \lvert zw \rvert$$.
 - Compute $${n \choose 0} - {n \choose 2} + {n \choose 4} - ...$$

#### Rotations of Complex Numbers, De Moivre, Roots of Unity
Given $$z = re^{i\theta}$$, consider multiplying by $$w = se^{i\phi}$$. Using our $$\text{cis }\theta$$ definition:

 - $$ zw =  r\text{cis }\theta * s\text{cis }\phi$$

 - $$ = rs(\cos\theta + i\sin\theta)(\cos\phi + i\sin\phi)$$

 - $$ = rs(\cos\theta\cos\phi - \sin\theta\sin\phi + i(\sin\theta\cos\phi + \cos\theta\sin\phi))$$

 - $$ = rs(\cos(\theta + \phi) + i\sin(\theta + \phi))$$

 - $$ = rs\text{ cis }(\theta + \phi)$$

So, multiplying $$z$$ by a complex number $$w$$ results in a **rotation** by $$\arg(w)$$, and a **dilation** by $$\lvert w \rvert$$. 

---

Here's an example of the rotation part, in the context of AIME 1994 Problem 8:

*Problem:* The points $$(0, 0) , (a, 11) ,$$ and $$(b, 37)$$ are the vertices of an equilateral triangle. Find the value of $$ab$$.

*Solution:* Consider these points in the complex plane, where our vertices are $$ O = 0, X = a + 11i,$$ and $$Y = b + 37i$$. $$Y$$ is a $$60^\circ$$ rotation of $$X$$ about $$O$$, so we can set up:
 - $$ (a + 11i)\text{ cis}(60) = b + 37i$$
 - $$ \frac{a - 11\sqrt{3}}{2} + \frac{11 + a\sqrt{3}}{2}i = b + 37i$$

Equating real and imaginary parts:
 - $$ \frac{11 + a\sqrt{3}}{2} = 37 \rightarrow a = 21\sqrt{3}$$
 - $$ b = \frac{a - 11\sqrt{3}}{2} = 5\sqrt{3}$$
 - $$ ab = \fbox{315}$$

---

**De Moivre's formula** applies this by stating that $$[r \text{ cis }\theta]^n = r^n \text{ cis }(n\theta)$$. This follows from an induction on repeated multiplication by $$r \text{ cis }\theta$$, using the statement of the proof for rotations/dilations.

The $$n$$th **roots of unity** are the solutions to $$z^n = 1$$. In particular, they will be $$1, \zeta, \zeta^2, ... \zeta^{n-1}$$, where $$\zeta = e^{i\frac{2\pi}{n}}$$ And since the roots are evenly spaced rotations of each other along a unit circle, they will map to the vertices of a regular $$n$$-gon.

*Exercises:*
 - A primitive $$n$$th root of unity $$\zeta$$ is a complex number that satisfies $$\zeta^n = 1$$ and $$\zeta^k \neq 1$$ for all positive integers $$k < n$$. Find the number of $$2022$$nd primitive roots of unity.
 - (AHSME 1984) If $$\omega = \cos 40^\circ + i\sin 40^\circ$$, find $$\lvert \omega + 2\omega^2 + ... + 9\omega^9 \rvert^{-1}$$.
 - Let $$1, \zeta, ..., \zeta^{n-1}$$ be the $$n$$th roots of unity. Prove that $$1 + \zeta + ... + \zeta^{n-1} = 0$$.

#### Gaussian Integers and Primes 

**Gaussian integers** $$\mathbb{Z}[i]$$ form a subring of $$\mathbb{C}[i]$$, and all elements are of the form $$\text{a} + \text{b}i$$ where $$a, b \in \mathbb{R}$$. They are the lattice points of the complex plane. 

**More Definitions:**
 - We say a Gaussian integer $$z$$ **divides** $$w \in \mathbb{Z}[i]$$ if there exists $$ u \in \mathbb{Z}[i]$$ such that $$w = u*z$$.
 - A Gaussian integer is **invertible** if $$\frac{1}{z}$$ is also a Gaussian integer, or that it has a multiplicative inverse within $$\mathbb{Z}[i]$$.
 - Note that $$\lvert z \rvert \in \mathbb{Z}$$  $$ \forall z \in \mathbb{Z}[i]$$.
 - $$\operatorname{N}(z)$$ is defined as $$\lvert z\rvert^2$$.

One property is that $$\pm 1 $$ and $$\pm i$$ are the only invertible Gaussian integers, which seems evident by the fact that squares of norms $$\operatorname{N}(\frac{1}{z})\operatorname{N}(z)= \lvert 1\rvert^2 = 1$$ cannot both be integral if they are not both equal to $$1$$. This implies $$z = a+bi$$ has one of $$(a,b)$$ equal to $$0$$, and the other $$\pm 1$$, as $$a, b \in \mathbb{Z}$$. And we can check that $$\pm 1, \pm i$$ all have multiplicative inverses in $$\mathbb{Z}[i]$$. We can also see that all four of these will divide any Gaussian integer, just potentially switching signs or coefficients.

 - We say $$z$$ is a **Gaussian prime** if its only Gaussian prime factors are $$z\epsilon$$ and $$\epsilon$$, where $$\epsilon \in \{ -i, i, -1, 1\}$$.

---
*Example 1:* Show that $$2$$ is not a Gaussian prime.

*Solution:* To disprove this, we need to find two complex Gaussian factors, neither of which are invertible, that will multiply to $$2$$. This will be $$(1+i)(1-i)$$ or $$(-1+i)(-1-i)$$.

*Example 2:* Show that $$3$$ is a Gaussian prime.

*Solution:* If $$3 = wz, \lvert 3 \rvert^2 = \lvert w \rvert^2 \lvert z \rvert^2$$. So, to try to disprove this, we will need two complex Gaussian factors, neither of which are invertible, whose squares of norms multiply to $$9$$. They must either have norms $$\pm 1$$ and $$\pm 9$$, or each $$\pm 3$$. The first case doesn't work because a Gaussian integer with norm $$\pm 1$$ must be invertible, and the second case does not either because we cannot find an integer sum of squares equal to $$3$$.

---

Something that you may have noticed is that each Gaussian integer has a unique factorization if you do not pay attention to factors of invertible Gaussian integers. For instance, $$2 = (1+i)(1-i)$$. There exists a **unique Gaussian prime factorization** for every $$\mathbb{Z}[i]$$:
 - As a first step, we can show that arbitrary Gaussian integer $$z$$ will have some finite expansion of Gaussian integer factors. If $$z$$ is prime, we are done. Otherwise, we know we can divide $$z = w_1*w_2$$ for $$w_1, w_2 \in \mathbb{Z}[i]$$, where $$\lvert w_1 \rvert$$ and $$\lvert w_2 \rvert$$ are strictly less than $$\lvert z \rvert$$. Now, repeat for the two new factors. The fact that any future factorization will result in two factors that are at least $$1$$ less in norm than your prior value forces your expansion to terminate, as $$\lvert z \rvert$$ is only finitely large.
 - Now, we must prove this is unique. So, assume we have two unique expansions $$z = w_1 * w_2 * ... * w_j = v_1 * v_2 * ... * v_k$$, where all $$w_i, v_i$$ are Gaussian primes. Now consider $$w_1$$. It must be true that $$w_1 \lvert v_1 * ... v_k$$. But since all values we are working with are Gaussian primes, it must be the case that $$w_1 = \epsilon v_l$$ for some $$l \in [1, k]$$. Disregarding $$\epsilon$$, we can cancel in our equation to get $$w_2 * ... w_j = v_1 * ... * v_{l-1} * v_{l+1} * ... * v_k$$. We can repeat this for every $$w_i$$, at which point we have to have canceled every factor on the right as well to get an expression equivalent to $$1$$. So, the two are equivalent.

#### Sums of Squares and Integer Primes

We can derive many properties about $$4k+1$$ and $$4k+3$$ primes based on Gaussian integers. 


The first is that any $$4k+3$$ prime is necessarily a Gaussian prime, which we can show in a way similar to example 2. If $$p$$ is an integer prime $$ \equiv 3 \text{ mod } 4$$ and $$p = z * w$$ for $$z, w \in \mathbb{Z}[i]$$,  we must have $$\operatorname{N}(z) = \operatorname{N}(w) = p$$, otherwise one of them is equal to $$1$$. But a sum of integer squares cannot be $$3 \text{ mod } 4$$, so we are done.

The second is that any $$4k+1$$ prime is not a Gaussian prime, and can be written as a sum of squares. The key part to this proof is that $$-1$$ is a quadratic residue $$\text{mod } p$$, which can be shown with Wilson's theorem:

 - $$ -1 \equiv (p-1)! = 1 * 2 * ... * \frac{p-1}{2} * \frac{p+1}{2} * ... * (p-1)$$


Note that the latter half of the terms is just the first half with each term negated.
 - $$ = (\frac{p-1}{2})! * (-1)^{\frac{p-1}{2}} \equiv (\frac{p-1}{2})!$$


Which is an integer square. From this, we have that, for some $$x$$, $$p \lvert (x^2+1) = (x+i)(x-i)$$. But since $$p$$ cannot divide $$(x+i)$$ or $$(x-i)$$, we require that $$p$$ is not Gaussian prime. Therefore, we have $$p = z*w$$, and for neither to be invertible, $$\operatorname{N}(z) = \operatorname{N}(w) = p$$, or that $$p = a^2+b^2$$ for $$z = a+bi$$.

And lastly, any $$p = a+bi$$,where $$a^2+b^2$$ is an integer prime, is a Gaussian prime. This follows directly from setting $$\operatorname{N}(p) = \operatorname{N}(z)*\operatorname{N}(w)$$, where we see that one of $$\operatorname{N}(z), \operatorname{N}(w)$$ must be $$1$$.

#### Problems
 - Let $$A$$ be the set of all Gaussian integers $$z$$ such that $$z^4-2016i$$ is real. Find $$\sum_{z \in A}\operatorname{N}(z)$$.
 - Find the number of Gaussian integers $$z$$ with magnitude less than $$10000$$ such that there exists a different Gaussian integer $$w$$ such that $$z = w^4$$. 
 - Find all integer solutions to $$x^2+4 = y^3$$.
 - Prove that an integer with exclusively $$4k+1$$ prime factors is the sum of squares.
 - Prove that an integer with no prime factors of the form $$4k+1$$ cannot be the hypotenuse of a pythagorean right triangle.
 - Prove that $$1000009 = 235^2+972^2$$ is not a prime.

#### Resources
 - https://www.maths.nottingham.ac.uk/plp/pmzcw/download/fnt_chap5.pdf
 - http://math.uchicago.edu/~may/REU2012/REUPapers/Woodbury.pdf
 - https://web.evanchen.cc/handouts/cmplx/en-cmplx.pdf
 - https://mathweb.ucsd.edu/~alina/oldcourses/2012/104b/zi.pdf

