# Git Assignment 3

## 🎯 Objective

Work with multiple branches, push them to GitHub, and manage local and remote deletions.

---

## 📝 Tasks Performed

1. Created a Git working directory `assignment3` under `git/`.
2. Created the following branches:
   - `develop`
   - `f1`
   - `f2`
3. In the `master` branch:
   - Committed `main.txt`
4. In each branch:
   - `develop` → committed `develop.txt`
   - `f1` → committed `f1.txt`
   - `f2` → committed `f2.txt`
5. Pushed all branches to GitHub.
6. Deleted `f2` branch locally.
7. Deleted `f2` branch remotely from GitHub.

---

## 💻 Git Commands Used

```bash
# Create assignment3 folder
cd ~/devops-assignments/git
mkdir assignment3
cd assignment3

# Create and commit main.txt in master
echo "Main file" > main.txt
git add git/assignment3/main.txt
git commit -m "Assignment 3: Added main.txt in master"

# Create branches
git branch develop
git branch f1
git branch f2

# develop branch
git checkout develop
echo "Develop file" > git/assignment3/develop.txt
git add git/assignment3/develop.txt
git commit -m "Added develop.txt in develop branch"

# f1 branch
git checkout f1
echo "F1 file" > git/assignment3/f1.txt
git add git/assignment3/f1.txt
git commit -m "Added f1.txt in f1 branch"

# f2 branch
git checkout f2
echo "F2 file" > git/assignment3/f2.txt
git add git/assignment3/f2.txt
git commit -m "Added f2.txt in f2 branch"

# Push all branches
git push origin master
git push origin develop
git push origin f1
git push origin f2

# Delete f2 branch locally and remotely
git branch -d f2              # or git branch -D f2
git push origin --delete f2
