https://www.biorxiv.org/content/10.1101/2024.11.27.625792v3

State-specific Peptide Design Targeting G Protein-coupled Receptors

### 1. Summary and Rating

This paper presents a novel computational pipeline for designing peptides that target specific conformational states (active or inactive) of G protein-coupled receptors (GPCRs). The authors aim to overcome the limitation of existing methods that primarily focus on binding affinity without controlling for the functional outcome (i.e., agonism vs. antagonism). The core of their approach is **HelixFold-Multistate**, an AI-based structure prediction model they developed by fine-tuning a reproduction of AlphaFold-Multimer on GPCR-peptide complex data and integrating state-specific modeling techniques. The pipeline first generates a diverse pool of peptide candidates using known structural scaffolds and an inverse folding model. Then, HelixFold-Multistate predicts the complex structures for a specified receptor state (active or inactive) and filters candidates based on confidence metrics (pAE and pLDDT) and state-specificity.

The authors demonstrate the pipeline's effectiveness by successfully designing and experimentally validating novel agonists and antagonists for three distinct GPCRs: the Apelin Receptor (APJR), the Glucagon-Like Peptide-1 Receptor (GLP-1R), and the Growth Hormone Secretagogue Receptor (GHSR). They achieve de novo agonists with high affinity (e.g., EC50 < 10 nM for APJR) and antagonists with moderate affinity (e.g., IC50 of 874 nM for GLP-1R). The work represents a significant step forward in rational peptide design by explicitly incorporating the functional state of the target receptor into the design process.

**Rating: 9/10**

This is a high-quality paper that addresses a critical challenge in GPCR drug discovery. The novelty lies in the development and application of a state-specific design framework, which is a conceptual leap beyond simple binder design. The methodology is rigorous, combining state-of-the-art AI models with thorough computational benchmarking and, most importantly, compelling wet-lab validation across multiple, therapeutically relevant targets. The ability to computationally direct the functional outcome of a designed peptide is highly impactful. The paper is well-written, and the results convincingly support the authors' claims. It falls just short of a perfect score as the authors acknowledge that the confidence metrics are not yet a perfect proxy for binding affinity, and future work is needed to integrate more precise energy-based scoring and other pharmacological properties.

### 2. Main Ideas

1.  **State-Specific Design Framework:** The central idea is to design peptides not just to bind to a GPCR, but to selectively stabilize either its active or inactive conformation, thereby controlling whether the peptide acts as an agonist or an antagonist. This is achieved by specifying the desired functional state of the GPCR at the beginning of the computational pipeline, which then guides the screening and selection of peptide candidates.

2.  **HelixFold-Multistate Model:** A key enabler of this framework is a specialized AI structure prediction model, HelixFold-Multistate. The authors created this by fine-tuning existing deep learning models (based on AlphaFold-Multimer) specifically on GPCR-peptide structural data. This refinement improved the model's ability to accurately predict the binding pose of the peptide and, crucially, to distinguish between the subtle conformational differences of the GPCR's active and inactive states.

3.  **End-to-End Pipeline with Experimental Validation:** The paper establishes and validates a complete workflow from computational design to experimental verification. This pipeline involves: i) identifying diverse peptide backbones using tools like FoldSeek, ii) generating sequences using an inverse folding model, iii) filtering and ranking candidates with HelixFold-Multistate, and iv) performing wet-lab experiments to confirm the affinity and functional modality (agonist/antagonist activity) of the designed peptides. The success of this process for three different GPCRs (APJR, GLP-1R, GHSR) demonstrates its practical utility and robustness.

### 3. 10 Most Important Citations

1.  **Evans et al. 2021.** Protein complex prediction with alphafold-multimer.
    This paper introduces AlphaFold-Multimer, the foundational model for predicting protein complex structures, upon which the authors' HelixFold-Multistate model is directly based.

2.  **Heo et al. 2022.** Multi-state modeling of g-protein coupled receptors at experimental accuracy.
    This work introduced AlphaFold-Multistate, and the authors specifically adapted its state-specific modeling techniques to enable their model to differentiate between active and inactive GPCR conformations. [https://github.com/huhlim/alphafold-multistate](https://github.com/huhlim/alphafold-multistate)

3.  **Hsu et al. 2022.** Learning inverse folding from millions of predicted structures.
    This paper describes a powerful inverse folding model (ESM-IF) used by the authors in their pipeline to generate diverse peptide sequences that can adopt a desired structural backbone. [https://github.com/facebookresearch/esm](https://github.com/facebookresearch/esm)

4.  **Dauparas et al. 2022.** Robust deep learning-based protein sequence design using proteinmpnn.
    This paper presents ProteinMPNN, another key inverse folding model that the authors employed to generate candidate peptide sequences for a given structural template, particularly in the GHSR case study.

5.  **Jumper et al. 2021.** Highly accurate protein structure prediction with alphafold.
    This is the landmark paper for the original AlphaFold model, which revolutionized protein structure prediction and laid the groundwork for all subsequent models used in this study.

6.  **Pándy-Szekeres et al. 2023.** Gpcrdb in 2023: state-specific structure models using alphafold2 and new ligand resources.
    This citation refers to the GPCRdb, a critical database the authors used to source training, fine-tuning, and benchmarking data on GPCR-peptide complex structures and their activation states. [https://gpcrdb.org/](https://gpcrdb.org/)

7.  **Van Kempen et al. 2024.** Fast and accurate protein structure search with foldseek.
    This paper introduces FoldSeek, the structural alignment tool the authors used in the initial stage of their pipeline to search the Protein Data Bank for suitable peptide backbone scaffolds to seed the design process. [https://github.com/steineggerlab/foldseek](https://github.com/steineggerlab/foldseek)

8.  **Davenport et al. 2020.** Advances in therapeutic peptides targeting g protein-coupled receptors.
    This highly-cited review provides essential context on the therapeutic importance and challenges of designing peptide drugs for GPCRs, motivating the entire study.

9.  **Bryant et al. 2022.** Evobind: in silico directed evolution of peptide binders with alphafold.
    This is cited as a recent AI-based peptide design method, providing a point of comparison to highlight the novelty of the current paper's focus on state-specificity, which methods like EvoBind do not explicitly address.

10. **Watson et al. 2023.** De novo design of protein structure and function with rfdiffusion.
    This paper on RFdiffusion represents the state-of-the-art in generative protein design and is mentioned as an important related approach, situating the authors' work within the rapidly evolving field of computational protein engineering.
