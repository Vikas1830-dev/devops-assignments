# Git Assignment 4

## 🎯 Objective

To practice advanced branching and merging in Git, simulating public/private workflows and syncing updates across multiple branches.

---

## 📝 Tasks Performed

1. Created `master.txt` on the `master` branch and committed it.
2. Created 3 branches:
   - `public 1`
   - `public 2`
   - `private`
3. On `public 1`, created and committed `public1.txt`
4. Merged `public 1` into `master`
5. Created and committed `public2.txt` in `public 2`, then merged into `master`
6. Switched to `private`, edited `master.txt`, and committed changes
7. Merged updated `master` into both `public 1` and `public 2`
8. Made a further update to `master.txt` in `master`
9. Merged final `master` updates into `private`

---

## 💻 Git Commands Used

```bash
# Step into assignment4 folder and create file
echo "This is master branch file" > git/assignment4/master.txt
git add git/assignment4/master.txt
git commit -m "Added master.txt"

# Create branches
git branch "public 1"
git branch "public 2"
git branch private

# public 1
git checkout "public 1"
echo "Public 1" > git/assignment4/public1.txt
git add git/assignment4/public1.txt
git commit -m "Added public1.txt"

# Merge into master
git checkout master
git merge "public 1" -m "Merged public 1"

# public 2
git checkout "public 2"
echo "Public 2" > git/assignment4/public2.txt
git add git/assignment4/public2.txt
git commit -m "Added public2.txt"
git checkout master
git merge "public 2" -m "Merged public 2"

# private
git checkout private
echo "Private branch update" >> git/assignment4/master.txt
git add git/assignment4/master.txt
git commit -m "Updated master.txt in private"

# Update public 1 and public 2 with new master
git checkout "public 1"
git merge master -m "Merged master into public 1"

git checkout "public 2"
git merge master -m "Merged master into public 2"

# Update master again
git checkout master
echo "Further update in master" >> git/assignment4/master.txt
git add git/assignment4/master.txt
git commit -m "Further update"

# Merge final update to private
git checkout private
git merge master -m "Merged latest master into private"
