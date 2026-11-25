# Open ADEP M2 Conformance Profile Annex

**Document Identifier:** ADEP-WI1-M2-v0  
**Status:** DRAFT — attached as Annex A (W3-T09)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §10.1  
**Parent contract:** ADEP-WI1-AC-v0.2 Annex A  
**Author:** LEAD (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This file is the drafting source for Annex A of `assurance-contract-v02-draft.md`. The attached copy uses section numbers A.1 through A.6. The numbers in this file are the drafting numbers. The claims-policy text is Annex B.

**Inputs:** SRS §10.1.1, §10.1.2, and §10.1.3; assurance contract v0.2 §6.2 through §6.9 and open items OI-7 and OI-8; completeness requirements v0.2 §3, §4, and §6; PA profile `adep.profile.pa.basic.v0`.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1-draft.1 | 2026-10-25 | LEAD | W3-T07. Eleven capabilities, test-case minimums, excluded list, and claim cross-references. No claim added. |
| 0.1-draft.2 | 2026-10-25 | LEAD | W3-T08 cross-reference. MC-9 points at the claims-policy annex §5. No capability or claim changed. |
| 0.1-draft.3 | 2026-10-25 | LEAD | W3-T09. Attached as Annex A of the assurance contract. No capability or claim changed. |

---

## 1. Objective

Normative for the capability list, the test-case minimums, and the excluded list. This is SRS §10.1.1. Milestone M2 is the first conformance target. The claims that target includes are the nine claims at M1 and M2 in the assurance contract §6.8: C-INT-1, C-AUT-1, C-TRS-2, C-PRV-1, C-PRV-2, C-CMP-1, C-CMP-2, C-INT-2, and C-AUT-2. C-AUT-3, C-TMP-1, and C-LOG-1 stay outside that set.

A claim identifier in this annex cites one of those claims, or records that the capability has none in the set. The citation does not add a claim, move a milestone, or add a state code.

---

## 2. Rules

1. The capability list is MC-1 through MC-11. Each row keeps the minimum count and the scenario names in SRS §10.1.2.
2. A claim cross-reference is valid when it matches assurance contract §6.9. MC-4, MC-5, MC-6, and MC-11 have a claim that states the check. MC-2 uses C-INT-1. MC-8 uses C-CMP-1 and C-CMP-2. MC-7 is an M2 capability whose property claims stay at M3. MC-1, MC-3, MC-9, and MC-10 have no claim in the set.
3. Where the claim cell is none, the capability remains a row. That absence is assurance contract open item OI-8. This annex does not close it.
4. The test-case counts are the SRS minima. This annex does not add a vector identifier. Vectors already named on a claim may be cited. Catalog follow-ons already recorded on those claims stay follow-ons.
5. The evidence-element codes are the seven in the completeness draft §3. This annex has no code named missing.
6. The profile required at M2 is `adep.profile.pa.basic.v0`. The agentic classes PA-EC-20 through PA-EC-24 stay defined in that profile and are outside M2 test coverage.
7. The attached copy is Annex A of the assurance contract. This file keeps the drafting section numbers.

---

## 3. Minimum conformance capabilities

| ID | Capability | M2 test minimum | Claim in the M2 set |
|----|------------|-----------------|---------------------|
| MC-1 | Package production. Generate an evidence package conforming to profile `adep.profile.pa.basic.v0`. | At least 3 test cases: normal flow, urgent flow, denial flow. | None |
| MC-2 | Schema validation. Reject or report structurally invalid packages with specific error identification. | At least 5 invalid-package test cases covering missing required fields, type errors, and malformed structures. | C-INT-1 |
| MC-3 | Referential integrity. Detect broken or unresolved required references between evidence records and the package manifest. | At least 3 test cases with broken references. | None |
| MC-4 | Integrity verification. Verify defined hashes, signatures, and integrity relationships. Produce a result per claim. | At least 5 test cases covering valid packages, tampered content, invalid signatures, and algorithm mismatch. | C-INT-1, C-INT-2, C-AUT-1, C-AUT-2 |
| MC-5 | Signer assessment. Distinguish signature validity (P-2) from signer trust (P-3). Report both independently. | At least 3 test cases: valid signature and trusted signer, valid signature and untrusted signer, invalid signature. | C-AUT-1, C-TRS-2 |
| MC-6 | Completeness assessment. Report expected evidence that is not present, and the scope of the assessment, using the seven evidence-element codes. | At least 5 test cases covering scope-complete, incomplete-documented, incomplete-undocumented, and excluded-evidence scenarios. | C-CMP-1, C-CMP-2 |
| MC-7 | Temporal assessment. Report applicable ordering inconsistencies and timestamp limitations. | At least 3 test cases with ordering violations and timestamp anomalies. | None in the M2 set |
| MC-8 | Selective disclosure. Verify redacted packages. Distinguish `present` and `redacted`. Produce a verification result for a package whose clinical content is withheld. | At least 4 test cases: full disclosure, partial redaction, full redaction (metadata only), and a redacted element reported as an absence (must fail). | C-CMP-1, C-CMP-2 |
| MC-9 | Independent verification. Permit verification without depending exclusively on one implementation's internal database or application logic. The package plus published trust anchors must be sufficient. Results agree with the clean-room reference verifier. | At least 2 test cases verified by both the implementation and the clean-room verifier, with results compared for agreement. | None |
| MC-10 | Exportability. Export the package with the required verification material: trust anchors, schema, and profile definition. | At least 2 test cases: export, re-import, and re-verify round-trip. | None |
| MC-11 | Failure reporting. Produce machine-readable verification results and a human-readable explanation for every failure. | Every test case that produces a failure has its error output checked for machine readability and for a human-readable explanation. | Every claim in the M2 set |

### 3.1 MC-1

Producing a package for `adep.profile.pa.basic.v0` is the PA profile. This row has no claim ID. SRS names the three cases normal flow, urgent flow, and denial flow. Urgent flow is the PA profile §6.1. The profile's other paths are the emergency exception and retrospective review. This annex keeps the SRS name denial flow. It does not add a denial class, and it does not add a fourth path to the profile.

### 3.2 MC-2

Structural validation is part of P-1. The claim is C-INT-1. The vectors named on that claim are TV-CAN-01 and TV-CAN-02. The SRS phrase "missing required fields" names a structural defect. It is not a state code. The minimum is five invalid-package cases covering that defect, type errors, and malformed structures. This annex does not assign vector identifiers to the cases beyond TV-CAN-01 and TV-CAN-02.

### 3.3 MC-3

No claim in the set detects an unresolved reference between an evidence record and the package manifest. The minimum is three test cases with broken references. The row stays, and the claim cell stays none. That residual is assurance contract open item OI-8.

### 3.4 MC-4

Hash checks are C-INT-1. A signature that does not bind is C-AUT-1. Algorithm mismatch is C-AUT-1, and the vector named on that claim is TV-SIG-03. C-INT-2 and C-AUT-2 are the M2 additions. Each claim reports its own result. The minimum is five test cases covering valid packages, tampered content, invalid signatures, and algorithm mismatch. Vectors already named on those claims include TV-INT-01, TV-INT-03, TV-SIG-01, TV-SIG-03, and TV-INT-02. This annex does not add a vector identifier for the valid-package case. Catalog-label follow-ons already written on the claims stay follow-ons.

### 3.5 MC-5

A binding the policy accepts is P-2 `PASS` and P-3 `PASS`. A binding whose key is outside the stated anchors is P-2 `PASS` and P-3 `FAIL`. A binding that fails is P-2 `FAIL`. The two results stay independent. C-AUT-3 is M3 and is outside this pair. The three SRS cases are those three results. C-TRS-2 already records that the vector catalog has no row for the untrusted-signer case. Adding one remains a catalog follow-on.

### 3.6 MC-6

The profile and the scope declaration are the precondition. The claims are C-CMP-1 and C-CMP-2. The minimum is five test cases. The four scenario names are the SRS names. This annex does not invent a fifth scenario name.

| SRS scenario name | Where it already lives |
|-------------------|------------------------|
| scope-complete | Completeness claim level Scope-complete. The verdict `complete` is the completeness draft §4.3, and it uses the declaration's expected-class list. A class the profile requires and the list omits stays completeness open item OI-2. |
| incomplete-documented | Verdict `incomplete_documented`. The claim level Scope-complete with documented gaps also requires a recorded reason. A gap with no reason keeps the verdict and does not receive that level. That package stays completeness open item OI-9. |
| incomplete-undocumented | Verdict `incomplete_undocumented`. That token is a verdict. It is not one of the four claim levels. |
| excluded-evidence | State `excluded`. C-CMP-2 says that state, by itself, does not make the P-5 result `INCOMPLETE`. A package whose expected classes are only `excluded` or `disposed` has no assigned verdict. That case stays completeness open item OI-7. This annex does not add a fifth verdict. |

SRS §10.1 says "missing." The claims use the seven codes and have no state by that name. An expected class that is neither `present` nor `redacted` is `INCOMPLETE` under C-CMP-1 and C-CMP-2 when the code is `expected_not_captured`, `unavailable`, or `arrived_late`.

### 3.7 MC-7

The capability is listed. The minimum is three test cases with ordering violations and timestamp anomalies. C-TMP-1 and C-LOG-1 stay at M3. An M2 verification reports both P-6 aspects `NOT_EVALUATED`. These cases do not move either claim to M2. Ordering for `adep.profile.pa.basic.v0` is the PA profile §4. An ordering flag does not change a completeness verdict. This annex does not set a duration for "shortly after," and it does not drop a named ordering pair.

### 3.8 MC-8

The claims are C-CMP-1 and C-CMP-2. A redacted class stays `redacted`. The four SRS cases are full disclosure, partial redaction, full redaction (metadata only), and the case that must fail. SRS §10.1 names `missing` as the third state and requires failure when a redacted element is reported as missing. This annex uses C-CMP-2: reporting a redacted class as `expected_not_captured` fails that claim. It does not add a state named missing. Disclosure-profile conformance is the privacy boundary in the assurance contract §8. C-DSC-1 and C-DSC-2 remain assurance contract open item OI-7.

### 3.9 MC-9

This row has no claim in the set. The independence level Independently verified is the assurance contract §7.3. A level does not change a property result. Verifier agreement was v0.1 C-VER-1, which remains assurance contract open item OI-7. The minimum is two test cases, run by the implementation and by the clean-room verifier, compared for agreement. The clean-room requirements are the claims-policy annex §5, which restates SRS §10.2.4. This row does not write them.

### 3.10 MC-10

Export of the package with its trust anchors, schema, and profile definition is security baseline SEC-OPS-4. C-TRS-2 and C-CMP-1 require the trust policy and the scope to be stated. They do not require an export step. This row has no claim ID. The minimum is two round-trip cases: export, re-import, and re-verify.

### 3.11 MC-11

Each claim in the M2 set has failure semantics. The result body in the assurance contract §7.4 carries the machine-readable checks, failures, and warnings, and the human-readable explanation. There is no separate claim ID. Every test case that produces a failure has that output checked. This annex does not define a further result schema.

---

## 4. Excluded from M2

These capabilities are not required at M2. SRS §10.1.3 expects them at later milestones. Listing them here does not add a claim and does not move a milestone.

- Full coverage indicator reconciliation. Completeness CI-6 does not set the method or the thresholds.
- Multi-workflow profile support. Only `adep.profile.pa.basic.v0` is required.
- Advanced deterministic replay.
- Multi-tenant support.
- Full public governance and certification.
- Agentic AI evidence classes PA-EC-20 through PA-EC-24. They are defined in the PA profile §5 and are not required in M2 test coverage.

---

## 5. Residuals

Assurance contract open item OI-8 stays open. It holds MC-7 on the M3 claims, the SRS word missing on MC-6 and MC-8, and the four rows with no claim: MC-1, MC-3, MC-9, and MC-10.

Assurance contract open item OI-7 stays open. C-DSC-1, C-DSC-2, and C-VER-1 remain in that list.

Completeness open items OI-2, OI-7, and OI-9 stay open. This annex cites them from §3.6 and does not choose a representation.

---

## 6. References

- ADEP-PHASE0-SRS-v0.1 §10.1.1, §10.1.2, and §10.1.3
- Assurance contract v0.2 §6.2 through §6.9, §7.3, §7.4, §8, and open items OI-7 and OI-8
- Completeness requirements v0.2 §3 (seven state codes), §4 (four verdicts), §5 (CI-6), and §6 (four claim levels)
- PA profile `adep.profile.pa.basic.v0` §3, §4, §5, and §6
- Security baseline v0.1 SEC-OPS-4
- Conformance claims and assessment policy annex §5 (clean-room reference verifier)

---

*End of annex draft through W3-T07 — ADEP-WI1-M2-v0. Attached as Annex A (W3-T09).*
