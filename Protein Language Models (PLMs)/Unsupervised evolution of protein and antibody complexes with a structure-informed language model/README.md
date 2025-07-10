https://pubmed.ncbi.nlm.nih.gov/38963838/

**Unsupervised evolution of protein and antibody complexes with a structure-informed language model**

### 1. Summary and Rating

This paper demonstrates a highly efficient, unsupervised method for protein and antibody engineering using a structure-informed language model, ESM-IF1. The authors' core hypothesis is that by guiding sequence exploration to variants that a model predicts will maintain the original protein backbone structure, one can enrich for functionally beneficial mutations without any task-specific training data. They first validate this concept retrospectively, showing that the model, when conditioned on a protein's structure, is significantly better at identifying high-fitness variants from large mutational scanning datasets across 10 diverse proteins compared to a leading sequence-only model.

Crucially, the authors show that ESM-IF1, which was trained only on single-chain proteins, can be extended to engineer multi-chain protein complexes. By providing the structure of an antibody-antigen complex, the model implicitly learns features of the binding interface and suggests mutations that improve function. The main contribution is a prospective experimental validation where they engineer two clinical SARS-CoV-2 antibodies (bebtelovimab and SA58). By screening only ~30 model-recommended variants for each, they successfully identified mutations that conferred up to a 25-fold improvement in neutralization and a 37-fold improvement in binding affinity against antibody-escaped viral variants like BQ.1.1 and XBB.1.5. The work highlights the power of using structural information as a general prior for fitness, enabling rapid and efficient evolution of therapeutically relevant proteins.

**Rating: 9/10.** This paper is excellent. Its primary strength lies in the elegant and powerful application of an existing model (ESM-IF1) to a new and impactful problem domain: the unsupervised evolution of multi-chain complexes. The generalization from single-chain training to multi-chain application is a significant and non-obvious step. The study is rigorously validated with both retrospective computational analyses and, most impressively, a successful and highly efficient prospective experimental campaign on clinically relevant antibodies. This convincingly demonstrates the method's practical utility in accelerating therapeutic development, a major advance over traditional directed evolution or models that require task-specific labeled data.

### 2. Main Ideas

1.  **Structure-Informed Likelihood as a General Prior for Fitness:** The central idea is that a protein's three-dimensional structure provides a powerful, task-agnostic prior for its function. By using an inverse folding model (ESM-IF1) to find sequences with a high likelihood of folding into a given backbone, the method effectively filters out destabilizing mutations. This constrains the vast search space to a smaller, more promising region of the fitness landscape, enriching for variants that are not only stable but also functionally improved, all without needing to be trained on specific experimental fitness data.

2.  **Generalization of Inverse Folding to Multi-Protein Complexes:** The authors demonstrate that a model trained exclusively on single-chain proteins can be successfully applied to engineer multi-chain protein complexes, such as an antibody bound to its antigen. By conditioning the model on the backbone coordinates of the entire complex, it implicitly learns to favor mutations that preserve or enhance the stability of the binding interface, effectively predicting mutations that improve binding affinity and neutralization potency.

3.  **Efficient, Unsupervised Directed Evolution:** The paper showcases a practical and highly efficient workflow for directed evolution. By experimentally testing only a small number of top-scoring variants suggested by the model, they achieved substantial improvements in the potency of two clinical antibodies against new viral escape variants. This "zero-shot" prediction capability, which requires no initial round of experimental data collection for model training, represents a significant acceleration of the protein engineering cycle compared to both traditional methods and many other machine learning-guided approaches.

### 3. 10 Most Important Citations

1.  Hsu et al. (2022) "Learning inverse folding from millions of predicted structures"
    This paper introduces ESM-IF1, the core structure-informed language model that the authors adapt and apply for their unsupervised evolution framework.
    Link: https://proceedings.mlr.press/v162/hsu22a.html

2.  Jumper et al. (2021) Highly accurate protein structure prediction with AlphaFold.
    This paper describes AlphaFold, a landmark in structure prediction; the current work positions itself as solving the "inverse" problem to guide protein design.

3.  Meier et al. (2021) Language models enable zero-shot prediction of the effects of mutations on protein function.
    This paper introduces ESM-1v, a leading sequence-only protein language model used as a key performance baseline, highlighting the added value of the structural information in the current study.

4.  Dauparas et al. (2022) Robust deep learning based protein sequence design using ProteinMPNN.
    This describes ProteinMPNN, a state-of-the-art alternative structure-based design model, which serves as an important point of comparison for the performance of their method on protein complexes.

5.  Hie et al. (2023) Efficient evolution of human antibodies from general protein language models.
    This work provides the sequence-only baseline method used for the head-to-head experimental comparison, demonstrating that the structure-informed model yields substantially better final antibody designs.

6.  Westendorf et al. (2022) LY-CoV1404 (bebtelovimab) potently neutralizes SARS-CoV-2 variants.
    This paper characterizes bebtelovimab (LY-CoV1404), one of the two clinical antibodies the authors successfully engineer, providing the experimental and clinical context for their main result.

7.  Cao et al. (2022) Rational identification of potent and broad sarbecovirus-neutralizing antibody cocktails from SARS convalescents.
    This paper characterizes SA58, the second clinical antibody the authors engineer, providing the necessary background for their successful evolution campaign against SARS-CoV-2 variants.

8.  Phillips et al. (2021) Binding affinity landscapes constrain the evolution of broadly neutralizing anti-influenza antibodies.
    This study provides key experimental datasets on influenza antibody binding affinity that the authors use for the retrospective validation of their model's predictive power on combinatorial mutations.

9.  Koenig et al. (2017) Mutational landscape of antibody variable domains reveals a switch modulating the interdomain conformational dynamics and antigen binding.
    This paper provides the deep mutational scanning dataset for the G6.31 antibody against VEGF-A, which is used as another important retrospective validation case for the model's performance.

10. Romero et al. (2009) Exploring protein fitness landscapes by directed evolution.
    This highly-cited review articulates the fundamental challenges of directed evolution and navigating protein fitness landscapes, which is the core problem the authors' computational method is designed to solve more efficiently.
