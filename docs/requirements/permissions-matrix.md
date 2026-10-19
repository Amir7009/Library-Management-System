# Permissions Matrix — Requirements Workflow Step 02

> Role names are approved; role privileges are not. This matrix exposes the
> undecided grants and does not grant permissions by implication.

Legend:

- **Required action** — explicitly required by the Step 02 prompt, subject
  to the application's eventual access policy.
- **Open** — no grant is specified; do not implement a grant until decided.
- **N/A** — not a role-based system action.

| Capability | Manager | Employee | Student | Guest |
|---|---|---|---|---|
| Search catalogue / view availability | Open (D30) | Open (D30) | Open (D30) | Open (D12, D30) |
| Create or edit categories, titles, and copies | Open (D30) | Open (D30) | Open (D30) | Open (D12, D30) |
| Create or manage user accounts | Open (D30) | Open (D30) | Open (D30) | Open (D12, D30) |
| Submit borrow / return / renewal request | Open (D12, D30) | Open, including staff-as-member policy D20 | Open (D30) | Open (D12, D30) |
| Review and approve/reject borrow requests | Open (D30) | Required action; exact permission model D30 | Open (D30) | Open (D12, D30) |
| Review return requests | Open (D30) | Open (D24, D30) | Open (D30) | Open (D12, D30) |
| Review renewal requests | Open (D10, D30) | Open (D10, D30) | Open (D30) | Open (D12, D30) |
| View personal dashboard and notifications | Open (D30, D32) | Open (D30, D32) | Open (D30, D32) | Open (D12, D30, D32) |
| View audit history / reports | Open (D15, D30, D34) | Open (D30, D34) | Open (D30, D34) | Open (D12, D30, D34) |
| Produce or restore backups | Open (D16, D30) | Open (D16, D30) | Open (D30) | Open (D12, D30) |

The employee review capability is required by the user's prompt. The separate
approved operational requirement says employees process borrowing requests
during working hours; automatic enforcement of hours, holidays, or time zones
remains open under D18. The matrix does not decide which other role grants,
including manager oversight, should exist.

## Unapproved recommendation

For discussion only, D30 recommends explicit role-based grants, with users
restricted to their own member records and employees receiving only the
circulation-review capabilities assigned to them. A manager grant set should
be defined separately. This recommendation is **unapproved** and must not be
treated as a permission rule.
