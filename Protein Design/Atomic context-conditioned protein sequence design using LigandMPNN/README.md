https://www.biorxiv.org/content/10.1101/2023.12.22.573103v1

**Paper:** Dauparas, J., Lee, G. R., Pecoraro, R., An, L., Anishchenko, I., Glasscock, C., & Baker, D. (2025). Atomic context-conditioned protein sequence design using LigandMPNN. *Nature Methods*, *22*, 717–723.

### 1. Summary and Rating

**Summary**

This paper introduces LigandMPNN, a deep-learning method for protein sequence design that explicitly accounts for the atomic environment of nonprotein components such as small molecules (ligands), nucleotides, and metals. The method extends the architecture of its predecessor, ProteinMPNN, which could only model protein backbones. It does so by representing the complete biomolecular system as a series of graphs—a protein graph, a ligand graph, and a protein-ligand graph—and using message-passing neural networks to learn the complex interactions between them.

The authors perform a rigorous *in silico* evaluation, demonstrating that LigandMPNN significantly outperforms both the leading deep-learning model (ProteinMPNN) and the established physics-based method (Rosetta) in native sequence recovery for residues interacting with nonprotein molecules. The model not only designs sequences but also predicts sidechain conformations with higher accuracy than Rosetta. The paper's primary strength lies in its extensive experimental validation. LigandMPNN has been successfully applied to design over 100 small-molecule and DNA-binding proteins with high affinity, rescue binding in previously failed designs, and increase the affinity of existing binders by up to 100-fold. The high accuracy of the method is further corroborated by five X-ray crystal structures of designed proteins, which closely match the computational models.

**Rating: 9.5/10**

This paper represents a significant and highly impactful advancement in computational protein design. It directly addresses a critical limitation of previous state-of-the-art deep learning models by enabling the design of functional sites that interact with nonprotein entities, a cornerstone of enzyme and sensor engineering. The architectural generalization from ProteinMPNN is elegant and effective. The work is exceptionally rigorous, supported by strong comparative benchmarks and, most impressively, a wealth of experimental validation that proves its real-world utility and power. For a PhD-level audience, this paper is exemplary in its clear problem definition, robust methodology, and conclusive validation that bridges computational development with tangible biochemical success. The public release of the code further solidifies its value to the research community. It falls just shy of a perfect 10 only because it is an extension of an existing, albeit revolutionary, architecture (ProteinMPNN) rather than a completely new paradigm from the ground up.

### 2. Main Ideas

1.  **Generalizing Protein Design for Nonprotein Contexts:** The central idea is to extend the powerful graph-based representation of proteins, used in models like ProteinMPNN, to explicitly include nonprotein atoms. LigandMPNN constructs a multi-graph system that allows information to be passed not only between protein residues but also between residues and ligand atoms, and among ligand atoms themselves. This "atomic context" enables the model to design amino acid sequences that are chemically and sterically complementary to a specific ligand, nucleotide, or metal ion.

2.  **Superior Sequence and Sidechain Prediction for Functional Sites:** The paper establishes LigandMPNN as the new state-of-the-art for designing binding pockets. Through systematic benchmarks, it shows that LigandMPNN achieves substantially higher native sequence recovery rates in proximity to ligands compared to both ProteinMPNN and Rosetta. Furthermore, its ability to co-design sequence and predict sidechain torsion angles results in more accurate structural models of binding interactions, which is critical for pre-organizing the functional site for high-affinity binding.

3.  **A Proven and Practical Tool for Functional *De Novo* Protein Design:** Beyond *in silico* metrics, the paper powerfully demonstrates LigandMPNN as a transformative, practical tool. The authors report its successful use in designing and experimentally validating over 100 functional proteins with high affinities and structural accuracy. This includes rescuing previously non-functional designs and dramatically improving binding affinity, proving that the model generalizes beyond its training data to create novel proteins with desired functions.

### 3. 10 Most Important Citations

1.  **Dauparas et al. 2022.** Robust deep learning-based protein sequence design using ProteinMPNN.
    This is the foundational paper for ProteinMPNN, the model that LigandMPNN directly extends and generalizes to include nonprotein contexts.
    [https://doi.org/10.1126/science.add2187](https://doi.org/10.1126/science.add2187)

2.  **Jumper et al. 2021.** Highly accurate protein structure prediction with AlphaFold.
    This paper describes AlphaFold2, which revolutionized structure prediction and is a key component of the modern protein design pipeline for filtering and validating designed structures.
    [https://doi.org/10.1038/s41586-021-03819-2](https://doi.org/10.1038/s41586-021-03819-2)

3.  **Leman et al. 2020.** Macromolecular modeling and design in Rosetta: recent methods and frameworks.
    This citation represents the Rosetta software suite, the primary physics-based method against which LigandMPNN is benchmarked for sequence design and performance.
    [https://doi.org/10.1038/s41592-020-0848-2](https://doi.org/10.1038/s41592-020-0848-2)

4.  **Watson et al. 2023.** De novo design of protein structure and function with RFdiffusion.
    This paper introduces RFdiffusion, a state-of-the-art generative model for creating novel protein backbones, upon which LigandMPNN is subsequently used to design sequences for function.
    [https://doi.org/10.1038/s41586-023-06415-8](https://doi.org/10.1038/s41586-023-06415-8)

5.  **An et al. 2024.** Binding and sensing diverse small molecules using shape-complementary pseudocycles.
    This is a key application paper demonstrating LigandMPNN's power to successfully design nanomolar binders for a variety of small molecules, providing strong experimental validation.
    [https://doi.org/10.1126/science.adj8273](https://doi.org/10.1126/science.adj8273)

6.  **Krishna et al. 2024.** Generalized biomolecular modeling and design with RoseTTAFold All-Atom.
    This paper showcases the integration of LigandMPNN into a larger design framework (RoseTTAFold All-Atom) to model and design proteins in complex with small molecules, highlighting its utility as a module in broader applications.
    [https://doi.org/10.1126/science.adl2528](https://doi.org/10.1126/science.adl2528)

7.  **Glasscock et al. 2023.** Computational design of sequence-specific DNA-binding proteins.
    This preprint is cited as crucial evidence of LigandMPNN's ability to design protein-nucleic acid interfaces, validated by a crystal structure that confirms the design accuracy.
    [https://doi.org/10.1101/2023.09.20.558720](https://doi.org/10.1101/2023.09.20.558720)

8.  **Hsu et al. 2022.** Learning inverse folding from millions of predicted structures.
    This paper (describing ESM-IF, referred to as IF-ESM in the text) is cited as another contemporary deep learning-based sequence design method, providing context for the state-of-the-art in the field.
    [https://proceedings.mlr.press/v162/hsu22a.html](https://proceedings.mlr.press/v162/hsu22a.html)

9.  **Ingraham et al. 2019.** Generative models for graph-based protein design.
    This work is cited as a pioneering paper that introduced the use of graph neural networks for protein sequence design, laying the conceptual groundwork for methods like ProteinMPNN and LigandMPNN.
    [https://proceedings.neurips.cc/paper/2019/hash/1113d7a76ffceca1bbe3a3999995f08c-Abstract.html](https://proceedings.neurips.cc/paper/2019/hash/1113d7a76ffceca1bbe3a3999995f08c-Abstract.html)

10. **Lee et al. 2023.** Small-molecule binding and sensing with a designed protein family.
    This is another important application preprint that validates LigandMPNN's ability to design a family of proteins capable of binding and sensing various small molecules, showcasing its versatility.
    [https://doi.org/10.1101/2023.11.01.565201](https://doi.org/10.1101/2023.11.01.565201)
