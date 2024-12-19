
# Azure DevOps Repo Training Agenda

## 1. Introduction
- Brief overview of **Azure DevOps** and its Repos feature.
- Importance of using version control in software development.

---

## 2. Basic Git Operations in Azure DevOps
### Step 1: Clone a Repository
- **Objective**: Understand how to get a local copy of the repository.
- **Command**: `git clone <repository_url>`
- **Demo**: 
  - Navigate to the Azure DevOps Repo.
  - Copy the repository URL.
  - Clone it locally using the terminal or IDE.

### Step 2: Make Changes Locally
- **Objective**: Learn to make changes in the code.
- **Steps**:
  - Open files and make edits.
  - Save changes locally.
  - Use `git status` to check modified files.

### Step 3: Push Changes to Remote
- **Objective**: Commit and push changes to the main branch.
- **Commands**:
  1. `git add <filename>` (or `git add .` for all changes)
  2. `git commit -m "Message"`
  3. `git push`
- **Demo**:
  - Show the updated files appearing in Azure DevOps after pushing.

---

## 3. Intermediate Git Operations
### Step 4: Create and Push a Branch
- **Objective**: Work on isolated branches for new features or bug fixes.
- **Commands**:
  1. Create a branch: `git checkout -b <branch_name>`
  2. Push branch: `git push -u origin <branch_name>`
- **Demo**:
  - Create a new branch, make changes, and push to Azure DevOps.

### Step 5: Understand Protected Branches
- **Objective**: Explain why some branches (like `main`) are protected.
- **Concepts**:
  - Prevents accidental overwrites or direct pushes.
  - Ensures code quality through PR and approvals.

### Step 6: Push Code to Protected Branch via PR
- **Objective**: Learn how to merge changes into protected branches.
- **Steps**:
  1. Push changes to a feature branch.
  2. Create a Pull Request (PR) in Azure DevOps.
  3. Add a reviewer and wait for approval.
  4. Complete the PR to merge changes into the protected branch.

---

## 4. Advanced Git Operations
### Step 7: Add a Reviewer
- **Objective**: Assign team members to review code before merging.
- **Steps**:
  - Open the Pull Request.
  - Add reviewers using Azure DevOps UI.
  - Explain the importance of code reviews for maintaining quality.

### Step 8: Revert or Reset Changes
- **Objective**: Handle mistakes in code using Git revert and reset.
- **Commands**:
  - **Revert**: Create a new commit that undoes changes.
    - `git revert <commit_hash>`
    - Safe for shared repositories.
  - **Reset**: Completely remove changes.
    - Soft Reset: `git reset --soft <commit_hash>` (keeps staged changes).
    - Hard Reset: `git reset --hard <commit_hash>` (removes changes permanently).
- **Difference**:
  - **Revert**: Keeps history intact.
  - **Reset**: Alters commit history.
- **Demo**:
  - Show both commands with examples and highlight scenarios to use each.

### Step 9: Use .gitignore to Skip Files
- **Objective**: Exclude specific files or directories from version control.
- **Steps**:
  1. Create a `.gitignore` file in the repository root.
  2. Add file patterns (e.g., `*.log`, `node_modules/`).
  3. Test by running `git status`.
- **Demo**:
  - Add entries to `.gitignore`, commit the file, and test its functionality.

---

## 5. Best Practices
- Use descriptive commit messages.
- Regularly pull changes from the remote branch.
- Avoid force-pushing to shared branches.
- Conduct thorough code reviews for every PR.
- Update `.gitignore` to avoid committing sensitive or unnecessary files.

---

## 6. Hands-On Session
- Assign practice tasks:
  1. Clone a repository.
  2. Create and switch to a new branch.
  3. Push changes and create a PR with a reviewer.
  4. Revert or reset a specific commit.
  5. Use `.gitignore` to exclude files.

---

## 7. Q&A and Wrap-Up
- Open the floor for questions.
- Share additional resources and documentation.
- Summarize key takeaways.
