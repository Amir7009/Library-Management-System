# Git and Commit Expectations

## Current Repository State (checked 2026-10-14, Phase 00)

- Branch `main`, tracking `origin/main` at
  `https://github.com/Amir7009/Library-Management-System.git`
- One commit (`a90a26d`) containing the initial `README.md`

## Commit Expectations

- **The user commits.** Nobody commits or pushes automatically (R06).
- **Small, focused commits** — one logical change per commit.
- **English commit messages** (R09), imperative mood, e.g.
  `docs: add open-decisions register`.
- **Suggested prefixes** (a convention, not a hard rule):
  `docs:` documentation · `feat:` new functionality · `fix:` bug fixes ·
  `chore:` maintenance and tooling · `refactor:` restructuring without
  behavior change.
  - *Alternative considered:* free-form messages. Prefixes were chosen because
    the project will grow across many phases and a scannable history makes
    review cheaper. This convention can be amended here by decision.

## Never Commit (R07)

- Passwords, API keys, tokens, database credentials
- Personal data
- Backup files (see the backup patterns in `.gitignore`)
- IDE workspace files (`.idea/` is ignored)

## What `.gitignore` Can and Cannot Do

- `.gitignore` prevents **untracked** files from being added to Git.
- It has **no effect on files that are already tracked**: adding a secret's
  path to `.gitignore` does not protect a secret that was already committed.
- If a secret is ever committed: remove the file, **rotate the credential**
  (assume it is compromised), and clean history if the repository is shared
  (e.g., `git filter-repo` or BFG) — then prevent recurrence via `.gitignore`.
- Check before committing: `git status`, and for a specific path
  `git check-ignore -v <path>` to see whether and why it is ignored.

## SQL Files

- **SQL source and migration files are version-controlled.** There is
  deliberately no blanket `*.sql` rule in `.gitignore`.
- Only generated backup artifacts are ignored: `*.sql.gz`, `*.backup.sql`,
  plus `*.bak`, `*.backup`, `*.dump`. If a future migration file ever fails to
  show up in `git status`, check `git check-ignore -v <path>` and fix the
  pattern — do not make `git add -f` a habit.
