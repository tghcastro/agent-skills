<!--
Template rules (remove every HTML comment from the final test plan):
- Translate headings and labels into the output language.
- [M] = mandatory, [O] = optional. Rules are in SKILL.md.
- Remove optional sections that have no confirmed content.
- Never fill a section with assumed content. Use TBD and add an Open Question.
-->
# Test Plan: <Feature Name>

| Field | Value |
|---|---|
| Source | <document titles, work item IDs or links as provided; remove the row if only chat was used> |
| Author | <name or TBD> |
| Status | Draft |
| Last updated | <YYYY-MM-DD> |
| Automation types | Yes / No |

## 1. Feature Summary <!-- [M] -->

> <One or two sentences describing the feature and its purpose.>

### 1.1. Business Rules <!-- [M] -->

| ID | Rule |
|---|---|
| BR-01 | <business rule as stated by the user> |

### 1.2. Test Scope <!-- [M] -->

**In scope:**
- <item included in this test plan>

**Out of scope:**
- <item explicitly excluded>

## 2. Acceptance Scenarios <!-- [M] -->

<!-- Each scenario traces to one or more business rules (BR-xx). Write in
     business-facing Gherkin: no technical details, no HTTP verbs, no database
     columns, no CSS selectors. -->

### SC-01: <Descriptive title> <!-- BR-xx -->

```gherkin
Given <business context>
When <user action>
Then <observable result>
```

### SC-02: <Descriptive title> <!-- BR-xx -->

```gherkin
Given <business context>
When <user action>
Then <observable result>
```

## 3. Validation Checklists <!-- [M] at least one area -->

<!-- Group items by testing concern area. Note the applicable heuristic IDs in a
     comment above each subsection. Items are checkboxes with CL-xx IDs. If
     automation types are enabled, prefix each item with [Type]. -->

### 3.1. <Testing Concern Area> <!-- H-xx -->

- [ ] **CL-01** — <what to validate> → <expected behavior>
- [ ] **CL-02** — <what to validate> → <expected behavior>

### 3.2. <Testing Concern Area> <!-- H-xx -->

- [ ] **CL-03** — <what to validate> → <expected behavior>

## 4. Automation Mapping <!-- [O] only when user opts in; remove entire section otherwise -->

| ID | Scenario / Check | Suggested Type | Priority |
|---|---|---|---|
| SC-01 | <scenario title> | Acceptance / E2E / Integration / Component / Unit | Must / Should / Could |
| CL-01 | <check description> | Acceptance / E2E / Integration / Component / Unit | Must / Should / Could |

## 5. Regression Considerations <!-- [O] -->

- <existing behavior or area to re-validate>

## 6. Open Questions <!-- [M] -->

| ID | Question | Related section | Owner | Status |
|---|---|---|---|---|
| Q-01 | <question> | <section> | <name or TBD> | Open |
