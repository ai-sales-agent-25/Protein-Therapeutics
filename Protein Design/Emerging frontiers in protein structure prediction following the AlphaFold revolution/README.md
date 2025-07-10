https://royalsocietypublishing.org/doi/full/10.1098/rsif.2024.0886

Emerging frontiers in protein structure prediction following the AlphaFold revolution

### 1. Summary and Rating

This review provides a comprehensive overview of the transformative impact of AlphaFold on structural biology. The authors begin by tracing the history of protein structure prediction, highlighting the foundational role of co-evolutionary analysis and deep learning, which culminated in the "AlphaFold revolution." The paper discusses the profound implications of this breakthrough, including the generation of vast public structure databases and the development of accessible tools like ColabFold. A significant portion is dedicated to explaining the critical importance of confidence metrics (pLDDT, PAE, pTM) for interpreting predictions and provides practical guidelines for reporting results in scientific literature. The core of the review then shifts to the "emerging frontiers" beyond static monomer prediction. These include predicting protein conformational changes, protein-protein interactions (PPIs), and interactions with non-protein entities like nucleic acids and small molecules using newer tools like AlphaFold3. The authors expertly frame the difficulty of these new frontiers by comparing the available co-evolutionary information against the geometric and chemical complexity of the target systems. The paper concludes that while the challenge of predicting protein-only structures is maturing rapidly, the general prediction of complex biomolecular interactions and the experimental validation of the flood of new predictions represent the next major bottlenecks and areas for future research.

**Rating: 9/10**

This is an excellent and timely review. It is well-structured, clearly written, and provides a sophisticated synthesis of the current state of the field. For a PhD-level audience, it serves as a superb summary of recent history, a guide to current best practices, and a forward-looking perspective on the key challenges and opportunities. The conceptual framework comparing evolutionary information to geometric complexity is particularly insightful for contextualizing the difficulty of various prediction tasks. The paper is comprehensive without being overly technical, making it valuable both for specialists in the field and for researchers in adjacent disciplines seeking to understand and apply these revolutionary tools.

### 2. Main Ideas

1.  **The frontier of computational structural biology has shifted from predicting static protein monomers to modeling dynamic and interactive molecular systems.** The paper argues that AlphaFold has largely solved the problem of predicting the fold of a single protein chain. The new, more complex challenges ("emerging frontiers") now involve predicting multiple functional conformations of a single protein, modeling large-scale protein-protein interaction networks, and, most recently, predicting interactions with other classes of biomolecules like nucleic acids and small-molecule ligands.
2.  **The accuracy and applicability of prediction methods are fundamentally tied to the availability of co-evolutionary information and the chemical complexity of the target.** The paper explains that the remarkable success of AlphaFold for proteins and PPIs relies on strong, "two-sided" co-evolutionary signals derived from multiple sequence alignments (MSAs). However, as prediction tasks move toward protein-nucleic acid or protein-ligand interactions, this signal becomes "one-sided" or non-existent, while the geometric and chemical complexity of the system drastically increases, making these problems inherently harder to solve.
3.  **The "AlphaFold revolution" has created a new bottleneck in experimental validation, necessitating rigorous, standardized assessment of predicted models.** The authors emphasize that the massive output of new structural models is not an end in itself. They dedicate significant space to explaining confidence metrics (pLDDT, PAE) and providing explicit guidelines for publishing predicted structures. This underscores a critical shift in the field, where the primary challenge is no longer the scarcity of structural information but the careful interpretation, prioritization, and experimental validation of an abundance of computational predictions.

### 3. Top 10 Most Important Citations

1.  **Jumper et al. 2021** Highly accurate protein structure prediction with alphafold.
    This is the seminal paper from DeepMind that introduced AlphaFold2 and demonstrated its revolutionary, near-experimental accuracy in protein structure prediction.
    https://doi.org/10.1038/s41586-021-03819-2

2.  **Evans et al. 2022** Protein complex prediction with AlphaFold-Multimer.
    This paper describes the extension of AlphaFold to predict the structures of protein-protein interactions, representing the first major frontier beyond monomer prediction discussed in the review.
    https://doi.org/10.1101/2021.10.04.463034

3.  **Abramson et al. 2024** Accurate structure prediction of biomolecular interactions with AlphaFold 3.
    This citation introduces AlphaFold3, the next generation of the tool, which expands prediction capabilities to include nucleic acids, small molecules, and post-translational modifications, a key "emerging frontier."
    https://doi.org/10.1038/s41586-024-07487-w

4.  **Marks et al. 2011** Protein 3D structure computed from evolutionary sequence variation.
    This is a foundational paper demonstrating that direct coupling analysis of co-evolving residues in multiple sequence alignments could be used to accurately determine residue-residue contacts and protein 3D structure.
    https://doi.org/10.1371/journal.pone.0028766

5.  **Baek et al. 2021** Accurate prediction of protein structures and interactions using a three-track neural network.
    This paper introduced RoseTTAFold, which achieved accuracy approaching AlphaFold2 and was developed concurrently, confirming that deep learning applied to co-evolutionary and structural information was a broadly successful strategy.
    https://doi.org/10.1126/science.abj8754

6.  **Lin et al. 2023** Evolutionary-scale prediction of atomic-level protein structure with a language model.
    This citation describes ESMFold, a powerful protein language model that can predict structures from a single sequence without requiring an explicit MSA, representing the primary alternative approach to AlphaFold.
    https://doi.org/10.1126/science.ade2574

7.  **Varadi et al. 2024** AlphaFold protein structure database in 2024: providing structure coverage for over 214 million protein sequences.
    This paper describes the AlphaFold Database, which made millions of high-quality predictions freely available and is a cornerstone of the revolution's impact on the biological sciences.
    https://doi.org/10.1093/nar/gkad1011

8.  **Mirdita et al. 2022** ColabFold: making protein folding accessible to all.
    This publication is cited for the development of ColabFold, a tool that massively increased the accessibility of AlphaFold2 to the wider research community by simplifying the pipeline and providing access to necessary GPU resources.
    https://doi.org/10.1038/s41592-022-01488-1

9.  **Watson et al. 2023** De novo design of protein structure and function with RFdiffusion.
    This paper is a key example of the application of deep learning to another frontier: the computational design of novel protein binders, which is highlighted in the review as a major future application.
    https://doi.org/10.1038/s41586-023-06415-8

10. **Moult et al. 1995** A large-scale experiment to assess protein structure prediction methods.
    This citation marks the establishment of the Critical Assessment of Methods of Protein Structure Prediction (CASP) experiment, which the review identifies as a crucial, long-running framework for rigorously and blindly benchmarking the progress of the field.
    https://doi.org/10.1002/prot.340230303
