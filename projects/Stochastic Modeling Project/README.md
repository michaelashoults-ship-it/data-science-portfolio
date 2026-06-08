# Stochastic Modeling Project: Gibbs Sampler and Yahoo Finance 

## Overview

This project was created for MA 420G: Intro to the Stochastic Process. It explores two stochastic modeling problems involving simulation and real-world data analysis. The first part implements a Gibbs sampler for a 2D lattice system to study spatial correlation and mixing behavior. The second part analyzes financial time series data to model jump events using Poisson and Hawkes processes.

---

## Problem 1: Gibbs Sampler for 2D Lattice

### Model Description

We consider a 2D lattice of size 100 × 100, where each cell takes a value of +1 or −1. A Gibbs sampler is used to simulate the system under different temperature and interaction range settings.

Each configuration evolves according to local interactions defined by a neighborhood size \(k\), and the system is studied under varying temperature values \(T\).

---

### Implementation

- Programming language: Python
- Libraries: `numpy`, `matplotlib`
- Lattice size: 100 × 100
- Parameters tested:
  - Temperature: T ∈ {0.5, 1.5, 3}
  - Interaction range: k ∈ {1, 10}

---

### Results

- Higher temperature values reduce spatial correlation, leading to more random configurations.
- Lower temperature values produce stronger clustering and more structured patterns.
- Larger interaction range (k = 10) increases spatial dependence and produces more homogeneous regions.
- Smaller interaction range (k = 1) leads to faster mixing and more local variation.

---

## Problem 2: Yahoo Finance 

### Data Description

Historical stock price data was obtained from Yahoo Finance for BlackBerry Limited (BB), covering approximately two years.

Log-returns were computed and jump events were defined as instances where the absolute daily return exceeded 3%.

---

### Jump Process Analysis

- Jump events were identified from log-return thresholds.
- Inter-arrival times between jumps were analyzed.
- The distribution of inter-arrival times was compared to an exponential distribution.
- Results suggest approximate Poisson-like behavior in jump occurrences.

---

### Hawkes Process Modeling

A Hawkes process was used to model potential self-exciting behavior in jump events.

Parameters estimated using maximum likelihood:

- Baseline intensity (μ): 0.1769660262257716  
- Self-excitation (α): 7.003542943604476e-10  
- Decay rate (β): 1.1977086565001382  

The results indicate very weak self-excitation, suggesting the process is close to a Poisson process.

---

## Tools Used

- Python
- NumPy
- Matplotlib
- Yahoo Finance API (yfinance)

---

## Key Concepts

- Gibbs sampling
- Markov Chain Monte Carlo (MCMC)
- Statistical physics models
- Spatial correlation analysis
- Poisson point processes
- Hawkes processes
- Maximum likelihood estimation

---

## Author

- Michaela Shoults 
