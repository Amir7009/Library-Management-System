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

## How to Resolve a Decision

Update the row (or D01 section) with: the chosen option, the date, who decided,
and the rationale — then reflect the outcome in the affected documentation.
Alternatives considered should stay recorded (R11).
