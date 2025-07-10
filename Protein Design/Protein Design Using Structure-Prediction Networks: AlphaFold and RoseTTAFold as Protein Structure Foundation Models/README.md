https://cshperspectives.cshlp.org/content/16/7/a041472.short

Protein Design Using Structure-Prediction Networks: AlphaFold and RoseTTAFold as Protein Structure Foundation Models
***

### 1. Summary and Rating

**Summary:**
This review paper describes the paradigm shift in *de novo* protein design catalyzed by the advent of highly accurate deep learning-based structure-prediction models, namely AlphaFold (AF) and RoseTTAFold (RF). The authors posit that these models serve as powerful "foundation models" for protein engineering. The paper outlines three major classes of design methodologies that leverage these networks: (1) **Hallucination**, an optimization process analogous to activation maximization, where a random sequence is iteratively modified to minimize a loss function, thereby generating novel protein structures; (2) **Inpainting**, where a fine-tuned RF model (RF_joint_) completes or "inpaints" missing structural or sequence information, proving highly effective for tasks like motif scaffolding; and (3) **Denoising Diffusion**, the current state-of-the-art, where models like RF_diffusion_ are fine-tuned from structure-prediction weights to generate high-quality, diverse, and functional proteins by reversing a noise-corruption process. The paper highlights the dramatic increase in wet-lab success rates achieved by these methods in designing complex monomers, oligomers, binders, and even enzymes, demonstrating their superiority over traditional physics-based approaches. It concludes by discussing remaining challenges and future directions, such as improving accuracy for non-protein molecules and achieving true joint sequence-structure generation.

**Rating: 9/10**
This is an outstanding and timely review for a specialized audience. It provides a clear, well-structured conceptual framework for understanding the rapidly evolving landscape of deep learning in protein design. The paper excels at synthesizing a large volume of very recent and impactful literature into a coherent narrative, effectively explaining how the field moved from using AF/RF as simple validators to repurposing them as generative engines. The distinction between hallucination, inpainting, and diffusion is particularly insightful and provides readers with a valuable mental model. The "foundation model" analogy is apt and forward-looking. The inclusion of numerous experimentally validated examples (Figure 2) grounds the review in real-world success. While it is a review and thus does not present novel primary research, its value as a high-level synthesis and guide to the state-of-the-art is immense for any researcher in computational biology or protein engineering.

### 2. Main Ideas Discussed

1.  **Repurposing Structure Prediction Models for Generative Design:** The central idea is that neural networks developed for protein *structure prediction* (e.g., AlphaFold, RoseTTAFold) can be "inverted" or fine-tuned to solve the inverse problem of protein *design*. Instead of predicting structure from sequence, these models are used to generate sequences and structures that satisfy specific design goals. This represents a fundamental shift away from relying solely on traditional, less accurate physics-based energy functions.

2.  **A Taxonomy of Deep Learning Design Methods:** The paper categorizes the new design methods based on how they leverage structure-prediction networks. This includes:
    *   **Hallucination:** Using the network as a "scorer" in an optimization loop to invent novel proteins by maximizing prediction confidence or other objectives.
    *   **Inpainting:** Fine-tuning a model to "fill-in-the-blanks," allowing for precise scaffolding of functional motifs within a larger, newly generated protein structure.
    *   **Denoising Diffusion (e.g., RF_diffusion_):** Fine-tuning a pretrained structure-prediction network to learn the data distribution of proteins. This method generates novel, high-quality proteins by starting with random noise and iteratively denoising it into a valid structure, achieving state-of-the-art results.

3.  **The "Foundation Model" Concept in Protein Science:** The paper argues that AF and RF act as "foundation models" for protein structure. Their weights, pretrained on vast amounts of structural data, encode a rich, implicit understanding of protein biophysics. This allows them to serve as a powerful starting point for fine-tuning on a wide array of downstream generative tasks (like diffusion), which dramatically accelerates progress and improves performance compared to training models from scratch.

### 3. 10 Most Important Citations

1.  **Jumper et al. 2021.** Highly accurate protein structure prediction with AlphaFold.
    *   This paper introduced AlphaFold2, the breakthrough model whose near-experimental accuracy in structure prediction catalyzed the new wave of design methods discussed in the review.
    *   Link: `https://doi.org/10.1038/s41586-021-03819-2`

2.  **Baek et al. 2021.** Accurate prediction of protein structures and interactions using a three-track neural network.
    *   This paper introduced RoseTTAFold, the other foundational structure-prediction model which, due to its architecture and accessibility, became the direct basis for many of the design tools described, including RF_joint_ and RF_diffusion_.
    *   Link: `https://doi.org/10.1126/science.abj8754`

3.  **Anishchenko et al. 2021.** De novo protein design by deep network hallucination.
    *   This was a pioneering study that experimentally validated the "hallucination" method, demonstrating that novel, stable proteins with diverse topologies could be designed by optimizing sequences using a structure-prediction network as a guide.
    *   Link: `https://doi.org/10.1038/s41586-021-04184-w`

4.  **Dauparas et al. 2022.** Robust deep learning-based protein sequence design using ProteinMPNN.
    *   This work introduced ProteinMPNN, a highly effective method for fixed-backbone sequence design that has become a standard and critical component in modern design pipelines, used to generate high-quality sequences for backbones created by hallucination or diffusion.
    *   Link: `https://doi.org/10.1126/science.add2187`

5.  **Watson et al. 2023.** De novo design of protein structure and function with RFdiffusion.
    *   This paper details the state-of-the-art RF_diffusion_ model, which is fine-tuned from RoseTTAFold and has demonstrated unprecedented success rates in designing complex assemblies, symmetric motifs, and high-affinity binders.
    *   Link: `https://doi.org/10.1038/s41586-023-06415-8`

6.  **Wang et al. 2022a.** Scaffolding protein functional sites using deep learning.
    *   This study introduced the "inpainting" approach by fine-tuning RoseTTAFold (creating RF_joint_) to build protein scaffolds around predefined functional motifs, successfully designing experimentally validated metal- and protein-binding proteins.
    *   Link: `https://doi.org/10.1126/science.abn2100`

7.  **Ho et al. 2020.** Denoising diffusion probabilistic models.
    *   This is a foundational machine learning paper that introduced the denoising diffusion probabilistic model (DDPM) framework, which was later adapted from images to proteins and forms the theoretical basis for generative models like RF_diffusion_.
    *   Link: `https://doi.org/10.48550/arXiv.2006.11239`

8.  **Huang et al. 2016.** The coming of age of de novo protein design.
    *   This review provides essential context by summarizing the state of de novo design before the deep learning revolution, highlighting the challenges (like inaccurate energy functions) that the new methods have begun to overcome.
    *   Link: `https://doi.org/10.1038/nature19946`

9.  **Krishna et al. 2023.** Generalized biomolecular modeling and design with RoseTTAFold all-atom.
    *   This paper describes the extension of RoseTTAFold to model non-protein molecules (RFAA), enabling the design of proteins that bind small molecules, a key frontier addressed at the end of the review paper.
    *   Link: `https://doi.org/10.1101/2023.10.09.561603`

10. **Lin et al. 2023.** Evolutionary-scale prediction of atomic-level protein structure with a language model.
    *   This paper introduced ESMFold, representing a parallel and important advancement where protein language models are used for structure prediction from a single sequence, offering an alternative to MSA-based models like AF and RF.
    *   Link: `https://doi.org/10.1126/science.ade2574`
