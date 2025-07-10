https://www.biorxiv.org/content/10.1101/2025.06.09.658639v1.abstract

AbDesign: Database of point mutants of antibodies with associated structures reveals poor generalization of binding predictions from machine learning models.

### 1. Summary and Rating

This paper addresses the critical issue of data scarcity and bias in the development of computational models for predicting antibody-antigen binding affinity. The authors introduce **AbDesign**, a new, high-quality dataset containing 672 single-point mutations in the CDR-H3 region of 14 distinct antibody-antigen complexes, where each of the seven antigens is bound by two different antibodies with known crystal structures. All binding measurements were generated using a standardized ELISA protocol, ensuring experimental consistency.

The authors use this novel dataset as a blind hold-out set to benchmark three state-of-the-art machine learning (ML) models (DSMBind, Binding-DDG-predictor, RDE-PPI) trained on existing public datasets (SKEMPIv2, AB-Bind). The results show that while these ML models perform well on in-distribution data, their predictive power collapses to near-zero correlation on the new, more heterogeneous AbDesign dataset. This failure is attributed to the models learning dataset-specific biases (e.g., overrepresentation of alanine-scanning mutations) and their sensitivity to structural inaccuracies. In stark contrast, the older, physics-based method, FoldX, demonstrates reasonable and consistent predictive power on AbDesign. The paper concludes that current ML-based affinity prediction methods lack generalizability and highlights the urgent need for larger, more diverse, and experimentally standardized datasets to drive progress in computational antibody engineering.

**Rating: 9/10**

This is an excellent paper that makes a significant and timely contribution to the field of computational antibody design. Its primary strength lies in the creation and rigorous application of the AbDesign dataset, which serves as a much-needed, high-quality benchmark. The "negative" result—the failure of modern ML models to generalize—is critically important and provides a sobering reality check on the current hype cycle around data-driven methods. The work is methodologically sound, the analysis is insightful, and the conclusion that robust, generalizable models will likely require hybrid approaches combining data-driven learning with physical principles is well-supported and forward-looking. The paper clearly articulates a major bottleneck in the field and provides a valuable resource to help overcome it.

### 2. Main Ideas

1.  **Creation of a Standardized and Diverse Antibody Affinity Dataset (AbDesign):** The paper's core contribution is the AbDesign database. It was created to address the limitations of existing resources like SKEMPI and AB-Bind, which are often small, experimentally inconsistent, and biased towards specific mutation types like alanine scanning. AbDesign provides 672 new single-point mutation data points across 14 structurally characterized antibody-antigen complexes, with all binding data generated via a uniform ELISA protocol, thereby providing a less biased and more consistent benchmark for model evaluation.

2.  **Modern Machine Learning Models for Affinity Prediction Lack Generalizability:** A key finding is that state-of-the-art ML models, despite performing well on the datasets they were trained on, fail to generalize to the novel sequence and structural contexts presented in the AbDesign dataset. Their predictive correlation drops to nearly zero, indicating they have overfit to biases in the training data and are not yet robust enough for reliable *de novo* prediction on unseen antibody scaffolds.

3.  **Physics-Based Methods Show More Robust Performance:** In contrast to the ML models, the established, physics-based program FoldX maintained reasonable predictive performance on the new AbDesign dataset. This suggests that methods grounded in first principles (e.g., electrostatics, van der Waals forces) are currently more generalizable than purely data-driven approaches and reaffirms their value as tools for antibody engineering, especially for initial filtering of mutations.

### 3. 10 Most Important Citations

1.  **Jankauskaite et al. (2019)** SKEMPI 2.0: an updated benchmark of changes in protein-protein binding energy, kinetics and thermodynamics upon mutation.
    *   This paper describes the SKEMPI 2.0 dataset, a primary resource used for training and benchmarking the machine learning models evaluated in the study.

2.  **Sirin et al. (2016)** AB-Bind: Antibody binding mutational database for computational affinity predictions.
    *   This paper introduces the AB-Bind dataset, another key antibody-specific database of mutation-affinity data that the authors compare and contrast their new AbDesign dataset against.

3.  **Abanades et al. (2022)** ImmuneBuilder: Deep-Learning models for predicting the structures of immune proteins. [https://doi.org/10.1101/2022.11.04.514231](https://doi.org/10.1101/2022.11.04.514231)
    *   This work presents ABodyBuilder2, the deep learning tool used by the authors to model the 3D structures of the antibody mutants, a critical step in their benchmarking pipeline.

4.  **Jin et al. (2023)** DSMBind: SE(3) denoising score matching for unsupervised binding energy prediction and nanobody design.
    *   This is the publication for DSMBind, one of the three modern machine learning models that the authors benchmarked for its ability to predict binding affinity changes.

5.  **Shan et al. (2022)** Deep learning guided optimization of human antibody against SARS-CoV-2 variants with broad neutralization.
    *   This paper is cited as the reference for the Binding-DDG-predictor, the second machine learning model benchmarked, which uses an attention-based geometric neural network.

6.  **Luo et al. (2023)** Rotamer Density Estimator is an Unsupervised Learner of the Effect of Mutations on Protein-Protein Interaction.
    *   This paper describes RDE-PPI, the third state-of-the-art machine learning model evaluated for its performance on the AbDesign dataset.

7.  **Schymkowitz et al. (2005)** The FoldX web server: an online force field.
    *   This citation refers to FoldX, the prominent physics-based energy function that, unlike the ML models, showed robust predictive performance on the new dataset.

8.  **Hummer et al. (2023)** Investigating the volume and diversity of data needed for generalizable antibody-antigen A AG prediction. [https://doi.org/10.1101/2023.05.17.541222](https://doi.org/10.1101/2023.05.17.541222)
    *   The authors leveraged pre-computed FoldX predictions from this study, which itself investigates the data requirements for generalizable antibody-antigen prediction, making it highly relevant.

9.  **Mason, D. M. & Reddy, S. T. (2024)** Predicting adaptive immune receptor specificities by machine learning is a data generation problem.
    *   This conceptual paper supports the central thesis of the work: that the primary limitation in developing effective ML models for antibody design is the lack of large, high-quality experimental data.

10. **Lippow et al. (2007)** Computational design of antibody-affinity improvement beyond in vivo maturation.
    *   This is a seminal paper demonstrating the utility of physics-based computational design; the authors cite it to contextualize the success of FoldX and highlight the enduring power of first-principles approaches.
