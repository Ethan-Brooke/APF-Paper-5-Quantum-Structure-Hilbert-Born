# Quantum Structure from Finite Enforceability

### Interactive Mathematical Appendix to Paper 5 of the Admissibility Physics Framework

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18439433.svg)](https://doi.org/10.5281/zenodo.18439433) [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ethan-Brooke/APF-Paper-5-Quantum-Structure-Hilbert-Born/blob/main/APF_Reviewer_Walkthrough.ipynb)

[Interactive Derivation DAG](https://ethan-brooke.github.io/APF-Paper-5-Quantum-Structure-Hilbert-Born/) · [Theorem Map](#theorem-mapping-table) · [Reviewers' Guide](REVIEWERS_GUIDE.md) · [The full APF corpus](#the-full-apf-corpus) · [Citation](#citation)

> **AI agents:** start with [`START_HERE.md`](START_HERE.md) — operational checklist that loads the framework context in 5–10 minutes. The corpus inventory and full file map are in [`ai_context/repo_map.json`](ai_context/repo_map.json).

---

## Why this codebase exists

Standard apparatus of quantum mechanics derived from PLEC plus three paper-specific hypotheses: linearity from coherence closure, complex Hilbert emergence via Frobenius trichotomy, T_tensor + T_Born (via Gleason) + T_Hermitian + T_CPTP (with Stinespring dilation interface-mediator interpretation), measurement as Type III regime exit via record-locking channels, spectral-action internalization, UV completion as Type IV exit. Version 2.0-PLEC main paper (12pp) + Technical Supplement v1.0 (31pp, 2026-04-19 self-contained formal companion).

This repository is the executable proof.

The codebase is a faithful subset of the canonical APF codebase v24.3.249 (3,745 bank-registered theorems across 422 modules). Each theorem in the manuscript traces to a named `check_*` function in `apf/core.py`, which can be called independently and returns a structured result.

The codebase requires Python 3.8+ and NumPy / SciPy (some numerical lemmas use them; see `pyproject.toml`).

## How to verify

Three paths, in order of increasing friction:

**1. Colab notebook — zero install.** [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Ethan-Brooke/APF-Paper-5-Quantum-Structure-Hilbert-Born/blob/main/APF_Reviewer_Walkthrough.ipynb) Every key theorem is derived inline, with annotated cells you can inspect and modify. Run all cells — the full verification takes under a minute.

**2. Browser — zero install.** Open the [Interactive Derivation DAG](https://ethan-brooke.github.io/APF-Paper-5-Quantum-Structure-Hilbert-Born/). Explore the dependency graph. Hover any node for its mathematical statement, key result, and shortest derivation chain to A1. Click **Run Checks** to watch all theorems verify in topological order.

**3. Local execution.**

```bash
git clone https://github.com/Ethan-Brooke/APF-Paper-5-Quantum-Structure-Hilbert-Born.git
cd APF-Paper-5-Quantum-Structure-Hilbert-Born
pip install -e .
python run_checks.py
```

Expected output:

```
      Paper 5 (Quantum Structure from Finite Enforceability): 8 passed, 0 failed, 8 total — verified in <minutes>
```

**4. Individual inspection.**

```python
from apf.bank import get_check
r = get_check('check_L_ST_algebra')()
print(r['key_result'])
```

For reviewers, a [dedicated guide](REVIEWERS_GUIDE.md) walks through the logical architecture, the structural assumptions, and the anticipated objections.

---

## Theorem mapping table

This table maps every result in the manuscript to its executable verification.

| Check | Type | Summary |
|-------|------|---------|
| `check_L_ST_algebra` | Lemma | L_ST_algebra: Connes Finite Algebra A_F = C ⊕ M_2(C) ⊕ M_3(C) from T_gauge [P]. |
| `check_L_Gleason_finite` | Lemma | L_Gleason_finite: Born Rule from Frame Function (Finite-Dim) [P]. |
| `check_T9` | Theorem | T9: L3-mu Record-Locking -> k! Inequivalent Histories. |
| `check_T_gauge` | Theorem | T_gauge: SU(3)*SU(2)*U(1) from Capacity Budget. |
| `check_T5` | Theorem | T5: Minimal Anomaly-Free Chiral Matter Completion. |
| `check_T4F` | Theorem | T4F: Flavor-Capacity Saturation. |
| `check_L_ST_Hilbert` | Lemma | L_ST_Hilbert: Connes Hilbert Space H_F = C^{90} from T_field + T7 [P]. |
| `check_Regime_exit_Type_III` | Other | Regime_exit_Type_III: Change of Admissible Class (Record Locking) [P]. |

All check functions reside in `apf/core.py`. Every function listed above can be called independently and returns a structured result including its logical dependencies and the mathematical content it verifies.

---

## The derivation chain

```
  Level 0: L_ST_algebra · L_Gleason_finite · T9 · T_gauge · T5 · T4F · L_ST_Hilbert · Regime_exit_Type_III
```

The [interactive DAG](https://ethan-brooke.github.io/APF-Paper-5-Quantum-Structure-Hilbert-Born/) shows the full graph with hover details and animated verification.

---

## Repository structure

```
├── README.md                              ← you are here
├── START_HERE.md                          ← AI operational checklist; read-first for AI agents
├── REVIEWERS_GUIDE.md                     ← physics-first walkthrough for peer reviewers
├── interactive_dag.html                   ← interactive D3.js derivation DAG (also served at docs/ via GitHub Pages)
├── repo_map.json                          ← machine-readable map of this repo (root copy of ai_context/repo_map.json)
├── theorems.json                          ← theorem catalog (root copy of ai_context/theorems.json)
├── derivation_graph.json                  ← theorem DAG as JSON (root copy of ai_context/derivation_graph.json)
├── ai_context/                            ← AI onboarding pack (corpus map, theorems, glossary, etc.)
│   ├── AGENTS.md                          ← authoritative entry point for AI agents
│   ├── FRAMEWORK_OVERVIEW.md              ← APF in 5 minutes
│   ├── GLOSSARY.md                        ← axioms, PLEC primitives, epistemic tags
│   ├── AUDIT_DISCIPLINE.md                ← engagement posture for critique/proposal
│   ├── OPEN_PROBLEMS.md                   ← catalog of open problems + verdicts
│   ├── repo_map.json                      ← machine-readable map of this repo
│   ├── theorems.json                      ← machine-readable theorem catalog
│   ├── derivation_graph.json              ← theorem DAG as JSON
│   └── wiki/                              ← bundled APF wiki (concepts, papers, codebase)
├── apf/
│   ├── core.py                            ← 8 theorem check functions
│   ├── apf_utils.py                       ← exact arithmetic + helpers
│   └── bank.py                            ← registry and runner
├── docs/
│   └── index.html                         ← interactive derivation DAG (GitHub Pages)
├── APF_Reviewer_Walkthrough.ipynb         ← Colab notebook
├── run_checks.py                          ← convenience entry point
├── pyproject.toml                         ← package metadata
├── zenodo.json                            ← archival metadata
├── Paper_5_Quantum_Structure_Hilbert_Born_v2.0-PLEC.tex                ← the paper

└── LICENSE                                ← MIT
```

---

## What this paper derives and what it does not

**Derived:** (see Theorem mapping table above)

**Not derived here:** Specific results outside this paper's scope live in companion papers — see the corpus table below for the full corpus (Papers 0-42).

---

## Citation

```bibtex
@software{apf-paper5,
  title   = {Quantum Structure from Finite Enforceability},
  author  = {Brooke, Ethan},
  year    = {2026},
  doi     = {10.5281/zenodo.18439433},
  url     = {https://github.com/Ethan-Brooke/APF-Paper-5-Quantum-Structure-Hilbert-Born}
}
```

For the full citation lineage (concept-DOI vs version-DOI, related identifiers, bibtex for all corpus papers), see [`ai_context/CITING.md`](ai_context/CITING.md).

---

<!-- FOOTER:start -->
---

## About the APF series

The Admissibility Physics Framework is a constraint-first derivation of the Standard Model and cosmological structure from a single primitive — finite enforcement capacity. The corpus runs from the foundational papers through the gauge sector, the quantum formalism, Lorentzian spacetime and the Einstein field equations, the cosmological constant, the electroweak and dark sectors, and the lattice Yang-Mills program. Each paper's main text and Technical Supplement is deposited separately on Zenodo and collected in the **[admissibility_physics](https://zenodo.org/communities/admissibility_physics)** community. The engine repository is the machine-verifiable companion to all of it (v24.3.249 — 3,745 bank-registered theorems across 422 typed modules, 48 quantitative predictions).

| # | Title | Concept DOI |
|---|---|---|
| Engine | Admissibility Physics — Unified Theorem Bank & Verification Engine | [10.5281/zenodo.18529115](https://doi.org/10.5281/zenodo.18529115) |
| 0 | What Physics Permits: A Constraint-First Framework for Physics | [10.5281/zenodo.18439523](https://doi.org/10.5281/zenodo.18439523) |
| 1 | The Enforceability of Distinction | [10.5281/zenodo.18439200](https://doi.org/10.5281/zenodo.18439200) |
| 2 | Finite Admissibility and the Failure of Global Description | [10.5281/zenodo.18439274](https://doi.org/10.5281/zenodo.18439274) |
| 3 | Entropy, Time, and Accumulated Cost | [10.5281/zenodo.18439363](https://doi.org/10.5281/zenodo.18439363) |
| 4 | Admissibility Constraints and Structural Saturation | [10.5281/zenodo.18439397](https://doi.org/10.5281/zenodo.18439397) |
| 5 | Quantum Structure from Finite Enforceability | [10.5281/zenodo.18439433](https://doi.org/10.5281/zenodo.18439433) |
| 6 | Dynamics and Geometry as Optimal Admissible Reallocation | [10.5281/zenodo.18439445](https://doi.org/10.5281/zenodo.18439445) |
| 7 | A Minimal Quantum of Action from Finite Admissibility | [10.5281/zenodo.18439513](https://doi.org/10.5281/zenodo.18439513) |
| 8 | The Admissibility-Capacity Ledger | [10.5281/zenodo.19721384](https://doi.org/10.5281/zenodo.19721384) |
| 9 | The Geometric Substrate as Cost Structure of Comparison Continuations | [10.5281/zenodo.20041675](https://doi.org/10.5281/zenodo.20041675) |
| 10 | The Calculus of Finite Continuability | [10.5281/zenodo.20041680](https://doi.org/10.5281/zenodo.20041680) |
| 11 | Forced Universality from Capacity-Bounded Admissibility | [10.5281/zenodo.20684198](https://doi.org/10.5281/zenodo.20684198) |
| 13 | The Minimal Admissibility Core | [10.5281/zenodo.18361446](https://doi.org/10.5281/zenodo.18361446) |
| 16 | Markov Breakdown and the Hard Problems | [10.5281/zenodo.20684207](https://doi.org/10.5281/zenodo.20684207) |
| 18 | The Electroweak Sector as a Capacity Equilibrium | [10.5281/zenodo.20684209](https://doi.org/10.5281/zenodo.20684209) |
| 20 | The Enforcement Crystal | [10.5281/zenodo.18531732](https://doi.org/10.5281/zenodo.18531732) |
| 21 | APF Engine — Unified Theorem Bank and Verification Engine | [10.5281/zenodo.18529115](https://doi.org/10.5281/zenodo.18529115) |
| 24 | The Recruitment-Radius Extension — Foundations | [10.5281/zenodo.20684211](https://doi.org/10.5281/zenodo.20684211) |
| 28 | Absolute Mass Scales from Electroweak Capacity Saturation | [10.5281/zenodo.20684215](https://doi.org/10.5281/zenodo.20684215) |
| 29 | Plaquette Representation Dominance and Confinement | [10.5281/zenodo.20684218](https://doi.org/10.5281/zenodo.20684218) |
| 30 | A Tube Mechanism for the Lattice Mass Gap | [10.5281/zenodo.20684220](https://doi.org/10.5281/zenodo.20684220) |
| 31 | Osterwalder-Schrader Structure of Lattice Yang-Mills | [10.5281/zenodo.20684222](https://doi.org/10.5281/zenodo.20684222) |
| 33 | Trace-to-Scheme Export Architecture | [10.5281/zenodo.20684224](https://doi.org/10.5281/zenodo.20684224) |
| 35 | The Dark Sector as a Two-Role Capacity Decomposition | [10.5281/zenodo.20684228](https://doi.org/10.5281/zenodo.20684228) |
| 40 | Between Symmetry and the Void — The Thermodynamics of Finite Distinction | [10.5281/zenodo.20684235](https://doi.org/10.5281/zenodo.20684235) |
| 41 | The Horizon as a Continuation Ledger | [10.5281/zenodo.20684241](https://doi.org/10.5281/zenodo.20684241) |
| 42 | The Weak Mixing Angle Is Not Free | [10.5281/zenodo.20684245](https://doi.org/10.5281/zenodo.20684245) |

Concept DOIs always resolve to the latest version. Technical Supplements are deposited as linked records — `isSupplementTo` the main paper, `isDocumentedBy` the companion repository.

## Author

Ethan Brooke — Independent Researcher, San Anselmo, California, USA.

- ORCID: [0009-0001-2261-4682](https://orcid.org/0009-0001-2261-4682)
- LinkedIn: [linkedin.com/in/ethanbrooke](https://www.linkedin.com/in/ethanbrooke/)
- GitHub: [github.com/Ethan-Brooke](https://github.com/Ethan-Brooke)
- Contact: brooke.ethan@gmail.com

MIT — see [LICENSE](LICENSE).
<!-- FOOTER:end -->
