# DevOps Learning

## Day 01

### What is DevOps?

**DevOps** is a combination of **Development (Dev)** and **Operations (Ops)**. It represents a set of practices and cultural philosophies that integrate software development and IT operations to deliver applications and services faster, more reliably, and with continuous improvement.

---

### Web Concepts: Website, WebApp, Static, & Dynamic

#### 1. Website

- **Purpose**: Primarily informational (e.g., news sites, blogs, portfolios).
- **Interaction**: Limited—users mostly read or view content.
- **Complexity**: Simple structure, fewer features.
- **Examples**: News sites, personal blogs, company homepages.

#### 2. Web Application (WebApp)

- **Purpose**: Interactive and task-oriented (e.g., Amazon, Facebook, Google Docs).
- **Interaction**: High—users perform actions like logging in, buying, or editing.
- **Complexity**: Includes complex logic, backend, and frontend integration.

#### 3. Static Sites

- **Content**: Fixed and the same for all users.
- **Tech Stack**: Pure HTML, CSS, and basic JS.
- **Performance**: Very fast (served directly from server/CDN).
- **Example**: Personal portfolio with bio and projects.

#### 4. Dynamic Sites

- **Content**: Changes based on user input, database, or server logic.
- **Tech Stack**: Backend languages (Node.js, PHP, Python) and databases (MongoDB, MySQL).
- **Performance**: Slightly slower as the server processes requests.
- **Example**: E-commerce platforms with product listings and payments.

> **Key Distinction**: A website can be static (simple info) or dynamic (news with updates). A WebApp is almost always dynamic due to the need for processing user actions and authentication.

---

### Key Terminology & Tools

#### Architecture

- **3-Tier Architecture**: Frontend, Backend, Database.
- **MLOps**: Machine Learning Operations.
- **ML / Algorithms**: Core logic for AI/ML.

#### Essential Linux Commands

- `touch`: Create an empty file.
- `cat`: View file content.
- `vim`: Text editor (`i` for insert mode, `Esc` to exit insert mode, `:wq` to save and quit, `:q!` to quit without saving, `:q` to quit, `:w` to save only).
- `rm`: Remove a file.
- `rm -rf`: Remove recursively (use with caution, e.g., for directories).
- `sudo`: SuperUser Do (execute with administrative privileges).

#### Git Version Control (VCS)

Git tracks changes and enables collaboration.

**The 3 Stages of Git:**

1.  **Working Directory** (Red/Unstaged)
    - Changes are local and untracked.
    - Check with: `git status`
2.  **Staging Area** (Green/Staged)
    - Files are marked to be committed.
    - Add with: `git add <file>`
3.  **Repository** (Blue/Committed)
    - A snapshot of the code is saved in the local repo with a commit ID/hash.
    - Commit with: `git commit -m "message"`

**The 3 Types of Git Reset (Undo Last Commit):**

1. **Soft Reset**:

   - Removes the last commit but keeps changes staged (ready to recommit).
   - Use: `git reset --soft HEAD~1`

2. **Hard Reset**:

   - Removes the last commit and discards changes.
   - Use: `git reset --hard HEAD~1`

3. **Mixed Reset** (Default):
   - Removes the last commit but keeps changes unstaged (ready to recommit).
   - Use: `git reset HEAD~1`

# 🔄 Git File Delete & Restore Scenarios

This guide explains how to restore files in Git depending on how they were deleted.

---

## 📂 Case 1: File was committed before deletion (deletion not committed yet)

- **Situation:** The file existed in a previous commit, you deleted it locally but haven’t committed the deletion.
- **Steps:**
  `git status`
  `git restore <filename>`
- ✅ Restores the file exactly as it was in the last commit.

2. **Case 2: File was deleted but not committed yet**

   - Situation: You created the file, never staged (git add) or committed it, then deleted it.
   - Git cannot restore this file because it was never tracked.
   - Recover it from your editor’s backup, recycle bin/trash, or external backup.
   - ⚠️ Git only restores files that were committed at least once.

3. **Case 3: File was deleted and already committed**

   - If you committed the deletion but want the file back:
   - Find the commit hash where the file still existed: Use: `git log -- <filename>`
   - Restore it from that commit: Use: `git checkout <commit_hash> -- <filename>`
   - Eaxmple:`git checkout abc123 -- index.html`
   - ✅ Brings the file back from history.

4. **Case 4:File was committed, then deleted, and pushed to remote**

- Situation: The deletion commit has already been pushed.
- Safe way (recommended): Restore the file from its old commit and commit it again:
- `git checkout <commit_hash> -- <filename>`
- `git add <filename>`
- `git commit -m "Restore deleted file"`
- `git push`
  **Dangerous way (avoid unless necessary): Rewrite history with `git reset` or `git revert`**
- ⚠️ This can cause conflicts if others have pulled the branch.

**Configuration:**

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Common Tasks:**

- **Untrack/Reset**: To remove the git tracking folder: `rm -rf .git`
