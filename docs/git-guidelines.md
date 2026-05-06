# Kidlat CivicLabs — Git Workflow Guidelines

This document describes the **Git workflow used in this repository**. Following these guidelines helps maintain a **clean commit history**, ensures **safe collaboration**, and keeps the Kidlat CivicLabs codebase organized.

---

## Branch Structure

This project uses the following branch structure:

```
main       → production-ready code (live site)
staging    → integration and testing branch
sandbox    → active development branch
feature/*  → temporary branches for new features
fix/*      → temporary branches for bug fixes
```

### Branch Roles

| Branch | Purpose |
|---|---|
| **main** | Stable, production-ready code — what's live on kidlatciviclabs.org |
| **staging** | Integration and pre-production testing |
| **sandbox** | Active development and experimentation |
| **feature/\*** | New features or page additions |
| **fix/\*** | Bug fixes and patches |

> ⚠️ **Never commit directly to `main` or `staging`.** All changes go through Pull Requests.

---

## Development Workflow Overview

```
sandbox → feature/* or fix/* → PR → staging → PR → main
```

All development is done in **feature branches** or **fix branches**, then merged into `sandbox` via **Pull Requests (PRs)**. Tested code is promoted from `sandbox` → `staging` → `main`.

---

## Step 1 — Update Your Base Branch

Before starting any work, make sure your local branch is up to date.

```bash
git checkout sandbox
git pull origin sandbox
```

---

## Step 2 — Create a Branch

Create a new branch depending on the type of work.

### For new features

```bash
git checkout -b feature/<feature-name>
```

Examples:

```bash
git checkout -b feature/projects-page
git checkout -b feature/contact-form
git checkout -b feature/research-section
```

### For bug fixes

```bash
git checkout -b fix/<bug-name>
```

Examples:

```bash
git checkout -b fix/contact-form-validation
git checkout -b fix/navbar-mobile-layout
git checkout -b fix/resend-api-error
```

---

## Step 3 — Work and Commit Changes

Stage and commit your changes regularly with clear, descriptive messages.

```bash
git add .
git commit -m "feat: add projects showcase page with case study cards"
```

---

## Commit Message Convention

We follow **Conventional Commits**. Every commit message must start with a type prefix.

| Type | Description |
|---|---|
| `feat` | New feature or page |
| `fix` | Bug fix or patch |
| `refactor` | Code improvement without changing behavior |
| `docs` | Documentation changes |
| `style` | UI/styling changes (brand colors, typography, layout) |
| `chore` | Maintenance tasks (dependency updates, config changes) |
| `perf` | Performance improvements |

### Format

```
<type>: <short description in sentence case>
```

### Examples

```
feat: add contact form with Resend email integration
fix: correct mobile navbar z-index overlap
refactor: simplify API contact route validation logic
docs: update Git guidelines with branch descriptions
style: apply Kidlat brand gradient to hero section
chore: update Resend and React Hook Form dependencies
perf: replace img tags with next/image for Core Web Vitals
```

> **Tips:**
> - Keep the description under 72 characters
> - Use the **imperative mood** — "add" not "added" or "adds"
> - Be specific — "fix contact form validation" not "fix bug"

---

## Step 4 — Push the Branch

Push your branch to GitHub and set the upstream.

```bash
git push -u origin feature/<feature-name>
```

Examples:

```bash
git push -u origin feature/projects-page
git push -u origin fix/contact-form-validation
```

The `-u` flag sets the **upstream branch**, so future pushes and pulls from that branch are simplified to:

```bash
git push
git pull
```

---

## Step 5 — Open a Pull Request

Open a **Pull Request (PR)** on GitHub targeting the correct base branch.

```
feature/<name>  →  sandbox
fix/<name>      →  sandbox
```

Once tested on `sandbox`:

```
sandbox  →  staging
staging  →  main
```

### PR Checklist

Before requesting a review, confirm the following:

- [ ] Code runs locally without errors (`npm run dev`)
- [ ] Commit messages follow the Conventional Commits format
- [ ] No `.env.local` or secrets committed
- [ ] Brand colors, fonts, and gradients follow the Kidlat CivicLabs brand guidelines
- [ ] No `console.log` statements left in production code
- [ ] Relevant pages tested on both desktop and mobile

### Review Process

Team members will:
- Review the code for correctness and brand consistency
- Suggest improvements or request changes
- Approve the PR when it's ready to merge

---

## Important Rules

1. **Never commit directly** to `main` or `staging`.
2. Always branch off from `sandbox` for new work.
3. Always open a **Pull Request** before merging into any protected branch.
4. Use **Squash and Merge** for a clean, readable commit history.
5. **Delete branches** after they are merged.
6. Never commit `.env.local` or any file containing API keys.
7. Keep PRs **small and focused** — one feature or fix per PR.

---

## Complete Workflow Example

### Adding a new Projects page:

```bash
# 1. Start from an updated sandbox
git checkout sandbox
git pull origin sandbox

# 2. Create a feature branch
git checkout -b feature/projects-page

# 3. Make your changes and commit
git add .
git commit -m "feat: add projects page with civic tech case study cards"

# 4. Push to GitHub
git push -u origin feature/projects-page
```

Then on GitHub, open a Pull Request:

```
feature/projects-page → sandbox
```

After review and approval, **Squash and Merge**, then **delete the branch**.

---

### Fixing a bug on the contact form:

```bash
git checkout sandbox
git pull origin sandbox
git checkout -b fix/contact-form-rate-limit

git add .
git commit -m "fix: resolve Upstash rate limit not resetting after 1 hour"

git push -u origin fix/contact-form-rate-limit
```

Open a Pull Request:

```
fix/contact-form-rate-limit → sandbox
```

---

## Quick Reference

| Action | Command |
|---|---|
| Update sandbox | `git checkout sandbox && git pull origin sandbox` |
| New feature branch | `git checkout -b feature/<name>` |
| New fix branch | `git checkout -b fix/<name>` |
| Stage all changes | `git add .` |
| Commit with message | `git commit -m "type: description"` |
| Push and set upstream | `git push -u origin <branch-name>` |
| Push after upstream set | `git push` |
| Check branch status | `git status` |
| View commit history | `git log --oneline` |

---

## Summary

Following this workflow ensures:

- A **clean commit history** that's easy to read and audit
- **Organized development** across team members
- **Safe collaboration** — no accidental overwrites on production
- **Clear code reviews** before anything reaches the live site

---

*Kidlat CivicLabs — All Rights Reserved 2025*
*Git Workflow Guidelines — Last updated May 2026*