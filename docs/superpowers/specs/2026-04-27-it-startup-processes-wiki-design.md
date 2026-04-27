# Design Spec: IT Startup Processes Wiki (MkDocs)

**Date:** 2026-04-27
**Status:** Approved
**Author:** AI Design Assistant
**Audience:** Startup team (4 devs, 3 QA, 1 TL, 1 Designer, 1 DevOps)

---

## 1. Overview

A centralized, searchable, version-controlled knowledge base documenting all engineering, QA, design, and operational processes for a small startup team. Built with **MkDocs + Material theme**, deployed as a static site.

### Goals
- Reduce repeated questions about "how we do things"
- Speed up onboarding of new team members
- Standardize processes across dev, QA, DevOps, and design
- Keep documentation close to code (Git-based workflow)

### Non-Goals
- Real-time collaboration editing (like Google Docs)
- Complex access control (public or team-wide)
- Integration with task trackers (Jira/Linear)

---

## 2. Architecture

```
Git Repository
├── docs/                    # Markdown source files
│   ├── index.md             # Landing page
│   ├── onboarding/
│   ├── development/
│   ├── testing/
│   ├── devops/
│   ├── releases/
│   ├── design/
│   ├── communication/
│   ├── incidents/
│   └── glossary.md
├── mkdocs.yml               # MkDocs configuration
├── requirements.txt         # Python dependencies
└── .github/workflows/
    └── deploy.yml           # Auto-deploy to GitHub Pages
```

### Technology Stack
| Component | Choice | Rationale |
|-----------|--------|-----------|
| Generator | MkDocs | Simple, fast, widely adopted |
| Theme | Material for MkDocs | Modern UI, dark mode, search, nav |
| Hosting | GitHub Pages | Free, integrated with Git |
| CI/CD | GitHub Actions | Auto-deploy on merge to main |

---

## 3. Content Structure

### 3.1 Landing Page (`index.md`)
- Project mission statement
- Quick links to most-used sections
- "How to edit this wiki" guide
- Last updated timestamp

### 3.2 Onboarding (`onboarding/`)
- **Day 1 Checklist**: accounts, accesses, workspace setup
- **Tools**: list of all services and how to get access
- **First PR**: step-by-step guide to making first contribution
- **Team Contacts**: who to ask about what

### 3.3 Development (`development/`)
- **Git Workflow**: branching model (e.g., trunk-based or GitFlow)
- **Code Style**: linters, formatters, naming conventions
- **Code Review**: who reviews, turnaround time, what to check
- **Commits**: conventional commits or team convention
- **Pull Requests**: template and required fields

### 3.4 Testing (`testing/`)
- **Test Pyramid**: unit, integration, e2e responsibilities
- **Bug Reports**: template, required fields, severity levels
- **Environments**: where testing happens
- **Regression**: when and how to run

### 3.5 DevOps (`devops/`)
- **CI/CD Pipeline**: stages, checks, approvals
- **Environments**: dev, staging, prod — what's different
- **Monitoring**: dashboards, key metrics, alerting
- **Access**: who can access what infrastructure

### 3.6 Releases (`releases/`)
- **Release Checklist**: pre-release, deployment, post-release
- **Ownership**: who is Release Manager
- **Hotfixes**: emergency process
- **Rollback**: when and how

### 3.7 Design (`design/`)
- **Handoff**: how designs move from Figma to dev
- **Design System**: components, tokens, usage
- **Tools**: Figma, other design resources

### 3.8 Communication (`communication/`)
- **Channels**: Slack/Teams channels and their purpose
- **Meetings**: standups, retros, plannings
- **Escalation**: when and how to escalate blockers

### 3.9 Incidents (`incidents/`)
- **Severity Levels**: P0 (prod down) to P3 (minor)
- **Runbook**: step-by-step response for each severity
- **Postmortem**: template and timeline requirements

### 3.10 Glossary (`glossary.md`)
- Company-specific terms, abbreviations, service names

---

## 4. Editing Workflow

1. **Create branch** for documentation changes
2. **Edit Markdown** files in `docs/`
3. **Open Pull Request** — treat docs like code
4. **Review** by at least one team member
5. **Merge to main** — auto-deploy via GitHub Actions
6. **Site updates** within 1-2 minutes

---

## 5. Deployment

### GitHub Actions Workflow
- Trigger: push to `main`
- Steps:
  1. Checkout code
  2. Setup Python
  3. Install `mkdocs-material`
  4. Run `mkdocs gh-deploy --force`
- Result: site available at `https://<org>.github.io/<repo>/`

### Local Preview
```bash
pip install -r requirements.txt
mkdocs serve
# Open http://127.0.0.1:8000
```

---

## 6. MkDocs Configuration Highlights

```yaml
site_name: "Team Wiki"
theme:
  name: material
  palette:
    - media: "(prefers-color-scheme: light)"
      scheme: default
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
features:
  - navigation.tabs
  - search.suggest
  - search.highlight
plugins:
  - search
```

---

## 7. Success Criteria

- [ ] All 10 sections have initial content
- [ ] Site is accessible via public/private URL
- [ ] Any team member can edit via PR in under 5 minutes
- [ ] Search returns relevant results for common queries
- [ ] Onboarding time for new hires reduced (measure after 1 month)

---

## 8. Future Enhancements (Post-MVP)

- Versioning (if multiple product versions need docs)
- Blog/Announcements section for process changes
- Integration with Slack bot for quick lookups
- PDF export for offline reading
