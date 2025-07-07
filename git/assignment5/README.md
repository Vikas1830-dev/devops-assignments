# Git Assignment 5 - Git Flow Workflow

devops-assignments/
└── git/
    └── assignment5/
        ├── feature.txt
        ├── urgent.txt
        └── README.md


## 🎯 Objective

Implement Git Flow branching strategy including:
- Feature development
- Release flow
- Hotfix management

---

## 🧱 Branches Created

- `master`: production-ready
- `develop`: integration of all features
- `feature/assignment5`: for feature development
- `release/1.0`: for preparing a release
- `hotfix/urgent-fix`: for immediate patch to production

---

## 📝 Tasks Performed

1. Created `feature/assignment5` branch and committed `feature.txt`
2. Merged `feature` into `develop`
3. Created `release/1.0`, merged into `master` and `develop`
4. Created `hotfix/urgent-fix`, added `urgent.txt`, merged into both `master` and `develop`

---

## 💻 Git Commands Used

```bash
# Step 1: Create feature branch and file
git checkout -b feature/assignment5
echo "Feature file" > git/assignment5/feature.txt
git add git/assignment5/feature.txt
git commit -m "Added feature.txt"

# Step 2: Create develop branch from master
git checkout master
git checkout -b develop
git push origin develop

# Step 3: Merge feature into develop
git checkout develop
git merge feature/assignment5 -m "Merged feature into develop"

# Step 4: Create release branch
git checkout -b release/1.0
git push origin release/1.0

# Merge release into master
git checkout master
git merge release/1.0 -m "Merged release/1.0 into master"

# Merge release back to develop
git checkout develop
git merge release/1.0 -m "Merged release into develop"

# Step 5: Hotfix
git checkout -b hotfix/urgent-fix master
echo "Urgent fix content" > git/assignment5/urgent.txt
git add git/assignment5/urgent.txt
git commit -m "Hotfix: urgent.txt added"

# Merge hotfix into master and develop
git checkout master
git merge hotfix/urgent-fix -m "Merged hotfix to master"
git checkout develop
git merge hotfix/urgent-fix -m "Merged hotfix to develop"

# Step 6: Push all branches
git push origin master
git push origin develop
git push origin release/1.0
git push origin feature/assignment5
git push origin hotfix/urgent-fix
