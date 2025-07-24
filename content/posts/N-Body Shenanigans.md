---
title: Optimized Real Time N-Body Simulation - Part 1 Quad Tree
date: 2025-06-14
tags:
  - simulations
  - optimizations
  - cpp
  - in_progress
---
# N-body Shenanigans (Writing In Progress)
![Image Description](/images/Pasted%20image%2020250704025301.png)

We've all seen those cool simulations colliding or a black hole sucking everything up. I find them pretty cool to look at. Wondering how every particle is simulated made me even more interested and also broke my brain. Eager to satisfy this curiosity and not let my braincells die in vain, I put my self through the long arduous journey of trying to make my own. Of course the fruits of this quest blessed the world with the fantastically written (you have been warned) n-body simulation optimized with parallelized quad-tree constructions using morton order sorting capable of running 200,000 independent particles in real-time!

If you have no idea what either of those words mean, neither did I a couple weeks ago. But do not worry, after reading this we will both be super-experts in optimizing n-body simulations.

## Simple Pair Interactions

The simulation initially employed the Brute Force N-body Method, which is a direct approach whereby the gravitational attraction between each pair of particle is calculated. At a given timestep, the net force acting on a particle is computed, and its positions and accelerations are updated using Euler’s Method for numerical integration as follows:  
$$
\mathbf{a}_i^n = -G \sum_{\substack{j=1 \\ j \neq i}}^{N} m_j \frac{\mathbf{r}_j^n - \mathbf{r}_i^n}{\left( \| \mathbf{r}_j^n - \mathbf{r}_i^n \|^2 + \epsilon^2 \right)^{3/2}}
$$