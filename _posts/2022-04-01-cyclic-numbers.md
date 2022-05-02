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

#### $$\mathbb{1/7}$$ and Primitive Roots

The decimal expansion of $$\frac{1}{7} = 0.\overline{142857}$$ has some interesting properties:
- It has a cycle of length $$6$$. For any integer $$k$$, the maximum possible length for a repeating decimal is $$k-1$$, as when dividing, there are $$k-1$$ possible remainder values $$\mod k$$ excluding $$0$$.
- The period also shifts for every multiple of $$\frac{1}{7}$$:

$$1 / 7 = 0.\overline{142857}$$

$$2 / 7 = 0.\overline{285714}$$

$$3 / 7 = 0.\overline{428571}$$

$$4 / 7 = 0.\overline{571428}$$

$$5 / 7 = 0.\overline{714285}$$

$$6 / 7 = 0.\overline{857142}$$

- This is because $$10 \equiv 3 $$ is a **primitive root** of $$7$$.
- **Definition:** A primitive root of a prime $$p$$ is a number $$a$$ for which $$a$$ has multiplicative order $$p-1$$, or that $$a^1, ... a^{p-1}$$ are all distinct $$\mod p$$.
- A primitive root $$\mod n$$ for $$n$$ isn't prime is defined as one with order $$\phi (n) - 1$$, where $$\phi$$ denotes Euler's totient.
- A multiplicative order of a number $$\mod p$$ can be at most $$p-1$$ (like repeating decimal length). And similarly, $$a^0, a^1, ...$$ are periodic mod $$p$$ if and only if $$\gcd(a, p) = 1$$.

In the case of $$1/7$$, indeed we go through each residue $$\mod 7$$ when we write $$10^1 \equiv 3, 10^2 \equiv 2, 10^3 \equiv 6, 10^4 \equiv 4, 10^5 \equiv 5, 10^6 \equiv 1$$. We kind of go through this process when long dividing, as you're taking the previous remainder and multiplying by 10. And, because each multiple of $$1/7$$ is starting somewhere in the cycle only later, it makes sense why each is a shift of the original.

#### Midy's Theorem
Maybe you've noticed that in $$1/7 = 0.\overline{142857}$$, The first and fourth, second and fifth, and third and sixth digits each add to $$9$$. In general, for any expansion $$a/p = 0.\overline{a_1a_2 ... a_na_{n+1} ... a_{2n}}$$ where $$p$$ is prime and $$a$$ has an even length period, $$a_i + a_{i+n} = 9$$ (the statement of Midy's Theorem).

Here's a corollary that will be helpful in the proof:
- If $$l$$ is the smallest integer for which $$p \vert 10^l-1$$, then $$a/p$$ has period length $$l$$. This is because $$a/p$$ can then be written as $$ak / 10^l-1$$ for $$pk = 10^l-1$$, which is a repeating decimal of period $$l$$.

**Proof:** We'll go back to the idea that any $$a/p = K / (10^{2n}-1)$$ for some period length $$2n$$ and where $$K$$ is the integer string of the period of $$a/p$$. $$10^n-1 \vert 10^{2n}-1$$, so we can also write this as $$am/p = K / (10^n-1)$$ (for $$m = \frac{10^{2n}-1}{10^n-1}$$). Note that $$p \vert m$$ because $$p \nmid 10^n-1$$ (then period isn't $$2n$$), so $$am/p \in \mathbb{Z}$$ we now have $$K \equiv 0 \mod 10^n-1$$. Let's split the string into two parts, $$L = a_1a_2...a_n$$ and $$R = a_{n+1}...a_{2n}$$ (left, right sides). $$0 \equiv K = 10^{n}L + R \equiv L + R \mod 10^n-1$$, and since $$0 \leq L, R \leq 10^{n}-1$$, and $$L, R$$ cannot be equal (therefore both $$0$$ or $$10^n-1$$), $$L+R = 10^n-1$$.

**Generalizations:** Midy's theorem also applies to decimals in different bases $$b$$, where repeating decimals of even length will have their left and right halves sum to a string of $$(b-1)$$'s. And, for periods of odd length (or any period length $$l = kn$$), dividing the period in $$k$$ segments of length $$n$$ sums to a multiple of $$10^n-1$$.

#### Generating Periodic Decimals

This is the same as (and about as possible as) determining the order of $$10 \operatorname{mod}$$ any other relatively prime number $$p$$.

From the earlier corollary to Midy's Theorem, we can generate some period lengths:
- $$10^1 - 1 = 9 = 3^2$$, therefore $$a/3, a/9$$ have periods of length $$1$$.
- $$10^2 - 1 = 99 = 3^2 * 11$$, therefore $$a/11$$ has a period of length $$2$$.
- $$999 = 3^2 * 37$$ means $$b/27, b \not\equiv 0 \mod 3$$ and $$a/37$$ have periods of length $$3$$.
- and so on.

---

#### Order/Primitive Roots Problems
- Prove that for all primes $$p$$ and $$a < p$$, $$a^1, a^2, ..., a^{p-1}$$ are unique $$\mod p$$ (and if you want to consequently prove Fermat's Little Theorem $$a^{p-1} \equiv 1 \mod p$$, you should do so).
- Prove Euler's Theorem, that for any $$a, n, \gcd(a, n) = 1$$, $$a^{(\phi{n})} \equiv 1 \mod n$$. 
- Show that the order of $$a \mod n$$, ($$\operatorname{ord}_n$$(a)), must divide $$\phi (n)$$.
- From two above, every prime has a primitive root. Prove that every prime has $$\phi(p-1)$$ primitive roots.

#### More Relevant Problems
- Prove the generalizations of Midy's Theorem (they use a very similar argument).
- Prove that in a repeating decimal expansion in base $$b$$ of $$1/n$$, any one digit can show up at most $$\lceil \frac{n}{b}\rceil + 1$$ times.
- (2014 AMC 12A #23) The fraction $$\frac{1}{99^2} = 0.\overline{b_{n-1}b_{n-2} ... b_2b_1b_0}$$, where $$n$$ is the length of the period of the repeating decimal expansion. What is the sum $$b_0 + b_1 + ... + b_{n-1}$$?
- Let $$K = 0.07142128... $$ where each two digits of $$K$$'s expansion form consecutive multiples of $$7$$ (and they may overlap into the previous value for large multiples). Find a rational expression for $$K$$.
- (BMT 2021) Consider a randomly generated base $$10$$ real number $$r = 0.\overline{p_0p_1p_2 ...}$$, where eac digit $$p_i$$ is a digit from $$0$$ to $$9$$, inclusive, generated as follows: $$p_0$$ is generated uniformly at random from $$0$$ to $$9$$, inclusive, and for all $$i \geq 0$$, $$p_{i+1}$$ is generated uniformly at random from $$p_i$$ to $$9$$, inclusive. Compute the expected value of $$r$$.
- Max is writing a repeating decimal number. He has one copy of each of the digits $$1$$ through $$5$$. He starts by writing $$0.$$ , then picks one of the remaining digits that hasn't been written yet and places it somewhere between $$1$$ and $$5$$ decimal places after the digit previously written, filling all in between place values with $$0$$s. Once he uses all five digits, he says that the period of the decimal is everything after the decimal point. Find the expected value of his decimal.