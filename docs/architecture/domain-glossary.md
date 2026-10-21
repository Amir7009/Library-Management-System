# Domain Glossary — Workflow Step 03

> Definitions describe the requirements baseline. They do not resolve
> policies listed in [the decision register](../open-decisions.md).

| Term | Domain meaning | Distinction or open boundary |
|---|---|---|
| **Catalog** | Records describing books/titles and their categories. | Separate from physical copies and circulation activity. |
| **Book title** | A catalog entry describing a book. | One title may have physical copies; category cardinality is open (D19; merged historical D41). |
| **Category** | A classification associated with a book title. | Taxonomy, hierarchy, permissions, and assignment cardinality remain open (D19). |
| **Physical copy** | One individually identifiable physical item associated with one title. | It is the item borrowed in a loan; no copy allocation rule is inferred. |
| **User account** | A system account associated with a person using the library system. | The named roles are manager, employee, student, and guest; role grants and staff membership remain open (D12, D20, D30). |
| **Role** | One of the named categories of user recognized by the requirements. | A role name alone grants no permission. Whether users may hold multiple roles is unspecified. |
| **Borrow request** | A recorded request to borrow a title or eligible copy. | Approval/rejection is recorded by an employee; a reservation is not automatically implied. Pending policy is open (D11, D23). |
| **Reservation** | A record representing a hold/reservation associated with a title. | Enrollment, activation, allocation, and expiry are open (D11; merged historical D21, D22, D39). |
| **Waiting queue** | An ordered set of eligible requests associated with demand for a title. | FIFO applies among eligible requests in the same applicable queue; membership, allocation, and equal-time ties remain open (D11, D40). |
| **Loan** | A recorded active borrowing of a physical copy by a borrower, with a due date. | FR-014 requires a loan record for an approved borrow request; creation timing and due-date policy are not specified (D13). |
| **Return request** | A request to return a copy associated with an active loan. | Submission is distinct from acceptance/effective return; review policy and effective date are open (D24, D25). |
| **Renewal request** | A request concerning extension of an active loan. | It is distinct from the loan and from an approved extension; eligibility, limits, authority, and effect are open (D10, D13, D14). |
| **Overdue** | A loan condition identified using approved due-date and return-date rules. | No duration, calendar, grace period, or effective return date is selected (D09, D13, D25). |
| **Fine** | A recordable monetary consequence associated with a late return. | Recording is supported; amount, formula, currency, and related policy inputs remain open (D09, D25). Payment collection is out of scope under A2. |
| **Notification** | An in-app message made available to its intended user. | Event selection, read state, and retention are open (D33). |
| **Audit event** | A record of a significant action for accountability. | Actor, target, event coverage, access, and retention details are not fully specified (D30, D34). |
| **Policy input** | A conceptual value or rule affecting outcomes such as due dates, fines, renewal, or queue behavior. | No persistent policy/configuration entity or schema is approved. |

## Distinguishing the circulation concepts

- A **borrow request** asks for permission to borrow. It can be approved or
  rejected; pending-request behavior remains open.
- A **reservation** represents demand/hold behavior associated with a title.
  It is not another name for a borrow request or loan, and the requirements do
  not say every borrow request creates one.
- A **loan** records an active borrowing of a copy by a person and has a due
  date. FR-014 requires a loan record for an approved borrow request, without
  specifying immediate creation or the intervening allocation process.
