# Open ADEP Trust Model and Deployment-Neutral Assurance Requirements v0.2

**Document Identifier:** ADEP-WI3-TM-v0.2  
**Status:** DRAFT — first assembly (W2-T28)  
**Date:** 2026-10-24  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §7.2, §7.3, §7.5, §7.6  
**Author:** ARCH (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This is the assembled trust-model draft. It contains the ten roles, the six separations, the five signature scopes, and requirements TM-1 through TM-7. Open items OI-1 through OI-7 stay open. The insurer-hosted role-to-party mapping remains the companion document `dt-insurer-hosted-role-mapping-v01.md`. It is not part of this specification.

**Inputs:** SRS §7.2, §7.3, §7.5, and §7.6; threat model v0.1.2 §2.1, §2.2, and assumptions A-2, A-3, A-4, and A-6; confirmed decision CD-2; W1-T10 annotation §2.2; assurance contract v0.1 §3.2; REC-005, REC-025, and REC-026.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.2-draft.1 | 2026-10-22 | ARCH | W1-T15. R-1 through R-10, each with a responsibility and security implications. |
| 0.2-draft.2 | 2026-10-22 | ARCH | W1-T21. Six separations from SRS §7.3, with rationale. Dual attestation is two holders of R-2. |
| 0.2-draft.3 | 2026-10-22 | ARCH | W1-T22. Five signature types, each with a positive scope and a negative scope. Package seal added. |
| 0.2-draft.4 | 2026-10-23 | ARCH | W1-T28. TM-1 through TM-7, each labeled REQUIRED. |
| 0.2-draft.5 | 2026-10-23 | ARCH | W1-T29. Pointer to the insurer-hosted companion mapping. The mapping is not part of this specification. |
| 0.2-draft.6 | 2026-10-24 | ARCH | W2-T28. First assembly. Section map, and cross-references aligned to the assurance contract. Open items OI-1 through OI-7 stay open. |
| 0.2-draft.7 | 2026-10-24 | ARCH + LEAD | W2-T29. Cross-reference check against the assurance contract. No section number changed. The report is ADEP-XREF-WI1-WI3-v0.1. |

---

## 1. Purpose

This document states the trust model. It is normative except where a section says it is informative. §3 is informative.

| Section | What it contains |
|---------|------------------|
| §2 | Ten roles, R-1 through R-10. |
| §3 | v0.1 party names. Informative. |
| §4 | Six role separations. |
| §5 | Five signature scopes. |
| §6 | Deployment-neutral requirements TM-1 through TM-7. |
| §7 | Open items OI-1 through OI-7. |
| §8 | References. |

§2 defines the functional roles. A role is a responsibility, not a party, a product, or a place where software runs. One party may hold more than one role. One role may be held by more than one party. Which combinations must be split across different parties, and for which claim, is §4. What each signature attests is §5. Requirements that apply in every topology are §6.

---

## 2. Role definitions

### 2.1 Normative rules

1. Open ADEP defines exactly ten trust-model roles, R-1 through R-10.
2. Each role has a responsibility and a statement of its security implications.
3. Role text does not name a vendor, a product, or a deployment location.
4. Holding a role does not, by itself, make that party trusted. TM-5 requires the three-way classification. The assignment of each role is open item OI-4.

### 2.2 Summary

| ID | Role | Responsibility | Security implications |
|----|------|----------------|----------------------|
| R-1 | Evidence producer | Creates or captures an evidence record from a source system. | Has access to the source data. Evidence integrity depends on the producer's correct operation at capture. |
| R-2 | Evidence signer | Applies a signature or other defined integrity protection to evidence records or packages. | Controls a signing key. May be instantiated more than once. Signature meaning is attestation scope, not a claim that the payload is true. |
| R-3 | Evidence custodian | Preserves evidence records and packages in a durable, access-controlled store. | Responsible for availability and tamper-evident storage. Not the same role as the signer. |
| R-4 | Continuity countersigner | Enforces one chain per case, sequential extension, and sealing, and detects a fork of that chain. | Must be operationally independent of R-1. Otherwise the producer can fork a chain undetected. |
| R-5 | Log operator | Operates the append-only transparency log that records commitments. | Controls the log infrastructure. Log integrity depends on append-only operation. |
| R-6 | Independent log witness | Monitors the transparency log for consistency. | Must be operationally and organizationally independent of R-5. Detects a forked or rewritten log. |
| R-7 | Evidence verifier | Checks a package against the defined evidence properties. | Needs the published verification material. Does not rely on the producer's proprietary systems to perform the check. |
| R-8 | Evidence consumer | Uses verification results for an authorized purpose. | Must read the claim boundaries and not treat a verification result as a broader conclusion. |
| R-9 | Disclosure issuer | Chooses what is redacted, under which disclosure profile, and applies that redaction. | Controls the privacy boundary. Redaction decisions are integrity-protected and auditable. |
| R-10 | Trust-anchor publisher | Publishes the registry of valid signing keys, certificate chains, and revocation information. | Root of trust for signer-trust assessment (P-3). The registry must be operationally secured. |

### 2.3 R-1 Evidence producer

**Responsibility.** Creates or captures an evidence record from a source system. Source systems include, as examples, an EHR, an AI model, or a utilization-management system. Capture points are parts of this role. They are not an eleventh role.

**Security implications.** The producer has access to the source data. What later roles can protect is what this role actually captured. A correct signature does not repair a record that was wrong at capture. Integrity of the evidence therefore depends on the producer's correct operation at the moment of capture.

**Informative.** Threat model v0.1.2 calls the organization that uses the AI the deployer, and calls the capture points by that name. Both sit inside this role. Assumption A-5 says capture points are honest at the moment of capture; if they are not, the non-goal on substantive correctness applies.

### 2.4 R-2 Evidence signer

**Responsibility.** Applies a signature, or another defined integrity protection, to an evidence record or package.

**Security implications.** The signer controls a signing key. This role may be instantiated more than once, with different keys, when a trust policy requires more than one signature. What a given signature attests is §5. It is not defined by this role. Whether that signer is accepted is property P-3 under a stated trust policy. A signature does not establish that the payload is true.

**Informative.** v0.1 keeps a deployer key and an operator key in separate key-management domains (assumption A-2). Which signature type in §5 each of those keys carries is open item OI-7. Key storage is infrastructure for the role, not a role of its own.

### 2.5 R-3 Evidence custodian

**Responsibility.** Preserves evidence records and packages in a durable store with access control.

**Security implications.** The custodian is responsible for availability of the store and for storage that makes tampering evident. Custody is not signing. The party that stores the bytes need not be the party that holds the signing key. A custodian who can change stored bytes without detection defeats later verification, so the store is inside the tamper-evidence regime rather than a silent archive.

**Informative.** v0.1 places the evidence store with the deployer. That placement is a deployment choice, not part of the role.

### 2.6 R-4 Continuity countersigner

**Responsibility.** Enforces the chain constraints: one chain for a case, extension only at the next position, and sealing. Detects a second chain or a conflicting event at the same position.

**Security implications.** R-4 must be operationally independent of R-1. If the producer also countersigns, that producer can fork a chain and the fork is not independently visible. This is the chain-level anti-fork guarantee. It is not the guarantee that every relying party saw the same log. That guarantee is R-6.

**Informative.** v0.1 calls this the witness signer, operated outside the deployer's administrative control even when capture runs on the deployer's premises (assumption A-3). The chain registry is this role's state. It is not a separate role. The witness countersignature's scope is the continuity counter-signature in §5.

### 2.7 R-5 Log operator

**Responsibility.** Operates the append-only transparency log. The log records commitments such as signed tree heads and inclusion proofs.

**Security implications.** The operator controls the log infrastructure. Integrity of the log depends on append-only operation: entries are added, not rewritten or dropped. Operating the log does not review the content of a package. The receipt's scope is §5. A log operator who can present two different histories is the reason R-6 exists.

**Informative.** v0.1 assigns the transparency log to the operator. Checkpoint signing is part of operating the log.

### 2.8 R-6 Independent log witness

**Responsibility.** Independently monitors the transparency log and checks that the checkpoints it sees are consistent with one append-only history.

**Security implications.** R-6 must be operationally and organizationally independent of R-5. If the log operator also witnesses the log, a forked or deleted history is not detected. The witness detects that misbehavior. It does not decide what the evidence means, and it does not replace R-4's check on the evidence chain. Assumption A-4 in v0.1 also requires independence from the organization that produces the evidence; the normative independence stated here is from R-5. The claim-level statement of that split is §4, row C-INT-4.

**Informative.** v0.1 calls this the log witness, as distinct from the witness signer (R-4). No specific witness party is named.

### 2.9 R-7 Evidence verifier

**Responsibility.** Checks an evidence package against the defined requirements: integrity (P-1), authenticity (P-2), signer trust (P-3), provenance (P-4), completeness (P-5), and temporal assurance (P-6), for the claims in scope.

**Security implications.** The verifier needs the verification material: trust anchors, published keys, and the schema. It performs that check without depending on the producer's proprietary systems. A check run by the producer on its own systems is a different independence level. It is still this role, and it does not become independent verification by being given the same name.

**Informative.** v0.1 folds verifiers into "relying party," together with the people who use the result. This taxonomy separates the checker (R-7) from the user of the result (R-8). A second implementation that verifies from the published specification is another holder of R-7.

### 2.10 R-8 Evidence consumer

**Responsibility.** Uses verification results for an authorized purpose, such as investigation, compliance, audit, or litigation.

**Security implications.** The consumer has to apply the claim boundaries in assurance contract v0.2 §8. A result that establishes one property does not establish the properties that property excludes. Using a verification result as proof of clinical correctness, legal compliance, or absolute completeness goes beyond what the result says.

**Informative.** v0.1's relying party includes regulators, auditors, appeal parties, courts, and technical reviewers. Those are consumers when they use a result, and verifiers when they run the check. The same organization may do both. They remain two roles.

### 2.11 R-9 Disclosure issuer

**Responsibility.** Decides which evidence is redacted, under which disclosure profile, and applies the redaction mechanism.

**Security implications.** This role controls the privacy boundary. A redaction decision is integrity-protected and auditable, so a later verifier can see what was withheld and under which profile. The issuer does not, by issuing a redaction, decide that the profile satisfies a privacy regulation. The disclosure profiles are security baseline PRV-DSC-1 through PRV-DSC-4. This role is who applies them.

**Informative.** Threat model v0.1.2 has no party whose job is this decision. The annotation records that as GAP-1. In the insurer-hosted sketch in SRS §7.4, the organization that controls redaction policy holds R-9. That sketch is not this section.

### 2.12 R-10 Trust-anchor publisher

**Responsibility.** Publishes and maintains the registry of valid signing keys, certificate chains, and revocation information.

**Security implications.** The registry is the root of trust for signer-trust assessment (P-3). It has to be operationally secured: publication, rotation, and revocation are attributable. A signer who also publishes the anchors that bless that signer can self-authorize. That split is §4, row C-TRS-1.

**Informative.** v0.1 assumption A-6 says relying parties obtain trust anchors out of band or from the log's key statements. It does not name a publisher. The annotation records that as GAP-2. This role is that publisher.

---

## 3. v0.1 parties (informative)

This table only points at the threat-model words. It is not the role-to-party mapping. That mapping is a separate document, one per deployment.

| v0.1 term | Roles in this section |
|-----------|------------------------|
| Deployer | R-1, and often a holder of R-2, plus R-3 and R-9 in the insurer-hosted sketch |
| Operator | A holder of R-2, plus R-4 and R-5 |
| Witness signer | R-4 |
| Log witness | R-6 |
| Relying party | R-7 and R-8 |
| Capture point | Part of R-1, not a role |
| Deployer or operator key store | Infrastructure for R-2 or R-4, not a role |
| (none) | R-10 |

---

## 4. Role-separation matrix

This section is normative. It records the six separations in SRS §7.3. A row names roles and a claim. It does not name a vendor, a product, or a deployment.

### 4.1 Rules

1. Different parties means two entities that are independent both operationally and organizationally. Two components administered by one organization are one party.
2. One party may hold several roles. A row in §4.2 withdraws that permission for the claim it names.
3. R-2 may have more than one holder. A row that lists R-2 twice means two holders, each with its own signing key.
4. R-4's role text requires operational independence from R-1, and R-6's role text requires operational and organizational independence from R-5. Every row in this matrix uses the same test: the named holders are different parties under rule 1.
5. The assurance contract v0.2 C-AUT-2 result is the payload-to-signature binding (P-2). That result stands whether or not the two holders are different parties. When they are one party, the dual-attestation policy in the first row is unmet. The P-2 result does not change.
6. For the other five rows, the separation is a precondition of the named claim. When the holders are one party, that claim is `NOT_EVALUATED`. A missing separation is not reported as `FAIL` of P-1 or P-2.
7. Collusion between the parties a row requires to be separate means the separation is unmet. The threat-model statement of collusion stays in that document.

### 4.2 Matrix

| Claim | Roles that must be different parties | Rationale |
|-------|--------------------------------------|-----------|
| C-AUT-2, dual attestation | Two holders of R-2 | A policy that asks for two signatures holds only when those keys belong to different parties. One party that holds both keys can produce both signatures. This row is that independence condition. The contract's C-AUT-2 checks only that each listed signature binds the same payload. |
| C-INT-3, anti-fork chain integrity | R-1 and R-4 | The evidence producer and the continuity countersigner are different parties. One party in both roles can fork the chain with no second party in a position to see the fork. |
| C-INT-4, log non-equivocation | R-5 and R-6 | The log operator and the independent log witness are different parties. One party in both roles can present two log histories with no second party in a position to compare them. This row is the log. The previous row is the evidence chain. |
| C-PRV-1, provenance-check independence | R-1 and R-7 | A provenance confirmation made by the producer is self-verification. An independent confirmation requires an evidence verifier that is a different party from the producer. The four independence levels are assurance contract v0.2 §7.3. |
| C-DSC-1, disclosure-check independence | R-9 and R-7 | The disclosure issuer and the evidence verifier are different parties. The party that chooses a redaction is a different party from the one that determines whether that redaction is valid. |
| C-TRS-1, signer-trust independence | R-10 and R-2 | The trust-anchor publisher and the evidence signer are different parties. A signer who publishes the anchors that authorize that signer can place its own key in the registry. |

Informative. The W1-T10 annotation connects the first row to one signing party producing both signatures, the chain row to a producer fork, and the log row to a log operator showing two histories. Those adversary identifiers remain in the threat model.

### 4.3 Claim labels and the v0.1 registry

The six rows are the SRS separations. Some labels do not name a v0.1 claim that says the same thing. This section adopts the separations. The claim sentences that do not have their own row remain assurance contract v0.2 open item OI-7.

| SRS label on the row | v0.1 claim with that identifier | What §4.2 separates |
|----------------------|---------------------------------|---------------------|
| C-AUT-2 | Each event is signed by both the deploying organization and DecisionTrace; neither can produce a valid event alone. | The independence half. Binding is C-AUT-2 in assurance contract v0.2. The requirement that the policy include both keys is a signer-trust (P-3) statement and is outside this matrix. |
| C-INT-3 | No v0.1 claim uses this identifier. The anti-fork sentences are C-CMP-3 and C-CMP-4. | R-1 from R-4. |
| C-INT-4 | No v0.1 claim uses this identifier. The same-history sentence is C-LOG-2. C-LOG-1 checks one verifier's append-only view and does not require R-6. | R-5 from R-6. |
| C-PRV-1 | Each event identifies its source type and the declared actor or component. The registry marks it as a declaration, with no adversary. | R-1 from R-7. The v0.1 sentence stays a declaration claim. |
| C-DSC-1 | Undisclosed elements reveal nothing beyond their existence, type, and position. | R-9 from R-7. The v0.1 sentence stays the selective-disclosure claim. |
| C-TRS-1 | No v0.1 claim uses this identifier. The traceability matrix already points property P-3 at C-TRS-1. | R-10 from R-2. |

---

## 5. Signature attestation

This section is normative. It defines the five signature types in SRS §7.5. A signature establishes its own row. It is not a general statement that the payload is true.

### 5.1 Rules

1. Open ADEP defines these five signature types, and no others.
2. Each type has a positive scope and a negative scope. A verifier may rely on the positive scope. The negative scope is outside what that signature establishes.
3. Acceptance of the signer under a trust policy is property P-3. Which roles must be held by different parties is §4. This table decides neither.
4. The holder column names a role. Which organization holds that role is the companion mapping.
5. `not_before_checkpoint` is an embedded header field. It is not a sixth signature type. Its statement is in §5.3.

### 5.2 Scopes

| Signature type | Holder | What it attests | What it does not attest |
|----------------|--------|-----------------|-------------------------|
| Evidence-record signature | R-2 | This signer signed this payload, including its content commitment, as presented at the capture interface. | That the payload is truthful, complete, or generated by a named upstream application. That a time value inside the payload is accurate. |
| Institutional co-signature | R-2 | This signer confirms receipt and acceptance of this payload for evidence purposes. | That the signer has verified the clinical correctness of the content. That this signer produced the payload at the capture interface. |
| Continuity counter-signature | R-4 | This record is at position N in chain C, and this signer observed no conflicting record at that position. | That the payload is truthful. That earlier records in the chain are correct. That the observation time is, by itself, a temporal-assurance result. |
| Package seal signature | Not assigned in this section | This package contains the declared evidence records, and their integrity relationships are as stated. | That the package is complete. Completeness is property P-5. |
| Transparency log receipt | R-5 operates the log that issues the inclusion | A commitment to this record or package was included in the log no later than checkpoint C. Where SRS §7.5 says "at time T," T is that checkpoint. | That the log operator reviewed the package content. That every verifier has seen the same log history. |

When a trust policy requires both an evidence-record signature and an institutional co-signature, the two signers are the two holders of R-2 in §4, row C-AUT-2.

### 5.3 Where the v0.1 rows went

Threat model §2.2 has four rows. Three of them land on signature types in §5.2. The fourth stays a header field. The package seal and the institutional co-signature are the SRS rows that §2.2 does not contain.

| This section | Threat model §2.2 |
|--------------|-------------------|
| Evidence-record signature | Deployer signature: "This event was produced by our system at the capture interface, with this content commitment." The positive cell keeps the content commitment and the capture interface. |
| Continuity counter-signature | Witness countersignature: the valid next link of the chain, and no conflicting event at that position. The v0.1 negative statement, that this signature does not attest truthfulness of content, is kept. The limit on earlier records is the SRS negative scope. |
| Transparency log receipt | Log inclusion: "This leaf existed in the log no later than checkpoint C." |
| `not_before_checkpoint` | The same embedded field, with no signer: "This event was created after checkpoint C′ existed." |
| Institutional co-signature | No §2.2 row. The scope is SRS §7.5. |
| Package seal signature | No §2.2 row. The scope is SRS §7.5. |

v0.1 states that temporal claims come from the log, and that `claimed_time` is advisory and supplied by the producer. That statement stands. A time value inside a signed payload remains a producer-supplied value.

The v0.1 lifecycle also has a sealing step. When a decision is final, a seal event fixes the chain length, and the continuity countersigner refuses later events for that chain. That step is a chain-length operation. It is not the package seal signature. The package seal signature attests that the package lists the records it contains and states their integrity relationships.

### 5.4 Assignment left open

v0.1 dual custody, assumption A-2, is a deployer key and an operator key. Assumption A-3 places the witness key with the operator, and §5.2 places the witness statement on R-4. Confirmed decision CD-2 assigns evidence-production attestation to one party and institutional attestation to the other. This section defines the five scopes. It does not decide which of those parties applies the evidence-record signature, which applies the institutional co-signature, or which role applies the package seal. That assignment is open item OI-7.

---

## 6. Deployment-neutral requirements

This section is normative. The seven requirements apply in every deployment topology. Each one is REQUIRED.

### 6.1 Requirements

| ID | Requirement | Level | Where this draft stands |
|----|-------------|-------|-------------------------|
| TM-1 | The trust model is expressible in abstract roles, with no vendor, product, or deployment location in the normative role text. | REQUIRED | Met by §2. Party names in §3 are informative. |
| TM-2 | Every signature in an evidence package has a defined attestation scope. | REQUIRED | Met by §5. The five scopes are the signature types. `not_before_checkpoint` is a header field, not a signature. |
| TM-3 | The role-separation matrix is satisfied for every assurance claim that depends on role separation. | REQUIRED | The six rows are §4. A claim acquires a separation only by a row in that matrix. Whether a row's label is a claim in the assurance contract is open item OI-6. |
| TM-4 | A role-to-party mapping is published for each deployment topology. | REQUIRED | The insurer-hosted mapping is the companion document `dt-insurer-hosted-role-mapping-v01.md`. It is not part of this specification. |
| TM-5 | The trust model identifies which roles are trusted, which are untrusted, and which are trust-but-verify. | REQUIRED | The requirement is this row. The classification of R-1 through R-10 is open item OI-4. |
| TM-6 | Changing the deployment topology does not require a change to evidence-package semantics or to the assurance contract. | REQUIRED | A topology change is a change to the TM-4 mapping. Package semantics stay in the schema. Property and claim semantics stay in the assurance contract. |
| TM-7 | The trust model addresses key generation, distribution, rotation, compromise, and revocation. | REQUIRED | The five stages are §6.2. Numbered cryptographic procedures stay in the security baseline. |

### 6.2 Key lifecycle (TM-7)

Each stage names the trust-model fact a verifier can use. It does not name an algorithm. Algorithm choice is NG-4 in the assurance contract, and the algorithm requirements are the security baseline.

| Stage | What the trust model requires |
|-------|-------------------------------|
| Generation | A signing key is generated for a named role. The roles that sign evidence are R-2 and R-4. Binding a key to a role is security baseline SEC-CRYPTO-1. Key storage is infrastructure for the role, not a role. |
| Distribution | R-10 publishes the key in the trust-anchor registry. A verifier uses that published material under the trust policy in the verification context. |
| Rotation | R-10 publishes the successor key. The trust policy states the interval, if any, during which both keys are accepted. |
| Compromise | R-10 records that the key is compromised, and the time of that record. Signatures that fail the trust policy after that time fail P-3. |
| Revocation | R-10 records the revocation. A signature made after the recorded revocation is not accepted under P-3. The effect on evidence signed before revocation is security baseline SEC-CRYPTO-2. This section does not write a second rule for that effect. |

---

## 7. Open issues

| ID | Issue | Deferred to |
|----|-------|-------------|
| OI-1 | The six separations are §4. | W1-T21 |
| OI-2 | The five signature scopes are §5. | W1-T22, REC-025 |
| OI-3 | The insurer-hosted mapping is the companion document (W1-T29). R-6 still has no named party. The normative model remains the ten roles. | Companion document. REC-021 |
| OI-4 | TM-5 is stated in §6. Which of R-1 through R-10 are trusted, untrusted, or trust-but-verify is not assigned. | Later trust-model classification |
| OI-5 | The ten-role catalog is the recorded resolution of the five-party conflict. | REC-025 |
| OI-6 | SRS labels C-INT-3, C-INT-4, and C-TRS-1 are not v0.1 claim identifiers. v0.1 C-PRV-1 and C-DSC-1 state different assertions from the matrix rows that use those labels. The separations themselves are adopted. Putting each separation on the seven-field claim template is later registry work. | Assurance contract v0.2 open item OI-7 |
| OI-7 | Which party applies the evidence-record signature, which applies the institutional co-signature, and which role applies the package seal. CD-2 and threat model §2.2 do not name the same assignment. This draft does not choose. | Companion mapping, SRS §7.4. CD-2 is reviewed in W1-T30. |

---

## 8. References

- ADEP-PHASE0-SRS-v0.1 §7.2, §7.3, §7.4, §7.5, §7.6, §8.2.1
- SRS §4, confirmed decision CD-2
- Threat model v0.1.2 §2.1, §2.2, assumptions A-2, A-3, A-4, A-6
- W1-T10 annotation §2.2, §3, §4, and GAP-1, GAP-2
- Assurance contract v0.1 §3.2 and §6
- Assurance contract v0.2 §5.4 (NG-4), §6.3 (C-AUT-2), §7.3 (independence levels), §8 (claim boundaries), and §9 OI-7
- Cross-reference report ADEP-XREF-WI1-WI3-v0.1 (W2-T29)
- Security baseline v0.1 SEC-CRYPTO-1, SEC-CRYPTO-2, and PRV-DSC-1 through PRV-DSC-4
- Reconciliation register REC-005, REC-021, REC-025, REC-026

---

*End of assembled draft through W2-T28 — ADEP-WI3-TM-v0.2*
