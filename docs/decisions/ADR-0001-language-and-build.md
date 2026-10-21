# ADR-0001: Language, Build, and Test Tooling

- **Status:** Proposed — pending explicit user approval; no tool is selected.
- **Workflow:** Step 04 — architecture and technology decisions.
- **Related open decisions:** D01 (Java), D02 (build), D05 (test framework).
- **Scope:** Documentation proposal only; no build files or dependencies are added.

## Context

The project is a Java library system whose first runnable application is the
console (project Phase 02). The repository currently has no application source
or build system. IntelliJ's JDK 21 setting is environment configuration, not
an approved project choice. A reproducible build and test command should be
available across supported developer environments without coupling the core
to the console.

## Options

- **Java target:** select a currently supported LTS after confirming course,
  IDE, and contributor constraints; or retain a lower supported baseline if
  those constraints require it.
- **Build:** Maven with its Wrapper; Gradle with its Wrapper; or plain IDE
  compilation/output directories.
- **Tests:** JUnit Jupiter; another framework required by the course; or defer
  the framework until test expectations are known.

## Proposed decision — UNAPPROVED

Recommend Java 25 LTS as the candidate target, Maven Wrapper for reproducible
build invocation, and JUnit Jupiter for automated tests. Do not pin exact
plugin or library versions in this proposal. Confirm IDE/course support and
the selected versions at approval and implementation time. This recommendation
does not resolve D01, D02, or D05.

## Rationale and trade-offs

Oracle lists Java 25 as an LTS release; it also lists Java 21 as LTS, while its
roadmap says Oracle JDK 21 updates after September 2026 are planned to move
under the Oracle Technology Network license. This describes Oracle's release
and licensing terms, not every OpenJDK distributor's support terms. Java 25
is therefore a candidate, not an assumption about the required course JDK.
Apache's Wrapper documentation describes using the Maven version configured
for the project and lists Windows support; this favors repeatable commands,
but still requires a compatible JDK and access to obtain the configured Maven
distribution. JUnit's current guide describes Jupiter as its programming and
extension model and says JUnit 6 requires Java 17 or higher at runtime; exact
test-engine and build-plugin compatibility must be checked when versions are
selected.

Alternatives remain credible: Gradle also provides a wrapper; plain IDE
builds reduce setup but make repeatable command-line verification harder; and
the course may require another JDK or test framework. A newer LTS target may
also be unsupported by an educational environment even when the cited tools
support it.

## Compatibility evidence (checked 2026-10-21)

- [Oracle Java SE Support Roadmap](https://www.oracle.com/java/technologies/java-se-support-roadmap.html) — LTS releases and Oracle JDK update/licensing information. Oracle's roadmap is not a universal support or licensing statement for other JDK vendors.
- [Apache Maven Wrapper](https://maven.apache.org/tools/wrapper/index.html) — configured Maven distribution and supported operating systems, including Windows.
- [JUnit User Guide](https://docs.junit.org/current/user-guide/) — current JUnit modules and Java runtime requirement. The `current` page can change; verify the exact JUnit release at adoption time.

## Consequences if approved

Build/test commands and CI can use the selected wrapper and target. Developers
must have a compatible JDK. The exact Java, Maven, JUnit, compiler-plugin,
and test-plugin versions must be pinned together only after approval and a
fresh compatibility check. No such configuration is part of this ADR.

## Approval boundary

D01, D02, and D05 remain **Open**. This proposal does not approve a Java
version, build tool, test framework, or dependencies. Course requirements and
the user's explicit decision take precedence.
