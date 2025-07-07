https://arxiv.org/abs/2409.08022

*De novo* design of high-affinity protein binders with AlphaProteo

### 1. Summary and Rating

This technical report from Google DeepMind introduces AlphaProteo, a machine learning system for the *de novo* design of high-affinity protein binders. The system comprises a generative model that produces binder candidates for a given protein target and a filtering model that predicts experimental success. The authors demonstrate its performance by designing and experimentally validating binders against eight structurally diverse and therapeutically relevant targets. For seven of these targets, AlphaProteo achieved significantly higher experimental success rates (9-88%) and binding affinities (3- to 300-fold better) compared to the best existing computational methods, including RFdiffusion. Notably, the system produced binders with picomolar to low-nanomolar affinities after only a single round of medium-throughput screening (testing <200 designs per target), without requiring any subsequent experimental affinity maturation. The functional relevance of these binders was confirmed through cell-based assays, demonstrating inhibition of VEGF signaling and neutralization of live SARS-CoV-2 variants. Finally, cryo-EM and X-ray crystallography confirmed that the designed binders fold correctly and bind their targets in the computationally predicted mode, validating the structural accuracy of the method.

**Rating: 9/10**

The paper presents a significant advancement in computational protein design. The ability to generate picomolar-affinity binders for a wide range of targets with high success rates from a single computational campaign and medium-throughput screen is a state-of-the-art result that pushes the boundaries of the field. The experimental validation is exceptionally rigorous, including direct comparisons to other methods, functional cell-based assays, and high-resolution structural verification. The results suggest that *de novo* design could become a more routine, accessible, and rapid tool for developing research reagents and therapeutic leads. The rating is docked one point because the paper, as a "technical report," omits all details of the machine learning architecture and training, which prevents the academic community from understanding, reproducing, or building upon the core methodology. However, the strength and potential impact of the demonstrated experimental results are undeniable.

### 2. Main Ideas

1.  **High-Affinity Binders Without Experimental Optimization:** The central achievement of AlphaProteo is its ability to generate protein binders with very high (picomolar to low-nanomolar) affinity "off the shelf." Unlike previous methods that often yield binders with micromolar affinity that require multiple, labor-intensive rounds of directed evolution to improve, AlphaProteo's designs are potent after a single round of screening. This is demonstrated across seven diverse targets, with the designed binders consistently showing better affinity than the unoptimized outputs of other state-of-the-art methods.

2.  **High Experimental Success Rate from Medium-Throughput Screening:** AlphaProteo achieves remarkably high "hit rates" (the percentage of tested designs that successfully bind the target) ranging from 9% to 88%. This efficiency means that potent binders can be identified by testing a relatively small number of candidates (e.g., a single 96-well plate). This is enabled by a two-component system: a generative model that creates a large pool of potential binders, followed by a filter that accurately predicts which designs are most likely to succeed, dramatically reducing the experimental search space.

3.  **Demonstrated Functional Activity and Structural Accuracy:** The paper goes beyond simply measuring binding and shows that the designed proteins are functional and structurally accurate. Binders designed against VEGF-A successfully inhibited its downstream signaling pathway in human cells, and binders targeting the SARS-CoV-2 spike protein neutralized live virus in cell culture. Furthermore, cryo-EM and X-ray crystallography of several binder-target complexes confirmed that the proteins folded and interacted precisely as predicted by the computational model, providing strong validation of the method's underlying physical and geometric accuracy.

### 3. 10 Most Important Citations

1.  Watson et al. 2023. De novo design of protein structure and function with RFdiffusion. This paper introduces RFdiffusion, the primary state-of-the-art method to which AlphaProteo is compared throughout the report to benchmark its superior performance in success rate and affinity. (https://doi.org/10.1038/s41586-023-06415-8)

2.  Jumper et al. 2021. Highly accurate protein structure prediction with AlphaFold. This foundational paper on AlphaFold2 revolutionized protein structure prediction and provides the technological underpinning for the new generation of protein design models, including AlphaProteo. (https://doi.org/10.1038/s41586-021-03819-2)

3.  Abramson et al. 2024. Accurate structure prediction of biomolecular interactions with AlphaFold 3. This paper introduces AlphaFold 3, which the authors used to develop an *in silico* benchmark to guide the iterative development and evaluation of AlphaProteo. (https://doi.org/10.1038/s41586-024-07487-w)

4.  Cao et al. 2022. Design of protein-binding proteins from the target structure alone. This work is a key benchmark for *de novo* binder design without a known template and is used as a point of comparison for several targets like IL-7RA and TrkA. (https://doi.org/10.1038/s41586-022-04654-9)

5.  Gainza et al. 2023. De novo design of protein interactions with learned surface fingerprints. This paper presents another leading computational design method that AlphaProteo is compared against, particularly for the design of a binder to the challenging target PD-L1. (https://doi.org/10.1038/s41586-023-05993-x)

6.  Cao et al. 2020. De novo design of picomolar SARS-CoV-2 miniprotein inhibitors. This study was a landmark demonstration of rapidly designing high-affinity binders and serves as the primary performance benchmark for the SARS-CoV-2 binders created by AlphaProteo. (https://doi.org/10.1126/science.abd9909)

7.  Dauparas et al. 2022. Robust deep learning-based protein sequence design using ProteinMPNN. This paper describes ProteinMPNN, a powerful sequence design tool that is a critical component in many modern protein generation pipelines, likely including or related to the methods used in AlphaProteo. (https://doi.org/10.1126/science.add2187)

8.  Ingraham et al. 2023. Illuminating protein space with a programmable generative model. This work introduces a powerful generative model for protein backbones and sequences, representing a key advance in the generative AI space that AlphaProteo operates in. (https://doi.org/10.1038/s41586-023-06728-8)

9.  Berger et al. 2024. Preclinical proof of principle for orally delivered TH17 antagonist miniproteins. This citation provides a very recent and relevant benchmark for the difficult target IL-17A, demonstrating the poor unoptimized affinities of prior methods which highlights AlphaProteo's improvement. (https://doi.org/10.1016/j.cell.2024.05.052)

10. Baek et al. 2021. Accurate prediction of protein structures and interactions using a three-track neural network. This paper introduced RoseTTAFold, which alongside AlphaFold2, established deep learning as the dominant paradigm for protein structure prediction and laid the groundwork for complex design tasks. (https://doi.org/10.1126/science.abj8754)
