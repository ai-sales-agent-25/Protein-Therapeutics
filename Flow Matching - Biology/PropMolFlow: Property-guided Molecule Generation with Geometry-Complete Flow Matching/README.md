https://arxiv.org/abs/2505.21469

**Relevance score: 6 / 10**

| Dimension                               | Match to your Pareto-aware, flow-matching peptide SaaS                                                                                                          | Evidence in *PropMolFlow*                                                                                      | Where you still differentiate                                                     |
| --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| **Flow-matching core**                  | **High.** Uses an SE(3)-equivariant *geometry-complete* flow-matching backbone for joint generation of atom types, bonds & 3-D coordinates.                     | “We introduce PropMolFlow… a novel approach… based on geometry-complete SE(3)-equivariant **flow matching**.”  | You may opt for rectified or one-step FM variants for even lower latency.         |
| **Property guidance**                   | **Medium.** Conditions on **one scalar property at a time** (gap, dipole, polarizability …). Provides several embedding tricks and shows both ID & OOD control. | §3.5–3.6 describe property embeddings; six single-property tasks on QM9.                                       | No simultaneous optimisation or Pareto frontier visualisation.                    |
| **Multi-objective / Pareto focus**      | **Low.** Demonstrates single-objective conditioning only; authors note multi-objective generation as *future work*.                                             | “Current model is limited to single-property guidance… extension to multi-objective is future work.”           | Your live potency-vs-stability-vs-CMC-vs-safety frontier remains unique.          |
| **Protein / peptide therapeutic scope** | **Low–moderate.** Benchmarks solely on **QM9 small molecules** (3-29 atoms); no peptides, no target binding.                                                    | “This work focuses on **small molecules** from the QM9 dataset.”                                               | You specialise in therapeutic peptides & target-aware design.                     |
| **Sampling speed**                      | **Useful.** 100 Euler steps → 8.8 min for 10 k molecules—\~8× faster than diffusion baselines.                                                                  | Table 2 reports NFE = 100, 8.8 min wall-clock for 10 k samples.                                                | Still need comparable benchmarks after adding more objectives.                    |
| **Safety / manufacturability heads**    | **None.** Focus on electronic & thermodynamic properties; no SPPS yield, oxidation hotspots, immunogenicity.                                                    | Properties list: α, ∆ε, HOMO/LUMO, µ, Cv.                                                                      | Early CMC-cost and tox predictors stay your moat.                                 |
| **Developer-first SaaS layer**          | **Absent.** Code promised on GitHub; no API, versioning, audit trail or compliance tooling.                                                                     | “Code will be publicly released… ”                                                                             | Your open SDK, cloud orchestration and regulatory export remain clear whitespace. |

---

### Why it’s a 6 (and not a 4 or an 8)

* **+** Shares the same *flow-matching* DNA and shows practical **property conditioning**, so more relevant than diffusion-only papers (e.g. PROUD).
* **–** Stops at **single-objective, small-molecule** generation and lacks manufacturability/safety modules or platform considerations—areas central to your mission.

---

### How you could leverage it

| Quick win                                  | Integration idea                                                                                                                |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| **Property-embedding recipes**             | Re-use their “concatenate / sum / multiply” embedding ablation to wire your potency, stability & tox scores into the FM field.  |
| **Geometry-complete graph representation** | Their bond-order + charge handling could improve peptide-linker chemistry and oxidation prediction modules.                     |
| **Speed layer**                            | Benchmark their 100-step Euler sampler as a low-latency preview path while your multi-objective solver refines designs offline. |

**Bottom line:** *PropMolFlow* is a solid algorithmic cousin—good proof that flow-matching can be steered by scalar property labels—but it falls short of the **multi-objective, peptide-focused, compliance-ready SaaS** you’re building.
