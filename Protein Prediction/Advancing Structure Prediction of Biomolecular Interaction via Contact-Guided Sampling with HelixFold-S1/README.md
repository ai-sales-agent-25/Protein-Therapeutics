https://arxiv.org/abs/2507.09251

Advancing Structure Prediction of Biomolecular Interaction via Contact-Guided Sampling with HelixFold-S1

### 1. Summary and Rating

This paper introduces HelixFold-S1, a deep learning model for predicting the structures of biomolecular complexes. The model's key innovation is a contact-guided sampling strategy designed to overcome the limitations of existing methods, particularly for challenging targets like protein-antibody complexes that lack co-evolutionary signals. Instead of relying on indiscriminate or random sampling of conformations, HelixFold-S1 follows a three-stage process: 1) it first predicts a probability map of contacts between the interacting molecules; 2) it then intelligently samples high-probability contacts to use as constraints; and 3) it generates and ranks structures guided by these constraints. This targeted approach enhances the diversity of generated conformations and more efficiently explores the conformational space. The authors demonstrate through extensive benchmarking that HelixFold-S1 consistently outperforms baseline models (including its predecessor, HelixFold3) and other state-of-the-art sampling methods across a wide range of interaction types, such as protein-protein, protein-antibody, protein-ligand, protein-RNA, and protein-DNA. The paper also establishes that the predicted contact probabilities can serve as a useful metric for gauging the intrinsic difficulty of a prediction task, helping to guide the allocation of computational resources.

**Rating: 8.5/10**

The paper presents a methodologically sound and significant incremental advance on the state-of-the-art in biomolecular structure prediction. The core idea of using predicted contacts to guide test-time sampling is an elegant and effective solution to the inefficiencies of brute-force sampling. The experimental validation is rigorous and comprehensive, with strong comparisons against relevant, cutting-edge baselines on carefully curated, non-data-leaked test sets. The demonstrated performance gains, especially on difficult antibody cases, are substantial and practically relevant. While not a complete paradigm shift, it represents a clever and powerful engineering contribution that meaningfully advances the field's ability to tackle complex structural modeling problems.

### 2. Main Ideas

1.  **Contact-Guided Sampling for Structure Prediction:** The central idea is to replace random sampling with a more intelligent, targeted strategy. The model first predicts the probability of contact for all pairs of residues between interacting molecules. It then uses these probabilities to guide the generation of structures, prioritizing conformations that satisfy high-probability contacts. This focuses computational effort on the most plausible binding modes, improving both efficiency and accuracy.
2.  **Enhancing Conformational Diversity and Accuracy through Test-Time Scaling:** The paper demonstrates that by increasing the number of samples, prediction accuracy consistently improves, a concept known as test-time scaling. The contact-guided approach of HelixFold-S1 makes this scaling particularly effective, as it generates a more diverse and higher-quality pool of candidate structures compared to methods using random sampling. This is especially crucial for difficult targets where single-shot predictions often fail.
3.  **Predicted Contact Probability as a Difficulty Proxy:** The model's initial contact probability prediction serves a dual purpose. Beyond guiding the sampling, the paper shows a strong correlation between the highest predicted contact probability for a target and its final prediction accuracy. Targets with low initial probabilities are intrinsically harder to model and benefit most from extensive sampling, while those with high probabilities are often solved with a single prediction. This provides an interpretable indicator of a problem's difficulty before committing to large-scale computation.

### 3. 10 Most Important Citations

1.  **Abramson et al. 2024. Accurate structure prediction of biomolecular interactions with alphafold 3.**
    This paper introduces AlphaFold3, the state-of-the-art model for biomolecular interaction prediction, whose architecture serves as the foundation for HelixFold-S1.

2.  **Jumper et al. 2021. Highly accurate protein structure prediction with alphafold.**
    This is the foundational paper for AlphaFold2, which revolutionized protein structure prediction and established the core deep learning architecture that later models, including HelixFold-S1, are built upon.

3.  **Liu et al. 2024. Technical report of helixfold3 for biomolecular structure prediction.**
    This paper describes HelixFold3, the direct predecessor to HelixFold-S1, which serves as the base model that is extended with the new contact-guided sampling modules.

4.  **Wallner, B. 2023. Afsample: improving multimer prediction with alphafold using massive sampling.**
    This paper introduces AFsample, a key method for improving complex prediction through massive, non-guided sampling, which serves as a primary baseline to demonstrate the superiority of HelixFold-S1's guided approach.

5.  **Evans et al. 2021. Protein complex prediction with alphafold-multimer.**
    This work extended the original AlphaFold to predict the structure of protein complexes, a critical step towards the generalized biomolecular interaction prediction tackled by HelixFold-S1.

6.  **Basu et al. 2016. Dockq: a quality measure for protein-protein docking models.**
    This paper introduces the DockQ score, the primary metric used throughout the study to evaluate the quality of predicted protein-protein and protein-antibody complex structures.

7.  **Burley et al. 2017. Protein data bank (pdb): the single global macromolecular structure archive.**
    This citation refers to the Protein Data Bank, which is the essential source of the experimental structures used for training, finetuning, and evaluating the HelixFold-S1 model.

8.  **team, C.D. et al. 2024. Chai-1: Decoding the molecular interactions of life.**
    This paper describes Chai-1, a state-of-the-art AF3-like model that was used as a key competitive baseline for benchmarking the performance of HelixFold-S1 on protein-antibody complexes.

9.  **Passaro et al. 2025. Boltz-2: Towards accurate and efficient binding affinity prediction.**
    This paper introduces Boltz-2, another leading structure prediction model that was used as a performance baseline to benchmark HelixFold-S1, highlighting its competitiveness in the field.

10. **Baek et al. 2021. Accurate prediction of protein structures and interactions using a three-track neural network.**
    This paper introduced RoseTTAFold, a method that, alongside AlphaFold2, represented a major breakthrough in protein structure prediction and established many of the core architectural concepts used today.
