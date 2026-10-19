# Functional Requirements — Requirements Workflow Step 02

> Status: Requirements baseline prepared from approved project documentation
> and the user's Step 02 prompt. Project Phase 02 remains the console
> application; this file does not authorize implementation.
> Policy choices marked open are not requirements until explicitly approved.

## Requirement conventions

Each requirement has a unique `FR-NNN` identifier and describes observable
system behavior. `[Approved]` identifies scope already approved in project
documentation; `[User-directed]` identifies behavior explicitly requested for
this requirements baseline. `[Open]` points to a decision and must not be
implemented as a selected policy. References use the decision register in
[open-decisions.md](open-decisions.md).

## Catalogue and accounts

| ID | Requirement | Status / trace |
|---|---|---|
| FR-001 | An authorized operator shall be able to create and edit book-category records and assign categories to catalogue titles. Category values, hierarchy, permissions, and assignment cardinality remain open (D19, D30). | Category capability requested; policy open |
| FR-002 | The system shall maintain a catalogue record for each book title and support category association as decided under D19. The catalogue shall distinguish a title from its physical copies. | [Approved] catalogue and book/copy distinction; category association requested |
| FR-003 | The system shall maintain each physical copy as a separately identifiable record associated with one catalogue title, including its availability state. | [Approved] individual copies; detailed copy states remain to be specified |
| FR-004 | The system shall create and maintain user accounts for manager, employee, student, and guest roles. | [Approved] roles; privileges and role grants remain open (D12, D30) |

## Search, availability, and circulation

| ID | Requirement | Status / trace |
|---|---|---|
| FR-005 | A user granted catalogue access shall be able to search the catalogue and view matching book records. Search fields, matching, and sorting remain open (D30–D31). | Catalogue/search capability requested |
| FR-006 | For users granted catalogue access, a catalogue result shall show copy-level availability derived from the copy and loan/request records. | Availability requested; access and status definitions depend on D11, D23, D30 |
| FR-007 | A user with the required permission shall be able to submit a borrow request for a title or eligible copy; the system shall record its requester, target, and submission time. | Borrow requests [Approved]; target and eligibility policy open |
| FR-008 | The system shall order requests in the same applicable queue by recorded submission time, earliest first. FIFO applies only to requests already eligible for that queue and does not decide queue membership, priority exceptions, reservation allocation, or equal-timestamp tie handling (D40). | [User-directed] FIFO request ordering; broader queue policy remains open (D11) |
| FR-009 | An employee shall be able to review a borrow request and approve or reject it, with the decision and decision time recorded. Rejection reasons and whether a rejected request may be resubmitted remain open (D23). | Employee review requested; operational working-hours requirement is approved; automatic enforcement remains open (D18) |
| FR-010 | The system shall support reservations and waiting-queue records associated with a book title, and shall present the queue in its applicable order. Enrollment, availability triggers, allocation, and expiration remain open (D11). | [Approved] capability; policy open |
| FR-011 | A borrower shall be able to submit a return request for an active loan; the system shall record the request and its submission time. | Return processing [Approved]; review and effective date open (D24–D25) |
| FR-012 | An authorized employee shall be able to review a return request and record its outcome. Whether every return requires review or only exceptions do remains open (D24). | Return review is user-requested; workflow policy open |
| FR-013 | A borrower shall be able to submit a renewal request for an active loan, and the system shall record its outcome. Eligibility, limits, decision authority, and handling of a pending renewal remain open (D10, D30). | Renewal requests [Approved]; policy open |
| FR-014 | For an approved borrow request, the system shall record a loan and a due date. The due-date calculation and loan period remain open (D13). | [Approved] capability; values open |
| FR-015 | The system shall identify loans as overdue according to the approved due-date and return-date rules and shall allow a fine to be recorded for a late return. Fine amounts, calculation, grace periods, and effective return date remain open (D09, D25). | [Approved] fine-recording capability; calculation open |

## Member information and governance

| ID | Requirement | Status / trace |
|---|---|---|
| FR-016 | A user shall be able to view a personal dashboard containing the library information that the user's approved permissions allow. Dashboard contents and role visibility remain open (D30, D32). | Profiles [Approved]; dashboard details requested |
| FR-017 | The system shall create in-app notifications for configured circulation and account events and make them available to the intended user. The event list and delivery/read behavior remain open (D33). | In-app channel [Approved] under assumption A4; event policy open |
| FR-018 | The system shall record an audit history for significant actions, including actor, action, target, and time where available, and permit authorized review of that history. Exact event coverage, visibility, and retention remain open (D34). | Audit records [Approved]; detail open |
| FR-019 | An authorized operator shall be able to produce a data backup and follow a documented procedure to restore it. Backup schedule, owner, location, retention, and recovery targets remain open (D16, D38). | [Approved] backup/recovery capability; operations open |

## Delivery boundaries

| ID | Requirement | Status / trace |
|---|---|---|
| FR-020 | The first user-facing application shall be operated through a console interface. | [Approved] initial interface; UI language remains open (D07) |
| FR-021 | The shared application behavior shall be usable independently of the console front-end. | [Approved] architecture constraint (R12) |
| FR-022 | The architecture shall preserve the planned delivery path of a later REST API followed by a web interface over the shared application behavior; neither interface is a deliverable of requirements-workflow Step 02. | [Approved] delivery direction; future work only |

## Acceptance notes

Each requirement can be turned into one or more acceptance checks once open
policies are decided. A check for a requirement tied to an open decision must
verify the capability without asserting an unapproved value or policy.
