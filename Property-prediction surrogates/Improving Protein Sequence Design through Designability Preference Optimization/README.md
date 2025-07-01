https://arxiv.org/abs/2506.00297

**Relevance score: 7 / 10**

**Why not a perfect 10?**
The paper is a tight, well-executed example of **surrogate-guided sequence optimization**—one of your five differentiator tracks—but it is *single-objective* (designability only) and does not yet plug into wet-lab active-learning loops or multi-endpoint Pareto trade-offs. Below is a quick map against each differentiator:

| Commercial differentiator                            | Coverage in the paper | Notes                                                                                                                                                                                  |
| ---------------------------------------------------- | --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **(i) Multi-objective / Pareto guidance & sampling** | **Low**               | ResiDPO optimises only one surrogate (per-residue pLDDT) rather than a vector of therapeutic KPIs. The authors do recognise objective mis-alignment, but stop short of Pareto fronts.  |
| **(ii) Rich property-prediction surrogates**         | **High**              | Uses AlphaFold-pLDDT as a *quantitative, differentiable oracle* and shows residue-level reward shaping—exactly the pattern you would reuse for multi-objective surrogates.             |
| **(iii) Physics/structure priors & constraints**     | **Medium-low**        | pLDDT implicitly encodes physics, but there is no explicit energy term or docking constraint. The method does not combine pLDDT with ΔG, MD or binding affinities.                     |
| **(iv) Active-/lab-learning loops**                  | **None**              | The work is purely *in silico*; no closed-loop wet-lab data acquisition is attempted or discussed.                                                                                     |
| **(v) Benchmarks & evaluation frameworks**           | **Medium**            | Authors curate **PDB-D** and adopt RFdiffusion enzyme/binder suites, adding useful residue-level labels. These could strengthen your SaaS validation story.                            |

**Bottom line:**
ResiDPO is highly relevant as a *template for preference-based fine-tuning using structural surrogates*—one pillar of your Pareto layer. However, to become a full commercial differentiator it would need to (a) generalise the reward to multiple therapeutically meaningful objectives and (b) sit inside an experiment-feedback loop. That gap is why the paper earns a solid—but not game-changing—**7/10** on direct applicability to your Pareto-FM SaaS vision.
