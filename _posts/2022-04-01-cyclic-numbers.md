---
title: Cyclic Numbers
auth: Julia Kozak
layout: post
categories: [Math, Number Theory]
image: assets/img/logo.jpg
# my computer ... png .......
description: "Cyclic Numbers"
published: true
---

#### Decimals and Modular Arithmetic

Let's say we wanted to write $$0.\overline{315}$$ as a fraction.

Converting a repeating decimal to its fractional form usually follows the following process:
- Set $$x$$ to equal your repeating decimal.
- If $$x$$ is of length $$n$$ digits, consider $$x * 10^n$$.
- Subtracting $$x$$ from this cancels your repeating decimal and produces a finite integer expression equal to $$(10^n - 1)x$$. So, solve for $$x$$.

So, for $$0.\overline{315}$$, we do the following:

$$x = 0.\overline{315}$$

$$1000x = 315.\overline{315}$$

$$999x = 315$$

$$x = \frac{35}{111}$$

It's then known that every repeating decimal can be written as a rational number. And from this process, we see that all rationals $$a/b < 1, \operatorname{gcd}(a, b) = 1$$ that strictly repeat $$(*)$$ are of the form $$m / (10^p-1)$$, where $$p$$ is the length of the period of the decimal (more generally, all rationals look like $$n / 10^k(10^p-1)$$ for some $$n, k$$ and period $$p$$). Let's say $$a/b = m / (10^p-1)$$.

Then we have $$a(10^p-1) = bm$$. And since $$\operatorname{gcd}(a, b) = 1$$, we have $$b \equiv 1 \mod{10^p} $$.

$$(*)$$ Define a number to strictly repeat if there is no leading portion to its repeating decimal that differs from the repeating portion, i.e. it is periodic starting at its tenths digit. For example, $$1/11 = 0.\overline{09}, $$ $$1/37 = 0.\overline{027}, 1/7 = 0.\overline{142857}$$ are strictly repeating. $$1/18 = 0.0\overline{5},1/35 = 0.02857\overline{142857}, 1/2 =$$ $$ 0.5\overline{0}$$ are not strictly repeating. A rational number is strictly repeating if and only if its denominator is relatively prime to $$10$$. This is because factors of $$2$$ and $$5$$ only shift the period, as, if not of the form $$1/2^a5^b$$ (in which case it terminates), the rational can be written as a power of $$10$$ scale of another strictly repeating decimal, in which case it doesn't strictly repeat.

#### $$\mathbb{1/7}$$

The decimal expansion of $$\frac{1}{7} = 0.\overline{142857}$$ has an interesting property, because it has a cycle of length $$6$$. For any integer $$k$$, the maximum possible length for a repeating decimal is $$k-1$$, as there are $$k-1$$ possible remainder values $$\mod k$$ excluding $$0$$.