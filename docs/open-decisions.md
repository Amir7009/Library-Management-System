# Open Decisions

Decisions listed here are deliberately unresolved. Working rules R08 and R14
forbid inventing them silently: a decision is resolved only when it is
explicitly authorized, and then this file is updated (status, date, rationale).

Rows are never deleted — a resolved decision stays here, marked resolved with
a date, so the project keeps its decision history.

## D01 — Target Java Version

- **Status:** Open (recorded 2026-10-14, Phase 00)
- **Context:** The IntelliJ configuration (`.idea/misc.xml`) currently
  indicates JDK 21 (language level `JDK_21`). That is IDE configuration
  created when the project was opened — **not** a ratified project decision.
- **Why it matters:** Language features, dependency and library versions, and
  later tooling choices all depend on it.
- **Phase 00 stance:** The target version and every file under `.idea/` remain
  untouched in this phase.
- **Resolution needed from:** user / course requirements.

## Other Open Decisions

| # | Decision | Status | Why it matters | Notes |
|---|----------|--------|----------------|-------|
| D02 | Build tool: Maven vs Gradle vs plain IntelliJ `out/` | Open | Determines build/test commands, dependency management, repo layout | Repository currently has no build files; `.idea/misc.xml` points output to `out/` |
| D03 | Persistence: DB engine; JDBC vs ORM; file-based storage for the console phase | Open | Core design for loans, reservations, fines, backups | Depends on course requirements |
| D04 | Package and module layout of the application core | Open | Affects every later source file | Fixed constraint: shared logic must not depend on the console interface |
| D05 | Test framework (JUnit 5 is the likely candidate) | Open | Needed before the first unit tests exist | No tests exist yet; none were run in Phase 00 |
| D06 | REST stack for the API phase (e.g., Spring Boot vs a lightweight framework) | Open | Design of the API layer | Later phase |
| D07 | Language of the console user interface (English / Persian / both) | Open | User-facing strings and input handling | Later phase |
| D08 | Branching strategy: single `main` vs feature branches | Open | Day-to-day workflow and review discipline | Currently only `main` exists |
| D09 | Fine calculation rules | Open | Business rule — must not be invented (R08) | Requires course specification |
| D10 | Renewal eligibility conditions and limits | Open | Business rule — must not be invented (R08) | Requires course specification |
| D11 | Waiting-queue and reservation policy | Open | Business rule — must not be invented (R08) | Requires course specification |
| D12 | Guest borrowing privileges | Open | Business rule — must not be invented (R08) | Requires course specification |
| D13 | Loan durations and due-date rules | Open | Business rule — must not be invented (R08) | Requires course specification |
| D14 | Concurrent borrowing/reservation limits per member | Open | Shapes loan-approval logic and member-facing views | Surfaced in Phase 01 (`docs/project/`); must not be invented (R08); related to D10, D13 |
| D15 | Manager reports and exports (which summaries, if any) | Open | Decides whether reporting is part of the console version at all | Surfaced in Phase 01; until decided, no reports are built |
| D16 | Backup ownership and storage location | Open | A backup nobody owns is not a backup — operational safety | Surfaced in Phase 01; interacts with SC8 (rehearsed restore) in `docs/project/success-criteria.md` |
| D17 | Academic grading criteria, if applicable | Open | Aligns documentation and delivery with how the project is evaluated | Surfaced in Phase 01; affects process priorities, not application behavior |
| D18 | Whether the application must automatically enforce working hours, holidays, and time-zone rules for circulation actions | Open | Decides whether time-rule logic is built at all; any values would also need course specification | The *operational practice* — employees process borrowing requests during working hours — is approved as a high-level requirement (2026-10-15); this decision covers only automatic enforcement by the software. Surfaced in Phase 01 |
| D19 | Book-category taxonomy, hierarchy, maintenance, and title association cardinality | Open | Defines how catalogue titles are classified, categories managed, and categories associated with titles | Includes former D41; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D20 | Whether and how employees may borrow as library members | Open | Affects account identity and separation of staff/member permissions | Surfaced during requirements-workflow Step 02; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D21 | Merged into D11: waiting-list enrollment trigger | Merged into D11 (Open) | Queue enrollment remains unresolved under D11 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D22 | Merged into D11: reservation activation, duration, and expiration | Merged into D11 (Open) | Reservation policy remains unresolved under D11 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D23 | Handling of unprocessed, rejected, or pending circulation requests | Open | Determines whether requests remain pending, expire, or are withdrawn/escalated | Related to D10–D11; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D24 | Whether returns require employee review or are accepted automatically | Open | Affects return state transitions and staff workload | Surfaced during requirements-workflow Step 02; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D25 | Effective return date: request submission, employee approval, or recorded receipt time | Open | Affects availability, overdue state, and fines | Related to D09; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D26 | Merged into D13: loan-period and due-date configuration | Merged into D13 (Open) | Loan-period and due-date policy remains unresolved under D13 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D27 | Merged into D10: renewal authority, limits, and configuration | Merged into D10 (Open) | Renewal policy remains unresolved under D10 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D28 | Merged into D18: schedule inputs if automatic enforcement is approved | Merged into D18 (Open) | Conditional schedule inputs remain unresolved under D18 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D29 | Merged into D09: fine calculation and configuration | Merged into D09 (Open) | Fine policy remains unresolved under D09 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D30 | Role-by-action permission grants, including guest access | Open | Protects personal data and defines staff/member capabilities | Related to D12 and D20; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D31 | Catalogue search fields, matching, normalization, and result ordering | Open | Determines search behavior and discoverability | Surfaced during requirements-workflow Step 02; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D32 | Personal-dashboard contents and visibility by role | Open | Determines which account, circulation, and history information users see | Related to D30; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D33 | In-app notification events, read state, and retention | Open | Determines which events notify users and how notifications are managed | Related to scope assumption A4; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D34 | Audit-event coverage, access, and retention | Open | Determines accountability history and access to personal/audit data | Related to D30; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D35 | Merged into D16: backup schedule, storage, retention, and restore rehearsal | Merged into D16 (Open) | Backup operations remain unresolved under D16 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D36 | Response-time and expected data-volume targets | Open | Defines measurable performance expectations | Related to assumption A5; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D37 | Account authentication, recovery, lockout, and session-security expectations | Open | Determines account protection and recovery behavior | Must respect D01–D05 and course constraints; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D38 | Availability, recovery-point, and recovery-time targets | Open | Defines acceptable service interruption and data-loss windows | Related to D16 and SC8; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D39 | Merged into D11: queue scope, allocation, and ineligible entries | Merged into D11 (Open) | Queue allocation policy remains unresolved under D11 | FIFO ordering for eligible requests is user-directed; historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D40 | Tie-breaking for requests with equal recorded submission timestamps | Open | Makes FIFO ordering deterministic when timestamps match | Surfaced during requirements-workflow Step 02; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |
| D41 | Merged into D19: category association cardinality | Merged into D19 (Open) | Category assignment remains unresolved under D19 | Historical ID retained; options and unapproved recommendation in [requirements/open-decisions.md](requirements/open-decisions.md) |

## How to Resolve a Decision

Update the row (or D01 section) with: the chosen option, the date, who decided,
and the rationale — then reflect the outcome in the affected documentation.
Alternatives considered should stay recorded (R11).
