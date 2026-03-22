# 🚀 GitHub Actions Learning Lab: From Zero to CD

[English](#-github-actions-learning-lab-from-zero-to-cd) | [Русский](README.md)

This repository is my practical playground for learning GitHub Actions (GHA).  
**Goal:** Go from simple automation to a full CI/CD pipeline with deployment to my own server.

--- 

## 🧭 Roadmap

### Step 1: Basics and CI (Continuous Integration)
- **YAML Syntax:** Workflow structure (name, on, jobs, steps).
- **Quality Control:** Setup linters and auto-build (`dotnet build` / `pip install`).
- **Testing:** Unit tests and blocking deploy if tests fail.
- **Artifacts:** Save build files using `actions/upload-artifact`.

### Step 2: Containerization and Security
- **Docker:** Build images inside GHA.
- **Registry:** Push images to GitHub Container Registry (GHCR).
- **Secrets:** Use encrypted variables for Docker/SSH access.

### Step 3: Infrastructure and CD (Continuous Deployment)
- **Self-hosted Runner:** Setup your own agent on a Virtual Machine (VM).
- **Vagrant:** Automation of runner environment (Infrastructure as Code).
- **Deployment:** Auto-update the app on the server after pushing to `main` branch.

---

## 🛠 Prerequisites

To practice "Self-hosted Runner" locally, you need:

| Tool | Min. Version | Link |
| :--- | :---: | :---:|
| Vagrant | 2.3 |[Install](https://developer.hashicorp.com/vagrant/downloads)<br>[Quick Start](https://developer.hashicorp.com/vagrant/tutorials/get-started) |
| VirtualBox | 7.0| [Download](https://www.virtualbox.org/) |
| Git | latest | [Download](https://git-scm.com/) | 

**Architectural Notes:** 
- We use Vagrant to avoid the ***"It works on my machine"*** problem.
- If you use Apple Silicon (M1/M2) or another ARM CPU, you need to adapt the [Architecture](https://developer.hashicorp.com/vagrant/docs/boxes).
- This project uses the *virtualbox* provider. If you use another one, you must adapt it for your [Provider](https://developer.hashicorp.com/vagrant/docs/providers).  

---

## 📚 Learning Checklist

### 🟢 Module 1: Basic Automation
- [ ] Create first Workflow (`hello-world.yml`).
- [ ] Learn triggers: `push`, `pull_request`, `workflow_dispatch`.
- [ ] Use Contexts (example: `github.sha`, `github.ref`).

### 🔵 Module 2: Continuous Integration (CI)
- [ ] App build step.
- [ ] Run tests and handle errors.
- [ ] Parallel Jobs (Matrix Strategy).
- [ ] Optimization: Dependency caching (`actions/cache`).

### 🟠 Module 3: Docker and Artifacts
- [ ] Write a Dockerfile (Multi-stage).
- [ ] Login and Push to GHCR.
- [ ] Share data between Jobs using Artifacts.

### 🔴 Module 4: Self-hosted & Deploy
- [ ] Setup `Vagrantfile` for server preparation.
- [ ] Install and register GitHub Runner in OS.
- [ ] CD: Update containers via `docker-compose` on the server.

---

## ⚠️ Security Best Practices

1. **Public Repo Warning:** Do not use self-hosted runners in public repositories without the *"Require approval for all outside collaborators"* setting.
2. **No Root:** Run the runner agent as a separate user, not as `root`.
3. **Secrets:** Never print secrets to the console (logging).

---
*Created for professional growth and automation mastery.*