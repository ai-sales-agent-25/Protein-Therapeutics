https://www.biorxiv.org/content/10.1101/2025.07.09.663945v1

**EZpred: improving deep learning-based enzyme function prediction using unlabeled sequence homologs**

### 1. Summary and Rating

This paper introduces EZpred, a novel computational pipeline for predicting enzyme function, specifically Enzyme Commission (EC) numbers. The central innovation is its use of features derived from unlabeled sequence homologs—sequences from related proteins that do not have known functional annotations. This approach is inspired by the success of similar strategies in protein structure prediction (e.g., AlphaFold) but has been largely overlooked for function prediction. EZpred consists of two main components: a deep learning (DL) module and a template-based module. The DL component extracts embeddings from both the target sequence and its unlabeled homologs using the ESMC protein language model, concatenates them, and feeds them into a neural network. The template-based component uses traditional sequence (MMseqs2) and structure (Foldseek) searches against databases of annotated proteins. The final prediction is a weighted combination of the outputs from both modules. The authors perform a large-scale benchmark against eight state-of-the-art methods, demonstrating that EZpred achieves a significantly higher F1-score (0.788) for full 4-digit EC number prediction, outperforming the next best methods by at least 27%. Ablation studies confirm that the inclusion of unlabeled homologs, the use of multiple layers from the protein language model, and the hybrid nature of the model are all key contributors to its superior performance.

**Rating: 9/10**

This paper presents a strong and logical contribution to the field of protein function prediction. The central idea of leveraging unlabeled homologous sequences is both novel for this specific problem and well-justified by analogy to the revolutionary advances in protein structure prediction. The methodology is robust, combining a sophisticated deep learning approach with a well-established template-based framework. The evaluation is comprehensive and rigorous, featuring a large-scale benchmark, performance stratification across target difficulty, and thorough ablation studies that convincingly support the authors' claims. The demonstrated performance leap over existing state-of-the-art tools is substantial. The work is a clear advancement and provides a new, powerful direction for function prediction research. The only minor detractor is that the deep learning component does not yet explicitly incorporate 3D structural information, a point the authors acknowledge as a direction for future work.

### 2. Main Ideas

1.  **Leveraging Unlabeled Sequence Homologs for Function Prediction:** The core conceptual advance of this paper is the idea that sequence homologs, even without known functional labels, contain valuable information that can improve function prediction. While deep learning models for structure prediction rely heavily on the co-evolutionary information within multiple sequence alignments (MSAs) of homologs, function prediction models have traditionally used homologs only as templates from which to transfer known annotations. EZpred is the first model to extract features from unlabeled homologs (via a protein language model) and use them as direct input to a deep learning model, significantly boosting prediction accuracy.

2.  **A Hybrid Pipeline Combining Deep Learning and Template-Based Predictions:** EZpred is a composite pipeline that synergistically combines two distinct approaches. It has a deep learning component that learns complex sequence patterns from the target and its homologs, and a template-based component that relies on direct sequence and structure similarity to proteins with known functions. By linearly combining the scores from both modules, EZpred leverages the strengths of each. The deep learning part excels at identifying patterns that might be missed by simple homology, while the template-based part provides robust predictions, especially for difficult targets where structural similarity can be more sensitive than sequence information alone.

3.  **Systematic Optimization through Ablation and Advanced Loss Functions:** The paper demonstrates the importance of specific methodological choices through detailed ablation studies. It shows that using embeddings from the last three layers of the ESMC protein language model is superior to using just the final layer. Furthermore, it highlights the benefit of using a ranking-based loss function (ZLPR loss) and including even rarely occurring EC numbers in the training set, which improves the model's ability to learn from sparse labels. These technical details are crucial for achieving the model's high performance.

### 3. 10 Most Important Citations

1.  **Jumper et al. (2021) Highly accurate protein structure prediction with AlphaFold. Nature 596, 583-589 (2021).**
    This paper is cited as the primary inspiration for using sequence homologs, as AlphaFold's success demonstrated the immense power of co-evolutionary information contained in multiple sequence alignments for prediction tasks.

2.  **Lin et al. (2023) Evolutionary-scale prediction of atomic-level protein structure with a language model. Science 379, 1123-1130 (2023).**
    This paper introduced ESMFold and the underlying ESM-2 protein language model, a foundational technology that EZpred uses (specifically the ESMC variant) to generate feature embeddings from protein sequences.

3.  **Steinegger et al. (2017) MMseqs2 enables sensitive protein sequence searching for the analysis of massive data sets. Nat Biotechnol 35, 1026-1028 (2017).**
    MMseqs2 is the critical search tool used by EZpred to identify both the unlabeled sequence homologs for the deep learning component and the labeled sequence templates for the template-based component.

4.  **van Kempen et al. (2023) Fast and accurate protein structure search with Foldseek. Nat Biotechnol 10.1038/s41587-023-01773-0 (2023).**
    Foldseek is the structural alignment tool used in EZpred's template-based component to find structural templates, complementing the sequence-based search from MMseqs2.

5.  **Song et al. (2024) Accurately predicting enzyme functions through geometric graph learning on ESMFold-predicted structures. Nat Commun 15, 8180 (2024).**
    This paper introduced GraphEC, one of the top-performing state-of-the-art methods that EZpred is benchmarked against and significantly outperforms.

6.  **Yu et al. (2023) Enzyme function prediction using contrastive learning. Science 379, 1358-1363 (2023).**
    This paper introduced CLEAN, another key state-of-the-art enzyme function predictor that serves as a primary benchmark for demonstrating the performance improvement of EZpred.

7.  **Hayes et al. (2025) Simulating 500 million years of evolution with a language model. Science 387, 850-858 (2025).**
    This reference points to the ESMC protein language model, which is the specific model used by EZpred to derive embeddings for the target protein and its homologs.

8.  **Liu et al. (2024) InterLabelGO+: unraveling label correlations in protein function prediction. Bioinformatics 40, btae655 (2024).**
    This is a previous work from the authors that introduced methodological concepts, such as the composite loss function and information content weighting, which are adapted and used in the training of EZpred's deep learning component.

9.  **Su et al. (2022) Zlpr: A novel loss for multi-label classification. arXiv preprint arXiv:2208.02955 (2022).**
    This citation introduces the Zero-bounded Log-sum-exp and Pairwise Rank-based (ZLPR) loss function, which the paper states is a more effective replacement for traditional binary cross-entropy loss and is a key part of EZpred's training regimen.

10. **Varadi et al. (2022) AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models. Nucleic Acids Res 50, D439-D444 (2022).**
    The AlphaFold DB is a critical resource for EZpred's template-based component, providing the high-quality predicted structures that are searched against using Foldseek.
