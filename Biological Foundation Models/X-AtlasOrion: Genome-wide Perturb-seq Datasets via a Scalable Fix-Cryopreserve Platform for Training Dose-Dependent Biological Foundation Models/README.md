https://www.biorxiv.org/content/10.1101/2025.06.11.659105v1

**Paper:** X-Atlas/Orion: Genome-wide Perturb-seq Datasets via a Scalable Fix-Cryopreserve Platform for Training Dose-Dependent Biological Foundation Models

### 1. Summary and Rating

**Summary:**
This paper introduces "Fix-Cryopreserve-ScRNAseq" (FiCS) Perturb-seq, an industrialized platform designed to address the critical need for large-scale, high-quality, causal perturbation data for training biological foundation models. The authors identify key bottlenecks in existing Perturb-seq protocols—namely scalability limitations, batch effects, and logistical constraints of working with fresh cells—and propose a workflow to overcome them. The FiCS platform integrates reversible chemical fixation, fixation-compatible FACS enrichment, long-term cryopreservation of perturbed cells, high-throughput microfluidics, and automation. This decouples the complex process of cell harvesting from library preparation, significantly improving scalability and reducing experimental variability.

As a demonstration of this platform, the authors generated and released X-Atlas/Orion, the largest publicly available Perturb-seq dataset to date. It consists of two genome-wide screens targeting all human protein-coding genes in HCT116 and HEK293T cells, totaling over eight million cells with deep sequencing. The paper validates that the FiCS platform produces high-quality data with high sensitivity and low batch effects, which successfully recapitulates known biological pathways. A key analytical innovation is the demonstration that sgRNA transcript abundance can serve as a reliable proxy for gene knockdown (KD) efficiency. This allows for the stratification of cells by perturbation strength, enabling the study of dose-dependent genetic effects and providing a richer, more quantitative dataset for building nuanced causal models of cell biology.

**Rating: 9/10**
This is an exceptional resource and methods paper that represents a significant step forward for the field of functional genomics and computational biology. The technical innovation of the FiCS platform thoughtfully addresses major, practical challenges in scaling Perturb-seq, making genome-scale experiments more feasible and reliable. The primary contribution—the X-Atlas/Orion dataset—is immense in its scale and depth, providing an invaluable public resource that will undoubtedly fuel the development of next-generation biological foundation models. The conceptual advance of using sgRNA abundance to measure dose-response is a crucial insight that moves the field beyond a binary view of genetic perturbations. The paper is well-executed, with rigorous benchmarking against previous state-of-the-art datasets. While its main output is the platform and the data rather than a novel biological discovery, its foundational importance for enabling future discoveries is clear. The rating is exceptionally high, with a minor deduction only because it is a preprint and the full impact of the dataset is yet to be realized by the community.

### 2. Main Ideas

1.  **The FiCS Perturb-seq Platform:** The central technical contribution is the development of an industrialized workflow that makes genome-wide Perturb-seq screens scalable and reproducible. By combining reversible cell fixation, cryopreservation, and automation, the FiCS platform solves major logistical hurdles, decouples experimental stages, and minimizes batch effects, thereby improving data quality and throughput.
2.  **The X-Atlas/Orion Dataset:** The paper introduces and releases a massive, deeply-sequenced, genome-wide Perturb-seq dataset covering all human protein-coding genes in two different cell lines. Comprising eight million cells, this is the largest resource of its kind and is intended to serve as a foundational dataset for training causal AI models in biology.
3.  **Dose-Dependent Analysis via sgRNA Abundance:** A key analytical insight is that the abundance of sgRNA UMIs within a cell strongly correlates with the efficacy of gene knockdown. This allows researchers to use sgRNA counts as a proxy for perturbation strength, enabling the study of dose-dependent cellular responses and providing a more quantitative and nuanced framework for understanding genetic interactions.

### 3. 10 Most Important Citations

1.  Replogle et al. (2022). Mapping information-rich genotype-phenotype landscapes with genome-scale Perturb-seq.
    *   This paper provides the previous state-of-the-art genome-scale Perturb-seq dataset, which serves as the primary benchmark for data quality, consistency, and KD efficiency comparisons throughout the manuscript.
2.  Dixit et al. (2016). Perturb-Seq: Dissecting Molecular Circuits with Scalable Single-Cell RNA Profiling of Pooled Genetic Screens.
    *   This is a seminal paper that first introduced the Perturb-seq methodology, making it a foundational citation for the entire field and the core technology this work aims to scale.
3.  Adamson et al. (2016). A Multiplexed Single-Cell CRISPR Screening Platform Enables Systematic Dissection of the Unfolded Protein Response.
    *   Published back-to-back with Dixit et al., this is another foundational paper establishing the single-cell CRISPR screening approach that the current work is built upon.
4.  Replogle et al. (2020). Combinatorial single-cell CRISPR screens by direct guide RNA capture and targeted sequencing.
    *   This paper describes the "direct capture" method for detecting sgRNAs, which the authors explicitly state they use in their FiCS platform for more robust sgRNA decoding compared to other methods.
5.  Cui et al. (2024). scGPT: toward building a foundation model for single-cell multi-omics using generative AI.
    *   Cited as a prime example of the biological "foundation models" whose development is currently limited by the lack of large-scale interventional data, motivating the entire study.
6.  Alerasool et al. (2020). An efficient KRAB domain for CRISPRi applications in human cells.
    *   This paper describes the dCas9-KRAB-Zim3 effector, which the authors selected for their CRISPRi system due to its reported high knockdown efficiency, making it a key component of their experimental design.
7.  Jiménez-Gracia et al. (2024). FixNCut: single-cell genomics through reversible tissue fixation and dissociation.
    *   This citation provides recent technical validation for the concept of using reversible chemical fixation for single-cell genomics, which is the core principle of the "Fix" step in the FiCS platform.
8.  Szklarczyk et al. (2021). The STRING database in 2021: customizable protein-protein networks, and functional characterization of user-uploaded gene/measurement sets.
    *   The STRING database is used as an external source of known protein-protein interactions to validate the biological coherence of the X-Atlas/Orion data, showing that transcriptomic correlations align with physical interactions.
9.  Song et al. (2025). Decoding heterogeneous single-cell perturbation responses.
    *   This work is cited as a complementary computational approach for inferring perturbation strength, highlighting the novelty and directness of the authors' method of using sgRNA abundance as a proxy.
10. Datlinger et al. (2017). Pooled CRISPR screening with single-cell transcriptome readout.
    *   This paper introduced CROP-seq, another of the pioneering methods for combining pooled CRISPR screens with scRNA-seq, establishing the fundamental principles upon which this large-scale study is based.
