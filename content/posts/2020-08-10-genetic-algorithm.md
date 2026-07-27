---
title: "How Genetic Algorithms Work"
date: 2020-08-10T16:44:04Z
tags: [genetic algorithm, optimization]
categories: [algorithms, data science]
draft: false
---

Genetic algorithms (GAs) are inspired by biology where only the fittest genes survive. It is based on Charles Darwin's Natural Selection theory. We start with 2 parent chromosomes that each contain an ordered set of genes. Each parent contributes some of their genes when they mate to create children chromosomes. There is a randomness to the mating process so that each child has a diverse set of genes. This diversity is created by the **crossover** and **mutation** processes. Over time and with sufficient genetic diversity, the fittest genes, representing optimal characteristics for the species to survive, be come dominant and are propagated. This is nature's way of optimizing over genetic diversity and we can co-opt this approach for tackling other optimization problems.

### Must Haves

  1. A suitable optimization problem to solve - GAs can be good for non-smooth, non-convex, gradient-free optimization problems
  2. Fitness function - quantitative way of evaluating solution candidates; what makes the solution good?
  3. Way to represent the solution as a chromosome 



### Examples of optimization problems tackled with GA

  * Travelling Salesperson Problem - salesman must visit every city exactly once and cover the shortest distance starting and ending at the origin city ([Link](<https://en.wikipedia.org/wiki/Travelling_salesman_problem>))
  * Learn Robot Behavior - used to teach robots how to walk ([Link](<https://towardsdatascience.com/making-a-robot-learn-how-to-move-part-1-evolutionary-algorithms-340f239c9cd2>))
  * Build a 2D car - constructs a 2D car-like object (torso and 2 wheels) optimized to travel as far as possible ([Link](<https://rednuht.org/test/simulator/>))
  * Design of water supply systems - optimize the water supply routes ([Link](<https://www.researchgate.net/publication/249643295_A_Real_Options_Approach_to_the_Design_and_Architecture_of_Water_Supply_Systems_Using_Innovative_Water_Technologies_Under_Uncertainty>))
  * Generative Art - reproduce an image with minimum number of triangles ([Link](<https://chriscummins.cc/s/genetics/>))



### (Pseudo) Code Implementation

  1. Generate 2 parent chromosomes (via tournament selection)
     * Take a small sample of random chromosomes or randomly ordered candidates
     * Choose the top 2 fittest candidates
  2. Create 1 generation of children chromosomes
     * Via one or more crossover methods
     * (Optional) mutate child chromosome with probability p by randomly swapping places of 1 pair of genes
  3. Take the top 2 fittest chromosomes (over parents and children chromosomes)
  4. Repeat Steps 2-3 to produce several generations, moving forward with the top 2 fittest candidates every generation



![](/images/Picture2.png)Illustration of mutating a pair of genes in a chromosome

**Crossover**| **Mutation**  
---|---  
Exploitation - capitalize on previous candidates found that are already somewhat fit| Exploration - find potentially new, fit candidates  
Improves average fitness of the generation| -  
Too high crossover rate could lead GA to getting stuck in a local minimum| Does not converge if mutation probability is too high; could run indefinitely  
Why we need crossover and mutation in the GA

#### Crossover Methods

  * Single Point Crossover
  * Two Point Crossover
  * Uniform Crossover



![](/images/Picture1-1.png)Illustration of crossover methods

### GA Hyperparameters

  * Number of Steps 
  * Population Size of Generation
    * too small => stuck in local minimum
  * Crossover Probability 
    * usually about 0.3
    * chance of swapping genes across 2 chromosomes
  * Mutation Probability 
    * usually about 0.1
    * chance genes swap within a single chromosome
    * too high means that the GA won't converge to global minima

**Advantages**| **Disadvantages**  
---|---  
Easy to implement using bespoke code or a package| Not guaranteed to converge to global minima, but this chance can be mitigated with high enough diversity  
-| May not be suitable to all optimization problems e.g. those where the order of the 'genes' doesn't matter  
The pros and cons of GAs
