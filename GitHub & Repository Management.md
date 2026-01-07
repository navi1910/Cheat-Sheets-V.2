# GitHub & Repository Management – Practical Cheat Sheet

> **Purpose**: This document is a **zero-fluff, copy-paste-ready GitHub cheat sheet**.
> It is designed for **real coding**, **emergencies**, **production discipline**, and **secure repo management**.
> Python-first, industry-aligned, and compliant with **OWASP Top 10** and **ISO/IEC 27001:2022**.

---

## 1. Core Concepts (Know This or You Will Break Things)

### Git vs GitHub

* **Git**: Distributed version control system running locally
* **GitHub**: Hosted platform for Git repositories, collaboration, CI/CD

### Repository (Repo)

* A container for:

  * Source code
  * Commit history
  * Branches
  * Issues, PRs, Actions

### Working Tree States

* **Untracked**: New files Git does not know
* **Modified**: File changed but not staged
* **Staged**: Ready to commit
* **Committed**: Saved in Git history

---

## 2. Initial Setup (Do This Once)

### Install Git

```bash
git --version
```

### Configure Identity

```bash
git config --global user.name "Your Name"
git config --global user.email "you@email.com"
```

### Secure Defaults (Mandatory)

```bash
git config --global init.defaultBranch main
git config --global pull.rebase true
git config --global fetch.prune true
```

---

## 3. Creating a Repository

### Create Local Repo

```bash
git init
```

### Clone Existing Repo

```bash
git clone https://github.com/user/repo.git
```

### Check Status (Run This Constantly)

```bash
git status
```

---

## 4. Basic Daily Workflow (90% of Usage)

```bash
git status
git add .
git commit -m "meaningful message"
git pull
git push
```

### Stage Specific File

```bash
git add app.py
```

### Commit Best Practice

```bash
git commit -m "feat: add demand forecasting baseline"
```

**Commit Prefixes**

* `feat:` new feature
* `fix:` bug fix
* `refactor:` internal change
* `docs:` documentation
* `test:` tests only

---

## 5. Branching (Non-Negotiable for Professionals)

### Create and Switch Branch

```bash
git checkout -b feature/scenario-agent
```

### List Branches

```bash
git branch
```

### Switch Branch

```bash
git checkout main
```

### Delete Branch

```bash
git branch -d feature/scenario-agent
```

---

## 6. Remote Management

### View Remotes

```bash
git remote -v
```

### Add Remote

```bash
git remote add origin https://github.com/user/repo.git
```

### Push First Time

```bash
git push -u origin main
```

---

## 7. Pull Requests (PRs) – How Real Teams Work

### Flow

1. Create branch
2. Commit changes
3. Push branch
4. Open PR on GitHub
5. Code review
6. Merge

### Never

* Commit directly to `main`
* Merge without review

---

## 8. Merge vs Rebase (Use This Correctly)

### Merge (Safe, Messy)

```bash
git merge main
```

### Rebase (Clean, Dangerous if Misused)

```bash
git rebase main
```

**Rule**: Never rebase shared branches

---

## 9. Undoing Mistakes (Emergency Section)

### Undo Last Commit (Keep Changes)

```bash
git reset --soft HEAD~1
```

### Undo Last Commit (Destroy Changes)

```bash
git reset --hard HEAD~1
```

### Discard File Changes

```bash
git checkout -- file.py
```

### Unstage File

```bash
git reset file.py
```

---

## 10. Stashing (Context Switching Like a Pro)

```bash
git stash
git stash list
git stash apply
git stash drop
```

---

## 11. Logs & Debugging

```bash
git log --oneline --graph --all
```

### Blame (Who Broke This?)

```bash
git blame app.py
```

---

## 12. .gitignore (Security Critical)

### Python Example

```gitignore
__pycache__/
.env
*.log
*.csv
*.db
.venv/
```

**Never commit**

* Secrets
* Credentials
* Production configs

---

## 13. GitHub Repo Structure (Recommended)

```text
repo/
├── src/
├── tests/
├── docs/
├── .github/workflows/
├── .gitignore
├── README.md
├── requirements.txt
```

---

## 14. README.md Template (Copy-Paste)

````md
# Project Name

## Overview
What problem this solves.

## Tech Stack
- Python
- Django
- PostgreSQL

## Setup
```bash
pip install -r requirements.txt
````

## Run

```bash
python manage.py runserver
```

````

---

## 15. GitHub Actions (Basic CI)

```yaml
name: CI
on: [push]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
      - run: pip install -r requirements.txt
      - run: pytest
````

---

## 16. Security Best Practices (OWASP + ISO Aligned)

* Enable branch protection rules
* Require PR reviews
* Enable secret scanning
* Use environment secrets
* Sign commits
* Least privilege access

---

## 17. Tagging & Releases

```bash
git tag v1.0.0
git push origin v1.0.0
```

---

## 18. Common Anti-Patterns (Stop Doing This)

* One giant commit
* No README
* Secrets in repo
* Direct push to main
* No branching strategy

---

## 19. Mental Model (Remember This)

> Git is a **timeline**, not storage.
> Commits are **checkpoints**.
> Branches are **parallel universes**.

---

## 20. Absolute Emergency Commands

```bash
git status
git log --oneline
git diff
git reset --soft HEAD~1
git stash
git pull --rebase
git push -f   # ONLY if you fully understand consequences
```

---

