https://www.biorxiv.org/content/10.1101/2025.06.13.659451v2.abstract

\*\*Relatedness score: \*\* **6 / 10**

| What maps to your Pareto-FM SaaS                                                                                                                                               | Evidence in the paper                                                                                                                                         | Why it’s useful |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| **Discrete, token-level generator for proteins.** The model runs a *D3PM* discrete diffusion process directly in sequence space—exactly the space your platform will explore.  | Confirms that sequence-only generative models (no backbone input) can produce novel, foldable proteins—good baseline or comparison point for your FM sampler. |                 |
| **All-atom SELFIES representation** accepts non-canonical residues & PTMs.                                                                                                     | Could be a premium feature: design/score modified residues that canonical-only FM checkpoints miss.                                                           |                 |
| **Practical tricks you can borrow**—absorbing-mask noise schedule beats uniform, and an automated validity pipeline removes junk sequences.                                    | Drop these into your discrete-FM pre-processing to cut inference waste and raise customer-visible “hit-rate per plate.”                                       |                 |

| Where it diverges from your product vision                                                                                                                                                                      | Impact on relevance |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------- |
| **Diffusion, not Flow-Matching.** No straight-path OT or <15-step inference—you still need your FM speed-ups to hit SaaS latency/\$\$ targets.                                                                  |                     |
| **Single-objective focus.** The paper optimises only *validity + foldability*; there’s no weight-vector conditioning or dominance-classifier for multi-objective trade-offs. Your Pareto slider remains unique. |                     |
| **No wet-lab cost framing or compliance story.** Evaluation pain is compute time, not \$250–\$1 000 assays; GxP/HIPAA aspects untouched.                                                                        |                     |

**Bottom line**

The work is a **solid technical cousin**—proving discrete diffusion can handle complex protein chemistry and offering engineering nuggets (SELFIES tokens, absorbing noise). But because it lacks Flow-Matching speed, explicit Pareto guidance, and a wet-lab ROI narrative, it complements rather than competes with the proprietary core of your protein/peptide Pareto-FM SaaS—landing at a **6 / 10** relevance.
