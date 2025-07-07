https://arxiv.org/abs/2503.03965

All-atom Diffusion Transformers: Unified generative modelling of molecules and materials

### 1. Summary and Rating

This paper introduces the All-atom Diffusion Transformer (ADiT), a unified generative framework capable of creating both periodic atomic systems (crystals) and non-periodic systems (molecules) using a single model. The approach avoids the complexity of specialized, equivariant models by employing a two-stage process. First, a Variational Autoencoder (VAE) with a standard Transformer architecture learns to map a unified, all-atom representation of both molecules and crystals into a shared, continuous latent space. Second, a class-conditional Diffusion Transformer (DiT) is trained to generate new samples within this latent space, which are then decoded back into atomic structures.

Experiments demonstrate that a jointly trained ADiT achieves state-of-the-art or competitive performance on standard benchmarks for both crystal (MP20) and molecule (QM9, GEOM-DRUGS) generation. Notably, joint training improves performance over models trained on a single data type, indicating successful transfer learning. By using standard Transformers instead of more computationally intensive equivariant networks, ADiT achieves significant speedups in training and inference and demonstrates predictable performance improvements with increased model scale, positioning it as a promising step towards scalable foundation models for generative chemistry.

**Rating: 9/10**

This is an excellent paper that makes a significant contribution to generative modeling for chemistry and materials science. Its primary strength lies in the elegant unification of molecule and crystal generation into a single, scalable framework. By demonstrating that a non-equivariant Transformer can outperform specialized, equivariant models—and that joint training is beneficial—the work challenges prevailing assumptions about the necessity of strong geometric inductive biases. The thorough experimental validation, including strong baseline comparisons, ablation studies, and scaling law analysis, provides compelling evidence for the method's effectiveness and efficiency. The paper is well-written, the method is clearly articulated, and the results position it as a key advancement towards building a general-purpose foundation model for atomic systems.

### 2. Main Ideas

1.  **Unified Latent Space for Molecules and Materials:** The core idea is to treat periodic (crystals) and non-periodic (molecules) systems within a single representational framework. A Variational Autoencoder (VAE) is used to compress both system types into a single, shared latent space. This unification simplifies the generative task, enabling a single model to learn the underlying principles common to both domains and facilitates transfer learning between them.

2.  **Latent Diffusion with Scalable Transformers:** The generative process is performed via diffusion in the simplified latent space using a Diffusion Transformer (DiT), rather than in the complex, multi-modal space of atomic coordinates and types. This circumvents the need for computationally expensive, SE(3)-equivariant networks typically used as denoisers. Instead, the model leverages the scalability and efficiency of standard Transformers, learning symmetries through data augmentation, which leads to significant speedups and predictable performance scaling with model size.

3.  **Joint Training Improves Performance:** A key finding is that a single ADiT model trained jointly on both molecule and crystal datasets outperforms models trained on either dataset alone. This demonstrates effective knowledge transfer, where the model learns fundamental chemical and physical patterns from one domain that improve its ability to generate valid and stable structures in the other. This empirically validates the hypothesis that a unified model can capture generalizable principles of atomic structures.

### 3. 10 Most Important Citations

1.  **Rombach et al. 2022.** High-resolution image synthesis with latent diffusion models.
    This paper introduced latent diffusion models, the core generative framework that ADiT adapts from the image domain to the domain of atomic systems.

2.  **Peebles et al. 2023.** Scalable diffusion models with transformers.
    This work introduced the Diffusion Transformer (DiT), the specific denoiser architecture used in ADiT's second stage, demonstrating the power of Transformers for high-performance diffusion models.

3.  **Hoogeboom et al. 2022.** Equivariant diffusion for molecule generation in 3d.
    This is a pioneering work and key baseline that established the use of equivariant diffusion models for 3D molecule generation, representing the specialized, domain-specific approach that ADiT seeks to unify and simplify.

4.  **Xie et al. 2022.** Crystal diffusion variational autoencoder for periodic material generation.
    This paper is a primary baseline for crystal generation, using a diffusion model over a product manifold of properties, which highlights the complexity ADiT circumvents with its unified latent space.

5.  **Kingma et al. 2014.** Auto-encoding variational bayes.
    This is the foundational paper on Variational Autoencoders (VAEs), the architecture used in the first stage of ADiT to learn a compressed latent representation of atomic systems.

6.  **Ho et al. 2022.** Classifier-free diffusion guidance.
    This paper introduced the classifier-free guidance technique that ADiT uses during sampling to control generation (i.e., specifying molecule or crystal output) without needing to train a separate classifier.
    *   **Link:** https://arxiv.org/abs/2207.12598

7.  **Vaswani et al. 2017.** Attention is all you need.
    This is the seminal paper that introduced the Transformer architecture, which is the fundamental building block for both the autoencoder and the diffusion denoiser in ADiT.

8.  **Miller et al. 2024.** Flowmm: Generating materials with riemannian flow matching.
    This is a state-of-the-art flow matching model for crystal generation that serves as a key performance baseline, against which ADiT demonstrates significant speed and performance improvements.

9.  **Xu et al. 2023.** Geometric latent diffusion models for 3d molecule generation.
    This work presents an alternative latent diffusion approach (GeoLDM) for molecules that still relies on an equivariant autoencoder, serving as an important point of comparison for ADiT's non-equivariant design choice.

10. **Abramson et al. 2024.** Accurate structure prediction of biomolecular interactions with alphafold 3.
    Cited as concurrent work, this paper demonstrates that standard Transformers with Gaussian diffusion can effectively model complex, all-atom biomolecular systems, reinforcing ADiT's hypothesis that explicit geometric equivariance is not strictly necessary for high performance.
