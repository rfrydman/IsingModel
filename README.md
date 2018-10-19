# PHYS250 assignment 3: Ising Model

In this assignment, you will fully simulate and then evaluate the 2-dimensional Ising model for system of spins that can be either spin up or spin down. There are several parts or exercises to this assignment, so read carefully and please ask questions if anything is unclear! 

*Please note:* I will give you much of what needs to be used here, and we will actively develop some of it in lectures during Week 4 as well, so don't get too worried about the apparent length. 

Also, Excercises 1-6 are effectively meant to walk you through the development phase of the computational algorithm. If you have your own conception of the design of this piece of software that you wish to use, please feel free to do so, as long as it is sufficiently well documented what you have done and how to run it. 

## Exercise 1: basic lattice setup
Here I just want you to write a few functions that will fill a lattice. I will provide some suggestions in the Jupyter notebook provided as a starting point. 

I suggest that you create 3 functions:
1. `normallattice`: create $N\times M$ lattice with uniform spin values
1. `randomlattice`: create $N\times M$ lattice with random spin values
1. `plotlattice`: plot an image of the lattice with a colour code for the spin

## Exercise 2: Randomly choose & flip a lattice point
We now need two functions:
1. a function to randomly select one of the particles in the lattice and return its coordinates $(i,j)$. 
1. a function to flip the spin of the particle pointed by the $(i,j)$ indices and return the new lattice state.

## Exercise 3: Nearest neighbors
A key element of this model is calculating the combined spin state of the 4 nearest neighbors around a given lattice point $(i,j)$.

Write a function to return the combined spin state and which respects periodic boundary conditions.

I suggest that you develop your code with a *small*, say, 5x5 lattice. Once you have convinced yourself that this functions correctly, you can move to the next item and also expand your lattice (no use debugging a big model that takes lots of time to evaluate).

## Exercise 4: Calculating the energy of the lattice
The local energy is defined as the total interaction energy between the selected particle and its immediate neighbours. 

1. write a function to calculate this.
1. also write a function to calculate the total energy of the lattice.

Again, I suggest that you perform some tests with a simple 5x5 lattice, for example:
1. Compare the energy of the lattice for different configuations of spins. 
1. What is the total energy of the system when all spins point up or down or randomly? 

## Exercise 5: Calculate the magnetisation of the lattice
Implement functions to calculate 

1. The total magnetisation of the lattice
1. The magnetisation per spin

Again, I suggest that you perform some tests with a simple 5x5 lattice first, for example:
1. What will be the value of $m$ if all spins are aligned up? what if all the spins are aligned down? What if half of the spins are up and half are down?
1. Set an initial condition with $m = 1.0$, that is all the spins point up. Try to perturb a few particles and recalculate the magnetisation

## Exercise 6: Implement the Metropolis algorithm
At this point in your the code you should have all the nesscessary functions properly implemented and the thermodynamic simulation of the system can take place. 

1. Set up the system in an initial configuration
1. Choose one of the particles at random using a Markov Monte Carlo approach
1. Calculate the energy change $\Delta E$ of the system if the spin of the chosen particle is flipped
1. If $\Delta E$  is negative, then select to flip the spin and go to step 7, otherwise ....
1. Generate a random number $r$ such that $0 < r < 1$
1. If this number is less than the probability of $\Delta E$ i.e. $r < \exp(-\Delta E/k_B T)$, then flip the spin. 
1. Choose another spin of the lattice at random and repeat steps 2 to 6 a chosen number of times ($N_{MCS}$)

## Exercise 7: Perform measurements 
Calculate the average magnetisation, average energy, and specific heat of the equilibrated system. If you perform many simulations at different temperatures, you should be in a position to observe phase transitions and measure the transition or Curie temperature, $kT_c$. 

