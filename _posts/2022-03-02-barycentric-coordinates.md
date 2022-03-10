---
title: Mass Points and Barycentric Coordinates
auth: Julia Kozak
layout: post
categories: [Math, Geometry]
image: /assets/img/logo.jpg
description: ""
published: true
---

#### Mass Points as a Physics Problem

Given some center of mass on a segment, **mass points** allows you to assign relative masses to two other points given their lengths from the center. The conclusion comes to, if your center $$C$$ is a distance $$r_A$$ from point $$A$$ and $$r_B$$ from $$B$$, you can assign masses $$k * r_B$$ to $$A$$ and $$k * r_A$$ to $$B$$, where $$k$$ is some constant, to balance their masses at $$C$$. Then (for mass points reasons) you can assign mass $$k *(r_A + r_B)$$ to $$C$$.
![](../../../assets/img/screenshots/Screenshotmp.png)
(sorry for the differently labeled diagram) In the example, $$A$$ has mass $$3$$ and $$C$$ has mass $$5$$ because $$\frac{AB}{BC} = \frac{5}{3}$$.

If we call the mass and distance to center $$C$$ of $$A$$, $$m_A$$ and $$r_A$$, respectively and for $$B$$, $$m_B$$ an $$r_B$$, we can see that $$m_Ar_A = m_Br_B$$. It kind of looks like a physics problem! If you've ever seen the torque problem of two people balancing on a seesaw or something of the sort, you'll recognize that if you were to place segment $$AB$$ (referring to the earlier $$AB$$, I will change the diagram) on a fulcrum at $$C$$, with those given masses, it will balance. 

Quick summary of torque. It's rotational force, as in, something measuring the strength of a change in the rate of rotation. Its equation is given by $$\tau = rF\sin\theta$$, where $$r$$ is your distance from the point of pivot (it makes sense that it would be greater for larger radius), $$F$$ is your directly applied force, and $$\theta$$ is the angle that your pivot point makes with the applied force. In this situation, with gravity, the two points $$A, B$$ will exert downward force perpendicular to the pivot point, and we want their torques to be of equal magnitude (and opposite direction). So, we can set $$\tau_A = \tau_B$$ or $$r_AF_A\sin\theta_A = r_BF_B\sin\theta_B$$, if we only consider the magnitude of each $$F$$. $$\theta_A = \theta_B = 90^\circ$$, so sine expressions cancel, and so will gravitational constants for $$F_A$$ and $$F_B$$, so we are left with $$r_Am_A = r_Bm_B$$. And the force on the segment acts directly on $$C$$, so $$C$$ experiences the force of mass $$m_A + m_B$$ (which explains the mass given to $$C$$). 

