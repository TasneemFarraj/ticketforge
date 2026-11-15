# Contributing to TicketForge

How Tala and Tasneem work together on this repo. Read it once, follow it always.

## 1. Workflow

1. Pick a task from the Notion Tasks board and move it to **In Progress**.
2. Start from an updated `main` and create a branch:
   ```
   git switch main
   git pull
   git switch -c feat/TF-12-short-name
   ```
3. Commit small steps on your branch (messy messages are OK here).
4. Before requesting review, rebase on the latest `main`:
   ```
   git fetch
   git rebase origin/main
   git push --force-with-lease
   ```
5. Open a PR, fill in the template, and request review from the other person.
   Move the Notion task to **In Review** and add the PR link.
6. Reviewer approves → the **author** clicks **Squash and merge** → task to **Done**.
7. Next task = a **new branch** from updated `main`. Never reuse a merged branch.

## 2. Branch names

`type/TF-<number>-short-name`

- `feat/TF-12-cursor-pagination`
- `fix/TF-20-double-booking`
- `chore/TF-1-repo-workflow`

## 3. Commit messages and PR titles

[Conventional Commits](https://www.conventionalcommits.org): `type(scope): description`

| Type       | Use for                              |
| ---------- | ------------------------------------ |
| `feat`     | a new feature                        |
| `fix`      | a bug fix                            |
| `chore`    | setup, tooling, config               |
| `docs`     | documentation only                   |
| `test`     | adding or fixing tests               |
| `refactor` | code change with no behaviour change |

- **scope** = the area of the code: `events`, `orders`, `auth`, `repo`…
- Lowercase, imperative ("add", not "added"), no full stop.
- ⚠️ The **PR title must follow this format**: with squash, it becomes the commit on `main`.

## 4. Merge strategy: squash only

We are learning, so our branches will have messy commits ("fix typo", "try again").
Squash combines **all** commits of a PR into **one** commit on `main`: no code is lost,
only the small messages disappear (they stay visible in the PR).
This keeps `main` clean and readable: **one task = one PR = one commit**, and the PR title becomes its message.

## 5. Rules on `main` (enforced by a GitHub ruleset)

- No direct pushes. GitHub rejects them with `GH013`.
- A PR needs **1 approval**. New commits dismiss old approvals, so rebase **before** requesting review.
- All review conversations must be resolved before merging.
- No force pushes to `main`, and `main` can't be deleted.

## 6. Definition of Done

See the checklist in the PR template (`.github/pull_request_template.md`).
