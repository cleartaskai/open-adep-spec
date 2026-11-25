# Open ADEP Evidence Scope and Completeness Requirements v0.2

**Document Identifier:** ADEP-WI2-CMP-v0.2  
**Status:** DRAFT — first draft final (W3-T02)  
**Date:** 2026-10-25  
**Parent SRS:** ADEP-PHASE0-SRS-v0.1 §6.2, §6.3, §6.4, §6.5, §6.6, §6.7, §6.8, §6.9  
**Author:** LEAD (AI draft for review)  
**Reviewer:** Pending (a reviewer who did not draft this section)

This is the first draft final of the completeness requirements. It contains the scope declaration, the seven evidence-element states, the completeness assessment, the coverage indicators, the claim hierarchy, the relationship to integrity, the motivating scenario, and the three JSON Schema fragments in `schemas/`. Open items OI-1 through OI-10 stay open. The scenario keeps its stand-in class labels.

**Inputs:** SRS §6.2, §6.3, §6.4, §6.5, §6.6, §6.7, §6.8, and §6.9; SRS §9.7 for the profile version recorded in the declaration; SRS §10.1.3 for the M2 exclusion of full coverage-indicator reconciliation; assurance contract v0.2 draft §5.2 (NG-2), §6.2 (C-INT-1, C-INT-2), and §6.6 (C-CMP-1, C-CMP-2); PA profile draft §3, §4, §5, and §6.

---

## Revision history

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 0.2-draft.1 | 2026-10-23 | LEAD | W2-T03. Seven scope-declaration elements, each with the SRS requirement level. |
| 0.2-draft.2 | 2026-10-23 | LEAD | W2-T04. Seven evidence-element states, each with a code, a definition, and a verification implication. |
| 0.2-draft.3 | 2026-10-24 | LEAD | W2-T07. Completeness assessment. Eight report fields and four verdicts. |
| 0.2-draft.4 | 2026-10-24 | LEAD | W2-T08. Motivating scenario. A signed package whose completeness verdict fails. |
| 0.2-draft.5 | 2026-10-24 | LEAD + ARCH | W2-T14. Coverage indicators. Definition, example, CI-1 through CI-6, and the limitations. |
| 0.2-draft.6 | 2026-10-24 | LEAD | W2-T15. Four completeness claim levels, and the integrity-by-completeness matrix. |
| 0.2-draft.7 | 2026-10-24 | LEAD | W2-T20 cross-reference. The basic prior-authorization class catalog points at the PA profile draft §3. |
| 0.2-draft.8 | 2026-10-24 | LEAD | W2-T21 cross-reference. Ordering flags point at the PA profile draft §4. The eight report fields are unchanged. |
| 0.2-draft.9 | 2026-10-24 | LEAD | W2-T22 cross-reference. The redacted commitment points at security baseline PRV-MIN-1. The mechanism list stays open. |
| 0.2-draft.10 | 2026-10-24 | LEAD | W2-T23 cross-reference. The redaction list and the redacted commitment point at security baseline PRV-DSC-1 through PRV-DSC-4. The mechanism list stays open. |
| 0.2-draft.11 | 2026-10-24 | LEAD | W2-T25 cross-reference. Verification without clinical content points at security baseline PRV-BND-3. The mechanism list stays open. |
| 0.2-draft.12 | 2026-10-24 | LEAD | W2-T26. First assembly. Section map, and cross-references aligned to the sections in this file. Open items OI-1 through OI-10 stay open. |
| 0.2-draft.13 | 2026-10-24 | LEAD | W2-T30 cross-reference. Agentic classes point at the PA profile draft §5. They are outside M2 test coverage. |
| 0.2-draft.14 | 2026-10-24 | LEAD | W2-T31 cross-reference. Exception paths point at the PA profile draft §6. The seven declaration elements and the eight report fields stay as written. |
| 0.2-draft.15 | 2026-10-25 | LEAD | W3-T01. Three JSON Schema fragments, draft 2020-12. No state, declaration element, or report field was added. |
| 0.2-draft.16 | 2026-10-25 | LEAD | W3-T02. Final read. The fragments are cited. The profile vocabulary in §2.3 points at the PA profile draft. Open items OI-1 through OI-10 stay open. |
| 0.2-draft.17 | 2026-10-25 | LEAD | W3-T04 cross-reference. Profile versioning points at the PA profile draft §7. The seven declaration elements stay as written. |
| 0.2-draft.18 | 2026-10-25 | LEAD | W3-T05 cross-reference. The class-list schema is the PA profile fragment. The declaration schema still accepts any profile's identifiers. |

---

## 1. Purpose

This document states the completeness requirements for an evidence package. It is normative except where a section says it is informative. The coverage-indicator example in §5.2 and the motivating scenario in §8 are informative.

| Section | What it contains |
|---------|------------------|
| §2 | Scope declaration. Seven elements. |
| §3 | Seven evidence-element states. |
| §4 | Completeness assessment. Eight report fields and four verdicts. |
| §5 | Coverage indicators, CI-1 through CI-6. |
| §6 | Four completeness claim levels. |
| §7 | Relationship to integrity. The four SRS rows and the two-by-four matrix. |
| §8 | Motivating scenario. The class labels are stand-ins. |
| §9 | Open items OI-1 through OI-10. |
| §10 | References. |

The three JSON Schema fragments in `schemas/` are normative annexes. They are not an eleventh section. The dialect is JSON Schema draft 2020-12.

§2 defines the scope declaration that every evidence package carries. The declaration states what the producer intended to collect. It is not an evidence-element state, a completeness verdict, a coverage indicator, or a claim level.

A verifier uses the declaration as the scope input to P-5. The assurance contract already states that C-CMP-1 is `NOT_EVALUATED` when the workflow profile or the scope declaration is absent. §4.3 names the assessment verdict for an insufficient declaration. The P-5 token for a declaration that is present and not complete remains open item OI-1.

---

## 2. Scope declaration

### 2.1 Rules

1. Every evidence package contains one scope declaration.
2. The declaration has the seven elements in §2.2. The count treats collection start time and collection end time as separate elements.
3. The requirement levels are the three levels in the SRS §6.3 table: `REQUIRED`, `REQUIRED if case is closed`, and `REQUIRED if limitations exist`.
4. A declaration that omits an element this section requires for that package is not a complete scope declaration.
5. The declaration does not assign an evidence state to a class. The seven state codes are §3.
6. The declaration does not produce a completeness verdict. The four verdicts are §4.3.
7. This section does not say which signature covers the declaration.

### 2.2 Elements

| Element | What it states | Requirement level |
|---------|----------------|-------------------|
| Workflow profile reference | Which workflow profile defines the class vocabulary for this package, including that profile's version. | REQUIRED |
| Declared collection scope | The subject and the activity boundaries this package intends to cover. | REQUIRED |
| Expected evidence classes | The evidence classes this package instance expects. | REQUIRED |
| Collection start time | When the producer declares that collection began. | REQUIRED |
| Collection end time | When the producer declares that collection ended, or that it is still open. | REQUIRED if case is closed |
| Scope limitations | Known limits on what collection could observe. | REQUIRED if limitations exist |
| Scope version | The version of this declaration. | REQUIRED |

The JSON names of these seven elements are the property names in `schemas/scope-declaration.schema.json`. A property name is not an eighth element.

#### 2.2.1 Workflow profile reference

The value is the profile identifier. The identifier includes the profile version. SRS §9.7 requires that version to be recorded in the scope declaration, and this element is where it is recorded. The rules are the PA profile draft §7. An example identifier is `adep.profile.pa.basic.v0`. The element does not define the profile. The seven elements stay as written.

The element is `REQUIRED`. A declaration without a profile identifier is not complete.

#### 2.2.2 Declared collection scope

The value states the subject of collection and the activity boundaries the package intends to cover. Collection start time and collection end time are separate elements. A prose boundary such as "from initiation through final determination" does not replace those time elements.

An informative example from SRS §6.3 is "all events related to PA case #12345 from initiation through final determination."

When the workflow profile that §2.2.1 names requires the declaration to note a particular character of the case, that note is part of this element's value. SRS §9.6 requires a retrospective prior-authorization profile to note that character. The note's wording is the PA profile draft §6.3. The seven elements stay as written.

The element is `REQUIRED`. A declaration without a subject and an activity boundary is not complete.

#### 2.2.3 Expected evidence classes

The value is a list of class identifiers. Each identifier is a class the referenced profile defines. The list is the set this package instance expects. It is the instance list, not a second copy of the profile's whole catalog required by this section. For `adep.profile.pa.basic.v0`, the allowed identifiers are the PA profile schema `expected-evidence-classes.schema.json`. The declaration schema in this document still accepts any non-empty string, because this section is not limited to one profile.

This section does not decide what follows when the list omits a class the profile requires for the case. That representation is open item OI-2. An empty list is a stated list. Whether C-CMP-1 is then `COMPLETE` is open item OI-3.

The element is `REQUIRED`. A declaration without the list is not complete. The list may be empty and still be present.

#### 2.2.4 Collection start time

The value is the producer's declared time at which collection began. It is a boundary of the declaration. It is not, by itself, a P-6 anchor, and a verifier does not treat it as evidence-event time.

The element is `REQUIRED`. A declaration without a start time is not complete.

The schema requires a non-empty string. It does not name a calendar format. That encoding is `schemas/scope-declaration.schema.json`.

#### 2.2.5 Collection end time

The requirement level is `REQUIRED if case is closed`.

This draft reads that level as follows. The element is present on every declaration. Its value is a timestamp when the case is closed, and the marker `open` when the case is ongoing. A timestamp meets the level for a closed case. The marker `open` is how an ongoing case records the end that SRS §6.3 says "may be open." Omitting the element does not meet it, because the verifier would otherwise be unable to tell an ongoing case from a closed case whose end time was left out.

A closed case with the marker `open`, and an ongoing case with a timestamp, are not complete declarations.

SRS §6.3's table also allows a reading in which an ongoing case omits the element. This draft does not use that reading. The choice is open item OI-4.

The end time is a declared boundary. It is not, by itself, a P-6 anchor.

#### 2.2.6 Scope limitations

The value is a list of known limits on collection. An informative example from SRS §6.3 is "clinical records from external provider systems are not instrumented."

The requirement level is `REQUIRED if limitations exist`. When the producer knows of no such limit, the element may be omitted or may be an empty list. Both meet the level. Meeting the level does not establish that collection had no limit the producer left unstated. That limit is the kind of gap NG-2 names.

The element does not assign the state `excluded`. A class outside the intended collection is an evidence state (§3.3). A limitation is a statement about what collection could observe.

#### 2.2.7 Scope version

The value is the version identifier of this declaration. The first declaration a package carries has a version. An amendment of the declaration carries a new version identifier. The identifier supports that distinction, which is the reason SRS §6.3 gives for the element.

This section does not define an ordering scheme for versions and does not define the amendment procedure. Both are open item OI-5. Equality of the identifier is the comparison this section requires.

The element is `REQUIRED`. A declaration without a version identifier is not complete.

### 2.3 What the verifier checks

For a package under assessment, the verifier checks:

1. The declaration is present.
2. Each `REQUIRED` element in §2.2 is present.
3. Collection end time is a timestamp when the case is closed, and `open` when the case is ongoing, under the reading in §2.2.5.
4. Scope limitations are present when the declaration states a limitation. Omission or an empty list meets the level when no limitation is stated.
5. Every class identifier in the expected-evidence-class list is defined by the referenced profile. For `adep.profile.pa.basic.v0`, that vocabulary is the PA profile draft §3 and §5. An identifier that profile does not define fails this check.

A declaration that fails one of these checks is not complete. The assessment verdict for that package is `indeterminate` (§4.3). The P-5 token is open item OI-1.

---

## 3. Evidence element states

Normative. This is SRS §6.4. Every evidence element the scope declaration references has exactly one of these states.

### 3.1 Rules

1. The codes are `present`, `redacted`, `excluded`, `expected_not_captured`, `unavailable`, `arrived_late`, and `disposed`. The state fragment enumerates those seven codes and no others.
2. An element has one code. A second code on the same element is not a state this section defines.
3. This catalog has no code `missing`. In SRS §6.4 the redacted row says the state is distinct from "missing," and the excluded row says missing means content was expected but not captured. That situation is `expected_not_captured`. Assurance-contract open item OI-8 records the same word in MC-6 and MC-8.
4. The producer assigns the code. The verifier applies the implication in §3.3. The verifier does not add an eighth code.
5. The P-5 result tokens remain those in the assurance contract. This section states what each code means for that check. It does not rewrite C-CMP-1 or C-CMP-2.
6. The state code and the P-1 result are separate. A P-1 failure does not replace the code. When an evaluated P-1 claim is `FAIL`, §7 treats the completeness assessment as unreliable.

### 3.2 Catalog

| State | Code | Definition | Verification implication |
|-------|------|------------|--------------------------|
| Present | `present` | The element is included in the package and integrity-protected. | The verifier applies the ordinary integrity checks to the included bytes. |
| Redacted | `redacted` | The element exists. Its content is replaced by a privacy-preserving commitment. Existence and metadata are visible. Content is not. | The verifier can confirm existence and the commitment. The verifier cannot verify the content. |
| Intentionally excluded | `excluded` | The element is outside the declared collection scope. The producer has stated that this class was not intended to be collected. | The verifier records the exclusion. |
| Expected but not captured | `expected_not_captured` | The element was inside the declared scope and expected, and it was not captured. | The verifier flags a completeness gap. The package cannot claim completeness for this class. |
| Unavailable | `unavailable` | The element was expected, capture was attempted, and the source was unavailable. | The verifier flags a completeness gap with a different cause from `expected_not_captured`. |
| Arrived late | `arrived_late` | The element was captured after the package was initially sealed, or after the expected temporal window. | The verifier flags the temporal discrepancy. |
| Disposed | `disposed` | The element existed and was removed under a documented retention or disposal policy. | The verifier can confirm that disposal was declared and that the disposal record is integrity-protected. The verifier cannot verify the original content. |

### 3.3 Implications

#### 3.3.1 `present`

The element is in the package, and the producer assigns it as integrity-protected. The ordinary checks are the P-1 checks on those bytes. A `present` element counts toward C-CMP-1 `COMPLETE`. The state does not establish that the content is true (NG-1).

#### 3.3.2 `redacted`

The element's existence and metadata remain visible. The content is a privacy-preserving commitment: a hash, a zero-knowledge proof, or another mechanism the privacy baseline defines. PRV-MIN-1 requires that metadata and clinical content can be separated, and it names this commitment as one separation. PRV-DSC-3 requires the verifier to check that commitment. PRV-BND-3 states what that verifier can check when the clinical content is withheld. None of these requirements closes the list of qualifying mechanisms.

The verifier confirms the existence and the commitment. The verifier has no content bytes to check. A `redacted` element counts toward C-CMP-1 `COMPLETE`. C-CMP-2 requires that a `redacted` element not be reported as `expected_not_captured`.

The state is distinct from `expected_not_captured`. The SRS wording "distinct from missing" is that distinction, under the reading in §3.1.

#### 3.3.3 `excluded`

The producer states that this class was outside the intended collection. The verifier records that statement. The state is not `redacted`: nothing is hidden inside the package. The state is not `expected_not_captured`: the class was not expected.

C-CMP-2 says this state, by itself, does not make the P-5 result `INCOMPLETE`. C-CMP-1 says `COMPLETE` only when every expected class is `present` or `redacted`. A class that is both on the expected-evidence-class list and `excluded` falls under both sentences. This section does not pick which sentence wins. That is open item OI-7. Which representation an omitted profile class uses remains open item OI-2.

#### 3.3.4 `expected_not_captured`

The class was inside the declared scope and was expected, and capture did not happen. The verifier flags a completeness gap. The package cannot claim completeness for this class. C-CMP-2 makes the P-5 result `INCOMPLETE`.

This is the situation SRS §6.4 describes as content expected but not captured. v0.1 called a related state `MISSING`. This catalog does not use that code.

#### 3.3.5 `unavailable`

The class was expected, the system attempted capture, and the source was unavailable. An informative example from SRS §6.4 is an external-system timeout or an API error. The verifier flags a completeness gap. The cause is the unavailable source. `expected_not_captured` records that the element was not captured, without this source failure. C-CMP-2 makes the P-5 result `INCOMPLETE`.

The reason for unavailability should be recorded with the element. A missing reason does not change the code. The state remains `unavailable`, and the gap still flags.

#### 3.3.6 `arrived_late`

The element was captured after the initial seal, or after the expected temporal window. Either condition is enough. The verifier flags that discrepancy. C-CMP-2 makes the P-5 result `INCOMPLETE` for the sealed scope.

SRS §6.4 says the element may be included in a package amendment. A later scope version can name it. The amendment procedure is open item OI-5. Inclusion in a later version does not change the result for the sealed scope.

#### 3.3.7 `disposed`

The element existed and was removed under a documented retention or disposal policy. The verifier confirms that the disposal was declared and that the disposal record is integrity-protected. The verifier cannot verify the original content. The report field that lists disposals is §4.2.

C-CMP-1 does not treat `disposed` as `present` or `redacted`, so the class does not count toward `COMPLETE`. C-CMP-2 does not list `disposed` among the states that make the result `INCOMPLETE`. This section does not close that difference. It is open item OI-7.

### 3.4 How the codes meet the two P-5 claims

| Code | Toward C-CMP-1 `COMPLETE` | C-CMP-2 |
|------|---------------------------|---------|
| `present` | Yes | The element is not a gap. |
| `redacted` | Yes | Reporting it as `expected_not_captured` fails the claim. |
| `excluded` | Only if the class is not an expected class. See OI-7. | The state alone does not make the result `INCOMPLETE`. |
| `expected_not_captured` | No | `INCOMPLETE`. |
| `unavailable` | No | `INCOMPLETE`. The cause differs from `expected_not_captured`. |
| `arrived_late` | No | `INCOMPLETE` for the sealed scope. |
| `disposed` | No | Not listed as a gap. See OI-7. |

---

## 4. Completeness assessment

Normative. This is SRS §6.5. An assessment compares three inputs and produces one completeness report.

### 4.1 Inputs and rules

The three inputs are:

1. The workflow profile's expected evidence classes: what that profile says should be present. For `adep.profile.pa.basic.v0`, the core catalog is the PA profile draft §3. The agentic classes are the PA profile draft §5. They are defined and not required in M2 test coverage. Ordering for the core classes is the PA profile draft §4. The agentic classes have no sequence slot in that section. Urgent PA, the emergency exception, and retrospective review are the PA profile draft §6. Profile versioning is the PA profile draft §7. The class-list schema is the PA profile file `schemas/expected-evidence-classes.schema.json`. The instance list in the scope declaration is §2.2.3.
2. The scope declaration's collection boundaries: what the producer intended to collect. Those boundaries are §2.
3. The evidence-element states actually reported. The codes are the seven in §3. SRS §6.5 describes this input as what is present, missing, redacted, excluded, and so on. The word missing in that sentence is not a state code.

Rules:

1. One assessment produces one completeness report.
2. The report has the eight fields in §4.2.
3. The completeness verdict is one of the four values in §4.3, except the case §4.3 leaves unassigned.
4. The report does not change a P-1 result.
5. The verdict tokens and the P-5 tokens are different vocabularies. §4.4 says how they line up. This section does not rewrite C-CMP-1 or C-CMP-2.
6. The claim-hierarchy names are §6. This section uses the four verdict tokens from SRS §6.5. A verdict token is not a claim level.
7. Coverage indicators are §5. A reconciliation under that section does not change the verdict in §4.3.
8. A workflow profile may require the assessment to flag an ordering violation. The eight fields in §4.2 do not include that flag. The basic prior-authorization rules are the PA profile draft §4. The flag does not change a verdict. The `emergency_exception` flag in the PA profile draft §6.2 is also not one of those eight fields. It does not change a verdict.

### 4.2 Report fields

| Field | What it contains |
|-------|------------------|
| Profile reference | The workflow profile the assessment used as its basis. |
| Scope coverage | The percentage and the list of expected classes whose state is `present`. |
| Gap list | Every class in `expected_not_captured`, `unavailable`, or `arrived_late`, with a reason where one is recorded. |
| Exclusion list | Every class in `excluded`, with the producer's stated reason. |
| Redaction list | Every class in `redacted`, with the disclosure profile reference. |
| Disposal list | Every class in `disposed`, with the disposal policy reference. |
| Completeness verdict | One value from §4.3. |
| Assessment limitations | What this assessment cannot detect. |

The JSON names of these eight fields are the property names in `schemas/completeness-report.schema.json`. A property name is not a ninth field.

#### Profile reference

The value is the profile identifier from the scope declaration, including the profile version. An assessment whose profile reference differs from that identifier is not an assessment of that declaration. Its verdict is `indeterminate`.

#### Scope coverage

The list is the expected classes whose state is `present`. When the expected-class list has at least one class, the percentage is the count of those `present` classes divided by the count of expected classes. A `redacted` class is not in that percentage. It is on the redaction list. A verdict of `complete` can therefore sit beside a percentage below 100.

When the expected-class list is empty, this percentage is not defined. That case is open item OI-3.

#### Gap list

The list holds every class in `expected_not_captured`, `unavailable`, or `arrived_late`. A reason is included when one is recorded. A class stays on the list when no reason is recorded. `excluded` and `disposed` are not gap-list entries.

#### Exclusion list

The list holds every class in `excluded`. Each entry carries the producer's statement that the class was not intended to be collected. An entry without that statement does not meet §3.3.3.

#### Redaction list

The list holds every class in `redacted`. Each entry carries the disclosure profile reference when a disclosure profile is in scope. When no profile is declared, the entry says so. The privacy boundary for that case is the assurance contract §8. The requirements for a disclosure profile are security baseline PRV-DSC-1 through PRV-DSC-4.

#### Disposal list

The list holds every class in `disposed`. Each entry carries the disposal policy reference. An entry without that reference does not meet §3.3.7, which requires a documented retention or disposal policy.

#### Assessment limitations

The field states what the assessment cannot detect. It includes NG-2: activity that was never routed to a capture point. It cites any scope limitations the declaration states. When the assessment relies on coverage indicators, it also includes the limit in §5.4. The indicator rules are §5. This field does not define them.

### 4.3 Verdicts

| Verdict | When it applies |
|---------|-----------------|
| `complete` | Every class on the expected-evidence-class list is `present` or `redacted`. |
| `incomplete_documented` | At least one expected class is on the gap list, and every expected class is `present`, `redacted`, or on the gap list. |
| `incomplete_undocumented` | At least one expected class is not `present`, not `redacted`, and not on the gap list, the exclusion list, or the disposal list. |
| `indeterminate` | The scope declaration is not complete under §2, the profile reference does not match the declaration, or the states needed for the comparison cannot be read. |

`complete` is the SRS §6.5 sentence: all expected classes are present or redacted. That is the same condition C-CMP-1 uses for `COMPLETE`.

`incomplete_documented` is the SRS sentence: gaps exist and are documented. Documentation here is the gap-list entry and its state. A missing reason does not move the class to `incomplete_undocumented`.

`incomplete_undocumented` is the SRS sentence: evidence classes are neither present nor accounted for. A class with no state and no list entry is that case when the class is on the expected list.

`indeterminate` is the SRS sentence: the scope declaration is insufficient to assess. An absent declaration and a declaration that fails §2.3 are both insufficient. C-CMP-1 remains `NOT_EVALUATED` when the declaration or the profile is absent. The P-5 token for a declaration that is present and not complete is open item OI-1.

An expected class in `excluded` or `disposed` is on the exclusion list or the disposal list, so it is accounted for, and it is not `present` or `redacted`, so `complete` does not apply. It is not a gap-list entry, so `incomplete_documented` does not apply either. None of the four verdicts names that package. The report still fills the lists. The verdict for that package is open item OI-7. This section does not add a fifth verdict. The report schema allows the verdict property to be absent for that case. Absence is not a fifth token.

The letter of `complete` is met by an empty expected-class list, because there is no expected class outside `present` and `redacted`. Whether that verdict is permitted remains open item OI-3. A class the profile requires and the expected list omits is open item OI-2. This section does not place that class on a list.

### 4.4 How the verdicts meet the P-5 claims

| Verdict | P-5 |
|---------|-----|
| `complete` | C-CMP-1 `COMPLETE`, aside from the empty-list case in OI-3. |
| `incomplete_documented` | C-CMP-1 `INCOMPLETE`. C-CMP-2 `INCOMPLETE` when the gap is `expected_not_captured`, `unavailable`, or `arrived_late`. |
| `incomplete_undocumented` | C-CMP-1 `INCOMPLETE`. |
| `indeterminate`, declaration or profile absent | C-CMP-1 `NOT_EVALUATED`. |
| `indeterminate`, declaration present and not complete | P-5 token not chosen. OI-1. |
| No verdict, expected class `excluded` or `disposed` | OI-7. The claims are unchanged. |

---

## 5. Coverage indicators

This section is SRS §6.6. The definition and CI-1 through CI-6 are normative. The example is informative. The statement of what reconciliation cannot detect is informative. The requirement to put that statement in a report that relies on indicators is normative.

Coverage indicators are external reconciliation signals. They can turn some omissions that the package itself does not show into differences a verifier can report. They do not close NG-2. An activity that no capture point and no emitting system recorded can remain undetected. Assurance contract v0.2 §5.2 keeps that non-goal.

### 5.1 Definition

A coverage indicator is a signed counter, a heartbeat, or a summary statistic. A capture point or an upstream system emits it. A verifier can reconcile it against the contents of an evidence package.

The word signed in that definition is CI-1. This section does not add an evidence state. The seven codes remain §3. This section does not add a signature type. The five types remain trust model v0.2 §5.

### 5.2 Example

Informative. This is the example in SRS §6.6.2.

> The utilization management system processes prior-authorization requests and emits a signed daily counter: "1,412 PA requests processed on 2026-10-17." DecisionTrace created 1,410 evidence chains for that date. The discrepancy of 2 is flagged for investigation.

The system name, the product name, the date, and the two counts are that illustration. §5.3 does not adopt them as required values. In the requirements, an emitting system produces the indicator, and the reconciliation compares it with an evidence package.

### 5.3 Requirements

| Requirement | Statement |
|-------------|-----------|
| CI-1 | A coverage indicator is integrity-protected. The emitting system signs it. |
| CI-2 | A coverage indicator includes a time period, a count or a summary, and the identity of the emitting system. |
| CI-3 | The evidence package may include coverage indicators as evidence elements with state `present`. |
| CI-4 | The completeness assessment may reconcile coverage indicators against the package contents and report discrepancies. |
| CI-5 | Coverage indicators do not guarantee detection of every omission. Their absence does not invalidate a package. They are a defense-in-depth mechanism. |
| CI-6 | The reconciliation method and the tolerance thresholds are documented in the workflow profile. |

#### CI-1 Integrity protection

The emitting system signs the indicator. A verifier checks that signature against the identity CI-2 requires.

When the package includes the indicator as a `present` evidence element, the ordinary P-1 and P-2 checks apply to those bytes. CI-1 does not name which trust-model role holds the emitting system's key.

#### CI-2 Contents

Each indicator carries a time period, a count or a summary, and the identity of the emitting system. A heartbeat may carry a summary where a counter would carry a count. An indicator that omits any of the three does not meet CI-2.

The time period is stated so the comparison can name which package contents fall inside it. The profile's method, under CI-6, says how that comparison is made.

#### CI-3 Inclusion

The package may include coverage indicators. Each included indicator is an evidence element in state `present`. The package may omit them. What omission means for the package is CI-5.

This section does not assign a class identifier. A workflow profile may define a class for these indicators. The prior-authorization class list, including the state used when indicators are not configured, is WI-5.

#### CI-4 Reconciliation

The assessment may reconcile indicators against the package contents. When it does, it reports each discrepancy.

A discrepancy is a difference, outside the tolerance the workflow profile documents, between an indicator and the package contents it is reconciled against. The difference is not an evidence state. It is not an entry on the gap list, the exclusion list, the redaction list, or the disposal list. It does not change the verdict in §4.3.

The statement that carries the reconciliation sits with the report. It names the indicators used, the package contents they were compared with, the profile method and tolerance applied, and each discrepancy. It is not one of the eight fields in §4.2. That placement is open item OI-8.

The reconciliation uses the method and the tolerance thresholds the profile documents. This section does not supply those values. A comparison that cannot cite them is not a CI-4 reconciliation.

Full coverage-indicator reconciliation is outside the M2 conformance target (SRS §10.1.3). CI-4 stays optional here. This section does not add a claim and does not move a milestone.

SRS §6.7 uses the phrase "no unexplained discrepancies" for Coverage-reconciled. §6 states what this draft means by that phrase. This section reports the difference.

#### CI-5 What an indicator does not guarantee

Indicators do not guarantee that every omission is detected. They are a defense-in-depth mechanism.

Their absence does not invalidate a package. The other property checks still apply, and an assessment under §4 can still be made. CI-5 does not treat an expected class as meeting C-CMP-1 when that class is neither `present` nor `redacted`. C-CMP-1 and C-CMP-2 are unchanged.

#### CI-6 Workflow profile

The reconciliation method and the tolerance thresholds are documented in the workflow profile. This draft does not set them for `adep.profile.pa.basic.v0` or for any other profile. The PA profile draft §3 names PA-EC-15 and does not set the method or the thresholds.

### 5.4 Limitations

Indicators can turn some unobservable omissions into detectable discrepancies. They cannot detect an omission in the indicators themselves. When the emitting system also failed to record the event, reconciliation against that indicator cannot detect the omission.

NG-2 remains in force. A coverage indicator does not establish that every activity was routed to a capture point.

Every completeness report that relies on coverage indicators states this limit. The assessment-limitations field in §4.2 carries that statement. A report that does not use indicators does not rely on them. The motivating scenario in §8 is that case. Its limitations field states NG-2 and says that coverage indicators are not used.

### 5.5 What this section leaves in place

The four claim levels are §6. The relationship between an integrity result and a completeness result is §7. This section does not rewrite C-CMP-1 or C-CMP-2, and it does not add an eighth evidence state.

---

## 6. Completeness claim hierarchy

Normative. This is SRS §6.7. A claim level qualifies what an implementation says about completeness. It is not a verdict, a P-5 token, or an evidence state.

### 6.1 Rules

1. An implementation does not claim that a package is complete without qualification.
2. A completeness claim is relative to a declared scope, the workflow profile's expected evidence classes, and the stated coverage-indicator reconciliation, if a reconciliation was stated.
3. The claim uses one of the four level names in §6.2, or it uses no level. §6.3 lists the packages that receive no level. This section does not add a fifth name.
4. A level name is not a verdict token. §4.3 is unchanged. A level does not change a P-1 result or a P-5 token.
5. The verdict token `complete` remains the §4.3 value. Quoting that token is the assessment. It is not, by itself, the claim this section permits.
6. Coverage-reconciled is the only level that requires a CI-4 reconciliation. The other levels may be used when no reconciliation was performed.
7. These levels do not add a claim to the assurance contract. C-CMP-1 and C-CMP-2 stay as written. Full coverage-indicator reconciliation remains outside the M2 target (SRS §10.1.3).

A qualified claim states the level name, the profile reference including its version, and the declared collection scope. When a reconciliation was performed, the claim includes the reconciliation statement from §5.

### 6.2 Levels

| Claim level | Meaning |
|-------------|---------|
| Scope-complete | All evidence classes expected by the workflow profile for the declared scope are `present` or `redacted`. |
| Scope-complete with documented gaps | Some evidence classes are `expected_not_captured`, `unavailable`, or `arrived_late`, and every gap is documented with a reason. |
| Coverage-reconciled | Scope-complete, and coverage indicators have been reconciled with no unexplained discrepancy. |
| Indeterminate | The scope declaration or the workflow profile is insufficient to evaluate completeness. |

#### Scope-complete

Every evidence class the workflow profile expects for the declared scope is `present` or `redacted`.

The verdict `complete` uses a different list. §4.3 assigns it when every class on the declaration's expected-evidence-class list is `present` or `redacted`. The profile's expected classes and that declaration list are the same list only when the declaration names each class the profile expects for the scope. A class the profile requires and the list omits is open item OI-2. This section does not assign Scope-complete in that case. It does not decide which of OI-2's representations is right.

An empty expected-class list meets the letter of `complete`, and it meets the letter of this level when the profile expects no class for the scope. Whether that result is permitted stays open item OI-3.

#### Scope-complete with documented gaps

At least one evidence class is `expected_not_captured`, `unavailable`, or `arrived_late`. Every such gap has a recorded reason. Every other expected class is `present` or `redacted`.

The verdict `incomplete_documented` is wider. §4.3 assigns it when the gap list holds the gaps, and a missing reason does not move the class to `incomplete_undocumented`. This level requires the reason. A gap with no recorded reason keeps the verdict `incomplete_documented` and does not receive this level. It receives no other level. That package is open item OI-9.

`excluded` and `disposed` are not the three states this level names.

#### Coverage-reconciled

The package meets Scope-complete. A CI-4 reconciliation was performed. That reconciliation has no unexplained discrepancy.

A discrepancy is the difference §5.3 reports: a difference outside the tolerance the workflow profile documents. The discrepancy is unexplained unless the profile's method marks it explained. This draft does not list those marks. CI-6 places the method and the thresholds in the workflow profile. The PA profile draft §3 names PA-EC-15 and does not set the method or the thresholds. This section does not set them. A reconciliation that reports no discrepancy has no unexplained discrepancy. A reported discrepancy that the method does not mark explained means this level is not met. When the method says nothing about explanations, a reported discrepancy is unexplained.

A package at Scope-complete with documented gaps is not Coverage-reconciled. A reconciliation may still be reported for it under CI-4. The level is not assigned. When Scope-complete is withheld under OI-2, Coverage-reconciled is withheld with it.

This level is not a verdict. The verdict stays `complete` when §4.3 says so. §4.1 keeps the rule that a reconciliation does not change the verdict.

#### Indeterminate

The scope declaration or the workflow profile is insufficient to evaluate completeness.

This draft uses this level for each case in which §4.3 assigns `indeterminate`: the declaration is not complete under §2, the profile reference does not match the declaration, or the states needed for the comparison cannot be read. An absent declaration and an absent profile are both insufficient. The P-5 token for a declaration that is present and not complete stays open item OI-1.

### 6.3 Where a level lines up with a verdict

| Claim level | Verdict it can sit beside | What this section does not treat as the same thing |
|-------------|---------------------------|-----------------------------------------------------|
| Scope-complete | `complete` | The level uses the profile's expected classes for the declared scope. The verdict uses the declaration's expected list. See OI-2. |
| Scope-complete with documented gaps | `incomplete_documented`, when every gap-list entry has a recorded reason | A gap with no reason keeps the verdict and receives no level. See OI-9. |
| Coverage-reconciled | `complete`, when Scope-complete is assigned and §6.2's reconciliation condition holds | The level is not a fifth verdict. |
| Indeterminate | `indeterminate` | The P-5 token for a present, incomplete declaration stays OI-1. |
| No level | `incomplete_undocumented` | The verdict stands. None of the four names applies. |
| No level | No verdict | An expected class in `excluded` or `disposed`. See OI-7. |

`incomplete_undocumented` is a §4.3 verdict. SRS §6.8 gives it a row. It is not one of the four levels. An implementation reports the verdict. It does not call that package Scope-complete, or Scope-complete with documented gaps.

---

## 7. Relationship between completeness and integrity

Normative. This is SRS §6.8. Completeness assessment and integrity verification are independent operations. They may produce different results.

A state code does not replace a P-1 result, and a P-1 result does not replace a state code (§3.1). A verdict does not change a P-1 result (§4.1).

### 7.1 What Passed and Failed mean here

Integrity in this section is property P-1. The claims are C-INT-1 and, when it is evaluated, C-INT-2.

Integrity is Passed when at least one of those claims was evaluated and every evaluated P-1 claim is `PASS`. Integrity is Failed when any evaluated P-1 claim is `FAIL`. A claim left `NOT_EVALUATED` because the milestone does not require it does not make the result Failed.

When every P-1 claim is `NOT_EVALUATED`, Passed and Failed are both unset. SRS §6.8 has no row for that case. This draft does not treat it as Failed. That case is open item OI-10.

A P-2 result is not an integrity result for this section.

### 7.2 The four SRS rows

SRS §6.8 states four rows. The completeness words in that table are kept below. They are not the verdict tokens, and they are not the four level names. The word "unexplained" in the third row is about evidence gaps. It is not the unexplained discrepancy in §6.2.

| Integrity | SRS §6.8 completeness result | How this draft reads that result | Interpretation |
|-----------|------------------------------|----------------------------------|----------------|
| Passed | Scope-complete | Verdict `complete`. The level Scope-complete is assigned only as §6 states. | The package is integrity-verified and complete relative to the declared scope. |
| Passed | Incomplete (documented) | Verdict `incomplete_documented`. | The package is integrity-verified and has documented evidence gaps. |
| Passed | Incomplete (undocumented) | Verdict `incomplete_undocumented`. This result is not a §6 level. | The package is integrity-verified and has unexplained evidence gaps. Highest risk. |
| Failed | Any | Whatever verdict §4.3 assigns, or no verdict. | Package integrity is compromised. The completeness assessment is unreliable. |

The second row follows the verdict `incomplete_documented`. The level Scope-complete with documented gaps is narrower, because that level requires a reason on every gap. A package can sit on this row and still receive no level, which is OI-9.

The Failed row is one row. The completeness result is "Any." §7.3 expands that single row across the four claim levels. The expansion does not add a fifth SRS row.

When integrity is Failed, the report may still carry a verdict. The implementation does not present a §6 level as a claim a reader should rely on. It presents the integrity failure, and it marks the completeness assessment unreliable. The P-5 tokens in §4.4 stay as written.

### 7.3 Two-by-four matrix

The rows are the two integrity results from §7.1. The columns are the four claim levels from §6.2. SRS §6.8 does not use these four columns. It has no column for Coverage-reconciled or for Indeterminate, and it does have a completeness result, incomplete (undocumented), that is not a column here. That result stays in §7.2.

| Integrity | Scope-complete | Scope-complete with documented gaps | Coverage-reconciled | Indeterminate |
|-----------|----------------|--------------------------------------|---------------------|---------------|
| Passed | Integrity-verified, and complete relative to the declared scope, where §6 assigns the level. | Integrity-verified. The gaps are documented with reasons, as §6 requires for this level. | Integrity-verified, Scope-complete, and reconciled with no unexplained discrepancy. | The integrity result stands. Completeness cannot be evaluated. |
| Failed | The completeness assessment is unreliable. | The completeness assessment is unreliable. | The completeness assessment is unreliable. | The completeness assessment is unreliable. |

The four Failed cells are the same sentence. They are the §7.2 row "Any," written once for each level.

---

## 8. Motivating scenario

Informative. This is SRS §6.2, written against §2, §3, §4, §6, and §7. The case is synthetic. The class labels are stand-ins. The PA profile draft §3 now has its own class identifiers. This scenario does not replace the stand-ins with those identifiers.

### 8.1 Package

Package `pkg-pa-example-001` carries one scope declaration.

| Element | Value |
|---------|-------|
| Workflow profile reference | `adep.profile.pa.basic.v0` |
| Declared collection scope | Synthetic prior-authorization case PA-1001, from initiation through final determination. |
| Expected evidence classes | AI recommendation, final determination, clinical record, prior treatment history, consulted guideline. |
| Collection start time | 2026-10-17T14:00:00Z |
| Collection end time | 2026-10-17T16:30:00Z. The case is closed. |
| Scope limitations | None stated. |
| Scope version | 1 |

The five classes are the ones this declaration expects. Each reported element has one state.

| Class | State |
|-------|-------|
| AI recommendation | `present` |
| Final determination | `present` |
| Clinical record | `expected_not_captured` |
| Prior treatment history | `expected_not_captured` |
| Consulted guideline | `expected_not_captured` |

The recommendation and the determination are in the package. Each is covered by one signature. The hash chain over the included bytes checks. The clinical record, the prior treatment history, and the consulted guideline were inside the declared scope and were expected. They were not captured. No class is `redacted`, `excluded`, `unavailable`, `arrived_late`, or `disposed`.

### 8.2 Verification results

The checks in scope for this example are the M1 checks on the bytes the package contains and on the expected classes. C-INT-2, C-AUT-2, and both P-6 claims are `NOT_EVALUATED`. They are outside the point of the example.

| Check | Result |
|-------|--------|
| P-1, C-INT-1 | `PASS`. The included recommendation and determination bytes satisfy the hash check and the structural check. |
| P-2, C-AUT-1 | `PASS`. Each included payload binds to the signature presented with it. |
| P-3, C-TRS-2 | `PASS`. Each signing key is accepted under the stated trust policy. |
| P-4, C-PRV-1 | `RESOLVED` for the two `present` events. Each names a source type and a declared actor. |
| P-5, C-CMP-1 | `INCOMPLETE`. Three expected classes are not `present` or `redacted`. |
| P-5, C-CMP-2 | `INCOMPLETE`. Those three classes are `expected_not_captured`. |

### 8.3 Completeness result

| Report field | Value |
|--------------|-------|
| Profile reference | `adep.profile.pa.basic.v0` |
| Scope coverage | 2 of 5 expected classes are `present`, which is 40 percent. The list is the AI recommendation and the final determination. |
| Gap list | Clinical record, prior treatment history, and consulted guideline, each `expected_not_captured`. The recorded reason is that the class was expected at the instrumented capture point and was not captured. |
| Exclusion list | Empty. |
| Redaction list | Empty. |
| Disposal list | Empty. |
| Completeness verdict | `incomplete_documented` |
| Assessment limitations | The assessment does not detect activity that was never routed to a capture point (NG-2). No scope limitation was stated. Coverage indicators are not used. |

### 8.4 Interpretation

The package is cryptographically valid for the records it contains. The signatures bind, the included bytes pass the integrity checks, and the stated trust policy accepts the keys. Those results do not make the package complete.

C-INT-1 is `PASS`. C-INT-2 was not evaluated. For the P-1 checks that were evaluated, integrity is Passed (§7.1). The verdict is `incomplete_documented`. Each gap has a recorded reason. Taking the five stand-in classes as the classes expected for this example, the claim level is Scope-complete with documented gaps. The example does not show that the WI-5 catalog expects only those five. A profile class omitted from the list would withhold the level (OI-2). Coverage indicators were not used, so the level is not Coverage-reconciled. The §7.2 row is integrity Passed and incomplete (documented): the package is integrity-verified and has documented evidence gaps.

The scope expected the clinical record, the prior treatment history, and the guideline the model consulted. All three are on the gap list. The verdict is `incomplete_documented`, and P-5 is `INCOMPLETE`. A reader can see which expected classes were not captured, and why the completeness result failed, without treating the gap as a broken signature.

The result does not establish that the determination was clinically wrong or clinically right. That question is NG-1. It establishes that the expected inputs are not in the package, so the package is not sufficient for a reconstruction that needs those inputs.

SRS §6.2 describes those three classes as missing. This scenario uses `expected_not_captured`. It does not use a state named missing.

---

## 9. Open issues

| ID | Issue | Deferred to |
|----|-------|-------------|
| OI-1 | The verdict for an insufficient declaration is `indeterminate` (§4.3). C-CMP-1 stays `NOT_EVALUATED` when the declaration or the profile is absent. The P-5 token for a declaration that is present and not complete under §2 is not chosen. | Review of C-CMP-1 against §4.3 |
| OI-2 | A class the profile requires and the expected list omits may be a list defect, a scope limitation, or `excluded`. §4.3 does not place that class on a list. The basic prior-authorization core catalog is the PA profile draft §3. The agentic classes are §5. This issue stays open. | PA profile draft and review |
| OI-3 | An empty expected-class list meets the letter of `complete`, and the scope-coverage percentage is not defined for it. Whether that verdict is permitted is not decided. | Review of §4.2 and §4.3 |
| OI-4 | Collection end time is present on every declaration in this draft, with the value `open` for an ongoing case. The SRS level is `REQUIRED if case is closed`, which also allows omission while a case is ongoing. | Review of §2.2.5 |
| OI-5 | Scope version changes when the declaration is amended. The ordering of version identifiers and the amendment procedure are not in SRS §6.3. §3.3.6 allows a later scope version to name an `arrived_late` element and does not define that procedure. | Later completeness work |
| OI-6 | The three JSON Schema fragments are in `schemas/`. The dialect is draft 2020-12. A time value is a non-empty string, and no calendar format is named. The verdict property may be omitted for the unassigned case in OI-7. That omission is not a fifth verdict. | Review of the fragments against §2, §3, and §4 |
| OI-7 | C-CMP-1 counts only `present` and `redacted` toward `COMPLETE`. C-CMP-2 says `excluded` alone is not `INCOMPLETE` and does not list `disposed` as a gap. An expected class in either state matches none of the four verdicts in §4.3. No fifth verdict is added. | Review of the claims against §3 and §4 |
| OI-8 | A CI-4 reconciliation is stated with the completeness report and is not one of the eight fields in §4.2. SRS §6.5 does not name a field for a coverage discrepancy. | Review of §4.2 and §5.3 |
| OI-9 | Scope-complete with documented gaps requires a reason on every gap. The verdict `incomplete_documented` does not. A gap with no recorded reason keeps that verdict and receives no claim level. `incomplete_undocumented` is a verdict and a §7.2 row, and it is not one of the four levels. An expected class in `excluded` or `disposed` is OI-7 and also receives no level. No fifth level is added. | Review of §6 against §4.3 |
| OI-10 | When every P-1 claim is `NOT_EVALUATED`, §7.1 leaves Passed and Failed unset. SRS §6.8 has no row for that case. This draft does not treat it as Failed. | Review of §7.1 |

---

## 10. References

- ADEP-PHASE0-SRS-v0.1 §6.2, §6.3, §6.4, §6.5, §6.6, §6.7, §6.8, §9.3, §9.6, §9.7, §10.1.3
- PA profile draft §3 (PA-EC-01 through PA-EC-15), §4 (temporal ordering), §5 (PA-EC-20 through PA-EC-24), §6 (exception paths), §7 (versioning), and `schemas/expected-evidence-classes.schema.json`
- Assurance contract v0.2 draft §5.1 (NG-1), §5.2 (NG-2), §6.2 (C-INT-1, C-INT-2), §6.6 (C-CMP-1, C-CMP-2), §6.9 (MC-6, MC-8), and §8 (privacy boundary)
- Trust model v0.2 §5 (five signature types)
- Security baseline v0.1 PRV-MIN-1 (metadata and clinical content), PRV-DSC-1 through PRV-DSC-4 (disclosure profiles), and PRV-BND-3 (verification without clinical content)
- `schemas/evidence-element-state.schema.json`, `schemas/scope-declaration.schema.json`, and `schemas/completeness-report.schema.json` (JSON Schema draft 2020-12)

---

*End of first draft final through W3-T02 — ADEP-WI2-CMP-v0.2*
