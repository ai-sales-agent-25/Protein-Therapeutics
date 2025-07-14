https://www.biorxiv.org/content/10.1101/2025.07.08.663754v1

**Closing the loop: Teaching single-cell foundation models to learn from perturbations**

### 1. Summary and Rating

This paper introduces and validates a "closed-loop" framework to improve the predictive accuracy of single-cell foundation models (scFMs). The authors first benchmark a state-of-the-art scFM, Geneformer, and show that its *in silico* perturbation (ISP) predictions, while better than differential expression on some metrics, suffer from a very low positive predictive value (PPV) of ~3%. This "open-loop" approach, where models predict but do not learn from experimental outcomes, is thus inefficient for guiding research. The core innovation is to "close the loop" by incorporating experimental perturbation data (both genetic and chemical) into the model's fine-tuning process.

The authors demonstrate that this closed-loop approach significantly enhances performance, tripling the PPV to 9% and substantially increasing the AUROC in a T-cell activation model. They find that as few as 20 perturbation examples are needed to achieve this improvement. They then apply this framework to a clinically relevant problem: the rare pediatric disease *RUNX1*-familial platelet disorder (*RUNX1*-FPD). The closed-loop model successfully prioritized therapeutic targets, including the mTOR and CD74-MIF signaling pathways, which were subsequently validated experimentally. Notably, the identification of the mTOR pathway as a target by this model has supported the launch of a phase 2 clinical trial. The work represents a critical step toward creating more accurate and useful "virtual cell" models that can accelerate biomedical discovery.

**Rating: 9/10**

This is a high-quality paper that addresses a well-recognized, critical limitation in a rapidly advancing field. The "closed-loop" concept is not new in machine learning, but its systematic application and rigorous benchmarking for single-cell foundation models are novel and impactful. The study design is excellent, using a well-studied system (T-cell activation) for methodical benchmarking against large-scale orthogonal data, and then demonstrating profound real-world utility in a rare disease context. The experimental validation of predicted targets, culminating in a clinical trial, provides powerful evidence for the framework's potential. The paper is clearly written and the findings are a significant contribution toward making *in silico* models a truly effective tool for hypothesis generation and therapeutic discovery.

### 2. Main Ideas

1.  **Standard "Open-Loop" Foundation Models Have Poor Predictive Accuracy:** The paper first establishes a critical baseline by benchmarking a state-of-the-art single-cell foundation model (scFM). It shows that while these models can predict the effects of genetic perturbations *in silico*, their predictions have a very low positive predictive value (~3%), making them unreliable for prioritizing which experiments to perform. This highlights a major gap between the promise and the practical utility of current scFMs.

2.  **"Closing the Loop" by Incorporating Perturbation Data Improves Predictions:** The central thesis is that model accuracy can be dramatically improved by creating a feedback loop. The authors develop a "closed-loop" framework where experimental data from perturbation screens (e.g., Perturb-seq or chemical screens) are used to further fine-tune the scFM. This iterative refinement significantly boosts performance, tripling the positive predictive value and substantially improving other metrics. A key finding is that even a small number of experimental examples (~20) can lead to substantial gains in accuracy.

3.  **The Closed-Loop Framework Can Accelerate Drug Discovery for Rare Diseases:** The authors demonstrate the practical power of their framework by applying it to *RUNX1*-familial platelet disorder, a rare disease where patient samples are scarce. The model, enhanced with data from a small chemical screen, successfully identified and prioritized novel therapeutic targets. The subsequent experimental validation of these targets, such as the mTOR pathway (leading to a clinical trial) and the CD74-MIF signaling axis, showcases the framework's potential to accelerate the development of treatments for challenging diseases.

### 3. 10 Most Important Citations

1.  **Theodoris, C. V. et al.** (2023) Transfer learning enables predictions in network biology. This paper introduces Geneformer, the specific single-cell foundation model used as the base for the open- and closed-loop frameworks evaluated in this study.
    - Link: [https://doi.org/10.1038/s41586-023-06139-9](https://doi.org/10.1038/s41586-023-06139-9)

2.  **Schmidt, R. et al.** (2022) CRISPR activation and interference screens decode stimulation responses in primary human T cells. This study provides the large-scale CRISPR screen data used as the "ground truth" for systematically benchmarking and validating the T-cell activation prediction models.
    - Link: [https://doi.org/10.1126/science.abj4008](https://doi.org/10.1126/science.abj4008)

3.  **Bunne, C. et al.** (2024) How to build the virtual cell with artificial intelligence: Priorities and opportunities. This reference establishes the broad conceptual goal of creating a "virtual cell," providing the high-level motivation for the current paper's work on improving predictive models of cellular behavior.
    - Link: [https://doi.org/10.1016/j.cell.2024.05.034](https://doi.org/10.1016/j.cell.2024.05.034)

4.  **Regev, A.** (2024) Design for Inference: From Random Experiments to Lab in the Loop. This perspective piece is cited for articulating the "Lab in the Loop" concept, which is the direct intellectual foundation for the "closed-loop" framework presented in the paper.
    - No link provided in paper.

5.  **Li, C. et al.** (2024) Benchmarking AI Models for In Silico Gene Perturbation of Cells. This paper is cited to frame the problem, as it is a recent, large-scale benchmark of existing models for in silico perturbation that highlights current challenges.
    - Link: [https://doi.org/10.1101/2024.12.20.629581](https://doi.org/10.1101/2024.12.20.629581)

6.  **Cui, H. et al.** (2024) scGPT: toward building a foundation model for single-cell multi-omics using generative AI. This paper is cited as a key example of a contemporary, powerful single-cell foundation model, helping to position the current work within the state-of-the-art landscape.
    - Link: [https://doi.org/10.1038/s41592-024-02201-0](https://doi.org/10.1038/s41592-024-02201-0)

7.  **Lopez, R., et al.** (2018) Deep generative modeling for single-cell transcriptomics. This is the foundational paper for scVI, one of the first and most influential deep generative models for single-cell analysis, which helped establish the field that scFMs are built upon.
    - Link: [https://doi.org/10.1038/s41592-018-0229-2](https://doi.org/10.1038/s41592-018-0229-2)

8.  **Mohammadhosseini, M. et al.** (2025) Targeting the CD74 signaling axis suppresses inflammation and rescues defective hematopoiesis in RUNX1 -familial platelet disorder. This citation provides crucial in vivo validation for one of the novel therapeutic targets (CD74-MIF) identified by the closed-loop model, strongly supporting the model's predictive power.
    - Link: [https://doi.org/10.1126/scitranslmed.adn9832](https://doi.org/10.1126/scitranslmed.adn9832)

9.  **Fan, A. C. et al.** (2023) RUNX1 loss renders hematopoietic and leukemic cells dependent on IL-3 and sensitive to JAK inhibition. This reference is critical for the *RUNX1*-FPD application, as it describes the guide RNA sequence for targeting *RUNX1* that was used in the study's in vitro model.
    - Link: [https://doi.org/10.1172/JCI167053](https://doi.org/10.1172/JCI167053)

10. **Bak, R. O. et al.** (2017) Multiplexed genetic engineering of human hematopoietic stem and progenitor cells using CRISPR/Cas9 and AAV6. This paper is cited in the methods for providing the control guide RNA sequence targeting the AAVS1 safe-harbor locus, which was essential for the experimental design of the *RUNX1*-FPD studies.
    - Link: [https://doi.org/10.7554/eLife.27873](https://doi.org/10.7554/eLife.27873)
