https://openreview.net/forum?id=i1Zu9htCMh

**FEW-SHOT ACTIVE LEARNING FOR DE NOVO DUAL-TARGET PEPTIDE DESIGN WITH HIGH BIO-ACTIVITY**

### 1. Summary and Rating

This paper introduces ORIDTP, a novel few-shot active learning pipeline for designing highly bioactive peptides for both single and dual therapeutic targets. The framework integrates advanced computational methods—including a target-guided diffusion model for *de novo* peptide generation, a reinforcement learning model for affinity maturation, and a screening model—with iterative rounds of *in vitro* experimental validation. In each cycle, the system proposes peptide candidates, which are synthesized and tested in a wet lab. The resulting bioactivity data (EC50 values) is then fed back to refine the computational models for the next round of design.

The authors demonstrate the pipeline's efficacy through two compelling case studies. First, they design single-target peptides for the glucagon-like peptide-1 receptor (GLP-1R), achieving a final peptide with an EC50 of 8.1 pM, significantly outperforming the most potent known natural peptide (40.8 pM). Second, and more impressively, they tackle the complex challenge of designing dual-target agonists for both GLP-1R and the glucagon receptor (GCGR). After four iterative rounds, they successfully developed peptides that showed superior bioactivity against both targets simultaneously compared to their respective natural counterparts, with the best peptide achieving an EC50 of 8.2 pM for GLP-1R and 0.24 nM for GCGR.

**Rating: 9/10**

For a sophisticated audience, this paper represents a significant step forward. Its primary strength lies in the successful closure of the design-build-test-learn loop for a highly challenging problem: *de novo* dual-target peptide design. The integration of state-of-the-art generative models (diffusion) and optimization techniques (reinforcement learning) with real-world experimental feedback is executed effectively. The results are not merely incremental; outperforming potent natural ligands in a dual-target setting is a landmark achievement that clearly demonstrates the power of the methodology. While it is a workshop paper and thus concise on some of the finer architectural and training details, its demonstrated success on a problem of high therapeutic relevance makes it a standout piece of work.

### 2. Main Ideas

1.  **Closed-Loop Active Learning for Peptide Design:** The central idea is the ORIDTP pipeline, which creates a rapid, iterative cycle between *in silico* design and *in vitro* testing. Instead of relying on massive static datasets, this active learning approach uses small batches of high-quality experimental data (15 peptides per round) to continuously refine the generative and predictive models, efficiently steering the design process toward peptides with exceptionally high bioactivity.
2.  **Dual-Target Co-optimization:** The paper extends the design paradigm from a single optimization objective to a more complex, dual-target problem. It introduces a "dual-target oriented" approach for affinity maturation and candidate screening, which must simultaneously balance and improve bioactivity against two different receptors (GLP-1R and GCGR). This directly addresses a major challenge in developing therapeutics for complex diseases where modulating multiple pathways can yield synergistic effects.
3.  **State-of-the-Art Generative AI Integration:** The pipeline's success is underpinned by its sophisticated computational core, which combines multiple advanced AI techniques. It uses a target-guided diffusion model for generating novel peptide sequences, reinforcement learning for maturing their binding affinity, and a dedicated affinity model for screening top candidates, showcasing how these methods can be composed into a powerful workflow to solve real-world molecular design problems.

### 3. 10 Most Important Citations

1.  **Watson et al. 2023.** De novo design of protein structure and function with rfdiffusion.
    This paper is foundational for the generative component of ORIDTP, introducing a diffusion model (RFdiffusion) capable of generating novel protein structures, which the current work adapts for peptide design.
2.  **Wang et al. 2023.** Self-play reinforcement learning guides protein engineering.
    This citation is directly relevant to the affinity maturation step, as it demonstrates the use of reinforcement learning to iteratively improve protein function, a strategy employed by ORIDTP.
3.  **Jiang et al. 2024.** Rapid in silico directed evolution by a protein language model with evolvepro.
    This work serves as a key inspiration for ORIDTP by demonstrating a successful integration of computational generation with experimental feedback for developing mutated enzymes, validating the closed-loop approach.
4.  **Cao et al. 2022.** Design of protein-binding proteins from the target structure alone.
    This is cited as a recent advancement in *de novo* binder design, providing important context and foundational techniques that the ORIDTP pipeline builds upon.
5.  **Muttenthaler et al. 2021.** Trends in peptide drug discovery.
    This review outlines the challenges and opportunities in the field, establishing the significance and timeliness of the problem that ORIDTP aims to solve.
6.  **Campbell et al. 2023.** Gipr/glp-1r dual agonist therapies for diabetes and weight loss—chemistry, physiology, and clinical applications.
    This citation provides the crucial biological and clinical rationale for selecting GLP-1R and GCGR as dual targets, grounding the research in a therapeutically important application.
7.  **Zhang et al. 2018.** Structure of the glucagon receptor in complex with a glucagon analogue.
    This paper provides the essential atomic-level structural information for the GCGR target, which is critical for any structure-aware computational design and modeling effort.
8.  **Chen et al. 2024.** Design of target specific peptide inhibitors using generative deep learning and molecular dynamics simulations.
    Cited as a recent and related work, this paper highlights the state-of-the-art in using generative AI for peptide design, against which ORIDTP represents a further advancement, particularly with its active learning loop.
9.  **Zha et al. 2021.** Dual-targeting peptide-guided approach for precision delivery and cancer monitoring by using a safe upconversion nanoplatform.
    This paper is cited to establish the precedent and utility of dual-target peptides in addressing complex diseases, supporting the motivation for the authors' work.
10. **Liu et al. 2024.** Dual activation of gcgr/glp1r signaling ameliorates intestinal fibrosis via metabolic regulation of histone h3k9 lactylation in epithelial cells.
    This recent paper further validates the therapeutic potential of dual GLP-1R/GCGR activation, reinforcing the importance of the biological problem chosen by the authors.
