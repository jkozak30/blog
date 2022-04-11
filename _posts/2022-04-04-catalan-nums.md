---
title: Catalan Numbers
auth: Julia Kozak, Maxwell Ito
layout: post
categories: [Math, Computer Science, Number Theory]
image: assets/img/logo.jpg
# my computer ... png .......
description: "Catalan Numbers"
published: true
---

There are a lot of ways to define Catalan Numbers. We'll number a few of them one by one.

#### Diagonal-Avoiding Paths
- This is probably the interpretation that is easiest to get an implicit formula from. 
- Take an $$n \times n$$ grid, going from $$(0, 0)$$ to $$(n, n)$$, and consider the number of paths to get from the bottom left corner to the top right corner such that you do not cross over the line $$y=x$$ (you may be on the diagonal however). How many ways are there to find such a path, going only right or up each move?

{insert diagram}

**One way to think about it** is in terms of the sequence of moves, where we'll say $$R$$ is right and $$U$$ is up. For an $$n \times n$$ grid, we need a total of $$n$$ of each move, ordered in some way (with constraints). If we could order them in any way to get a path, that is essentially just solving the problem of how many ways to get to $$(n, n)$$ in any way, which is also choosing $$n$$ of your $$2n$$ moves to be $$R$$, and the other $$n$$ to be $$U$$. This is $${2n \choose n}$$. But, the added condition is that you can't go more times up than right at any point, because then $$y > x$$, and you're above the diagonal.

**So,** let's subtract off the cases that do this. 

{insert diagram}

Let's consider an arbitrary path that crosses the diagonal. At the point where it passes the diagonal, reflect the rest of the path at $$y=x+1$$. Basically, at the point where you've made an invalid move, swap each next move, where $$R$$ changes to $$U$$ and $$U$$ to $$R$$. Then, our final landing position shouldn't be at $$(n, n)$$ but $$(n-1, n+1)$$. And, there is a one to one correspondence between invalid paths and paths going to this point, as any path to $$(n-1, n+1)$$ will pass $$y=x$$ at some specific point, meaning we can retrace the path corresponding to $$(n, n)$$.

**Now,** we can get a closed formula. The $$n$$th Catalan number $$C_n$$ is defined as this number of paths, which is $${2n \choose n} - {2n \choose n+1} = \frac{1}{n+1}{2n \choose n}$$.


#### Another Interpretation: Matched Parenthesis

- There are different scenarios that are essentially the same as the diagonal-avoiding path scenario, one of which is solving for the number of ways to order $$n$$ pairs of parenthesis such that each given pair is placed correctly.
- For instance, for $$n=3$$, $$()(())$$ is correct, but $$(()))($$ is not correct.

**Solving this** relies on the observation that, for an arrangement to be valid, there must be at least one opening parenthesis that hasn't been closed yet it order for it to be valid that you place a closing parenthesis. So, this is exactly the same as diagonal-avoiding. You need at least as many open parenthesis at any point as closing parenthesis.

Here's my (Max's) implementation in JavaScript (CoderByte problem code):

```javascript
function BracketCombinations(num) {

    function numPoss (open, closed) {
        if (open == 0 && closed == 0)
            return 1;
        var res = 0;
        if (open > 0)
            res += numPoss(open - 1, closed);
        if (closed > open)
            res += numPoss(open, closed - 1);
        return res;
    }
    // code goes here  
    return numPoss(num, num);
}

   
// keep this function call here 
BracketCombinations(readline());
```

It uses the same idea as stated, defined recursively. The function <code>numPoss</code> will track the number of open and closed parenthesis at any point. The recursion terminates at <code>open = closed = 0</code>. For any other case, if there are open parenthesis to be placed, the first case will add the possibilites in which you placed one. It could also be possible (though not mutually exclusive) that you can place a closed parenthesis (when there are more open then closed), which is dealt with in the second case.

With this, **let's also define Catalan Numbers recursively**. For some sequence that is a case of $$C_n$$, consider the subsequence of parenthesis that is in between the first parenthesis, which must be open, and the closing parenthesis corresponding to that first parenthesis. Now, for everything in between those two, it must be true that the subsequence is also a valid pairing of $$k$$ parenthesis pairs, where $$0 \leq k < n$$. Also, everything to the right of that closing parenthesis is also a valid pairing of $$n-k-1$$ pairs. So, placing our first pair is essentially splitting two valid sequences that are cases of $$C_k$$ and $$C_{n-k-1}$$. 

Recursively, $$C_n = C_{n-1}C_0 + C_{n-2}C_1 + C_{n-3}C_{2} + ... + C_1C_{n-2} + C_0C_{n-1}$$.

#### Polygon Triangulations

This recursive definition applies to a new situation. The problem is: how many ways are there to triangulate a regular $$n+2$$-gon? It turns out to be $$C_n$$.

{insert diagram}

- Here's how to do it inductively/recursively. Assume it is true for all $$<n+2$$-gons. 
- Pick a side, and draw a triangle by picking one other vertex to connect the endpoints of the side to. You've split the polygon into a triangle, and $$1$$ or $$2$$ other convex polygons that can be triangulated similarly. For instance, if you picked the vertex directly to the left of the side, you get two new polygons, $$2$$-gon and $$n-1$$-gon. If you picked the next vertex, you get a $$3$$-gon and $$n-2$$-gon.
- You can get every pair of $$k$$-gon and $$n-k+1$$-gon, for $$2 \leq k < n-2$$. 
- So, using our inductive hypothesis, the total is $$C_{0}C_{n-1} + C_{1}C_{n-2}+ ... + C_{n-1}C_0$$, which is $$C_n$$.

#### Binary Tree Counting

{insert diagram}

This also ends up being equal to the total number of binary trees with $$n$$ internal nodes. 
- **Definition:** a binary tree is an arrangement of nodes with a root such that every node descending from the root terminates, or leads to two more nodes.
- An internal node is one vertex that has two descending nodes.
- Every binary tree will have a unique root.

This follows from a similar argument to the one for polygon triangulations. Your top vertex leads to two new binary trees, which will have $$k, n-k-1$$ internal vertices, for each $$0 \leq k < n$$. So, you get the recursive definition once again.

There's actually a one to one correspondence between polygon triangulations and binary trees, if you were to give each triangle within your polygon a vertex, and connect it to the triangles it shares a side with.

{insert diagram}


#### Generating Function $$\sum_{i=1}^{\infty}C_nx^n$$

- Let's get a closed form for $$\sum_{n=0}^{\infty}C_nx^n$$ for a certain $$x$$.
- Let $$y = \sum_{n=0}^{\infty}C_nx^n$$. 

- $$\sum_{n=0}^{\infty}C_{n+1}x^n = \sum_{n=0}^{\infty}(\sum_{k=0}^{n}C_{k}C_{n-k})x^n.$$

Now we can rewrite:
- $$x\sum_{n=0}^{\infty}C_{n+1}x^n = \sum_{n=1}^{\infty}C_{n+1}x^n = y-1.$$

We also know that $$\sum_{k=0}^{n}C_{k}C_{n-k}$$ is the coefficient of $$x^n$$ in $$y^2 = (\sum{n=0}{\infty}C_nx^n)^2$$, if we consider pairwise factors coming from each $$y$$.

The coefficient is then:
- $$\frac{y-1}{x} = y^2.$$
- $$xy^2 - y + 1 = 0. $$

Now we can solve for y:
- $$y = \frac{1 \pm \sqrt{1-4x}}{2x}.$$

Which sign is correct? Let's consider the $$C_0$$ term in that case. If it were the case that the sign should be $$+$$, then as $$x \rightarrow 0$$, $$y \rightarrow \infty$$, which wouldn't make sense.

#### Problems
- How many ways are there to get from $$(0, 0)$$ to $$(6, 6)$$ along lattice points and going only right or up such that you do not enter the region $$y > x$$?
- (Ballot Problem) Two candidates, $$A$$ and $$B$$ are in an election, and each of them receives $$n$$ votes. What is the probability that $$A$$ will never have less votes than $$B$$?
- (PUMaC 2021) Nelson is having his friend drop his unique bouncy ball from a $$12$$ foot building, and Nelson will only catch the ball at the peak of its trajectory between bounces. On any given bounce, there is an $$80\%$$ chance that the next peak occurs at $$\frac{1}{3}$$ the height of the previous peak and a $$20\%$$ chance that the next peak occurs at $$3$$ times the height of the previous peak (where the first peak is at $$12$$ feet). If Nelson can only reach $$4$$ feet into the air and will catch the ball as soon as possible, what is the probability that Nelson catches the ball after exactly $$13$$ bounces?
- You have two types of parenthesis, brackets $$[]$$ and curly braces $$\{\}$$. How many ways are there to arrange $$5$$ pairs of brackets and $$3$$ pairs of curly braces such that each pair is valid (through code or mathematically)? How many ways are there for $$m$$ bracket pairs and $$n$$ curly braces pairs?