# Question Bank

Ask only about what is missing. Rephrase in the user's language. Use at most
5 questions per round, mandatory sections first. Each section lists its
**purpose** (so you can judge if an answer is sufficient), then the questions.

## 1. Feature Summary [M]
Purpose: a short description of what the feature does and the problem it solves.
- In one or two sentences, what does this feature do?
- What problem does it solve, and for whom?

## 1.1. Business Rules [M]
Purpose: the rules, conditions, and constraints that drive test scenarios.
- What are the key business rules? (required fields, allowed values, limits)
- Which conditions should allow or block an action? (permissions, states, thresholds)
- Are there validation rules for the input? (format, length, range, uniqueness)
- Does behavior vary by user type, role, state, or context? How?

## 1.2. Test Scope [M]
Purpose: explicit boundaries so the test plan doesn't cover more or less than intended.
- What is included in the scope of this test plan?
- What is explicitly excluded or out of scope?

## 2. Acceptance Scenarios [M]
Purpose: the must-work behaviors from the user's perspective.
- What are the main actions a user can perform? (the happy paths)
- For each action, what is the expected result?
- What should happen when something goes wrong? (invalid input, unauthorized access, missing data)
- Are there business-critical edge cases that must work correctly?

## 3. Validation Checklists [M — at least one area]
Purpose: identify which testing concern areas apply so the right heuristics
are used. Ask only the questions that seem relevant to the feature.
- Does the feature create, update, or delete data?
- Does the feature accept input with fields, parameters, or uploaded files?
- Does the feature require authentication or limit access by role or ownership?
- Does the entity have states or a lifecycle (e.g., draft, active, archived)?
- Do any rules depend on dates, time periods, or monetary values?
- Does the feature return or display lists, with pagination, filtering, or sorting?
- Does the feature depend on an external service or send notifications?
- Does the feature have a user interface with forms, navigation, or multi-step flows?
- Does this change alter behavior that existing users or systems rely on?

## 4. Automation Mapping [O — always ask once]
Purpose: when included, each scenario and checklist item gets a suggested
automation type (Unit, Integration, E2E, Acceptance, Component).
- Do you want the test plan to include automation type suggestions? (This adds
  a column indicating which type of automated test — Unit, Integration, E2E,
  Acceptance, Component — would best cover each scenario. No code is included,
  only the suggestion.)

## 5. Regression Considerations [O]
Purpose: identify existing behavior that might be affected by the change.
- Does this change alter or replace any existing behavior?
- Which existing features or flows interact with this one?
- Are there known fragile areas that should be re-validated?

## 6. Open Questions [M]
Purpose: collect every unresolved decision and every TBD from the test plan.
- Who should answer each open question?
