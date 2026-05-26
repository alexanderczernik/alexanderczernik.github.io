---
layout: archive
title: "Publications & Theses"
permalink: /publications/
author_profile: true
---

<div style="display: none;">
$$
\newcommand{\wick}[1]{\mathopen{:} #1 \mathclose{:}}
$$
</div>

## Publications

1. **A Comparative Study on Generative Models for High Resolution Solar Observation Imaging**  
   M. Cherti, **A. Czernik**, S. Kesselheim, F. Effenberger, and J. Jitsev.  
   Presented at the *2nd ICML Workshop on Machine Learning for Astrophysics* (2023).    
   Links: [[ICML Workshop](https://icml.cc/virtual/2023/workshop/21497)] [[arXiv](https://arxiv.org/abs/2304.07169)]

   <details style="margin-top: 0.5em; margin-bottom: 1em; cursor: pointer;">
     <summary style="font-weight: bold; font-size: 0.9em;">See Abstract</summary>
     <p markdown="1" style="margin-top: 0.5em; padding-left: 15px; border-left: 4px solid var(--border-color, #ccc); font-style: italic; opacity: 0.85;">
   Solar activity is one of the main drivers of variability in our solar system and the key source of space weather phenomena that affect Earth and near Earth space. The extensive record of high resolution extreme ultraviolet (EUV) observations from the Solar Dynamics Observatory (SDO) offers an unprecedented, very large dataset of solar images. In this work, we make use of this comprehensive dataset to investigate capabilities of current state-of-the-art generative models to accurately capture the data distribution behind the observed solar activity states. Starting from StyleGAN-based methods, we uncover severe deficits of this model family in handling fine-scale details of solar images when training on high resolution samples, contrary to training on natural face images. When switching to the diffusion based generative model family, we observe strong improvements of fine-scale detail generation. For the GAN family, we are able to achieve similar improvements in fine-scale generation when turning to ProjectedGANs, which uses multi-scale discriminators with a pre-trained frozen feature extractor. We conduct ablation studies to clarify mechanisms responsible for proper fine-scale handling. Using distributed training on supercomputers, we are able to train generative models for up to 1024x1024 resolution that produce high quality samples indistinguishable to human experts, as suggested by the evaluation we conduct. We make all code, models and workflows used in this study publicly available at [[GitHub](https://github.com/SLAMPAI/generative-models-for-highres-solar-images)]. 



## Preprints

1. **On the Smoluchowski-Kramers Approximation for global dynamics of the hyperbolic $O(N)$ linear sigma model**  
   **A. Czernik**, R. Liu, and S. Liu.  
   *In preparation*, 2026.

   <details style="margin-top: 0.5em; margin-bottom: 1em; cursor: pointer;">
     <summary style="font-weight: bold; font-size: 0.9em;">See Abstract</summary>
     <p markdown="1" style="margin-top: 0.5em; padding-left: 15px; border-left: 4px solid var(--border-color, #ccc); font-style: italic; opacity: 0.85;">
       We study the two-dimensional hyperbolic $$O(N)$$ linear sigma model, i.e.~a system of $N$ interacting stochastic damped nonlinear wave equations (SdNLW) with coupled cubic nonlinearities, indexed by a parameter $$\varepsilon > 0$$. We show that as $$\varepsilon$$ goes to zero (Smoluchowski-Kramers approximation) and $$N$$ goes to infinity (mean-field limit), each component of the solution to the SdNLW system converges to the solution to the stochastic nonlinear heat equation (SNLH) with a mean-field nonlinearity. We prove such convergence via two regimes: first with $$\varepsilon$$ going to zero to obtain the parabolic $$O(N)$$ linear sigma model, i.e.~a system of $$N$$ coupled SNLH, and then with $$N$$ going to infinity; or first with $$N$$ going to infinity for each component to obtain the mean-field SdNLW and then with $$\varepsilon$$ going to zero. As a result, we obtain a commuting diagram regarding the convergence from the hyperbolic $$O(N)$$ linear sigma model and the mean-field SNLH.


---

## Theses

### Master's Thesis
**The Stochastic Smoluchowski-Kramers Approximation with a Mean-Field Nonlinearity**  
Rheinische Friedrich-Wilhelms-Universität Bonn, 2026.  
Supervised by [Prof. Herbert Koch](https://www.math.uni-bonn.de/~koch/).  
Links: [[Download PDF](/assets/files/master_thesis_czernik.pdf)] *<!-- Update path when uploaded -->*

<details style="margin-top: 0.5em; margin-bottom: 1em; cursor: pointer;">
     <summary style="font-weight: bold; font-size: 0.9em;">See Abstract</summary>
     <p markdown="1" style="margin-top: 0.5em; padding-left: 15px; border-left: 4px solid var(--border-color, #ccc); font-style: italic; opacity: 0.85;">
    We consider the Smoluchowski Kramers Approximation for the stochastic damped mean field wave equation (SDMFW) $$\varepsilon^2 \partial_t^2 u_\varepsilon +  \partial_t u_\varepsilon + (1 - \Delta) u_\varepsilon  + \mathbb{E}[\wick{u_\varepsilon^2}]u_\varepsilon = \sqrt{2}\xi$$ to the stochastic mean field heat equation (SMFH) $$u_0 + (1 - \Delta) u_0  + \mathbb{E}[\wick{u_0^2}]u_0 = \sqrt{2}\xi$$, with a white-noise forcing term $$\xi$$, posed on the two-dimensional torus $$\mathbb{T}^2$$. The main contributions of this thesis are: (i) We apply the $$I$$-Method to derive a global bound on $$u_\varepsilon$$ that is uniform in $$\varepsilon$$, allowing for the strong global convergence of $$u_\varepsilon$$ to $$u_0$$ as $$\varepsilon \to 0$$. (ii) We establish an argument, utilizing self-adjoint operator theory, to prove that $$\rho_\varepsilon := \mathcal{N}\left(0, \begin{pmatrix} (1-\Delta)^{-1} & 0 \\ 0 & \varepsilon^{-2} \end{pmatrix}\right) \in \mathcal{P}(H^{-\sigma}(\mathbb{T}^2) \times H^{-1-\sigma}(\mathbb{T}^2))$$ is the unique invariant measure of the SDMFW in the class $$\{\mu \in \mathcal{P}(H^{-\sigma}(\mathbb{T}^2) \times H^{-1-\sigma}(\mathbb{T}^2)) : \mathbb{E}_\mu[\wick{u^2}] \in H^{-\sigma}(\mathbb{T}^2) \}$$, where $$\wick{u^2}$$ denotes a Wick renormalization. (iii) We prove the convergence of $$\rho_\varepsilon$$ to $$\rho_0$$ as $$\varepsilon \to 0$$ using continuous bounded test functions that vanish at infinity, where $$\rho_0 := \mathcal{N}(0,(1-\Delta)^{-1}) \in \mathcal{P}(H^{-\sigma}(\mathbb{T}^2))$$ is the invariant measure of the SMFH, and discuss why this convergence fails in a weak sense and is trivial in a vague sense.  
</p>
   </details>

### Bachelor's Thesis
**Impact of Datasets on Generative Models in Imaging**  
Rheinische Friedrich-Wilhelms-Universität Bonn, 2023.  
Co-supervised by [Prof. Alexander Effland](https://www.uni-bonn.de/de/forschung-lehre/forschungprofil/transdisziplinaere-forschungsbereiche/tra-3-life-1/mitgliederverzeichnis/alexander-effland) and [Prof. Stefan Kesselheim](https://www.fz-juelich.de/profile/kesselheim_s).  
Links: [[Download PDF](/assets/files/bachelor_thesis_czernik.pdf)] *<!-- Update path when uploaded -->*

<details style="margin-top: 0.5em; margin-bottom: 1em; cursor: pointer;">
     <summary style="font-weight: bold; font-size: 0.9em;">See Abstract</summary>
     <p markdown="1" style="margin-top: 0.5em; padding-left: 15px; border-left: 4px solid var(--border-color, #ccc); font-style: italic; opacity: 0.85;">
    Quality and diversity assessments of generated image datasets are vital to choose and improve algorithmic generators. Based on summary statistics we present a framework to compute established generative model performance indices like FID, Precision, and Recall on different feature layers of different deep convolutional neural networks. Building on this framework we model neural network activation distributions with Extreme Value Theory (EVT). We observe that looking at layers deeper within neural networks the clustering behavior of maximum values of activation distributions becomes more distinct. Based on EVT we propose the Extreme Value Index to Compare Image Distributions (EVI). The proposed index is supposed to measure mode coverage, generated artifacts and quality of a generated dataset. However, in a series of empirical tests the index fails to definitely distinguish between declines of quality or diversity of generated datasets.
</p>
   </details>

