# ADR-0004: Future REST, Security, and Web Architecture

- **Status:** Conceptual proposal — pending explicit user approval; no future stack is selected.
- **Workflow:** Step 04 — architecture and technology decisions.
- **Related open decisions:** D06 (REST stack), D37 (account security); D01 also constrains Java compatibility.
- **Scope:** Future-facing evaluation only. Project Phase 03 (REST) and Phase 04 (web) are not authorized by this document.

## Context

Approved project direction places a REST API after the console application
and a web interface after the API, both over the shared core (FR-020–FR-022,
R12). The present work does not implement those phases. Authentication,
account recovery, lockout, and session-security expectations remain open
(D37); framework selection cannot define those policies.

## Options

- **REST framework:** Spring Boot; a smaller framework such as Javalin; a
  Jakarta REST implementation; or defer selection until the API phase and
  course constraints are known.
- **Security:** framework-supported authentication/authorization after D37
  is decided; a course-provided identity mechanism; or defer implementation
  until security requirements are approved. No specific password, session,
  token, or recovery behavior is selected here.
- **Web client:** semantic HTML, CSS, and browser JavaScript; server-rendered
  pages; or a client-side framework if approved requirements justify one.

## Proposed decision — UNAPPROVED

For evaluation in the future API phase, use Spring Boot as the leading REST
candidate because its official documentation publishes explicit Java and
build-tool requirements; compare its footprint and course fit with a lighter
framework before selection. Consider Spring Security only after D37 and the
permission model are approved. For the initial web interface, prefer
standards-based HTML, CSS, and browser JavaScript or server-rendered pages;
add a client-side framework only if approved requirements warrant its
complexity. All components remain future concepts; no framework or security
behavior is approved by this proposal.

## Rationale and trade-offs

Spring Boot offers an integrated application stack but adds conventions and
dependencies; a lighter REST framework may reduce framework surface while
requiring more decisions about integration. On the check date, Spring Boot
4.1.1's official system-requirements page states Java 17 minimum through
Java 26 and Maven 3.6.3 or later (or listed Gradle versions). That is a
version-specific compatibility snapshot, not a selection of Spring Boot 4.1.1
or proof that the future approved Java/toolchain will match it. Recheck when
the API phase is authorized.

Browser standards avoid committing to a client framework before UI needs are
known. A framework can improve structure for a larger interactive client but
adds a separate toolchain and maintenance surface. Security policy is
especially sensitive to role grants and identity requirements: D30 and D37
must remain open until explicitly resolved. A framework's built-in security
features do not themselves decide who may do what.

## Compatibility evidence (checked 2026-10-21)

- [Spring Boot system requirements](https://docs.spring.io/spring-boot/system-requirements.html) — current documented Java and build-tool ranges. The page is versioned/current and must be rechecked when D06 is decided.
- [WHATWG HTML Living Standard](https://html.spec.whatwg.org/multipage/) — current HTML platform specification. It does not establish browser support targets for this project.
- [W3C CSS specifications](https://www.w3.org/Style/CSS/) — standards and specification status. No browser compatibility target is approved.

## Consequences if approved

The eventual API and web interface should call the same application use cases
as the console rather than duplicate library rules. Security requirements,
permission grants, session handling, browser support, and deployment remain
separate decisions. No REST endpoint, login flow, web page, dependency, or
security configuration is delivered in Workflow Step 04.

## Approval boundary

D06 and D37 remain **Open**. Spring Boot, Spring Security, and the web-client
approach are unapproved recommendations; they do not authorize work in
project Phases 03 or 04.
