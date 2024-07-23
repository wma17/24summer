---
title: "Week1"
---

<script type="text/javascript"
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.0/es5/tex-mml-chtml.js">
</script>

# Week 1

Topic: Bayesian Optimization

Keynote Speaker: Wang Ma

Time: Jul 22, 20:00 - 21:30 pm

Venue: Room 314, School of Business

Tencent Meeting: #907-2153-6929 

## Compendium

### Introduction
Bayesian Optimization (BO) is a machine-learning-based method for optimizing expensive, noisy, and black-box functions without gradient information. It excels in high-dimensional spaces (typically dimension is less than 20) and is used in applications like hyperparameter optimization, algorithm tuning, and materials discovery.

### 1. Problem Setup
BO aims to solve:
$$\hat{x} = \max_{x \in A} f(x)$$
where f is continuous, derivative-free, expensive, and possibly noisy. 

### 2. Bayesian Optimization Algorithm
1. Assume a Bayesian prior on $f$.
2. Iteratively:
   - Maximize the acquisition function to find the next point.
   - Evaluate the function at this point.
   - Update the posterior distribution on $f$.

### 3. Gaussian Process Model
A Gaussian Process (GP) models $f$ with a mean function $m(x)$ and a covariance function $k(x, x')$:
- Mean: $$m(x) = \mathbb{E}[f(x)]$$
- Covariance: $$k(x, x') = \mathbb{E}[(f(x) - m(x))(f(x') - m(x'))]$$

#### Common Covariance Functions
- Squared Exponential
- Matern
- Rational Quadratic

#### Prediction
With observations $$ f = [f(x_1), f(x_2), \ldots, f(x_t)] $$, the prediction at new point is:
$$ \mathbb{P}\left( \begin{bmatrix} f \\ f^* \end{bmatrix} \right) = \mathcal{N} \left( 0, \begin{bmatrix} K[X, X] & K[X, x^*] \\ K[x^*, X] & K[x^*, x^*] \end{bmatrix} \right) $$

### 4. Acquisition Functions
Acquisition functions balance exploration and exploitation to select the next evaluation point.

#### Common Acquisition Functions
- **Upper Confidence Bound (UCB)**
- **Probability of Improvement (PI)**
- **Expected Improvement (EI)**

#### Parallel Acquisition Functions
- **Parallel Expected Improvement (PEI)**
- **Knowledge Gradient (KG)**

### Conclusion
Bayesian Optimization effectively optimizes expensive and noisy functions by leveraging Gaussian Processes and acquisition functions to balance exploration and exploitation. It has broad applications in various fields requiring efficient optimization techniques.

## Material

<embed src="/docs/pdfs/Week1_BayesOPT.pdf" type="application/pdf" width="100%" height="600px" />


## References
1. UDL book further reading about Bayesian Optimization: https://www.borealisai.com/research-blogs/tutorial-8-bayesian-optimization/
2. Prof. Peter Frazier's talk about BO: https://people.orie.cornell.edu/pfrazier/Presentations/2018.11.INFORMS.tutorial.pdf
3. Louis Tiao's introduction to Knowledge Gradient: https://tiao.io/post/an-illustrated-guide-to-the-knowledge-gradient-acquisition-function/
4.  V. Nguyen, "Bayesian Optimization for Accelerating Hyper-Parameter Tuning," 2019 IEEE Second International Conference on Artificial Intelligence and Knowledge Engineering (AIKE), Sardinia, Italy, 2019, pp. 302-305, doi: 10.1109/AIKE.2019.00060.
5. Frazier, P. I. (2018). A Tutorial on Bayesian Optimization. arXiv preprint arXiv:1807.02811
6. Wang, J., Clark, S. C., Liu, E., & Frazier, P. I. (2016). Parallel Bayesian global optimization of expensive functions. arXiv preprint arXiv:1602.05149.
