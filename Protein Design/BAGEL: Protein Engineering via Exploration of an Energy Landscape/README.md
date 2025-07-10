https://www.biorxiv.org/content/10.1101/2025.07.05.663138v1

BAGEL: PROTEIN ENGINEERING VIA EXPLORATION OF AN ENERGY LANDSCAPE

### 1. Summary and Rating

This paper introduces BAGEL (Biomolecular Algorithm for Guidance in Energy Landscapes), a modular, open-source Python framework for programmable protein engineering. The authors address the rigidity and specificity of existing deep learning-based design pipelines, which are often ill-suited for custom, multi-objective, or non-differentiable design goals. BAGEL reframes protein design as an energy landscape exploration problem, where a user defines a custom energy function composed of various weighted terms (e.g., geometric constraints, structural confidence metrics, embedding similarities). The framework then employs gradient-free sampling methods, primarily Markov Chain Monte Carlo (MCMC), to explore the sequence space and identify candidate proteins that minimize this energy function. Key features of BAGEL include its model-agnostic architecture (allowing seamless integration of different deep learning "oracles" like ESMFold), native support for multi-state optimization (e.g., designing a binder to be selective for one target over another), and a flexible, user-friendly interface. The paper demonstrates the framework's versatility across four applications: de novo peptide binder design, targeting intrinsically disordered regions, multi-state selective binding, and generative sampling of enzyme variants. BAGEL's primary goal is to democratize protein design by abstracting complex implementation details and providing a powerful, adaptable tool for the broader scientific community.

**Rating: 9/10**

For a PhD-level audience, this paper presents a significant contribution to the computational protein design toolkit. Its strength lies not in developing a new predictive model, but in creating a robust, highly flexible, and conceptually elegant framework that synthesizes the power of existing state-of-the-art models. The formalization of protein design as the minimization of a user-defined, modular energy function via gradient-free methods is powerful, as it circumvents the limitations of differentiability required by methods like hallucination and offers greater customizability than fixed generative pipelines. The engineering choice to make the framework model-agnostic via the `boileroom` backend is particularly insightful, ensuring BAGEL can adapt and "withstand the test of time" by easily incorporating future, more powerful oracles. The inclusion of multi-state optimization is a critical feature for tackling real-world biological problems like specificity. The paper is exceptionally well-written and clear, and the provided examples effectively showcase the framework's breadth. The only reason for not awarding a perfect score is the inherent limitation, which the authors acknowledge, that the designs are presented without experimental validation. However, as a methods paper introducing a powerful new research tool, the work is outstanding.

### 2. Main Ideas

1.  **Protein Design as Programmable Energy Landscape Exploration:** The central idea of BAGEL is to abstract protein design into a search problem on a custom energy landscape. Instead of relying on rigid, pre-defined pipelines (e.g., backbone generation -> inverse folding), users can program their design objectives by combining various "Energy Terms" into a single loss function. The system then uses MCMC sampling to find sequences that occupy low-energy regions of this landscape. This makes the design process transparent, highly customizable, and applicable to goals that are non-differentiable or difficult to express in other frameworks.

2.  **A Modular and Model-Agnostic Architecture:** BAGEL is built from the ground up with modularity in mind. It separates the core components of a design problem: the `System` (the overall goal), `States` (specific functional contexts), `Chains` (the proteins), `EnergyTerms` (the objectives), `Oracles` (external prediction models like ESMFold), and `Minimizers` (the optimization algorithms). This architecture not only makes it easy for users to define complex problems but, crucially, makes the framework "model-agnostic." It can readily integrate new and improved folding or language models as they become available, preventing obsolescence and allowing for direct benchmarking.

3.  **Native Support for Multi-State and Generative Design Tasks:** The framework's structure inherently supports complex design challenges beyond simple optimization. By defining a `System` with multiple `States` (e.g., a "binding" state with a target and an "avoiding" state with an off-target), BAGEL can perform multi-objective optimization for properties like binding selectivity. Furthermore, by adjusting the sampling temperature in the MCMC algorithm, the framework can be used not just to find a single optimal sequence (optimization) but to generate a diverse ensemble of viable candidates that satisfy the design constraints (generative sampling), as demonstrated in the enzyme variant example.

### 3. 10 Most Important Citations

1.  Jumper et al. 2021. Highly accurate protein structure prediction with alphafold.
    *   This paper introduced AlphaFold2, the landmark model that revolutionized protein structure prediction and underpins the modern era of computational protein design, providing key metrics like pLDDT and PAE that are used as energy terms in BAGEL.
    *   http://dx.doi.org/10.1038/s41586-021-03819-2

2.  Lin et al. 2023. Evolutionary-scale prediction of atomic-level protein structure with a language model.
    *   This paper introduced ESMFold, the fast protein structure prediction model that BAGEL uses as its primary `FoldingOracle` in the examples, demonstrating the framework's ability to leverage state-of-the-art deep learning models.
    *   http://dx.doi.org/10.1126/science.ade2574

3.  Hie et al. 2022. A high-level programming language for generative protein design.
    *   This work is the most direct intellectual predecessor to BAGEL; the authors explicitly state they are inspired by it while aiming to improve upon its representation and flexibility, making it a critical point of reference.
    *   http://dx.doi.org/10.1101/2022.12.21.521526

4.  Watson et al. 2023. De novo design of protein structure and function with rfdiffusion.
    *   This paper details RFDiffusion, a leading deep generative model for protein design, which BAGEL presents as part of an alternative design paradigm that their framework complements.
    *   http://dx.doi.org/10.1038/s41586-023-06415-8

5.  Dauparas et al. 2022. Robust deep learning-based protein sequence design using proteinmpnn.
    *   This paper introduced ProteinMPNN, a premier inverse folding algorithm that is a core component of the "inverse folding paradigm" which BAGEL aims to provide a more flexible alternative to.
    *   http://dx.doi.org/10.1126/science.add2187

6.  Anishchenko et al. 2021. De novo protein design by deep network hallucination.
    *   This work describes a gradient-based optimization approach ("hallucination") for protein design, which BAGEL contrasts with its own gradient-free MCMC method, highlighting the advantage of not requiring differentiable objectives.
    *   http://dx.doi.org/10.1038/s41586-021-04184-w

7.  Bowie et al. 1991. A method to identify protein sequences that fold into a known three-dimensional structure.
    *   This is a classic paper cited by the authors as foundational to the "inverse folding paradigm," providing historical context for the multi-step design workflows that BAGEL seeks to improve upon.
    *   http://dx.doi.org/10.1126/science.1853201

8.  Metropolis et al. 1953. Equation of state calculations by fast computing machines.
    *   This foundational paper introduced the Metropolis-Hastings algorithm, the specific type of Markov Chain Monte Carlo (MCMC) method that is the core optimization and sampling engine within BAGEL.
    *   http://dx.doi.org/10.1063/1.1699114

9.  Lála. 2025. boileroom: serverless protein prediction models.
    *   This is the backend package developed by the authors to manage and run the deep learning "oracles," representing a crucial component of BAGEL's architecture that enables its modularity and accessibility.
    *   https://github.com/jakublala/boileroom

10. Abramson et al. 2024. Accurate structure prediction of biomolecular interactions with alphafold 3.
    *   Cited as AlphaFold2/3 in the "Future Outlook," this paper introduces the next generation of AlphaFold with capabilities for multimers and ligands, representing the type of future "oracle" that BAGEL's modular design is built to readily incorporate.
    *   http://dx.doi.org/10.1038/s41586-024-07487-w
