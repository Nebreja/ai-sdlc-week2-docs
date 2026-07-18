# PM Notes <span class="owner-badge" data-owner="harlyn">Harlyn</span>

Board setup steps, milestone status, and screenshots for the AI SDLC Workflow project — kept here as the running log for coordinating the five stages across the team.

---

## Part 1: Plane — Board Setup

### 1. Invite the team

- [ ] Click your workspace name (top-left) → **Settings**
- [ ] Click **Members** in the left pane
- [ ] Click **Add member**

### 2. Set up labels

Labels let you filter and group work items by what kind of work they are.

- [ ] Click the **•••** next to your project name in the sidebar → **Settings**
- [ ] Click **Labels** in the settings sidebar
- [ ] Click **Add label**
- [ ] Type `rag`, pick a color, click **Add**
- [ ] Repeat for each of the following:

| Label |
|---|
| `PM+DOCS` |
| `ARCHITECTURE` |
| `DEVELOPMENT` |
| `RAG` |
| `TESTING` |

### 3. Create modules (group work by feature area)

Modules group related work items into a sub-project — this is what lets you see "how's RAG setup going" separately from "how's testing going."

For each of the four modules below, repeat:

- [ ] Click **Modules** in the project sidebar (or press `M`)
- [ ] Click **Add Module**
- [ ] Fill in the fields
- [ ] Click **Create Module**

| Module | Name | Description | Lead | Start date | Due date |
|---|---|---|---|---|---|
| 1 | PM+DOCS | _fill in_ | _fill in_ | _fill in_ | _fill in_ |
| 2 | ARCHITECTURE | _fill in_ | _fill in_ | _fill in_ | _fill in_ |
| 3 | DEVELOPMENT | _fill in_ | _fill in_ | _fill in_ | _fill in_ |
| 4 | RAG | _fill in_ | _fill in_ | _fill in_ | _fill in_ |
| 5 | TESTING | _fill in_ | _fill in_ | _fill in_ | _fill in_ |

### 4. Create the work items with full properties

Now create the real work items — this time filling in everything, not just the title.

- [ ] Click **Work items** in the sidebar → **Add work item** (or press `C`)
- [ ] Fill in the fields below for each item
- [ ] Click **Save**

| Field | Value |
|---|---|
| Title | _fill in_ |
| State | Todo |
| Priority | _fill in_ |
| Assignee | yourself |
| Label | _fill in_ |
| Estimate | _fill in_ |
| Module | _fill in_ |
| Start date | _fill in_ |
| Due date | _fill in_ |

### 5. Set dependencies matching the flow

- [ ] Open a work item → relations icon → **Add relation**
- [ ] Type **Blocked by** → select both work items → **Add**

### 6. Create the cycle with dates

- [ ] **Cycles** in the sidebar → **Add cycle**
- [ ] Name it
- [ ] Set the date range to your actual dates
- [ ] Create it, open it, **Add existing work item** → select all five → **Add to cycle**

---

## Part 2: Documentation — Deployment

### 1. Create the repo

- [ ] Go to `github.com/new`
- [ ] Name it
- [ ] Set it to **Public** (needed for free GitHub Pages) unless your org has a paid plan for private Pages
- [ ] Check **Add a README file**, click **Create repository**

!!! warning "Public repos only for free Pages"
    GitHub Pages is free for public repositories. If this needs to stay private, you'll need a paid GitHub plan that supports private Pages.

### 2. Add the MkDocs config

- [ ] In the repo, click **Add file** → **Create new file**
- [ ] Name it `mkdocs.yml`, paste your config
- [ ] Click **Commit changes** (directly to `main`)

### 3. Add the doc structure — one file per owner

Create each of these the same way (**Add file** → **Create new file**), inside a `docs/` folder — just type `docs/index.md` as the filename and GitHub creates the folder automatically.

| File | Owner | Content |
|---|---|---|
| `docs/index.md` | Team | Project overview, one-line team summary, short explanation of the flow |
| `docs/architecture.md` | <span class="owner-badge" data-owner="jenilyn">Jenilyn</span> | Placeholder heading — diagram + wireframes |
| `docs/development.md` | <span class="owner-badge" data-owner="daryll">Daryll</span> | Placeholder — Cline setup notes, one task run end-to-end |
| `docs/rag-knowledgebase.md` | <span class="owner-badge" data-owner="reymel">Reymel</span> | Placeholder — reuses the Part B template from the project build guide |
| `docs/testing-observability.md` | <span class="owner-badge" data-owner="vincent">Vincent</span> | Placeholder — Playwright results + SigNoz metric |
| `docs/pm-notes.md` | <span class="owner-badge" data-owner="harlyn">Harlyn</span> | This file — board setup steps, milestone status, screenshots |

### 4. Add the auto-deploy GitHub Action

Create `.github/workflows/deploy.yml` (same "create new file" trick — type the full path as the filename), then paste:

```yaml
name: Deploy MkDocs
on:
  push:
    branches: [main]
permissions:
  contents: write
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: pip install mkdocs-material
      - run: mkdocs gh-deploy --force
```

- [ ] Commit it

!!! tip "Zero-touch builds"
    This runs automatically on every push to `main` — no one on the team needs to run a build command, ever.

### 5. Enable GitHub Pages

- [ ] Repo → **Settings** → **Pages**
- [ ] Under **Build and deployment** → **Source**, select **Deploy from a branch**
- [ ] Branch: `gh-pages` (created automatically the first time the Action above runs — if it's not there yet, push any small change to `main` first and wait a minute)
- [ ] Save — the site is now live

### 6. Invite the team as collaborators

- [ ] Repo → **Settings** → **Collaborators** → **Add people**

---

## Milestone status

| Stage | Owner | Status | Notes |
|---|---|---|---|
| 01 · Home | Team | _fill in_ | |
| 02 · PM Notes | <span class="owner-badge" data-owner="harlyn">Harlyn</span> | _fill in_ | |
| 03 · Architecture | <span class="owner-badge" data-owner="jenilyn">Jenilyn</span> | _fill in_ | |
| 04 · Development | <span class="owner-badge" data-owner="daryll">Daryll</span> | _fill in_ | |
| 05 · RAG Knowledgebase | <span class="owner-badge" data-owner="reymel">Reymel</span> | _fill in_ | |
| 06 · Testing & Observability | <span class="owner-badge" data-owner="vincent">Vincent</span> | _fill in_ | |




