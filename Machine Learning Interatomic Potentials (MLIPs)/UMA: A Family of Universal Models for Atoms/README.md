https://arxiv.org/abs/2506.23971

https://ai.meta.com/research/publications/uma-a-family-of-universal-models-for-atoms/

**UMA: A Family of Universal Models for Atoms**

### 1. Summary and Rating

**Summary:**
This paper introduces the Universal Models for Atoms (UMA), a family of machine learning interatomic potentials (MLIPs) designed to create a single, general-purpose AI model for chemistry and materials science. The authors compiled an unprecedentedly large and diverse dataset of nearly half a billion atomic structures, spanning domains from molecules and materials to catalysts. A key architectural innovation is the use of a Mixture of Linear Experts (MoLE), which allows the models to have a very high parameter count (up to 1.4 billion) for increased accuracy and generalization, while keeping the number of active parameters low to maintain high inference speeds essential for simulations. The paper systematically develops and analyzes empirical scaling laws, demonstrating a predictable relationship between model size, data volume, and performance, akin to what has been observed in large language models. The resulting UMA models demonstrate remarkable zero-shot performance, matching or surpassing state-of-the-art specialized models across a wide range of benchmarks without any domain-specific fine-tuning.

**Rating: 9.5/10**
This work represents a landmark achievement in the field of computational materials science. The scale of the data aggregation and the successful training of a truly "universal" potential that generalizes across disparate chemical domains is a major breakthrough. The novel application and adaptation of the Mixture of Experts architecture (as MoLE) to equivariant GNNs is a clever and highly effective solution to the critical trade-off between model capacity and inference efficiency. Furthermore, the rigorous scaling law analysis brings a new level of systematic, principled model development to the field. The extensive and challenging evaluation provides compelling evidence for the models' capabilities, and the public release of the models, code, and data will undoubtedly accelerate progress and enable new scientific discoveries. The paper is exceptionally well-executed and poised to have a significant impact on the field.

### 2. Main Ideas

1.  **Unified General-Purpose Potential Through Scaling:** The central thesis is that by massively scaling up a unified training dataset—pooling nearly 500 million structures from diverse domains like materials (OMat24), molecules (OMol25), and catalysis (OC20)—it is possible to train a single MLIP that generalizes across these domains. This "universal" model can perform as well as or better than specialized models in zero-shot settings, removing the need to train bespoke models for each new chemical problem.

2.  **Mixture of Linear Experts (MoLE) for Efficient Performance:** To build a model large enough to learn from such a diverse dataset without becoming too slow for practical simulations, the authors use a MoLE architecture. A router network, conditioned on global system information (like elemental composition), dynamically selects and combines a set of "expert" linear layers. This allows for models with huge total parameter counts (e.g., UMA-M has 1.4B parameters) but a much smaller number of "active" parameters for any given calculation (~50M). Crucially, for a single simulation where the global information is constant, the expert weights can be pre-merged, resulting in no inference overhead compared to a smaller, dense model.

3.  **Empirical Scaling Laws for Principled Model Design:** The paper is the first to conduct a large-scale study of Chinchilla-style scaling laws for MLIPs. By analyzing the relationships between compute budget, model size, dataset size, and validation loss, the authors are able to make principled decisions about model architecture and training regimes. This analysis not only guides the creation of the UMA family but also demonstrates the quantitative advantage of the MoLE architecture over dense models, showing it can achieve a given accuracy with significantly fewer active parameters.

### 3. 10 Most Important Citations

1.  **Fu et al. 2025.** Learning smooth and expressive interatomic potentials for physical property prediction.
    This paper introduces eSEN, the equivariant graph neural network architecture that serves as the fundamental backbone for the UMA models.

2.  **Kaplan et al. 2020.** Scaling laws for neural language models.
    This seminal work on scaling laws for LLMs provides the direct inspiration and methodological framework for the scaling analysis performed for UMA.

3.  **Jacobs et al. 1991.** Adaptive mixtures of local experts.
    This is a foundational paper introducing the Mixture of Experts concept, the core architectural idea adapted into MoLE to allow UMA to scale its parameter count efficiently.

4.  **Chanussot et al. 2021.** Open catalyst 2020 (oc20) dataset and community challenges.
    This paper introduced the OC20 dataset, a massive and challenging dataset for catalysis that forms a major component of UMA's training data and is a key benchmark for evaluation.
    (Link: https://doi.org/10.1021/acscatal.1c00914)

5.  **Barroso-Luque et al. 2024.** Open materials 2024 (omat24) inorganic materials dataset and models.
    This work provides the OMat24 dataset, a large-scale dataset of inorganic materials that is a cornerstone of the diverse training data used to achieve UMA's generalization.

6.  **Levine et al. 2025.** The open molecules 2025 (omol25) dataset, evaluations, and models.
    This paper introduces the OMol25 dataset, which covers a vast range of molecules and constitutes another of the primary data domains used to train the universal UMA models.
    (Link: https://arxiv.org/abs/2505.08762)

7.  **Riebesell et al. 2023.** Matbench discovery-a framework to evaluate machine learning crystal stability predictions.
    This paper established the Matbench Discovery benchmark, a critical test for materials discovery on which the UMA models achieve new state-of-the-art performance.

8.  **Lan et al. 2023.** Adsorbml: a leap in efficiency for adsorption energy calculations using generalizable machine learning potentials.
    This citation presents the AdsorbML benchmark, which evaluates the practical utility of MLIPs for catalysis discovery; UMA's strong performance on this benchmark highlights its real-world applicability.
    (Link: https://doi.org/10.1038/s41524-023-01121-5)

9.  **Deng et al. 2023.** Chgnet as a pretrained universal neural network potential for charge-informed atomistic modelling.
    This paper introduced CHGNet, a prominent prior attempt at a universal potential, serving as an important point of context and comparison for the UMA models.
    (Link: https://doi.org/10.1038/s42256-023-00716-3)

10. **Achiam et al. 2023.** Gpt-4 technical report.
    Cited as a prime example of how scaling model and dataset size leads to powerful, generalist models, providing the high-level motivation from the language modeling domain for the UMA project.
