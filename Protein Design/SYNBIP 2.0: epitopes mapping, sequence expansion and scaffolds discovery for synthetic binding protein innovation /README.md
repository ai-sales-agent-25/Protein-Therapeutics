https://academic.oup.com/nar/article/53/D1/D595/7824214

**SYNBIP 2.0: epitopes mapping, sequence expansion and scaffolds discovery for synthetic binding protein innovation**

### 1. Summary and Rating

This paper describes SYNBIP 2.0, a major update to the SYNBIP database of synthetic binding proteins (SBPs). The authors have significantly enhanced the database in three principal ways. First, they have mapped the binding epitopes for hundreds of SBP-target interactions by providing 899 experimentally-determined or computationally-modeled 3D complex structures, offering crucial insights for rational protein design. Second, leveraging the deep learning framework ProteinMPNN, they have expanded the known sequence space of SBPs five-fold, generating over 12,000 new sequences and providing predictions for their stability and solubility. Third, using the structure-search tool Foldseek, they performed a massive search across the PDB and AlphaFold databases, identifying over 16 million potential "SBP-like" scaffolds from thousands of organisms. The update also includes the addition of 153 new SBPs, updated 3D structures using AlphaFold2, and refreshed clinical status information. Overall, SYNBIP 2.0 is positioned as a comprehensive and indispensable resource to accelerate innovation in the design of SBPs for therapeutic, diagnostic, and research applications.

**Rating: 9/10**

This is an excellent database update paper that provides a substantial and timely contribution to the field of protein engineering and synthetic biology. The integration of state-of-the-art computational tools like AlphaFold2, ProteinMPNN, and Foldseek is executed thoughtfully and addresses key bottlenecks in SBP development—namely, understanding binding mechanisms, exploring novel sequence space, and discovering new structural scaffolds. The scale of the data expansion, particularly the discovery of millions of potential new scaffolds, is impressive and provides a rich resource for the research community. For a PhD-level audience, the paper clearly articulates its value by providing tools and data that directly enable new research avenues in rational and *de novo* protein design. It serves as a powerful example of how modern computational methods can be harnessed to create high-value biological resources.

### 2. Main Ideas

1.  **Structural Characterization of SBP-Target Epitopes:** A primary focus of the update is to provide atomistic details of how SBPs interact with their targets. By curating a dataset of 899 SBP-target complex structures (221 experimental, 678 computationally modeled), the database allows researchers to visualize and analyze the specific binding epitopes. This structural information is fundamental for understanding the mechanism of action and for guiding the rational design of new SBPs with enhanced affinity or specificity.

2.  **AI-Driven Sequence Space Expansion:** The paper moves beyond merely cataloging existing SBPs by using the deep learning model ProteinMPNN to computationally generate over 12,000 new SBP sequences based on existing structures. Critically, these novel sequences are annotated with predicted biophysical properties (solubility and stability), providing a pre-screened, high-quality library of candidates for experimental validation and broadening the available sequence diversity for known scaffolds.

3.  **Large-Scale Discovery of Novel SBP-like Scaffolds:** Addressing the limitation of the relatively small number of known SBP scaffolds, the authors used the fast structural-search tool Foldseek to mine the entire RCSB PDB and AlphaFold DB. This effort yielded a massive dataset of over 16 million proteins that are structurally similar to existing SBP scaffolds. This vast repository of potential new scaffolds from diverse organisms offers countless new starting points for protein engineering and humanization efforts.

### 3. 10 Most Important Citations

*The reference list in the provided paper does not consistently include hyperlinks for its citations. The following list is formatted as requested, noting where links are absent in the source material.*

1.  **Wang et al. 2022.** SYNBIP: synthetic binding proteins for research, diagnosis and therapy.
    This citation describes the original SYNBIP 1.0 database, which is the foundation upon which the current work in SYNBIP 2.0 is built.

2.  **Wang et al. 2022.** Scaffolding protein functional sites using deep learning.
    This paper introduces ProteinMPNN, the deep learning framework that was essential for the "sequence expansion" feature of the SYNBIP 2.0 update.

3.  **Jumper et al. 2021.** Highly accurate protein structure prediction with AlphaFold.
    This work describes AlphaFold2, the AI system used in this paper to update the 3D structures of all SBPs, ensuring the database contains the most accurate structural models available.

4.  **van Kempen et al. 2024.** Fast and accurate protein structure search with Foldseek.
    This citation introduces Foldseek, the key computational tool used to perform the large-scale structural similarity search that identified over 16 million new SBP-like scaffolds.

5.  **Varadi et al. 2022.** AlphaFold Protein Structure Database: massively expanding the structural coverage of protein-sequence space with high-accuracy models.
    This paper describes the AlphaFold Protein Structure Database, which served as a primary source of protein structures that were mined for the discovery of novel SBP-like scaffolds.

6.  **Burley et al. 2021.** RCSB Protein Data Bank: powerful new tools for exploring 3D structures of biological macromolecules for basic and applied research and education in fundamental biology, biomedicine, biotechnology, bioengineering and energy sciences.
    This citation describes the RCSB PDB, the central repository for experimental protein structures and a foundational data source for SBP structures and the scaffold discovery pipeline.

7.  **Cao et al. 2022.** Design of protein-binding proteins from the target structure alone.
    This reference is a landmark paper in *de novo* protein design, representing the type of advanced protein engineering research that the SYNBIP 2.0 database is explicitly designed to facilitate and support.

8.  **Hebditch et al. 2017.** Protein-Sol: a web tool for predicting protein solubility from sequence.
    This citation refers to the Protein-Sol tool, which was used to predict the solubility of the thousands of new SBP sequences generated by ProteinMPNN.

9.  **Guruprasad et al. 1990.** Correlation between stability of a protein and its dipeptide composition: a novel approach for predicting in vivo stability of a protein from its primary sequence.
    This is the seminal paper describing the Instability Index (II), a method used in this work to predict the stability of the computationally generated SBP variants.

10. **Adasme et al. 2021.** PLIP 2021: expanding the scope of the protein-ligand interaction profiler to DNA and RNA.
    This citation refers to the PLIP tool, which was used to perform the detailed analysis of interaction types (e.g., hydrogen bonds, hydrophobic contacts) within the 899 SBP-target complex structures.
