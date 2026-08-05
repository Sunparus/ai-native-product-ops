# Git & GitHub — Quick Reference

## Daily commands
```bash
git status              # what changed since last commit
git add -A               # stage all changes
git commit -m "message"  # save a versioned snapshot
git log --oneline        # see your history
git diff                 # see exactly what changed, unstaged
git push                 # send commits to GitHub
git pull                 # get changes from GitHub
```

## One-time: connect this repo to GitHub
```bash
git remote add origin https://github.com/YOUR-USERNAME/ai-native-product-ops.git
git branch -M main
git push -u origin main
```

## Deploy to GitHub Pages (after pushing to GitHub)
```bash
mkdocs gh-deploy
```
Gives you a live URL at `https://YOUR-USERNAME.github.io/ai-native-product-ops/`.

## Undo mistakes
```bash
git diff                       # see what changed before deciding
git checkout -- <file>         # discard uncommitted changes to one file
git revert <commit-hash>       # safely undo a specific past commit
git reset --soft HEAD~1        # undo the last commit, keep the changes staged
```

## Rules of thumb
1. **Commit small, commit often** — one topic edited = one commit.
2. **Write commit messages that answer "why," not "what."**
3. **Never `git push -f` unless you know exactly why** — it can destroy history.

## Learn properly (30–45 min total, not a course)
- [Learn Git Branching](https://learngitbranching.js.org) — interactive, visual
- [GitHub's Hello World guide](https://docs.github.com/get-started) — covers repos, Pages, pull requests
