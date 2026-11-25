# Open ADEP Conformance Claims and Assessment Policy Annex

**Document Identifier:** ADEP-WI1-POL-v0  
**Status:** DRAFT — attached as Annex B (W3-T09)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §10.2  
**Parent contract:** ADEP-WI1-AC-v0.2 Annex B  
**Author:** LEAD (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This file is the drafting source for Annex B of `assurance-contract-v02-draft.md`. The attached copy uses section numbers B.1 through B.7. The numbers in this file are the drafting numbers. The M2 capability list is Annex A.

**Inputs:** SRS §10.2.1, §10.2.2, §10.2.3, and §10.2.4; assurance contract v0.2 §5.1, §5.2, §5.3, and open item OI-7; M2 conformance profile annex §3.9 (MC-9).

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1-draft.1 | 2026-10-25 | LEAD | W3-T08. Four subsections. Permissible-claim sentence with named slots. No claim added to the contract. |
| 0.1-draft.2 | 2026-10-25 | LEAD | W3-T09. Attached as Annex B of the assurance contract. No subsection changed. |

---

## 1. Rules

Normative for the four subsections below. This is SRS §10.2.

1. The seven concepts in §2 stay distinct.
2. After a published test suite is passed, the permitted conformance claim is the sentence in §3. The five statements in §3.2 are not permitted on that basis alone.
3. §4 states the four assessment questions. It does not name assessors, a validity-period length, or a publication venue.
4. §5 states the four clean-room requirements. It does not build the verifier, and it does not add C-VER-1 as a claim. C-VER-1 remains assurance contract open item OI-7.
5. MC-9 in the M2 annex remains the agreement baseline named in §5.
6. The attached copy is Annex B of the assurance contract. This file keeps the drafting section numbers.

---

## 2. Separation of concerns

The following are distinct and shall not be conflated. This is SRS §10.2.1.

| Concept | Definition | Who provides it |
|---------|------------|-----------------|
| Normative specification | What Open ADEP requires. | Open ADEP specification documents. |
| Implementation | Software that aims to satisfy the specification. | Any vendor. The SRS example is DecisionTrace. This row does not make that example the only implementation. |
| Conformance test suite | Published test vectors and expected results. | The Open ADEP project, maintained independently of any implementation. |
| Verifier | Software that checks packages against the specification. | Any party. At least one is the clean-room reference verifier in §5. |
| Internal test results | Results of running the test suite against one's own implementation. | The implementation vendor. |
| Independent verification | Results of running an independent verifier against the implementation's output. | An independent party or tool. |
| Independent assessment | An expert evaluation of the implementation's conformance, security, and operational characteristics. | An independent assessor. |

Passing the test suite is an internal test result, or a suite run. It is not independent assessment. Agreement with the clean-room verifier is independent verification under MC-9. That agreement is not independent assessment, and it is not a property result. The independence level Independently verified is the assurance contract §7.3. A level does not change P-1 through P-6.

---

## 3. Permissible conformance claims

An implementation may make the following claim after passing the published test suite. This is SRS §10.2.2. The sentence is the template. The four slots are named. No implementation name, implementation version, or suite version is filled in.

> "[Implementation name] version [implementation version] passed the published Open ADEP conformance test suite version [suite version] for profile [profile], subject to the test suite's stated scope and limitations."

| Slot | What it holds |
|------|----------------|
| Implementation name | The name of the implementation that passed the suite. |
| Implementation version | The version of that implementation. SRS writes this slot as X. |
| Suite version | The version of the published Open ADEP conformance test suite. SRS writes this slot as Y. |
| Profile | The workflow profile the suite run covers. For an M2 run against the prior-authorization profile, the identifier is `adep.profile.pa.basic.v0`. |

### 3.2 Prohibited on the basis of the suite alone

An implementation shall not claim any of the following solely because it passed the test suite:

- Independent certification.
- Legal admissibility of evidence packages.
- HIPAA compliance.
- Detection of every possible omission.
- Equivalence to independent assessment.

HIPAA compliance, claimed for Open ADEP itself, is non-goal NG-3 in the assurance contract §5.3. Detection of every possible omission is the limit in NG-2, assurance contract §5.2: P-5 is completeness relative to a declared scope. Legal compliance of the underlying decision is non-goal NG-1, assurance contract §5.1. Legal admissibility of evidence packages stays its own prohibited claim. This section does not collapse that claim into NG-1.

---

## 4. Path to independent assessment

The assessment policy defines the four items below. This is SRS §10.2.3. Each item uses the scope the SRS states.

1. **Who can assess.** A qualified assessor is independent of the vendor and has relevant expertise. The SRS does not name assessors. This annex does not list them. That gap is open item OI-1.
2. **What is assessed.** The scope is conformance test results, security review, and operational review.
3. **How results are published.** Publication uses assessment reports, validity periods, and public disclosure. The SRS does not state a validity-period length. This annex does not set one. That gap is open item OI-2. The SRS does not name a publication venue. This annex does not name one. That gap is open item OI-3.
4. **How other vendors are tested.** Other implementations must be testable using only the published specification, the test suite, and public trust anchors, without requiring access to DecisionTrace's proprietary internals.

---

## 5. Clean-room reference verifier

A clean-room reference verifier is developed independently of DecisionTrace. This is SRS §10.2.4. This annex states the requirement. It does not produce the verifier.

The verifier:

1. Is implemented from the published specification, without reference to DecisionTrace source code.
2. Is open-source, or at minimum source-available.
3. Verifies all M2 conformance capabilities. Those capabilities are the M2 annex §3, which restates SRS §10.1.2.
4. Serves as the agreement baseline for MC-9. The capability row is the M2 annex §3.9. The minimum there is two test cases, run by the implementation and by this verifier, compared for agreement.

Verifier agreement was v0.1 C-VER-1. That identifier remains assurance contract open item OI-7. This section does not give it a claim row.

---

## 6. Open items

| ID | Issue | Where it stands |
|----|-------|-----------------|
| OI-1 | SRS §10.2.3 requires independence from the vendor and relevant expertise, and does not name assessors. | §4 item 1. No assessor list is added. |
| OI-2 | SRS §10.2.3 includes validity periods and does not state a length. | §4 item 3. No length is set. |
| OI-3 | SRS §10.2.3 includes public disclosure and does not name a venue. | §4 item 3. No venue is named. |

Assurance contract open item OI-7 stays open. C-VER-1 has no row in this annex.

---

## 7. References

- ADEP-PHASE0-SRS-v0.1 §10.2.1, §10.2.2, §10.2.3, and §10.2.4
- Assurance contract v0.2 §5.1 (NG-1), §5.2 (NG-2), §5.3 (NG-3), §7.3 (independence levels), and open item OI-7
- M2 conformance profile annex §3 (MC-1 through MC-11) and §3.9 (MC-9)

---

*End of annex draft through W3-T08 — ADEP-WI1-POL-v0. Attached as Annex B (W3-T09).*
