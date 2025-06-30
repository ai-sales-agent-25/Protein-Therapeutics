https://www.nature.com/articles/s41586-023-06415-8

De novo design of protein structure and function with RFdiffusion

### 1. Summary and Rating

This paper introduces RFdiffusion, a generative diffusion model for de novo protein design, created by fine-tuning the RoseTTAFold (RF) structure prediction network. The model is trained to reverse a noising process, progressively transforming random coordinates into coherent, designable protein backbones. The authors demonstrate that this single, unified framework can successfully address a wide range of previously difficult protein design challenges. These include unconditional generation of novel monomeric proteins, design of complex higher-order symmetric oligomers (including dihedral and icosahedral symmetries), scaffolding of functional motifs for catalysis and metal binding, and the design of high-affinity protein binders to specified targets. A key strength of the work is the extensive and successful experimental validation of hundreds of computationally generated designs. Biophysical characterization confirmed the stability and folding of designed monomers and oligomers, while a high-resolution cryo-EM structure of a designed binder in complex with influenza hemagglutinin confirmed the atomic accuracy of the method, showing an almost perfect match to the computational model. RFdiffusion represents a substantial leap in the power, generality, and reliability of computational protein design.

**Rating: 10/10**

For a specialized audience, this paper is a landmark achievement. It presents a novel and exceptionally powerful deep-learning architecture that provides a general solution to a multitude of grand challenges in protein design. The methodological innovation of adapting a state-of-the-art structure predictor into a generative diffusion model is elegant and highly effective. The claims of the paper are substantiated by rigorous computational benchmarks and an impressive scale of experimental validation, including multiple high-resolution structures, which bridges the gap between *in silico* modeling and real-world application. The reported two-orders-of-magnitude improvement in experimental success rates for *de novo* binder design is transformative for the fields of protein engineering and therapeutic development.

### 2. Main Ideas

1.  **Fine-tuning a Structure Prediction Network for Generative Diffusion:** The core methodological breakthrough is the adaptation of a powerful, pre-trained protein structure prediction network (RoseTTAFold) to serve as the denoising model within a diffusion probabilistic model (DDPM) framework. Instead of learning protein geometry from scratch, RFdiffusion leverages the rich, nuanced understanding of protein structure already encoded in RoseTTAFold. This allows the model to generate highly realistic and designable protein backbones by iteratively reversing a noising process applied to both residue positions and orientations.

2.  **A General and Versatile Framework for Diverse Design Tasks:** RFdiffusion is presented not as a tool for a single problem, but as a comprehensive platform for protein design. By providing different types of conditioning information during the generative process, the same model can be used for a wide array of tasks. The paper demonstrates outstanding performance in unconditional monomer generation, the design of complex symmetric assemblies (by enforcing symmetry at each denoising step), scaffolding functional motifs (by fixing the geometry of key residues), and generating *de novo* binders to specific protein targets (by specifying a target interface). This generality marks a significant advance over previous, more specialized methods.

3.  **Achieving High Experimental Success Rates with Atomic Accuracy:** A defining feature of this work is the large-scale experimental validation that proves the real-world utility of RFdiffusion. The authors show that designed proteins are not just computationally plausible but are experimentally well-behaved—they express solubly, fold into their intended structures, and exhibit high thermal stability. Crucially, the paper demonstrates that RFdiffusion can design functional proteins, such as high-affinity binders, with success rates far exceeding prior methods, and that the resulting structures match the computational design with atomic-level precision, as confirmed by cryo-EM.

### 3. 10 Most Important Citations

1.  **Jumper et al. 2021. Highly accurate protein structure prediction with AlphaFold. Nature 596, 583–589 (2021).**
    This paper introduced AlphaFold2, which revolutionized protein structure prediction and is used throughout the RFdiffusion paper as the gold-standard computational tool for validating the accuracy of the generated designs.
    [https://doi.org/10.1038/s41586-021-03819-2](https://doi.org/10.1038/s41586-021-03819-2)

2.  **Baek et al. 2021. Accurate prediction of protein structures and interactions using a three-track neural network. Science 373, 871–876 (2021).**
    This paper details the RoseTTAFold (RF) architecture, the structure prediction network that was directly fine-tuned to create the RFdiffusion model, making it the foundational technology upon which this work is built.
    [https://doi.org/10.1126/science.abj8754](https://doi.org/10.1126/science.abj8754)

3.  **Ho et al. 2020. Denoising diffusion probabilistic models. in Adv. Neural Information Processing Systems Vol. 33 (eds Larochelle, H. et al.) 6840–6851 (Curran Associates, 2020).**
    This is the key machine learning paper that introduced the high-performing DDPM framework which RFdiffusion adapts for the task of protein structure generation.

4.  **Dauparas et al. 2022. Robust deep learning-based protein sequence design using ProteinMPNN. Science 378, 49–56 (2022).**
    This paper describes ProteinMPNN, the deep learning method used in the RFdiffusion pipeline to design amino acid sequences that will fold into the generated backbones, making it a critical complementary tool for the overall design process.
    [https://doi.org/10.1126/science.add2187](https://doi.org/10.1126/science.add2187)

5.  **Anishchenko et al. 2021. De novo protein design by deep network hallucination. Nature 600, 547–552 (2021).**
    This is a key prior deep learning method for *de novo* protein design from the same lab, which RFdiffusion is frequently compared against and shown to be a more general and powerful approach.
    [https://doi.org/10.1038/s41586-021-04184-w](https://doi.org/10.1038/s41586-021-04184-w)

6.  **Cao et al. 2022. Design of protein-binding proteins from the target structure alone. Nature 605, 551–560 (2022).**
    This paper represents the previous state-of-the-art for *de novo* binder design using the Rosetta framework, and RFdiffusion's two-orders-of-magnitude improvement in experimental success rate over this method highlights its transformative impact.
    [https://doi.org/10.1038/s41586-022-04654-9](https://doi.org/10.1038/s41586-022-04654-9)

7.  **Sohl-Dickstein et al. 2015. Deep unsupervised learning using nonequilibrium thermodynamics. in Proc. 32nd International Conference on Machine Learning Vol. 37 (eds Bach, Francis and Blei, David) 2256–2265 (PMLR, 2015).**
    This is the foundational theoretical paper that first proposed the diffusion model framework based on non-equilibrium thermodynamics, providing the original concept for this class of generative models.

8.  **Wang et al. 2022. Scaffolding protein functional sites using deep learning. Science 377, 387–394 (2022).**
    This describes the "RFjoint Inpainting" method, a direct predecessor to RFdiffusion from the same lab for motif scaffolding, which RFdiffusion is shown to outperform in robustness and accuracy.
    [https://doi.org/10.1126/science.add1933](https://doi.org/10.1126/science.add1933)

9.  **Trippe et al. 2023. Diffusion probabilistic modeling of protein backbones in 3D for the motif-scaffolding problem. in The Eleventh International Conference on Learning Representations (2023).**
    This conference paper from many of the same authors represents an earlier, more focused application of diffusion models to protein design, providing important context for the development of the more general RFdiffusion model.

10. **Kuhlman et al. 2003. Design of a novel globular protein fold with atomic-level accuracy. Science 302, 1364–1368 (2003).**
    This is a classic paper from the early days of computational protein design that demonstrated the first successful *de novo* design of a novel protein fold using the physics-based Rosetta software, providing historical context for the long-standing goals of the field that RFdiffusion now addresses.
    [https://doi.org/10.1126/science.1089427](https://doi.org/10.1126/science.1089427)
