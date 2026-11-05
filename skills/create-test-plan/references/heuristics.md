# Testing Heuristics

A heuristic is a trigger question plus a set of scenario templates. For each
feature, check which trigger questions apply, then use the matching scenarios as
a starting point — adapt them to the feature's context.

## Markers

- **`[ACC]`** — Acceptance-level scenario. Write it as business-facing Gherkin
  in Section 2 of the test plan.
- All other scenarios become validation checklist items in Section 3.

## Index

| ID | Testing Concern | Priority | Applies to |
|---|---|---|---|
| H-01 | Data Creation and Mutation | Core | Any |
| H-02 | Input Validation and Constraints | Core | Any |
| H-03 | Uniqueness and Deduplication | When applicable | Any |
| H-04 | Data Retrieval and Display | Core | Any |
| H-05 | Pagination and Navigation | When applicable | Any |
| H-06 | Filtering and Search | When applicable | Any |
| H-07 | Sorting and Ordering | When applicable | Any |
| H-08 | Single Item Access | Core | Any |
| H-09 | Deletion and Referential Integrity | When applicable | Any |
| H-10 | State and Lifecycle | When applicable | Any |
| H-11 | Date, Time and Periods | When applicable | Any |
| H-12 | Monetary Values and Precision | When applicable | Any |
| H-13 | Authentication and Session | Core | Any |
| H-14 | Authorization and Ownership | Core | Any |
| H-15 | Input Hardening and Security | Core | Any |
| H-16 | Data Exposure and Privacy | Core | Any |
| H-17 | Error Handling and User Feedback | Core | Any |
| H-18 | Concurrency and Idempotency | When applicable | Any |
| H-19 | Backward Compatibility and Migration | When applicable | Any |
| H-20 | Audit and Traceability | When applicable | Any |
| H-21 | Rate Limiting and Abuse Prevention | When applicable | Any |
| H-22 | Performance and Resilience | When applicable | Any |
| H-23 | Time Zones and Localization | When applicable | Any |
| H-24 | UI Behavior and Accessibility | When applicable | UI |
| H-25 | Navigation and Multi-step Flows | When applicable | UI |
| H-26 | Notifications and Messaging | When applicable | Any |
| H-27 | File and Media Handling | When applicable | Any |
| H-28 | External Dependencies and Integrations | When applicable | Any |

---

## Data Integrity

### H-01 Data Creation and Mutation

**Trigger:** Can the feature create, update, or delete data?
**Applies to:** Any
**Priority:** Core
**Techniques:** equivalence partitioning

- [ACC] Valid create, update, or delete by an authorized user succeeds and the change is persisted
- Unauthorized attempt to modify data is rejected (see H-14)
- Bulk operation enforces minimum and maximum list size

### H-02 Input Validation and Constraints

**Trigger:** Does the feature accept input with fields or parameters?
**Applies to:** Any
**Priority:** Core
**Techniques:** equivalence partitioning, boundary value analysis

- Only mandatory fields provided — accepted
- Mandatory and optional fields provided — accepted, optional values persisted
- [ACC] Missing mandatory field — rejected with a clear, field-level message
- Wrong data type (text for a number, number for a boolean) — rejected
- Wrong semantic value (e.g., a date that is not a real date, an amount with too many decimals) — rejected
- Text at maximum length — accepted; one character over maximum — rejected
- Numeric value at minimum and maximum boundary — accepted; one below minimum or above maximum — rejected
- Enum or option: each valid value accepted; unknown value rejected; empty value handled per requirements
- Leading and trailing whitespace, whitespace-only input, unicode, and emoji — trimmed, rejected, or accepted per requirements

### H-03 Uniqueness and Deduplication

**Trigger:** Must any value be unique (e.g., email, category name)?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** error guessing

- [ACC] Exact duplicate — rejected with a conflict message
- Case or whitespace variant of an existing value — handled per requirements
- Same value owned by a different user — allowed when uniqueness is per user
- Value previously used by a soft-deleted record — handled per requirements

---

## Data Retrieval

### H-04 Data Retrieval and Display

**Trigger:** Does the feature return or display a collection of items?
**Applies to:** Any
**Priority:** Core
**Techniques:** equivalence partitioning

- [ACC] Non-empty collection — every expected field present on each item
- No data — empty state displayed or returned correctly
- [ACC] Soft-deleted, inactive, or wrong-status records — excluded from results
- Records owned by other users — excluded (see H-14)

### H-05 Pagination and Navigation

**Trigger:** Is the collection paginated or loaded incrementally?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** boundary value analysis

- [ACC] Full page, partial last page, and empty page — correct items and navigation metadata
- Request beyond the last page — empty result, not an error (or per requirements)
- Page size of zero, negative, above maximum, or non-numeric — rejected or clamped per requirements
- Invalid or tampered page token — rejected

### H-06 Filtering and Search

**Trigger:** Can the user narrow results by criteria or search terms?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** equivalence partitioning, pairwise (for multiple filters)

- [ACC] Single supported filter — only matching items returned
- Valid filter with no matches — empty result
- Unsupported filter parameter — rejected or ignored per requirements
- Filter values of wrong type, out of range, invalid enum, or empty — rejected per H-02
- Combined filters — intersection applied correctly
- Search with partial match, exact match, and no match — results as expected
- Search with special characters — handled safely

### H-07 Sorting and Ordering

**Trigger:** Do results have a default or user-chosen order?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** equivalence partitioning

- [ACC] Default order applied when none is specified
- Each supported sort field, ascending and descending — correct order
- Equal sort values — deterministic tie-breaker, stable across pages
- Unsupported sort field or direction — rejected per requirements

### H-08 Single Item Access

**Trigger:** Does the feature show or return one item by identifier?
**Applies to:** Any
**Priority:** Core
**Techniques:** decision table (exists / deleted / owned by other)

- [ACC] Existing item accessible to the user — displayed or returned with all expected fields
- [ACC] Non-existing identifier — clear not-found message
- Soft-deleted or wrong-status item — not-found (or per requirements)
- Item belonging to another user — see H-14
- Malformed identifier — validation error, not a system error

---

## State and Lifecycle

### H-09 Deletion and Referential Integrity

**Trigger:** Can a record be deleted while others depend on it?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** decision table

- Delete with no dependents — succeeds
- [ACC] Delete with dependents — blocked, cascaded, or reassigned per requirements
- [ACC] Soft delete — record hidden from lists and detail views but preserved for history
- Delete twice — idempotent or not-found per requirements

### H-10 State and Lifecycle

**Trigger:** Does the entity have states or a lifecycle (e.g., draft, active, archived)?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** state transition testing

- [ACC] Each allowed state transition — succeeds
- Each forbidden state transition — rejected
- Operations allowed or blocked depending on current state

### H-11 Date, Time and Periods

**Trigger:** Does a rule depend on a date, time, or period?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** boundary value analysis

- Before the start, exactly at start, inside, exactly at end, after the end — expected outcome for each
- Inclusive versus exclusive bounds confirmed against requirements
- Same action repeated across different periods — each period evaluated independently
- Month-end and leap day (February 29) dates

### H-12 Monetary Values and Precision

**Trigger:** Does the feature store, compute, or display money?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** boundary value analysis, error guessing

- Rounding rule applied consistently (scale and mode per requirements)
- [ACC] Totals and balances match the sum of individual amounts — no precision drift
- Zero, negative (if allowed), and very large amounts
- Currency of each amount preserved and not mixed in aggregations

---

## Security

### H-13 Authentication and Session

**Trigger:** Does the feature require an authenticated user?
**Applies to:** Any
**Priority:** Core
**Techniques:** equivalence partitioning

- [ACC] Valid credentials or session — access granted
- [ACC] Missing credentials — unauthenticated error
- Invalid, malformed, or expired credentials — unauthenticated error
- Credentials of a deleted or disabled user — unauthenticated error

### H-14 Authorization and Ownership

**Trigger:** Is access limited by role, permission, or ownership?
**Applies to:** Any
**Priority:** Core
**Techniques:** decision table

- Owner or allowed role performs read, create, update, delete — allowed
- [ACC] Attempt to access another user's resource — denied
- Attempt to link to another user's resource — denied
- [ACC] Lists and aggregates never include other users' data

### H-15 Input Hardening and Security

**Trigger:** Does the feature accept user-provided input?
**Applies to:** Any
**Priority:** Core
**Techniques:** error guessing

- Unknown or extra fields — ignored or rejected; never silently applied
- Injection payloads (SQL, script tags) in text fields — stored and returned safely, never executed
- Oversized payload — rejected
- Wrong content type — rejected

### H-16 Data Exposure and Privacy

**Trigger:** Does the feature return, display, or log user data?
**Applies to:** Any
**Priority:** Core
**Techniques:** error guessing

- Sensitive fields (e.g., password hash) never exposed to the user
- Responses or screens contain only fields defined in the requirements
- Logs contain no secrets or personal data, per the project's conventions

---

## Reliability

### H-17 Error Handling and User Feedback

**Trigger:** Can the feature fail?
**Applies to:** Any
**Priority:** Core
**Techniques:** error guessing

- Each expected failure — documented error message or state
- Messages are actionable and reveal no internal details (stack traces, queries, other users' data)
- Unexpected failure — generic error, details logged only
- Partial failure in a batch — all-or-nothing or per-item results per requirements
- Error state is visually clear and the user can recover or retry

### H-18 Concurrency and Idempotency

**Trigger:** Can the same data be changed by parallel or retried requests?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** error guessing

- Concurrent updates to one record — conflict detected or defined winner, no lost update
- Concurrent creates of a unique value — exactly one succeeds
- Balances and aggregates stay consistent after concurrent writes
- Retried request — no duplicate side effects (if idempotency is required)

### H-19 Backward Compatibility and Migration

**Trigger:** Does the change alter behavior or a contract that existing users rely on?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** regression testing

- New behavior with newly created data — as specified
- New behavior with data created before the change — still valid, migrated without loss
- Existing inputs still accepted
- [ACC] Existing scenarios in the regression scope still pass

---

## Operations

### H-20 Audit and Traceability

**Trigger:** Must the system record who changed what and when?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** verification

- Create, update, and delete — audit entry with actor, timestamp, and changed values
- Audit entries cannot be changed or deleted by regular users

### H-21 Rate Limiting and Abuse Prevention

**Trigger:** Can the feature be abused by repetition or volume?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** error guessing

- [ACC] Repeated failed attempts (e.g., login) — throttled or locked per requirements
- Requests above the limit — rate-limit error; normal traffic unaffected

### H-22 Performance and Resilience

**Trigger:** Is there an expected volume, latency target, or external dependency?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** performance testing

- Response time within target at expected and peak volume
- Dependency slow, down, or timing out — graceful failure, no data corruption
- Retries and backoff — no duplicate processing

### H-23 Time Zones and Localization

**Trigger:** Does the feature store or display dates, numbers, or text that vary by locale?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** boundary value analysis

- Dates stored in one canonical zone and converted consistently
- Actions near midnight or daylight saving transitions land in the correct day
- Number and currency formatting per supported locale

---

## User Interface and Experience

### H-24 UI Behavior and Accessibility

**Trigger:** Does the feature have a user interface?
**Applies to:** UI
**Priority:** When applicable
**Techniques:** exploratory testing, usability testing

- [ACC] Loading, empty, error, and success states — each visually distinct and correct
- All interactive elements reachable and operable via keyboard
- Screen reader announces content and state changes
- Focus managed correctly after actions (create, delete, modal open/close)
- Layout works at standard breakpoints (mobile, tablet, desktop)
- Form fields show inline validation feedback
- Unavailable actions appear disabled with an explanation

### H-25 Navigation and Multi-step Flows

**Trigger:** Does the feature involve multiple steps, pages, or a wizard?
**Applies to:** UI
**Priority:** When applicable
**Techniques:** state transition testing, exploratory testing

- [ACC] Complete flow from first to last step — succeeds
- Back and forward navigation preserves previously entered input
- Abandonment and return — behavior per requirements (data saved or discarded)
- Direct link to a mid-flow step — handled per requirements
- Unsaved changes warning when leaving
- Progress indicator reflects the current step accurately

---

## Integration and Communication

### H-26 Notifications and Messaging

**Trigger:** Does the feature send notifications (email, push, in-app, SMS)?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** equivalence partitioning, error guessing

- [ACC] Notification delivered with correct content and recipient when the trigger condition is met
- Notification not sent when the condition is not met
- Duplicate action does not send a duplicate notification
- Notification content in the user's language or locale
- Unsubscribe or preference setting respected

### H-27 File and Media Handling

**Trigger:** Does the feature accept, store, or display files?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** equivalence partitioning, boundary value analysis, error guessing

- [ACC] Supported file type accepted and stored or displayed correctly
- Unsupported file type rejected with a clear message
- File at size limit accepted; above size limit rejected
- Empty file handled per requirements
- Malicious file content (script in image, macro in document) handled safely
- Upload progress and cancellation work correctly

### H-28 External Dependencies and Integrations

**Trigger:** Does the feature depend on an external service or third-party system?
**Applies to:** Any
**Priority:** When applicable
**Techniques:** error guessing

- [ACC] Integration works end-to-end with valid data
- External service unavailable — graceful degradation or clear error
- External service slow or timing out — timeout handling
- Invalid response from external service — no data corruption
- Credential or token refresh — handled if applicable
