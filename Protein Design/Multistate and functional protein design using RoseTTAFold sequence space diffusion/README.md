https://www.nature.com/articles/s41587-024-02395-w

Multistate and functional protein design using RoseTTAFold sequence space diffusion

### 1. Summary and Rating

This paper introduces ProteinGenerator (PG), a novel denoising diffusion model for *de novo* protein design that operates in **sequence space** rather than the more common structure space. Built upon the RoseTTAFold architecture, PG iteratively denoises a random sequence representation to simultaneously generate a protein's sequence and structure. The key advantage of this approach is the ability to directly guide the generation process using sequence-specific constraints and properties. The authors demonstrate the power and versatility of PG through a series of impressive design challenges that are difficult for structure-first methods. They successfully generate thermostable proteins with highly unusual amino acid compositions, design complex repeat proteins with specified symmetries, and create "caged" bioactive peptides (e.g., melittin) that are inert until activated by proteolytic cleavage. Most notably, the paper presents a method for explicit **multistate design**, generating single sequences that are experimentally shown (via CD and NMR) to adopt different, well-defined folds depending on whether the protein is in its full-length parent state or cleaved into child domains. Finally, the authors show that PG can be guided by gradients from a surrogate model trained on experimental data, providing a powerful framework for integrating computational design with experimental feedback for function optimization.

**Rating: 9.5/10**

This is an exceptional paper representing a significant conceptual and practical advance in generative protein design. The core innovation of performing diffusion in sequence space elegantly solves the major limitation of structure-first models—the difficulty of imposing "soft" sequence-based constraints. The experimental validation is extensive and rigorous, spanning SEC, CD, mass spectrometry, and, crucially, high-resolution NMR and X-ray crystallography to confirm the most complex designs. The demonstration of true multistate design is a landmark achievement and a highlight of the work. The paper is dense but clearly written, and its contributions open up new frontiers for designing proteins with switchable functions, improved biophysical properties, and integrated experimental optimization loops.

### 2. Main Ideas

1.  **Sequence-Space Diffusion for Guided Protein Design:** The central idea is to adapt the diffusion framework to operate on protein sequences (represented as one-hot encodings) instead of 3D coordinates. By fine-tuning the RoseTTAFold network to denoise sequence representations, the model (ProteinGenerator) can be directly guided by sequence-level properties. This enables the design of proteins with specific amino acid compositions, charge, hydrophobicity, or internal repeats, capabilities that are cumbersome or impossible with models that diffuse in structure space.

2.  **Explicit Multistate Protein Design via Logit Averaging:** A powerful application of this sequence-first approach is the design of proteins that can adopt multiple, distinct conformations. The authors achieve this by running parallel diffusion trajectories for a single sequence under different structural constraints (e.g., a parent protein with an alpha/beta fold and its two child domains with all-alpha folds). By averaging the predicted sequence logits from these parallel runs at each step, they guide the model to find a single sequence that satisfies all structural states. This novel strategy was experimentally validated by NMR, confirming that the designed proteins undergo large-scale structural rearrangement upon cleavage.

3.  **Scaffolding of Functional Motifs and Integration with Experimental Data:** The paper demonstrates that PG can scaffold pre-defined functional sequences, such as bioactive peptides or barcodes, into stable, folded protein structures. By fixing the sequence of the motif and allowing the rest of the protein to diffuse freely, PG generates novel cages. This was used to create a conditionally active version of the lytic peptide melittin. Furthermore, the authors show that the diffusion process can be guided by gradients from a classifier trained on experimental activity data (demonstrated *in silico* on the GB1 fitness landscape), creating a direct bridge between computational generation and experimental optimization.

### 3. Top 10 Most Important Citations

1.  Watson et al. 2023. De novo design of protein structure and function with RFdiffusion.
    This paper introduces RFdiffusion, the state-of-the-art structure-space diffusion model, which serves as the primary conceptual counterpoint and performance benchmark for the sequence-space diffusion approach developed in this work.
    [https://doi.org/10.1038/s41586-023-06415-8](https://doi.org/10.1038/s41586-023-06415-8)

2.  Ho et al. 2020. Denoising diffusion probabilistic models.
    This is the foundational paper that introduced Denoising Diffusion Probabilistic Models (DDPMs), the core machine learning methodology that ProteinGenerator is based on.
    [https://doi.org/10.48550/arXiv.2006.11239](https://doi.org/10.48550/arXiv.2006.11239)

3.  Jumper et al. 2021. Highly accurate protein structure prediction with AlphaFold.
    AlphaFold is used throughout the paper as the gold standard for *in silico* validation of the designed proteins' structures, making this a critical citation for benchmarking design success.
    [https://doi.org/10.1038/s41586-021-03819-2](https://doi.org/10.1038/s41586-021-03819-2)

4.  Baek et al. 2023. Efficient and accurate prediction of protein structure using RoseTTAFold2.
    The ProteinGenerator model is a fine-tuned version of the RoseTTAFold architecture, making this citation essential as it describes the underlying network that was adapted for sequence-space diffusion.
    [https://doi.org/10.1101/2023.05.24.542179](https://doi.org/10.1101/2023.05.24.542179)

5.  Li et al. 2022. Diffusion-LM improves controllable text generation.
    This work is highly relevant as it demonstrates the application of diffusion models to categorical data (text), providing a key precedent and technical framework for applying diffusion to protein sequences.
    [https://doi.org/10.48550/arXiv.2205.14217](https://doi.org/10.48550/arXiv.2205.14217)

6.  Dauparas et al. 2022. Robust deep learning-based protein sequence design using ProteinMPNN.
    ProteinMPNN is the leading method for inverse folding (designing a sequence for a given backbone) and is used as a point of comparison, representing the typical second step in a structure-first design pipeline.
    [https://doi.org/10.1126/science.add2187](https://doi.org/10.1126/science.add2187)

7.  Dhariwal, P. & Nichol, A. 2021. Diffusion models beat GANs on image synthesis.
    This paper introduced classifier-guidance for diffusion models, a technique that the authors adapt to guide the generation process using sequence-specific potentials and experimental fitness data.
    [https://doi.org/10.48550/arXiv.2105.05233](https://doi.org/10.48550/arXiv.2105.05233)

8.  Chen, T., Zhang, R. & Hinton, G. 2022. Analog Bits: generating discrete data using diffusion models with self-conditioning.
    This paper is cited for the self-conditioning technique, which the authors explicitly state was implemented to improve their model's training and inference performance.
    [https://doi.org/10.48550/arXiv.2208.04202](https://doi.org/10.48550/arXiv.2208.04202)

9.  Anishchenko, I. et al. 2021. De novo protein design by deep network hallucination.
    This paper represents an alternative, influential deep learning approach for co-designing sequence and structure, providing important context for the state of the field and a method against which PG is benchmarked.
    [https://doi.org/10.1038/s41586-021-04184-w](https://doi.org/10.1038/s41586-021-04184-w)

10. Wei, K. Y. et al. 2020. Computational design of closely related proteins that adopt two well-defined but structurally divergent folds.
    This citation is important as it describes prior work on the challenging problem of computational multistate design, highlighting the novelty and difficulty of the multistate proteins successfully created with ProteinGenerator.
    [https://doi.org/10.1073/pnas.1919833117](https://doi.org/10.1073/pnas.1919833117)
