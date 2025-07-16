https://arxiv.org/abs/2507.10877

BioScore: A Foundational Scoring Function For Diverse Biomolecular Complexes

### 1. Summary and Rating

This paper introduces BioScore, a novel foundational scoring function designed to assess a wide and diverse range of biomolecular complexes, including protein-ligand, protein-protein, protein-nucleic acid, and nucleic acid-ligand interactions, as well as more challenging systems like cyclic peptides and carbohydrates. The central problem the authors address is the lack of generalizability in existing scoring functions, which are typically tailored to specific systems (e.g., only protein-small molecule) and tasks. BioScore employs a unified dual-scale (atom and block-level) geometric graph representation and an equivariant transformer architecture to create a single, versatile framework.

A key aspect of their methodology is a pre-training/fine-tuning strategy where the model is pre-trained on large, mixed-structure datasets (e.g., combining protein-ligand and protein-protein complexes) to learn universal principles of molecular interaction. This approach is shown to significantly boost performance, particularly in data-scarce domains, enabling effective zero-shot and few-shot predictions. The paper also introduces a new comprehensive benchmark for protein-protein interactions (PPI Benchmark) to facilitate more rigorous and standardized evaluation. Across 16 benchmark tasks, BioScore is shown to consistently achieve state-of-the-art or near state-of-the-art performance against 70 other methods, demonstrating its capabilities in scoring, ranking, docking, and screening.

**Rating: 9.5/10**

This paper is a significant contribution to the field of computational biology and drug discovery. The ambition to create a universal scoring function is high, and the execution is remarkably thorough. The development and validation of BioScore are rigorous, supported by extensive benchmarking, insightful ablation studies, and strong performance in challenging zero-shot scenarios. The introduction of a new, well-constructed PPI benchmark is a valuable contribution in its own right. By successfully bridging the gap between specialized models and demonstrating strong cross-domain knowledge transfer, BioScore represents a major step towards more generalizable and powerful tools for structural assessment, addressing a critical need in the post-AlphaFold era.

### 2. Main Ideas

1.  **A Unified Framework for All Biomolecules:** The core idea is the creation of a single, foundational scoring function that transcends molecular classes. Instead of developing separate models for proteins, nucleic acids, and small molecules, BioScore uses a unified geometric graph representation that treats all systems with a consistent dual-scale (atomic and block-level) approach. This allows it to process and learn from heterogeneous data, breaking down the silos that have traditionally limited the scope of scoring functions.

2.  **Cross-Domain Pre-training for Generalization:** The paper demonstrates that pre-training on a diverse mix of biomolecular complex types is critical for achieving high performance and generalizability. By learning from the combined structural data of, for example, protein-ligand and protein-protein interactions, the model captures fundamental physical and geometric patterns that are transferable. This strategy effectively addresses the data sparsity problem in less-studied domains (like nucleic acid-ligand interactions) and enables robust zero-shot and few-shot learning.

3.  **Task-Versatile, Physics-Inspired Architecture:** BioScore is designed not just for one purpose but for the four key tasks of scoring, ranking, docking, and screening. It achieves this with a dual-tower architecture inspired by the inverse Boltzmann distribution for statistical potentials. One pathway is optimized for docking/screening by identifying native-like conformations, while the other is tailored for scoring/ranking by more directly modeling binding free energy. This design, combined with a novel "interface-masking" strategy, allows BioScore to balance generality with high performance across its full range of functions.

### 3. 10 Most Important Citations

1.  **Abramson, J. et al. (2024)** Accurate structure prediction of biomolecular interactions with AlphaFold 3.
    This citation is crucial context, as the authors position BioScore as a solution to a key limitation of AlphaFold3—its inability to accurately score and rank binding affinities, which is essential for functional interpretation and drug discovery.

2.  **Kong, X. et al. (2024)** Generalist Equivariant Transformer Towards 3D Molecular Interaction Learning. Preprint at https://doi.org/10.48550/arXiv.2306.01474
    This paper provides the core encoder architecture (GET, or Geometric Equivariant Transformer) that BioScore adopts to enable its unified, E(3)-equivariant representation of diverse biomolecular complexes.

3.  **Wang, R. et al. (2004)** The PDBbind Database: Collection of Binding Affinities for Protein-Ligand Complexes with Known Three-Dimensional Structures.
    This is the foundational dataset from which the vast majority of the training, validation, and testing data for all complex types in the study is sourced, making it indispensable to the paper's results.

4.  **Su, M. et al. (2019)** Comparative Assessment of Scoring Functions: The CASF-2016 Update.
    This is the gold-standard benchmark for protein-ligand scoring functions, against which BioScore's performance is extensively compared to establish its state-of-the-art capabilities in the most data-rich domain.

5.  **Shen, C. et al. (2022)** Boosting Protein-Ligand Binding Pose Prediction and Virtual Screening Based on Residue-Atom Distance Likelihood Potential and Graph Transformer.
    This is a previous, more specialized model (RTMScore) from the authors' group, whose limitations in efficiency and generalizability are explicitly mentioned as the motivation for developing the more foundational BioScore.

6.  **Fang, A. et al. (2025)** ATOMICA: Learning Universal Representations of Intermolecular Interactions. Preprint at https://doi.org/10.1101/2025.04.02.646906
    Cited as a contemporary effort to create a generalist model for molecular interactions, this paper helps situate BioScore within the current landscape of research on universal biomolecular models.

7.  **Ullanat, V. et al. (2025)** Learning the language of protein-protein interactions. Preprint at https://doi.org/10.1101/2025.03.09.642188
    This paper introduces MINT, a top-performing model for protein-protein interaction scoring, which serves as a key benchmark and competitor that helps to highlight BioScore's broader versatility (i.e., its docking and screening abilities).

8.  **Mysinger, M. M. et al. (2012)** Directory of Useful Decoys, Enhanced (DUD-E): Better Ligands and Decoys for Better Benchmarking.
    This provides a widely-used external benchmark dataset for virtual screening, which is used to validate BioScore's generalization performance for differentiating active from inactive compounds.

9.  **Pierce, B. G. et al. (2011)** Accelerating Protein Docking in ZDOCK Using an Advanced 3D Convolution Library.
    The ZDOCK program was used to generate the vast number of decoy conformations required to construct the authors' novel and comprehensive PPI Benchmark, making this citation methodologically critical.

10. **Nguyen, E. et al. (2024)** Sequence modeling and design from molecular to genome scale with Evo.
    The authors cite the Evo model series as a landmark foundational framework for biomolecular modeling on the sequence level, providing a parallel to BioScore's goal of creating a foundational model on the structural level.
