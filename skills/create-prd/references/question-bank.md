# Question Bank

Ask only about what's missing. Rephrase in the user's language. Use at most
5 questions per round, mandatory sections first. Each section lists its
**purpose** (so you can judge if an answer is sufficient), then the questions.

## Scope (always first if unclear)
- Is this a whole project or a single feature? If a feature, which product is it part of?

## 1. Product Headline [M]
Purpose: one sentence stating the value for the target user.
- In one sentence, what does this give its users?

## 1.1. Problem Statement [M]
Purpose: the main issue being solved, who has it and its impact.
- Who has this problem today?
- What do they do today instead (workaround, cost, pain)?
- What evidence do you have (feedback, tickets, data, research)?

## 1.2. Job To Be Done [M]
Purpose: the core job the user needs done, independent of the solution.
- When users reach for this, what are they ultimately trying to get done?

## 1.3. Value Proposition [M project / O feature]
Purpose: expected benefits for users **and** for the business.
- What changes for users if this works?
- What's the business benefit (revenue, retention, cost, risk)?

## 1.4. Stakeholder Responsibilities [O]
Purpose: clear ownership per area.
- Which teams or people are involved, and what does each own?

## 1.5. Shared Delivery Values [O]
Purpose: principles that guide trade-off decisions.
- Are there principles the team should use to settle trade-offs?

## 1.6. Target Audience / Personas [O]
Purpose: who the users are and their key characteristics.
- Who are the primary and secondary users? (roles, segments, personas)
- What are their key characteristics or constraints?
- What are their most important needs or jobs to be done?

## 2.1. User Stories [M] (+ Acceptance Criteria: M for feature)
Purpose: user-centred needs in the form "As a <user>, I want <goal> so that <reason>".
- Which types of users will use it, and what does each need to do?
- Which stories are Must / Should / Could?
- For each story: what observable result means it's done?
- Which edge cases, validations or error situations must be handled?
- Are there business rules or limits (values, permissions, states)? Don't assume; ask.

## 2.2. User Flow [O]
Purpose: the steps from start to finish, including decision points.
- What are the main steps a user goes through? Where can they take different paths?

## 2.3. Design [O]
Purpose: UI/UX principles or constraints that are already decided.
- Are there design guidelines, existing design systems or accessibility needs?

## 2.4. Out of Scope [M]
Purpose: what's explicitly excluded, to prevent scope creep.
- What is explicitly NOT part of this version?

## 2.5. Risks & Dependencies [O]
Purpose: external factors or obstacles that could affect delivery or success.
- Are there external dependencies (other teams, third-party services, infrastructure)?
- What risks could block or delay this? How will they be mitigated?
- Are there assumptions that could fail, and what's the backup plan?

## 3. Non-Functional Requirements [M — always ask; "none specific" is valid]
Purpose: quality expectations for the product (how well it works, not what it
does). Never suggest typical values.
- Performance: are there response-time or volume expectations?
- Security: are there authentication, authorization or data-protection needs?
- Accessibility: is there an accessibility standard or need to meet?
- Privacy & Compliance: do any regulations apply (e.g., data protection laws)?
- Availability: are there uptime or offline-use expectations?

## 3.1. Constraints [O — never ask]
Purpose: technical details the user **explicitly wrote** (e.g., "must use our
existing payment provider"). Record them as written. Don't ask about technical
solutions and don't suggest any.

## 4. Launch Plan [O]
Purpose: how the product reaches users. Ask only if the user wants this part.
- 4.1: What has to be ready before launch (testing, docs, training)?
- 4.2: Soft or full launch? Which regions, segments or channels, and why?
- 4.3: Are marketing activities planned? What are the key messages?
- 4.4: How will sales be supported?
- 4.5: What support will new users get (tutorials, FAQs, channels)?

## 5. KPIs and Value Tracking [O — ask once]
Purpose: how success is measured. If the user doesn't know, leave the section
out and move on.
- Do you already know how success will be measured? If yes: which metric,
  target value, timeframe, and how it's measured?
  (If they're unsure but interested, you may offer candidates such as adoption
  rate or CSAT, labelled `Suggestion — please confirm`.)

## 6. Open Questions [M]
Purpose: collect every `TBD` and unresolved decision.
- Who should answer each open question?
