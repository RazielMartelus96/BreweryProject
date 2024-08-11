24202408111105
Status: #idea
Tags: 
# Git Workflow 
## Overview 
This document outlines a common Git workflow involving multiple branches such as `master`, `dev`, and `feature` branches. This workflow is designed to help teams work on new features, fix bugs, and deploy stable code efficiently. 
## 1. Branch Structure 
![[Git Workflow Image.png]]
### 1.1. `master` Branch 
The `master` branch is the main branch in the repository. It should always reflect a stable version of the project that is ready for deployment. Direct commits to `master` are generally avoided. 
### 1.2. `dev` Branch 
The `dev` branch is the integration branch where all feature branches are merged before being pushed to `master`. It represents the latest working state of the project. 
### 1.3. `feature` Branches
Feature branches are created from `dev` for working on new features, bug fixes, or other tasks. Once a feature is complete, it is merged back into `dev`. Feature branches are often named based on the feature or issue being addressed, for example, `feature/new-login` or `bugfix/login-error`.
### 1.4. `release` Branches 
Release branches are created from `dev` when the code in `dev` is feature-complete and ready for final testing and bug fixing before being merged into `master`. These branches allow the team to stabilise the release without interrupting ongoing development in `dev`. 
### 1.5. `hotfix` Branches
Hotfix branches are created from `master` to quickly address critical issues found in the production environment. Once the hotfix is completed, it is merged back into both `master` and `dev` to ensure the fix is applied across the project.
# References
[Workflow Image](https://miro.medium.com/v2/resize:fit:1400/0*0TGRkQG3gZ_X94li.png)