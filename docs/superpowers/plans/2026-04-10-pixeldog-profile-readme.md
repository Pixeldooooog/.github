# Pixeldog Profile README Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build the `Pixeldooooog/.github` organization profile README in the correct `profile/README.md` location, add restrained dynamic widgets, and automate the contribution snake asset.

**Architecture:** Keep the visible profile content in `profile/README.md`, keep the repository root `README.md` as a small repository note, and generate snake assets through a scheduled GitHub Actions workflow that publishes SVG files to an `output` branch. The design stays text-first so the page still works even when third-party widgets are unavailable.

**Tech Stack:** GitHub Flavored Markdown, inline HTML inside Markdown, GitHub Actions YAML, `Platane/snk`, `peaceiris/actions-gh-pages`, `github-readme-stats`, `readme-typing-svg`

---

### Task 1: Correct the profile file location

**Files:**
- Create: `profile/README.md`
- Modify: `README.md`
- Modify: `docs/superpowers/specs/2026-04-10-pixeldog-profile-readme-design.md`

- [ ] **Step 1: Write the failing test**

```bash
test -f profile/README.md
```

- [ ] **Step 2: Run test to verify it fails**

Run: `test -f profile/README.md`
Expected: exit code `1` because the organization profile README does not exist yet

- [ ] **Step 3: Write minimal implementation**

Create `profile/README.md` with the manifesto-style homepage content, and update the root `README.md` to briefly explain that the live organization profile content lives in `profile/README.md`. Update the design spec so the documented file plan matches the actual `.github` organization profile behavior.

- [ ] **Step 4: Run test to verify it passes**

Run: `test -f profile/README.md`
Expected: exit code `0`

- [ ] **Step 5: Commit**

```bash
git add profile/README.md README.md docs/superpowers/specs/2026-04-10-pixeldog-profile-readme-design.md
git commit -m "feat: move profile content to organization README"
```

### Task 2: Add the styled dynamic profile content

**Files:**
- Modify: `profile/README.md`

- [ ] **Step 1: Write the failing test**

```bash
rg -n "readme-typing-svg|github-readme-stats|raw.githubusercontent.com/.*/github-snake" profile/README.md
```

- [ ] **Step 2: Run test to verify it fails**

Run: `rg -n "readme-typing-svg|github-readme-stats|raw.githubusercontent.com/.*/github-snake" profile/README.md`
Expected: exit code `1` before the widget embeds are added

- [ ] **Step 3: Write minimal implementation**

Add:

- one centered manifesto header
- one `readme-typing-svg` line set with philosophical short lines
- one restrained `github-readme-stats` card
- one optional compact skills line if it supports the page
- one snake embed using a dark/light `<picture>` block pointing at the `output` branch asset URLs

- [ ] **Step 4: Run test to verify it passes**

Run: `rg -n "readme-typing-svg|github-readme-stats|raw.githubusercontent.com/.*/github-snake" profile/README.md`
Expected: at least one match for each widget family and exit code `0`

- [ ] **Step 5: Commit**

```bash
git add profile/README.md
git commit -m "feat: add dynamic organization profile content"
```

### Task 3: Add contribution snake automation

**Files:**
- Create: `.github/workflows/generate-snake.yml`

- [ ] **Step 1: Write the failing test**

```bash
test -f .github/workflows/generate-snake.yml
```

- [ ] **Step 2: Run test to verify it fails**

Run: `test -f .github/workflows/generate-snake.yml`
Expected: exit code `1` because the workflow does not exist yet

- [ ] **Step 3: Write minimal implementation**

Create a workflow that:

- runs on schedule, workflow dispatch, and pushes to `main`
- uses `Platane/snk@v3`
- generates light and dark SVG variants into `dist/`
- publishes `dist/` to an `output` branch with `peaceiris/actions-gh-pages@v4`

- [ ] **Step 4: Run test to verify it passes**

Run: `test -f .github/workflows/generate-snake.yml`
Expected: exit code `0`

- [ ] **Step 5: Commit**

```bash
git add .github/workflows/generate-snake.yml
git commit -m "feat: automate contribution snake assets"
```

### Task 4: Verify README and workflow structure

**Files:**
- Modify: `profile/README.md` (only if verification finds issues)
- Modify: `.github/workflows/generate-snake.yml` (only if verification finds issues)

- [ ] **Step 1: Write the failing test**

```bash
ruby -e 'require "yaml"; YAML.load_file(".github/workflows/generate-snake.yml")'
```

- [ ] **Step 2: Run test to verify it fails**

Run: `ruby -e 'require "yaml"; YAML.load_file(".github/workflows/generate-snake.yml")'`
Expected: this fails before the workflow exists, then passes after Task 3 creates valid YAML

- [ ] **Step 3: Write minimal implementation**

If validation fails, fix YAML structure or malformed README embed URLs until:

- YAML loads successfully
- `profile/README.md` contains the expected owner/repo asset URLs
- the root `README.md` clearly points to `profile/README.md`

- [ ] **Step 4: Run test to verify it passes**

Run these commands:

```bash
ruby -e 'require "yaml"; YAML.load_file(".github/workflows/generate-snake.yml")'
rg -n "profile/README.md|organization profile" README.md
rg -n "Pixeldooooog/.github/output|github-readme-stats|readme-typing-svg" profile/README.md
git status --short
```

Expected:

- YAML command exits `0`
- `rg` commands exit `0`
- `git status --short` shows only the expected modified or new files before the final commit

- [ ] **Step 5: Commit**

```bash
git add README.md profile/README.md .github/workflows/generate-snake.yml docs/superpowers/specs/2026-04-10-pixeldog-profile-readme-design.md
git commit -m "feat: finalize github organization profile"
```
