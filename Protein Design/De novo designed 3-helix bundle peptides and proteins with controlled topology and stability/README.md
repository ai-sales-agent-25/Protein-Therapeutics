https://www.biorxiv.org/content/10.1101/2025.06.30.662276v1

*De novo* designed 3-helix bundle peptides and proteins with controlled topology and stability

### 1. Summary and Rating

This paper presents a robust and elegant methodology for the *de novo* design of three-helix bundle (3HB) proteins with precise control over their topology and thermodynamic stability. The authors employ a powerful hybrid approach that begins with rational design principles, gleaned from analyzing known protein structures, to create sequences for heterotrimeric coiled-coil peptide assemblies (an acidic 'A', a basic 'B', and a neutral 'N' helix). By strategically placing charged residues and a buried polar network, they successfully designed for both clockwise (CW) and anticlockwise (ACW) topologies of an 'up-down-up' 3HB.

These peptide assemblies were modeled using AlphaFold2, and these models were then used as "seeds" for the computational design of single-chain proteins, where the helices are connected by optimized loops. The resulting single-chain proteins were expressed, purified, and shown to be stable, monomeric, and correctly folded, as confirmed by high-resolution X-ray crystal structures that matched the design models with sub-angstrom accuracy. Finally, the authors demonstrated that the hyperstability common in *de novo* proteins can be systematically tuned by incrementally substituting layers of the hydrophobic core with polar residues. This allowed them to create a variant with a reversible thermal unfolding transition, enabling a detailed thermodynamic analysis that revealed its stability parameters are comparable to those of natural proteins.

**Rating: 9/10**

This is an excellent paper that exemplifies a state-of-the-art protein design pipeline. It masterfully integrates first principles of protein structure, modern AI-driven modeling, and rigorous biophysical and structural validation. The achievement of controlling not only the overall fold but also the subtle topological handedness (CW vs. ACW) is a significant accomplishment. Furthermore, the systematic tuning of stability and the subsequent detailed thermodynamic characterization provide a much-needed bridge between the design of hyper-stable scaffolds and the more nuanced stability profiles required for functional proteins. The work serves as a strong case study for achieving "programmable" protein design, where structural and biophysical properties can be specified in advance.

### 2. Main Ideas

1.  **A Hybrid Pipeline for Designing with Topological Control:** The paper's core methodological advance is its successful integration of rational design with modern computational tools. They began by deriving sequence-to-structure rules from the PDB to design peptide helices (A, B, N) with specific electrostatic and packing features intended to favor a heterotrimeric assembly. This rational design was then used to create models with AlphaFold2, which in turn served as templates for designing single-chain proteins with computationally optimized loops. This multi-stage process proved highly effective, allowing them to precisely control the topology (handedness) of the final 3-helix bundle, a sophisticated structural feature.

2.  **Peptide Assemblies as "Seeds" for Single-Chain Protein Design:** A key concept demonstrated is the use of well-defined, self-assembling peptide systems as structural scaffolds or "seeds" for building larger, single-chain proteins. By first validating the heterotrimeric peptide assembly, they established a robust structural core. Computationally stitching these validated helical segments together with loops is a powerful and efficient strategy for creating stable, monomeric proteins with predictable structures.

3.  **Systematic Tuning of Protein Stability via Core Engineering:** The paper addresses the common issue of hyperstability in *de novo* proteins, which can be a barrier to function. The authors show that stability can be rationally and predictably attenuated by systematically replacing hydrophobic (Leucine) layers in the protein's core with polar (Asparagine/Threonine) layers. This allowed them to design a series of proteins with a wide range of stabilities, including one that unfolds cooperatively and reversibly, enabling a full thermodynamic characterization that is rare for *de novo* proteins but essential for understanding the forces governing folding.

### 3. 10 Most Important Citations

1.  **Huang et al. 2016.** The coming of age of de novo protein design.
    This highly cited review from the Baker lab outlines the state of the field and its future potential, providing the broad context of achievement into which this paper fits.

2.  **Watson et al. 2023.** De novo design of protein structure and function with RFdiffusion.
    This paper introduces a key generative AI method for protein backbone design, which is referenced in the introduction as representing the current state-of-the-art in AI-driven design that the authors' more rational approach complements.

3.  **Woolfson, D. N. 2023.** Understanding a protein fold: The physics, chemistry, and biology of a-helical coiled coils.
    This review by the paper's corresponding author details the design principles of coiled coils, the fundamental structural motif that forms the basis of all the designs in this work.

4.  **Boyken et al. 2016.** De novo design of protein homo-oligomers with modular hydrogen-bond network-mediated specificity.
    This paper is cited for its pioneering work in using buried polar hydrogen-bond networks to control protein-protein interaction specificity, a key design principle the authors use to specify their antiparallel heterotrimer.

5.  **Naudin et al. 2022.** From peptides to proteins: coiled-coil tetramers to single-chain 4-helix bundles.
    This is the authors' own previous work that established the "peptide seeding" concept for designing single-chain proteins, which they apply and expand upon here for 3-helix bundles.

6.  **Bryson et al. 1998.** From coiled coils to small globular proteins: Design of a native-like three-helix bundle.
    This is a classic paper from the DeGrado lab on the foundational design of a 3HB, establishing many of the core principles for designing this specific fold.

7.  **Lombardi et al. 1996.** De novo design of heterotrimeric coiled coils.
    This foundational paper from the DeGrado lab is a key precedent for the design of the ABN heterotrimeric peptide system presented in the manuscript.

8.  **Nautiyal et al. 1995.** A Designed Heterotrimeric Coiled Coil.
    This work from the Alber lab is another foundational paper on using electrostatic interactions at the helix-helix interface to guide the formation of a specific heterotrimer over homooligomers.

9.  **Bermeo et al. 2022.** De novo design of obligate ABC-type heterotrimeric proteins.
    This very recent paper on designing obligate ABC heterotrimers is cited to highlight the state-of-the-art in a closely related design challenge, providing context for the current paper's contribution.

10. **Rocklin et al. 2017.** Global analysis of protein folding using massively parallel design, synthesis, and testing.
    This landmark paper demonstrates the power of high-throughput methods to quantitatively map sequence-stability landscapes, representing the broader quest for a "fully programmable" design paradigm that this paper's detailed thermodynamic analysis contributes to.
