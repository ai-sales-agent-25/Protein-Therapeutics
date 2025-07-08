https://www.biorxiv.org/content/10.1101/2025.07.03.663105v1

Ambient Proteins: Training Diffusion Models on Low Quality Structures

### 1. Summary and Rating

**Summary:** This paper introduces Ambient Protein Diffusion, a novel framework for training generative diffusion models for *de novo* protein design. The central problem it addresses is the field's reliance on computationally predicted structures from AlphaFold2 (AF2) for training data, which is necessary due to the scarcity of experimentally determined structures. Standard practice is to filter out low-quality AF2 predictions (identified by low pLDDT scores), which introduces a bias towards smaller, simpler proteins and hinders the generation of diverse and complex long-chain proteins. Ambient Protein Diffusion overcomes this by treating low-quality AF2 structures not as data to be discarded, but as "corrupted" versions of true structures. The framework adjusts the diffusion training objective based on the quality (pLDDT score) of each structure, allowing the model to learn from the entire dataset. The core insight is that as noise is added during the diffusion process, the distributions of high-quality and low-quality structures eventually merge, enabling the model to effectively leverage the low-quality data at higher noise levels without distorting the learned distribution. Empirically, the method achieves state-of-the-art results, dramatically improving the diversity and designability of generated long proteins (e.g., 700+ residues) and establishing a new Pareto frontier for the trade-off between diversity and designability in shorter proteins.

**Rating: 9.5/10**

This paper is excellent. It presents an elegant and theoretically grounded solution to a significant and practical bottleneck in generative protein design. The core idea of leveraging, rather than discarding, imperfect training data by treating it as "ambiently" corrupted is both clever and highly effective. The experimental results are impressive and demonstrate substantial gains over the state-of-the-art (Proteína), particularly on the challenging task of long protein generation, using a much smaller model. The authors also show scientific diligence by identifying and correcting an error in a standard evaluation metric (TM-Novelty) and by performing careful ablations to isolate the impact of their proposed method. The work is a strong contribution that is likely to become a foundational technique for training future protein generation models.

### 2. Main Ideas Discussed

1.  **Training on Corrupted Data via Ambient Diffusion:** The primary idea is to reframe the problem of low-quality AlphaFold predictions as a problem of learning from corrupted data. Instead of filtering structures with low pLDDT scores, the method treats them as noisy observations. It defines a "merging time" for each protein based on its pLDDT score, which is the diffusion time (i.e., noise level) at which the distribution of that protein's quality class becomes indistinguishable from the distribution of high-quality proteins. The model is then trained using these low-quality structures only for diffusion timesteps *beyond* their assigned merging time, effectively using them as valid samples from the highly-noised target distribution. This allows the model to learn coarse-grained information and structural diversity from the full dataset without being negatively biased by the initial prediction errors.

2.  **Re-clustering the Training Set for Geometric Diversity:** The authors recognized that the commonly used AlphaFold Database (AFDB) cluster dataset was created to capture evolutionary relationships, resulting in significant structural redundancy and an imbalanced representation of the protein fold space. To create a dataset better suited for generative modeling of backbones, they re-clustered the AFDB representatives using parameters optimized for *geometric similarity* (using TM-Align) rather than homology. This produced a smaller, more structurally diverse, and more uniform dataset that better represents the landscape of possible protein folds, which contributes to the model's ability to generate novel and diverse structures.

### 3. 10 Most Important Citations

1.  **Jumper et al. 2021.** Highly accurate protein structure prediction with alphafold.
    This paper introduces AlphaFold2, the structure prediction tool that provides the large-scale synthetic dataset (and its associated quality issues) which Ambient Protein Diffusion is designed to leverage.

2.  **Geffner et al. 2025.** Proteina: Scaling flow-based protein structure generative models.
    This paper presents Proteína, the state-of-the-art model for long protein generation that Ambient Protein Diffusion is directly compared against and significantly outperforms.
    *Link*: https://arxiv.org/abs/2403.00710 (Note: The preprint version provided has a 2025 date, the arXiv version is 2024.)

3.  **Lin et al. 2024.** Out of many, one: Designing and scaffolding proteins at the scale of the structural universe with genie 2.
    This paper introduces Genie2, the model architecture and codebase upon which Ambient Protein Diffusion is built, serving as a critical baseline for ablation studies.
    *Link*: https://arxiv.org/abs/2405.15489

4.  **Daras et al. 2023.** Ambient diffusion: Learning clean distributions from corrupted data.
    This is the foundational theoretical work that introduced the "ambient diffusion" concept, which this paper adapts and applies to the domain of protein structures.
    *Link*: https://openreview.net/forum?id=wBJBLy9kBY

5.  **Barrio-Hernandez et al. 2023.** Clustering predicted structures at the scale of the known protein universe.
    This paper created the widely used AFDB cluster dataset, which serves as the starting point for this paper's own data curation and re-clustering pipeline.
    *Link*: https://www.nature.com/articles/s41586-023-06510-3

6.  **Watson et al. 2023.** De novo design of protein structure and function with rfdiffusion.
    This paper introduced RFDiffusion, a seminal diffusion-based model for protein design that established a strong baseline and helped popularize the use of diffusion models in this field.
    *Link*: https://www.nature.com/articles/s41586-023-06415-z

7.  **Varadi et al. 2022.** Alphafold protein structure database: massively expanding the structural coverage of protein-sequence space with high-accuracy models.
    This paper describes the AlphaFold Protein Structure Database (AFDB), the ultimate source of the ~214M computationally generated structures used to train the models in this work.
    *Link*: https://doi.org/10.1093/nar/gkab1061

8.  **van Kempen et al. 2022.** Foldseek: fast and accurate protein structure search.
    This paper introduces FoldSeek, the structural alignment tool that is essential to this work for both its re-clustering of the training data and for evaluating the diversity and novelty of generated proteins.
    *Link*: https://www.biorxiv.org/content/10.1101/2022.02.07.479318v1

9.  **Dauparas et al. 2022.** Robust deep learning-based protein sequence design using proteinmpnn.
    This paper introduces ProteinMPNN, the standard model for inverse folding, which is a critical component of the evaluation pipeline used to assess the "designability" of generated backbones.
    *Link*: https://www.science.org/doi/10.1126/science.add2187

10. **Daras et al. 2023.** Consistent diffusion models: Mitigating sampling drift by learning to be consistent.
    This work, along with its follow-ups, provides the specific formulation for training diffusion models on data corrupted by known additive Gaussian noise, which is the loss function used by Ambient Protein Diffusion after the initial "annotation" stage.
    *Link*: https://arxiv.org/abs/2302.09057
