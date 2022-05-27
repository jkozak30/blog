---
title: Continued Fractions and Radicals
auth: Julia Kozak
layout: post
categories: [Math]
image: assets/img/sqwoo.jpg
# my computer ... png .......
description: "Infinity."
published: true
---

<p style="color: rgb(255, 255, 200, 0.6);">I'll probably keep this one short. Sorry if it's not too thorough.</p>

Here's an expression:

$$a_0 + \frac{1}{ a_1 + \frac{1}{  a_2 + ...  } }$$

where each $$a_i \in \mathbb{Z}$$.

This **continued fraction** occasionally shows up in problems and holds some interesting properties regarding radical expressions.

#### Rationals as Continued Fractions

There is a general recursive method for writing a rational $$m/n$$ in the form above, and it is given as:
- $$a_n = \lfloor \frac{K_n}{K_{n+1}} \rfloor$$,
- where $$K_{0} = m/n, K_{1} = 1$$, 
- and $$K_{n+1} := K_{n-1} \mod K_n$$,
- terminating when $$K_{n+1} = 0$$.

Here's an example:
- Let's say you want to write $$\frac{28}{13}$$ as a continued fraction.
- First, we'll take the floor of $$m/n$$. This will give us integer part $$2$$ that we'll set to $$a_0$$. 

$$2 + \frac{1}{ a_1 + \frac{1}{  a_2 + ...  } }$$

- Then, we'll take the remaining part, $$2/13$$, and find the floor of $$13/2$$ to give us an integer part to the denominator.

$$2 + \frac{1}{ 6 + \frac{1}{  a_2 + ...  } }$$

- We repeat with the remaining part, $$1/2$$. That just remains as $$1/2$$:

$$2 + \frac{1}{ 6 + \frac{1}{  2 } }$$

- We essentially take the integer part off each time and repeat on the remaining fraction that is strictly less than $$1$$.

We can observe uniqueness of the expression for every rational. We also know that it must terminate for every rational, because given that the remaining part on the next step must be a rational less than $$1$$, the numerator is less than the denominator therefore the sequence of denominators is strictly decreasing until it terminates at, at latest, $$1/2$$.

#### Irrationals as Continued Fractions

We can also say uniqueness exists for irrationals, as we've defined sequences $$\{ a_n \}$$ and $$\{ K_n \}$$.

A periodic continued fraction "repeats" when there exist values $$N, c$$ for which, for all $$M \geq N,$$ $$a_{M} = a_{M+c}$$ (and $$\{ a_n \}$$ does not terminate). The minimum possible value for $$c$$ is the period length.

It turns out that every square root expression has a periodic continued fraction, and here's some intuition as to why.
- Take a radical expression, for instance, $$\phi = \frac{1+\sqrt{5}}{2}$$. This is also a solution to the equation $$x^2+x-1=0$$.
- We can write this as $$(x)(x+1) - 1 = 0$$, or $$x = \frac{1}{x+1}$$.
- We can continuously substitute $$x$$:

$$x = \frac{1}{1+x}$$

$$x = \frac{1}{1 + \frac{1}{1+x}}$$

$$x = \frac{1}{1 + \frac{1}{1+\frac{1}{1+x}}}$$

Which is basically $$a_0=1, a_i=1 \ \ \forall \ \ i > 0$$.

A different approach is:
- Consider the point at which a continued fraction starts repeating. For instance, if  $$\{ a_n \} =$$  $$\{ 5, 2, 4, \overline{2, 3}\}$$, consider $$\{  \overline{2, 3}\}$$.
- For this example, we then have:

$$x = 2 + \frac{1}{3 + \frac{1}{2 + \frac{1}{3 + \frac{1}{...}}}} = 2 + \frac{1}{3 + \frac{1}{x}}$$

- So, we have equation $$3x^2-6x-2 = 0$$.
- This is also $$3(x)(x-2) = 2$$, sort of similar to the first example.
- Essentially any quadratic root (so any radical expression) will work in this way. Any repeating continued fraction can have its value substituted at the point it is periodic, which will result in an equation of the form $$k = \frac{ax+b}{cx+d}$$ and a quadratic solution.

#### Other Things

These can be used for square root approximation. For instance:

$$\sqrt{2} = 1 + \frac{1}{2 + \frac{1}{2 + \frac{1}{2 + ...}}}$$

This value increases and converges to $$\sqrt{2}$$ as we continue to expand out more $$a_i$$'s, but the first few can give us a pretty good estimate of $$\sqrt{2}$$. By $$a_5$$, we already have $$\frac{99}{70} = 1.4\overline{142857}$$.

There are also some continued fractions (of different forms) expressions for pi:

- $$\pi = 2 + \frac{2}{1 + \frac{1}{1/2 + \frac{1}{1/3 + \frac{1}{1/4 + ... }}}}$$

- $$\pi = 3 + \frac{1^3}{6 + \frac{3^3}{6 + \frac{5^3}{6 + \frac{7^3}{6 + ...}}}}$$

---

#### Problems

- Find a continued fraction expansion for $$\sqrt{17}$$.
- Find a continued fraction expansion for $$\sqrt{k^2+1}$$ for general $$k$$.
- Find the exact value of $$1 + \frac{1}{2 + \frac{4}{2^2 + \frac{4^2}{2^3 + \frac{4^3}{2^4 + ...}}}}$$.
- (this feels somewhat relevant) Find the exact value of $$\sqrt{1 + 2\sqrt{1 + 3\sqrt{1 + 4\sqrt{1 + ...}}}}$$.