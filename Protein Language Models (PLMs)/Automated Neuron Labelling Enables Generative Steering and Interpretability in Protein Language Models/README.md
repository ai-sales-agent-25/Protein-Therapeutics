https://arxiv.org/abs/2507.06458

Automated Neuron Labelling Enables Generative Steering and Interpretability in Protein Language Models

### 1. Summary and Rating

This paper introduces a novel, scalable framework for interpreting the internal workings of Protein Language Models (PLMs) like ESM-2. The core idea is to automatically assign a biologically-grounded, natural language label to every individual neuron in the model. This is achieved through a two-stage process: first, an "explainer" LLM generates hypotheses about a neuron's function by analyzing the common features of proteins that maximally activate it; second, a "simulator" model validates these hypotheses by predicting neuron activations, with the best-correlating hypothesis being chosen as the final label.

The authors leverage these neuron labels for two main contributions. First, they perform interpretability analyses, revealing how PLMs of different sizes represent information. They find evidence for a hierarchical organization of features (from simple biochemical properties in early layers to complex functional roles in later layers) and discover scaling laws where larger models distribute feature representations more diffusely and capture more fine-grained concepts. Second, they introduce a "generative steering" method. By identifying neurons whose labels correspond to a desired trait (e.g., "alpha helix" or "high molecular weight") and artificially amplifying their activations during generation, they successfully steer the model to produce proteins with those specific characteristics. While the generated proteins are shown to be structurally unstable (a noted limitation), the work serves as a powerful proof-of-concept for fine-grained, interpretable control over PLM-based protein design.

**Rating: 9/10**

This is an excellent paper presenting a highly novel and impactful methodology. The approach of combining an explainer and a simulator LLM to create a full, validated map of neuron function is a significant step forward for mechanistic interpretability in a complex domain like protein modeling. The subsequent use of these labels for generative steering is a direct and compelling application that moves beyond passive observation to active model control. The analysis of scaling laws and feature locality is thorough and provides valuable insights into how these massive models work. The primary reason it does not receive a perfect score is the current inability of the method to generate structurally viable proteins, which tempers its immediate practical utility for de novo design. However, as a foundational framework and a rigorous exploration of interpretability, the work is of very high quality.

### 2. Main Ideas

1.  **Automated, Scalable Neuron Labeling:** The central contribution is a framework that automates the process of assigning a natural language description to every neuron in a PLM. Unlike prior work relying on manual annotation or training auxiliary models like sparse autoencoders (SAEs), this method uses a two-step LLM-based pipeline (Explain-then-Simulate) that is scalable to hundreds of thousands of neurons and grounded in a rich dataset of biological annotations. This creates a human-readable map of the model's internal feature space.

2.  **Generative Steering via Neuron Activation:** The paper demonstrates that the generated neuron labels can be used as a direct interface for controllable protein generation. By semantically identifying neurons associated with a desired biochemical or structural property and then applying an affine transformation to amplify their activations during the generation process, the model can be effectively "steered" to create sequences that exhibit the target trait. This represents a shift towards concept-level, interpretable control over generative models in biology.

3.  **Investigating PLM Scaling Laws and Feature Hierarchies:** By applying their labeling technique to ESM-2 models of varying sizes (8M, 35M, and 3B parameters), the authors analyze how model scale affects internal representations. They provide evidence that PLMs learn a hierarchy of features, with basic sequence properties encoded in early layers, structural motifs in middle layers, and global functional roles in late layers. Furthermore, they find that larger models can represent more niche features and tend to distribute feature detection more broadly across layers, whereas smaller models exhibit more rigid layer specialization due to information bottlenecks.

### 3. Top 10 Most Important Citations

1.  **Bills et al. (2023).** Language models can explain neurons in language models.
    This paper is foundational to the authors' approach, as it established the viability of using LLMs to generate natural language explanations for neurons in general-purpose language models (GPT-2), which the current work adapts and extends to the domain of PLMs.

2.  **Lin et al. (2022).** Evolutionary-scale prediction of atomic level protein structure with a language model.
    This is the paper introducing ESM-2, the specific family of PLMs that the authors analyze, making it the central subject of their investigation.

3.  **Rao et al. (2021).** Transformer protein language models are unsupervised structure learners.
    This influential work demonstrated that PLMs learn protein structure without explicit supervision, providing the core motivation for this paper's goal of understanding *how* and *where* this information is encoded within the model's neurons.

4.  **Bau et al. (2017).** Network dissection: Quantifying interpretability of deep visual representations.
    This is a seminal paper on neuron-level interpretability, showing that units in vision models correspond to human-understandable concepts, providing the conceptual ancestry for the neuron-labeling approach taken in this work.

5.  **Simon & Zou (2024).** Interplm: Discovering interpretable features in protein language models via sparse autoencoders.
    This paper represents a key alternative approach (using sparse autoencoders) for finding interpretable features in PLMs, which the authors contrast their method against, arguing their framework avoids issues like training instability.

6.  **Beltagy et al. (2020).** Longformer: The long-document transformer.
    The authors explicitly name Longformer as the architecture for their "Simulator Model," chosen for its ability to handle the long protein sequences and associated feature contexts required for validating the neuron labels.

7.  **Consortium, T. U. (2023).** Uniprot: the universal protein knowledgebase in 2023.
    The UniProt database is the primary source for the 500,000 protein sequences and qualitative annotations used to build the dataset for this study, making it fundamental to the entire experimental setup.
    *   Link: `https://academic.oup.com/nar/article/51/D1/D523/6835362`

8.  **Cock et al. (2009).** Biopython: freely available python tools for computational molecular biology and bioinformatics.
    This citation is crucial as the authors used the BioPython library to compute the quantitative biochemical features (like molecular weight and GRAVY score) that enrich their dataset and serve as targets for generative steering.

9.  **McGuffin et al. (2000).** The psipred protein structure prediction server.
    The authors use PsiPred to predict and analyze the secondary structure of their generated proteins, which is essential for validating the success of their secondary structure steering experiments (e.g., generating alpha helices).

10. **Ruffolo & Madani (2024).** Designing proteins with language models.
    This citation helps frame the broader context and importance of the research problem, highlighting that de novo protein design using language models is a major goal in the field, which their work on interpretable control directly addresses.
    *   Link: `https://www.nature.com/articles/s41587-024-02123-4`
