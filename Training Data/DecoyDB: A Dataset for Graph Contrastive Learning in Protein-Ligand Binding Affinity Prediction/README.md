https://arxiv.org/abs/2507.06366

**DecoyDB: A Dataset for Graph Contrastive Learning in Protein-Ligand Binding Affinity Prediction**

### 1. Summary and Rating

This paper addresses the significant challenge of data scarcity in predicting protein-ligand binding affinity, a critical task in drug discovery. The authors argue that while labeled data (e.g., the PDBbind dataset) is limited, a vast amount of unlabeled 3D complex structures exists. To leverage this unlabeled data, they propose a self-supervised learning strategy based on graph contrastive learning (GCL).

The primary contribution is the creation of **DecoyDB**, a large-scale dataset specifically designed for this purpose. DecoyDB contains over 61,000 high-resolution protein-ligand complexes from the Protein Data Bank (PDB), each augmented with dozens of computationally generated "decoys." These decoys are alternative, suboptimal binding poses for the ligand, each annotated with its Root Mean Squared Deviation (RMSD) from the true (native) pose. This structure provides well-defined positive pairs (the native pose) and a spectrum of negative pairs (the decoys) essential for contrastive learning.

The second contribution is a customized GCL framework tailored for DecoyDB. This framework features a novel two-category contrastive loss function that distinguishes between two types of negative samples: 1) decoys of the same complex, which are weighted by their RMSD, and 2) structures from different complexes. It also incorporates a denoising score matching (DSM) regularizer, which perturbs ligand coordinates and trains the model to recognize the stability of the original structure.

Experiments demonstrate that pre-training various graph neural network (GNN) models on DecoyDB and fine-tuning on PDBbind consistently improves prediction accuracy, sample efficiency, and model generalization compared to training from scratch or using other pre-training methods.

**Rating: 9/10**

The paper makes a significant and highly valuable contribution to the field of computational drug discovery. The creation of DecoyDB is a substantial undertaking that provides a crucial resource for the community, enabling novel self-supervised learning approaches that were previously difficult to implement. The proposed GCL framework is thoughtfully designed, incorporating domain-specific knowledge (RMSD-weighted loss, structural stability via DSM) into the learning objective. The experimental validation is rigorous and comprehensive, demonstrating clear benefits across multiple GNN architectures and against relevant, state-of-the-art baselines. The work successfully bridges the gap between the abundance of structural data and the scarcity of affinity labels, presenting a well-executed and impactful solution.

### 2. Main Ideas

1.  **The Creation of DecoyDB for Structure-Aware Contrastive Learning:** The central idea is to construct a large-scale dataset to facilitate self-supervised learning for binding affinity prediction. This is achieved by taking real, high-resolution protein-ligand complexes and generating numerous "decoy" poses for each ligand using molecular docking software. Crucially, each decoy is annotated with its RMSD from the native pose, creating a rich set of positive samples (native poses) and structurally-informed negative samples (decoy poses), which is ideal for training models to distinguish between correct and incorrect binding conformations.

2.  **A Customized GCL Framework with Two-Category Loss and Denoising:** The paper introduces a novel training framework that leverages DecoyDB's unique structure. The framework's loss function has two key components:
    *   A **two-category graph contrastive loss** that pushes embeddings of incorrect poses away from the correct one. It intelligently handles two types of negatives: decoys from the same complex (weighted by their RMSD, so worse poses are pushed further away) and poses from different complexes entirely.
    *   A **denoising score matching (DSM) regularizer** that adds noise to the ligand's coordinates and penalizes the model if it cannot recognize the original, unperturbed structure as the most stable (i.e., at a local energy minimum). This enforces a physical constraint on the model.

### 3. 10 Most Important Citations

1.  **Wang et al. (2005)** The pdbbind database: methodologies and updates.
    *   This is the most widely used benchmark dataset containing experimentally measured binding affinities, which the authors use for fine-tuning and evaluating their pre-trained models.

2.  **Berman et al. (2000)** The protein data bank.
    *   This is the primary repository of all experimentally determined biomolecular structures from which the authors sourced the ground-truth complexes for creating DecoyDB.

3.  **Eberhardt et al. (2021)** Autodock vina 1.2. 0: New docking methods, expanded force field, and python bindings.
    *   This molecular docking software was the specific tool used to computationally generate the millions of decoy structures that form the core of the new DecoyDB dataset.

4.  **Chen et al. (2020)** A simple framework for contrastive learning of visual representations.
    *   This foundational paper (SimCLR) on contrastive learning provides the conceptual basis for the graph contrastive learning (GCL) framework developed by the authors.

5.  **Yang et al. (2023)** Geometric interaction graph neural network for predicting protein-ligand binding affinities from 3d structures (gign).
    *   This paper introduced the GIGN model, which the authors use as their strongest baseline GNN and the primary architecture for demonstrating the effectiveness of their pre-training framework.

6.  **Luo et al. (2024)** Enhancing generalizability in protein-ligand binding affinity prediction with multimodal contrastive learning.
    *   This paper (ConBAP) is a direct and contemporary related work that also uses decoys for pre-training, serving as a key baseline to show the superiority of the proposed method and dataset.

7.  **Satorras et al. (2021)** E (n) equivariant graph neural networks.
    *   This work introduced the influential EGNN architecture, which the authors use as another base model to prove that their pre-training framework can improve the performance of various types of GNNs.

8.  **Zaidi et al. (2023)** Pre-training via denoising for molecular property prediction.
    *   This paper provides the direct inspiration and methodological foundation for the denoising score matching (DSM) regularization component of the authors' proposed loss function.

9.  **Li et al. (2024a)** Leak proof pdbbind: a reorganized dataset of protein-ligand complexes for more generalizable binding affinity prediction.
    *   The authors use this "leakage-proof" dataset split (LP-PDBbind) to rigorously test their model's generalization capabilities, adding significant strength to their evaluation.

10. **Kitchen et al. (2004)** Docking and scoring in virtual screening for drug discovery: methods and applications.
    *   This highly-cited review establishes the fundamental importance of accurately predicting protein-ligand binding affinity in the drug discovery pipeline, providing the core motivation for the entire paper.
