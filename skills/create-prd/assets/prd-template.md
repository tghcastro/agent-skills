<!--
Template rules (remove every HTML comment from the final PRD):
- Translate headings and labels into the output language.
- [M] = mandatory, [O] = optional. Scope-specific rules are in SKILL.md.
- Remove optional sections that have no confirmed content.
- Never fill a section with assumed content. Use TBD and add an Open Question.
-->
# PRD: <Product or Feature Name>

| Field | Value |
|---|---|
| Scope | Project / Feature (of <product>) |
| Author | <name or TBD> |
| Status | Draft |
| Last updated | <YYYY-MM-DD> |
| Sources | <chat; document titles; work item IDs or links as provided. Remove the row if only chat was used> |

## 1. Product Headline <!-- [M] -->

> <One clear sentence stating the value for the target user.>

### 1.1. Problem Statement <!-- [M] -->
- <Who has the problem, what the problem is, its current impact or workaround>
- <Evidence, if provided: surveys, tickets, data>

### 1.2. Job To Be Done (JTBD) <!-- [M] -->
<One or two sentences: the core job the user needs done.>

### 1.3. Value Proposition <!-- [M] project / [O] feature -->
- **Users:** <benefit>
- **Business:** <benefit>

### 1.4. Stakeholder Responsibilities <!-- [O] -->
| Stakeholder / Area | Responsibility |
|---|---|

### 1.5. Shared Delivery Values <!-- [O] -->
1. **<Value>:** <short description>

### 1.6. Target Audience / Personas <!-- [O] -->
| Persona / Segment | Characteristics | Key Needs |
|---|---|---|
| | | |

## 2. Solution Overview

### 2.1. User Stories <!-- [M] -->
| ID | User Story | Priority |
|---|---|---|
| US-01 | As a <user>, I want <goal> so that <reason>. | Must / Should / Could |

<!-- [M] for Feature, [O] for Project: acceptance criteria per story -->
**Acceptance Criteria**
| ID | Story | Given / When / Then |
|---|---|---|
| AC-01 | US-01 | Given <context>, when <action>, then <observable result>. |

### 2.2. User Flow <!-- [O] -->
1. **<Step>:** <user or system action>

### 2.3. Design <!-- [O] -->
- **<Consideration>:** <description>

### 2.4. Out of Scope <!-- [M] -->
- <Item explicitly excluded from this version>

### 2.5. Risks & Dependencies <!-- [O] -->
| Item | Type | Mitigation / Notes |
|---|---|---|
| | Risk / Dependency | |

## 3. Non-Functional Requirements <!-- [M] always asked; if the user says none, write "No specific requirements." -->
| ID | Category | Requirement |
|---|---|---|
| NFR-01 | Performance / Security / Accessibility / Privacy & Compliance / Availability | <requirement as stated by the user> |

### 3.1. Constraints <!-- [O] only technical details the user explicitly wrote; never asked for or suggested -->
- <constraint as stated by the user>

## 4. Launch Plan <!-- [O] include only the subsections with confirmed content -->

### 4.1. Pre-Launch Preparations
- <activity>

### 4.2. Launch Strategy
<Soft or full launch, regions, segments, channels, and the reasons for these choices.>

### 4.3. Marketing and Promotion Strategy
- <activity → key message → expected outcome>

### 4.4. Sales Enablement
- <activity>

### 4.5. Customer Support and Training
- <support structure>

## 5. KPIs and Value Tracking <!-- [O] asked once; remove the section if the user doesn't know -->
| ID | KPI | Target | Timeframe | How it's measured |
|---|---|---|---|---|
| KPI-01 | <e.g., adoption rate> | <value> | <period> | <source> |

## 6. Open Questions <!-- [M] -->
| ID | Question | Related section | Owner | Status |
|---|---|---|---|---|
| Q-01 | <question> | <section> | <name or TBD> | Open |
