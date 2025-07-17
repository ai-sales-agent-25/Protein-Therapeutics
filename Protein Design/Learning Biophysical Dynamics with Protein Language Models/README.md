https://www.biorxiv.org/content/10.1101/2024.10.11.617911v4

Learning Biophysical Dynamics with Protein Language Models

### 1. Summary and Rating

This paper introduces SeqDance and ESMDance, two protein language models (pLMs) designed to overcome the limitations of existing models that rely primarily on evolutionary or static structural information. The authors argue that such data fails to capture the dynamic nature of proteins, which is crucial for their function, especially for intrinsically disordered regions (IDRs), designed proteins, and rapidly evolving viral proteins. To address this, they curate a large dataset of dynamic properties derived from molecular dynamics (MD) simulations and normal mode analysis (NMA) for over 64,000 proteins.

SeqDance is a transformer model trained from scratch on this dynamic data, demonstrating that it can learn to capture dynamic interactions and global conformational properties from sequence alone. ESMDance builds upon the powerful ESM2 model, integrating its pre-trained evolutionary knowledge with newly learned dynamic properties. The key finding is that this integration leads to significantly improved zero-shot prediction of mutation effects. ESMDance substantially outperforms ESM2 and other models on proteins lacking evolutionary information, such as de novo designed proteins and certain viral proteins, demonstrating that dynamic and evolutionary information are complementary. The work provides a new framework for creating more generalizable pLMs by directly incorporating biophysical dynamics.

**Rating: 9/10**

This paper is a significant contribution to the field of protein machine learning. Its novelty lies in the direct use of large-scale dynamical simulation data for pre-training, a conceptually important step beyond static structures. The creation of the training dataset itself is a valuable resource for the community. The experimental design is rigorous, featuring thoughtful comparisons to state-of-the-art models (ESM2, ProSE, METL) and compelling evaluations on challenging protein classes where existing methods falter. The results convincingly demonstrate that integrating biophysical dynamics with evolutionary information leads to more robust and fundamentally grounded models. The work effectively bridges the gap between biophysical simulation and sequence-based deep learning, opening a promising new direction for research.

### 2. Main Ideas

1.  **Training pLMs on Protein Dynamics:** The central thesis is that static structures and evolutionary history provide an incomplete picture of protein function. The authors propose a new training paradigm where pLMs learn the principles of protein behavior by being pre-trained directly on dynamic properties (e.g., residue fluctuations, interaction frequencies, and collective motions) derived from large-scale molecular dynamics (MD) simulations and normal mode analysis (NMA). This allows the model to learn from biophysical first principles rather than relying solely on the correlational patterns in evolutionary data.

2.  **Synergy between Evolutionary and Dynamic Information:** The paper demonstrates that evolutionary information and biophysical dynamics are highly complementary. While SeqDance (trained only on dynamics) learns meaningful properties, the superior performance comes from ESMDance, which integrates the evolutionary knowledge from ESM2 with dynamic properties. This synergy is most evident in its exceptional performance on designed and viral proteins, which lack deep evolutionary records. By combining these two information sources, ESMDance achieves a more complete and generalizable understanding of the sequence-to-function relationship.

### 3. 10 Most Important Citations

1.  **Lin et al. (2023)**. Evolutionary-scale prediction of atomic-level protein structure with a language model.
    This paper introduces the ESM-2 model and ESMFold, which serve as the architectural and pre-trained foundation for the ESMDance model presented in this work.

2.  **Rives et al. (2021)**. Biological structure and function emerge from scaling unsupervised learning to 250 million protein sequences.
    This is the foundational paper for the ESM family of models, establishing the viability and power of large-scale self-supervised learning on protein sequences, a paradigm this research builds upon and extends.

3.  **Tsuboyama et al. (2023)**. Mega-scale experimental analysis of protein folding stability in biology and design.
    This work provides the large-scale experimental dataset of mutation effects on protein stability that is used as the primary benchmark for validating the zero-shot prediction performance of SeqDance and ESMDance.

4.  **Notin et al. (2023)**. ProteinGym: Large-Scale Benchmarks for Protein Design and Fitness Prediction.
    This paper provides key benchmark datasets, including deep mutational scans of viral proteins, which are used to demonstrate the enhanced performance of the new models on rapidly evolving sequences that are challenging for traditional pLMs.

5.  **Bepler et al. (2021)**. Learning the protein language: Evolution, structure, and function.
    This paper introduces ProSE, a pLM that integrates sequence and static structure information, serving as an important model for comparison to highlight the distinct benefits of incorporating dynamic properties.

6.  **Tesei et al. (2024)**. Conformational ensembles of the human intrinsically disordered proteome.
    This citation refers to the IDRome dataset, a critical source of coarse-grained molecular dynamics trajectories for intrinsically disordered proteins used in the pre-training dataset.

7.  **Mirarchi et al. (2024)**. mdCATH: A Large-Scale MD Dataset for Data-Driven Computational Biophysics.
    This paper introduces the mdCATH dataset, which provided a large portion of the all-atom molecular dynamics simulation data used to train the SeqDance and ESMDance models.

8.  **Vaswani et al. (2017)**. Attention is All You Need.
    This seminal paper introduced the Transformer architecture, which is the fundamental deep learning framework used to build the SeqDance and ESMDance models.

9.  **Haliloglu et al. (1997)**. Gaussian Dynamics of Folded Proteins.
    This is a foundational paper describing the Gaussian Network Model (GNM), a type of Normal Mode Analysis that the authors used to efficiently generate a large volume of low-resolution protein dynamics data for their training set.

10. **Gelman et al. (2024)**. Biophysics-based protein language models for protein engineering.
    This paper introduces METL, a pLM trained on biophysical properties from static structures, which serves as a key point of comparison to demonstrate the additional value of using dynamic, rather than static, information.
