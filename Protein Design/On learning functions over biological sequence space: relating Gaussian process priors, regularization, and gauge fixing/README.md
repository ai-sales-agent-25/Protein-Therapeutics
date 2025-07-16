https://arxiv.org/abs/2504.19034

On learning functions over biological sequence space: relating Gaussian process priors, regularization, and gauge fixing
### 1. Summary and Rating

This paper presents a rigorous and comprehensive theoretical framework that unifies two key approaches for modeling biological sequence-to-function landscapes: L2-regularized regression in an overparameterized "weight space" and Gaussian Process (GP) regression in "function space". The central challenge addressed is the non-identifiability of model parameters (weights of subsequence contributions), which necessitates "gauge fixing" for meaningful interpretation.

The authors formally establish that the choice of an L2 regularizer in weight space simultaneously performs two distinct roles: it fixes the gauge for the optimal weight vector, and it implicitly imposes a Gaussian process prior on the learned function. The paper's main theorem provides a constructive recipe for creating a weight-space regularizer that corresponds to *any* chosen GP prior and *any* linear gauge. This is achieved by showing the regularizer can be additively decomposed into a term for the prior and a term for the gauge.

Furthermore, the paper introduces a powerful kernel trick that enables the efficient computation of the posterior distribution for various interpretable representations of the function, including gauge-fixed weights. This method bypasses the need to work with the intractably large, full-dimensional function or weight vectors, making the framework computationally practical even for long sequences. Finally, the authors analyze common weight-space regularizers (e.g., diagonal matrices) and explicitly derive the function-space priors they induce, clarifying the assumptions embedded in these widely-used models.

**Rating: 9/10**

This paper is a significant theoretical contribution that provides a deep and elegant unification of previously disparate modeling concepts. For a sophisticated audience, its strength lies in its mathematical rigor, generality, and the clarity it brings to the subtle relationship between regularization, priors, and parameter interpretability in a high-dimensional, overparameterized setting. The constructive nature of the main theorems and the development of a computationally efficient kernel trick for posterior inference are major advances that are both theoretically insightful and practically empowering for researchers in the field. The work provides a principled foundation for choosing, understanding, and interpreting models of sequence-function landscapes.

### 2. Main Ideas

1.  **Unification of Regularization and Priors:** The core idea is that L2-regularized regression in weight space and Bayesian regression with a Gaussian Process prior in function space are two sides of the same coin. The paper demonstrates that any positive-definite weight-space regularizer not only enforces a "gauge" (a unique representation for the weights) but also implicitly defines a GP prior on the functions being learned. It formalizes this by showing a regularizer Λ can be constructed as the sum of two matrices: one (ΦᵀK⁻¹Φ) that sets the function-space prior K, and another (BᵀB) that determines the gauge.

2.  **A Constructive Framework for Custom Models:** The paper provides a clear recipe for building a regularizer that precisely matches a researcher's desired assumptions. One can select any valid GP prior (via a kernel K) to specify beliefs about the function's smoothness and structure, and separately choose any linear gauge (e.g., hierarchical, wild-type) to ensure the model's parameters are interpretable in a specific way. Theorem 1 shows how to combine these choices into a single weight-space regularizer, offering explicit control over the model's inductive biases.

3.  **Efficient and Tractable Posterior Inference via a Kernel Trick:** A key practical challenge in this domain is the immense size of the full sequence space, which makes direct computation of the function or its full weight vector intractable. The paper overcomes this with a general kernel trick (Theorem 5) that allows for the efficient computation of the posterior distribution of any linear transformation of the function (such as gauge-fixed weights or Fourier coefficients). This allows for rigorous uncertainty quantification of interpretable parameters without ever instantiating the high-dimensional vectors, making the framework applicable to real-world problems.

### 3. 10 Most Important Citations

1.  **Posfai et al. 2025.** Gauge fixing for sequence-function relationships. This paper is the direct predecessor that established the connection between L2 regularization and gauge fixing, providing the foundational problem that the current work extends and generalizes.

2.  **Rasmussen et al. 2006.** Gaussian Processes for Machine Learning. This is the canonical textbook on Gaussian processes and is cited for the fundamental definitions and formulas of GP regression that are central to the paper's function-space perspective.

3.  **Posfai et al. 2025.** Symmetry, gauge freedoms, and the interpretability of sequence-function relationships. This citation provides the underlying theoretical motivation, explaining how symmetries in sequence space lead to gauge freedoms and the need for gauge fixing to obtain interpretable parameters.

4.  **Zhou et al. 2022.** Higher-order epistasis and phenotypic prediction. This work is cited as an example of a state-of-the-art model using variance component (VC) kernels, a major class of function-space priors that the paper's framework is shown to be able to induce.

5.  **Brookes et al. 2022.** On the sparsity of fitness functions and implications for learning. This paper is cited for its work on Fourier representations of fitness functions, which is one of the key interpretable transformations that the paper's kernel trick can be efficiently applied to.

6.  **Faure et al. 2024.** An extension of the walsh-hadamard transform to calculate and model epistasis in genetic landscapes of arbitrary shape and complexity. This is cited for defining background-averaged epistatic coefficients, another important interpretive framework that the paper's general kernel trick is shown to handle.

7.  **Kauffman et al. 1989.** The NK model of rugged fitness landscapes and its application to maturation of the immune response. This is a classic citation that introduced the NK model, a foundational concept in the literature on fitness landscapes that is related to the paper's analysis of priors induced by independent weights.

8.  **Weinberger. 1991.** Fourier and Taylor series on fitness landscapes. This is a foundational paper on using mathematical bases like Fourier/Walsh-Hadamard to represent fitness landscapes, providing context for the analysis of different model representations.

9.  **Poelwijk et al. 2016.** The context-dependence of mutations: a linkage of formalisms. This work is cited for its formalisms of epistasis and is an example of the type of interpretive model whose coefficients can be estimated within the paper's new framework.

10. **Zhou et al. 2025.** Manuscript in preparation. This manuscript is cited for introducing product kernels, the second major class of function-space priors (along with VC kernels) for which the paper develops specific, computationally efficient formulas.
