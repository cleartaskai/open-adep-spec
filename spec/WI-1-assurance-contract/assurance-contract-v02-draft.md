# Open ADEP Evidence Assurance Contract v0.2

**Document Identifier:** ADEP-WI1-AC-v0.2  
**Status:** DRAFT — first assembly (W2-T06), annexes attached (W3-T09)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §5.2, §5.3, §5.4, §5.5, §5.6, §5.7, §10.1, §10.2  
**Author:** LEAD (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This is the assembled assurance-contract draft. It contains the evidence-property taxonomy, the reclassification of two former property candidates, non-goals NG-1 through NG-4, twelve claims on the seven-field template, the milestone map, the verification context, and the claim boundaries. Annex A is the M2 conformance profile. Annex B is the claims and assessment policy. Both are part of this document. The remaining v0.1 claim rows are open item OI-7. Open item OI-8 stays open.

**Inputs:** SRS §5.2, §5.3, §5.4, §5.5, §5.6, §5.7, §10.1, §10.2; assurance contract v0.1 §2, §3, §4, §6, §7, and §8; verification spec §53; W1-T09 annotation; reconciliation register REC-022, REC-023, and REC-027.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.2-draft.1 | 2026-10-22 | LEAD | W1-T14. Six properties, each with a formal definition, an establishes statement, and a does-not-establish statement. |
| 0.2-draft.2 | 2026-10-22 | LEAD | W1-T19. Reclassification of substantive correctness and verification independence. Non-goals NG-1 through NG-4. |
| 0.2-draft.3 | 2026-10-22 | LEAD | W1-T20. Seven-field claim template. Four example claims for P-1 and P-2. |
| 0.2-draft.4 | 2026-10-22 | LEAD | W1-T21 cross-reference. C-AUT-2 failure semantics point at the trust-model separation row. |
| 0.2-draft.5 | 2026-10-22 | LEAD | W1-T22 cross-reference. Signature scopes are cited from the trust-model draft §5. |
| 0.2-draft.6 | 2026-10-23 | LEAD | W1-T26. Verification context. Six fields and four independence levels. |
| 0.2-draft.7 | 2026-10-23 | LEAD | W1-T27. Claim boundaries. Five dimensions, each with a positive and a negative column. |
| 0.2-draft.8 | 2026-10-23 | LEAD | W2-T01. Two claims each for P-3, P-4, P-5, and P-6. Twelve claims in total. |
| 0.2-draft.9 | 2026-10-23 | LEAD | W2-T02. The twelve claims grouped by milestone. The cumulative M2 set mapped onto MC-1 through MC-11. |
| 0.2-draft.10 | 2026-10-23 | LEAD | W2-T04 cross-reference. P-5 state definitions point at the completeness draft §3. |
| 0.2-draft.11 | 2026-10-24 | LEAD | W2-T06. First assembly. Section map, and cross-references aligned to the sections in this file. |
| 0.2-draft.12 | 2026-10-24 | LEAD | W2-T09 cross-reference. P-1 canonicalization points at security baseline SEC-CRYPTO-6. |
| 0.2-draft.13 | 2026-10-24 | LEAD | W2-T14 cross-reference. P-5 coverage-indicator rules point at the completeness draft §5. |
| 0.2-draft.14 | 2026-10-24 | LEAD | W2-T15 cross-reference. Qualified completeness claims point at the completeness draft §6 and §7. |
| 0.2-draft.15 | 2026-10-24 | LEAD | W2-T16 cross-reference. P-4 import rules point at security baseline SEC-PROV-1 through SEC-PROV-3. |
| 0.2-draft.16 | 2026-10-24 | LEAD | W2-T17 cross-reference. P-6 source, assumption, and anchoring rules point at security baseline SEC-TEMP-1 through SEC-TEMP-4. |
| 0.2-draft.17 | 2026-10-24 | LEAD | W2-T18 cross-reference. MC-10 export points at security baseline SEC-OPS-4. No claim is added. |
| 0.2-draft.18 | 2026-10-24 | LEAD | W2-T22 cross-reference. Data minimization points at security baseline PRV-MIN-1 through PRV-MIN-3. No claim is added. |
| 0.2-draft.19 | 2026-10-24 | LEAD | W2-T23 cross-reference. Disclosure profiles point at security baseline PRV-DSC-1 through PRV-DSC-4. No claim is added. |
| 0.2-draft.20 | 2026-10-24 | LEAD | W2-T24 cross-reference. Identifier pseudonymization points at security baseline PRV-ID-1 through PRV-ID-3. No claim is added. |
| 0.2-draft.21 | 2026-10-24 | LEAD | W2-T25 cross-reference. Boundary crossing points at security baseline PRV-BND-1 through PRV-BND-3. CD-4 is cited and left unaffirmed. No claim is added. |
| 0.2-draft.22 | 2026-10-24 | ARCH + LEAD | W2-T29. Cross-reference check against the trust model. No claim or section number changed. The report is ADEP-XREF-WI1-WI3-v0.1. |
| 0.2-draft.23 | 2026-10-25 | LEAD | W3-T07 cross-reference. The M2 annex is drafted and not attached. No claim is added. |
| 0.2-draft.24 | 2026-10-25 | LEAD | W3-T08 cross-reference. The claims-policy annex is drafted and not attached. No claim is added. |
| 0.2-draft.25 | 2026-10-25 | LEAD | W3-T09. Annex A and Annex B are part of this document. Table of contents added. No claim is added. Sections §2 through §8 are unchanged apart from the two annex pointers in §6 and §6.9. |

---

## Contents

- [1. Purpose](#1-purpose)
- [2. Evidence property taxonomy](#2-evidence-property-taxonomy)
- [3. Mapping from v0.1 dimensions](#3-mapping-from-v01-dimensions)
- [4. Properties reclassified](#4-properties-reclassified)
- [5. Non-goals](#5-non-goals)
- [6. Claim structure](#6-claim-structure)
- [7. Verification context](#7-verification-context)
- [8. Claim boundaries](#8-claim-boundaries)
- [9. Open issues](#9-open-issues)
- [10. References](#10-references)
- [Annex A. M2 Conformance Profile](#annex-a-m2-conformance-profile)
- [A.1 Objective](#a1-objective)
- [A.2 Rules](#a2-rules)
- [A.3 Minimum conformance capabilities](#a3-minimum-conformance-capabilities)
- [A.4 Excluded from M2](#a4-excluded-from-m2)
- [A.5 Residuals](#a5-residuals)
- [A.6 References](#a6-references)
- [Annex B. Conformance Claims and Assessment Policy](#annex-b-conformance-claims-and-assessment-policy)
- [B.1 Rules](#b1-rules)
- [B.2 Separation of concerns](#b2-separation-of-concerns)
- [B.3 Permissible conformance claims](#b3-permissible-conformance-claims)
- [B.4 Path to independent assessment](#b4-path-to-independent-assessment)
- [B.5 Clean-room reference verifier](#b5-clean-room-reference-verifier)
- [B.6 Open items](#b6-open-items)
- [B.7 References](#b7-references)

---

## 1. Purpose

This document states what an Open ADEP verification result establishes. It is normative except where a section says it is informative. The v0.1 mapping in §3 and the capability alignment in §6.9 are informative.

The contract is deployment-neutral. A property does not name a vendor, a product, or a deployment location. What a particular signature attests is trust model v0.2 §5. This contract cites that section and does not restate the five signature scopes.

| Section | What it contains |
|---------|------------------|
| §2 | Six evidence properties, P-1 through P-6. |
| §3 | How v0.1 §3 maps onto those properties. Informative. |
| §4 | Substantive correctness and verification independence, reclassified. |
| §5 | Non-goals NG-1 through NG-4. |
| §6 | Twelve claims, the milestone each one first requires, and the M2 set against MC-1 through MC-11. |
| §7 | Verification context. Six fields and four independence levels. |
| §8 | Five claim boundaries. |
| §9 | Pointers to text in this draft, and the two residuals this draft leaves open. |
| §10 | References. |
| Annex A | M2 conformance profile. Eleven capabilities, test minimums, and the excluded list. |
| Annex B | Claims and assessment policy. Separation of concerns, the permissible claim, the assessment path, and the clean-room verifier. |

---

## 2. Evidence property taxonomy

### 2.1 Normative rules

1. The assurance contract defines exactly six evidence properties: P-1 through P-6.
2. Each property has a formal definition, a statement of what Open ADEP establishes, and a statement of what Open ADEP does not establish.
3. No property implies another. In particular, integrity does not imply completeness, and neither implies that recorded content is true.
4. A verifier reports each property that is in scope on its own terms. The result tokens are §6.1.

### 2.2 Summary

| ID | Property | What Open ADEP establishes | What Open ADEP does not establish |
|----|----------|----------------------------|-----------------------------------|
| P-1 | Integrity | Whether protected content passes the specified integrity checks (hash verification, structural validation). | That the content is truthful, accurate, or free from upstream errors. |
| P-2 | Authenticity | What source or identity a record can be associated with, under stated cryptographic assumptions. The binding between a payload and a signing operation. | That the signing identity is authorized, trusted, or acting in good faith. See P-3. |
| P-3 | Signer trust | Whether the signing identity and relevant trust conditions (key validity, role authorization, certificate chain) are accepted under a stated trust policy. | That the signer's internal processes were correct or that the signer was not compromised. |
| P-4 | Provenance | Where evidence originated, through which intermediaries it passed, and how it was transformed. The chain of custody from production to current state. | That the originating system was itself trustworthy or that no undisclosed intermediaries existed. |
| P-5 | Completeness | Whether expected evidence is present relative to a declared and testable scope, using defined evidence states and coverage indicators. | That every relevant real-world event was captured. Unobservable omissions may remain undetected. |
| P-6 | Temporal assurance | What can be established about event ordering, timestamp accuracy, and temporal relationships, given stated assumptions about clock sources and anchoring. | That timestamps are absolutely accurate or that no events occurred between recorded timestamps. |

### 2.3 P-1 Integrity

**Formal definition.** Integrity is the outcome of the specified checks that protected content is unchanged since it was signed. The checks are hash verification of the protected bytes and structural validation of the protected structure. Protected content includes committed elements, event headers, and chain links.

**Establishes.** Whether that protected content passes those checks.

**Does not establish.** That the content is truthful, accurate, or free from upstream errors. It also does not establish that nothing was omitted (P-5), or which identity the signing operation binds (P-2).

**Relationship to v0.1.** Revises v0.1 §3.1. The establishes statement adds structural validation to hash verification. The negative scope is unchanged in substance.

**Informative.** The checks are comparable only when the producer and the verifier apply the same canonical serialization. That serialization is SEC-CRYPTO-6 in the security baseline. For the baseline version that names it, the algorithm is RFC 8785.

### 2.4 P-2 Authenticity

**Formal definition.** Authenticity is the binding between a payload and the signing operation that covers it, under stated cryptographic assumptions. It answers which key performed that operation, and therefore which source or identity the record can be associated with on the strength of that binding alone.

**Establishes.** What source or identity a record can be associated with, under those assumptions, and that the payload is bound to that signing operation.

**Does not establish.** That the signing identity is authorized, trusted, or acting in good faith. Those questions are P-3. It also does not establish that a person or system named inside the payload performed the action the payload describes. That question is P-4.

**Relationship to v0.1.** Splits v0.1 §3.2. v0.1 treated "valid signatures from keys listed in the trust anchors and valid at the relevant time" as authenticity. Key validity, trust-anchor membership, and role authorization move to P-3. The fixed meanings of particular signatures are trust model v0.2 §5. They are not part of this definition.

### 2.5 P-3 Signer trust

**Formal definition.** Signer trust is the acceptance, under a stated trust policy, of the signing identity together with the trust conditions that policy names. Those conditions include key validity at the relevant time, role authorization, and the certificate chain or other trust-anchor path the policy requires.

**Establishes.** Whether that identity and those conditions are accepted under the stated trust policy.

**Does not establish.** That the signer's internal processes were correct, or that the signer was not compromised. A policy may require more than one signature. What each signature attests is trust model v0.2 §5, not this property.

**Relationship to v0.1.** New property. v0.1 had no separate signer-trust property; §3.2 folded it into authenticity. This is the split required by SRS §5.2.

### 2.6 P-4 Provenance

**Formal definition.** Provenance is the chain of custody of an evidence record from production to its current state: where it originated, through which intermediaries it passed, and how it was transformed, as declared in the record and as resolved to artifacts supplied with it.

**Establishes.** That chain of custody, to the extent the record declares it and the supplied artifacts resolve. A declaration may name a source type and an actor or component identifier. A reference to an input, a policy, or a model may resolve by content hash to a supplied artifact.

**Does not establish.** That the originating system was itself trustworthy, or that no undisclosed intermediaries existed. It also does not establish that a declared identity is genuine beyond the declaration, or that a referenced policy or model was appropriate, correct, or lawfully applied.

**Relationship to v0.1.** Keeps v0.1 §3.3. Wording is aligned to SRS §5.2. The hash-resolution behavior from v0.1 remains part of what provenance establishes. Import provenance, the `unverified_import` label, and the record of tools used in production are security baseline SEC-PROV-1, SEC-PROV-2, and SEC-PROV-3. Those requirements do not add a claim to this contract.

### 2.7 P-5 Completeness

**Formal definition.** Completeness is whether the evidence expected by a declared and testable scope is present. Presence is reported with the evidence states and coverage indicators defined for that scope. The scope is the workflow profile together with the scope declaration, not an implicit claim about the world outside that declaration.

**Establishes.** Whether expected evidence is present relative to that scope, using those states and coverage indicators.

**Does not establish.** That every relevant real-world event was captured. An omission that no capture point observed can remain undetected. Completeness relative to one scope says nothing about completeness relative to another scope. It also does not establish that the scope declaration lists every event that occurred.

**Relationship to v0.1.** Keeps v0.1 §3.6, and adds coverage indicators, which v0.1 did not name. The state codes are the completeness draft §3. The coverage-indicator rules are the completeness draft §5. Qualified completeness claims are the completeness draft §6. How an integrity result sits beside such a claim is §7 of that draft. Those sections do not add a claim to this contract. v0.1 used `PRESENT`, `REDACTED`, `MISSING`, and `UNAVAILABLE`. The completeness draft §3 publishes the seven SRS §6.4 codes (`present`, `redacted`, `excluded`, `expected_not_captured`, `unavailable`, `arrived_late`, `disposed`). This property uses that set.

### 2.8 P-6 Temporal assurance

**Formal definition.** Temporal assurance is what can be established about event ordering, timestamp accuracy, and temporal relationships, given the clock sources and anchoring assumptions that are stated for the verification.

**Establishes.** Those ordering, accuracy, and relationship facts that follow from the stated assumptions. Where the assumptions include an anchoring checkpoint and a lower bound such as `not_before_checkpoint`, an event can be placed no later than that checkpoint and no earlier than that bound. Where they include a tolerance Δ, an event anchored later than its claimed time plus Δ is distinguishable from an event inside that tolerance. Where they include an append-only log, the checkpoints presented to the verifier can be checked for consistency with one history. That log check is part of P-6. It is not a seventh property.

**Does not establish.** That timestamps are absolutely accurate, or that no events occurred between recorded timestamps. A producer-supplied `claimed_time`, taken alone, is not timestamp accuracy. Ordering finer than the anchor interval is not established. That every relying party was shown the same history depends on an independent log witness. That split is trust model v0.2 §4, row C-INT-4. When the witness is in scope, the result is still reported under P-6.

**Relationship to v0.1.** Renames v0.1 §3.4 from "temporal integrity" to "temporal assurance," and adds event ordering and temporal relationships to the establishes statement. Folds v0.1 §3.5 (log consistency / non-equivocation) into this property as the log aspect above. v0.1 §3.5 is not an independent property. Timestamp source identification, stated accuracy assumptions, external anchoring where an anchor is available, and the recording of administrative and configuration changes that affect capture or signing are security baseline SEC-TEMP-1 through SEC-TEMP-4. Those requirements do not add a claim, and they do not move C-TMP-1 or C-LOG-1 off M3.

---

## 3. Mapping from v0.1 dimensions

Informative. This mapping is how the six properties relate to assurance contract v0.1 §3. Substantive correctness and verification independence are reclassified in §4. The contract non-goals are §5.

| v0.1 §3 | In this taxonomy |
|---------|------------------|
| 3.1 Integrity | P-1 |
| 3.2 Authenticity, payload-to-signature binding | P-2 |
| 3.2 Authenticity, trust anchors, key validity, authorization | P-3 |
| 3.3 Provenance | P-4 |
| 3.6 Completeness | P-5 |
| 3.4 Temporal integrity | P-6 |
| 3.5 Log consistency | An aspect of P-6, not its own property |
| 3.7 Disclosure conformance | Not a property. A verification check whose normative requirements are in the privacy baseline (WI-4). |
| 3.8 Reconstruction | Not a property. A reporting output. |
| 3.9 Reporting rules | Not a property. The result tokens are §6.1. The result body is §7.4. |

---

## 4. Properties reclassified

Normative. These two items are not evidence properties. Each one has a rationale.

| Item | Reclassification | Rationale |
|------|------------------|-----------|
| Substantive correctness | Non-goal NG-1 (§5) | A statement whose content is that Open ADEP does not establish it is a non-goal. Placing it in the property list makes it look like a result a verifier can return. v0.1 §8 already said that a package does not prove the decision was correct. That statement moves here, as NG-1, and stays out of P-1 through P-6. |
| Verification independence | A verification-context attribute, not a property of the evidence | Independence describes how the check was performed: with or without reliance on the producer's systems. It is not a fact about the package. The context that carries it is §7. The four levels are Self-verified, Cross-verified, Independently verified, and Independently reviewed. v0.1 §7 mixed this axis with claim-maturity labels such as Specified. Those maturity labels belong to the claims-policy annex (Annex B, SRS §10.2). |

No other candidate is added to the property list by this section. Log consistency, disclosure conformance, and reconstruction are already disposed of in §3. They are not a third and fourth reclassification under SRS §5.3.

---

## 5. Non-goals

Normative. The following are not goals of this contract. A verification result, a claim, or a public statement about Open ADEP must not be read as achieving any of them.

These four identifiers have the meanings in this section. They do not have the threat-model meanings that used the same numbers. REC-027 keeps threat-model-only statements under TM-NG-3 through TM-NG-7 in the threat model. This contract does not define that series. A sentence about the limits of recorded model reasoning cites TM-NG-6, not a fifth contract non-goal.

### 5.1 NG-1 Substantive correctness

**Non-goal.** Whether the underlying decision was clinically correct, legally compliant, or based on complete source information.

**Rationale.** A verified package must not be read as proof that a prior-authorization determination was clinically correct. Evidence integrity and decision quality are separate. v0.1 §8 already prohibits "proves the decision was correct, fair, or compliant" and points at this limit. The threat-model statement of the same limit cites this non-goal (REC-001) and does not keep a second wording.

### 5.2 NG-2 Absolute completeness

**Non-goal.** Detecting activity that was never routed to any capture point.

**Rationale.** If no instrumented system observed an event, no evidence standard can detect its absence. P-5 establishes completeness only relative to a declared scope. Coverage indicators are the completeness draft §5. They narrow the gap and do not close it. v0.1 §8 already prohibits "complete record of the decision" and requires the profile to be named.

### 5.3 NG-3 Universal HIPAA certification

**Non-goal.** Making Open ADEP itself a certification that a deployment complies with HIPAA or any other specific privacy regulation.

**Rationale.** Compliance depends on the deployment, the contracts, and the organizational controls around the evidence format. Those are outside this contract. v0.1 §8 already prohibits "HIPAA compliant" and "HIPAA certified" as claims about Open ADEP. This identifier is not the threat model's collusion non-goal. That statement is TM-NG-3.

### 5.4 NG-4 Cryptographic algorithm mandate

**Non-goal.** Prescribing specific cryptographic algorithms in this contract, rather than requiring stated algorithms and a way to change them.

**Rationale.** Algorithm choices have to be replaceable as practice changes. This contract requires that producer and verifier apply the same canonical serialization (P-1) and that signer trust is assessed under a stated policy (P-3). It does not name the algorithm. Which algorithms are acceptable is a requirement of the security baseline (WI-4), and that baseline is required to allow agility. This identifier is not the threat model's statement about confidentiality against the deployer. That statement is TM-NG-4.

---

## 6. Claim structure

Normative. A claim is a testable assertion about one evidence property. Claims are organized by the milestone that first requires them. M2 is the first conformance target. Which claims that target includes, and how they line up with MC-1 through MC-11, is §6.8 and §6.9. The profile annex, including its test-case counts, is Annex A.

### 6.1 Template

Every claim has these seven fields.

| Field | Rule |
|-------|------|
| Claim ID | Stable identifier. Integrity claims use `C-INT-`. Authenticity claims use `C-AUT-`. Signer trust uses `C-TRS-`, except the carried revocation claim `C-AUT-3`. Provenance uses `C-PRV-`. Completeness uses `C-CMP-`. The temporal aspect of P-6 uses `C-TMP-`. The log aspect uses `C-LOG-`. |
| Property | Exactly one of P-1 through P-6. |
| Assertion | The testable statement. It names what passes. It does not name a vendor or a product. |
| Preconditions | What must be true before the claim can be evaluated. If a precondition is absent, the result is `NOT_EVALUATED`, not `FAIL`. |
| Test method | The procedure and the published vector identifiers that demonstrate it. Vector definitions live in the threat-model catalog (REC-003). |
| Failure semantics | What a `FAIL` means, and what it does not mean. |
| Milestone | The first milestone (M1, M2, M3, …) that requires the claim. |

For P-1, P-2, and P-3 the property result is `PASS`, `FAIL`, or `NOT_EVALUATED`. P-4 uses `RESOLVED`, `UNRESOLVED`, `MISMATCH`, or `NOT_EVALUATED`. P-5 uses `COMPLETE`, `INCOMPLETE`, or `NOT_EVALUATED`. P-6 reports a time aspect and a log aspect. The time aspect is `ANCHORED`, `LATE`, `UNANCHORED`, or `INCONSISTENT`. The log aspect is `WITNESSED`, `UNWITNESSED`, or `INCONSISTENT`. Either P-6 aspect may be `NOT_EVALUATED`. These are the REC-022 tokens.

§6.2 through §6.7 are the minimum set: two claims for each property. Further v0.1 claims are open item OI-7. §6.8 groups this set by milestone. §6.9 maps it onto MC-1 through MC-11.

### 6.2 P-1 Integrity

#### C-INT-1

| Field | Value |
|-------|-------|
| Claim ID | C-INT-1 |
| Property | P-1 Integrity |
| Assertion | Any modification of a protected element, event header, or chain link after the signature that covers it is detected. Structural validation of those bytes is part of the same check. |
| Preconditions | The verifier has the protected bytes, the signature that covers them, and the canonical serialization this verification uses. |
| Test method | Recompute the integrity checks over the canonical bytes. TV-INT-01 flips one byte of a committed element and expects P-1 `FAIL`. TV-INT-03 moves a valid event onto another chain and expects P-1 `FAIL`. TV-CAN-01 (duplicate JSON keys) and TV-CAN-02 (non-canonical signed bytes) expect the structural check to reject the input. The catalog still labels these results `INTEGRITY FAIL`. That label is this claim's P-1 `FAIL`. |
| Failure semantics | `FAIL` means the protected bytes do not satisfy the hash check or the structural check. It does not mean the content was false when recorded (NG-1). It does not mean expected evidence is absent (P-5). It does not mean the signing key is unauthorized (P-3). |
| Milestone | M1 |

Carried from v0.1 C-INT-1. The assertion adds structural validation, which P-1 requires and which those canonicalization vectors already exercised.

#### C-INT-2

| Field | Value |
|-------|-------|
| Claim ID | C-INT-2 |
| Property | P-1 Integrity |
| Assertion | If protected bytes are changed and only one of the signatures that covered the previous bytes is replaced, each signature that was not replaced fails verification over the new bytes. |
| Preconditions | More than one signature covered the previous bytes, and at least one of those signatures is still present unchanged. Before M2, where a single signature is all the milestone requires, this claim is `NOT_EVALUATED`. |
| Test method | Apply TV-INT-02: modify the event and re-sign with only one of the keys. Verify the signature that was not replaced. The expected property result for this claim is P-1 `FAIL`. The catalog row currently says `AUTHENTICITY FAIL`, which is the v0.1 dimension name for that vector. Under REC-022 the unchanged signature's coverage failure is a P-1 result. Aligning the catalog label is a follow-on edit to the vector catalog, not a second claim. |
| Failure semantics | `FAIL` means a signature that this claim treats as still covering the bytes does not verify. It does not mean the replaced signature is unauthorized, and it does not mean the two signers are or are not independent parties. Whether the stated trust policy required both signatures is C-TRS-2. |
| Milestone | M2 |

Carried from v0.1 C-INT-2. The v0.1 wording named the deploying organization. This wording states the same check without a party name.

### 6.3 P-2 Authenticity

#### C-AUT-1

| Field | Value |
|-------|-------|
| Claim ID | C-AUT-1 |
| Property | P-2 Authenticity |
| Assertion | The protected payload verifies under the signature presented with it, using the cryptographic assumptions stated for that signing operation. |
| Preconditions | The payload, the signature, and the stated assumptions (including which algorithm identifiers are in scope for the binding) are available to the verifier. |
| Test method | Run signature verification over the canonical payload. TV-SIG-03 uses an unknown algorithm identifier, or `none`, and expects the binding to fail: P-2 `FAIL`. A payload that does not match the signed bytes fails the same way. |
| Failure semantics | `FAIL` means this payload is not bound to this signing operation under the stated assumptions. It does not mean the key is revoked, absent from a trust anchor, or outside a role. Those are P-3. v0.1 C-AUT-1 said "the deploying organization's registered key." Registration and key status are not this claim. |
| Milestone | M1 |

#### C-AUT-2

| Field | Value |
|-------|-------|
| Claim ID | C-AUT-2 |
| Property | P-2 Authenticity |
| Assertion | When the claim's signing set lists more than one signature, each listed signature binds the same protected payload. |
| Preconditions | The signing set is stated, and each listed signature value is either present or recorded as absent. The set is the one the milestone requires. At M1 a single signature is sufficient for C-AUT-1, and this claim is `NOT_EVALUATED`. |
| Test method | Verify each signature in the set over the same canonical payload. TV-SIG-01 removes one signature in the set and expects P-2 `FAIL` for that missing binding. TV-INT-02 replaces one signature after a modification and expects P-2 `FAIL` for any listed signature that no longer binds the new payload. |
| Failure semantics | `FAIL` means at least one signature in the set does not bind this payload. It does not mean the signers are authorized (P-3), and it does not mean the signers are operationally independent. v0.1 C-AUT-2 said the deploying organization and DecisionTrace must both sign and that neither can produce a valid event alone. The binding half is this claim. Whether the stated policy requires both keys is C-TRS-2. Whether one party holds both keys is trust model v0.2 §4, row C-AUT-2 (two holders of R-2). |
| Milestone | M2 |

---

### 6.4 P-3 Signer trust

P-3 results are `PASS`, `FAIL`, or `NOT_EVALUATED`. Trust model v0.2 §4, row C-TRS-1, is the separation between R-10 and R-2. It is not one of these claims. A key can be `PASS` under a stated policy while that separation is unmet.

#### C-TRS-2

| Field | Value |
|-------|-------|
| Claim ID | C-TRS-2 |
| Property | P-3 Signer trust |
| Assertion | The key named by the signature is accepted under the stated trust policy: it is in the stated trust anchors, it is valid at the time the policy uses, and it is authorized for the signature type's role. |
| Preconditions | The trust policy is stated, including its anchors and the role the signature type requires. The signature names a key identifier. If the policy is not stated, this claim is `NOT_EVALUATED`. |
| Test method | Evaluate the stated policy against that key identifier. A signature that binds under C-AUT-1 and whose key is outside the stated anchors is P-3 `FAIL`. The vector catalog has no row whose construction is that case. Adding one is a catalog follow-on, not a second claim. |
| Failure semantics | `FAIL` means the stated policy does not accept this key. It does not mean the payload fails to bind (P-2). It does not mean the signer and the trust-anchor publisher are different parties. That separation is trust model v0.2 §4, row C-TRS-1. v0.1 C-AUT-1 put registration inside authenticity. Registration is this claim. |
| Milestone | M1 |

#### C-AUT-3

| Field | Value |
|-------|-------|
| Claim ID | C-AUT-3 |
| Property | P-3 Signer trust |
| Assertion | A signature made after the recorded revocation of its key is rejected. |
| Preconditions | A revocation record for that key is available to the verifier, and the record states the revocation time. If no revocation record is in scope, this claim is `NOT_EVALUATED`. Before M3 this claim is `NOT_EVALUATED`. |
| Test method | TV-SIG-02 signs an event after a logged revocation and expects rejection. The property result is P-3 `FAIL`. The catalog row says `AUTHENTICITY FAIL`. That label is the v0.1 dimension name. Aligning it is a catalog follow-on. |
| Failure semantics | `FAIL` means the signature's time is after the recorded revocation. It does not mean the payload was altered (P-1). It does not state the effect on evidence signed before revocation. That effect is SEC-CRYPTO-2 in the security baseline. |
| Milestone | M3 |

Carried from v0.1 C-AUT-3. The property is P-3, as open item OI-7 already recorded.

### 6.5 P-4 Provenance

P-4 results are `RESOLVED`, `UNRESOLVED`, `MISMATCH`, or `NOT_EVALUATED`. Trust model v0.2 §4, row C-PRV-1, is the R-1 and R-7 separation. The claim below keeps the v0.1 sentence, which is a declaration.

#### C-PRV-1

| Field | Value |
|-------|-------|
| Claim ID | C-PRV-1 |
| Property | P-4 Provenance |
| Assertion | Each event in scope identifies its source type and the declared actor or component. |
| Preconditions | The event is available to the verifier. A missing source type or a missing declared actor is not a missing precondition. It is an `UNRESOLVED` result. |
| Test method | Read the source-type field and the declared actor or component. TV-REC-01 carries an AI-rationale event that names the recording component. A declaration that names both is `RESOLVED`. The catalog has no vector whose only defect is a blank source type. |
| Failure semantics | `UNRESOLVED` means the source type or the declared actor is absent. `RESOLVED` does not mean the named actor is the party that holds a signing key (P-2, P-3), and it does not mean the declaration was checked by a party other than the producer. That independence is trust model v0.2 §4, row C-PRV-1. |
| Milestone | M1 |

#### C-PRV-2

| Field | Value |
|-------|-------|
| Claim ID | C-PRV-2 |
| Property | P-4 Provenance |
| Assertion | Each policy reference and each model reference in scope resolves by content hash to an artifact supplied with the package. |
| Preconditions | The event cites at least one such reference. If it cites none, this claim is `NOT_EVALUATED`. If it cites one and the artifact is not supplied, the result is `UNRESOLVED`, not `MISMATCH`. |
| Test method | Compare the reference hash with the hash of the supplied artifact. TV-POL-01 (policy) and TV-POL-02 (model) expect P-4 `MISMATCH`. The catalog says `PROVENANCE MISMATCH`. That is this result. |
| Failure semantics | `MISMATCH` means the supplied artifact is not the bytes the reference names. It does not mean the policy or the model was appropriate, correct, or lawfully applied (NG-1). |
| Milestone | M1 |

### 6.6 P-5 Completeness

P-5 results are `COMPLETE`, `INCOMPLETE`, or `NOT_EVALUATED`. The state codes are the seven in SRS §6.4: `present`, `redacted`, `excluded`, `expected_not_captured`, `unavailable`, `arrived_late`, and `disposed`. The definitions are the completeness draft §3. These claims use the codes. They do not use a state named missing.

#### C-CMP-1

| Field | Value |
|-------|-------|
| Claim ID | C-CMP-1 |
| Property | P-5 Completeness |
| Assertion | Every evidence class the stated scope expects has exactly one of the seven states. The result is `COMPLETE` only when every expected class is `present` or `redacted`. |
| Preconditions | The workflow profile and the scope declaration are stated. If either is absent, this claim is `NOT_EVALUATED`. |
| Test method | Compare the expected classes with the reported states. TV-OMI-02 removes tail events and supplies no seal. The expected result is P-5 `INCOMPLETE`. The catalog says `COMPLETENESS INCOMPLETE`. |
| Failure semantics | `INCOMPLETE` means at least one expected class is not `present` or `redacted`. It does not mean protected bytes were altered (P-1). It does not mean an event outside the declared scope occurred (NG-2). |
| Milestone | M1 |

#### C-CMP-2

| Field | Value |
|-------|-------|
| Claim ID | C-CMP-2 |
| Property | P-5 Completeness |
| Assertion | `excluded` does not, by itself, make the result `INCOMPLETE`. `expected_not_captured` and `unavailable` do. `redacted` is not reported as `expected_not_captured`. `arrived_late` is `INCOMPLETE` for the sealed scope. |
| Preconditions | C-CMP-1's preconditions, and each expected class already has one of the seven states. |
| Test method | TV-REC-02 has a profile-required event absent and a redacted element. The absent class is a gap: P-5 `INCOMPLETE`. The redacted element stays `redacted`. A class the scope marks `excluded` is recorded as excluded and does not, alone, make the result `INCOMPLETE`. |
| Failure semantics | `INCOMPLETE` under this claim means a gap state, or `arrived_late`, on a class the scope expected. An `excluded` class is outside that scope. Disposal (`disposed`) confirms a declared disposal record and does not restore the original content. |
| Milestone | M1 |

### 6.7 P-6 Temporal assurance

P-6 has a time aspect and a log aspect. Each may be `NOT_EVALUATED`. Before M3 both claims are `NOT_EVALUATED`. v0.1 C-TMP-2, C-TMP-3, and C-LOG-2 are folded into these two claims rather than given their own rows.

#### C-TMP-1

| Field | Value |
|-------|-------|
| Claim ID | C-TMP-1 |
| Property | P-6 Temporal assurance, time aspect |
| Assertion | For each event in scope, the time aspect is `ANCHORED` when an inclusion proof places the event no later than its anchoring checkpoint and, where a tolerance Δ is stated, no later than `claimed_time` plus Δ. |
| Preconditions | An anchoring checkpoint is in scope. If none is in scope, the time aspect is `NOT_EVALUATED`. `claimed_time` alone is not an anchor. |
| Test method | TV-TMP-03 omits the inclusion proof and expects `UNANCHORED`. TV-TMP-01 anchors later than `claimed_time` plus Δ and expects `LATE`. TV-TMP-02 sets `not_before_checkpoint` later than the anchoring checkpoint and expects `INCONSISTENT`. |
| Failure semantics | `UNANCHORED` means no inclusion proof. `LATE` means the anchor is after the stated tolerance. `INCONSISTENT` means the lower bound is after the anchor. None of these means the event's content is false (NG-1), and none of them is the log aspect. |
| Milestone | M3 |

Carried from v0.1 C-TMP-1, C-TMP-2, and C-TMP-3. One claim reports the time-aspect values from REC-022.

#### C-LOG-1

| Field | Value |
|-------|-------|
| Claim ID | C-LOG-1 |
| Property | P-6 Temporal assurance, log aspect |
| Assertion | The checkpoints presented to this verifier are either consistent with one append-only history or they are not. The log aspect is `WITNESSED` when they are consistent and carry an independent witness cosignature, `UNWITNESSED` when they are consistent and that cosignature is absent, and `INCONSISTENT` when they are not one history. |
| Preconditions | At least one checkpoint is presented. If the verification scope includes no log, the log aspect is `NOT_EVALUATED`. |
| Test method | TV-LOG-01 presents a checkpoint inconsistent with a witness-cosigned checkpoint and expects `INCONSISTENT`. TV-LOG-02 presents a checkpoint with no independent cosignature and expects `UNWITNESSED`. The catalog says `LOG INCONSISTENT` and `LOG UNWITNESSED`. Those are this claim's log-aspect results. |
| Failure semantics | `INCONSISTENT` means the presented checkpoints are not one append-only history. `UNWITNESSED` means this verifier's consistent history has no independent cosignature. It does not mean a second verifier was shown a different history. v0.1 C-LOG-2 stated that second fact. It is not a separate row here. Trust model v0.2 §4, row C-INT-4, still requires R-5 and R-6 to be different parties before a witness result is available. |
| Milestone | M3 |

### 6.8 Milestones

Normative for the twelve claims in §6.2 through §6.7. Each claim keeps the milestone already written on it. Milestones are cumulative. A claim first required at Mn is required at Mn and at every later milestone. Before that milestone the claim is `NOT_EVALUATED`, which the claim's preconditions already state.

| Milestone | What it first requires | Claims |
|-----------|------------------------|--------|
| M1 | One covering signature, acceptance of its key under a stated trust policy, declared provenance, and completeness against a stated scope. | C-INT-1, C-AUT-1, C-TRS-2, C-PRV-1, C-PRV-2, C-CMP-1, C-CMP-2 |
| M2 | A signing set of more than one signature, and detection when one of those signatures is replaced and another is left unchanged. | C-INT-2, C-AUT-2 |
| M3 | Rejection after a recorded revocation, the P-6 time aspect, and the P-6 log aspect. | C-AUT-3, C-TMP-1, C-LOG-1 |
| M4 | No claim in this set. v0.1 M4 is external scrutiny of a packaged verifier. That activity is not an evidence property. | — |

The M2 claim set is the nine claims at M1 and M2. It is the first conformance target (SRS §5.4, §10.1). C-AUT-3, C-TMP-1, and C-LOG-1 are outside that set.

v0.1 §4 and §6 used these same milestones for the claims carried forward. v0.1 C-INT-2 was marked "M2 (operator-trusted); M3 (independently verifiable)." This contract assigns that claim to M2 only. Whether a second implementation performed the check is an independence level in §7.

### 6.9 Alignment with MC-1 through MC-11

Informative. The annex that restates the eleven capabilities and their minimum test-case counts is Annex A. This table names the M2-set claim each capability exercises. It does not add a claim, move a milestone, or add a state code. §6.6 already names the seven SRS §6.4 codes. Their definitions are the completeness draft §3.

| Capability | Claim in the M2 set | Alignment |
|------------|---------------------|-----------|
| MC-1 Package production | None | Producing a package for `adep.profile.pa.basic.v0` is the workflow profile (WI-5). The capability remains an annex row with no claim ID. |
| MC-2 Schema validation | C-INT-1 | Structural validation is part of P-1. The vectors named on the claim are TV-CAN-01 and TV-CAN-02. The annex owns the minimum of five invalid-package cases. |
| MC-3 Referential integrity | None | No claim in this set detects an unresolved reference between an evidence record and the package manifest. The capability remains an annex row until a later registry entry adds a claim. |
| MC-4 Integrity verification | C-INT-1, C-INT-2, C-AUT-1, C-AUT-2 | Hash checks are C-INT-1. A signature that does not bind is C-AUT-1. Algorithm mismatch is C-AUT-1 (TV-SIG-03). C-INT-2 and C-AUT-2 are the M2 additions. Each claim reports its own result. |
| MC-5 Signer assessment | C-AUT-1, C-TRS-2 | A binding the policy accepts is P-2 `PASS` and P-3 `PASS`. A binding whose key is outside the stated anchors is P-2 `PASS` and P-3 `FAIL`. A binding that fails is P-2 `FAIL`. The two results stay independent. C-AUT-3 is M3 and is outside this pair. |
| MC-6 Completeness assessment | C-CMP-1, C-CMP-2 | The profile and the scope declaration are the precondition. An expected class that is neither `present` nor `redacted` is `INCOMPLETE` under those claims. SRS §10.1 says "missing." The claims use the seven §6.4 codes and have no state by that name. |
| MC-7 Temporal assessment | None in the M2 set | C-TMP-1 and C-LOG-1 stay at M3, which is also where v0.1 placed the temporal claims. An M2 verification reports both P-6 aspects `NOT_EVALUATED`. The annex lists MC-7 and states that its property claims are first required at M3. |
| MC-8 Selective disclosure | C-CMP-1, C-CMP-2 | A redacted class stays `redacted`. Reporting it as `expected_not_captured` fails C-CMP-2. SRS §10.1 names `missing` as the third state and requires failure when a redacted element is reported as missing. This row uses C-CMP-2 and does not add that state. Disclosure-profile conformance is the privacy boundary in §8. C-DSC-1 and C-DSC-2 remain open item OI-7. |
| MC-9 Independent verification | None | The level Independently verified is §7.3. It does not change a property result. Verifier agreement was v0.1 C-VER-1, which remains open item OI-7. |
| MC-10 Exportability | None | Export of the package with its trust anchors, schema, and profile is security baseline SEC-OPS-4. C-TRS-2 and C-CMP-1 require the trust policy and the scope to be stated. They do not require an export step. This row does not add a claim ID. |
| MC-11 Failure reporting | Every claim in the M2 set | Each claim has failure semantics. The result body in §7.4 carries the machine-readable checks, failures, and warnings, and the human-readable explanation. There is no separate claim ID. |

Four capabilities have a claim that states the check: MC-4, MC-5, MC-6, and MC-11. MC-2 and MC-8 use a claim for part of the capability, with the residuals in the table. MC-7 is an M2 capability whose claims are M3. MC-1, MC-3, MC-9, and MC-10 stay annex rows with no claim in this set. Open item OI-8 holds those residuals for the annex.

---

## 7. Verification context

This section is normative. It is the verification context required by SRS §5.5 and assigned by REC-023. A context describes the check. It is not an evidence property.

### 7.1 Rules

1. Every verification result includes all six fields in §7.2.
2. The independence level is exactly one of the four levels in §7.3.
3. A result that omits any of the six fields is not a complete Open ADEP verification result.
4. The context does not change a property result. A limitation does not turn `FAIL` into `PASS`, and it does not establish substantive correctness (NG-1).
5. `packageId`, `status`, `checks`, `failures`, and `warnings` may travel in the same report. They are the result body. They are not context fields. An overall status, when present, remains the derived summary from REC-022.
6. The timestamp in this context is the time of the verification. It is not an evidence-event time under P-6.

### 7.2 Fields

| Field | What it records |
|-------|-----------------|
| Verifier identity | Which implementation performed the verification, named with its version. |
| Verification scope | Which claims were checked, and which claims were out of scope. |
| Trust policy | Which trust anchors, key registries, and acceptance criteria were used. |
| Independence level | One level from §7.3. |
| Limitations | The constraints, assumptions, and known gaps that bound this verification. |
| Timestamp | When the verification was performed, and the clock source used for that time. |

The following v0.1 and verification-spec items sit inside those fields. They are not extra context fields.

| Carried item | Field that holds it |
|--------------|---------------------|
| Specification version, workflow profile, disclosure profile, milestone | Verification scope |
| Trust anchors | Trust policy |
| Verifier name and version; verification-spec `verifier` | Verifier identity |
| Verification-spec `verifiedAt` | Timestamp. This section also requires the clock source. |

### 7.3 Independence levels

The level is one fact about the check. It is not a maturity label. v0.1 labels such as Specified belong to the claims-policy annex (Annex B).

| Level | Definition |
|-------|------------|
| Self-verified | The same implementation that produced the package performed the verification. |
| Cross-verified | A different installation of the same implementation performed the verification. |
| Independently verified | A different implementation performed the verification, using only the published specification and exported trust anchors. |
| Independently reviewed | A party other than the evidence producer (R-1) and the evidence consumer (R-8) performed the verification, with tooling that party operates. |

When more than one definition is true, the result uses the single level chosen in this order:

1. Independently reviewed, when the party condition in that row is met.
2. Independently verified, when a different implementation used only the published specification and exported trust anchors.
3. Cross-verified, when another installation of the producer's implementation performed the check.
4. Self-verified, otherwise.

Verifier identity still names the implementation, so a review by an independent party that also used a different implementation remains visible there.

A level does not, by itself, change P-1 through P-6. Which separations require different parties is trust model v0.2 §4. Self-verified does not meet the R-1 and R-7 separation. That separation is the matrix row that uses the identifier C-PRV-1. The property claim C-PRV-1 in §6.5 is the source-type declaration. A Self-verified result leaves the separation unevaluated. It does not, by itself, change that declaration's P-4 result.

### 7.4 Result body

Informative. REC-023 places these outside the context.

| Report item | Belongs to |
|-------------|------------|
| `packageId` | The result body. It identifies the package that was checked. |
| `status`, `checks`, `failures`, `warnings` | The result body. Procedure checks and any overall summary are derived from the property results. |
| Per-property results | The result body. The value sets are §6.1. |

---

## 8. Claim boundaries

This section is normative. It states what a verified package establishes, and what it does not establish, for the five dimensions in SRS §5.6. A boundary is a limit on what a reader may conclude. It does not add an evidence property.

### 8.1 Rules

1. The contract defines these five boundaries.
2. A positive cell holds only when the properties it names are in scope and their results support it. A property reported `NOT_EVALUATED` does not fill the positive cell.
3. A negative cell holds even when every in-scope property is `PASS`.
4. The negative cells restate NG-1, NG-2, and NG-3 for a reader of a package. They do not create new non-goals.

### 8.2 Boundaries

| Dimension | A verified package does establish | A verified package does not establish |
|-----------|-----------------------------------|---------------------------------------|
| Clinical correctness | The recorded recommendation and the recorded determination are the ones that were signed, and those bytes pass the integrity checks (P-1). | That the recommendation was medically appropriate, guideline-compliant, or based on complete patient information. This is NG-1. |
| Legal compliance | The recorded decision process leaves an evidence trail that can be checked for the properties in scope. | That the decision complied with any applicable law, regulation, or contract. A court's decision on admissibility is inside this cell. This is NG-1. |
| Completeness | Every element the declared scope manifest calls for is accounted for by an evidence state that scope accepts, and the protected bytes pass the integrity checks (P-5 and P-1). | That the scope manifest lists every event that occurred. Activity never routed to a capture point is NG-2. |
| Temporal accuracy | Recorded timestamps are internally consistent, and they are externally anchored where the stated assumptions require an anchor (P-6). | That a timestamp is absolutely accurate, or accurate to a precision finer than the anchor. A producer-supplied `claimed_time`, taken alone, does not fill the positive cell. |
| Privacy | Disclosed data conforms to the declared disclosure profile, when that check is in scope. | That the disclosure profile satisfies HIPAA or any other privacy regulation. This is NG-3. |

An evidence state the declared scope accepts can be a state other than present, including redacted, when that scope says so. The state codes named by the P-5 claims are the seven in SRS §6.4. Their definitions are the completeness draft §3. The disclosure-profile check is not an evidence property. Its requirements are security baseline PRV-DSC-1 through PRV-DSC-4. Data minimization is security baseline PRV-MIN-1 through PRV-MIN-3. Pseudonymization of privacy-sensitive identifiers is security baseline PRV-ID-1 through PRV-ID-3. Boundary crossing for the insurer-hosted deployment is security baseline PRV-BND-1 through PRV-BND-3. Those three requirements cite CD-4 and leave it unaffirmed. None of the privacy requirements named in this paragraph adds a claim. PRV-ID-2 and PRV-ID-3 are Informative. C-DSC-1 and C-DSC-2 remain open item OI-7. If no profile is declared, the privacy positive cell is not established.

v0.1 §8 also prohibits calling the record tamper-proof, claiming the model's reasoning is explained, claiming the system is trustless, and stating a claim above its current milestone. Those limits belong to the claims-policy annex (Annex B). Model reasoning is TM-NG-6. None of them is a sixth row in this table.

---

## 9. Open issues

Rows OI-1 through OI-6 point at text that is already in this draft. OI-7 and OI-8 are residuals this draft does not fill.

| ID | Issue | Where it stands |
|----|-------|-----------------|
| OI-1 | Property-result tokens, including the P-6 aspect values. | §6.1. REC-022 is the decision record. |
| OI-2 | Role identifiers cited by this contract. This contract does not define the roles. | Trust model v0.2 §2. REC-025 is the decision record. |
| OI-3 | Contract non-goals NG-1 through NG-4. Threat-model-only statements stay TM-NG-3 through TM-NG-7. | §5. REC-027 is the decision record. |
| OI-4 | The seven P-5 state codes. | Completeness draft §3. |
| OI-5 | The six-property taxonomy. | §2. REC-020 and REC-024 are the decision record. |
| OI-6 | Six verification-context fields and four independence levels. | §7. REC-023 is the decision record. |
| OI-7 | v0.1 claims without their own row: C-PRV-3, C-CMP-3, C-CMP-4, C-RCP-1, C-DSC-1, C-DSC-2, C-REC-1, and C-VER-1. C-TMP-2 and C-TMP-3 are folded into C-TMP-1. C-LOG-2 is folded into C-LOG-1. C-AUT-3 is the P-3 revocation claim in §6.4. | Later registry work. Annex B states the clean-room requirements and does not give C-VER-1 a row. |
| OI-8 | M2 alignment residuals: MC-7 stays on the M3 claims; MC-6 and MC-8 say "missing" in SRS §10.1; MC-1, MC-3, MC-9, and MC-10 have no claim row. | §6.9 and Annex A. The residuals stay open. |

---

## 10. References

- ADEP-PHASE0-SRS-v0.1 §5.2, §5.3, §5.4, §5.5, §5.6, §5.7, §6.4, §6.6, §10.1, §10.2
- Annex A, M2 conformance profile, in this document. Drafting source: `m2-conformance-profile-annex.md`
- Annex B, conformance claims and assessment policy, in this document. Drafting source: `conformance-claims-policy-annex.md`
- Assurance contract v0.1 §2, §3, §4, §6, §7, and §8
- Verification specification §53
- Threat model v0.1.2 §10 (vector catalog)
- W1-T09 annotation, dispositions for v0.1 §3.1–§3.8 and §6
- Reconciliation register REC-001, REC-003, REC-005, REC-020, REC-022, REC-023, REC-024, REC-025, REC-027
- Trust model v0.2 draft §2 (roles), §4 (rows C-AUT-2, C-INT-4, C-PRV-1, C-TRS-1), and §5 (signature scopes)
- Cross-reference report ADEP-XREF-WI1-WI3-v0.1 (W2-T29)
- Completeness draft §2 (scope declaration), §3 (evidence element states), §5 (coverage indicators), §6 (claim levels), and §7 (integrity relationship)
- Security baseline v0.1 draft SEC-CRYPTO-6 (canonicalization), SEC-PROV-1 through SEC-PROV-3 (import provenance), SEC-TEMP-1 through SEC-TEMP-4 (temporal security), SEC-OPS-4 (export), PRV-MIN-1 through PRV-MIN-3 (data minimization), PRV-DSC-1 through PRV-DSC-4 (disclosure profiles), PRV-ID-1 through PRV-ID-3 (privacy-sensitive identifiers), and PRV-BND-1 through PRV-BND-3 (boundary crossing)

---

## Annex A. M2 Conformance Profile

**Document Identifier:** ADEP-WI1-M2-v0  
**Status:** Attached to this document (W3-T09)  
**Source:** `m2-conformance-profile-annex.md`, through revision 0.1-draft.2

This annex states the eleven minimum capabilities, the test-case minimum for each, the list excluded from M2, and the claim each capability exercises. The drafting source keeps its own section numbers. The numbers below are the numbers in this document.

### A.1 Objective

Normative for the capability list, the test-case minimums, and the excluded list. This is SRS §10.1.1. Milestone M2 is the first conformance target. The claims that target includes are the nine claims at M1 and M2 in §6.8: C-INT-1, C-AUT-1, C-TRS-2, C-PRV-1, C-PRV-2, C-CMP-1, C-CMP-2, C-INT-2, and C-AUT-2. C-AUT-3, C-TMP-1, and C-LOG-1 stay outside that set.

A claim identifier in this annex cites one of those claims, or records that the capability has none in the set. The citation does not add a claim, move a milestone, or add a state code.

### A.2 Rules

1. The capability list is MC-1 through MC-11. Each row keeps the minimum count and the scenario names in SRS §10.1.2.
2. A claim cross-reference is valid when it matches §6.9. MC-4, MC-5, MC-6, and MC-11 have a claim that states the check. MC-2 uses C-INT-1. MC-8 uses C-CMP-1 and C-CMP-2. MC-7 is an M2 capability whose property claims stay at M3. MC-1, MC-3, MC-9, and MC-10 have no claim in the set.
3. Where the claim cell is none, the capability remains a row. That absence is open item OI-8. This annex does not close it.
4. The test-case counts are the SRS minima. This annex does not add a vector identifier. Vectors already named on a claim may be cited. Catalog follow-ons already recorded on those claims stay follow-ons.
5. The evidence-element codes are the seven in the completeness draft §3. This annex has no code named missing.
6. The profile required at M2 is `adep.profile.pa.basic.v0`. The agentic classes PA-EC-20 through PA-EC-24 stay defined in that profile and are outside M2 test coverage.
7. This annex is part of this document.

### A.3 Minimum conformance capabilities

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

#### A.3.1 MC-1

Producing a package for `adep.profile.pa.basic.v0` is the PA profile. This row has no claim ID. SRS names the three cases normal flow, urgent flow, and denial flow. Urgent flow is the PA profile §6.1. The profile's other paths are the emergency exception and retrospective review. This annex keeps the SRS name denial flow. It does not add a denial class, and it does not add a fourth path to the profile.

#### A.3.2 MC-2

Structural validation is part of P-1. The claim is C-INT-1. The vectors named on that claim are TV-CAN-01 and TV-CAN-02. The SRS phrase "missing required fields" names a structural defect. It is not a state code. The minimum is five invalid-package cases covering that defect, type errors, and malformed structures. This annex does not assign vector identifiers to the cases beyond TV-CAN-01 and TV-CAN-02.

#### A.3.3 MC-3

No claim in the set detects an unresolved reference between an evidence record and the package manifest. The minimum is three test cases with broken references. The row stays, and the claim cell stays none. That residual is open item OI-8.

#### A.3.4 MC-4

Hash checks are C-INT-1. A signature that does not bind is C-AUT-1. Algorithm mismatch is C-AUT-1, and the vector named on that claim is TV-SIG-03. C-INT-2 and C-AUT-2 are the M2 additions. Each claim reports its own result. The minimum is five test cases covering valid packages, tampered content, invalid signatures, and algorithm mismatch. Vectors already named on those claims include TV-INT-01, TV-INT-03, TV-SIG-01, TV-SIG-03, and TV-INT-02. This annex does not add a vector identifier for the valid-package case. Catalog-label follow-ons already written on the claims stay follow-ons.

#### A.3.5 MC-5

A binding the policy accepts is P-2 `PASS` and P-3 `PASS`. A binding whose key is outside the stated anchors is P-2 `PASS` and P-3 `FAIL`. A binding that fails is P-2 `FAIL`. The two results stay independent. C-AUT-3 is M3 and is outside this pair. The three SRS cases are those three results. C-TRS-2 already records that the vector catalog has no row for the untrusted-signer case. Adding one remains a catalog follow-on.

#### A.3.6 MC-6

The profile and the scope declaration are the precondition. The claims are C-CMP-1 and C-CMP-2. The minimum is five test cases. The four scenario names are the SRS names. This annex does not invent a fifth scenario name.

| SRS scenario name | Where it already lives |
|-------------------|------------------------|
| scope-complete | Completeness claim level Scope-complete. The verdict `complete` is the completeness draft §4.3, and it uses the declaration's expected-class list. A class the profile requires and the list omits stays completeness open item OI-2. |
| incomplete-documented | Verdict `incomplete_documented`. The claim level Scope-complete with documented gaps also requires a recorded reason. A gap with no reason keeps the verdict and does not receive that level. That package stays completeness open item OI-9. |
| incomplete-undocumented | Verdict `incomplete_undocumented`. That token is a verdict. It is not one of the four claim levels. |
| excluded-evidence | State `excluded`. C-CMP-2 says that state, by itself, does not make the P-5 result `INCOMPLETE`. A package whose expected classes are only `excluded` or `disposed` has no assigned verdict. That case stays completeness open item OI-7. This annex does not add a fifth verdict. |

SRS §10.1 says "missing." The claims use the seven codes and have no state by that name. An expected class that is neither `present` nor `redacted` is `INCOMPLETE` under C-CMP-1 and C-CMP-2 when the code is `expected_not_captured`, `unavailable`, or `arrived_late`.

#### A.3.7 MC-7

The capability is listed. The minimum is three test cases with ordering violations and timestamp anomalies. C-TMP-1 and C-LOG-1 stay at M3. An M2 verification reports both P-6 aspects `NOT_EVALUATED`. These cases do not move either claim to M2. Ordering for `adep.profile.pa.basic.v0` is the PA profile §4. An ordering flag does not change a completeness verdict. This annex does not set a duration for "shortly after," and it does not drop a named ordering pair.

#### A.3.8 MC-8

The claims are C-CMP-1 and C-CMP-2. A redacted class stays `redacted`. The four SRS cases are full disclosure, partial redaction, full redaction (metadata only), and the case that must fail. SRS §10.1 names `missing` as the third state and requires failure when a redacted element is reported as missing. This annex uses C-CMP-2: reporting a redacted class as `expected_not_captured` fails that claim. It does not add a state named missing. Disclosure-profile conformance is the privacy boundary in §8. C-DSC-1 and C-DSC-2 remain open item OI-7.

#### A.3.9 MC-9

This row has no claim in the set. The independence level Independently verified is §7.3. A level does not change a property result. Verifier agreement was v0.1 C-VER-1, which remains open item OI-7. The minimum is two test cases, run by the implementation and by the clean-room verifier, compared for agreement. The clean-room requirements are Annex B §B.5.

#### A.3.10 MC-10

Export of the package with its trust anchors, schema, and profile definition is security baseline SEC-OPS-4. C-TRS-2 and C-CMP-1 require the trust policy and the scope to be stated. They do not require an export step. This row has no claim ID. The minimum is two round-trip cases: export, re-import, and re-verify.

#### A.3.11 MC-11

Each claim in the M2 set has failure semantics. The result body in §7.4 carries the machine-readable checks, failures, and warnings, and the human-readable explanation. There is no separate claim ID. Every test case that produces a failure has that output checked. This annex does not define a further result schema.

### A.4 Excluded from M2

These capabilities are not required at M2. SRS §10.1.3 expects them at later milestones. Listing them here does not add a claim and does not move a milestone.

- Full coverage indicator reconciliation. Completeness CI-6 does not set the method or the thresholds.
- Multi-workflow profile support. Only `adep.profile.pa.basic.v0` is required.
- Advanced deterministic replay.
- Multi-tenant support.
- Full public governance and certification.
- Agentic AI evidence classes PA-EC-20 through PA-EC-24. They are defined in the PA profile §5 and are not required in M2 test coverage.

### A.5 Residuals

Open item OI-8 stays open. It holds MC-7 on the M3 claims, the SRS word missing on MC-6 and MC-8, and the four rows with no claim: MC-1, MC-3, MC-9, and MC-10.

Open item OI-7 stays open. C-DSC-1, C-DSC-2, and C-VER-1 remain in that list.

Completeness open items OI-2, OI-7, and OI-9 stay open. This annex cites them from §A.3.6 and does not choose a representation.

### A.6 References

- ADEP-PHASE0-SRS-v0.1 §10.1.1, §10.1.2, and §10.1.3
- This document §6.2 through §6.9, §7.3, §7.4, §8, and open items OI-7 and OI-8
- Completeness requirements v0.2 §3 (seven state codes), §4 (four verdicts), §5 (CI-6), and §6 (four claim levels)
- PA profile `adep.profile.pa.basic.v0` §3, §4, §5, and §6
- Security baseline v0.1 SEC-OPS-4
- Annex B §B.5 (clean-room reference verifier)

---

## Annex B. Conformance Claims and Assessment Policy

**Document Identifier:** ADEP-WI1-POL-v0  
**Status:** Attached to this document (W3-T09)  
**Source:** `conformance-claims-policy-annex.md`, through revision 0.1-draft.1

This annex states the separation of concerns, the one permissible conformance claim, the path to independent assessment, and the clean-room reference verifier. The drafting source keeps its own section numbers. The numbers below are the numbers in this document.

### B.1 Rules

Normative for the four subsections below. This is SRS §10.2.

1. The seven concepts in §B.2 stay distinct.
2. After a published test suite is passed, the permitted conformance claim is the sentence in §B.3. The five statements in §B.3.2 are not permitted on that basis alone.
3. §B.4 states the four assessment questions. It does not name assessors, a validity-period length, or a publication venue.
4. §B.5 states the four clean-room requirements. It does not build the verifier, and it does not add C-VER-1 as a claim. C-VER-1 remains open item OI-7.
5. MC-9 in Annex A §A.3.9 remains the agreement baseline named in §B.5.
6. This annex is part of this document.

### B.2 Separation of concerns

The following are distinct and shall not be conflated. This is SRS §10.2.1.

| Concept | Definition | Who provides it |
|---------|------------|-----------------|
| Normative specification | What Open ADEP requires. | Open ADEP specification documents. |
| Implementation | Software that aims to satisfy the specification. | Any vendor. The SRS example is DecisionTrace. This row does not make that example the only implementation. |
| Conformance test suite | Published test vectors and expected results. | The Open ADEP project, maintained independently of any implementation. |
| Verifier | Software that checks packages against the specification. | Any party. At least one is the clean-room reference verifier in §B.5. |
| Internal test results | Results of running the test suite against one's own implementation. | The implementation vendor. |
| Independent verification | Results of running an independent verifier against the implementation's output. | An independent party or tool. |
| Independent assessment | An expert evaluation of the implementation's conformance, security, and operational characteristics. | An independent assessor. |

Passing the test suite is an internal test result, or a suite run. It is not independent assessment. Agreement with the clean-room verifier is independent verification under MC-9. That agreement is not independent assessment, and it is not a property result. The independence level Independently verified is §7.3. A level does not change P-1 through P-6.

### B.3 Permissible conformance claims

An implementation may make the following claim after passing the published test suite. This is SRS §10.2.2. The sentence is the template. The four slots are named. No implementation name, implementation version, or suite version is filled in.

> "[Implementation name] version [implementation version] passed the published Open ADEP conformance test suite version [suite version] for profile [profile], subject to the test suite's stated scope and limitations."

| Slot | What it holds |
|------|----------------|
| Implementation name | The name of the implementation that passed the suite. |
| Implementation version | The version of that implementation. SRS writes this slot as X. |
| Suite version | The version of the published Open ADEP conformance test suite. SRS writes this slot as Y. |
| Profile | The workflow profile the suite run covers. For an M2 run against the prior-authorization profile, the identifier is `adep.profile.pa.basic.v0`. |

#### B.3.2 Prohibited on the basis of the suite alone

An implementation shall not claim any of the following solely because it passed the test suite:

- Independent certification.
- Legal admissibility of evidence packages.
- HIPAA compliance.
- Detection of every possible omission.
- Equivalence to independent assessment.

HIPAA compliance, claimed for Open ADEP itself, is non-goal NG-3 in §5.3. Detection of every possible omission is the limit in NG-2, §5.2: P-5 is completeness relative to a declared scope. Legal compliance of the underlying decision is non-goal NG-1, §5.1. Legal admissibility of evidence packages stays its own prohibited claim. This section does not collapse that claim into NG-1.

### B.4 Path to independent assessment

The assessment policy defines the four items below. This is SRS §10.2.3. Each item uses the scope the SRS states.

1. **Who can assess.** A qualified assessor is independent of the vendor and has relevant expertise. The SRS does not name assessors. This annex does not list them. That gap is Annex B open item OI-1.
2. **What is assessed.** The scope is conformance test results, security review, and operational review.
3. **How results are published.** Publication uses assessment reports, validity periods, and public disclosure. The SRS does not state a validity-period length. This annex does not set one. That gap is Annex B open item OI-2. The SRS does not name a publication venue. This annex does not name one. That gap is Annex B open item OI-3.
4. **How other vendors are tested.** Other implementations must be testable using only the published specification, the test suite, and public trust anchors, without requiring access to DecisionTrace's proprietary internals.

### B.5 Clean-room reference verifier

A clean-room reference verifier is developed independently of DecisionTrace. This is SRS §10.2.4. This annex states the requirement. It does not produce the verifier.

The verifier:

1. Is implemented from the published specification, without reference to DecisionTrace source code.
2. Is open-source, or at minimum source-available.
3. Verifies all M2 conformance capabilities. Those capabilities are Annex A §A.3, which restates SRS §10.1.2.
4. Serves as the agreement baseline for MC-9. The capability row is Annex A §A.3.9. The minimum there is two test cases, run by the implementation and by this verifier, compared for agreement.

Verifier agreement was v0.1 C-VER-1. That identifier remains open item OI-7. This section does not give it a claim row.

### B.6 Open items

These three identifiers belong to this annex. They are not assurance-contract open items OI-1 through OI-8.

| ID | Issue | Where it stands |
|----|-------|-----------------|
| OI-1 | SRS §10.2.3 requires independence from the vendor and relevant expertise, and does not name assessors. | §B.4 item 1. No assessor list is added. |
| OI-2 | SRS §10.2.3 includes validity periods and does not state a length. | §B.4 item 3. No length is set. |
| OI-3 | SRS §10.2.3 includes public disclosure and does not name a venue. | §B.4 item 3. No venue is named. |

Open item OI-7 stays open. C-VER-1 has no row in this annex.

### B.7 References

- ADEP-PHASE0-SRS-v0.1 §10.2.1, §10.2.2, §10.2.3, and §10.2.4
- This document §5.1 (NG-1), §5.2 (NG-2), §5.3 (NG-3), §7.3 (independence levels), and open item OI-7
- Annex A §A.3 (MC-1 through MC-11) and §A.3.9 (MC-9)

---

*End of assembled draft through W3-T09 — ADEP-WI1-AC-v0.2*
