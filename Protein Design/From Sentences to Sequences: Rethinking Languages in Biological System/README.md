https://arxiv.org/abs/2507.00953

**From Sentences to Sequences: Rethinking Languages in Biological System**

### 1. Summary and Rating

This paper presents a critical analysis of applying large language model (LLM) paradigms, developed for Natural Language Processing (NLP), directly to the modeling of biological sequences like proteins and RNA. The authors argue that a fundamental mismatch exists between natural and biological languages. While natural language semantics are abstract and dependencies are often local, biological language "semantics" are physically grounded in the molecule's 3D structure, which is governed by strong, long-range dependencies (e.g., base pairing).

The authors use the biomolecule inverse folding task (designing a sequence for a given 3D structure) as a case study. They argue that the standard sequential, left-to-right generation common in NLP is suboptimal for biological sequences. Instead, they propose and empirically validate a "stochastic-order" generation paradigm that can better capture long-range interactions. Following this logic, they also critique standard NLP evaluation metrics like BLEU and advocate for a structure-aware evaluation pipeline incorporating metrics like TM-score, RMSD, and energy, which directly assess the "semantic" correctness of the generated sequence. Their proposed RNA inverse folding model, RiFold, which uses stochastic-order generation, is shown to outperform previous state-of-the-art models on both sequence and structure recovery metrics.

**Rating: 9/10**

This is an excellent and timely paper. For a specialized audience, it provides a clear, well-argued, and empirically supported critique of the naive transfer of methods from NLP to computational biology. The core contribution is not a novel architecture but a conceptual reframing of how to approach generation and evaluation for biological sequences. The distinction between sequential and stochastic-order generation is insightful, and the proposed evaluation pipeline is a practical and necessary contribution to the field. The work is rigorous, the experiments are well-designed, and the paper clearly articulates a crucial point that can help guide future research in generative models for biology.

### 2. Main Ideas Discussed

1.  **The Fundamental Mismatch Between Natural and Biological Languages**: The paper's central thesis is that biological sequences and natural language are fundamentally different. Biological sequences have semantics that are concrete and measurable (their 3D structure), and they are defined by strong, long-range dependencies dictated by physics. In contrast, natural language has abstract semantics and more local, syntactic dependencies, making the direct application of NLP methods and paradigms potentially flawed.

2.  **Stochastic-Order Generation is Superior to Sequential Generation**: Arising from the first point, the paper argues that the standard left-to-right autoregressive generation used in NLP is ill-suited for biological sequences. It demonstrates that a stochastic-order generation, where tokens can be generated in an arbitrary order based on model confidence, is more effective at capturing the critical long-range dependencies, leading to improved performance in the inverse folding task.

3.  **The Necessity of Structure-Based Evaluation over Sequence-Based Metrics**: The paper critiques the use of traditional NLP metrics (like BLEU) and even simple native sequence recovery for evaluating biological sequence design. It argues that since the function of a biomolecule is tied to its structure, evaluation must be structure-aware. The authors propose and use a pipeline that evaluates generated sequences by folding them and measuring structural similarity (TM-score, RMSD) and stability (energy) against the target, providing a more meaningful assessment of semantic correctness.

### 3. 10 Most Important Citations

*No hyperlinks were provided in the paper's reference section.*

1.  **Dauparas et al. 2022**. Robust deep learning-based protein sequence design using proteinmpnn.
    This paper introduces ProteinMPNN, a state-of-the-art method for protein inverse folding that serves as a key point of comparison and a foundational model in the field.

2.  **Tan et al. 2024**. RDesign: Hierarchical data-efficient representation learning for tertiary structure-based RNA design.
    This work presents RDesign, the primary state-of-the-art model for RNA inverse folding against which the paper's own model, RiFold, is benchmarked.

3.  **Brown et al. 2020**. Language models are few-shot learners.
    This paper on GPT-3 represents the success and power of the autoregressive language modeling paradigm in NLP that the authors argue needs to be rethought for biological applications.

4.  **Ingraham et al. 2019**. Generative models for graph-based protein design.
    This is a foundational paper on using graph neural networks for protein design, representing a major class of structure-based models that the authors compare their work against.

5.  **Vaswani et al. 2017**. Attention is all you need.
    This paper introduced the Transformer architecture, which is the foundational technology for most of the large-scale models discussed, both in NLP and their biological adaptations.

6.  **Pace et al. 2014a**. Contribution of hydrogen bonds to protein stability.
    This citation provides the biophysical grounding for the paper's core argument about the importance of long-range interactions in biological sequences.

7.  **Lin et al. 2023a**. Evolutionary-scale prediction of atomic-level protein structure with a language model.
    This paper introduces ESMFold, a powerful structure prediction model that is essential for the structure-based evaluation pipeline advocated for by the authors.

8.  **Papineni et al. 2002**. Bleu: a method for automatic evaluation of machine translation.
    This is the canonical citation for the type of NLP-based evaluation metric that the authors argue is insufficient and inappropriate for assessing the quality of generated biological sequences.

9.  **Yim et al. 2023**. SE(3) diffusion model with application to protein backbone generation.
    This paper is cited in the context of modern evaluation metrics (TM-score, RMSD), highlighting the current standards for structural comparison used in the proposed evaluation pipeline.

10. **Radford et al. 2019**. Language models are unsupervised multitask learners.
    This paper on GPT-2 is another key example of the sequential, autoregressive models from NLP whose success motivated the transfer to biology but whose methodology the authors critique.
