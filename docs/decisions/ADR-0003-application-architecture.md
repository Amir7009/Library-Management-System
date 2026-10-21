# ADR-0003: Application Architecture and Core Boundaries

- **Status:** Proposed — pending explicit user approval; exact layout is not selected.
- **Workflow:** Step 04 — architecture and technology decisions.
- **Related open decisions:** D04 (package/module layout); D01/D02 constrain language and build choices.
- **Scope:** Conceptual boundaries only; no source code or module configuration is added.

## Context

The approved direction requires a console-first delivery, shared behavior
independent of the console, future REST and web front-ends over that shared
behavior, and a simple modular application rather than microservices
(FR-020–FR-022, R12). This boundary must also keep unresolved domain policies
out of the technology proposal.

## Options

- One Java application organized into packages; a single deployable with
  enforced Java Platform Module System modules; or a multi-module build.
- A core-owned persistence interface with an adapter; direct persistence
  access from use cases; or another course-required structure.
- JDK `java.util.logging`; SLF4J with a provider such as Logback; or defer
  logging selection until project needs are clearer.

## Proposed decision — UNAPPROVED

Recommend one simple modular application, initially organized into packages
in one build/deployment: domain and application use cases form the shared
core; console and persistence are adapters at its boundary. Keep dependencies
pointing inward: adapters call core-owned interfaces, while core code does
not import console, database-driver, or web-framework types. Add REST and web
adapters only in their authorized project phases. For initial technical logs,
consider the JDK logging API to avoid an extra dependency; revisit a facade
such as SLF4J if multiple logging implementations or operational needs justify
it. This is a proposed shape, not a selection under D04.

## Rationale and trade-offs

The proposed boundary directly supports the approved requirement that shared
application behavior work independently of the console. A package-level
modular monolith is simpler to learn and run than multiple deployables or an
early multi-module structure. Its discipline depends on review unless module
boundaries are enforced by tooling. Java modules or multiple build modules
could strengthen isolation later, at the cost of extra configuration.

The JDK API is part of the Java platform and provides loggers, records,
handlers, and destinations including console and files. That may be enough
for the initial console phase. A logging facade can make provider changes
more flexible but brings dependency and configuration choices. Neither
option is a user-facing audit-history mechanism; application audit events
remain separate domain records governed by FR-018 and D34.

## Compatibility evidence (checked 2026-10-21)

- [Java SE 25 `java.logging` module documentation](https://docs.oracle.com/en/java/javase/25/docs/api/java.logging/module-summary.html) — the Java Logging API is provided by the JDK module. This source describes Java 25; confirm against the ultimately approved target version.
- [Java SE 25 `java.util.logging` package documentation](https://docs.oracle.com/en/java/javase/25/docs/api/java.logging/java/util/logging/package-summary.html) — logging facilities and handler capabilities.

## Consequences if approved

Use-case and domain behavior can be tested independently from console I/O.
The console and future front-ends translate their inputs and outputs at the
boundary. Persistence can be replaced without moving business rules into a
database adapter. Exact packages, module boundaries, dependency injection,
logging configuration, and test conventions still require a decision and
implementation review.

## Approval boundary

D04 remains **Open**. The suggested boundaries and logging option are
unapproved; they do not establish package names, modules, frameworks, or
library dependencies.
