# git-recovery-practice

A practice repo where I made three Git mistakes on purpose and fixed them.

## 1. Wrong commit
I committed a file by mistake (`wrong.txt`, "oops wrong file").
Fix: `git reset --soft HEAD~1` undid the commit and kept my work.
Why: the commit was local and unpushed, so rewriting it affected nobody.
If it had been pushed, I would use `git revert` instead.

## 2. Merge conflict
I changed the same line of `app.txt` on `main` and `feature`, then ran `git merge feature`.
Fix: I edited the file, removed the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`),
kept the correct line, then ran `git add` and `git commit`.
Why: Git cannot decide which version is right, so a person must choose.

## 3. Lost branch
I made `lost-branch` with a commit, then deleted it with `git branch -D lost-branch`.
Fix: `git reflog` showed the last commit (`e4e875f`), and
`git branch lost-branch e4e875f` brought the branch back.
Why: deleting a branch only removes the pointer, and the commits stay in Git for a while.

## Safety
This is a practice repo only. It has no passwords or secrets.
I used `reset` only on unpushed work, and would use `revert` on shared history.