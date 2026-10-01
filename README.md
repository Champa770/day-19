## Practice — Team Workflow Simulation

This is a practice/consolidation day — no new concepts, just applying everything from this week (branching, merging, remote, GitHub, PRs) in one realistic simulated flow. 

**Goal**

Simulate a real 2-developer workflow on a shared GitHub repo, end to end — from issue creation to merged PR.

---

**Setup**

- One student creates a repo on GitHub with a README
- Adds the second student as a collaborator (Settings → Collaborators), or if solo, just proceed as one person doing both roles in sequence
- Both clone the repo locally

```bash
git clone https://github.com/username/team-practice.git
```**Step-by-step simulation**

**1. Create issues first (project owner)**

Open 3 issues on GitHub representing small tasks:

- "Add header section"
- "Add footer section"
- "Style buttons"

**2. Pick up an issue, branch off it (developer 1)**

```bash
git switch -c feature-header
```

Build the header section in `index.html`/`style.css`.

```bash
git add .
git commit -m "Add header section, re
``````bash
fs #1"
git push -u origin feature-header
```

**3. Open a PR**

On GitHub — base: `main`, compare: `feature-header`. Description should reference the issue:

```markdown
Closes #1
```

**4. Second developer reviews (or pretend-review if solo)**

- Leave at least one comment on a specific line
- Either approve, or request a small change

**5. Address feedback if requested**

```bash
# make the requested change
git add .
git commit -m "Adjust header padding per review"
git push
```

PR updates automatically — no need to reopen anything.

**6. Merge the PR**

Use "Squash and merge" on GitHub. Confirm issue #1 auto-closes.

**7. Sync main locally**

```bash
git switch main
git pull origin main
```

**8. Repeat for the footer and button-styling issues**

Same cycle: branch → commit → push → PR → review → merge → pull → delete branch.

**9. Deliberately create a merge conflict**

On two separate branches, edit the exact same line in `index.html` differently. Open PRs for both, merge the first cleanly, then try merging the second — GitHub will flag a conflict. Resolve it either:

- Locally (pull the branch, fix the conflict, commit, push), or
- Directly in GitHub's web editor, which shows the same conflict markers

**10. Clean up**

```bash
git branch -d feature-header
git push origin --delete feature-header
```

Delete all merged branches, locally and remotely.

---

**What to check at the end**

- `main` has a clean, readable commit history (thanks to squash merges)
- All 3 issues show as closed, each linked to the PR that closed it
- No leftover merged branches cluttering the repo
- Commit messages are clear and descriptive throughout, not "fix", "update", "asdf"# day-19
git 5 practice- team workflow simulation
