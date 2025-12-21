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


**Configuration:**

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Common Tasks:**

- **Untrack/Reset**: To remove the git tracking folder: `rm -rf .git`
