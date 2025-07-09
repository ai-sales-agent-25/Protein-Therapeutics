https://www.arxiv.org/abs/2507.05502

**Paper:** Predicting mutational effects on protein binding from folding energy

### 1. Summary and Rating

This paper introduces STAB-DDG, a deep learning model for predicting the effects of mutations on protein-protein binding affinity (∆∆G_bind). The central innovation is a transfer learning approach based on the thermodynamic principle that binding energy can be expressed as a difference in folding energies: ∆G_bind = ∆G_fold(complex) - (∆G_fold(partner A) + ∆G_fold(partner B)). This allows the authors to leverage large, publicly available datasets of protein *folding* stability to address the data scarcity problem in *binding* affinity prediction.

The method begins with a pre-trained inverse folding model, ProteinMPNN, as a zero-shot proxy for folding energy. This model is then sequentially fine-tuned, first on a large folding stability dataset (Megascale) and subsequently on a smaller, curated binding affinity dataset (SKEMPIv2.0). The authors demonstrate that this approach systematically improves performance. The final STAB-DDG model is the first deep learning method to match the accuracy of the state-of-the-art empirical force-field method, FoldX, on a rigorously constructed homology-aware benchmark. Critically, it achieves this performance while being over 1,000 times faster, enabling large-scale *in silico* screening.

**Rating: 9/10**

This is an excellent paper. Its primary strength lies in the clever and principled application of a thermodynamic identity to create a bridge between two related but distinct data domains (folding and binding). This allows the model to overcome the key limitation of data scarcity that has hindered previous deep learning approaches. The methodology is rigorous, featuring careful ablation studies that justify each component of the model and training procedure. The evaluation is thorough and fair, directly addressing recent criticisms of data leakage in the field by using a homology-aware test set. By matching the accuracy of established, but slow, force-field methods with a massive speed-up, the work represents a significant and practical step forward for computational protein engineering.

### 2. Main Ideas

1.  **Binding Energy Prediction via Folding Energy:** The core idea is to reframe the prediction of binding affinity change (∆∆G_bind) as a function of folding energy change (∆∆G_fold). By using the thermodynamic identity ∆∆G_bind(A:B → A':B) = ∆∆G_fold(A:B → A':B) - ∆∆G_fold(A → A'), the authors can leverage models and datasets developed for protein stability to solve the more data-scarce binding prediction problem. This is the first time this identity has been successfully leveraged in a deep learning framework for this task.

2.  **Sequential Transfer Learning from an Inverse Folding Model:** The authors implement this strategy by using a pre-trained inverse folding model, ProteinMPNN, as a proxy for folding energy. They demonstrate a multi-stage training process that systematically improves performance:
    *   **Zero-shot:** Using the pre-trained ProteinMPNN weights with the thermodynamic identity.
    *   **Stability Fine-tuning:** Fine-tuning the model on a large dataset of experimental folding stability measurements (Megascale).
    *   **Binding Fine-tuning:** Further fine-tuning on a smaller, curated dataset of binding affinity measurements (SKEMPIv2.0).

3.  **State-of-the-Art Accuracy with a >1,000x Speedup:** A key result is that STAB-DDG is the first deep learning predictor to match the performance of highly-tuned empirical force-field methods like FoldX on a challenging, leakage-free benchmark. While achieving comparable accuracy, STAB-DDG is orders of magnitude faster due to GPU parallelization, reducing computation time from hours per mutation (for methods like Flex ddG) to fractions of a second. This makes the method highly practical for high-throughput computational screening and design.

### 3. Top 10 Most Important Citations

1.  Dauparas et al. 2022. Robust deep learning-based protein sequence design using ProteinMPNN.
    *   This paper introduced ProteinMPNN, the foundational pre-trained inverse folding model that STAB-DDG uses as its starting point and architectural backbone.

2.  Tsuboyama et al. 2023. Mega-scale experimental analysis of protein folding stability in biology and design.
    *   This provided the Megascale dataset, a massive collection of folding stability measurements that is critical for the first, and most data-rich, fine-tuning stage of the STAB-DDG model.

3.  Jankauskaitė et al. 2019. SKEMPI 2.0: an updated benchmark of changes in protein-protein binding energy, kinetics and thermodynamics upon mutation.
    *   This is the source of the SKEMPIv2.0 dataset, the largest curated public dataset for binding affinity changes, which is used for the final fine-tuning stage and for benchmarking STAB-DDG against all other methods.

4.  Bushuiev et al. 2024. Learning to design protein-protein interactions with enhanced generalization.
    *   This citation is crucial for context, as it highlighted that previous deep learning predictors' superiority was often due to data leakage, and established that classical methods like Flex ddG remained state-of-the-art on properly split data.

5.  Guerois et al. 2002. Predicting changes in the stability of proteins and protein complexes: a study of more than 1000 mutations.
    *   This introduced FoldX, a widely used and highly cited empirical force-field method that serves as a key performance benchmark which STAB-DDG successfully matches.

6.  Barlow et al. 2018. Flex ddG: Rosetta ensemble-based estimation of changes in protein-protein binding affinity upon mutation.
    *   This introduced Flex ddG, another state-of-the-art Rosetta-based force-field predictor that the authors use as a top-performing, albeit computationally expensive, baseline for comparison.

7.  Notin et al. 2023. Proteingym: Large-scale benchmarks for protein fitness prediction and design.
    *   This work corroborated the strong correlation between sequence log-likelihoods and folding energies for models like ProteinMPNN, providing a key piece of evidence that justifies the paper's core assumption.

8.  Riesselman et al. 2018. Deep generative models of genetic variation capture the effects of mutations.
    *   This is a foundational paper that first showed deep learning models of protein sequences could predict the effects of mutations, establishing the link between log-likelihoods and fitness that this paper builds upon.

9.  Alford et al. 2017. The Rosetta all-atom energy function for macromolecular modeling and design.
    *   This paper describes the Rosetta energy function, which is the underlying engine for the powerful Flex ddG baseline, making it essential for understanding the classical methods being compared against.

10. Hsu et al. 2022b. Learning inverse folding from millions of predicted structures.
    *   This paper introduced ESM-IF1, an alternative inverse folding model compared in the benchmarks, and is also representative of the large-scale pre-training paradigm on which this work depends.
