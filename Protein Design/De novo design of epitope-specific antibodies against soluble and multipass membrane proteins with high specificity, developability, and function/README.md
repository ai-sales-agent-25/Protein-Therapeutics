https://www.biorxiv.org/content/10.1101/2025.01.21.633066v1

De novo design of epitope-specific antibodies against soluble and multipass membrane proteins with high specificity, developability, and function

### 1. Summary and Rating

**Summary:**
This paper introduces JAM (Joint Atomic Modeling), a generative AI system for the fully computational, *de novo* design of therapeutic antibodies. The authors demonstrate that JAM can generate antibodies in both single-domain (VHH) and paired (scFv/mAb) formats that exhibit therapeutic-grade properties—such as double-digit nanomolar affinities, high specificity, and favorable developability profiles—without requiring any experimental optimization or affinity maturation. A key achievement is the successful design of the first fully computational antibodies against challenging multipass membrane proteins (Claudin-4 and CXCR7), a class of targets that has been historically difficult to address. The paper also presents a novel methodological insight by showing that applying iterative introspection, a concept from large language models, significantly improves design success rates and affinities, suggesting that test-time compute scaling is a viable strategy for physical protein design. The entire workflow from computational design to characterization is reported to be under six weeks.

**Rating: 8/10**

For a sophisticated, PhD-level audience, this paper presents potentially transformative results. The ability to computationally design high-affinity, developable, and epitope-specific antibodies, particularly against intractable targets like GPCRs and other multipass membrane proteins, would represent a paradigm shift in therapeutic discovery. The breadth of experimental validation across multiple targets and formats is impressive, and the novel application of "iterative introspection" from machine learning to protein design is a significant conceptual contribution.

The rating is not a perfect 10 primarily because of the major caveat stated in the disclaimer: the methodological details of the JAM system are completely withheld for commercial reasons. This lack of transparency makes the work non-reproducible and prevents a full scientific assessment of the underlying model, positioning the paper more as a technology demonstration than a complete scientific publication. While the results are spectacular, the "black box" nature of the core method is a significant drawback for a scientific audience that values verifiability and the ability to build upon new methods.

### 2. Main Ideas

1.  **Fully Computational Design of Therapeutic-Grade Antibodies:** The central idea is that the JAM system enables *de novo* antibody design that is purely computational, generating binders with high affinity, function (e.g., viral neutralization), and good "developability" metrics (e.g., production yield, monomericity, low polyspecificity) from the outset. This aims to bypass the need for traditional, labor-intensive experimental screening and subsequent optimization cycles like affinity maturation.

2.  **Unlocking Intractable and Novel Drug Targets:** A major theme is the application of JAM to historically difficult drug targets. The paper highlights the first-ever successful computational design of antibodies against multipass membrane proteins (MPMPs) Claudin-4 and CXCR7. This was enabled by a dual-capability of JAM: designing not only the antibody but also a soluble, well-behaved "proxy" of the membrane protein to facilitate high-throughput experimental screening.

3.  **Improving Design Success Through Iterative Introspection:** The paper introduces a concept from large language models to protein design, showing that increasing "test-time computation" improves results. By allowing JAM to iteratively use its own generated antibody-target structures as inputs for subsequent design rounds (a process they call introspection), the system produces a higher rate of binding candidates and achieves higher affinities, demonstrating a novel scaling law for computational protein design.

### 3. 10 Most Important Citations

1.  Watson et al. 2023. De novo design of protein structure and function with RFdiffusion.
    This paper describes the state-of-the-art diffusion model for general protein design, providing a key benchmark and point of comparison for the capabilities of JAM.

2.  Bennett et al. 2024. Atomically accurate de novo design of single-domain antibodies.
    This is cited as a contemporary approach to *de novo* antibody design, highlighting the current progress and challenges in the field that JAM aims to overcome.
    Link: [https://doi.org/10.1101/2024.03.14.585103](https://doi.org/10.1101/2024.03.14.585103)

3.  Jain et al. 2017. Biophysical properties of the clinical-stage antibody landscape.
    This work provides the essential benchmarks for "developability" (e.g., polyspecificity, production) against which the JAM-designed antibodies are compared throughout the paper, using approved mAbs like Trastuzumab as a reference.

4.  Hutchings et al. 2020. Mini-review: antibody therapeutics targeting G protein-coupled receptors and ion channels.
    This review establishes the context and immense therapeutic challenge of targeting multipass membrane proteins, underscoring the significance of JAM's reported success in this area.

5.  Walls et al. 2020. Structure, Function, and Antigenicity of the SARS-CoV-2 Spike Glycoprotein.
    This citation provides the biological rationale for targeting the SARS-CoV-2 RBD-ACE2 interface, which serves as the primary and most deeply characterized use case for validating JAM's performance.

6.  McMahon et al. 2018. Yeast surface display platform for rapid discovery of conformationally selective nanobodies.
    This paper describes the state-of-the-art naive VHH library and screening method that was used as a negative control, demonstrating that JAM's designed library successfully identified binders where a large empirical library failed.

7.  Qu et al. 2024. Recursive IntroSpEction: Teaching language model agents how to self-improve.
    This citation is the direct methodological inspiration for the "iterative introspection" process, showcasing a novel transfer of ideas from LLM agent improvement to computational protein design.
    Link: [https://arxiv.org/abs/2405.15839](https://arxiv.org/abs/2405.15839)

8.  Raybould et al. 2020. Thera-SAbDab: the Therapeutic Structural Antibody Database.
    This database was used to benchmark the "humanness" of JAM's designs by comparing their sequence identity to known clinical-stage antibodies, a critical metric for assessing immunogenicity risk.
    Link: [https://doi.org/10.1093/nar/gkz827](https://doi.org/10.1093/nar/gkz827)

9.  Carter et al. 2022. Designing antibodies as therapeutics.
    This review outlines the aspirational goals of the antibody engineering field, such as achieving atomic-level control over binding, providing a high-level framing for the importance of the advances claimed in the paper.

10. Lyu et al. 2022. The global landscape of approved antibody therapies.
    Cited in the introduction, this paper establishes the clinical and commercial importance of antibody therapeutics, motivating the need for more efficient and powerful discovery platforms like JAM.
