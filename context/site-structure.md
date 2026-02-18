# AI for All — Site Structure

## Deployment

- **Hosting:** Vercel
- **URL:** https://ai-for-all.vercel.app
- **Repo:** https://github.com/rramkhel/ai-for-all
- **Deploy trigger:** Auto-deploy on push to `main`

## Page Map

### Public Pages (linked from main nav)

| Page | File | Purpose |
|------|------|---------|
| Home | `index.html` | Program overview, timeline, stats |
| Calendar | `calendar.html` | Session schedule with timeline + calendar toggle views |
| Survey | `survey.html` | Tally survey embed for member preferences |
| Resource Hub | `hub/index.html` | Password-protected participant resources (login page) |

### Hub Pages (behind password gate)

| Page | File | Purpose |
|------|------|---------|
| Hub Home | `hub/index.html` | Hub landing / login |
| AI Ally Setup | `hub/ally-setup.html` | Guide for configuring AI assistant |
| Business Profile | `hub/business-profile.html` | Template for business context document |
| Guardrails | `hub/guardrails.html` | AI usage policies and safety guidelines |
| Prompt Builder | `hub/prompt-builder.html` | Interactive prompt crafting tool |
| Resources | `hub/resources.html` | Curated links and materials |
| Sector Packs | `hub/sector-packs.html` | Industry-specific AI toolkits |

### Internal/Planning Pages (not in nav, noindex)

| Page | File | Purpose |
|------|------|---------|
| Planning Hub | `planning/index.html` | Team coordination dashboard |
| Session 1 Review | `planning/session-1/review.html` | Session 1 review materials |
| Demo A: NotebookLM | `planning/session-1/demo-a-notebooklm.html` | NotebookLM demo playbook |
| Demo C: Gemini | `planning/session-1/demo-c-gemini.html` | Gemini demo playbook |

### Assets

| File | Purpose |
|------|---------|
| `styles.css` | Shared design system (tokens, base components) |
| `robots.txt` | Search engine directives |
| `planning/session-1/canada-alberta-logo.png` | Government funder logo |

## Navigation Structure

Main nav (all public pages): Home | Calendar | Survey | Resource Hub

Hub pages have their own internal nav within the hub.

Planning pages are standalone — accessed via direct URL only.

## Authentication

- Hub pages use a simple client-side password gate (not server-side auth)
- Planning pages are unlisted with `noindex` meta tags — security through obscurity
