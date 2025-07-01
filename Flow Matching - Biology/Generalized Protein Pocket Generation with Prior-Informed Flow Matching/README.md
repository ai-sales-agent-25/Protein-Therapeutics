https://zitniklab.hms.harvard.edu/projects/PocketFlow/

**Relatedness score: 8 / 10**

### Why PocketFlow is strongly aligned with your Pareto-FM SaaS

* **Same core engine – Flow-Matching.** PocketFlow trains conditional vector fields on backbone frames, torsion angles, residue and interaction types *using the FM loss*—the exact technology stack you’re commercialising.&#x20;
* **Domain-specific generation, not just scoring.** It *creates* sequence + structure pockets around ligands, so it could be a plug-in candidate factory or benchmark inside your platform.&#x20;
* **Built-in guidance hooks.** During sampling it adds two classifier-guided terms—(i) a lightweight binding-affinity predictor and (ii) detailed geometry constraints on hydrogen bonds, salt bridges, etc.—demonstrating exactly how FM models can incorporate extra rewards on-the-fly.
* **Multi-modality proof.** PocketFlow already generalises from small-molecule ligands to peptides and RNA by re-using the same conditional flows, showing the cross-domain flexibility your SaaS will need.&#x20;
* **Clear wet-lab value.** Affinity and clash metrics improve versus diffusion baselines, illustrating that FM + physical priors can *reduce downstream screening*—the economic story you pitch to protein-design teams.&#x20;

### Where it diverges from your product vision

* **Scalar-goal guidance, not full Pareto.** Affinity + geometry act as two separate scalars; there’s no weight-vector conditioning or dominance-classifier that lets users slide across *many* objectives. Your Pareto layer remains the differentiator.
* **Pocket-centric, not whole-protein HPO.** It redesigns residues within \~3.5 Å of a ligand; broader properties like immunogenicity or manufacturability are outside its scope.
* **No latency/solver-step optimisation.** The paper focuses on quality, not runtime. You still need your < 15-step straight-path tricks to meet SaaS cost targets.
* **Research code, not service.** Compliance, VPC deployment and pay-per-evaluation billing—the business plumbing of your SaaS—are untouched.

### Take-away

PocketFlow is a **ready technical cousin**: you can ① borrow its interaction-prior guidance modules, ② cite its benchmark wins to reassure customers that FM competes with diffusion, and ③ even surface it as an optional “pocket-design generator” in your catalogue.
But because it stops at *two* fixed rewards and lacks a Pareto front or SaaS-grade efficiency stack, it complements rather than replaces the proprietary layer that will power your protein/peptide optimisation business—earning a solid **8 / 10** relevance score.
