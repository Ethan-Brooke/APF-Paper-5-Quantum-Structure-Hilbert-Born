# Claims Ledger — Paper 5

| # | Claim | Status | Proof location | Code check | Failure mode |
|---|---|---|---|---|---|
| 1 | Linearity from coherence closure | nontrivial | Supp §1 | `check_L_linearity` | non-linear closure counterexample |
| 2 | $\mathbb{C}$-Hilbert via Frobenius trichotomy | nontrivial | Supp §2 | `check_L_frobenius_C` | $\mathbb{R}$ or $\mathbb{H}$ admissible |
| 3 | $T_{\rm tensor}$ | nontrivial | Supp §3 | `check_T_tensor` | alternative composition law |
| 4 | $T_{\rm Born}$ via Gleason | imported + structural | Supp §4 | `check_T_Born` | Kochen-Specker style counter |
| 5 | $T_{\rm Hermitian}$ | nontrivial | Supp §5 | `check_T_Hermitian` | non-self-adjoint observable admissible |
| 6 | $T_{\rm decoherence}$ as Type III exit | nontrivial | Supp §6 | `check_T_decoherence` | coherent persistence |
| 7 | $L_{\rm spectral\_action\_internal}$ $a_0 = 61$ | nontrivial + arithmetic | Supp §7 | `check_L_spectral_action` | Seeley-DeWitt coefficient drift |
| 8 | I3 on Paper 5 Hilbert | nontrivial (receiver) | Supp v1.1 §I3 | `check_T_ACC_unification` (Paper 8) | I3 fails at quantum interface |
| 9 | Sector A ↔ B as measurement | $[P + framing]$ | Supp v1.1 §framing | `check_T_horizon_reciprocity` (Paper 6) | framing disputed |

## Attack surface priority

Claims 1, 2, 6. The Frobenius trichotomy (claim 2) is the least-familiar structural step to outside readers.

---

*6 bank-registered checks verify this paper's subset in this repo; fuller derivation in the canonical codebase.*
