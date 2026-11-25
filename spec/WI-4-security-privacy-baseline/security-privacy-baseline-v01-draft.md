# Open ADEP Security and Privacy Requirements Baseline v0.1

**Document Identifier:** ADEP-WI4-SPB-v0.1  
**Status:** DRAFT — first draft final (W3-T03)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §8.1, §8.2.1, §8.2.2, §8.2.3, §8.2.4, §8.2.5, §8.3.1, §8.3.2, §8.3.3, §8.3.4  
**Author:** ARCH (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This is the first draft final of the security and privacy baseline. It contains the thirty-five requirements in SRS §8.2 and §8.3, each with the SRS classification. §2.1 records the role and claim check. Open items OI-1 through OI-19 stay open. CD-4 stays unaffirmed. Salt length stays unset. Encryption stays unspecified.

**Inputs:** SRS §8.1, §8.2.1 through §8.2.5, and §8.3.1 through §8.3.4; threat model v0.1.2 §2.1, §6 (A-1, A-2, A-7), §8.4 (T-13, T-14, T-23), §8.5 (T-16a, T-17), and §8.6 (T-19, T-20, T-26, T-29); W1-T10 annotation; privacy model v0.1 §5.3 and §11; confirmed-decisions register CD-4; assurance contract v0.2 NG-1, NG-3, NG-4, P-1, P-2, P-4, P-5, P-6, §6, §6.9, §7, and §8; trust model v0.2 §4, §5, and §6.2; insurer-hosted role mapping v0.1; completeness draft §3 and §4.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1-draft.1 | 2026-10-24 | ARCH | W2-T09. SEC-CRYPTO-1 through SEC-CRYPTO-6, each Normative. Canonicalization specified as RFC 8785. |
| 0.1-draft.2 | 2026-10-24 | ARCH | W2-T10. SEC-INTEG-1 through SEC-INTEG-5, each Normative. |
| 0.1-draft.3 | 2026-10-24 | ARCH | W2-T16. SEC-PROV-1 and SEC-PROV-2 Normative. SEC-PROV-3 Implementation-dependent. |
| 0.1-draft.4 | 2026-10-24 | ARCH | W2-T17. SEC-TEMP-1 through SEC-TEMP-4, each Normative. |
| 0.1-draft.5 | 2026-10-24 | ARCH | W2-T18. SEC-OPS-1, SEC-OPS-2, and SEC-OPS-4 Normative. SEC-OPS-3 Implementation-dependent. |
| 0.1-draft.6 | 2026-10-24 | ARCH | W2-T22. PRV-MIN-1 through PRV-MIN-3, each Normative. |
| 0.1-draft.7 | 2026-10-24 | ARCH | W2-T23. PRV-DSC-1 through PRV-DSC-4, each Normative. Redacted is not reported as expected_not_captured. |
| 0.1-draft.8 | 2026-10-24 | ARCH | W2-T24. PRV-ID-1 Normative. PRV-ID-2 and PRV-ID-3 Informative. |
| 0.1-draft.9 | 2026-10-24 | ARCH | W2-T25. PRV-BND-1 through PRV-BND-3, each Normative. PRV-BND-1 is scoped to the insurer-hosted deployment. CD-4 is cited and left unaffirmed. |
| 0.1-draft.10 | 2026-10-24 | ARCH | W2-T32. First assembly. Section map, and each label checked against the SRS table. No label changed. Open items OI-1 through OI-19 stay open. |
| 0.1-draft.11 | 2026-10-25 | ARCH | W3-T03. Final review. Cited roles are R-1 through R-10. Cited contract claims have rows. No label changed, and no claim was added. |

---

## 1. Purpose

This document extracts security and privacy requirements from the SRS and the threat model.

| Section | What it contains |
|---------|------------------|
| §2 | The three SRS labels, the label of each of the thirty-five requirements, and the role and claim check. |
| §3 | SEC-CRYPTO-1 through SEC-CRYPTO-6. SRS §8.2.1. All Normative. |
| §4 | SEC-INTEG-1 through SEC-INTEG-5. SRS §8.2.2. All Normative. |
| §5 | SEC-PROV-1 through SEC-PROV-3. SRS §8.2.3. SEC-PROV-3 is Implementation-dependent. |
| §6 | SEC-TEMP-1 through SEC-TEMP-4. SRS §8.2.4. All Normative. |
| §7 | SEC-OPS-1 through SEC-OPS-4. SRS §8.2.5. SEC-OPS-3 is Implementation-dependent. |
| §8 | PRV-MIN-1 through PRV-MIN-3. SRS §8.3.1. All Normative. |
| §9 | PRV-DSC-1 through PRV-DSC-4. SRS §8.3.2. All Normative. |
| §10 | PRV-ID-1 through PRV-ID-3. SRS §8.3.3. PRV-ID-2 and PRV-ID-3 are Informative. |
| §11 | PRV-BND-1 through PRV-BND-3. SRS §8.3.4. All Normative. PRV-BND-1 is scoped to the insurer-hosted deployment. |
| §12 | Open items OI-1 through OI-19. |
| §13 | References. |

These sections are normative except where a paragraph says otherwise, and except SEC-PROV-3 and SEC-OPS-3, which carry the SRS label Implementation-dependent. The identifiers are the SRS identifiers. The W1-T10 annotation used some of the same identifiers for different topics. Those maps are open items OI-1, OI-6, and OI-7. The annotation's temporal topics match §6, and it records no threat-model source for SEC-TEMP-4. That gap is open item OI-9. Its operational topics match §7. The threat-model gaps for key access control and audit logging are open item OI-10. PRV-MIN-1 through PRV-MIN-3 are Normative. The annotation's gaps for that set are open item OI-11. PRV-DSC-1 through PRV-DSC-4 are Normative. The annotation's partial coverage of PRV-DSC-2 is open item OI-15. PRV-ID-1 is Normative. PRV-ID-2 and PRV-ID-3 are Informative. The annotation's partial coverage of PRV-ID-1 and PRV-ID-3 is open items OI-16 and OI-17. PRV-BND-1 through PRV-BND-3 are Normative. The parenthetical on PRV-BND-1 scopes that requirement to the insurer-hosted deployment. The annotation's gaps for that set are open item OI-18. The wording difference between the SRS list and CD-4 is open item OI-19.

A requirement does not name a vendor or a product. §11 names the insurer-hosted deployment because SRS §8.3.4 scopes PRV-BND-1 to that deployment. Assurance-contract NG-4 keeps a specific algorithm out of the assurance contract. This baseline is the document that states the algorithm requirements. A recommended set is not a permanent mandate. Canonicalization is the exception in §3.6: one specified algorithm, because two canonicalizations do not verify against each other.

---

## 2. Classification

SRS §8.1 uses three labels.

| Label | Meaning in this baseline |
|-------|--------------------------|
| Normative | A conforming implementation satisfies the requirement. |
| Implementation-dependent | The requirement applies. The mechanism is left to the implementation. |
| Informative | Guidance. It is not a conformance condition. |

Each label below is the label in the SRS table for that identifier. This assembly does not relabel any row.

| Requirement | Section | Label |
|-------------|---------|-------|
| SEC-CRYPTO-1 | §3.1 | Normative |
| SEC-CRYPTO-2 | §3.2 | Normative |
| SEC-CRYPTO-3 | §3.3 | Normative |
| SEC-CRYPTO-4 | §3.4 | Normative |
| SEC-CRYPTO-5 | §3.5 | Normative |
| SEC-CRYPTO-6 | §3.6 | Normative |
| SEC-INTEG-1 | §4.1 | Normative |
| SEC-INTEG-2 | §4.2 | Normative |
| SEC-INTEG-3 | §4.3 | Normative |
| SEC-INTEG-4 | §4.4 | Normative |
| SEC-INTEG-5 | §4.5 | Normative |
| SEC-PROV-1 | §5.1 | Normative |
| SEC-PROV-2 | §5.2 | Normative |
| SEC-PROV-3 | §5.3 | Implementation-dependent |
| SEC-TEMP-1 | §6.1 | Normative |
| SEC-TEMP-2 | §6.2 | Normative |
| SEC-TEMP-3 | §6.3 | Normative |
| SEC-TEMP-4 | §6.4 | Normative |
| SEC-OPS-1 | §7.1 | Normative |
| SEC-OPS-2 | §7.2 | Normative |
| SEC-OPS-3 | §7.3 | Implementation-dependent |
| SEC-OPS-4 | §7.4 | Normative |
| PRV-MIN-1 | §8.1 | Normative |
| PRV-MIN-2 | §8.2 | Normative |
| PRV-MIN-3 | §8.3 | Normative |
| PRV-DSC-1 | §9.1 | Normative |
| PRV-DSC-2 | §9.2 | Normative |
| PRV-DSC-3 | §9.3 | Normative |
| PRV-DSC-4 | §9.4 | Normative |
| PRV-ID-1 | §10.1 | Normative |
| PRV-ID-2 | §10.2 | Informative |
| PRV-ID-3 | §10.3 | Informative |
| PRV-BND-1 | §11.1 | Normative |
| PRV-BND-2 | §11.2 | Normative |
| PRV-BND-3 | §11.3 | Normative |

The SRS parenthetical on PRV-BND-1 is the scope of that requirement, the insurer-hosted deployment. It is not a fourth label. The SRS phrase "if used" on SEC-CRYPTO-5 is the condition in §3.5. It is not a fourth label. §3.7 states the agility already required by SEC-CRYPTO-3 and SEC-CRYPTO-4. It is not a seventh cryptographic requirement.

### 2.1 Roles and claims

This check reads every role identifier and every claim identifier in §3 through §11. No label in the table above changed.

The roles cited are R-2, R-4, R-5, R-6, R-7, R-9, and R-10. Each is one of R-1 through R-10 in trust model v0.2 §2. The names used here match that section: evidence signer, continuity countersigner, log operator, independent log witness, evidence verifier, disclosure issuer, and trust-anchor publisher. R-1, R-3, and R-8 are not cited. That absence is not a broken reference.

The contract claims cited are C-AUT-1, C-AUT-3, C-TRS-2, C-PRV-1, C-PRV-2, C-CMP-1, C-CMP-2, C-TMP-1, and C-LOG-1. Each has a row in assurance contract v0.2 §6.3 through §6.7. C-INT-1, C-INT-2, and C-AUT-2 are not cited. That absence is not a broken reference.

Four identifiers are matrix rows in trust model v0.2 §4.2 and are not rows among the contract's twelve claims. C-INT-3 separates R-1 and R-4. C-INT-4 separates R-5 and R-6. C-TRS-1 separates R-10 and R-2. C-DSC-1 separates R-9 and R-7. This baseline cites them as those separations. C-DSC-1 and C-DSC-2 remain assurance contract open item OI-7. This check does not add a claim.

MC-6, MC-7, MC-8, MC-9, MC-10, and MC-11 are SRS §10.1 capabilities. MC-10 has no claim row. That residual stays assurance contract open item OI-8. This check does not add a claim.

A requirement that states it adds no claim stays without a claim identifier.

---

## 3. Cryptographic requirements

### 3.1 SEC-CRYPTO-1 Signing-key identity

**Classification.** Normative.

**Requirement.** A signing-key identity is bound to one specific role through a certificate or a key-registration record. The roles this requirement names are R-2 (evidence signer) and R-4 (continuity countersigner). The binding is the role authorization that C-TRS-2 checks under the stated trust policy.

**Sources.** Trust model v0.2 §6.2, generation stage. Threat model T-22, distinct key identifiers and roles.

The package-seal holder is unassigned (trust model open item OI-7). This requirement does not bind a package-seal key.

Informative. Threat-model assumption A-2 places the two signing keys in separate key-storage domains. Storage and access control are SEC-OPS-1. They are not this requirement.

### 3.2 SEC-CRYPTO-2 Compromise and revocation

**Classification.** Normative.

**Requirement.** Compromise and revocation are recorded, and the effect on evidence signed before revocation is the following.

1. R-10 records a compromise with the time of that record, and records a revocation with the revocation time. The trust model states those facts. This requirement states their effect on evidence.
2. A signature made after the recorded revocation time is rejected. The property result is P-3 `FAIL`. That is C-AUT-3. The demonstrating vector is TV-SIG-02.
3. Evidence signed before the recorded revocation keeps the signature binding it had. P-1 and P-2 are unchanged by the later revocation record. P-3 uses key validity at the time the stated trust policy uses. Threat model T-13 checks that validity at anchoring time. When that time is before the recorded revocation, P-3 can pass.
4. Revocation does not rewrite an earlier signature into a failure.

**Sources.** Trust model v0.2 §6.2, compromise and revocation stages. Threat model T-13 and T-14. TV-SIG-02.

The interval between a compromise and the logged revocation record remains. T-13 names that window as the residual. This requirement does not close it.

Rotation, including any interval in which two keys are both accepted, is the trust policy. It is not a second revocation rule.

### 3.3 SEC-CRYPTO-3 Hash algorithms

**Classification.** Normative.

**Requirement.** A hash used for an integrity check or a commitment is collision-resistant and pre-image-resistant. The recommended set for this baseline version is SHA-256. Algorithm agility is required. The mechanism is §3.7.

**Sources.** SRS §8.2.1. Threat-model assumption A-1. Threat model T-17, for the current suite, and T-23, for later migration.

Informative. Element salts of at least 128 bits from a cryptographic random source are assumption A-7. The annotation placed that rule in a differently numbered requirement. SRS §8.2.1 does not give salt generation its own identifier. This draft does not fold A-7 into SEC-CRYPTO-3. That placement is open item OI-2.

### 3.4 SEC-CRYPTO-4 Signature algorithms

**Classification.** Normative.

**Requirement.** A signature algorithm meets the binding C-AUT-1 checks, under stated cryptographic assumptions. The recommended set for this baseline version is ES256, ECDSA with P-256 and SHA-256. Algorithm agility is required. The mechanism is §3.7.

An absent algorithm identifier, an identifier outside the set for the named baseline version, or the identifier `none`, fails the binding. The property result is P-2 `FAIL`. The demonstrating vector is TV-SIG-03.

**Sources.** SRS §8.2.1. Threat-model assumption A-1. Threat model T-17.

### 3.5 SEC-CRYPTO-5 HMAC

**Classification.** Normative.

**Requirement.** When HMAC is used for integrity protection, the implementation states how the symmetric key is generated, held, and retired, and it states this consequence: any party that holds the key can produce a valid HMAC. An asymmetric signature does not give every verifier that capability. The v0.1 evidence-signature suite in T-17 is ES256. It is not HMAC. This requirement does not require an implementation to use HMAC.

**Sources.** SRS §8.2.1. The threat-model catalog does not use HMAC for evidence signatures.

Key-storage controls for either kind of key are SEC-OPS-1. They are not restated here.

### 3.6 SEC-CRYPTO-6 Canonicalization

**Classification.** Normative.

**Requirement.** Before hashing or signing, evidence records are reduced to one canonical form. For this baseline version the algorithm is RFC 8785, the JSON Canonicalization Scheme. The algorithm is deterministic. Two conforming implementations produce identical output for the same input.

Duplicate names in one JSON object are rejected. The demonstrating vector is TV-CAN-01. Signed bytes that are not in that canonical form are rejected. The demonstrating vector is TV-CAN-02. Unicode normalization is not applied. NFC and NFD strings remain distinct inputs and produce distinct hashes. The demonstrating vector is TV-CAN-03.

A package names this canonicalization by the baseline version it claims. A verifier uses that algorithm and no other. A second canonicalization in the same baseline version is not conforming, because the two outputs would not match.

**Sources.** SRS §8.2.1. Threat model §2.1 step 1 and T-16a. Assurance contract P-1, which leaves the serialization to this requirement.

Informative. A Java producer can reject duplicate keys with Jackson `STRICT_DUPLICATE_DETECTION` and without lenient number parsing. That configuration is one way to meet the duplicate-key rule. It is not the requirement. The requirement is the canonical form, which a clean-room verifier can check without that library.

Changing the canonicalization algorithm is a new baseline version. It is not a per-package choice, and it is not the hash-algorithm agility in §3.7. Already-signed evidence stays under the canonicalization named for the version that signed it.

### 3.7 Algorithm agility

Normative for SEC-CRYPTO-3 and SEC-CRYPTO-4.

Every hashed or signed structure carries the algorithm identifier it used. A verifier accepts that identifier only when it is in the recommended set published for the baseline version named in the verification scope. A later baseline version may publish a different set. The property requirements in §3.3 and §3.4 stay in force. Publishing the new set is the agility this baseline requires.

Threat model T-17 describes the current set as a single v0 suite, SHA-256 and ES256. This section treats that suite as the recommended set for this version. It does not treat it as a prohibition on a later set.

The procedure that re-anchors evidence after an algorithm in the set weakens is threat model T-23. It is not specified. That procedure is open item OI-3. Post-quantum algorithms are threat-model non-goal NG-7, carried in the trust model as TM-NG-7. They are not in the recommended set.

---

## 4. Integrity and verification requirements

### 4.1 SEC-INTEG-1 Coverage of an evidence record

**Classification.** Normative.

**Requirement.** Integrity protection covers every normative field of an evidence record. Hashing and signing use the canonical bytes from SEC-CRYPTO-6.

For an event, the signed header includes `chain_id`, `seq`, `prev_event_hash`, `claimed_time`, `not_before_checkpoint`, and the commitment root. Each element is covered by its own commitment. A change to element content changes that commitment and therefore the root in the signed header. A field the record schema marks as normative, and that sits outside both the header and the element commitments, is not a conforming record.

**Sources.** SRS §8.2.2. Threat model §2.1 steps 1 and 2, and T-01.

### 4.2 SEC-INTEG-2 Records and the package seal

**Classification.** Normative.

**Requirement.** The integrity relationship between evidence records and the package seal is the following.

1. Element commitments for one event combine into the commitment root in that event's signed header.
2. Events in one chain link by `prev_event_hash`, at the position `seq` names, for the `chain_id` the header names.
3. The package seal signature covers the package's list of records and the statement of those relationships. What that signature attests, and what it does not attest, is trust model v0.2 §5.2. It does not establish completeness. Completeness is P-5.

The SRS names a Merkle tree, a hash chain, or a hash list as examples. This baseline uses the commitment root and the hash chain from the threat model. A Merkle tree is not the required structure.

The v0.1 sealing step fixes the chain length, and the continuity countersigner refuses later events on that chain. That step is R-4. It is not the package seal signature.

The role that holds the package-seal key is unassigned. This requirement defines what the seal covers. It does not assign the holder. That assignment is trust model OI-7, recorded here as open item OI-5.

**Sources.** SRS §8.2.2. Threat model §2.1 steps 1 and 5. Trust model v0.2 §5.2 and §5.3.

### 4.3 SEC-INTEG-3 Verification without the producer's systems

**Classification.** Normative.

**Requirement.** A package produced by one implementation can be verified by a different implementation using only the published specification, the exported trust anchors, and the package. Verification does not require the producer's internal store or the producer's application logic.

That condition is the independence level Independently verified in assurance contract §7.3. The level does not change a property result.

**Sources.** SRS §8.2.2. Assurance contract §7.3. SRS §10.1 capability MC-9 is the conformance test of this requirement. The test-case count is the M2 annex (W3-T07).

### 4.4 SEC-INTEG-4 Machine-readable results

**Classification.** Normative.

**Requirement.** A verification result is a structured record. It includes the six verification-context fields in assurance contract §7.2, and the property results named in assurance contract §6.1. A result that exists only as prose does not meet this requirement.

`packageId`, `status`, `checks`, `failures`, and `warnings` may travel with that record. They are the result body in assurance contract §7.4. They are not context fields.

**Sources.** SRS §8.2.2, which points at SRS §5.5. Assurance contract §7. SRS §10.1 capability MC-11 asks, in addition, for a human-readable explanation of each failure. That explanation is part of the result body. This requirement's condition is the structured record.

### 4.5 SEC-INTEG-5 Reporting of expected evidence that is not present

**Classification.** Normative.

**Requirement.** Detection and reporting of expected evidence that the package does not contain follow the completeness model. The state codes are the seven in the completeness draft §3. The report is the completeness report in the completeness draft §4.

A class in `expected_not_captured`, `unavailable`, or `arrived_late` is a gap and is listed on the gap list. The verdicts are the four in completeness draft §4.3. The P-5 tokens are those in assurance contract §6.6, as completeness draft §4.4 lines them up.

SRS §8.2.2 says "missing evidence." The completeness model has no state named missing. This requirement uses the seven codes. It does not add that state.

**Sources.** SRS §8.2.2, which points at SRS §6. Completeness draft §3 and §4. Assurance contract §6.6 and §6.9 (MC-6, MC-8).

The W1-T10 annotation used SEC-INTEG-5 for log non-equivocation. That topic is P-6 and trust model v0.2 §4, row C-INT-4. It is not this requirement. The identifier difference is open item OI-6.

---

## 5. Provenance and import requirements

### 5.1 SEC-PROV-1 Import provenance

**Classification.** Normative.

**Requirement.** Evidence imported from an external system, from another ADEP implementation, or from a pre-existing record carries a provenance record of that import. The record states the import source, the time of the import, and the transformations applied.

The import source identifies where the evidence came from. The time is the time the importer records for the import. That time is part of the import record. It is not, by itself, a P-6 anchor. The transformations are those applied in the course of the import. When none were applied, the record says so.

The import record is the chain-of-custody statement for the import. Assurance contract §2.6 defines provenance as origin, intermediaries, and transformations, to the extent the record declares them. This requirement is that import declaration. It does not replace C-PRV-1, which is the source-type and actor declaration on an event.

**Sources.** SRS §8.2.3. Assurance contract §2.6 and §6.5 (C-PRV-1).

### 5.2 SEC-PROV-2 Unverified import

**Classification.** Normative.

**Requirement.** Imported evidence that cannot be independently verified is labeled `unverified_import`. Evidence with that label does not contribute to an assurance claim that requires verified provenance.

For this requirement, independently verified means a verifier can check the imported evidence from the published specification, the exported trust anchors, and the imported bytes. Those are the materials SEC-INTEG-3 names for a package. When those materials are absent, or the check cannot be completed, the label applies.

`unverified_import` is an import label. It is not an evidence-element state. The seven state codes remain the completeness draft §3. An imported element still has one of those codes.

C-PRV-1 is a declaration of source type and declared actor. The label does not set that claim to `FAIL` or `UNRESOLVED`. A declaration on the import record can still be `RESOLVED`. C-PRV-2 compares a reference hash with a supplied artifact. The label does not set that claim to `MISMATCH`.

The assurance contract does not mark any of the twelve claims as one that requires verified provenance. This requirement keeps the prohibition: the labeled import is not treated as provenance a verifier has checked, and it is not reported as a verified result for the content inside the import. Which of the twelve claims, if any, that prohibition changes is open item OI-8. This section does not add a claim.

**Sources.** SRS §8.2.3. SEC-INTEG-3. Assurance contract §6.5 (C-PRV-1, C-PRV-2). Completeness draft §3.

### 5.3 SEC-PROV-3 Tools used in production

**Classification.** Implementation-dependent.

**Requirement.** The evidence package records the tool versions, the configurations, and, where an MCP tool was used, the MCP tool hashes, that were used in producing the evidence.

The requirement applies. The way those values are carried in the package is left to the implementation. When no MCP tool was used, no MCP tool hash is required. A configuration that was not used in producing the evidence is outside this requirement.

This section does not assign an evidence-class identifier for the tool record. A workflow profile may define one. That list is WI-5.

**Sources.** SRS §8.2.3. The SRS label is Implementation-dependent.

The W1-T10 annotation used SEC-PROV-1 for source identification, SEC-PROV-2 for content-hash references, and SEC-PROV-3 for build and supply-chain provenance. It called SEC-PROV-3 informative. SRS §8.2.3 uses the three topics in §5.1, §5.2, and §5.3, and it labels SEC-PROV-3 Implementation-dependent. This draft follows the SRS. Content-hash resolution of a policy or a model stays C-PRV-2. The identifier difference is open item OI-7.

---

## 6. Temporal security requirements

### 6.1 SEC-TEMP-1 Timestamp source

**Classification.** Normative.

**Requirement.** Each evidence timestamp identifies its source. The source is a local clock, NTP, or an external timestamping authority, and the record names which one produced that timestamp.

A time field does not identify its source. A producer-supplied `claimed_time` does not. The import time recorded under SEC-PROV-1 does not. Where one of those fields is used as an evidence timestamp, the source is named in addition to the field.

**Sources.** SRS §8.2.4. Assurance contract §2.8.

### 6.2 SEC-TEMP-2 Accuracy assumptions

**Classification.** Normative.

**Requirement.** The trust assumptions about timestamp accuracy are stated for the verification. The statement says what the named source is relied on to establish, and what it is not relied on to establish.

Absolute accuracy is not an assumption this requirement adds. Assurance contract §2.8 already excludes it. Where the assumptions include a tolerance Δ, the stated value is part of the assumption. This requirement does not fix that value. C-TMP-1 uses Δ only where an assumption states it.

Stating the assumptions does not move C-TMP-1 or C-LOG-1. Both remain first required at M3. Before M3 both are `NOT_EVALUATED`.

**Sources.** SRS §8.2.4. Assurance contract §2.8 and §6.7.

### 6.3 SEC-TEMP-3 External anchoring

**Classification.** Normative.

**Requirement.** Where an external timestamp anchor is available, it is used. The package then carries temporal evidence that does not rest only on the producer's clock. A transparency-log receipt timestamp is one such anchor.

The receipt is the transparency-log receipt in trust model v0.2 §5.2. R-5 operates the log that issues it. The receipt attests that a commitment was included no later than checkpoint C. This requirement does not add a signature type. The log check stays the log aspect of P-6. It is not a seventh property. Whether R-5 and R-6 are different parties remains trust model v0.2 §4, row C-INT-4.

When no anchoring checkpoint is in scope, the time aspect of C-TMP-1 is `NOT_EVALUATED`. That is the claim's precondition. It is not a failure of this requirement, and `claimed_time` does not fill the gap. C-TMP-1 and C-LOG-1 stay at M3. SRS §10.1 lists temporal assessment as an M2 capability. The property claims that assess it remain the M3 claims. This section does not move them.

**Sources.** SRS §8.2.4. Trust model v0.2 §5.2 and §4, row C-INT-4. Assurance contract §2.8 and §6.7. SRS §10.1, MC-7.

### 6.4 SEC-TEMP-4 Changes that affect capture or signing

**Classification.** Normative.

**Requirement.** An administrative or configuration change that affects evidence capture or signing is recorded as an evidence event, and that event carries a timestamp.

The event uses the evidence-record rules already in this baseline. It does not add an evidence state, and it does not add a signature type. The timestamp's source is identified under SEC-TEMP-1. A `claimed_time` on the event, with no source, does not meet this requirement.

This section does not assign a workflow-profile class identifier for the event. A profile may define one. That list is WI-5.

The W1-T10 annotation says the threat model does not address this requirement. The text above is the SRS requirement. The missing threat-model source is open item OI-9. The annotation's topics for SEC-TEMP-1, SEC-TEMP-2, and SEC-TEMP-3 are the topics in §6.1, §6.2, and §6.3.

**Sources.** SRS §8.2.4. W1-T10 annotation, temporal extraction notes.

---

## 7. Operational security requirements

### 7.1 SEC-OPS-1 Key storage and access control

**Classification.** Normative.

**Requirement.** Storage and access for signing keys are the following.

1. Private key material for a signing key is stored outside the evidence package. A verifier does not need that material. When HMAC is used, the same storage rule applies to the symmetric key.
2. Use of a key bound under SEC-CRYPTO-1 is limited to the holder of that R-2 or R-4 binding. The binding remains the certificate or the key-registration record. This access rule does not replace the binding, and it does not replace the trust policy that C-TRS-2 checks.
3. When HMAC is used, the same limit applies to who may hold and use the symmetric key. SEC-CRYPTO-5 states that any party holding that key can produce a valid HMAC, and it states generation and retirement. This requirement does not restate those sentences.
4. The package-seal holder is unassigned. This requirement does not define storage for that key until a holder is assigned. The assignment is open item OI-5. When a holder is assigned, the storage and access rules above apply to that key.

Informative. Threat-model assumption A-2 places signing keys in separate storage domains. That arrangement is one way to store them. It is not required. The annotation says explicit access control is missing from the threat model. The rules above are the SRS requirement. That gap is open item OI-10.

**Sources.** SRS §8.2.5. SEC-CRYPTO-1 and SEC-CRYPTO-5. Threat-model assumption A-2, as informative context.

### 7.2 SEC-OPS-2 Audit logging

**Classification.** Normative.

**Requirement.** Signing operations, verification operations, and administrative changes are written to an audit log.

A signing entry names the operation, the key identity, and the time. It does not contain private key material. A verification entry names the operation and the time. An administrative entry names the change and the time.

The audit log is an operational record. It is not the transparency log that R-5 operates, and it is not a P-6 result. An administrative change that affects evidence capture or signing is also an evidence event under SEC-TEMP-4. The audit entry does not replace that event.

The annotation records no threat-model source for this requirement. The text is SRS §8.2.5. That gap is open item OI-10.

**Sources.** SRS §8.2.5. SEC-TEMP-4.

### 7.3 SEC-OPS-3 Deployment topology

**Classification.** Implementation-dependent.

**Requirement.** The security implications of each deployment topology are assessed in the role-to-party mapping for that topology.

The insurer-hosted mapping is one such assessment. It is the companion document from W1-T29. That assessment records separations the named parties do not meet, including C-INT-3, C-INT-4, and C-TRS-1. Logical separation inside one organization is not the different-parties test in the trust-model matrix. This requirement cites that result. It does not change the mapping, it does not choose trust-model open item OI-7, and it does not affirm CD-1 through CD-4. Affirmation is W1-T30.

Another topology is another mapping. This baseline does not write that second document.

**Sources.** SRS §8.2.5. Insurer-hosted role mapping v0.1 §5 and §6. Trust model v0.2 §4.

### 7.4 SEC-OPS-4 Exported verification material

**Classification.** Normative.

**Requirement.** An exported evidence package includes the trust anchors and the other verification material needed to verify it without the producer's systems.

The verification that uses that export is SEC-INTEG-3: the published specification, the exported trust anchors, and the package. SRS §10.1 capability MC-10 names the trust anchors, the schema, and the profile definition as material included with the export. This requirement includes those.

The assurance contract does not give MC-10 a claim. This requirement does not add one. That residual stays assurance-contract open item OI-8.

**Sources.** SRS §8.2.5. SEC-INTEG-3. SRS §10.1, MC-10. Assurance contract §6.9.

The W1-T10 annotation uses SEC-OPS-1 through SEC-OPS-4 for the same four topics as SRS §8.2.5. It marks key storage as partial, audit logging as absent, topology assessment as an open question, and export material as implicit. This draft uses the SRS topics and the SRS labels. It does not renumber the annotation. The two drafting gaps are open item OI-10.

---

## 8. Data minimization

### 8.1 PRV-MIN-1 Metadata and clinical content

**Classification.** Normative.

**Requirement.** An evidence package supports separation of evidence metadata from sensitive clinical content. Metadata used to identify an element and to check its integrity can be carried while the clinical content is not carried in the clear.

The `redacted` state is one such separation. Existence and metadata stay visible, and the content is a commitment. That state is the completeness draft §3.3.2. This requirement does not require every clinical element to be redacted. It requires the package to be able to separate the two.

A commitment mechanism that qualifies for that state is still the list named in the completeness draft: a hash, a zero-knowledge proof, or another mechanism the privacy baseline defines. This requirement does not close that list. Disclosure profiles, which say when content is withheld, are §9. §9.3 uses the commitment and does not close the list.

Encryption of clinical content is not specified here. The annotation's note of encrypted content with clear commitments is partial coverage of this row. That mechanism remains open item OI-4.

Separation does not establish that a deployment complies with HIPAA or any other privacy regulation. That limit is NG-3.

**Sources.** SRS §8.3.1. Completeness draft §3.3.2. Assurance contract §5.3 (NG-3) and §8 (privacy boundary).

### 8.2 PRV-MIN-2 Minimum data for a claim

**Classification.** Normative.

**Requirement.** The minimum data for each assurance claim is defined, so an implementation can avoid collecting more than the declared assurance level requires.

The minimum for a claim is the data that claim's precondition and test method read. Those texts are the twelve claims in assurance contract §6.2 through §6.7. This requirement does not add a claim, and it does not change a precondition or a failure rule.

The declared assurance level is the set of claims in scope for the verification, including the milestone in assurance contract §6.8. A claim that is `NOT_EVALUATED` because its milestone has not been reached does not, under this requirement, require its inputs to be collected. Data that no in-scope claim reads is not required by this baseline for that level.

The phrase "declared assurance level" is not a defined term in the assurance contract. The reading above is this draft's. It is open item OI-12.

**Sources.** SRS §8.3.1. Assurance contract §6 and §6.8.

### 8.3 PRV-MIN-3 External references

**Classification.** Normative.

**Requirement.** A package supports a controlled reference to external evidence. The reference is an evidence element. It carries a target identifier, a content hash of the external bytes, and a statement that those bytes are not copied into the package. The element's own fields are integrity-protected. The external bytes are not required to be in the package.

The reference has one of the seven state codes. It is not an eighth state. A reference that is included and integrity-protected is `present` as a reference. An omitted class remains the state in the completeness draft §3. A reference is not a way to leave an expected class unstated.

`redacted` keeps a commitment in the package and withholds content. A reference names bytes that stay outside the package. The two are different separations under PRV-MIN-1.

C-PRV-2 is `RESOLVED` when a policy or model artifact is supplied with the package and the hash matches. A reference that leaves those bytes outside the package does not, by itself, satisfy that claim. This requirement does not rewrite C-PRV-2. That relationship is open item OI-13.

**Sources.** SRS §8.3.1. Completeness draft §3. Assurance contract §6.5 (C-PRV-2).

The W1-T10 annotation marks PRV-MIN-1 as partial, citing encrypted content and clear commitments, and it records no threat-model source for PRV-MIN-2 or PRV-MIN-3. This draft uses the three SRS requirements and the Normative label. It does not specify encryption. Those gaps are open item OI-11.

---

## 9. Disclosure profiles

### 9.1 PRV-DSC-1 Disclosure profile

**Classification.** Normative.

**Requirement.** A disclosure profile names one sharing context. For each evidence class in the workflow profile the package declares, the profile assigns one disposition: disclosed, redacted, or excluded. The profile carries an identifier. A class in that workflow profile with no disposition does not meet this requirement. The absence is not read as disclosed.

The three words are dispositions. They are not evidence-state codes, and they do not add an eighth state. The evidence state of a class stays one of the seven codes in the completeness draft §3.

This draft reads two of the dispositions against those codes.

- Disclosed matches `present`.
- Redacted matches `redacted`. Existence and metadata stay visible. The content is the commitment in the completeness draft §3.3.2.

A class whose state does not match its disposition keeps that state. The mismatch does not change a completeness verdict, and it does not change C-CMP-1 or C-CMP-2. The privacy positive cell in assurance contract §8 is not established for a package that contains such a mismatch.

The profile word excluded is not given a match in this draft. Completeness `excluded` means the class was not intended to be collected. A class collected for the record and left out of one sharing context is not that meaning. Both words stay as written. The missing match is open item OI-14. Until that match is stated, a disposition of excluded does not by itself establish the privacy positive cell.

The mechanism does not require every package to carry a profile. When no profile is declared, that positive cell is not established. The redaction-list entry says that no profile is declared. That entry is the completeness draft §4.2.

The role that chooses the profile is R-9, already defined in the trust model. This requirement does not add a role. It does not add C-DSC-1 or C-DSC-2. Those claims remain assurance-contract open item OI-7. The separation of R-9 and R-7 stays trust model §4. A profile does not establish that the sharing satisfies HIPAA or any other privacy regulation. That limit is NG-3.

**Sources.** SRS §8.3.2. Completeness draft §3 and §4.2. Assurance contract §5.3 (NG-3), §6.6 (C-CMP-1, C-CMP-2), §8, and §9 OI-7. Trust model v0.2 §4 row C-DSC-1.

### 9.2 PRV-DSC-2 Inclusion and integrity

**Classification.** Normative.

**Requirement.** When a disclosure profile is applied, that profile is included in the evidence package, and its bytes are integrity-protected.

Integrity protection is the protection §4 already requires for package content. The profile is not a sixth signature type. The five signature types stay trust model §5. The package-seal holder stays unassigned.

The redaction list cites the identifier of the included profile. That list is the completeness draft §4.2.

The annotation records this requirement as implied rather than stated as its own threat-model rule. The text above is the SRS requirement. That gap is open item OI-15.

**Sources.** SRS §8.3.2. §4 of this baseline. Trust model v0.2 §5. Completeness draft §4.2.

### 9.3 PRV-DSC-3 Verification when content is redacted

**Classification.** Normative.

**Requirement.** A verifier can check a package that contains redacted elements.

For an element whose state is `present`, the verifier checks the integrity of the content bytes. Those checks are the P-1 checks.

For an element whose state is `redacted`, the verifier checks the commitment. The check confirms that the element was bound into the signed bytes. It does not give the verifier the content. It does not establish that the content is true. That limit is NG-1.

The SRS sentence "present at the time of signing" is this binding. It is not the evidence state `present`. A redacted element stays `redacted`.

The commitment mechanisms remain the open list in the completeness draft §3.3.2. This requirement does not close that list, and it does not specify encryption.

**Sources.** SRS §8.3.2. Completeness draft §3.3.2. Assurance contract §5.1 (NG-1) and §6.2 (P-1).

### 9.4 PRV-DSC-4 Present, redacted, and missing

**Classification.** Normative.

**Requirement.** The verification result distinguishes `present`, `redacted`, and the case the SRS calls missing.

This draft reads "missing" as `expected_not_captured`. That is the reading in the completeness draft §3.1. This requirement does not add a state named missing.

A verifier reports a `redacted` element as `redacted`. It does not report that element as `expected_not_captured`. A verifier reports an `expected_not_captured` element as `expected_not_captured`. It does not report that element as `redacted`.

The first direction is C-CMP-2. This requirement does not change that claim, and it does not add a claim. The other four state codes stay distinct under the completeness draft §3. This requirement does not collapse them into the three words in the SRS sentence.

**Sources.** SRS §8.3.2. Completeness draft §3.1 and §3.3.2. Assurance contract §6.6 (C-CMP-2) and §6.9 (MC-8).

The annotation marks PRV-DSC-1, PRV-DSC-3, and PRV-DSC-4 as covered by the threat model. It marks PRV-DSC-2 as partial. This draft uses the four SRS requirements and the Normative label. The partial row is open item OI-15.

---

## 10. Privacy-sensitive identifiers

### 10.1 PRV-ID-1 Pseudonymization

**Classification.** Normative.

**Requirement.** A package can carry a pseudonym in place of a patient identifier, a provider identifier, or a case number. The signed bytes are the bytes that contain that pseudonym. The P-1 checks run on those bytes. The verifier does not need the original identifier to run those checks.

Replacing an identifier in a package whose signature binds the original value changes the canonical bytes. That package fails P-1. The failure is the integrity check. A conforming pseudonymized package is one whose signature binds the pseudonym.

The pseudonym is a value in the package. It has no separate evidence state. An element that contains a pseudonym keeps the state the completeness draft §3 assigns. An identifier inside redacted content is withheld with that content. That case is §9. An identifier that remains visible in the package, including in metadata, is in scope here.

This requirement is the capability. A package may still carry the original identifier. Those bytes are what P-1 checks.

No pseudonymization algorithm is named. A hash is not required. A salt is not specified. Salt length remains open item OI-2. Salted hashes at a deployment boundary are a later section.

A random `chain_id` is a header field under §4.1. It is not a pseudonym for a patient identifier, a provider identifier, or a case number. The annotation's note for this row is limited to `chain_id`. That gap is open item OI-16.

Pseudonymization does not establish that the identifier meets a privacy regulation. That limit is NG-3. This requirement does not add a claim.

**Sources.** SRS §8.3.3. Assurance contract §5.3 (NG-3), §5.4 (NG-4), and §6.2 (P-1). §4.1 of this baseline.

### 10.2 PRV-ID-2 Limits of hashing and pseudonymization

**Classification.** Informative.

**Requirement.** This baseline states the limits. The statement is guidance. It is not a conformance condition.

A hash of an identifier drawn from a small set can be recovered by trying the likely values and comparing the hashes. Patient identifiers, provider identifiers, and case numbers are such sets when the likely values are known or few. The same identifier hashed the same way produces the same hash, so a reader who can try the set learns which value was hashed.

A pseudonym that the producer can reverse, because the producer holds the mapping from pseudonym to identifier, hides the identifier from a reader who lacks that mapping. It does not hide the identifier from the producer.

Threat model T-19 describes the same kind of attack against a commitment of a low-entropy value, and it names a per-element salt as a mitigation. This section states the limitation. It does not adopt that salt, and it does not set a length. Salt length remains open item OI-2.

The annotation marks this row fully covered. The label in the SRS table is Informative. This draft keeps that label. The statement does not add a claim.

**Sources.** SRS §8.3.3. Threat model v0.1.2 T-19. Assurance contract §5.4 (NG-4).

### 10.3 PRV-ID-3 Cross-package linkability

**Classification.** Informative.

**Requirement.** This baseline records the linkability risk. The record is guidance. It is not a conformance condition, and an implementation is not failed for omitting a separate linkability report.

The same pseudonym in two packages lets a reader treat those packages as carrying the same identifier. The same `chain_id` in two packages links those packages. A transparency-log receipt that a reader can match to a log entry links the package that carries the receipt to that entry. A shared receipt or a shared `chain_id` can link one package to another.

Privacy model T-29 records receipt linkage and leaves the residual accepted or assigned to a restricted lookup. This section documents the risk. It does not choose that lookup, and it does not change the receipt rules in trust model §5.2 or the anchoring rule in §6.3.

The annotation marks this row partial: the risk is identified and not given a mitigation. That gap is open item OI-17. The SRS label is Informative. This draft keeps that label. The record does not add a claim.

**Sources.** SRS §8.3.3. Threat model v0.1.2 T-20. Privacy model v0.1 T-29. Trust model v0.2 §5.2. §6.3 of this baseline.

---

## 11. Boundary crossing

### 11.1 PRV-BND-1 Data that crosses the insurer boundary

**Classification.** Normative.

The scope is the insurer-hosted deployment. The parenthetical in the SRS table is that scope. It is not a fourth label.

**Requirement.** In the insurer-hosted deployment, data that crosses the insurer's trust boundary is limited to headers, structural metadata, and salted hashes.

Headers are the signed header fields in §4.1 and the signatures that bind them. Structural metadata names an element's class, its evidence state, and its position in the package. It does not include the clinical value. Clinical content stays inside the insurer environment. That is the rationale recorded with CD-4.

A salted hash may cross. The salt and the clinical value stay inside the insurer environment. This requirement does not set the salt length or the salt's randomness. Those remain open item OI-2.

CD-4, in the confirmed-decisions register dated 2026-10-20, says "Headers and salted hashes only (privacy model §5.3)." The register rationale says metadata, structural evidence, and salted hashes. The SRS sentence lists headers, structural metadata, and salted hashes. This draft uses the SRS list. It does not rewrite the register. The wording difference is open item OI-19.

The register status is PENDING AFFIRMATION. The affirmation boxes for CD-1 through CD-4 are empty. Affirmation is W1-T30. This requirement cites CD-4. It does not affirm CD-1 through CD-4. It does not change the insurer-hosted role mapping, and it does not choose trust-model open item OI-7.

The insurer-hosted mapping is the companion from W1-T29. Another topology is outside this requirement. SEC-OPS-3 remains the topology assessment.

The annotation marks this row partial. Threat model §2.1 step 6 states the principle and does not state this requirement. The text above is SRS §8.3.4. That gap is open item OI-18.

Crossing the boundary does not establish compliance with HIPAA or any other privacy regulation. That limit is NG-3. This requirement does not add a claim.

**Sources.** SRS §8.3.4. Confirmed-decisions register CD-4, status PENDING AFFIRMATION, 2026-10-20. Privacy model v0.1 §5.3. Insurer-hosted role mapping v0.1 §6. Assurance contract §5.3 (NG-3).

### 11.2 PRV-BND-2 Disclosure profile for the crossing

**Classification.** Normative.

**Requirement.** When data is shared across a boundary, the disclosure profile applied for that sharing is recorded in the evidence package.

The crossing this baseline defines is §11.1. The SRS label on this requirement has no deployment parenthetical. A later topology names its own boundary in its own mapping. That assessment is SEC-OPS-3.

The profile is a disclosure profile under §9. The redaction list cites its identifier, and the profile is included and integrity-protected, under §9.2. This requirement does not create a second profile mechanism.

A package that does not cross that boundary is not given a cross-boundary profile by this requirement. When no profile is declared, the privacy positive cell in assurance contract §8 is not established.

The annotation has no threat-model source for this row. The text is SRS §8.3.4. That gap is open item OI-18.

**Sources.** SRS §8.3.4. §9 of this baseline. Assurance contract §8.

### 11.3 PRV-BND-3 Verification without the clinical content

**Classification.** Normative.

**Requirement.** When the verifier does not have the clinical content, the verifier checks the bytes in the package. The verifier does not check the withheld content.

The verifier can check the following.

- The integrity of the headers, the structural metadata, and the salted hashes in the package. Those checks are the P-1 checks on those bytes.
- The signature binding of those bytes. That check is P-2.
- For an element whose state is `redacted`, that its commitment was bound into the signed bytes. That check is §9.3. The element stays `redacted`.
- The completeness state under the completeness draft §3. A `redacted` class still counts toward C-CMP-1 `COMPLETE`. Reporting it as `expected_not_captured` fails C-CMP-2.

The verifier cannot check the following.

- The clinical content. The verifier has no content bytes.
- That a salted hash matches the clinical value. The value and the salt are not in the package. The hash bytes that are in the package remain subject to P-1.
- That the withheld content is true. That limit is NG-1.
- That the withheld content satisfies a privacy regulation. That limit is NG-3.

C-PRV-2 stays a check of a policy or model artifact supplied with the package. A salted hash of withheld clinical content does not make that claim `RESOLVED`. This requirement does not rewrite C-PRV-2. The commitment mechanisms remain the open list in the completeness draft §3.3.2. Encryption is not specified. That mechanism remains open item OI-4.

The annotation marks this row partial, through threat model §2.1 step 8 and T-26. The text above is SRS §8.3.4. That gap is open item OI-18. This requirement does not add a claim.

**Sources.** SRS §8.3.4. §9.3 of this baseline. Completeness draft §3.3.2. Assurance contract §5.1 (NG-1), §5.3 (NG-3), §6.2 (P-1), §6.3 (P-2), and §6.6 (C-CMP-1, C-CMP-2).

---

## 12. Open issues

| ID | Issue | Deferred to |
|----|-------|-------------|
| OI-1 | The W1-T10 annotation numbered six cryptographic topics differently from SRS §8.2.1. Annotation SEC-CRYPTO-1 (signature algorithms) is SRS SEC-CRYPTO-4. Annotation SEC-CRYPTO-2 (hash algorithms) is SRS SEC-CRYPTO-3. Annotation SEC-CRYPTO-4 (key lifecycle) is split across SRS SEC-CRYPTO-1 and SEC-CRYPTO-2. Annotation SEC-CRYPTO-5 (agility) is §3.7. Annotation SEC-CRYPTO-6 matches SRS SEC-CRYPTO-6. This draft uses the SRS numbers. | This section. The annotation is not renumbered here. |
| OI-2 | Element-salt length and randomness are threat-model assumption A-7. The annotation called that its SEC-CRYPTO-3. SRS §8.2.1 has no salt row. §3.3 does not absorb A-7. §11.1 allows a salted hash to cross the insurer boundary and does not set the length. | The length and the randomness remain open. |
| OI-3 | Re-anchoring after a recommended algorithm weakens is threat model T-23. The procedure is not specified. | Later baseline work. The threat model marks it P1. |
| OI-4 | The annotation maps content encryption under a per-package data key to its SEC-CRYPTO-2. SRS SEC-CRYPTO-2 is revocation. §8 separates metadata from clinical content. §9 checks a redacted commitment. §10 allows a pseudonym in the signed bytes. §11 keeps clinical content inside the insurer environment. None of these sections specifies encryption. | A later decision to add the mechanism. |
| OI-5 | The package-seal role is unassigned. SEC-CRYPTO-1 binds keys for R-2 and R-4 only. SEC-INTEG-2 defines what the package seal covers and does not name the holder. | Trust model OI-7. |
| OI-6 | The W1-T10 annotation used SEC-INTEG-1 through SEC-INTEG-5 for evidence protection, hash linking, seal enforcement, anti-fork, and non-equivocation. SRS §8.2.2 uses those identifiers for record coverage, the package-seal relationship, verification from the published specification and trust anchors, machine-readable results, and completeness reporting. This draft uses the SRS topics. Seal enforcement and anti-fork stay with R-4. Non-equivocation stays with P-6. | This section. The annotation is not renumbered here. |
| OI-7 | The W1-T10 annotation used SEC-PROV-1 for source identification, SEC-PROV-2 for content-hash references to policies and models, and SEC-PROV-3 for build and supply-chain provenance, and it called SEC-PROV-3 informative. SRS §8.2.3 uses those identifiers for import provenance, the `unverified_import` label, and the tool versions, configurations, and MCP tool hashes used in production. The SRS label on SEC-PROV-3 is Implementation-dependent. This draft uses the SRS topics and that label. | This section. The annotation is not renumbered here. |
| OI-8 | SEC-PROV-2 prohibits an `unverified_import` from contributing to a claim that requires verified provenance. The twelve claims do not use that phrase. C-PRV-1 stays a declaration, and the label does not rewrite C-PRV-1 or C-PRV-2. The set of claims the prohibition changes is not listed. | Review of SEC-PROV-2 against assurance contract §6.5. |
| OI-9 | SEC-TEMP-4 requires an evidence event, with a timestamp, for an administrative or configuration change that affects capture or signing. The W1-T10 annotation records no threat-model source for that requirement. The requirement is drafted from SRS §8.2.4. The annotation's topics for SEC-TEMP-1 through SEC-TEMP-3 match §6. | This section. The annotation is not renumbered here. |
| OI-10 | SEC-OPS-1 specifies access control. Threat-model assumption A-2 is separate storage domains and stays informative. The annotation says explicit access control is missing from the threat model. SEC-OPS-2 has no threat-model source. Both requirements are drafted from SRS §8.2.5. The annotation's operational topics match §7. | This section. The annotation is not renumbered here. |
| OI-11 | The annotation marks PRV-MIN-1 partial, through encrypted content and clear commitments, and it has no threat-model source for PRV-MIN-2 or PRV-MIN-3. §8 drafts all three from SRS §8.3.1 as Normative and does not specify encryption. | This section. The annotation is not renumbered here. |
| OI-12 | SRS §8.3.1 says "declared assurance level." The assurance contract does not define that phrase. §8.2 reads it as the claims in scope, including the milestone. | Review of §8.2 against assurance contract §6.8. |
| OI-13 | A PRV-MIN-3 reference leaves external bytes out of the package. C-PRV-2 is `RESOLVED` when a cited policy or model artifact is supplied with the package. §8.3 does not rewrite that claim. | Review of §8.3 against assurance contract §6.5. |
| OI-14 | A disclosure profile may mark a class excluded. Completeness `excluded` means the class was not intended to be collected. §9.1 states no match between the profile word and a state code. | Review of §9.1 against completeness draft §3.3.3. |
| OI-15 | The annotation marks PRV-DSC-2 partial. It says integrity protection of a disclosure profile is implied and not stated as its own threat-model rule. §9.2 drafts the requirement from SRS §8.3.2 as Normative. The annotation's topics for PRV-DSC-1, PRV-DSC-3, and PRV-DSC-4 match §9. | This section. The annotation is not renumbered here. |
| OI-16 | The annotation marks PRV-ID-1 partial. Its source is a random `chain_id`, unlinkable to a member identifier. §10.1 requires a pseudonym for a patient identifier, a provider identifier, or a case number. A random `chain_id` does not meet that requirement. The requirement is drafted from SRS §8.3.3 as Normative. | This section. The annotation is not renumbered here. |
| OI-17 | The annotation marks PRV-ID-3 partial. T-20 and T-29 identify cross-package linkability, including receipt linkage, and do not require a mitigation. §10.3 documents the risk. The SRS label stays Informative. | This section. The annotation is not renumbered here. |
| OI-18 | The annotation marks PRV-BND-1 partial, through threat model §2.1 step 6. It has no threat-model source for PRV-BND-2. It marks PRV-BND-3 partial, through §2.1 step 8 and T-26. §11 drafts all three from SRS §8.3.4 as Normative. | This section. The annotation is not renumbered here. |
| OI-19 | CD-4's decision cell says headers and salted hashes only. Its rationale says metadata, structural evidence, and salted hashes. SRS §8.3.4 lists headers, structural metadata, and salted hashes. §11.1 uses the SRS list and does not rewrite the register. The register remains PENDING AFFIRMATION. | W1-T30. The affirmation boxes stay empty. |

---

## 13. References

- ADEP-PHASE0-SRS-v0.1 §5.5, §6, §8.1, §8.2.1, §8.2.2, §8.2.3, §8.2.4, §8.2.5, §8.3.1, §8.3.2, §8.3.3, §8.3.4, §10.1 (MC-6, MC-7, MC-8, MC-9, MC-10, MC-11)
- Threat model v0.1.2 §2.1, §6, §8.4, §8.5, §8.6 (T-19, T-20, T-26, T-29), §10 (TV-SIG-02, TV-SIG-03, TV-CAN-01, TV-CAN-02, TV-CAN-03)
- W1-T10 annotation, cryptographic, integrity, provenance, temporal, operational, data-minimization, disclosure-profile, identifier, and boundary-crossing extraction notes
- Privacy model v0.1 §5.3 (what integrity infrastructure sees) and §11 (T-29)
- Confirmed-decisions register CD-4, status PENDING AFFIRMATION, 2026-10-20
- Assurance contract v0.2 §2.3 (P-1), §2.4 (P-2), §2.6 (P-4), §2.8 (P-6), §5.1 (NG-1), §5.3 (NG-3), §5.4 (NG-4), §6 (twelve claims), §6.1 (claim template and result tokens), §6.3 (C-AUT-1), §6.4 (C-TRS-2, C-AUT-3), §6.5 (C-PRV-1, C-PRV-2), §6.6 (C-CMP-1, C-CMP-2), §6.7 (C-TMP-1, C-LOG-1), §6.8 (milestones), §6.9 (MC-8, MC-10), §7 (verification context), §8 (claim boundaries, including the privacy boundary), §9 OI-7, and §9 OI-8
- Trust model v0.2 §4 rows C-INT-4 and C-DSC-1, §5 (signature types), §5.2 (package seal and transparency log receipt), §5.3, §6.2 (TM-7), and §7 OI-7
- Insurer-hosted role mapping v0.1 §5 and §6
- Completeness requirements v0.2 §3 (states) and §4 (assessment), first draft final (W3-T02)
- RFC 8785, JSON Canonicalization Scheme

---

*End of first draft final through W3-T03 — ADEP-WI4-SPB-v0.1*
