# Git Assignment 1

## 🎯 Objective

To demonstrate basic Git operations: creating a folder, adding files, selectively staging, committing, and pushing to a GitHub repository.

---

## 📝 Tasks To Be Performed

1. Based on what you have learnt in the class, do the following steps:

   a. Create a new folder named `assignment1` under the `git` topic.

   b. Inside the folder, create three files:
   - `Code.txt`
   - `Log.txt`
   - `Output.txt`

   c. Stage only:
   - `Code.txt`
   - `Output.txt`

   d. Commit the staged files.

   e. Push the commit to your GitHub repository.

2. Share the commands used for the above steps (see last section).

---

## ✅ Steps Performed

1. Navigated to the main project directory: `devops-assignments`
2. Entered the `git/` folder and created `assignment1`:
   - `mkdir -p git/assignment1`
3. Moved into the folder and created required files:
   - `Code.txt`: Contains dummy code
   - `Log.txt`: Log output (not committed)
   - `Output.txt`: Simulated output
4. Went back to the project root and staged only the required files:
   - `Code.txt`
   - `Output.txt`
   - `README.md`
   - `instructions.md`
6. Committed the staged files with a meaningful message.
7. Pushed the commit to GitHub on the `main` branch.

---

## 🧾 Git Commands Used

```bash
# Step into project folder
cd ~/devops-assignments

# Create assignment1 folder under git topic
mkdir -p git/assignment1
cd git/assignment1

# Create required files
echo "Sample code for Git assignment" > Code.txt
echo "Log file for debugging (not staged)" > Log.txt
echo "Program output content" > Output.txt

# Create documentation
echo "# Git Assignment 1" > README.md
echo "Instructions for the task" > instructions.md

# Go back to root to prepare for commit
cd ~/devops-assignments

# Stage only the required files (excluding Log.txt)
git add git/assignment1/Code.txt
git add git/assignment1/Output.txt
git add git/assignment1/README.md
git add git/assignment1/instructions.md

# Commit the staged files
git commit -m "Git Assignment 1: Added Code.txt, Output.txt, README, and instructions (excluded Log.txt)"

# Push to GitHub
git push origin main

