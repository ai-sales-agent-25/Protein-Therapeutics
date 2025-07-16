https://advanced.onlinelibrary.wiley.com/doi/10.1002/advs.202506240

https://x.com/chenru_duan/status/1945475363737588036

Harnessing Machine Learning to Enhance Transition State Search with Interatomic Potentials and Generative Models

### 1. Summary and Rating

This paper presents the first systematic and rigorous benchmarking framework for evaluating machine learning (ML) methods in transition state (TS) searches. The authors compare two main strategies: Machine Learning Interatomic Potentials (MLIPs), which aim to accurately model the potential energy surface, and generative models, which directly predict the TS geometry. Seven representative MLIPs (including foundation models like MACE and DPA-2, and equivariant GNNs like LEFTNet) and a state-of-the-art generative model, React-OT, are evaluated using a comprehensive end-to-end TS search workflow on the Transition1x dataset and a realistic γ-ketohydroperoxide (KHP) decomposition network.

The study reveals several key insights. First, pre-trained universal MLIPs often fail to reliably locate transition states without task-specific fine-tuning on reactive data. Second, traditional metrics like energy and force mean absolute errors (MAEs) are insufficient predictors of a model's success in the actual TS search workflow. The paper introduces more informative "implicit" metrics, such as success rate and intended rate, which better capture practical performance. Third, the generative model, React-OT, frequently outperforms its MLIP counterparts in generating high-quality initial TS guesses, highlighting the potential of generative approaches. Finally, the work demonstrates that for MLIPs, preserving physical constraints (i.e., using energy-derived forces) is critical, as direct-force prediction schemes can lead to inaccurate Hessians that severely degrade TS optimization performance. The paper concludes by advocating for hybrid methods and the development of models that can directly predict Hessians to further advance the field.

**Rating: 9/10**

This is an excellent and timely paper that addresses a critical need in the computational chemistry and machine learning communities. Its primary strength lies in establishing a rigorous, standardized, and open benchmark for a complex and important task. The analysis is thorough, moving beyond simplistic accuracy metrics (MAEs) to evaluate models on their practical utility in a multi-step scientific workflow. The insights regarding the limitations of foundation models, the disconnect between explicit and implicit metrics, and the critical importance of physically correct Hessians are valuable and actionable for researchers developing new ML methods for chemistry. The paper is well-structured, clearly written, and provides a strong foundation for future work in this rapidly evolving area.

### 2. Main Ideas Discussed

1.  **The Insufficiency of Standard Metrics and the Need for End-to-End Evaluation:** A central theme is that traditional ML metrics like Mean Absolute Error (MAE) on energies and forces are poor proxies for performance on the complex, multi-step task of transition state searching. The paper demonstrates that a model can have low force/energy error but still fail to locate the correct TS. To address this, it introduces and systematically evaluates task-specific, "implicit" metrics such as the **GSM success rate** (ability to generate a minimal energy pathway) and the **intended rate** (ability to find the correct, validated TS), arguing these better reflect a model's practical utility.

2.  **Comparative Strengths of MLIPs vs. Generative Models for TS Search:** The paper provides a head-to-head comparison of MLIPs and generative models. It finds that the generative model, **React-OT**, is more robust and effective at producing high-quality initial TS guesses that lead to successful DFT-level optimization, outperforming even the best fine-tuned MLIPs. Conversely, fine-tuned MLIPs like **LEFTNet** can be highly efficient for refining structures and calculating barriers but require significant task-specific training and can be less reliable. This suggests a promising future direction lies in hybrid workflows that leverage the strengths of both approaches: using generative models for robust TS guess generation and MLIPs for efficient refinement.

3.  **The Critical Role of Accurate Hessians in ML-driven TS Search:** The study systematically investigates different force-training schemes for MLIPs, comparing models where forces are derived from energy gradients ("autograd") versus models that predict forces directly. It shows that while direct-force models achieve lower force MAEs, they break the physical energy-force relationship, leading to highly inaccurate Hessians. Since Hessian information is crucial for guiding saddle point optimization, these models perform very poorly in locating intended transition states. This finding underscores that for reactivity modeling, simply minimizing force error is not enough; preserving correct physical constraints is essential for reliable performance.

### 3. 10 Most Important Citations

1.  **Duan et al. 2025.** *Accelerating transition state discovery with a generative model of reaction trajectories.* This paper introduces React-OT, the state-of-the-art generative model that serves as a primary benchmark and a top performer in this study for generating initial TS guesses.
    *   Link: https://doi.org/10.1038/s42256-024-00832-y (Note: The provided paper lists this as a 2025 publication in Nat. Mach. Intell., a link might be to a preprint or placeholder)

2.  **Du et al. 2023.** *LEFTNet: 3D-graph-based deep feature learning for advanced E(3)-equivariant interatomic potentials.* This citation describes LEFTNet, the equivariant GNN architecture that is identified as the best-performing MLIP after fine-tuning and is used for extensive comparisons.
    *   Link: Not provided in the paper.

3.  **Grambow et al. 2020.** *A public database of transition states on the potential energy surfaces of organic reactions.* This work presents the original dataset of graphically-enumerated reactions that, after re-computation, forms the basis of the Transition1x dataset used for training and validating the models in the paper.
    *   Link: https://doi.org/10.1038/s41597-020-0474-z

4.  **Zimmerman. 2013.** *A growing-string method for finding transition states: Application to isomerization and dissociation reactions.* This paper details the Growing String Method (GSM), the core physics-based algorithm used throughout the study's workflow to generate the initial reaction pathway and TS guess.
    *   Link: https://doi.org/10.1063/1.4816717

5.  **Batatia et al. 2022.** *MACE: Higher Order Equivariant Message Passing Neural Networks for Fast and Accurate Force Fields.* This introduces the MACE architecture, a prominent higher-order equivariant GNN that is one of the key foundation MLIPs benchmarked in the paper.
    *   Link: https://openreview.net/forum?id=YPpSngE-ZU

6.  **Zhang et al. 2024.** *DPA-2: Towards a universal large atomic model for molecular and material simulation.* This citation describes the DPA-2 model, a significant multi-task pre-trained foundation model that is evaluated for its transferability from non-reactive to reactive systems.
    *   Link: https://doi.org/10.1038/s41524-024-01443-x

7.  **Smith et al. 2017.** *ANI-1: an extensible neural network potential with DFT accuracy at force field computational cost.* This paper introduces the ANI model, representing an early and influential transferable potential based on local atomic environment descriptors, which is used as a baseline MLIP.
    *   Link: https://doi.org/10.1039/C6SC05720A

8.  **Zhao et al. 2022.** *Automated Reaction Network Exploration for Chemistry and Catalysis with the Reaction Program YARP.* This citation establishes the γ-ketohydroperoxide (KHP) decomposition reaction network and the YARP framework, which is used in the paper as a realistic, multi-step application to test the models' capabilities beyond single reactions.
    *   Link: https://doi.org/10.1002/anie.202210693

9.  **Schütt et al. 2021.** *Equivariant message passing for the prediction of tensorial properties and forces.* This introduces the influential PaiNN architecture, an equivariant GNN that helped pioneer methods for accurately and efficiently modeling atomic systems, setting the stage for many of the models tested.
    *   Link: Not provided in the paper, but found in PMLR: http://proceedings.mlr.press/v139/schutt21a.html

10. **Behler et al. 2007.** *Generalized Neural-Network Representation of High-Dimensional Potential-Energy Surfaces.* This is the seminal paper that introduced the foundational concept of modern high-dimensional neural network potentials (NNPs) based on atom-centered symmetry functions, which underpins the entire field of MLIPs.
    *   Link: https://doi.org/10.1103/PhysRevLett.98.146401
