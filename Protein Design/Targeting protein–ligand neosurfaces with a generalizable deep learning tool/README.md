https://www.nature.com/articles/s41586-024-08435-4

**Targeting protein–ligand neosurfaces with a generalizable deep learning tool**

### 1. Summary and Rating

This paper presents a novel computational framework, MaSIF-neosurf, for the *de novo* design of proteins that bind specifically to "neosurfaces"—the hybrid molecular surfaces formed by a protein in complex with a small-molecule ligand. The authors leverage a geometric deep learning approach, originally developed for protein-protein interactions (PPIs), and demonstrate its remarkable generalizability to this more complex design challenge without requiring retraining. The core innovation is to represent the protein-ligand pair as a single entity and use learned surface fingerprints to identify complementary binding motifs from a large structural database.

The authors experimentally validate their approach by successfully designing, from scratch, binders for three distinct and therapeutically relevant protein-ligand complexes: Bcl2-venetoclax, the antibody DB3-progesterone, and PDF1-actinonin. The designed proteins exhibit strict ligand-dependent binding with high specificity and affinities that, after computational and experimental optimization, reach the low nanomolar range. The accuracy of the design process is rigorously confirmed through X-ray crystallography and cryo-EM, which show that the solved structures of the designed complexes are in excellent agreement with the computational models.

Finally, the paper showcases the immense practical utility of these designed chemically induced dimerization (CID) systems by engineering them into functional ON-switches for a variety of synthetic biology applications. These include cell-free reporters, cytoplasmic and membrane-bound biosensors, and, most impressively, a split CAR-T cell system where T-cell-mediated tumor killing is inducibly controlled by the FDA-approved drug venetoclax.

**Rating: 9.5/10**

This paper is a landmark achievement in computational protein design. It tackles an exceptionally difficult problem—the rational design of binders to neosurfaces—with a powerful and generalizable method. The level of rigor is outstanding, seamlessly integrating state-of-the-art deep learning, extensive experimental validation, high-resolution structural biology, and functional implementation in therapeutically relevant systems. For a PhD-level audience, this work stands out for its technical novelty, the significance of its contribution to designing controllable biologics and molecular glues, and its near-flawless execution from computational concept to functional proof-of-principle.

### 2. Main Ideas

1.  **Generalization of Geometric Deep Learning for Neosurface Recognition:** The central concept is that a geometric deep learning model (MaSIF), trained on the geometric and chemical features of protein-protein interfaces, can be directly applied to design binders for protein-ligand neosurfaces without retraining. This is accomplished by treating the small molecule as an integral part of the target surface, featurizing its properties, and using the learned model of molecular complementarity to find matching protein fragments. This demonstrates that the model learned fundamental principles of surface recognition that are generalizable beyond its original training data.

2.  **A Robust Pipeline for De Novo Design of Chemically-Induced Dimerizers (CIDs):** The paper establishes a complete pipeline that proceeds from *in silico* design to experimentally and structurally validated CIDs. It uses MaSIF-neosurf to identify binding motifs ("seeds"), grafts them onto stable protein scaffolds, and uses Rosetta for refinement. This process successfully yielded novel protein binders that function as highly specific, ligand-gated ON-switches, whose binding is strictly dependent on the presence of the target small molecule. The high-resolution structural validation of the designs confirms the accuracy and power of the computational pipeline.

3.  **Engineering Designed CIDs into Functional Synthetic Biology Modules:** A key contribution is the demonstration of the practical utility of the designed binders. The authors successfully repurposed their CID systems to function as controllable modules in various contexts, including cell-free sensors, cell-based reporters (split-luciferase), and membrane-bound signaling systems (GEMS). Most significantly, they engineered a split CAR-T system that enables small-molecule control over T-cell activity, showcasing a direct path towards creating safer, more controllable cell-based therapies.

### 3. 10 Most Important Citations

1.  **Gainza et al.** (2020) Deciphering interaction fingerprints from protein molecular surfaces using geometric deep learning.
    This is the original MaSIF paper, which introduced the foundational geometric deep learning framework for analyzing and predicting protein interactions that this work extends.

2.  **Gainza et al.** (2023) De novo design of protein interactions with learned surface fingerprints.
    This paper introduced the MaSIF-seed design pipeline for standard PPIs, which the current work adapts and applies to the more challenging task of targeting neosurfaces.

3.  **Krishna et al.** (2024) Generalized biomolecular modeling and design with RoseTTAFold All-Atom.
    This paper describes a state-of-the-art deep learning tool for biomolecular modeling that was used as a key benchmark to demonstrate the superior performance of MaSIF-neosurf for predicting neosurface interactions.
    Link: https://doi.org/10.1126/science.adl2528

4.  **Jumper et al.** (2021) Highly accurate protein structure prediction with AlphaFold.
    The authors use AlphaFold2 to assess the quality of their computational designs and suggest that incorporating it as a filter could significantly improve the experimental success rate of their pipeline.

5.  **Dauparas et al.** (2023) Atomic context-conditioned protein sequence design using LigandMPNN.
    This citation introduces LigandMPNN, a novel sequence design tool that the authors use to demonstrate a path to dramatically improving their design success rate, highlighting a promising synergy with their surface-centric approach.
    Link: https://doi.org/10.1101/2023.12.22.573103

6.  **Schreiber, S. L.** (2021) The rise of molecular glues.
    This review article provides the broader scientific context for the work, highlighting the importance and challenge of creating molecules that induce protein interactions, a field to which this paper makes a significant contribution.

7.  **Spencer et al.** (1993) Controlling signal transduction with synthetic ligands.
    This is a classic paper that established the concept of chemically induced dimerization (CID) using experimental methods, representing the foundational work that computational approaches like MaSIF-neosurf aim to advance.

8.  **Fleishman et al.** (2011) RosettaScripts: a scripting language interface to the Rosetta macromolecular modeling suite.
    Rosetta is an essential component of the design pipeline used for refining binding motifs and grafting them onto new scaffolds, making this citation fundamental to the computational methodology.
    Link: https://doi.org/10.1371/journal.pone.0020161

9.  **Giordano-Attianese et al.** (2020) A computationally designed chimeric antigen receptor provides a small-molecule safety switch for T-cell therapy.
    This work serves as a key precedent, demonstrating the utility of computational design to create small-molecule-controlled switches for therapeutic applications like CAR-T, a goal directly realized in the current paper.

10. **Scheller et al.** (2018) Generalized extracellular molecule sensor platform for programming cellular behavior.
    The GEMS system described in this paper was one of the specific cellular platforms the authors successfully adapted to functionally validate their designed CID system, demonstrating its modularity and applicability.
