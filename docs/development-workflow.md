# Development Workflow

This page describes how work proceeds in every phase. The numbered working
rules referenced here are defined in [../AGENTS.md](../AGENTS.md).

Numbered prompt or workflow steps are separate from project delivery phases:
for example, requirements-engineering Step 02 does not change project Phase 02,
which is the planned console application.

`AGENTS.md` is the repository-level instruction source for Codex and other
contributors. Keep project requirements and decisions in the project
documentation; do not create a second, conflicting instruction system.

## Phase Protocol

Every phase follows the same six steps:

1. **Inspect** — read the repository state before anything else: `git status`,
   branch, remotes, existing files, README, and documentation (R01, R02).
2. **Plan** — write a plan: files to create or change, their purpose,
   alternatives for technical decisions (R11), and open questions.
3. **Approve** — the user approves the plan before implementation. No work
   outside the approved scope (R14).
4. **Implement** — make exactly the approved changes; preserve all
   pre-existing user content (R03).
5. **Verify** — check the result honestly: what was checked, what was not run
   (e.g., "no tests exist yet — none were run"). Never claim unrun work.
6. **Report** — list every created or modified file with its purpose, list the
   unresolved decisions, and state clearly whether anything was committed or
   pushed (nothing is — R06).

## Committing

- Only the user commits and pushes (R06). Agents leave changes in the working
  tree for review.
- Before committing, review `git status` and `git diff`; follow
  [git-and-commits.md](git-and-commits.md) for message style and the
  never-commit list.

## Handling Open Decisions

When work needs a rule or choice that is not yet decided:

1. Stop — do not guess (R08).
2. Record the question in [open-decisions.md](open-decisions.md) if it is not
   already there.
3. Continue with the parts that are decidable, or present the decision to the
   user.

## Working with Agents

- Agents read `AGENTS.md` first and follow the numbered rules (R01–R14).
- Agents propose; the user decides: plans and scopes are approved by the user.
- Each workflow step adds a Persian learning note under
  `learning/fa/step-NN.md` (R10). Workflow-step numbering is separate from
  project-phase numbering; the filename does not change the project's phase
  mapping.
- Documentation is updated in the same phase that changes how the project works.
