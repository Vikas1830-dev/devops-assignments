# Git Assignment 2

## 🎯 Objective

Practice Git branching, stashing, and working with multiple branches.

---

## 📝 Tasks Performed

1. Created `feature1.txt` and `feature2.txt` in the `master` branch and committed them.
2. Created three branches:
   - develop
   - feature1
   - feature2
3. In the `develop` branch:
   - Created `develop.txt`
   - Did NOT stage or commit it
4. Stashed `develop.txt`
5. Switched to `feature1` branch
   - Created and committed `new.txt`
6. Switched back to `develop`
   - Unstashed `develop.txt`
   - Staged and committed it

---

## 💻 Git Commands Used

```bash
# Create and move into assignment2
cd git
mkdir assignment2
cd assignment2

# Create initial files in master
echo "Feature 1 content" > feature1.txt
echo "Feature 2 content" > feature2.txt

# Stage and commit in master
cd ~/devops-assignments
git add git/assignment2/feature1.txt git/assignment2/feature2.txt
git commit -m "Git Assignment 2: Added feature1.txt and feature2.txt to master branch"

# Create branches
git branch develop
git branch feature1
git branch feature2

# Work in develop
git checkout develop
echo "Develop branch file" > git/assignment2/develop.txt

# Stash untracked file
git stash push -m "Uncommitted develop.txt file" --include-untracked

# Switch to feature1 and add new.txt
git checkout feature1
echo "This is a new file in feature1 branch" > git/assignment2/new.txt
git add git/assignment2/new.txt
git commit -m "Added new.txt in feature1 branch"

# Go back to develop and unstash
git checkout develop
git stash pop
git add git/assignment2/develop.txt
git commit -m "Committed develop.txt after unstashing in develop branch"

# Push all branches
git push origin master
git push origin develop
git push origin feature1
git push origin feature2
