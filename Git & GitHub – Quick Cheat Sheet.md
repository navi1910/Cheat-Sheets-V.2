# Git & GitHub – Quick Cheat Sheet

Fast, scannable commands for daily Git + GitHub usage.

---

## 1. Check / Set Git Identity

```bash
git config --global --list
git config --local --list
```

```bash
git config --global user.name "USERNAME"
git config --global user.email "EMAIL_USED_ON_GITHUB"
```

---

## 2. Start Repo (Local → GitHub)

```bash
cd C:\dev\project
git init
git add .
git commit -m "Initial commit"
```

(Create EMPTY repo on GitHub)

```bash
git remote add origin https://github.com/USERNAME/REPO.git
git branch -M main
git push -u origin main
```

---

## 3. Clone Existing Repo

```bash
git clone https://github.com/USERNAME/REPO.git
cd REPO
```

---

## 4. Daily Workflow

```bash
git status
git pull
git add .
git commit -m "message"
git push
```

---

## 5. Branching

Create:

```bash
git checkout -b feature/name
```

Switch:

```bash
git checkout main
```

Delete local:

```bash
git branch -d branch-name
```

Delete remote:

```bash
git push origin --delete branch-name
```

---

## 6. Delete a File Properly

```bash
git rm file.ext
git commit -m "Remove file"
git push
```

---

## 7. Rename Branch

```bash
git branch -m old-name new-name
git push origin new-name
git push origin --delete old-name
```

(Set default branch on GitHub UI)

---

## 8. .gitignore (Minimal)

```gitignore
__pycache__/
*.pyc
.env
.venv/
venv/
.vscode/
.idea/
.DS_Store
Thumbs.db
```

---

## 9. Check Commit Author

```bash
git log --pretty=full -1
```

---

## 10. Reset GitHub Login (Windows)

```bash
cmdkey /list
cmdkey /delete:git:https://github.com
```

Re-auth:

```bash
git push
```

(Use PAT, not password)

---

## 11. Delete & Recreate Repo (Same Name)

```bash
git remote remove origin
git remote add origin https://github.com/USERNAME/REPO.git
git push -u origin main
```

---

## 12. Do NOT Do These

* Commit `.env`
* Work inside OneDrive
* Force push blindly
* Delete repos to fix mistakes
