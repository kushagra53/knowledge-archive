**From Absolute Basics → Branching → Merging → Professional Feature Branch Workflow**

> *Documented for daily commits & internship portfolio. Based on SuperSimpleDev tutorial + real project experience (AgriAdvisor, NSL-KDD).*

---

## 📋 Table of Contents
- [Core Concepts](#🧠-core-concepts)
- [Daily Local Workflow](#🔄-daily-local-workflow)
- [Remotes & GitHub](#🌐-remotes--github)
- [Branching](#🌿-branching)
- [Merging & Conflicts](#🔗-merging--conflicts)
- [Feature Branch Workflow](#🚀-feature-branch-workflow)
- [Daily Cheat Sheet](#📝-daily-cheat-sheet)
- [Pro Tips](#💡-pro-tips)

---

## 🧠 Core Concepts

| Concept | What it is | Example |
|---------|------------|---------|
| **Repository** | Folder tracked by Git (contains `.git/`) | `~/GitHub/AgriAdvisor/` |
| **Working Directory** | Your current files | Files you edit in VS Code |
| **Staging Area** | Files marked "ready to commit" | `git add WeatherCard.tsx` |
| **Commit** | Saved snapshot with message | `git commit -m "Fix location callback"` |
| **Remote** | Copy on GitHub (`origin`) | `https://github.com/kushagra53/AgriAdvisor` |

---

## 🔄 Daily Local Workflow

git status # What's changed? Current branch?
git add filename.tsx # Stage specific file
git add . # Stage everything
git commit -m "Fix bug" # Save snapshot
git log --oneline --graph # See history visually

text

**Real example from your WeatherCard work:**
git add WeatherCard.tsx page.tsx
git commit -m "Add geolocation callback for header display"

text

---

## 🌐 Remotes & GitHub

### First-time setup
git remote add origin https://github.com/yourusername/repo.git
git remote -v

text

### Push main branch
git checkout main
git push -u origin main

text

### Daily sync
git push # Push current branch
git pull origin main # Sync main after PR merges

text

**Why `git pull`?** GitHub `main` moves ahead when PRs merge. Local catches up.

---

## 🌿 Branching

**Problem:** Building big feature (5 WIP commits) but need bugfix NOW.

**Solution:** Branches = parallel timelines from same starting point.

git checkout main
git pull origin main
git checkout -b feature/geolocation-weather # Create + switch

text

Now work on `feature/geolocation-weather`. `main` stays production-clean.

git branch # List branches
git checkout main # Switch back
git branch -d feature-name # Delete when done

text

**Visual:**
main: A---B---C

feature: D---E (WIP)

text

---

## 🔗 Merging & Conflicts

### Merge feature → main
git checkout main
git pull origin main
git merge feature/geolocation-weather

text

**Auto-merge success:** Creates merge commit on `main`.

**Merge conflict:** Same line changed differently.
<<<<<<< HEAD (main)
old location code
new location callback (feature)

feature-branch

text

**Fix:** Delete markers, write final code, then:
git add .
git commit -m "Resolve merge conflict"

text

---

## 🚀 Feature Branch Workflow
*90% of companies use this exact process.*

### 1. Start clean
git checkout main && git pull origin main

text

### 2. Create feature branch
git checkout -b feature/add-weather-location-header

text

### 3. Build incrementally
git add .
git commit -m "Add geolocation hook"
git add .
git commit -m "Connect WeatherCard to location state"

text

### 4. Push for review
git push -u origin feature/add-weather-location-header

text

### 5. **Pull Request (PR) on GitHub**
Base: main ✓
Compare: feature/add-weather-location-header

text
- Team reviews code diff
- Comments: "Bug here" → Fix → Re-push
- Tests pass → **Merge pull request**

### 6. Sync local
git checkout main && git pull origin main

text

### 7. Cleanup
git branch -d feature/add-weather-location-header
git push origin --delete feature/add-weather-location-header

text

---

## 📝 Daily Cheat Sheet

| When | Commands |
|------|----------|
| **New feature** | `git checkout main && git pull origin main`<br>`git checkout -b feature/name`<br>`git add . && git commit -m "..."`<br>`git push -u origin feature/name` |
| **After PR merged** | `git checkout main && git pull origin main` |
| **Check status** | `git status`<br>`git log --oneline --graph --all` |
