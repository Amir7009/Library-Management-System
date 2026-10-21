# ADR-0002: Database and Persistence

- **Status:** Proposed — pending explicit user approval; no persistence option is selected.
- **Workflow:** Step 04 — architecture and technology decisions.
- **Related open decisions:** D03 (database, JDBC/ORM, and console persistence); D01/D02 constrain compatibility.
- **Scope:** Conceptual proposal only; no database, schema, driver, or dependency is added.

## Context

Approved requirements include related catalog and circulation records,
requests, loans, audit history, and backup/recovery. The console phase still
needs to be evaluated for setup burden and the expected local environment.
D03 explicitly leaves the database engine, JDBC versus ORM, and file-based
console storage open. No choice may change the domain model or settle library
policies.

## Options

- **Database:** PostgreSQL; a file-based relational database such as SQLite;
  another course-required relational database; or defer selection until the
  deployment/evaluation environment is known.
- **Data access:** direct JDBC; an ORM; or another course-mandated persistence
  abstraction.
- **Schema evolution:** reviewed SQL migrations managed manually; a migration
  tool such as Flyway; or a course-required mechanism.

## Proposed decision — UNAPPROVED

Recommend a relational database, with PostgreSQL as the leading shared
environment candidate, direct JDBC for an initially small core, and
version-controlled SQL migrations. Evaluate Flyway as a migration tool only
after confirming the selected Java and database versions. Keep SQLite or
another local database as a viable alternative if the course requires a
self-contained, server-free console setup. This proposal does not resolve D03.

## Rationale and trade-offs

The domain contains linked records and needs traceable updates; relational
constraints and transactions are a reasonable fit, but this is a technical
recommendation rather than a requirement. PostgreSQL's official versioning
policy gives each major release five years of support. On the check date,
PostgreSQL 18 was listed as supported through November 2030. That supports
considering a current major release; it does not establish that PostgreSQL is
available or desired in the course environment. A server-based database adds
installation, configuration, backup, and operations work compared with a
file-based option.

Direct JDBC exposes SQL and transaction boundaries with fewer abstractions but
requires explicit mapping and careful resource handling. An ORM can reduce
repetitive mapping while introducing framework concepts and configuration.
Manual SQL migrations keep the mechanism simple but require a disciplined
record of applied changes. Flyway can track and apply migrations, but it adds
a dependency and database-specific compatibility must be confirmed. Redgate's
current Java API documentation states a JDK 17+ baseline and notes that Flyway
14 requires Java 21; the exact edition, artifact coordinates, database driver,
and release compatibility still require checking at adoption.

## Compatibility evidence (checked 2026-10-21)

- [PostgreSQL Versioning Policy](https://www.postgresql.org/support/versioning/) — support duration and current supported major versions. Recheck the release table at approval time.
- [pgJDBC download and compatibility information](https://jdbc.postgresql.org/download/) — driver/JDBC compatibility details. Select a matching driver only after Java and PostgreSQL versions are approved.
- [Flyway Java API documentation](https://documentation.red-gate.com/flyway/reference/usage/api-java) — stated Java baseline and version note. Flyway's Java requirements vary by release; verify the exact release and edition before selection.
- [Flyway supported database versions](https://documentation.red-gate.com/fd/supported-database-versions-143754067.html) — supported database list, which may vary by edition/capability.

## Consequences if approved

The persistence adapter can implement interfaces owned by the application
core (see ADR-0003). Schema changes should be reviewed and repeatable. Backup
ownership, schedule, location, retention, and recovery targets remain open
(D16, D35, D38); choosing a database or migration tool does not answer them.

## Approval boundary

D03 remains **Open**. PostgreSQL, JDBC, Flyway, and SQL migrations are
unapproved recommendations; no schema, driver, migration, or persistence
implementation is authorized here. Migration-tool selection is not currently
a separately numbered open decision; it is included here as a subordinate
technical option to confirm alongside D03, not as a new approved decision.
