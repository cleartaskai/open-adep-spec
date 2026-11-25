# Open ADEP — Open AI Decision Evidence Protocol (Phase 0 Specification)

**Open ADEP** is an open, vendor-neutral specification and JSON Schema suite for **verifiable decision evidence packages** in high-stakes, AI-assisted workflows, with an initial focus on **healthcare prior authorization (PA)**.

This repository contains the Phase 0 normative specification drafts and JSON Schema (Draft 2020-12) fragments defining the Open ADEP Assurance Contract, Completeness Requirements, Trust Model, Security & Privacy Baseline, and Prior-Authorization Workflow Profile.

---

## Architectural Overview: How & Why Decision Reconstruction Works

Auditability in AI-assisted healthcare decisions fails when logs only record *that* an algorithm ran, without preserving *what clinical evidence, coverage policy, model version, and human review* produced the determination. Open ADEP solves this by standardizing a **decision evidence package** that supports independent, third-party **decision reconstruction** without requiring access to proprietary system internals.

### 1. Healthcare Decision-Reconstruction Semantics
A reconstructible prior-authorization evidence package binds together the discrete artifacts required to explain a determination:
- **Request & Clinical Context:** Initial PA request receipt (`PA-EC-01`) and supporting clinical documentation/records (`PA-EC-02`).
- **Policy & Criteria Binding:** The exact version of the payer's applicable coverage policy or clinical criteria (`PA-EC-03`) evaluated at the time of decision.
- **AI Model Provenance:** Exact model inputs (`PA-EC-04`), model identification/version/configuration (`PA-EC-05`), and model outputs/recommendations (`PA-EC-06`), plus optional agentic delegation and tool-invocation records (`PA-EC-20`–`PA-EC-24`).
- **Human Clinical Review Attestations:** Explicit records of reviewer assignment (`PA-EC-07`) and human review action—accept, modify, or override (`PA-EC-08`)—alongside the final determination (`PA-EC-09`) and rationale (`PA-EC-10`).
- **Downstream & Exception Artifacts:** Requestor notification (`PA-EC-11`), appeal receipts (`PA-EC-12`), adverse determination notices (`PA-EC-13`), external timestamp anchors (`PA-EC-14`), and coverage indicators (`PA-EC-15`), with defined semantics for urgent, emergency-exception, and retrospective review paths.

### 2. Cross-Organization Evidence Graphs & Privacy Boundaries
Prior-authorization decisions routinely span multiple independent organizations: **payers/insurers**, **delegated utilization-management (UM) entities**, **AI model vendors**, **clinical reviewers**, and **external transparency/timestamping services**. Open ADEP models this via:
- **10 Distinct Trust-Model Roles (`R-1`–`R-10`)** and a **Separation-of-Duties Matrix** ensuring no single party can unilaterally forge, countersign, or self-verify an evidence chain.
- **5 Signature Scopes:** Evidence-record signatures, institutional co-signatures, continuity counter-signatures, package seals, and transparency-log inclusion receipts.
- **Boundary-Preserving Verification:** Clinical content (PHI) can remain inside the evidence custodian's boundary while headers, salted hashes, and privacy-preserving commitments cross organizational boundaries (`PRV-MIN-1`, `PRV-DSC-1`–`4`, `PRV-BND-1`–`3`), allowing an independent clean-room verifier to check structural integrity and completeness without inspecting raw clinical text (`redacted` state).

### 3. Cryptographically Valid vs. Decision-Sufficient Verification
A central principle of Open ADEP is that **cryptographic integrity does not imply decision completeness**:
- **Independent Assurance Properties (`P-1`–`P-6`):** Integrity (`P-1`), Authenticity (`P-2`), Signer Trust (`P-3`), Provenance (`P-4`), Completeness (`P-5`), and Temporal Ordering/Anchoring (`P-6`) are evaluated independently.
- **Seven Evidence-Element States:** Every expected evidence class is explicitly classified as `present`, `redacted`, `excluded`, `expected_not_captured`, `unavailable`, `arrived_late`, or `disposed`.
- **Four Completeness Verdicts & Claim Hierarchy:** A package whose hashes and signatures all `PASS` (`P-1`/`P-2`) can still receive `incomplete_documented` or `incomplete_undocumented` under `P-5` if expected clinical records, policy versions, or human-review attestations were not captured. Completeness claims are always qualified (`Scope-complete`, `Scope-complete with documented gaps`, `Coverage-reconciled`, or `Indeterminate`) relative to the declared scope and workflow profile.

---

## Repository Contents

### Specifications (`spec/`)

| Work Item | Document | Description |
|---|---|---|
| **WI-1** | [assurance-contract-v02-draft.md](spec/WI-1-assurance-contract/assurance-contract-v02-draft.md) | Core assurance contract: 6 properties (`P-1`–`P-6`), 4 non-goals (`NG-1`–`NG-4`), 12 verifiable claims, verification context, and milestone mapping. |
| **WI-1 Annex A** | [m2-conformance-profile-annex.md](spec/WI-1-assurance-contract/m2-conformance-profile-annex.md) | M2 conformance profile (`MC-1`–`MC-11`). |
| **WI-1 Annex B** | [conformance-claims-policy-annex.md](spec/WI-1-assurance-contract/conformance-claims-policy-annex.md) | Permissible conformance claims, assessment policy, and clean-room verifier rules. |
| **WI-2** | [completeness-requirements-v02-draft.md](spec/WI-2-completeness-requirements/completeness-requirements-v02-draft.md) | Scope declaration (7 elements), 7 evidence-element states, completeness report (8 fields, 4 verdicts), coverage indicators (`CI-1`–`CI-6`), claim hierarchy, and integrity–completeness matrix. |
| **WI-3** | [trust-model-v02-draft.md](spec/WI-3-trust-model/trust-model-v02-draft.md) | 10 trust-model roles (`R-1`–`R-10`), role-separation matrix, 5 signature scopes, and trust requirements (`TM-1`–`TM-7`). |
| **WI-4** | [security-privacy-baseline-v01-draft.md](spec/WI-4-security-privacy-baseline/security-privacy-baseline-v01-draft.md) | 35 security and privacy requirements (`SEC-CRYPTO`, `SEC-INTEG`, `SEC-PROV`, `SEC-TEMP`, `SEC-OPS`, `PRV-MIN`, `PRV-DSC`, `PRV-ID`, `PRV-BND`). |
| **WI-5** | [pa-workflow-profile-v0-draft.md](spec/WI-5-pa-workflow-profile/pa-workflow-profile-v0-draft.md) | Basic Prior-Authorization workflow profile (`adep.profile.pa.basic.v0`): 15 core classes (`PA-EC-01`–`15`), 5 agentic classes (`PA-EC-20`–`24`), temporal ordering, exception paths, and versioning. |

### JSON Schemas (`schemas/`, Draft 2020-12)

- [scope-declaration.schema.json](schemas/scope-declaration.schema.json) — Scope declaration object (`urn:open-adep:wi2:scope-declaration`)
- [evidence-element-state.schema.json](schemas/evidence-element-state.schema.json) — Seven normative evidence-element state codes (`urn:open-adep:wi2:evidence-element-state`)
- [completeness-report.schema.json](schemas/completeness-report.schema.json) — Completeness assessment report (`urn:open-adep:wi2:completeness-report`)
- [expected-evidence-classes.schema.json](schemas/expected-evidence-classes.schema.json) — Allowed class identifiers for `adep.profile.pa.basic.v0` (`urn:open-adep:wi5:expected-evidence-classes`)

---

## Release Integrity & Verification

`RELEASE_MANIFEST.json` records the SHA-256 cryptographic digest of every specification and schema file in this release. After publication, it can be independently anchored via OpenTimestamps (`RELEASE_MANIFEST.json.ots`) or an RFC 3161 TSA.
