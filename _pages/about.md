---
permalink: /
title: ""
author_profile: true
redirect_from: 
  - /about/
  - /about.html
header:
  overlay_image: langevin-banner.png
  overlay_filter: 0.2
---
<style>
  /* 1. Make the banner taller */
  .page__hero--overlay {
    padding-top: 150px !important;
    padding-bottom: 150px !important;
  }

  /* 2. Hide the fallback title text so the banner is pure art
  .page__hero--overlay .page__title {
    display: none !important;
  }
  */
  
  /* 3. Push the sidebar down below the banner */
  .sidebar {
    margin-top: 2em !important; 
  }
  
  /* 4. Force the sidebar down on desktop screens (Overriding the theme's negative margin) */
  @media (min-width: 64em) {
    .sidebar {
      margin-top: 2em !important;
    }
  }
</style>

<div style="display: none;">
$$
\newcommand{\wick}[1]{\mathopen{:} #1 \mathclose{:}}
$$
</div>

In April I completed my Master’s Degree in Mathematics at the **University of Bonn** (I am just waiting for my final grade), where my work focused on the intersection of stochastic analysis and constructive quantum field theory. 

My recent research investigates the stochastic quantization of the $$\Phi^4_2$$-model. Specifically, I proved that the non-interacting scalar Euclidean Quantum Field Theory (EQFT) measure is the unique equilibrium state of the underdamped Langevin quantization of the mean-field limit of the $$\Phi^4_2$$-model. 

Currently, I am working along two parallel tracks: compiling this recent uniqueness result into a solo preprint, and shifting my focus from the abstract mathematical foundations toward **computational quantum field theory**—exploring how the mathematical frameworks can be implemented numerically to make physical predictions.

---

## Recent Results

### Background: The Stochastic Quantization Paradigm 

The primary goal of this research area is to sample configuration fields from a target Euclidean Quantum Field Theory (EQFT) described by a probability measure on a distribution space:

$$d\mu[\phi] = \frac{1}{Z} e^{-S_E[\phi]} \, d\mathcal{D}\phi$$

* **The Challenge:** Direct sampling from the infinite-dimensional measure $$\mu$$ is highly intractable due to many reason, however most notably due to the size of the configuration space (which is infinite-dimensional...) and ultraviolet divergences of interacting fields.
* **The Strategy (Stochastic Quantization):** We construct a continuous-time stochastic process $$\{\phi_\tau\}_{\tau \geq 0}$$ governed by a Langevin-type dynamic that satisfies:
  1. **Invariance:** The target EQFT measure $$\mu$$ is the unique equilibrium (invariant) state of the dynamics.
  2. **Convergence:** For an "easy to sample from" initial distribution $$\phi_0 \sim \rho$$, the law of the process converges to the target measure:
     $$P(\phi_\tau) \xrightarrow{\tau \to \infty} \mu[\phi]$$
     
> **What does this implicate for computing quantum dynamics:** By establishing these properties, we can, at least in theory, numerically sample from the true quantum field theory measure $$\mu$$ by computing ergodic time-averages of the stochastic trajectory $$\phi_\tau$$ after a sufficiently large burn-in time.

### The Hyperbolic Stochastic Quantization of the $$O(N)$$ $$\Phi^4_2$$-Model

Recently, the focus in the field has shifted from stochastic quantization via a parabolic approach (overdamped Langevin dynamics) to a hyperbolic approach (underdamped Langevin dynamics): In this framework, we aim to sample from the target Euclidean QFT on a two-dimensional torus $$\mathbb{T}^2$$ by sampling the first marginal of a joint phase-space distribution:

$$
d\rho_N[\mathbf{\phi}_N, \pi_N] = \frac{1}{Z_N} \exp \left[ -S_E[\phi_N] - \frac{1}{2}\int_{\mathbb{T}^2} \sum_{j=1}^N|\pi_{N,j}|^2 dx \right] \mathcal{D}\phi_N \, \mathcal{D}\pi_N
$$

Here, $$\pi_N = \partial_\tau \phi_N$$ represents an auxiliary fictitious momentum field, and the corresponding Euclidean action is given by:

$$S_{E}[\phi_N] = \int_{\mathbb{T}^2} \left( \frac{1}{2}\sum_{j=1}^N(|\nabla \phi_{N,j}|^2 + |\phi_{N,j}|^2) + \frac{1}{4N} \wick{\Big(\sum_{j = 1}^N \phi_{N,j}^2 \Big)^{2}} \right) dx$$

*(Note: The notation $$\wick{\cdot}$$ denotes the standard normal ordering necessary to prevent ultraviolet divergences in two dimensions).*

Building on foundational frameworks established for the two-dimensional stochastic nonlinear wave equation by [Gubinelli et al. (2022)](#gubinelli2022), the ergodicity of the hyperbolic $$P(\Phi)_2$$-model was demonstrated by [Tolomeo (2023)](#tolomeo2023). Recently, [Liu et al. (2025)](#liu2025) extended these techniques to the multi-component hyperbolic $$O(N)$$ linear sigma model and its mean-field limit. 

Within this setup, the phase-space measure $$\rho_N$$ is realized as the unique equilibrium state of a system of coupled non-linear stochastic wave equations for $$1 \leq j \leq N$$:

$$\partial_\tau^2 \phi_{N,j} +  \partial_\tau \phi_{N,j} + (1 - \Delta) \phi_{N,j}  + \frac{1}{N} \sum^N_{k=1} \wick{ \phi_{N,k}^{2} \phi_{N,j}} = \sqrt{2}\xi_j(\tau, x)$$

where $$\xi_j(\tau, x)$$ is a standard space-(fictitious)-time white noise vector. 

This hyperbolic formulation introduces an "inertia"-term (the $$\partial_\tau^2 \phi$$ term) to the quantization process. 

> **Why underdamped dynamics?** The hyperbolic formulation helps prevent the diffusive random walk behavior that the parabolic algorithm often suffers from, and it reduces the risk of the algorithm becoming trapped in local minima. While it comes at the cost of higher implementation complexity to prevent numerical instability, this makes the hyperbolic formulation a promising alternative — especially in the complex, infinite-dimensional setting of QFT measures.

---

### My Main Contribution: Unique Equilibrium of the SDMFW

[Liu et al. (2025)](#liu2025) showed that as the number of components $$N \to \infty$$, the coupled interactions vanish, and the joint phase-space target measures $$\rho_N$$ converge weakly to the non-interacting Gaussian measure $$\mu_0 \otimes \mu_1$$. They further demonstrated that the corresponding underdamped Langevin dynamics converges to the **Stochastic Damped Mean-Field Wave Equation (SDMFW)**:

$$\partial_\tau^2 \phi + \partial_\tau \phi + (1 - \Delta) \phi + \langle \wick{\phi^{2}} \rangle \phi = \sqrt{2}\xi(\tau, x).$$

Where $$\langle \wick{\phi^{2}} \rangle$$ represents the expected value of the normal-ordered square of the field. 

While this equation describes the limiting behavior, the question of whether the SDMFW admits a unique equilibrium state remained. The second part of my Master's thesis addresses this gap by proving that the Gaussian measure

$$\mu_0 \otimes \mu_1 = \frac{1}{Z} \exp \left[ - \int_{\mathbb{T}^2} \frac{1}{2}|\nabla \phi|^2 + |\phi|^2 + |\pi|^2  dx \right] \mathcal{D}\phi \, \mathcal{D}\pi$$

is the unique equilibrium state of the SDMFW: 

> **Theorem (Contribution: Unique Equilibrium of the SDMFW)**
>
>Let $$\sigma \in (0, \frac{1}{2})$$. The Gaussian measure $$\mu_0 \otimes \mu_1$$ is the **unique equilibrium state** of the SDMFW in the class of probability measures satisfying a bounded normal-ordered second moment condition:
> 
>$$
>\left\langle \int_{\mathbb{T}^2} |\nabla^{-\sigma} \wick{\phi^{2}}|^2 \, dx \right\rangle < \infty
>$$

**Remarks on the Theorem**

Establishing uniqueness for the SDMFW presents the mathematical challenge that standard ergodic theory for Markov processes cannot be applied for two reasons:
1. **Lack of Regularity:** The associated Markov semigroup is not continuous on the space of bounded, measurable functions.
2. **Mean-Field Dependence:** The dynamics of the solution depend non-linearly on its own law through the mean-field expectation $$\langle \wick{\phi^{2}} \rangle$$.

To overcome these obstacles, I developed a novel self-consistency argument to guarantee that $$\mu_0 \otimes \mu_1$$ is the unique equilibrium state of the SDMFW. *(For complete technical details, see my [Master's Thesis](link_to_thesis.pdf) Section 6 — or hopefully soon my solo preprint which is currently in preparation).*

**Physical & Computational Significance:** 
From an applied perspective, this result demonstrates that within the stochastic quantization program, the best approximation of a large $$N$$-component $$\Phi^4_2$$-system is achieved simply by sampling from the non-interacting Gaussian Free Field measure.

---

## Future Directions: Shifting to Computational QFT

While proving the existence of a stochastic flow and the uniqueness of its equilibrium state provides the mathematical foundation for a stochastic EQFT-sampling algorithm, unfortunately, the theory does not directly translate to perfectly working numerical algorithms. Therefore, currently, I am working to bridge the gap between abstract functional analysis and quantum simulations. 

My future research interests focus on:

* **Efficient Stochastic Quantization Algorithms:** Leveraging the additional inertia of the underdamped Langevin dynamics to design faster-converging Markov Chain Monte Carlo (MCMC) algorithms for lattice field theories, explicitly mitigating issues like random-walk behavior. Furthermore, I aim to address challenges like the complex action (sign) problem in more advanced quantum field models.
* **Deterministic Approaches to Quantum Simulation:** Investigating state-of-the-art deterministic frameworks — such as variants of Tensor Networks and Matrix Product States (MPS) — and comparing them against stochastic sampling methods.
* **Beyond Scalar QFT:** Expanding the scope of my research from foundational scalar models (like the $$\Phi^4_2$$ theory) to more physically realistic and complex systems, particularly gauge theories (e.g., pure Yang-Mills and Quantum Chromodynamics) and models involving fermions.

* ---
---

## 📚 References

* <a id="gubinelli2022"></a> **[Gubinelli et al., 2022]** Gubinelli, M., Koch, H., Oh, T., & Tolomeo, L. (2022). *Global dynamics for the two-dimensional stochastic nonlinear wave equations.* International Mathematics Research Notices (IMRN), 2022(21), 16954–16999. [DOI: 10.1093/imrn/rnab084](https://doi.org/10.1093/imrn/rnab084)

* <a id="tolomeo2023"></a> **[Tolomeo, 2023]** Tolomeo, L. (2023). *Ergodicity for the hyperbolic $$P(\Phi)_2$$-model.* [arXiv:2310.02190](https://arxiv.org/abs/2310.02190)

* <a id="liu2025"></a> **[Liu et al., 2025]** Liu, R., Liu, S., & Oh, T. (2025). *Hyperbolic $$O(N)$$ linear sigma model and its mean-field limit.* [arXiv:2511.21950](https://arxiv.org/abs/2511.21950)
