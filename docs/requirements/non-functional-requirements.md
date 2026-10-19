# Quality Requirements — Requirements Workflow Step 02

> Status: Documentation baseline only. These requirements do not authorize
> application implementation or select unresolved technical decisions.

Quality requirements have unique `NFR-NNN` identifiers. A measurable threshold
that has not been approved is recorded as an open question rather than guessed.

| ID | Quality requirement | Verification approach / open dependency |
|---|---|---|
| NFR-001 | The system shall preserve the distinction between catalogue titles and separately identifiable physical copies in all supported views and operations. | Inspect records and acceptance scenarios for title/copy separation. |
| NFR-002 | A rejected or invalid state-changing request shall leave the prior valid record state intact and provide a user-visible explanation. | Exercise invalid transitions after workflow states are defined. |
| NFR-003 | Each accepted request, employee decision, loan, return, renewal, and fine record shall be traceable to its related records and timestamps. | Review linked records and audit entries; exact event policy D34 remains open. |
| NFR-004 | The same persisted state, explicit timestamps, and approved policy configuration shall produce the same search, availability, queue-order, and due-date outputs. | Repeat scenarios against the same data; policy inputs remain open. |
| NFR-005 | The system shall prevent a user from viewing or changing information beyond the user's approved permissions. | Permission tests cannot be finalized until D30 and D32 are decided. |
| NFR-006 | The system shall preserve data across application restarts using the persistence approach selected under D03. | Restart and compare saved records after D03 is decided. |
| NFR-007 | Backup and restore procedures shall be documented and a restore shall be rehearsed, consistent with success criterion SC8. | Follow the documented procedure; ownership, retention, and recovery targets remain open (D16, D38). |
| NFR-010 | Once the console language is selected under D07, the console shall present user-facing text consistently in that approved language. | Compare console labels and messages against the approved language selection; D07 remains Open. |
| NFR-012 | The system's performance and recovery behavior shall be verifiable against any targets approved for them. | Measure representative response times and restoration outcomes externally, then compare them with approved targets; performance/scale D36 and recovery targets D38 remain Open. |

## Technical constraints

Technical constraints have unique `TC-NNN` identifiers. These are boundaries
from the approved project direction or the user's Step 02 prompt, not choices
of language version, build tool, persistence, or framework.

| ID | Constraint | Source / verification |
|---|---|---|
| TC-001 | Requirements-workflow Step 02 defines requirements and business rules only; it shall not deliver application source code. This does not change project Phase 02, the console application. | User's explicit task boundary; inspect changes |
| TC-002 | The initial interface is console-first; the shared application behavior must not depend on console input/output. | Approved project direction, R12; architecture review |
| TC-003 | The planned REST API and web interface are future front-ends over the shared core, not deliverables of this baseline. | Approved delivery direction |
| TC-004 | The application shall remain a simple modular application, not a microservices system. | R12 |
| TC-005 | The library application shall not include AI features. | R13 |
| TC-006 | Java version, build tool, persistence technology, package layout, test framework, and REST stack remain unselected until D01–D06 are resolved. | Existing decisions D01–D06 remain Open |

The shared-core and future-interface boundaries are recorded only once as
technical constraints TC-002 and TC-003. The modular-architecture and no-AI
boundaries are recorded only once as TC-004 and TC-005.

## Quality questions requiring decisions

- D36: response-time and data-volume targets.
- D37: authentication, session, and account-security expectations.
- D38: availability, recovery-point, and recovery-time targets.
- D07 remains the open decision for console language. Accessibility and
  localization expectations beyond that have not been specified.
