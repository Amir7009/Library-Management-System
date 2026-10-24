# Proposed Constraints and Indexes

**Status:** Technical proposal; no SQL dialect or DBMS-specific syntax is selected (D03). Constraints below are separated into approved facts that can be represented, proposed structural safeguards, and conditional rules that must wait for open decisions.

## Integrity constraints

### Directly supported facts

- Primary keys identify each catalog or operational record. Exact key type is open under D03.
- `physical_copy.title_id` is non-null and references `book_title.title_id`: every copy belongs to one title (FR-002, FR-003).
- `borrow_request.requester_account_id` and `submitted_at` are non-null: those facts are required by FR-007.
- `loan.copy_id`, `loan.borrower_account_id`, and `loan.due_date` are non-null; a loan identifies a copy and borrower and has a due date (FR-014 and the approved domain model). Whether a loan is created immediately on approval is not decided.
- FR-014 requires an approved borrow request to have a loan and due date; it does not require every loan to have an originating request. Therefore `loan.borrow_request_id` is optional in this proposal, and completeness of the request-to-loan direction is a transaction/business invariant rather than a reverse mandatory FK.
- Return and renewal requests reference a loan and record submission time (FR-011, FR-013). An account is recorded as requester only in the proposed schema where known; exact role-based permission remains open.
- A reservation/queue record references a title, consistent with FR-010. This does not settle queue entry rules or copy allocation.
- Use foreign keys for declared, non-polymorphic references. Prefer `RESTRICT`/`NO ACTION` so catalog or account deletion cannot erase circulation history.

### Proposed technical safeguards

- `copy_claim.copy_id` is the primary key. This is the central portable relational uniqueness mechanism to ensure that two transactions cannot commit separate current-claim rows for the same physical copy.
- A shape `CHECK` on `copy_claim` should require exactly one valid claim reference matching `claim_kind`. Use text plus a CHECK rather than a DBMS enum for portability. Actual CHECK and FK enforcement must be confirmed for the selected DBMS/version.
- For loan claims, a composite FK `(loan_id, copy_id) → loan(loan_id, copy_id)` plus a candidate unique key on the loan pair ensures a claim cannot name a copy other than the loan's copy. For reservation claims, `copy_claim` does not duplicate title data: transaction validation must ensure the reservation's `title_id` equals the physical copy's `title_id`, with concurrent updates serialized. Ordinary FKs on the two separate rows cannot prove this cross-table equality.
- The copy-claim primary key prevents two committed claims for one copy, but it does not ensure that every active loan or copy-bound reservation has a claim. The transaction protocol must maintain that converse invariant for every allocation path.
- Queue-promotion concurrency needs a separate per-entry/request guard because two workers could choose different copies for the same waiting request. If an approved queue-entry lifecycle supports one current promotion, a conditional update of its persisted promotion marker from NULL (or its approved prior state) plus a row lock/compare-and-set can serialize it. If one request may have multiple queue entries, guard the stable request identity as well; a per-entry marker alone is insufficient. A unique active-promotion constraint is another candidate. Marker, reset rule, and cardinality are conditional on D11/D23 and are not business rules selected here. Row-lock syntax and affected-row reporting details must be checked for the selected DBMS.
- Use unique constraints on stable identifiers only when their uniqueness scope and normalization are defined. Role codes are unique in the proposed role catalog. Do not invent unique bibliographic fields or category labels.
- Index every frequently joined FK when the selected DBMS does not create that index automatically; the primary/unique constraint on the referenced key already supplies the referenced-side index in common relational systems, but confirm platform specifics.
- Avoid duplicate stored state such as an independently writable availability flag or overdue flag when it can conflict with operational records and approved due dates (FR-006, FR-015).
- Historical request, loan, return, renewal, fine, notification, and audit rows should not be cascade-deleted from parent account/title/copy rows. Retention and account-erasure policy remain open; physical deletion must not destroy auditability by default.

### Conditional integrity rules — not active until decisions resolve

| Candidate rule | Why conditional |
|---|---|
| One category per title (`book_title.category_id`) or many-to-many `title_category` with composite PK | Category cardinality/taxonomy remains open (D19; D41 is merged into D19). |
| Single role FK on account or `user_role` bridge; any role/action grant constraints | Assignment cardinality and permissions remain open (D12, D30). Role names do not grant actions. |
| Exactly one of `borrow_request.title_id` / `copy_id` non-null (XOR CHECK), or normalized target subtype | Request target form remains open. FR-007 names a title or eligible copy, but its persistence choice is not approved. |
| Mandatory `loan.borrow_request_id`, and `UNIQUE(borrow_request_id)` on loan | FR-014 establishes approved-request → loan, not loan → request or exact multiplicity. Keep the FK nullable; decide any one-loan limit separately. |
| Unique active queue membership, one active reservation per account/title, reservation-to-copy constraints, or queue ordering uniqueness | Membership, eligibility, expiry, duplicate entries, ties, and allocation policies remain open (D11, D23, D40; D39 is merged into D11). Do not enforce strict FIFO beyond BR-003’s qualified rule for already-eligible requests in the same applicable queue. |
| Mandatory fine-to-loan link, fine amount nonnegative, currency, rounding/scale, or uniqueness per loan | Fine linkage/cardinality and formula remain open (D09, D25; D29 is merged into D09). Keep `fine.loan_id` nullable and conditional until the association is approved. |
| Unique/one-pending return or renewal request per loan; mandatory reviewer/outcome; return-date update rule | Review and request lifecycle remain open (D10, D24, D25; D27 is merged into D10). FR-012 permits an authorized employee to review and record an outcome; it does not require review of every return. |
| Non-overlapping policy effective intervals, key registry, mandatory policy values | Persistent policy storage and effective-period semantics are not approved. |

## Proposed indexes

These are workload-oriented candidates; validate with actual query patterns and the selected DBMS. An index does not settle a business rule.

| Candidate index | Purpose / caveat |
|---|---|
| `physical_copy(title_id, copy_id)` | Find copies for a title and support catalog/availability queries. |
| `borrow_request(requester_account_id, submitted_at)` | Personal request history and chronological access. |
| `borrow_request(submitted_at)` or `(outcome, submitted_at)` | Review queues; outcome index is useful only if outcome labels/query semantics are settled. No priority/tie rule implied. |
| `waiting_queue(title_id)` | Locate queues by title. |
| `queue_entry(queue_id, entered_at)` | Candidate scan order only; submission-time ordering is the requirement for eligible requests within the same applicable queue (BR-003). Membership and eligibility policy remain open; do not use this index to imply FIFO eligibility/ties. |
| `queue_entry(promotion_reservation_id)` | Candidate lookup for the optional promotion guard; add only if the marker/link is approved. A uniqueness rule is conditional on D11/D23 lifecycle cardinality. |
| `reservation(queue_entry_id)` | Candidate provenance lookup for queue promotion; add only if that association is approved. |
| `reservation(title_id, created_at)` | Find title-associated reservation records; no expiry rule implied. |
| `loan(borrower_account_id, due_date)` | Personal loan dashboard and due-date queries, subject to permissions (D30, D32). |
| `loan(copy_id)` | Copy history/availability and copy-level integrity checks. A unique active-copy index is not portable unless active-state representation is approved; use `copy_claim` for proposed exclusive allocation. |
| `return_request(loan_id, submitted_at)`; `renewal_request(loan_id, submitted_at)` | Retrieve request history for a loan without requiring one-pending-request semantics. |
| `fine(loan_id)` | Retrieve linked fine records if that optional association is approved; nullability/cardinality remain unresolved. |
| `notification(recipient_account_id, created_at)` and optionally `(recipient_account_id, read_at, created_at)` | Dashboard retrieval; read behavior/index usefulness depends on D33. |
| `audit_event(occurred_at)`, `(actor_account_id, occurred_at)`, `(target_type, target_id, occurred_at)` | Time-window and actor/target audit queries. Target pair is polymorphic, not FK constrained; coverage/access are open (D34). |
| `copy_claim` primary key `(copy_id)` | Atomic contention point for exclusive current claims. A unique index on `reservation_id` is conditional on reservation-to-copy cardinality; no separate unique `loan_id` index is needed because the composite loan/copy FK and `copy_id` primary key already constrain a loan claim to its loan's one copy. |
| `policy_revision(policy_key, revision_number)` | Candidate lookup/version uniqueness if persistent policy storage is approved. Effective-time lookup needs a decision on interval semantics and possibly DBMS-specific indexing. |

No partial/filtered indexes, exclusion constraints, advisory locks, vendor-specific enum types, or vendor-specific JSON operators are required by this proposal. A selected DBMS may offer useful stronger mechanisms, but they need a separate compatibility and migration review; D03 remains open.
