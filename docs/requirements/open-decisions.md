# Requirements Workflow Step 02 Open Decisions

This step-specific register preserves the authoritative decisions in
[`../open-decisions.md`](../open-decisions.md). D01–D18 retain their existing
names and **Open** statuses; this file does not resolve or replace them.
Decision IDs D19 onward are additions surfaced while defining requirements.
Every recommendation below is **UNAPPROVED** and is not an implementation
instruction. Resolve a decision only through explicit user/course approval,
then update both the authoritative register and affected requirements.

## Existing decisions preserved

| ID | Existing decision | Status |
|---|---|---|
| D01 | Target Java version | Open |
| D02 | Build tool | Open |
| D03 | Persistence approach | Open |
| D04 | Package and module layout | Open |
| D05 | Test framework | Open |
| D06 | REST stack | Open |
| D07 | Console UI language | Open |
| D08 | Branching strategy | Open |
| D09 | Fine calculation rules | Open |
| D10 | Renewal eligibility and limits | Open |
| D11 | Waiting-queue and reservation policy | Open |
| D12 | Guest borrowing privileges | Open |
| D13 | Loan durations and due-date rules | Open |
| D14 | Concurrent borrowing/reservation limits | Open |
| D15 | Manager reports and exports | Open |
| D16 | Backup ownership and storage location | Open |
| D17 | Academic grading criteria | Open |
| D18 | Automatic enforcement of working hours, holidays, and time zones | Open |

The approved operational practice that employees process borrowing requests
during working hours is distinct from D18's open question about automatic
software enforcement.

## Step 02 policy decisions

For each decision, the recommendation is a discussion aid only and is
**UNAPPROVED**.

| ID | Question and available choices | UNAPPROVED recommendation |
|---|---|---|
| D19 | **Category taxonomy and association:** fixed built-in categories; operator-managed controlled categories; free-text categories; one required or optional category per title; multiple categories; or one primary category plus optional tags. | Operator-managed controlled categories with one primary category and optional tags, to reduce spelling variants while allowing catalogue growth. This is unapproved. |
| D20 | **Can staff borrow as members?** Prohibit staff loans; allow an employee account also to have member status; or require a separate member account linked to staff identity. | Allow staff to borrow only through explicit member status, with staff and member permissions kept distinct. |
| D21 | **Merged into D11 — queue enrollment trigger.** The policy remains Open under D11; choices are automatic entry on a borrow request, explicit opt-in, explicit reservation, or no waiting-list entry. | The prior recommendation is retained as historical discussion only: explicit opt-in. It remains unapproved and is not a separate decision. |
| D22 | **Merged into D11 — reservation activation and duration.** The policy remains Open under D11; choices include no expiry, fixed/configured expiry, or expiry beginning when a copy is offered. | The prior recommendation is retained as historical discussion only: configurable hold period beginning on offer. It remains unapproved and is not a separate decision. |
| D23 | **Unprocessed requests:** remain pending indefinitely; expire after a configured period; be withdrawn by the requester; or escalate/remind staff before expiry. Determine whether borrow, return, and renewal requests share a policy. | Keep requests pending with a visible age and staff reminder; use no automatic expiry until a duration and consequences are approved. |
| D24 | **Return request review:** employee approval for every return; automatic acceptance with employee review only for exceptions; or automatic acceptance. | Record the request immediately and let an employee confirm it, pending a decision on whether all returns require review. |
| D25 | **Effective return date:** request submission time; employee approval time; or a separate recorded physical-receipt time. Physical handover is outside the application, so any receipt-time option must be a user-entered record. | Use request submission time for the recorded return date, with later employee review preserving both timestamps. |
| D26 | **Merged into D13 — loan period and due-date configuration.** The policy remains Open under D13; choices include global, role-based, category-based, or operator-configured duration and calendar-day/business-day/holiday calculation. | The prior recommendation is retained as historical discussion only: operator-configured durations. It remains unapproved and is not a separate decision. |
| D27 | **Merged into D10 — renewal authority and limits.** The policy remains Open under D10; options include no renewals, limited/multiple renewals, staff approval, or automatic decisions, with limits potentially global, role-based, or category-based. D11 and D14 remain related constraints. | The prior recommendation is retained as historical discussion only: staff review and no automatic extension during a queue conflict. It remains unapproved and is not a separate decision. |
| D28 | **Merged into D18 — schedule inputs, conditional on automatic enforcement.** The policy remains Open under D18; if enforcement is approved, schedule, holiday calendar, and time-zone choices must also be decided. | The prior recommendation is retained as historical discussion only: one operator-configured library schedule/calendar/time zone. It remains unapproved and is not a separate decision. |
| D29 | **Merged into D09 — fine calculation and configuration.** The policy remains Open under D09; choices include amount/formula, grace period, cap, currency, and rounding. D25 remains related because the effective return date affects overdue calculation. | The prior recommendation is retained as historical discussion only: configurable per-day amount, grace period, and cap. It remains unapproved and is not a separate decision. |
| D30 | **Role grants and permissions:** broad manager/employee/member tiers; least-privilege grants configured per action; or another course-defined matrix. Decide whether guests can search, reserve, or borrow and whether staff are members. | Explicit least-privilege grants per action; self-service restricted to own records; managers receive only separately approved oversight grants. Links D12, D20. |
| D31 | **Search behavior:** exact match; prefix/substring match; tokenized text; or combinations. Decide searchable fields, case/diacritic handling, and result ordering. | Case-insensitive matching on title, author, and category with relevance ordering; fields and matching rules remain unapproved. |
| D32 | **Dashboard contents and visibility:** minimal personal loans/requests; include fines and notifications; include history; role-configured panels; or other. | Show a user only their own circulation state and notifications, subject to D30; no staff-wide content by default. |
| D33 | **Notification events and lifecycle:** notify every state transition; selected events only; read/unread state; retention or dismissal rules. | Notify request submission and staff decisions, plus availability/overdue events when those workflows are approved; retain unread state until the user reads or dismisses. |
| D34 | **Audit coverage, access, and retention:** append-only history for all changes; significant actions only; role-limited access; fixed or indefinite retention. | Append-only records of significant state changes, access-limited by D30; retention period remains unapproved. |
| D35 | **Merged into D16 — backup operations.** The policy remains Open under D16; schedule, storage, retention/rotation, restore rehearsal, and operational owner are details of the existing backup decision. | The prior recommendation is retained as historical discussion only: named operator, scheduled backups, protected storage, and periodic restore rehearsal. It remains unapproved and is not a separate decision. |
| D36 | **Performance and scale targets:** define response-time and expected record/user volumes; or defer numeric targets for the course-scale baseline. | Defer numeric targets until representative course data and evaluation expectations are known; this is not a claim that performance is unlimited. Links assumption A5. |
| D37 | **Account security:** password policy and recovery; account lockout; session handling; administrative reset; or course-provided authentication. | Use a standard framework-supported credential and recovery approach once D01–D05 and course constraints are known; no specific mechanism is selected. |
| D38 | **Recovery objectives and availability:** define recovery-point and recovery-time targets; or document backup/restore capability without numeric service targets. | Require a documented, rehearsed restore first, then set numeric objectives with the course/operator; no numeric target is approved. Links D16. |
| D39 | **Merged into D11 — queue scope, allocation, and ineligible entries.** The policy remains Open under D11; choices include title/copy queues, automatic/staff allocation, and handling of ineligible entries. FIFO for eligible requests remains user-directed; equal-timestamp handling is separately D40. | The prior recommendation is retained as historical discussion only: title-level queue and earliest eligible request. It remains unapproved and is not a separate decision. |
| D40 | **Equal-timestamp request ordering:** preserve insertion order; use a unique request identifier; use another recorded sequence; or treat simultaneous submissions as tied. | Use a stable, unique request identifier as a deterministic tie-breaker. This is unapproved. |
| D41 | **Merged into D19 — category association cardinality.** The policy remains Open under D19; category count and primary/secondary/tag relationships are part of category taxonomy. | The prior recommendation is retained as historical discussion only: one controlled primary category and optional tags. It remains unapproved and is not a separate decision. |

## Existing business-policy decisions with options

These entries expand the choices for existing open decisions; they do not
change their status in the authoritative register.

| ID | Available choices | UNAPPROVED recommendation |
|---|---|---|
| D09 | No fines; flat amount per overdue loan; per-day amount; tiered amount; optionally add grace period, cap, or both; decide currency and rounding. | Configurable per-day amount with grace period and cap, pending course direction. |
| D10 | No renewals; one renewal; multiple renewals; renewal allowed only if no eligible waiter; employee approval or automatic decision; global, role-based, or category-based limits. | Request plus employee decision, with no extension while a conflicting eligible wait exists; exact count and conditions unapproved. |
| D11 | Title-level or copy-level queue; automatic or staff allocation; enrollment on borrow request, opt-in, or explicit reservation; reservation activation and no/fixed/configured expiry; handling or skipping ineligible entries. FIFO request order is separately specified by BR-003 for eligible requests, with equal-timestamp ties under D40. | Opt-in title-level queue, earliest eligible request offered an available copy, with a configurable hold period; all policy components unapproved. |
| D12 | Guests may have no account; catalogue search only; search plus reservation; or circulation access subject to limits. | Catalogue search and availability only until guest privileges are specified; this recommendation is unapproved. |
| D13 | One global loan period; per-role or per-category periods; operator-configured rules; calendar-day or business-day calculation; configured holidays or no holiday calendar. | Configurable per-role period with calendar-day calculation until course-specific values are known; unapproved. |
| D14 | No concurrent limit; one global limit; per-role or per-category limits; separate loan and reservation limits. | Configurable per-role limits, with distinct loan and reservation counts; no numeric values selected and recommendation unapproved. |
| D15 | No manager reports/exports; a defined set of summary reports; configurable reports; or reports deferred to a later phase. | Defer reports and exports until course/user needs are specified; unapproved. |
| D16 | Backups owned by a named library operator, a course/project maintainer, or a designated IT operator; stored locally or in separately controlled storage; manual or scheduled creation; define retention/rotation and restore-rehearsal frequency. | Assign a named operator and separately protected storage, then define schedule and retention; unapproved. |
| D17 | Apply an instructor-provided rubric; use course-wide criteria; or treat grading criteria as not applicable. | Follow the instructor/course rubric if one is provided; otherwise record as not applicable rather than inventing grading rules. Unapproved. |
| D18 | No automatic enforcement; warning only; block outside configured hours; if enforcement is selected, configure operating hours, holiday calendar, and time zone. The approved operational practice remains that employees process requests during working hours. | Warning-only until hours, holiday calendar, time zone, and consequences are explicitly approved; unapproved. |

## Decision status rule

All underlying policies in this Step 02 register remain **Open**. D01–D18
retain their existing authoritative status. D19, D20, D23–D25, D30–D34,
D36–D38, and D40 are independent open questions. D21, D22, D26–D29, D35,
D39, and D41 are historical IDs merged into the parent decision named in
their row; they are not separate active questions. Every recommendation is
unapproved and does not change status. The authoritative history remains in
`docs/open-decisions.md`.
