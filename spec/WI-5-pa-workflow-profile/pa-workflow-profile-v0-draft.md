# Open ADEP Prior-Authorization Workflow Profile v0

**Document Identifier:** ADEP-WI5-PA-v0  
**Status:** DRAFT — first assembly (W3-T04), class-list schema (W3-T05)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §9.2, §9.3, §9.4, §9.5, §9.6, §9.7, §9.8, §10.1.3  
**Author:** DOMAIN (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This is the assembled prior-authorization profile. It contains the fifteen core evidence classes, their temporal ordering, the five agentic classes, the three exception paths, the versioning rules, and the class-list schema in `schemas/expected-evidence-classes.schema.json`. Open items OI-1 through OI-12 stay open.

**Inputs:** SRS §9.2, §9.3, §9.4, §9.5, §9.6, §9.7, §9.8, and §10.1.3; completeness requirements v0.2 §2.2.1 (profile reference), §2.2.2 (declared collection scope), §2.2.3 (expected-class list), §3 (seven state codes, including `arrived_late`), §4 (assessment), and §6 (claim levels); assurance contract v0.2 §5.1 (NG-1) and §6.7 (C-TMP-1); security baseline SEC-PROV-3.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.1-draft.1 | 2026-10-24 | DOMAIN | W2-T20. Fifteen core evidence classes. Each row has an identifier, a name, a description, a criticality, and a state if absent. |
| 0.1-draft.2 | 2026-10-24 | DOMAIN | W2-T21. Expected sequence, concurrency, and ordering-violation flags. |
| 0.1-draft.3 | 2026-10-24 | DOMAIN | W2-T30. PA-EC-20 through PA-EC-24. Defined, and not required in M2 test coverage. |
| 0.1-draft.4 | 2026-10-24 | DOMAIN | W2-T31. Urgent PA, emergency exception, and retrospective review. The ordinary sequence in §4 is unchanged. |
| 0.1-draft.5 | 2026-10-25 | DOMAIN | W3-T04. First assembly. Versioning rules from SRS §9.7. No eighth declaration element. Open items OI-1 through OI-11 stay open. OI-12 records the unspecified forward-compatibility cases. |
| 0.1-draft.6 | 2026-10-25 | DOMAIN + LEAD | W3-T05. Class-list schema, draft 2020-12. Twenty identifiers. The list is not required to contain every class. |

---

## 1. Identity

This profile is the basic prior-authorization workflow named in SRS §9.2.

| Field | Value |
|-------|-------|
| Profile ID | `adep.profile.pa.basic.v0` |
| Profile name | Basic Prior-Authorization Decision Evidence Profile |
| Version | 0 |

The version value is 0, from SRS §9.2. The rules for a profile version are §7.

The classes below are what this profile expects for a basic prior-authorization case. A scope declaration names this profile, including this version, and lists the class identifiers that package instance expects. The declaration's list is completeness requirements v0.2 §2.2.3. Each identifier on a list for this profile is one of the twenty values in `schemas/expected-evidence-classes.schema.json`. The list may be empty, and it is not required to name every class. Omitting a class this profile expects for the case remains completeness open item OI-2. This section does not choose how that omission is represented.

---

## 2. Rules

1. The core catalog is PA-EC-01 through PA-EC-15. Each row has five fields: class identifier, name, description, criticality, and state if absent.
2. A class has one state code. The codes are the seven in the completeness draft §3. This profile has no code named missing.
3. The state if absent is the code used when the package has no element of that class. When the row names a condition, §3.2 says which code that condition selects.
4. Criticality is the label in the row: Critical, High, or Medium, including a label that applies only when a condition holds. Criticality does not change C-CMP-1, C-CMP-2, or the four assessment verdicts.
5. A remark in a source cell, such as "cannot claim scope-completeness" or "essential for decision reconstruction," is not a sixth field. §3.3 says what this profile does with those remarks.
6. When §3.2 says a class is not expected for that package, the class is not placed on the declaration's expected-evidence-class list. The state `excluded` is the producer's statement that the class was not intended to be collected. Placing the same class on the expected list and marking it `excluded` is completeness open item OI-7. This profile does not use that combination.
7. Temporal order of the core classes is §4. The agentic classes are §5. Urgent PA, the emergency exception, and retrospective review are §6. Those paths do not rewrite §4.
8. One class is one unit in the assessment. Several documents may belong to one class. The producer still assigns one code to the class. This profile does not define a fraction inside a class.
9. Versioning is §7. The class-list schema is `schemas/expected-evidence-classes.schema.json`. The dialect is JSON Schema draft 2020-12.

---

## 3. Core evidence classes

### 3.1 Catalog

| Class ID | Name | Description | Criticality | State if absent |
|----------|------|-------------|-------------|-----------------|
| PA-EC-01 | PA request receipt | The initial prior-authorization request as received by the payer. An X12 278 request is one form. An equivalent request is also this class. | Critical | `expected_not_captured` |
| PA-EC-02 | Clinical documentation | The clinical records, medical history, and supporting documentation submitted with or referenced by the PA request. | Critical | `expected_not_captured`, or `unavailable` when capture was attempted and the source was unavailable (§3.2) |
| PA-EC-03 | Applicable coverage policy | The payer's coverage determination guidelines, medical policies, or clinical criteria applied to this request. | High | `expected_not_captured` |
| PA-EC-04 | AI model input | The data provided to the AI model as input for its recommendation, including any preprocessing or transformation. | Critical | `expected_not_captured` |
| PA-EC-05 | AI model identification | Model name, version, configuration parameters, and any model card or documentation that identifies the model. | Critical | `expected_not_captured` |
| PA-EC-06 | AI model output | The AI model's recommendation, confidence scores, and any explanation or reasoning the model provided. | Critical | `expected_not_captured` |
| PA-EC-07 | Human reviewer assignment | The record of which human reviewer, if any, was assigned to review the AI recommendation. | High | `expected_not_captured` when human review occurred; `excluded` when the case is fully automated (§3.2) |
| PA-EC-08 | Human review action | The human reviewer's decision to accept, modify, or override the AI recommendation, with any stated rationale. | Critical when review occurred | `expected_not_captured` when review occurred and the action is absent; `excluded` when no human review occurred (§3.2) |
| PA-EC-09 | Final determination | The final PA decision issued by the payer: approve, deny, pend, or partial approve. | Critical | `expected_not_captured` |
| PA-EC-10 | Determination rationale | The stated clinical and administrative rationale for the final determination. | High | `expected_not_captured` |
| PA-EC-11 | Notification to requestor | The record that the PA determination was communicated to the requesting provider, the patient, or both. | Medium | `expected_not_captured`, or `unavailable` when capture was attempted and the source was unavailable (§3.2) |
| PA-EC-12 | Appeal receipt | The record of an appeal filed against the determination. | High when an appeal was filed | `excluded` when no appeal was filed; `expected_not_captured` when an appeal was filed and the receipt is absent (§3.2) |
| PA-EC-13 | Adverse determination notice | The adverse benefit determination notice for a denial. SRS §9.3 names CMS-0062-P as an example of a regulation that may require such a notice. | Critical when the determination is a denial | `expected_not_captured` when the determination is a denial and the notice is absent; `excluded` when the determination is not a denial (§3.2) |
| PA-EC-14 | Timestamp anchors | External timestamp receipts or transparency-log receipts that anchor key events. A package may include more than one such receipt. | High | `unavailable` when the anchoring service is down; `expected_not_captured` when the service is operating and no receipt is included (§3.2) |
| PA-EC-15 | Coverage indicators | Signed counters or heartbeats from upstream systems, for the reconciliation in the completeness draft §5. | Medium | `excluded` when coverage indicators are not configured; `expected_not_captured` when they are configured and none are included (§3.2) |

### 3.2 Conditions

An element has one code. The conditions below select that code. They do not assign two codes to one class.

**Source unavailable.** PA-EC-02 and PA-EC-11 use `unavailable` when the class was expected, capture was attempted, and the source was unavailable. A reason is recorded when one is known. A missing reason does not change the code. That is the completeness draft §3.3.5. Every other absence of those two classes is `expected_not_captured`.

**Human review.** Human review occurred when a person was assigned to review the AI recommendation or did review it. The case is fully automated when no such review occurred.

PA-EC-07 is `expected_not_captured` when review occurred and the assignment record is absent. It is `excluded`, and it is not on the expected list, when the case is fully automated. Both codes are in the SRS cell.

PA-EC-08 is `expected_not_captured` when review occurred and the action is absent. That code is the SRS cell. When no human review occurred, this draft uses `excluded` and leaves the class off the expected list. The SRS cell does not write that second code. The reading is open item OI-1.

**Appeal.** PA-EC-12 is `excluded`, and off the expected list, when no appeal was filed. That code is the SRS cell. When an appeal was filed and the receipt is absent, this draft uses `expected_not_captured`, because the class was then expected and was not captured. The SRS cell does not write that second code. The reading is open item OI-1.

**Denial.** PA-EC-13 is `expected_not_captured` when the final determination is a denial and the notice is absent. That code is the SRS cell. When the determination is not a denial, this draft uses `excluded` and leaves the class off the expected list. The SRS cell does not write that second code. The reading is open item OI-1. The class records the notice. It does not establish that the notice satisfied a regulation.

**Anchors.** PA-EC-14 is `unavailable` when the external anchoring service is down. That code is the SRS cell. When the service is operating and the package includes no receipt of this class, this draft uses `expected_not_captured`. The SRS cell does not write that second code. The reading is open item OI-1. Where no anchoring checkpoint is in scope, the time aspect of C-TMP-1 stays `NOT_EVALUATED`. A `claimed_time` does not fill that result. An anchor may attach to any present class, including more than one. §4 states that attachment. It does not name a class that must carry an anchor.

**Coverage indicators.** PA-EC-15 is `excluded`, and off the expected list, when coverage indicators are not configured. That code is the SRS cell. When they are configured and none are included, this draft uses `expected_not_captured`. The SRS cell does not write that second code. The reading is open item OI-1.

The reconciliation method and the tolerance thresholds are CI-6. They are not in this table. This class does not set them, and it does not close NG-2. Full coverage-indicator reconciliation remains outside the M2 target.

### 3.3 Remarks that are not fields

PA-EC-01's source cell says a package cannot claim scope-completeness when the request receipt is absent. The state is `expected_not_captured`. The claim level Scope-complete is then not assigned. That level is the completeness draft §6. This remark does not add a verdict.

PA-EC-04's source cell says the model input is essential for decision reconstruction. The state is `expected_not_captured`. Reconstruction is not an evidence property. The class records the input. It does not establish that the recommendation was clinically right or clinically wrong. That limit is NG-1.

PA-EC-09's source cell says the package is incomplete without the final determination. The state is `expected_not_captured`. C-CMP-1 and C-CMP-2 then use `INCOMPLETE` under the completeness draft §3. This remark does not add a state.

PA-EC-06 records the explanation or reasoning the model provided. Recording that text does not establish that the model's reasoning was adequate. NG-1 still applies.

---

## 4. Temporal ordering

Normative. This is SRS §9.4 for the basic path. Urgent, emergency, and retrospective paths are §6. They do not change the rules in this section.

### 4.1 Diagram

The sequence below is the ordering diagram. An arrow is the backbone. A bracket is the concurrency or condition rule in §4.2. PA-EC-12 and PA-EC-15 do not appear. Their place in the sequence is open item OI-2. PA-EC-20 through PA-EC-24 do not appear. Their place in the sequence is open item OI-6.

```
PA-EC-01 (request receipt)
  → PA-EC-02 (clinical documentation)  [same time as PA-EC-01, or later]
  → PA-EC-03 (coverage policy)
  → PA-EC-04 (AI model input)
  → PA-EC-05 (AI model identification)  [no required order against PA-EC-04]
  → PA-EC-06 (AI model output)
  → PA-EC-07 (reviewer assignment)  [only when human review occurred]
  → PA-EC-08 (human review action)  [only when human review occurred]
  → PA-EC-09 (final determination)
  → PA-EC-10 (determination rationale)  [no required order against PA-EC-09]
  → PA-EC-11 (notification)
  → PA-EC-13 (adverse notice)  [only when the determination is a denial; same time as PA-EC-11, or later]
  → PA-EC-14 (timestamp anchors)  [may attach at more than one point; not one step]
```

### 4.2 Precedence and concurrency

The comparison uses the recorded time on each present element when that time is visible to the verifier. When the profile's event carries `claimed_time` as that recorded time, the comparison uses it. The comparison does not establish that the time is accurate. It is not a P-6 result. C-TMP-1 stays at M3, and a `claimed_time` alone remains outside that claim.

A class that §3.2 leaves off the expected list is skipped. A class that is expected and absent keeps the state in §3. That absence is not an ordering violation.

For two present classes whose times are both visible:

| Earlier class | Later class | Rule |
|---------------|-------------|------|
| PA-EC-01 | PA-EC-02 | PA-EC-02 is not earlier than PA-EC-01. The same time is allowed. |
| PA-EC-02 | PA-EC-03 | PA-EC-03 is not earlier than PA-EC-02. When PA-EC-02 is absent, PA-EC-03 is not earlier than PA-EC-01. |
| PA-EC-03 | PA-EC-04 | PA-EC-04 is not earlier than PA-EC-03. |
| PA-EC-04 | PA-EC-05 | Neither order is a violation. The same time is allowed. |
| PA-EC-04 | PA-EC-06 | PA-EC-06 is not earlier than PA-EC-04. |
| PA-EC-05 | PA-EC-06 | When PA-EC-05 is present, PA-EC-06 is not earlier than PA-EC-05. |
| PA-EC-06 | PA-EC-07 | When human review occurred, PA-EC-07 is not earlier than PA-EC-06. |
| PA-EC-07 | PA-EC-08 | When human review occurred, PA-EC-08 is not earlier than PA-EC-07. |
| PA-EC-08 | PA-EC-09 | When human review occurred, PA-EC-09 is not earlier than PA-EC-08. When it did not, PA-EC-09 is not earlier than PA-EC-06. |
| PA-EC-09 | PA-EC-10 | Neither order is a violation. The same time is allowed. |
| PA-EC-09 | PA-EC-11 | PA-EC-11 is not earlier than PA-EC-09. PA-EC-11 is not ordered against PA-EC-10. |
| PA-EC-11 | PA-EC-13 | When the determination is a denial, PA-EC-13 is not earlier than PA-EC-11. The same time is allowed. |

SRS §9.4 says PA-EC-02 may arrive concurrently or shortly after PA-EC-01. This section allows the same time or a later time. It states no maximum gap. That missing duration is open item OI-3.

PA-EC-14 is not a single step at the end of the diagram. A package may include more than one anchor, and an anchor may attach to any present class. This section does not require a named class to carry one.

### 4.3 Ordering violations

A pair that breaks a rule in §4.2 is an ordering violation. The completeness assessment flags that pair.

The flag names the two classes and the two recorded times. It does not change either class's state. A present class stays `present`. A `redacted` class stays `redacted`. The flag does not assign `arrived_late`. That code remains the completeness draft §3.3.6. The flag does not change the four verdicts, C-CMP-1, or C-CMP-2.

The completeness report has eight fields. None of them is this flag. This profile does not add a field to that report. Where the flag is carried is open item OI-4.

When either recorded time is not visible, that pair is not flagged. It is reported as not compared, under the same open item.

---

## 5. Agentic AI extensions

Normative. This is SRS §9.5. The five classes are defined. SRS §10.1.3 places them outside M2 test coverage. Defining them does not add a claim and does not move a milestone.

### 5.1 Catalog

The SRS table has four columns. This catalog uses those four. It does not add a state if absent. That missing column is open item OI-5.

| Class ID | Name | Description | Criticality |
|----------|------|-------------|-------------|
| PA-EC-20 | Agent delegation record | Record of one AI agent delegating a sub-task to another agent, including the delegating agent's identity, the sub-task specification, and the delegation timestamp. | Critical when delegation occurred |
| PA-EC-21 | Sub-agent input | The data provided to the delegated sub-agent. | Critical when delegation occurred |
| PA-EC-22 | Sub-agent output | The delegated sub-agent's result, including its own confidence and reasoning. | Critical when delegation occurred |
| PA-EC-23 | Agent aggregation record | How the primary agent combined or reconciled outputs from multiple sub-agents into its final recommendation. | High when more than one sub-agent was used |
| PA-EC-24 | Agent tool invocation record | Record of external tools invoked by any agent, including database lookups, API calls, and MCP tool calls. The record includes tool identity, input, output, and tool version hash. | High |

### 5.2 Criticality conditions

Delegation occurred when one agent assigned a sub-task to another agent. More than one sub-agent means more than one agent received such a sub-task.

Those conditions select the criticality in §5.1. They do not select a state code. The state if absent remains open item OI-5.

PA-EC-24's criticality is High. The SRS cell does not limit that label to a case in which a tool was invoked. This section does not add that limit.

Criticality still does not change C-CMP-1, C-CMP-2, or the four assessment verdicts. That is rule 4.

### 5.3 Limits

PA-EC-22 records the sub-agent's confidence and reasoning. Recording that text does not establish that the reasoning was adequate. That limit is NG-1. Model reasoning is TM-NG-6.

PA-EC-24 records the tool invocation, including the tool version hash named in the SRS. Tool versions, configurations, and MCP tool hashes, when an MCP tool was used, are security baseline SEC-PROV-3. This class does not add a second hash rule, and it does not set the encoding. SEC-PROV-3 stays Implementation-dependent.

The five classes do not appear in §4. SRS §9.4 does not place them in the sequence. This section does not assign them a position. That absence is open item OI-6.

M2 test coverage does not require these classes. A package that places one of them on its expected-evidence-class list is assessed under the completeness draft. The missing state if absent does not add an eighth state and does not change the four verdicts.

---

## 6. Emergency and exception paths

Normative. This is SRS §9.6. These paths do not change §4. They do not change the seven state codes, the four assessment verdicts, C-CMP-1, or C-CMP-2.

### 6.1 Urgent PA

Urgent PA is a decision required within 72 hours or less. That bound names the scenario. It is not a duration for the ordinary path. §4.2 still states no maximum gap, and that gap remains open item OI-3. This section does not measure the 72-hour bound and does not state how the bound is evidenced.

All evidence classes apply. That means the classes this profile expects for the case under §3 and, when their conditions hold, under §5. This path does not drop a class and does not add one.

Temporal ordering constraints are relaxed. The SRS does not name which pairs in §4.2 stop being flagged. This section does not drop a pair. That unspecified relaxation is open item OI-9.

Late-arriving PA-EC-02 and PA-EC-03 are accepted with state `arrived_late`. That code is the completeness draft §3.3.6. This path does not assign `arrived_late` to any other class. `arrived_late` remains `INCOMPLETE` for the sealed scope under C-CMP-2. This section does not change that result.

### 6.2 Emergency exception

An emergency exception is an immediate clinical need. The PA determination is concurrent with treatment or after treatment.

The package carries a mandatory `emergency_exception` flag. The seven declaration elements do not include that flag. The eight report fields do not include it. This section does not add a field to either list and does not change a verdict. Where the flag is carried is open item OI-7.

PA-EC-04 through PA-EC-08 may be initially `expected_not_captured`. The SRS names a mandatory post-hoc completion deadline and states no length. This section states no duration. That missing length is open item OI-8.

The permission covers those five classes. It does not extend to any other class. `expected_not_captured` remains `INCOMPLETE` under C-CMP-2. A later capture does not, by this section, change the result for the sealed scope. The amendment procedure remains completeness open item OI-5.

### 6.3 Retrospective review

Retrospective review is a prior authorization requested after treatment delivery.

All evidence classes apply, in the same sense as §6.1.

Temporal ordering constraints reflect the retrospective sequence. The SRS does not draw that sequence. §4 is the ordinary path. This section does not assign a pair. That missing sequence is open item OI-10.

The scope declaration notes the retrospective nature. The note is part of declared collection scope, one of the seven elements (completeness draft §2.2.2). The note states that the request followed treatment delivery. This section does not add an eighth element.

The completeness check list in §2.3 does not name that note. This section does not add a check to that list. That gap is open item OI-11.

---

## 7. Versioning

Normative. This is SRS §9.7. The identifier, the name, and version 0 are §1.

Profiles are versioned. This profile's version is the value in §1.

A package produced under profile version N is verifiable under profile version N. A package whose profile reference is `adep.profile.pa.basic.v0` is verified under version 0, which is this document. This section does not define a later version.

Forward compatibility, verifying a version-0 package under a later version's rules, should be supported where possible. The SRS does not say when that is possible. This section does not list those cases. That gap is open item OI-12.

The profile version is recorded in the scope declaration. It is part of the workflow profile reference, one of the seven elements (completeness requirements v0.2 §2.2.1). The identifier `adep.profile.pa.basic.v0` includes version 0. This section does not add an eighth element.

---

## 8. Open items

| ID | Issue | Deferred to |
|----|-------|-------------|
| OI-1 | The SRS state-if-absent cell names one condition for PA-EC-08, PA-EC-12, PA-EC-13, PA-EC-14, and PA-EC-15. §3.2 also names the complementary condition, using `excluded` or `expected_not_captured` as that section states. Those complements are this draft's reading. | Review of §3.2 against SRS §9.3 |
| OI-2 | SRS §9.4 does not place PA-EC-12 or PA-EC-15 in the sequence. §4 does not assign them a position. | Review of §4.1 |
| OI-3 | SRS §9.4 says clinical documentation may arrive concurrently or shortly after the request. §4.2 allows the same time or a later time and states no maximum gap. | Review of §4.2 |
| OI-4 | An ordering violation is flagged for the completeness assessment. The completeness report's eight fields do not include that flag. §4.3 does not add a field, a state, or a verdict. | Review of §4.3 against completeness draft §4.2 |
| OI-5 | SRS §9.5 gives PA-EC-20 through PA-EC-24 no state if absent. §5.1 does not invent a code. Criticality conditions in §5.2 do not select one. | Review of §5.1 against SRS §9.5 |
| OI-6 | SRS §9.4 does not place PA-EC-20 through PA-EC-24 in the sequence. §4 and §5 do not assign them a position. | Review of §4.1 |
| OI-7 | The `emergency_exception` flag is mandatory. The seven declaration elements and the eight report fields do not include it. §6.2 does not add a field, a state, or a verdict. | Review of §6.2 against completeness draft §2.2 and §4.2 |
| OI-8 | SRS §9.6 requires a post-hoc completion deadline for an emergency exception and states no length. §6.2 states no duration. | Review of §6.2 |
| OI-9 | SRS §9.6 says the temporal ordering constraints of urgent PA are relaxed and does not name which pairs in §4.2 stop being flagged. §6.1 does not drop a pair. `arrived_late` is named only for PA-EC-02 and PA-EC-03. | Review of §6.1 against §4.2 |
| OI-10 | SRS §9.6 says retrospective ordering reflects the retrospective sequence and does not draw that sequence. §6.3 does not assign a pair. §4 is not that sequence. | Review of §6.3 |
| OI-11 | The retrospective note is required in declared collection scope. Completeness draft §2.3 does not check for it. §6.3 does not add an element or a check. | Review of §6.3 against completeness draft §2.3 |
| OI-12 | SRS §9.7 says forward compatibility should be supported where possible and does not say when that is possible. §7 does not list those cases. | Review of §7 |

---

## 9. References

- ADEP-PHASE0-SRS-v0.1 §9.2, §9.3, §9.4, §9.5, §9.6, §9.7, §9.8, and §10.1.3 (agentic classes and full coverage-indicator reconciliation are outside M2 test coverage)
- Completeness requirements v0.2 §2.2.1 (profile reference, including version), §2.2.2 (declared collection scope), §2.2.3 (expected-class list), §2.3 (declaration checks), §3.3.6 (`arrived_late`), §3 (state codes), §4 (assessment), §5 (coverage indicators), §6 (claim levels), and open items OI-2, OI-5, and OI-7
- Assurance contract v0.2 §5.1 (NG-1), §5.2 (NG-2), §6.6 (C-CMP-1, C-CMP-2), §6.7 (C-TMP-1), and §8 (TM-NG-6)
- Security baseline v0.1 SEC-PROV-3 (tool versions and MCP tool hashes)
- `schemas/expected-evidence-classes.schema.json` (JSON Schema draft 2020-12)

---

*End of assembled draft through W3-T05 — ADEP-WI5-PA-v0*
