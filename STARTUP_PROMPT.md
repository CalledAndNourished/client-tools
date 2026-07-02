# CALLED AND NOURISHED — CLIENT TOOLS — SESSION STARTUP PROMPT
*Updated July 2, 2026*

---

## HOW TO START A SESSION

**Step 1 — Upload this file first.**

**Step 2 — Tell Claude what you need:** build a new tool, update an existing one, fix branding, or something else.

**Step 3 — For any new tool, Claude should read the branding section below before writing any code**, so it matches the existing tools without you having to re-specify colors/fonts/logo each time.

Repository: **github.com/CalledAndNourished/client-tools** (public)
Live site: **https://calledandnourished.github.io/client-tools/**

---

## WHAT THIS REPO IS

Public, client-facing interactive tools for the Called and Nourished nutrition practice — calculators and trackers a client or Pamela can use directly in a browser, no login, no data saved between visits. This is separate from:
- `called-and-nourished` — the YouTube channel content repo (private)
- `pamela-clinical-practice` — patient case files and clinical reference (private)

**This repo must stay public** for GitHub Pages to work on the free tier. For that reason: **never put patient data, real client names, or anything clinical/confidential in this repo.** Tools here should only ever be generic calculators — no data persistence, no accounts, nothing that could leak between users.

---

## CLAUDE BEHAVIOR RULES (same as the other two repos)
1. Read a file before and after every update; verify content is complete after any push.
2. Never omit, condense, shorten, or delete content without explicit permission.
3. Always ask before acting — especially before overwriting an existing tool.
4. **Check for parallel-session conflicts before building anything new.** This repo has already had one instance of a tool (`bmr-macro-calculator`) being built independently in a separate session while another session was mid-conversation about the same feature. Before starting new work, look at what's already in the repo — don't assume a blank slate.
5. GitHub Pages is enabled (Settings → Pages → Source: Deploy from branch → `main` → `/ (root)`). This is already configured — do not need to re-enable it.
6. The GitHub connector cannot create new repositories. If a future session needs a new repo, ask Pamela to create it empty via the GitHub UI first, then push files into it.

---

## BRANDING — apply to every tool automatically, don't ask each time

**Colors:**
| Name | Hex | Use |
|---|---|---|
| Warm cream | `#F5EFE0` | page background |
| Paper white | `#FFFFFF` | card backgrounds |
| Deep forest green | `#2D4A2D` | primary accent, buttons, headers |
| Teal-deep | `#1F331F` | eyebrow text, darker accent |
| Burnished gold | `#C9A84C` | secondary accent |
| Terracotta | `#A0522D` | alert/warning states |
| Ink | `#2D2A22` | body text |
| Ink-soft | `#746B54` | secondary/muted text |
| Line | `#DCD0AE` | borders |

**Typography (Google Fonts):**
- Headings: `Source Serif 4` (weight 600–700)
- Body: `Work Sans` (weight 400–600)
- Numbers/data/labels: `IBM Plex Mono` (weight 500–600) — used for the "nutrition label" data feel

**Visual identity:** warm, calm, credible — evokes a nutrition-label aesthetic (thick rules, small-caps mono labels) rather than a sterile medical or generic SaaS look. Mobile-first, single-column, max-width ~480–520px centered.

**Logo:** circular Called and Nourished logo, embedded as base64 PNG (~85KB compressed from original) directly in each tool's `<img>` tag so every tool is a single self-contained file with no external image dependency. The base64 string is already present in `index.html`, `carb-choice-converter/index.html`, and `bmr-macro-calculator/index.html` — **copy it from any existing file rather than asking Pamela to re-upload the logo.**

---

## REPOSITORY STRUCTURE

```
index.html                          ← landing page, lists all tools as cards
carb-choice-converter/
└── index.html                      ← Carb Choice Converter (see below)
bmr-macro-calculator/
└── index.html                      ← BMR & Macro Calculator (see below)
test.png                            ← stray leftover test file at repo root, not part of any tool — consider removing, ask before deleting
```

**Pattern for adding a new tool:**
1. Build the tool as a single self-contained HTML file (inline CSS + JS, logo as embedded base64).
2. Push it to a new folder: `new-tool-name/index.html`.
3. Add a new card to the `.tools` div in root `index.html` linking to `new-tool-name/`.
4. No other setup needed — GitHub Pages picks it up automatically once pushed to `main`.

---

## TOOLS CURRENTLY LIVE

### 1. Carb Choice Converter
**Path:** `carb-choice-converter/index.html`
**URL:** `https://calledandnourished.github.io/client-tools/carb-choice-converter/`

- Bidirectional converter: grams of carbohydrate ↔ carb choices (15g = 1 choice)
- Built-in quick-reference food list (grains, fruit, dairy, starchy/non-starchy vegetables)
- Same-day food log: add entries, running total in grams and choices
- Optional daily target with live "remaining" / "over target" feedback
- No data persistence — resets on page reload by design

### 2. BMR & Macro Calculator
**Path:** `bmr-macro-calculator/index.html`
**URL:** `https://calledandnourished.github.io/client-tools/bmr-macro-calculator/`

Practitioner-facing tool for building a client's starting macro targets. Formulas:
- **BMR:** Mifflin-St Jeor equation (weight in kg, height in cm, age, sex)
- **TDEE:** BMR × activity factor (Sedentary 1.2 / Light 1.375 / Moderate 1.55 / Active 1.725 / Extra 1.9)
- **IBW:** Devine formula (primary, used for protein calc) shown alongside Hamwi formula (reference only)
- **Protein:** 1.2 g per kg IBW (Devine)
- **Fat:** 30% of TDEE
- **Carbohydrate:** remainder of TDEE after protein and fat calories
- **Fiber:** fixed 35g minimum — counted *within* the carb total, not added on top
- Includes a warning state if protein + fat calories alone exceed TDEE (carb would go negative)

---

## OPEN ITEMS
1. `test.png` at repo root — stray file, not linked from anywhere, ask Pamela before removing
2. No tools beyond the two above yet — landing page has a "More tools coming soon" note that should be removed once a third tool is added, or kept if it reads fine indefinitely
3. Consider whether `bmr-macro-calculator` should eventually get a data-log feature similar to the carb converter's same-day log, if that becomes useful in practice

---

## KNOWN CONTEXT FROM PRIOR SESSIONS
- Pamela's clinical practice logo file was uploaded once (`Circle_logo_sm.png`, ~1.7MB original) and resized to ~85KB for embedding. No need to re-upload — reuse the base64 already in any existing tool.
- GitHub Pages took a few minutes to go live on first setup; subsequent pushes update instantly, no re-configuration needed.
- Pamela sometimes runs multiple Claude sessions concurrently across her repos — always check current repo state before assuming what exists.

---

*Called and Nourished | Client Tools | www.calledandnourished.com*
