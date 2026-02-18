# Claude Code Instructions

Read these files at repo root before doing anything:
- `PROJECT.yaml` — project config (stack, autonomy, conventions)
- Everything in `context/` — persistent project knowledge (design system, users, business rules)

PROJECT.yaml defines how you work. Context files define what you're building and for whom. These instructions reference both throughout.

---

## How Work Gets Assigned

Rachel plans with Claude Browser. They produce sprint docs that go in `docs/`:

```
docs/
├── sprint-3-milestone.md          # Overview: what this milestone achieves
├── sprint-3.1-repo-setup.md       # Detailed tasks for phase 1
├── sprint-3.2-access-config.md    # Detailed tasks for phase 2
├── ...
└── archive/                       # Completed sprints get moved here
```

When you receive work, it comes in one of two ways:

### Big jobs (Ralph Wiggum loop)
Rachel starts a ralph-loop pointed at `PLAN.md`. You work through PLAN.md top-to-bottom. Each task may reference a sprint doc: "Implement per docs/sprint-3.2-access-config.md". Read the sprint doc for the detailed spec, execute it, mark the PLAN.md task done.

### Small jobs (direct instruction)
Rachel tells you to execute a specific sprint doc: "Execute docs/sprint-4.1-calendar-fix.md". Read it, do what it says, commit when done. No PLAN.md involved.

For both: sprint docs are the source of truth for implementation details. They contain the code snippets, file paths, and acceptance criteria.

---

## Executing Sprint Docs

When working through a sprint doc:

1. Read the entire doc first — understand the full scope before starting
2. Follow the steps in order
3. Use the code snippets as-is unless they conflict with PROJECT.yaml conventions
4. Complete the doc's checklist at the end
5. Commit the work (see Git section below)
6. If the doc has issues (missing info, conflicting instructions), try your best interpretation. Note what you assumed in the commit message.

---

## Autonomy Mode

Check `PROJECT.yaml → autonomy`.

### If `full`:
- You CAN create and manage env vars via CLI tools (Vercel CLI, Supabase CLI)
- You CAN run `supabase init`, `vercel env add`, etc.
- You CAN push to the working branch without asking
- You CAN create `.env.local` with real values from CLI tools
- You CAN install packages and configure third-party services
- If branching is `dev-then-main`, you CANNOT push to main

### If `restricted`:
- You CANNOT touch env vars, secrets, or external services
- You CANNOT run CLI commands that create or modify external resources
- Create `.env.local` with placeholder values only
- Output `BLOCKED` with a list of what needs manual setup
- You CAN still write code, run builds, install npm packages, run tests

---

## Git Strategy

Check `PROJECT.yaml → branching`.

### If `dev-then-main`:
- Work on the `dev` branch. Create it if it doesn't exist: `git checkout -b dev`
- All commits go to `dev`
- Push to `dev` freely: `git push origin dev`
- NEVER push to `main` — Rachel merges when ready
- Vercel automatically creates preview deploys for dev pushes

### If `main-only`:
- Work directly on `main`
- Push when verified locally

### Commits

Check `PROJECT.yaml → commit_granularity`.

- `logical`: Commit when you've completed a meaningful, revertable chunk.
- `per-phase`: One commit per phase in PLAN.md.
- `per-task`: One commit per checkbox task.

Before every commit:
1. Review what you're staging — don't blindly `git add .`
2. Never commit `.env.local`, `.env`, or any file with secrets

Write clear commit messages:
```
Brief summary of what changed

- Specific change 1
- Specific change 2

Sprint: 3.2 (if applicable)
```

---

## Code Conventions

### File Size
- Max lines per file: check `PROJECT.yaml → max_file_lines`
- If a file exceeds this, split into logical sub-modules

### Naming
- Components: `PROJECT.yaml → component_naming` (PascalCase)
- Files: `PROJECT.yaml → file_naming` (kebab-case)
- Folders: `PROJECT.yaml → folder_naming` (kebab-case)

### Code Quality
- No unused imports or variables
- No commented-out code (delete it, git has history)
- No swallowed errors — handle or throw
- Remove debug console.logs before committing

### Static HTML Conventions (ai-for-all specific)
- All pages should link the shared `styles.css` for base design tokens
- Page-specific styles go in a `<style>` block in that page's `<head>`
- Don't duplicate CSS variables — they live in `styles.css :root`
- Use the design system tokens from `context/design-system.md`
- All public-facing pages share the same nav and footer structure
- Internal/planning pages use `<meta name="robots" content="noindex, nofollow">`

---

## Sprint Doc Archiving

When a sprint milestone is fully complete (all sub-sprints done, all checklists passed):
- Move the milestone doc and all its sub-sprint docs to `docs/archive/`
- Don't delete them — they're useful history

---

## Repo Hygiene

### .gitignore
Always ignore:
- `.DS_Store`
- `docs/` (sprint docs are local only)
- `*.log`
- `.env*` (if any env files exist)

### Clean Up
- Delete starter/boilerplate files you're not using
- Remove placeholder files once real content replaces them
- Don't leave TODO comments in code — track tasks in sprint docs or PLAN.md

---

## Handling Blockers

If you hit something you can't resolve:

1. Try 3 different approaches
2. If all 3 fail, output BLOCKED
3. Include:
   - What task you're stuck on
   - What you tried (all 3 approaches)
   - What you think the issue is
   - What Rachel would need to do to unblock you

---

## What You Never Do

- Never commit `.env.local` or any secrets
- Never modify `PROJECT.yaml` or `CLAUDE.md` unless explicitly told to
- Never modify files in `context/` unless explicitly told to
- Never install packages outside of project needs
- Never modify files outside the repo directory
- Never run destructive commands unless it's an explicit task
- Never ignore build errors — fix them before moving on
