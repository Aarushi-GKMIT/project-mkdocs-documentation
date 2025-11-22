# Code Merge Workflow

This document outlines the complete workflow followed for merging code in the **frontend and backend repositories** of this project.  
The workflow ensures clean commits, stable branches, predictable releases, and automated CI/CD deployments to EC2 instances.

---

# 1. Branching Strategy

The project follows a **feature-branch workflow**, where each feature or module is developed in its own branch.

---

## Backend Branches

The backend (API Server, Build Server, Reverse Proxy Server) contains the following branches:

- `dev`
- `main`
- `feature/add-folder-structure`
- `feature/admin-routes`
- `feature/auth-routes`
- `feature/build-server`
- `feature/ci-cd`
- `feature/db-schema`
- `feature/project-routes`
- `feature/route53`
- `feature/s3-reverse-proxy`

---

## Frontend Branches

The frontend repository contains the following branches:

- `dev`
- `main`
- `feature/admin-dashboard`
- `feature/auth-pages`
- `feature/ci-cd`
- `feature/project-pages`
- `feature/project-structure`
- `feature/pwa`
- `feature/readme`
- `feature/test-cases`

Each branch corresponds to a page, module, or CI/CD related task.

---

# 2. Pull Request (PR) Workflow

All code merges must come through a Pull Request.

### Steps:

1. **Create a feature branch**
```bash
   git checkout -b feature/branch-name
```

2. **Work on a feature**
```bash
    git add .
    git commit -m "Meaningful commit message"
```

3. **Push branch to remote**
```bash
    git push origin feature/branch-name
```

4. Create a Pull Request (PR)

5. Code Review

```bash
    git commit -m "fix: updated based on review"
    git push
```

6. Automated Checks (CI)
7. Merge the PR
8. Pull updates locally

```bash
    git checkout dev
    git pull
```


