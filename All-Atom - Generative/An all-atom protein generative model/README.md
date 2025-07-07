https://www.pnas.org/doi/10.1073/pnas.2311500121

**An all-atom protein generative model**

### 1. Brief Summary and Rating

This paper introduces Protpardelle, a novel all-atom diffusion model for de novo protein design that simultaneously codesigns the protein backbone, sequence, and sidechains. Current generative models for protein design often focus solely on the backbone or handle sidechains as a post-hoc step, leading to a "chicken-and-egg" problem where sequence defines atoms, but structural context influences sequence. Protpardelle addresses this by representing all possible sidechain states at each residue position as a "superposition" that is "collapsed" to a specific amino acid type during the iterative denoising (sampling) process, guided by a mini-MPNN-based sequence predictor. This allows the model to manage the jointly continuous (coordinates) and discrete (atom identity/sequence) nature of proteins. The authors demonstrate that Protpardelle generates high-quality protein structures, with sidechains exhibiting chemical fidelity comparable to natural proteins. It shows competitive performance in unconditional generation relative to state-of-the-art backbone-only models, particularly in terms of speed, and explores its potential for all-atom functional motif scaffolding, even conditioning on specific chemical groups rather than entire residues or backbone segments.

**Rating: 9/10**

For a PhD-level audience, this paper represents a significant advancement. The "superposition" concept is a particularly elegant and innovative solution to the challenging problem of codesigning discrete sequence and continuous all-atom structure within a diffusion framework. The comprehensive evaluation, including chemical fidelity of sidechains and exploration of functional conditioning, highlights the model's potential and robustness. While the paper acknowledges areas for further improvement (e.g., fidelity for complex motif scaffolding tasks), the core methodology is sound, well-explained, and opens new avenues for precise, function-driven protein design, moving beyond backbone-centric approaches. The computational efficiency achieved is also a practical strength.

### 2. Main Ideas

1.  **All-atom protein generation via "superposition":** The core innovation is the development of a diffusion model that can generate full atomic protein structures (backbone and sidechains) by representing all 20 possible amino acid sidechain states at each residue position simultaneously as a "superposition." During the iterative denoising process, this superposition "collapses" into a single, specific residue type based on an estimated sequence, thereby enabling the management of the coupled continuous (atomic coordinates) and discrete (amino acid identity) nature of proteins.
2.  **Integrated structure and sequence co-design:** Protpardelle directly integrates a sequence design component (a "mini-MPNN") into the diffusion process. This allows the model to predict the amino acid sequence at each step of structure generation, enabling a synergistic co-design where sidechains influence backbone conformation and vice versa, leading to coherent all-atom protein designs.
3.  **Direct functional motif scaffolding:** The model demonstrates the capability to perform all-atom protein design conditioned directly on specific functional elements or chemical groups, rather than just backbone coordinates. This opens up new possibilities for designing proteins with predefined functional sites, such as scaffolding an iron-binding site by conditioning only on the carboxylate groups of glutamate and the imidazole ring of histidine, paving the way for more precise and function-driven protein engineering.

### 3. List of 10 Most Important Citations

1.  **Song et al. 2021. *Score-based generative modeling through stochastic differential equations*.**
    This paper provides the foundational theoretical framework for score-based generative models via stochastic differential equations, which Protpardelle leverages as its underlying diffusion paradigm.
    Link: https://arxiv.org/abs/2011.13456

2.  **Ho et al. 2020. *Denoising diffusion probabilistic models*.**
    This work introduces Denoising Diffusion Probabilistic Models (DDPMs), a key class of generative models that influenced the development of Protpardelle's iterative denoising mechanism.
    Link: https://arxiv.org/abs/2006.11239

3.  **Karras et al. 2022. *Elucidating the design space of diffusion-based generative models*.**
    This paper's insights into the design space of diffusion models, particularly regarding sampling routines and hyperparameter tuning (like `s_churn` and `step_scale`), were adapted and found crucial for optimizing Protpardelle's sample quality.
    Link: https://arxiv.org/abs/2206.00364

4.  **Ingraham et al. 2023. *Illuminating protein space with a programmable generative model*.**
    This citation refers to RFdiffusion, a prominent backbone-only diffusion model for protein generation, against which Protpardelle's performance (especially for backbone-only generation) is compared in terms of designability, diversity, novelty, and computational speed.

5.  **Watson et al. 2022. *Broadly applicable and accurate protein design by integrating structure prediction networks and diffusion generative models*.**
    This work presents another significant diffusion-based protein generative model (a variant of RFdiffusion) used for comparison with Protpardelle, particularly regarding its broad applicability and accuracy in protein design.
    Link: https://doi.org/10.1101/2022.12.09.519842

6.  **Lin et al. 2023. *Generating novel, designable, and diverse protein structures by equivariantly diffusing oriented residue clouds*.**
    This paper introduces Chroma, another state-of-the-art equivariant diffusion model for protein generation, serving as a key comparative benchmark for Protpardelle's performance and architectural design choices.
    Link: https://doi.org/10.48550/arXiv.2301.12485

7.  **Dauparas et al. 2022. *Robust deep learning-based protein sequence design using proteinMPNN*.**
    This paper introduces ProteinMPNN, the highly effective graph neural network architecture that Protpardelle adapts into a "mini-MPNN" for its sequence codesign component, allowing it to predict sequences based on structural information.

8.  **Alford et al. 2017. *The rosetta all-atom energy function for macromolecular modeling and design*.**
    This citation describes the Rosetta all-atom energy function, which is utilized by Protpardelle for evaluating the chemical quality and energy landscape of its generated structures, specifically through metrics like fa_dun energies.

9.  **Varadi et al. 2021. *AlphaFold Protein Structure Database: Massively expanding the structural coverage of protein-sequence space with high-accuracy models*.**
    This paper describes the AlphaFold Protein Structure Database (AFDB), which, along with CATH, was used as a significant source of training data for Protpardelle's all-atom model, contributing to its diversity and generalization capacity.

10. **Lin et al. 2023. *Evolutionary-scale prediction of atomic-level protein structure with a language model*.**
    This paper details ESMFold, which Protpardelle employs as an "oracle" for structure prediction to assess the self-consistency of its generated designs and their corresponding sequences, using metrics like scRMSD and scTM.
