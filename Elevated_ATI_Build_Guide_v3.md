# Elevated ATI Suite — Definitive Build Guide v3

**Generated:** 2026-05-13 (revised from v2: 2026-05-12)
**Source of truth:** the working MN, PD, and Pharm suites — all three are now feature-complete.
**Coverage:** every feature, every design token, every subsystem, every breakpoint.

This guide is meant to be re-uploaded at the start of any new build session. With this in context, I can rebuild any subject suite to match the existing ones without inferring patterns from existing files.

---

## CHANGES SINCE v2

**Pharm suite completed (all three sub-files now feature-complete):**
- 49 chapters, all with Active Learning Scenarios (no skipped chapters; ch3 has a custom dose-calc scenario; ch5 has a bonus ALS-2 on warfarin + St. John's wort)
- 50 worked templates across 5 used template types (Medication 41, System Disorder 3, Nursing Skill 3, Therapeutic Procedure 2, Basic Concept 1)
- **260 flashcards** (98 typed mid-prompts + 162 inline mid-reads), shares `nur2460_fc_schedule` with MN

**Inline mid-reads — new pattern documented:**
- Variable-density approach: Heavy chapters get 4–5 cards, standard 3, light 2.
- Native `data-fc-type="priority"` discovered and documented (red border, highest-urgency styling).
- See new section **§7.X Inline mid-reads** below.

**Theme key unified across all 13 files:**
- Canonical key: `nur2460_theme` (used by all Hubs, Books, Templates, Flashcards, and index.html).
- Salvage migrations in place for legacy keys (`elevated_theme`, `atipd_theme`, `nur2460_pharm_theme`).
- Books and Templates now persist theme (previously they had toggle buttons but didn't save state).
- See updated section **§3.4 Theme switching** and **§C.3.x Theme unification**.

**Ch5 (Pharm) cleanup:**
- Pharm ch5 had two complete content sets from earlier source-document handling. H2 headings now disambiguated; no content removed; no IDs touched.
- See new section **§H.3.3.5 Ch5 dual-content note**.

**index.html updated:**
- PD and Pharm placeholder dashes replaced with real stats.
- Whole-suite totals: **120 chapters · 369 worked templates · 741 flashcards.**

**Whole-suite snapshot:**

| Subject | Chapters | Templates | Cards (typed + inline) | Theme key | Schedule key |
|---|---:|---:|---:|---|---|
| MN | 27 | 152 | 122 (0 typed + 122 inline)* | nur2460_theme | nur2460_fc_schedule |
| PD | 44 | 167 | 359 (? typed + ? inline)* | nur2460_theme | atipd_fc_schedule |
| Pharm | 49 | 50 | 260 (98 typed + 162 inline) | nur2460_theme | nur2460_fc_schedule (shared with MN) |
| **Total** | **120** | **369** | **741** | — | — |

\* MN's cards predate the "typed + inline" distinction; treat as inline equivalent for the catalog model.

---


---


## TABLE OF CONTENTS

```
PART 0  — Non-negotiable principles
PART 1  — File inventory (5 files per suite)
            1.1 Cross-file data flow
PART 2  — Architecture
            2.1 Key design decisions (and why they matter)
PART 3  — Visual design system
            3.1 Typography
            3.2 Color tokens (all 29 CSS variables, both modes)
            3.3 Shadows, radii, spacing, transitions
            3.4 Theme switching (data-theme="light")
            3.X Light-mode color contrast verification
PART 4  — Responsive design & mobile behavior
            4.1 Breakpoints (900px primary, 600px secondary)
            4.2 Mobile sidebar (hamburger + overlay + translateX)
            4.3 Mobile back-home button
            4.4 Touch targets and tap behavior
            4.5 Modal on mobile
            4.6 Tab strip scrolling
            4.X iOS Safari quirks
PART 5  — index.html
            5.X Index-page cross-subject view notes
PART 6  — Subject Hub
            6.1 Document structure
            6.2 Hero
            6.3 Stats row
            6.4 Pickup panel
            6.5 Primary grid (3 tool cards)
            6.6 Units grid
            6.7 Template types grid
            6.8 Storage panel (export/import/reset)
            6.9 Full Hub function catalog
            6.X Backup & recovery procedure
PART 7  — Book file
            7.1 Document structure
            7.2 Sidebar
            7.3 Main content
            7.4 Chapter-pool pattern
            7.5 Chapter content structure
            7.6 Modal mechanism
            7.7 Brief-card (TL;DR)
            7.8 Content sections & condition blocks
            7.9 Inline mid-read prompts (3 types + target density spec)
            7.10 Injected typed prompts (4 types: CONTENT/JUDGMENT/PRINCIPLE/PRIORITY)
            7.11 Active Learning Scenario (ALS)
            7.12 Exercises with NCLEX filter
            7.13 Templates bridge
            7.14 Bookmarks system
            7.15 Search system
            7.16 Abbreviation tooltips (277 entries)
            7.17 Print/PDF overlay
            7.18 Cross-tool sync
            7.19 Sidebar nav with collapsible units
            7.20 Reading progress tracking (3-state checkboxes)
            7.21 Full function catalog (49 functions)
            7.22 Reference template — full chapter skeleton
            7.23 Reference data — full ABBR_DICT (277 entries)
            7.24 Reference data — full MID_PROMPTS (54 prompts)
            7.X Cross-link map (Book ↔ Templates)
            7.X Procedure — add a new abbreviation
PART 8  — Templates file
            8.1 Document structure
            8.2 Template-pool (with template-section wrappers)
            8.3 The 8 template types
            8.4 Example cards
            8.5 Filled/Blank toggle (per-card, canonical)
            8.6 Template filter system (canonical state shape)
            8.7 Example modal
            8.8 Per-template & master print
            8.9 Navigator list per accordion (canonical)
            8.10 Per-example studied checkboxes
            8.11 Full function catalog
            8.12 Reference templates — one per template type
            8.X Procedure — add a new template type
PART 9  — Flashcards file
            9.1 Document structure
            9.2 Deck stats
            9.3 SM-2 algorithm
            9.4 Card rendering (.flashcard- prefix, canonical)
            9.5 Card styling (.flashcard-* CSS)
            9.6 Keyboard shortcuts
            9.7 Session timer
            9.8 Tabs (Review vs Browse)
            9.9 Filter system
            9.10 Full Flashcards function catalog
PART 10 — CSS reference
            10.1 :root CSS variables (29 total)
            10.2 Theme attribute switching
            10.3 Master CSS structure
            10.4 Modifier classes (the state machine)
            10.5 Key naming convention (canonical)
            10.6 Example-card CSS reference
PART 11 — JavaScript reference (every function categorized)
PART 12 — LocalStorage schema (every key, every data shape, every subject)
PART 13 — Subject porting
            13.1 PDF → finished suite (high-level)
            13.2 Build sequence (8 phases)
            13.3 Per-subject variation table
            13.4 Chapter completeness checklist
            13.5 Validation script (Python)
            13.6 JS lint check
            13.7 What NOT to do
            13.8 Porting-leak categories
            13.9 Per-file leak inventory
            13.10 Porting checklist (run for every new subject)
            13.11 Static vs dynamic gotcha
            13.12 Sweep script
            13.X Quality assurance checklists
            13.X PDF extraction tooling
            13.X Procedure — add a new chapter
            13.X Procedure — production deployment
            13.X User flow walkthroughs
            13.X Testing on actual devices
PART 14 — Editorial standards
            14.1 Content-writing voice guide
            14.2 Mid-prompt selection rubric
            14.3 NCLEX question rubric
PART 15 — Common pitfalls
            15.1–15.12 (original 12 failure modes)
            15.X Overarching lesson from the PD port
            15.X Edge cases — chapter structure / templates / flashcards / UI / data integrity
            15.X Subject deviation log
            15.X Procedure — update existing content without breaking user data
            15.X Subject-specific structural variations
PART 16 — Quick reference cheatsheet

APPENDIX G — UNCERTAINTY LOG
```

---

## PART 0 — NON-NEGOTIABLE PRINCIPLES

Before any code:

1. **MN is the basis.** Every other suite must structurally match MN. Same section count per chapter, same patterns, same CSS classes, same JS conventions. Deviation is a bug.

2. **Every chapter MUST have:** `chN-tldr` (brief-card), 2-7 `content-section` sections, `chN-als` (Active Learning Scenario; MN has it on 24/27), `chN-exercises` (5 NCLEX Qs), `chN-templates` (tpl-bridge). Each is a direct `<section>` child with an `id` — that's what makes it a modal tab.

3. **The chapter-pool pattern is fixed.** All chapter content lives in `<div class="chapter-pool" id="chapterPool">` with `display: none`. Chapters never render directly — JS clones them into a modal when opened. Breaking the pool's div nesting causes orphan content to leak as visible text.

4. **Cross-link bi-directionally.** Book→Templates: every chapter has a `tpl-bridge` section listing relevant templates. Templates→Book: every example-card has an `.ex-jump` link back to the source chapter (or ALS).

5. **Tag-balance after every chapter edit.** Count `<div>` opens vs `</div>` closes. Count `<section>` opens vs `</section>` closes. Mismatch → chapter pool closes early → all subsequent chapters render as visible text on the page.

6. **Validate JS after every script change.** Each inline `<script>` block must pass `node --check`. A single broken script breaks the entire modal mechanism. There are exactly **3 inline `<script>` blocks** in MN Book, in this order:
   - Script 1: Main book IIFE `(function(){...})()`
   - Script 2: BATCH 3 — NCLEX filter + answered tracking
   - Script 3: Mid-read flashcard prompts

7. **Subject-namespace localStorage keys.** See PART 12 for the actual scheme — it's more complex than a simple prefix.

---

## PART 1 — FILE INVENTORY

A full subject suite is **5 files**. There is also one top-level `index.html`.

| File | Purpose | MN size | PD size | Pharm size |
|---|---|---|---|---|
| `index.html` | Top-level landing — 3 subject cards | 11.5 KB | — | — |
| `Elevated ATI {Subject} Hub.html` | Per-subject landing | 37.2 KB | 36.9 KB | 40.9 KB |
| `Elevated ATI {Subject} Book.html` | Chapter reference (TL;DR + content + ALS + exercises + bridge) | 1,570 KB | 1,070 KB | 647 KB |
| `Elevated ATI {Subject} Templates.html` | Worked Active Learning Template examples | 1,250 KB | 1,578 KB | — (not yet built) |
| `Elevated ATI {Subject} Flashcards.html` | SM-2 spaced repetition deck | 122 KB | 153 KB | — (not yet built) |

`{Subject}` is `MN`, `PD`, or `Pharm` (exactly that capitalization in filenames).

**Naming conventions:**
- Spaces in filenames → URL-encoded as `%20` in hrefs (e.g., `Elevated%20ATI%20MN%20Book.html`)
- IDs use lowercase + hyphens
- Chapter IDs: `ch1` through `chN`
- Chapter-section IDs within a chapter: `ch{N}-{topic}` (e.g., `ch1-tldr`, `ch1-natural`, `ch1-als`, `ch1-exercises`, `ch1-templates`)
- Template example IDs: `ex-ch{N}-{topic}` (e.g., `ex-ch1-cocs`, `ex-ch3-skin-breast`)
- Flashcard IDs: `fc-ch{N}-{topic}` for inline asides; `ch{N}-p1`/`ch{N}-p2` for typed injected prompts

### 1.1 Cross-file data flow

The 4 subject files cross-reference each other and share state through `localStorage`. Every file is single-page HTML with inline `<style>` and `<script>` tags. No external dependencies other than Google Fonts (DM Serif Display + DM Sans).

This is what each file READS from and WRITES to (verified against MN as of 2026-05-12):

```
                 BOOK                  TEMPLATES              FLASHCARDS               HUB
   ─────────────────────────  ─────────────────────  ─────────────────────  ──────────────────
   writes:                    writes:                writes:                writes:
     atimn_progress             atimnTemplates_        fc_schedule            theme
     fc_schedule                  progress             fc_filters             pickup_dismissed
     last_chapter               tpl_filters            theme                    (sessionStorage)
     bookmarks                  last_template
     nclex_done

   reads:                     reads:                 reads:                 reads:
     (its own writes)           (its own writes)       (its own writes)       atimn_progress
     theme                      theme                                          atimnTemplates_
                                                                                progress
                                                                              fc_schedule
                                                                              theme
                                                                              last_chapter
                                                                              last_template
```

**Key cross-file relationships:**
- **`fc_schedule`** is shared between Book and Flashcards. When user rates a mid-prompt in Book, it adds to the same SM-2 schedule that Flashcards reads from. The two files are different views of the same review deck.
- **`theme`** is shared across all 4 files. Toggling theme in any file affects all (after page reload of the others). All 4 files BOTH read AND write this key.
- **`last_chapter` and `last_template`** are "pickup pointers" written by Book/Templates respectively; read only by Hub for the "pick up where you left off" panel.
- **`pickup_dismissed`** lives in sessionStorage (not localStorage) — Hub's pickup-panel dismissal lasts one tab session only.

All other keys are owned by a single file.

For the full localStorage key reference (including PD's isolated `atipd_*` namespace), see PART 12.

---

## PART 2 — ARCHITECTURE

```
                          ┌──────────────┐
                          │ index.html   │  (top-level: 3 subject cards)
                          └──────┬───────┘
                                 │
              ┌──────────────────┼──────────────────┐
              ▼                  ▼                  ▼
        ┌──────────┐       ┌──────────┐       ┌──────────┐
        │   MN     │       │   PD     │       │  Pharm   │
        │   Hub    │       │   Hub    │       │   Hub    │
        └─────┬────┘       └─────┬────┘       └─────┬────┘
              │                  │                  │
       ┌──────┼──────┐    ┌──────┼──────┐    ┌──────┼──────┐
       ▼      ▼      ▼    ▼      ▼      ▼    ▼      ▼      ▼
     Book Templates FC  Book Templates FC  Book Templates FC
       ▲     ▲                                   ▲     ▲
       │     │                                   │     │
       └─────┴── cross-links (Book↔Templates) ───┴─────┘
                 cross-tool sync via localStorage
```

Each Book/Templates/Flashcards page has:
- A 280px-wide left sidebar (collapsible to off-screen on mobile via hamburger)
- Main content area
- Theme toggle (☀️/🌙) in sidebar header
- "Back to Hub" link in sidebar header AND a mobile-only floating "Back to Hub" button
- Shared color scheme via CSS variables
- LocalStorage progress that the Hub's pickup panel reads to show "where you left off"

### 2.1 Key design decisions (and why they matter)

A few non-obvious architectural choices in the MN model. Understanding these prevents accidental regressions during porting.

**Chapter-pool pattern (vs. lazy load):** The chapter-pool has ALL chapter content inline in the HTML, hidden by `display:none`. Click → clone → modal. This simplifies modal mechanics (no async load), makes search work across all chapters, and makes print work without coordination. Cost: the Book file is large (1.5 MB for MN).

**Two kinds of mid-prompts (inline vs typed):** Two parallel systems coexist — **Inline mid-reads** declared as `<aside class="mid-read">` in HTML body content, and **typed mid-prompts** declared as JS data in `MID_PROMPTS`, injected dynamically. Why two: inline allows hand-placing the prompt mid-paragraph for narrative flow (more "narrative integration"); typed allows structured per-chapter prompt management with a selection rubric (more "systematic coverage"). Both share the SAME SM-2 schedule.

**Per-card mode toggle (Templates):** MN Templates puts the Filled/Blank toggle on EACH card (vs a global body toggle). Lets the user toggle individual cards independently — useful for self-quizzing one card while keeping others as reference. The global toggle pattern (which an earlier version of this guide originally documented) was actually a design step BACK from MN's actual implementation; see PART 8.5 for the canonical per-card design.

**Modal-clone vs persistent DOM:** When you open a chapter, the modal CLONES the content from the pool rather than moving it. Why: searches still work across the whole pool while a modal is open; back button doesn't lose state; multiple opens don't fight each other.

**Why the storage panel lives only on Hub:** The Hub is the only "settings" page. Other pages don't have a storage UI because Hub is the canonical place to manage state. Backup/restore via Hub is the supported workflow.

**Why namespace decisions matter:** `nur2460_*` (MN's namespace, also used by Pharm by design) means MN+Pharm share theme, flashcard schedule, and bookmarks. A user studying both subjects sees their unified state. PD opted for `atipd_*` (isolation) — PD's data doesn't appear in MN's view. This was a one-time design choice per subject; changing it after data exists requires migration.

---

## PART 3 — VISUAL DESIGN SYSTEM

### 3.1 Typography

**Fonts loaded** (Google Fonts):
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
```

**Body default:**
```css
body {
  font-family: 'DM Sans', sans-serif;
  /* font-size set on html: ~15px; line-height 1.55-1.6 throughout */
  transition: background 0.25s, color 0.25s;
}
```

**Serif display** (used only for major headings):
```css
.main-title,
.modal-title,
.chapter-name,
.condition-name,
.brief-card h2,
h1, h2 {
  font-family: 'DM Serif Display', serif;
  font-weight: 400;  /* the serif is intentionally light */
  letter-spacing: -0.005em;
}
```

**Font size scale** (every size used in MN Book):
```
8px   — micro labels (rarely used)
9px   — tiny eyebrow text
10px  — uppercase eyebrows ("UNIT 1", "NCLEX CATEGORY")
10.5px — tab labels in modal-tabs
11px  — micro tags, NCLEX tags, condition-tags
12px  — small UI text, q-num, tab buttons, type badges
13px  — sidebar items, footer text
13.5px — sidebar-item with item-name
14px  — secondary body text
14.5px — section leads, exercise rationales
15px  — primary body text (default)
15.5px — emphasized body
16px  — slightly larger body (kb-card)
17px  — TL;DR paragraph
18px  — sidebar title, hamburger icon
20px  — condition-name (h3 in content)
22px  — brief-card h2, section h2 in main
24px  — main subtitle
26px  — modal-title on mobile
28px  — modal-title default
30px  — chapter-banner h2 (consumed by modal)
32px  — large heading
34px  — chapter banner h1 in modal
42px  — main-title fallback
44px  — main-title default (DM Serif Display)
```

**Heading weights:**
- All `DM Serif Display` headings: `font-weight: 400` (the font itself is light/elegant)
- All `DM Sans` headings: `font-weight: 600` for h3-h4; `font-weight: 700` for eyebrows/uppercase
- Body text: `font-weight: 400` default; `font-weight: 600` for `<strong>`

### 3.2 Color tokens (CSS variables)

All 29 variables defined on `:root` (dark mode = default):

```css
:root {
  /* Backgrounds */
  --bg: #0f1117;              /* page background */
  --surface: #181c27;         /* cards, panels */
  --surface2: #1e2336;        /* nested surfaces */
  --surface3: #242a40;        /* tertiary, deeper */

  /* Borders */
  --border: #2a3050;          /* visible borders */
  --border-soft: rgba(255,255,255,0.06); /* subtle dividers */

  /* Subject accent (THIS is what differs per subject) */
  --accent: #fbbf24;          /* MN: amber-yellow */
  --accent2: #fcd34d;         /* lighter accent for hovers/secondary */
  --accent-soft: rgba(251,191,36,0.12);  /* faded background tint */
  --accent-stripe-bg: rgba(251,191,36,0.25);  /* for highlight stripes */

  /* Text */
  --text: #e8eaf2;            /* primary body text */
  --text2: #8b92b8;            /* secondary, captions */
  --text3: #555e85;            /* tertiary, hints */

  /* FHR pattern colors (used in maternal-newborn content) */
  --reassuring: #3db87a;       /* green — reassuring FHR */
  --reassuring-bg: rgba(61,184,122,0.10);
  --indeterminate: #e8a838;    /* yellow — indeterminate FHR */
  --indeterminate-bg: rgba(232,168,56,0.10);
  --nonreassuring: #e05c6a;    /* red — nonreassuring FHR */
  --nonreassuring-bg: rgba(224,92,106,0.10);

  /* 4 ATI clinical-judgment prompt colors */
  --prompt-content: #4fa3e0;       /* blue — CONTENT (factual) */
  --prompt-content-bg: rgba(79,163,224,0.10);
  --prompt-judgment: #a78bfa;      /* purple — JUDGMENT (decision) */
  --prompt-judgment-bg: rgba(167,139,250,0.10);
  --prompt-principle: #14b8a6;     /* teal — PRINCIPLE (rationale) */
  --prompt-principle-bg: rgba(20,184,166,0.10);
  --prompt-priority: #ef4444;      /* red — PRIORITY (urgency) */
  --prompt-priority-bg: rgba(239,68,68,0.10);

  /* Special-purpose */
  --nav-bg: rgba(15,17,23,0.92);   /* sticky nav backdrop */
  --shadow: 0 8px 24px rgba(0,0,0,0.3);
}
```

**Light mode** override (toggled via `[data-theme="light"]` attribute on `<html>`, NOT a class):

```css
[data-theme="light"] {
  --bg: #faf7f2;              /* warm cream/paper */
  --surface: #f4f0e8;
  --surface2: #ece6d8;
  --surface3: #e3dccc;
  --border: #d6ccb8;
  --border-soft: rgba(0,0,0,0.07);

  /* Light mode uses DIFFERENT accent colors (deliberate reading aesthetic) */
  --accent: #ea580c;          /* burnt orange (replaces amber) */
  --accent2: #0f766e;          /* teal (replaces yellow) */
  --accent-soft: rgba(13,148,136,0.10);
  --accent-stripe-bg: rgba(13,148,136,0.20);

  --text: #1e1c18;
  --text2: #5a5448;
  --text3: #9e9080;

  --reassuring: #1a9157;
  --reassuring-bg: rgba(26,145,87,0.10);
  --indeterminate: #b87418;
  --indeterminate-bg: rgba(184,116,24,0.10);
  --nonreassuring: #c0384a;
  --nonreassuring-bg: rgba(192,56,74,0.10);

  --nav-bg: rgba(250,247,242,0.92);
  --shadow: 0 8px 24px rgba(0,0,0,0.10);
}
```

**Subject-specific accent palettes** (the only thing that differs between subjects):

```css
/* MN — dark mode */
--accent: #fbbf24;   /* amber-400 */
--accent2: #fcd34d;  /* amber-300 */
--accent-soft: rgba(251,191,36,0.12);

/* PD — dark mode */
--accent: #60a5fa;   /* blue-400 */
--accent2: #93c5fd;  /* blue-300 */
--accent-soft: rgba(96,165,250,0.12);

/* Pharm — dark mode */
--accent: #fb923c;   /* orange-400 */
--accent2: #fdba74;  /* orange-300 */
--accent-soft: rgba(251,146,60,0.12);
```

**index.html palette** (its own — uses PURPLE as primary accent + 3 subject colors):

```css
:root {
  --accent: #a78bfa;           /* purple-400 for hub itself */
  --accent2: #c4b5fd;
  --mn-color: #fbbf24;          /* amber for MN card */
  --pd-color: #38bdf8;          /* sky-400 for PD card */
  --pharm-color: #fb923c;       /* orange-400 for Pharm card */
}
```

### 3.3 Shadows, radii, spacing, transitions

**Shadow scale** (used throughout):
```css
/* Subtle (cards at rest) */
box-shadow: 0 1px 3px rgba(0,0,0,0.04);
box-shadow: 0 1px 4px var(--accent-soft);

/* Standard (raised cards, popovers) */
box-shadow: 0 8px 24px rgba(0,0,0,0.2);

/* Modal */
box-shadow: 0 12px 40px rgba(0,0,0,0.3);
box-shadow: 0 20px 60px rgba(0,0,0,0.4);  /* main chapter modal */

/* Focus ring */
box-shadow: 0 0 0 2px var(--accent), 0 2px 8px rgba(0,0,0,0.2);

/* Strong focus (accessibility) */
box-shadow: 0 0 0 2px var(--accent), 0 0 0 8px var(--accent-soft);

/* Tab strip edge fades (indicates scrollable) */
box-shadow: inset 70px 0 30px -20px rgba(0,0,0,0.15);   /* left fade */
box-shadow: inset -70px 0 30px -20px rgba(0,0,0,0.15);  /* right fade */
/* In dark mode, opacity is 0.45 instead of 0.15 */
```

**Border-radius scale:**
```
2px   — tightest (small badges, tags)
3px   — small UI accents
4px   — micro-pills (nclex-tag)
5px   — small UI elements
6px   — sidebar items, tab corners, small buttons
7px   — medium-small
8px   — buttons, search input, hamburger
10px  — finding-card, content cards
12px  — exercises, mid-prompts, modals on mobile
14px  — brief-card, unit-accordion, kb-card
16px  — main modal
50%   — circles (icons, avatars)
99px  — fully-pill-shaped (progress bars, condition-tags rarely)
```

**Spacing scale** (most-used values; ad-hoc but consistent):
```
2px   — tightest gap
4px   — micro spacing (chip gaps)
6px   — small inline gaps
8px   — standard small gap
10px  — moderate spacing
12px  — card internal padding tight
14px  — card padding standard
16px  — section internal padding
18px  — header padding
20px  — card padding generous (mid-prompts)
22px  — modal-header bottom padding
24px  — grid gap large, modal padding-x
28px  — brief-card padding
32px  — main content padding-x
36px  — main-content padding-top
40px  — bottom-of-section spacing, modal padding-y on overlay
48px  — between content-sections
60px  — main-content padding-bottom on mobile
80px  — main-content padding-bottom on desktop
116px — sidebar-header top padding on mobile (clears floating buttons)
124px — main-content top padding on mobile (clears floating buttons)
```

**Transitions** (timing values used):
```css
/* Color/background changes */
transition: background .12s, color .12s;
transition: color .15s;
transition: border-color .15s ease;

/* General interactions */
transition: all .15s;
transition: all 0.15s ease;
transition: background .15s;
transition: box-shadow .15s ease;

/* Larger movements */
transition: transform 0.25s, background 0.2s;  /* sidebar slide */
transition: opacity .25s;                       /* overlay fade */
```

### 3.4 Theme switching mechanism

**The theme toggle uses an attribute, not a class:**

```javascript
var THEME_KEY = 'nur2460_theme';  // UNIFIED across all 13 files in the suite (v3). Salvage migrations are in place for legacy keys: 'elevated_theme' (old index.html), 'atipd_theme' (old PD), 'nur2460_pharm_theme' (intermediate Pharm). PD's other localStorage keys remain 'atipd_*' (only theme is shared).

function applyThemeUI() {
  var isLight = document.documentElement.getAttribute('data-theme') === 'light';
  if (themeIcon)  themeIcon.textContent  = isLight ? '🌙' : '☀️';
  if (themeLabel) themeLabel.textContent = isLight ? 'Dark Mode' : 'Light Mode';
}

// Toggle:
document.getElementById('themeToggle').addEventListener('click', function() {
  var isLight = document.documentElement.getAttribute('data-theme') === 'light';
  var next = isLight ? 'dark' : 'light';
  if (next === 'dark') document.documentElement.removeAttribute('data-theme');
  else document.documentElement.setAttribute('data-theme', 'light');
  localStorage.setItem(THEME_KEY, next);
  applyThemeUI();
});

// On page load: apply saved theme
(function() {
  var saved = localStorage.getItem(THEME_KEY);
  if (saved === 'light') document.documentElement.setAttribute('data-theme', 'light');
  applyThemeUI();
})();
```

**Theme HTML controls** (in sidebar header):
```html
<button id="themeToggle" type="button">
  <span id="themeIcon">☀️</span> <span id="themeLabel">Light Mode</span>
</button>
```

The button shows what theme will activate on next click (NOT current theme). If currently dark, button says "Light Mode" with ☀️ icon (suggesting "switch to light"). If currently light, button says "Dark Mode" with 🌙 icon.

**Meta theme-color** (sets the mobile browser chrome color):
```html
<meta name="theme-color" content="#d97706">
```
This is amber for MN. Should match the subject's accent darker tone for the mobile address bar.


**Theme unification (v3 change):** Previously, each subject used a different theme key (MN/Pharm used `nur2460_theme`, PD used `atipd_theme`, index.html used `elevated_theme`). In v3, **all 13 files write to a single canonical key**: `nur2460_theme`. Each file also runs a one-time salvage migration on first visit:

```javascript
// Run BEFORE reading THEME_KEY
try {
  ['elevated_theme', 'atipd_theme', 'nur2460_pharm_theme'].forEach(function(oldKey){
    var oldVal = localStorage.getItem(oldKey);
    if (oldVal !== null) {
      if (localStorage.getItem('nur2460_theme') === null) {
        localStorage.setItem('nur2460_theme', oldVal);
      }
      localStorage.removeItem(oldKey);  // remove orphan after salvaging
    }
  });
} catch(e){}
```

This ensures a user who toggled light mode on (e.g.) the PD Hub before v3 doesn't lose that preference. Theme now propagates instantly across the whole suite — toggle in any file, all others reflect it on next load. Books and Templates also persist theme in v3 (previously they had toggle buttons but didn't save state).

**Important:** PD's OTHER `atipd_*` keys (book progress, templates progress, fc_schedule, fc_filters) intentionally remain separate per §C.3.3. Only `_theme` was unified.

### 3.5 Light-Mode Color Contrast Verification

> *Consolidated from former Addendum C.4.*

#### C.4.1 WCAG AA standards

For body text: contrast ratio ≥ 4.5:1
For large text (18px+ bold or 24px+): contrast ratio ≥ 3:1
For UI components (borders, icons): ratio ≥ 3:1

#### C.4.2 Light-mode contrast audit (MN subject)

```
Foreground        Background       Ratio   AA?
────────────────  ───────────────  ──────  ───
--text  #1e1c18   --bg  #faf7f2    14.8:1  ✓ AAA
--text  #1e1c18   --surface #f4f0e8 13.7:1 ✓ AAA
--text2 #5a5448   --bg  #faf7f2    7.8:1   ✓ AAA
--text2 #5a5448   --surface #f4f0e8 7.2:1  ✓ AAA
--text3 #9e9080   --bg  #faf7f2    3.4:1   ✗ FAIL for body
                                           ✓ OK for large text + UI
--accent #ea580c  --bg  #faf7f2    4.6:1   ✓ AA (body)
--accent #ea580c  --surface #f4f0e8 4.2:1  ✗ FAIL by margin
                                           ✓ AA for large text
--accent2 #0f766e --bg  #faf7f2    5.3:1   ✓ AA (body)
```

**Issues found:**
1. `--text3` on `--bg` for body text fails WCAG AA. Currently used in `.planner-src`, `.unit-range`, footer text. **Mitigation:** these are all auxiliary metadata, considered "large" or "decorative". Acceptable but borderline.

2. `--accent` (#ea580c orange) on `--surface` cream fails WCAG AA by a small margin. Used for hover states and active sidebar items. **Mitigation:** these are large UI elements (icons, full-width items), and the ratio passes for "large text" rules.

#### C.4.3 Dark-mode contrast audit (MN subject)

```
Foreground        Background       Ratio   AA?
────────────────  ───────────────  ──────  ───
--text  #e8eaf2   --bg  #0f1117    14.2:1  ✓ AAA
--text  #e8eaf2   --surface #181c27 12.8:1 ✓ AAA
--text2 #8b92b8   --bg  #0f1117    6.5:1   ✓ AA
--text2 #8b92b8   --surface #181c27 5.9:1  ✓ AA
--text3 #555e85   --bg  #0f1117    3.6:1   ✗ FAIL body
                                           ✓ OK for large + UI
--accent #fbbf24  --bg  #0f1117    11.6:1  ✓ AAA
--accent #fbbf24  --surface #181c27 10.5:1 ✓ AAA
```

**Issue:** `--text3` on `--bg` in dark mode is also borderline failing. Same mitigation: used only for auxiliary metadata.

#### C.4.4 Per-subject accent contrast

```
MN dark mode    --accent #fbbf24 on #0f1117  11.6:1  ✓ AAA
MN light mode   --accent #ea580c on #faf7f2   4.6:1  ✓ AA  (body, close)

PD dark mode    --accent #60a5fa on #0f1117   6.8:1  ✓ AAA
PD light mode   --accent #2563eb on #faf7f2   5.9:1  ✓ AA  (estimated)

Pharm dark mode --accent #fb923c on #0f1117   7.4:1  ✓ AAA
Pharm light mode --accent #c2410c on #faf7f2  6.1:1  ✓ AA  (estimated)
```

#### C.4.5 Prompt-type colors on white print background

When the print overlay renders with white background (#ffffff), prompt-type colored borders need verification:

```
--prompt-content   #4fa3e0 on #ffffff   3.2:1  ✓ OK for borders/UI
--prompt-judgment  #a78bfa on #ffffff   2.9:1  ✗ Below 3:1 for UI
--prompt-principle #14b8a6 on #ffffff   3.1:1  ✓ OK
--prompt-priority  #ef4444 on #ffffff   3.8:1  ✓ OK
```

**Issue:** `--prompt-judgment` (purple) is too low contrast on print's white background. **Mitigation:** in print stylesheets, deepen prompt-judgment to a darker purple:

```css
@media print {
  .mid-prompt-judgment {
    border-left-color: #6d4ea3 !important;
  }
  .mid-prompt-judgment .mid-prompt-tag {
    background: #6d4ea3 !important;
    color: white !important;
  }
}
```

#### C.4.6 FHR colors verification

These colors are clinical and must be perceivable for color-blind users:

```
Dark mode:
--reassuring    #3db87a green     on bg #0f1117  6.0:1  ✓ AA
--indeterminate #e8a838 yellow    on bg #0f1117  9.4:1  ✓ AAA
--nonreassuring #e05c6a red       on bg #0f1117  5.4:1  ✓ AA

Light mode:
--reassuring    #1a9157 darker grn on bg #faf7f2  4.7:1  ✓ AA
--indeterminate #b87418 amber      on bg #faf7f2  5.2:1  ✓ AA
--nonreassuring #c0384a darker red on bg #faf7f2  5.9:1  ✓ AA
```

**Color-blind check:** the 3-color FHR scheme (green/yellow/red) doesn't distinguish for deuteranopia. **Mitigation:** every FHR card also has a textual label ("Reassuring", "Indeterminate", "Nonreassuring") — color is reinforcement, not the only signal.

#### C.4.7 Verification script

```python
"""Calculate WCAG contrast ratios for all CSS variable combinations."""
import re

def hex_to_rgb(hex_str):
    hex_str = hex_str.lstrip('#')
    return tuple(int(hex_str[i:i+2], 16) for i in (0, 2, 4))

def relative_luminance(rgb):
    def channel(c):
        c = c / 255
        return c / 12.92 if c <= 0.03928 else ((c + 0.055) / 1.055) ** 2.4
    r, g, b = rgb
    return 0.2126 * channel(r) + 0.7152 * channel(g) + 0.0722 * channel(b)

def contrast_ratio(fg, bg):
    l1 = relative_luminance(hex_to_rgb(fg))
    l2 = relative_luminance(hex_to_rgb(bg))
    if l1 < l2: l1, l2 = l2, l1
    return (l1 + 0.05) / (l2 + 0.05)

# All combos to check
fg_colors = {
    '--text':           '#e8eaf2',
    '--text2':          '#8b92b8',
    '--text3':          '#555e85',
    '--accent':         '#fbbf24',
    '--accent2':        '#fcd34d',
    '--reassuring':     '#3db87a',
    '--indeterminate':  '#e8a838',
    '--nonreassuring':  '#e05c6a',
}
bg_colors = {
    '--bg':       '#0f1117',
    '--surface':  '#181c27',
    '--surface2': '#1e2336',
}

print(f"{'FG':<20} {'BG':<15} {'Ratio':<10} {'WCAG':<10}")
for fg_name, fg in fg_colors.items():
    for bg_name, bg in bg_colors.items():
        ratio = contrast_ratio(fg, bg)
        wcag = 'AAA' if ratio >= 7 else 'AA' if ratio >= 4.5 else 'FAIL'
        print(f"{fg_name:<20} {bg_name:<15} {ratio:.1f}:1     {wcag}")
```

#### C.4.8 Recommendations for color tuning

If accessibility is a top priority:
1. Tighten `--text3` from #555e85 to #6b75a2 (dark) and from #9e9080 to #7d6f5d (light) to lift contrast above 4.5:1.
2. Darken `--accent` in light mode from #ea580c to #c2410c for body text compliance.
3. Add the `prompt-judgment` print override in C.4.5 to every Book file.

**However:** these changes affect the visual identity. The current palette is borderline-but-acceptable for the educational context. Don't change unless deploying to a user base with documented accessibility needs.

---

---

## PART 4 — RESPONSIVE DESIGN & MOBILE BEHAVIOR

### 4.1 Breakpoints

The suite uses **two media query breakpoints**:

```css
/* Primary mobile breakpoint — everything below desktop */
@media (max-width: 900px) { ... }

/* Tight phones — small adjustments only */
@media (max-width: 600px) { ... }

/* Tablet-only range — rarely used */
@media (max-width: 900px) and (min-width: 601px) { ... }
```

There's also **print mode** for the PDF overlay feature:
```css
@media print { ... }   /* 5 separate print blocks for different scopes */
```

### 4.2 Sidebar — mobile transformation

**Default (desktop, > 900px):**
```css
.layout { display: flex; min-height: 100vh; }
.sidebar {
  width: 280px; min-width: 280px;
  background: var(--surface);
  border-right: 1px solid var(--border);
  display: flex; flex-direction: column;
  position: fixed; top: 0; left: 0; bottom: 0;
  overflow: hidden;
  z-index: 10;
  transition: transform 0.25s, background 0.2s;
}
.main-content {
  margin-left: 280px;   /* leave room for fixed sidebar */
  flex: 1; min-width: 0;
  padding: 36px 32px 80px;
  max-width: 820px;
}
.sidebar-toggle { display: none; }       /* hamburger hidden on desktop */
.back-home-mobile { display: none; }     /* mobile back-to-hub button hidden */
```

**Mobile (≤ 900px):**
```css
@media (max-width: 900px) {
  .sidebar {
    transform: translateX(-100%);    /* offscreen by default */
    transition: transform .25s;
  }
  .sidebar.open {
    transform: translateX(0);         /* slides in when .open class added */
  }
  .sidebar-header {
    padding-top: 116px;               /* clear the floating back button */
  }
  .sidebar-header .back-home {
    display: none;                    /* hide desktop back-home; mobile floating button takes over */
  }
  .main-content {
    margin-left: 0;                   /* full-width on mobile */
    padding: 124px 24px 60px;         /* top padding clears floating buttons */
  }
  .sidebar-toggle { display: flex; }   /* show hamburger */
  .back-home-mobile { display: flex; } /* show floating back-to-hub */
}
```

### 4.3 Mobile floating buttons

Two fixed-position buttons appear on mobile only:

**Hamburger menu (sidebar toggle):**
```html
<button class="sidebar-toggle" id="sidebarToggle" type="button" aria-label="Toggle navigation">☰</button>
```
```css
.sidebar-toggle {
  display: none;
  position: fixed;
  top: 66px; left: 14px;
  z-index: 50;
  background: var(--surface);
  border: 1px solid var(--border); color: var(--text);
  width: 40px; height: 40px; border-radius: 8px;
  font-size: 18px; cursor: pointer;
  align-items: center; justify-content: center;
}
```

**Back-to-Hub floating button:**
```html
<a class="back-home-mobile" href="Elevated%20ATI%20MN%20Hub.html">← Back to Hub</a>
```
```css
.back-home-mobile {
  display: none;
  position: fixed;
  top: 14px; left: 14px;
  z-index: 51;          /* above hamburger */
  font-size: 11px; font-weight: 600;
  color: var(--text2); text-decoration: none;
  letter-spacing: .03em;
  align-items: center; gap: 5px;
  background: var(--surface); border: 1px solid var(--border);
  padding: 8px 14px; border-radius: 8px;
  transition: color .15s, border-color .15s;
}
```

Positioning: Back-to-Hub at top-left (top: 14px), hamburger just below it (top: 66px = 14 + 40 + 12 gap).

**Sidebar overlay** (dark backdrop when sidebar is open):
```html
<div class="sidebar-overlay" id="sidebarOverlay"></div>
```
```css
.sidebar-overlay {
  display: none;
  position: fixed; inset: 0;
  background: rgba(0,0,0,.4);
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  z-index: 9;                         /* just below sidebar's z-index: 10 */
  transition: opacity .25s;
}
.sidebar-overlay.show {
  display: block;
}
```

**Toggle logic:**
```javascript
function openSidebarPanel() {
  document.getElementById('sidebar').classList.add('open');
  document.getElementById('sidebarOverlay').classList.add('show');
}
function closeSidebarPanel() {
  document.getElementById('sidebar').classList.remove('open');
  document.getElementById('sidebarOverlay').classList.remove('show');
}
document.getElementById('sidebarToggle').addEventListener('click', function() {
  if (document.getElementById('sidebar').classList.contains('open')) closeSidebarPanel();
  else openSidebarPanel();
});
document.getElementById('sidebarOverlay').addEventListener('click', closeSidebarPanel);

// Also close sidebar when opening a chapter on mobile
if (window.innerWidth <= 900) closeSidebarPanel();
```

### 4.4 Touch targets

All tappable elements meet WCAG 2.5.5 minimum (24×24 CSS px), most exceed it:
- Hamburger: 40×40
- Back-home: ~36 high × wide content
- Sidebar items: 32 high (8px vertical padding + ~16 line-height)
- Tab buttons: ~33 high (9px vertical padding + 12px font)
- Planner check: 20×20 (slightly under — relies on parent .planner-row being clickable area)
- Exercise headers: full row clickable
- Mid-read rate buttons: full button area, ~36 high

### 4.5 Modal on mobile

```css
.modal-overlay {
  position: fixed; inset: 0;
  background: var(--modal-bg);
  backdrop-filter: blur(8px);
  z-index: 100;
  display: none;
  align-items: flex-start; justify-content: center;
  padding: 40px 24px;          /* less padding on mobile via base */
  overflow-y: auto;
}
.modal {
  width: 100%; max-width: 980px;
  background: var(--bg);
  border: 1px solid var(--border);
  border-radius: 16px;
  margin: auto;
  display: flex; flex-direction: column;
  max-height: calc(100vh - 80px);
  overflow: hidden;
  box-shadow: 0 20px 60px rgba(0,0,0,0.4);
}
```

On mobile, the modal expands to nearly full screen width with the 24px overlay padding providing the visible edge.

**Mobile-specific tweak (≤600px):**
```css
@media (max-width: 600px) {
  .modal-fc-btn { font-size: 12px; padding: 7px 10px; }
  .modal-fc-btn span { /* shortened text on tiny screens */ }
}
```

### 4.6 Tab strip — scrolling

The modal-tabs wrap allows horizontal scrolling when there are too many tabs:

```css
.modal-tabs-wrap {
  position: relative;
  flex: 1; min-width: 0;
  overflow-x: auto; overflow-y: hidden;
  -webkit-overflow-scrolling: touch;
  touch-action: pan-x;
  scrollbar-width: none;       /* hide scrollbar in Firefox */
  transition: box-shadow .15s ease;
  width: 100%;
}
.modal-tabs-wrap::-webkit-scrollbar { display: none; }  /* hide in WebKit */

.modal-tabs {
  display: inline-flex; gap: 4px;
  white-space: nowrap; flex-wrap: nowrap;
}
```

When scrolled, edge gradients indicate more content:
```css
.modal-tabs-wrap.shadow-left  { box-shadow: inset 70px 0 30px -20px rgba(0,0,0,0.45); }
.modal-tabs-wrap.shadow-right { box-shadow: inset -70px 0 30px -20px rgba(0,0,0,0.45); }
/* Light mode: opacity 0.15 instead of 0.45 */
```

The `updateTabFade()` JS function adds/removes these classes on scroll:
```javascript
function updateTabFade() {
  var wrap = document.getElementById('modalTabsWrap');
  if (!wrap) return;
  var scrollLeft = wrap.scrollLeft;
  var maxScroll = wrap.scrollWidth - wrap.clientWidth;
  wrap.classList.toggle('shadow-left',  scrollLeft > 5);
  wrap.classList.toggle('shadow-right', scrollLeft < maxScroll - 5);
}
```

### 4.7 Ios Safari Quirks (Reference)

> *Consolidated from former Addendum H.1.*

The suite is mobile-first and the dominant testing surface is iOS Safari. Known quirks and mitigations:

#### H.1.1 100vh includes the bottom toolbar

**Problem:** `100vh` on iOS Safari includes the bottom URL/tab bar area, which CAN auto-hide when scrolling. Layouts using `min-height: 100vh` jump when the bar appears/disappears.

**Where it matters in the suite:**
- `.layout { min-height: 100vh }` — the main grid
- `.modal { max-height: calc(100vh - 80px) }` — chapter modal
- `.bookmarks-overlay { ... }` — bookmarks panel

**Mitigation:** Use `dvh` (dynamic viewport height) where supported:
```css
.layout { min-height: 100vh; min-height: 100dvh; }
.modal { max-height: calc(100vh - 80px); max-height: calc(100dvh - 80px); }
```

`dvh` is supported in iOS Safari 15.4+. Fallback to `vh` for older versions.

#### H.1.2 Position: sticky with scrolling parents

**Problem:** `position: sticky` only sticks within its nearest scrolling ancestor. The Book modal-tabs use sticky but the body is the scroller, not modal-body — leading to inconsistent behavior.

**Where it matters:**
- `.modal-header` (sticky to top of modal-body)
- `.print-toolbar` (sticky to top of print-overlay)

**Mitigation:** ensure each sticky element's scrolling parent has `overflow: auto` or `overflow: scroll`:
```css
.modal-body { overflow-y: auto; }
.modal-header { position: sticky; top: 0; }  /* sticks within modal-body */
```

#### H.1.3 Touch events vs click events

**Problem:** iOS sometimes delays click events ~300ms or doesn't fire them at all on elements without `cursor: pointer` or button role.

**Where it matters:** custom div-as-button elements (`<div class="planner-check">`, `<div class="unit-header">`)

**Mitigation:**
- Use `<button>` instead of `<div>` where possible
- For divs that must be clickable: add `cursor: pointer` and `role="button"`
- For critical interactions, listen to both `touchend` and `click`:
  ```javascript
  function bindClick(el, handler) {
    el.addEventListener('click', handler);
    el.addEventListener('touchend', function(e) {
      e.preventDefault();
      handler(e);
    });
  }
  ```

#### H.1.4 Backdrop-filter performance

**Problem:** `backdrop-filter: blur(...)` is GPU-intensive on iOS. On older iPhones (X and below), modals with blur can drop to 30fps when scrolling.

**Where it matters:**
- `.modal-overlay { backdrop-filter: blur(8px); }`
- `.sidebar-overlay { backdrop-filter: blur(4px); }`
- `.bookmarks-overlay { backdrop-filter: blur(6px); }`

**Mitigation:** Reduce blur radius on mobile:
```css
@media (max-width: 600px) {
  .modal-overlay { backdrop-filter: blur(4px); }
  .sidebar-overlay { backdrop-filter: blur(2px); }
}
```

Or remove entirely on very old devices:
```css
@supports not (backdrop-filter: blur(1px)) {
  .modal-overlay { background: rgba(0,0,0,0.7); }
}
```

#### H.1.5 Scroll-snap and momentum scrolling

**Problem:** `.modal-tabs-wrap` is horizontally scrollable. iOS doesn't show scrollbars but the scroll feels "loose" without snap points.

**Mitigation:** Already includes `-webkit-overflow-scrolling: touch` for momentum. Consider adding scroll-snap if many tabs:
```css
.modal-tabs-wrap {
  scroll-snap-type: x proximity;
}
.tab-btn {
  scroll-snap-align: start;
}
```

(Not currently in MN — would require validation that it doesn't break.)

#### H.1.6 Form input zoom

**Problem:** Tapping an input with font-size < 16px causes iOS to auto-zoom into the field.

**Where it matters:**
- `#searchInput { font-size: 13px; }`
- `#tplFilterInput { font-size: 13px; }`
- `#filterChapter` select dropdown

**Mitigation:** bump to 16px on small screens:
```css
@media (max-width: 600px) {
  #searchInput, #tplFilterInput, .fc-filters select { font-size: 16px; }
}
```

Or apply globally and use `transform: scale()` to visually shrink (uglier hack).

#### H.1.7 LocalStorage limits

**Problem:** iOS Safari Private Browsing has a localStorage quota of ~5MB (sometimes less). Heavy users with many flashcards approach this limit.

**Mitigation:**
- Wrap every `localStorage.setItem` in `try/catch`
- Show a graceful warning if quota exceeded:
  ```javascript
  try { localStorage.setItem(key, value); }
  catch(e) {
    if (e.name === 'QuotaExceededError') {
      alert('Storage full. Export your backup and reset some progress.');
    }
  }
  ```

#### H.1.8 Date input on iOS

**Problem:** Native `<input type="date">` on iOS shows a roller UI that's awkward.

**Where it matters:** The flashcards Browse tab might filter by due date.

**Mitigation:** Use text input with format hint, or build a custom date picker. (Currently not an issue since the suite doesn't expose date pickers to users.)

#### H.1.9 Safe-area insets (notch / home indicator)

**Problem:** iPhones with notches/home indicators have safe-area insets that overlap fixed elements.

**Where it matters:**
- `.sidebar-toggle { top: 66px; }` — may overlap notch
- `.back-home-mobile { top: 14px; }` — definitely overlaps notch on newer iPhones

**Mitigation:**
```css
.back-home-mobile {
  top: 14px;
  top: max(14px, env(safe-area-inset-top));
}
.sidebar-toggle {
  top: 66px;
  top: max(66px, calc(env(safe-area-inset-top) + 52px));
}
```

And add to viewport meta:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
```

#### H.1.10 Tap highlight color

**Problem:** iOS shows a gray flash when tapping any clickable element by default.

**Mitigation:** Suppress globally:
```css
* {
  -webkit-tap-highlight-color: transparent;
}
```

Or keep it for accessibility but tune the color:
```css
* {
  -webkit-tap-highlight-color: var(--accent-soft);
}
```

#### H.1.11 Pull-to-refresh on body

**Problem:** Pulling down at the top of any page triggers iOS pull-to-refresh, which can disrupt the modal-open state.

**Mitigation:**
```css
body { overscroll-behavior-y: contain; }
body.modal-open { overflow: hidden; position: fixed; width: 100%; }
```

The `body.modal-open` class is added in `openChapter()`. The `position: fixed` lock prevents the document from scrolling behind the modal but does cause a scroll-position reset when closing.

**Better mitigation:** save and restore scroll position:
```javascript
var savedScroll = 0;
function lockBody() {
  savedScroll = window.scrollY;
  document.body.style.position = 'fixed';
  document.body.style.top = '-' + savedScroll + 'px';
  document.body.style.width = '100%';
}
function unlockBody() {
  document.body.style.position = '';
  document.body.style.top = '';
  document.body.style.width = '';
  window.scrollTo(0, savedScroll);
}
```

#### H.1.12 Local file:// protocol issues

**Problem:** Opening Book.html directly from filesystem (not via http://localhost) blocks localStorage on some browsers and Google Fonts may not load due to CORS.

**Mitigation:** Always test via a local server:
```bash
cd path/to/NUR2460
python3 -m http.server 8000
# Open http://localhost:8000/Elevated%20ATI%20MN%20Hub.html
```

Or use GitHub Pages preview directly.

---

---

## PART 5 — INDEX.HTML

The top-level landing. Three subject cards on a single page.

### 5.1 Document structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#a78bfa">
  <title>Elevated · NUR 2460 ATI Companion</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg:#0f1117; --surface:#181c27; --surface2:#1e2336; --surface3:#242a40;
      --border:#2a3050; --text:#e8eaf2; --text2:#8b92b8; --text3:#555e85;
      --accent:#a78bfa; --accent2:#c4b5fd; --accent-soft:rgba(167,139,250,0.12);
      --mn-color:#fbbf24; --mn-color-soft:rgba(251,191,36,0.12);
      --pd-color:#38bdf8; --pd-color-soft:rgba(56,189,248,0.12);
      --pharm-color:#fb923c; --pharm-color-soft:rgba(251,146,60,0.12);
      --shadow:0 8px 24px rgba(0,0,0,0.3);
    }
    [data-theme="light"] {
      --bg:#faf7f2; --surface:#f4f0e8; --surface2:#ede7d8; --surface3:#e0d8c4;
      --border:#d6ccb8; --text:#1e1c18; --text2:#6b5f4d; --text3:#9c8e7a;
      --accent:#7c3aed; --accent2:#a78bfa; --accent-soft:rgba(124,58,237,0.10);
    }
    * { box-sizing: border-box; }
    body {
      margin:0; font-family:'DM Sans', sans-serif;
      background:var(--bg); color:var(--text);
      font-size:15px; line-height:1.55;
      transition: background 0.25s, color 0.25s;
    }
    /* ... see Part 11 for full ruleset ... */
  </style>
</head>

<body>
  <main class="page">

    <!-- HEADER -->
    <header class="page-header">
      <div class="brand">
        <div class="brand-dot"></div>
        <div class="brand-text">
          <div class="brand-eyebrow">NUR 2460</div>
          <div class="brand-name">Elevated</div>
        </div>
      </div>
      <button class="theme-toggle" id="themeToggle" type="button">
        <span id="themeIcon">☀️</span>
        <span id="themeLabel">Light Mode</span>
      </button>
    </header>

    <!-- HERO -->
    <section class="hero">
      <h1>Elevated · <em>NUR 2460</em></h1>
      <p class="hero-sub">
        ATI RN Companion suites for Maternal-Newborn, Pediatric, and Pharmacology.
        Chapter-by-chapter reference, worked Active Learning Templates, and spaced-repetition
        flashcards — all built for fast mobile lookup.
      </p>
    </section>

    <!-- SUBJECT GRID -->
    <section class="subject-grid">
      <a class="subject-card" href="Elevated%20ATI%20MN%20Hub.html" data-subject="mn">
        <div class="subject-eyebrow">Maternal-Newborn · 27 chapters · 4 units</div>
        <h2>Maternal-Newborn Nursing</h2>
        <p class="subject-desc">
          Antepartum care, intrapartum management, postpartum recovery, and newborn complications.
          Includes 105 worked templates and 122 starter flashcards.
        </p>
        <div class="subject-cta">Open MN suite ↗</div>
      </a>

      <a class="subject-card" href="Elevated%20ATI%20PD%20Hub.html" data-subject="pd">
        <div class="subject-eyebrow">Pediatric · 44 chapters · 3 units</div>
        <h2>Nursing Care of Children</h2>
        <p class="subject-desc">
          Growth & development across all ages, system disorders from neonate through adolescent,
          medication-administration considerations specific to pediatric clients.
        </p>
        <div class="subject-cta">Open PD suite ↗</div>
      </a>

      <a class="subject-card" href="Elevated%20ATI%20Pharm%20Hub.html" data-subject="pharm">
        <div class="subject-eyebrow">Pharmacology · 49 chapters · 13 units</div>
        <h2>Pharmacology for Nursing</h2>
        <p class="subject-desc">
          Pharmacokinetic principles, drug class prototypes, contraindications, nursing administration,
          and therapeutic monitoring across 13 body-system units.
        </p>
        <div class="subject-cta">Open Pharm suite ↗</div>
      </a>
    </section>

    <!-- FOOTER -->
    <footer class="footer">
      <p>Elevated · NUR 2460 · ATI RN Companion</p>
      <p>sleepyius.github.io/NUR2460/</p>
    </footer>
  </main>

  <script>
    /* Theme toggle - see Part 3.4 */
  </script>
</body>
</html>
```

### 5.2 Subject-card styling per subject

Each subject card uses its own color via the `[data-subject]` attribute:

```css
.subject-card[data-subject="mn"]   { --card-accent: var(--mn-color);    --card-soft: var(--mn-color-soft); }
.subject-card[data-subject="pd"]   { --card-accent: var(--pd-color);    --card-soft: var(--pd-color-soft); }
.subject-card[data-subject="pharm"]{ --card-accent: var(--pharm-color); --card-soft: var(--pharm-color-soft); }

.subject-card {
  background: linear-gradient(135deg, var(--surface), var(--surface2));
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 28px 26px;
  text-decoration: none;
  color: var(--text);
  display: flex; flex-direction: column;
  gap: 12px;
  transition: all .2s ease;
  position: relative;
  overflow: hidden;
}
.subject-card::before {
  content: ''; position: absolute;
  top: 0; left: 0; right: 0; height: 3px;
  background: var(--card-accent);
}
.subject-card:hover {
  border-color: var(--card-accent);
  box-shadow: 0 8px 24px rgba(0,0,0,0.3), 0 0 0 1px var(--card-soft);
  transform: translateY(-2px);
}
.subject-eyebrow {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: var(--card-accent);
}
.subject-card h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 28px; font-weight: 400;
  margin: 0; line-height: 1.15;
}
.subject-desc {
  font-size: 14px; color: var(--text2);
  margin: 0; line-height: 1.55;
}
.subject-cta {
  margin-top: auto;
  font-size: 13px; font-weight: 600;
  color: var(--card-accent);
}
```

### 5.3 Grid responsive layout

```css
.subject-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 18px;
  margin: 40px 0;
}
@media (max-width: 900px) {
  .subject-grid { grid-template-columns: 1fr; }
}
```

### 5.4 Index-Page Cross-Subject View Notes

> *Consolidated from former Addendum H.4.*

`index.html` is intentionally minimal. It shows 3 subject cards and a theme toggle, nothing else.

**What index does NOT show:**
- Pickup panel (per-subject; lives in each Hub)
- Storage panel (per-subject)
- Aggregate stats across subjects

**Why:** users typically commit to one subject per session. Aggregate cross-subject views would require reading multiple localStorage prefixes, complicating the index. Each Hub handles its own subject's state.

**If you want cross-subject:** add a separate `dashboard.html` that reads all 3 subjects' progress and displays a unified view. Currently not built.

---

---

## PART 6 — SUBJECT HUB

The per-subject landing page. Has **exactly 6 `<section>` blocks** plus **3 non-section blocks**.

### 6.1 Document structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#d97706">     <!-- darker accent shade -->
  <title>Elevated · ATI Maternal-Newborn Companion</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>/* see Part 11 */</style>
</head>
<body>

  <main class="page">

    <!-- TOP BAR (back to index + theme toggle) -->
    <header class="page-header">
      <a class="back-link" href="index.html">← All subjects</a>
      <button class="theme-toggle" id="themeToggle" type="button">
        <span id="themeIcon">☀️</span><span id="themeLabel">Light Mode</span>
      </button>
    </header>

    <!-- 1. HERO -->
    <section class="hero">
      <div class="hero-eyebrow">Elevated · ATI Maternal-Newborn Companion</div>
      <h1>Maternal-Newborn<br><em>Nursing Care</em></h1>
      <p class="hero-sub">
        A chapter-by-chapter reference and worked-template companion for the
        ATI RN Maternal Newborn Nursing review module. Built for fast lookup,
        focused study, and exam preparation.
      </p>
    </section>

    <!-- 2. STATS -->
    <section class="stats">
      <div class="stat"><div class="stat-value">27</div><div class="stat-label">Chapters</div></div>
      <div class="stat"><div class="stat-value">4</div><div class="stat-label">Units</div></div>
      <div class="stat"><div class="stat-value">105</div><div class="stat-label">Worked Templates</div></div>
      <div class="stat"><div class="stat-value">8</div><div class="stat-label">Template Types</div></div>
      <div class="stat"><div class="stat-value">122</div><div class="stat-label">Starter Cards</div></div>
    </section>

    <!-- 3. PICKUP PANEL (resume reading) -->
    <section class="pickup-panel" id="pickupPanel" hidden>
      <div class="pickup-head">
        <h3>▶ Pick up where you left off</h3>
        <button class="pickup-dismiss" id="pickupDismiss" type="button" title="Hide this panel">×</button>
      </div>
      <div class="pickup-cards">
        <a class="pickup-card" id="pickupBook" href="#" hidden>
          <div class="pickup-icon">📖</div>
          <div class="pickup-text">
            <div class="pickup-label">Continue reading</div>
            <div class="pickup-value" id="pickupBookValue">—</div>
          </div>
        </a>
        <a class="pickup-card" id="pickupFc" href="Elevated%20ATI%20MN%20Flashcards.html" hidden>
          <div class="pickup-icon">🃏</div>
          <div class="pickup-text">
            <div class="pickup-label">Review queue</div>
            <div class="pickup-value" id="pickupFcValue">—</div>
          </div>
        </a>
        <a class="pickup-card" id="pickupTpl" href="#" hidden>
          <div class="pickup-icon">📋</div>
          <div class="pickup-text">
            <div class="pickup-label">Last template</div>
            <div class="pickup-value" id="pickupTplValue">—</div>
          </div>
        </a>
      </div>
    </section>

    <!-- 4. PRIMARY GRID (3 tool cards) -->
    <section class="primary-grid">
      <a class="tool-card" href="Elevated%20ATI%20MN%20Book.html">
        <div class="tool-eyebrow">Reference · 27 chapters</div>
        <h2>ATI Chapter Book</h2>
        <p class="tool-desc">
          Full chapter-by-chapter content from the ATI review module — antepartum
          care through newborn complications. Each chapter has a TL;DR, condition
          cards, mnemonics, and an Active Learning Scenario.
        </p>
        <div class="tool-meta">
          <span class="tool-meta-item"><strong>4</strong> units</span>
          <span class="tool-meta-item"><strong>27</strong> chapters</span>
          <span class="tool-meta-item"><strong>10</strong> pp avg / ch</span>
        </div>
        <div class="progress-row">
          <div class="progress-bar"><div class="progress-fill" id="bookProgress"></div></div>
          <div class="progress-text" id="bookProgressText">0 / 27 read</div>
        </div>
        <div class="tool-cta">Open chapter book</div>
      </a>

      <a class="tool-card" href="Elevated%20ATI%20MN%20Templates.html">
        <div class="tool-eyebrow">Practice · 105 examples</div>
        <h2>ATI Templates</h2>
        <p class="tool-desc">
          Worked examples for all 8 ATI Active Learning Template types: Basic Concept,
          Medication, System Disorder, and more. Toggle Filled / Blank to test yourself.
        </p>
        <div class="tool-meta">
          <span class="tool-meta-item"><strong>8</strong> template types</span>
          <span class="tool-meta-item"><strong>105</strong> worked examples</span>
        </div>
        <div class="progress-row">
          <div class="progress-bar"><div class="progress-fill" id="tplProgress"></div></div>
          <div class="progress-text" id="tplProgressText">0 / 105 studied</div>
        </div>
        <div class="tool-cta">Open templates</div>
      </a>

      <a class="tool-card" href="Elevated%20ATI%20MN%20Flashcards.html">
        <div class="tool-eyebrow">Active recall · SM-2 spaced</div>
        <h2>Flashcards</h2>
        <p class="tool-desc">
          Spaced-repetition review of every prompt you've rated in the chapter book.
          Cards return on the SM-2 schedule — hard cards come back sooner, easy ones spread out.
        </p>
        <div class="tool-meta">
          <span class="tool-meta-item"><strong>SM-2</strong> algorithm</span>
          <span class="tool-meta-item"><strong>122</strong> starter cards</span>
        </div>
        <div class="progress-row">
          <div class="progress-bar"><div class="progress-fill" id="fcProgress"></div></div>
          <div class="progress-text" id="fcProgressText">0 due now</div>
        </div>
        <div class="tool-cta">Start review</div>
      </a>
    </section>

    <!-- 5. UNITS GRID -->
    <section class="units-grid">
      <a class="unit-card" href="Elevated%20ATI%20MN%20Book.html#ch1" data-unit="unit1">
        <div class="unit-num">Unit 1</div>
        <h3>Antepartum</h3>
        <div class="unit-range">Ch 1 – 10</div>
        <div class="unit-progress">
          <div class="unit-progress-bar"><div class="unit-progress-fill" data-unit-bar="unit1"></div></div>
          <div class="unit-progress-text" data-unit-text="unit1">0 / 10 read</div>
        </div>
      </a>
      <a class="unit-card" href="Elevated%20ATI%20MN%20Book.html#ch11" data-unit="unit2">
        <div class="unit-num">Unit 2</div><h3>Intrapartum</h3>
        <div class="unit-range">Ch 11 – 14</div>
        <div class="unit-progress">
          <div class="unit-progress-bar"><div class="unit-progress-fill" data-unit-bar="unit2"></div></div>
          <div class="unit-progress-text" data-unit-text="unit2">0 / 4 read</div>
        </div>
      </a>
      <!-- ... one per unit ... -->
    </section>

    <!-- 6. TYPES GRID (template types) -->
    <section class="types-grid">
      <a class="type-row" href="Elevated%20ATI%20MN%20Templates.html#basic-concept-acc">
        <span class="type-page">A1</span>
        <span class="type-name">Basic Concept</span>
        <span class="type-count">14 examples</span>
      </a>
      <a class="type-row" href="Elevated%20ATI%20MN%20Templates.html#diagnostic-procedure-acc">
        <span class="type-page">A3</span>
        <span class="type-name">Diagnostic Procedure</span>
        <span class="type-count">6 examples</span>
      </a>
      <!-- ... all 8 template types ... -->
    </section>

    <!-- 7. FUTURE CARD -->
    <div class="future-card">
      <h3>Planned additions</h3>
      <ul class="future-list">
        <li>Mid-read prompts (CONTENT/JUDGMENT/PRINCIPLE/PRIORITY)</li>
        <li>Spaced-repetition flashcards</li>
        <li>Pediatric ATI companion</li>
        <li>Community ATI companion</li>
      </ul>
    </div>

    <!-- 8. STORAGE PANEL (collapsed by default) -->
    <div class="storage-panel" id="storagePanel">
      <div class="storage-panel-head" id="storagePanelHead">
        <h3 class="storage-panel-title">Sync &amp; storage</h3>
        <span class="storage-panel-caret">▸</span>
      </div>
      <div class="storage-panel-body">
        <div class="storage-actions">
          <button class="storage-btn" id="exportBtn" type="button">⬇ Export backup</button>
          <button class="storage-btn" id="importBtn" type="button">⬆ Import backup</button>
          <button class="storage-btn danger" id="resetBtn" type="button">⌫ Reset all progress</button>
          <input type="file" id="importFile" accept="application/json" style="display:none">
        </div>
        <div class="storage-status" id="storageStatus">Click a button to manage your local data.</div>
        <div class="storage-keys-list" id="storageKeysList"></div>
      </div>
    </div>

    <!-- 9. FOOTER -->
    <footer class="footer">
      <p>Elevated · Maternal-Newborn Nursing · ATI RN Companion · 11th Edition</p>
      <p>Built for sleepyius.github.io/NUR2460/</p>
    </footer>
  </main>

  <script>/* See Part 11 — Hub JS */</script>
</body>
</html>
```

### 6.2 Hero styling

```css
.hero {
  margin-top: 24px; padding: 32px 0 24px;
  text-align: center;
}
.hero-eyebrow {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.15em;
  color: var(--accent);
  margin-bottom: 14px;
}
.hero h1 {
  font-family: 'DM Serif Display', serif;
  font-size: 48px; font-weight: 400;
  line-height: 1.05; margin: 0 0 18px;
  letter-spacing: -0.01em;
}
.hero h1 em {
  font-style: italic;
  color: var(--accent);
}
.hero-sub {
  font-size: 16px; line-height: 1.6;
  color: var(--text2);
  max-width: 600px; margin: 0 auto;
}
@media (max-width: 600px) {
  .hero h1 { font-size: 36px; }
  .hero-sub { font-size: 14px; }
}
```

### 6.3 Stats row

```css
.stats {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 12px;
  margin: 24px 0;
  padding: 24px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 14px;
}
.stat {
  text-align: center;
  padding: 8px;
}
.stat-value {
  font-family: 'DM Serif Display', serif;
  font-size: 36px; font-weight: 400;
  color: var(--accent);
  line-height: 1;
  margin-bottom: 4px;
}
.stat-label {
  font-size: 11px; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.08em;
  color: var(--text2);
}
@media (max-width: 700px) {
  .stats { grid-template-columns: repeat(3, 1fr); }
  /* 5th and 4th items wrap to a 2nd row */
}
@media (max-width: 480px) {
  .stats { grid-template-columns: repeat(2, 1fr); }
}
```

### 6.4 Pickup panel

```css
.pickup-panel {
  background: linear-gradient(135deg, var(--accent-soft), transparent);
  border: 1px solid var(--accent);
  border-radius: 14px;
  padding: 20px 24px;
  margin: 24px 0;
}
.pickup-head {
  display: flex; justify-content: space-between; align-items: center;
  margin-bottom: 14px;
}
.pickup-head h3 {
  font-size: 14px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.08em;
  color: var(--accent);
  margin: 0;
}
.pickup-dismiss {
  background: transparent; border: none;
  color: var(--text3); font-size: 20px;
  cursor: pointer; padding: 0 8px;
}
.pickup-cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 12px;
}
.pickup-card {
  display: flex; align-items: center; gap: 12px;
  padding: 14px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 10px;
  text-decoration: none; color: var(--text);
  transition: all .15s;
}
.pickup-card:hover {
  border-color: var(--accent);
  transform: translateY(-1px);
}
.pickup-icon {
  font-size: 28px;
  flex-shrink: 0;
}
.pickup-label {
  font-size: 11px; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.06em;
  color: var(--text3);
  margin-bottom: 2px;
}
.pickup-value {
  font-size: 14px; font-weight: 500;
  color: var(--text);
}
```

**Pickup panel JS** (verified canonical against MN):

> ✅ **VERIFIED canonical.** (Earlier guide versions had several errors: used `localStorage` for `pickup_dismissed` — actually `sessionStorage`; treated `last_chapter`/`last_template` as pipe-delimited strings — actually JSON objects `{id, name}`; wired dismiss listener separately — actually wired inside `updatePickupPanel` itself with `_wired` guard; used `removeAttribute('hidden')` — actually `panel.hidden = ...` boolean.)

```javascript
// Storage key constants (top of Hub script)
var LAST_CH_KEY_HUB    = 'nur2460_last_chapter';      // Book writes; Hub reads
var LAST_TPL_KEY_HUB   = 'nur2460_last_template';     // Templates writes; Hub reads
var PICKUP_DISMISS_KEY = 'nur2460_pickup_dismissed';  // SESSIONSTORAGE — resets next visit

// loadJson — safe JSON parse from localStorage (used throughout Hub)
function loadJson(key) {
  try {
    var raw = localStorage.getItem(key);
    return raw ? JSON.parse(raw) : null;
  } catch(e) { return null; }
}

// countDueCards — returns an OBJECT {due, scheduled}, not just a number
function countDueCards() {
  var schedule = loadJson('nur2460_fc_schedule') || {};
  var now = Date.now();
  var due = 0, scheduled = 0;
  for (var k in schedule) {
    if (!schedule[k] || !schedule[k].nextReview) continue;
    scheduled++;
    if (new Date(schedule[k].nextReview).getTime() <= now) due++;
  }
  return { due: due, scheduled: scheduled };
}

function updatePickupPanel() {
  var panel = document.getElementById('pickupPanel');
  if (!panel) return;

  // Honor dismissal for this session (sessionStorage — reappears on next visit)
  try {
    if (sessionStorage.getItem(PICKUP_DISMISS_KEY) === '1') {
      panel.hidden = true;
      return;
    }
  } catch(e) {}

  var fcStats = countDueCards();
  var lastCh  = loadJson(LAST_CH_KEY_HUB);   // {id: 'ch3', name: 'Newborn Assessment'}
  var lastTpl = loadJson(LAST_TPL_KEY_HUB);  // {id: 'ex-ch1-cocs', name: 'COCs'}

  var hasAny = false;

  // Book card
  var bookCard  = document.getElementById('pickupBook');
  var bookValue = document.getElementById('pickupBookValue');
  if (lastCh && lastCh.id && lastCh.name) {
    bookCard.href = 'Elevated%20ATI%20MN%20Book.html#' + lastCh.id;
    bookValue.textContent = 'Ch ' + lastCh.id.replace('ch', '') + ': ' + lastCh.name;
    bookCard.hidden = false;
    hasAny = true;
  }

  // Flashcards card
  var fcCard  = document.getElementById('pickupFc');
  var fcValue = document.getElementById('pickupFcValue');
  if (fcStats.scheduled > 0) {
    if (fcStats.due > 0) {
      fcValue.textContent = fcStats.due + ' card' + (fcStats.due === 1 ? '' : 's') + ' due now';
    } else {
      fcValue.textContent = 'All caught up · ' + fcStats.scheduled + ' in deck';
    }
    fcCard.hidden = false;
    hasAny = true;
  } else {
    fcValue.textContent = 'Load starter deck →';
    fcCard.hidden = false;
    hasAny = true;
  }

  // Templates card
  var tplCard  = document.getElementById('pickupTpl');
  var tplValue = document.getElementById('pickupTplValue');
  if (lastTpl && lastTpl.id && lastTpl.name) {
    tplCard.href = 'Elevated%20ATI%20MN%20Templates.html#' + lastTpl.id;
    tplValue.textContent = lastTpl.name;
    tplCard.hidden = false;
    hasAny = true;
  }

  panel.hidden = !hasAny;

  // Wire dismiss button (idempotent — _wired guard)
  var dismiss = document.getElementById('pickupDismiss');
  if (dismiss && !dismiss._wired) {
    dismiss._wired = true;
    dismiss.addEventListener('click', function() {
      try { sessionStorage.setItem(PICKUP_DISMISS_KEY, '1'); } catch(e) {}
      panel.hidden = true;
    });
  }
}
```

**Key cross-file data contract:**
- `last_chapter` is written by **Book** as `{id: 'chN', name: 'Chapter Title'}` (JSON), NOT a pipe-delimited string
- `last_template` is written by **Templates** as `{id: 'ex-ch1-cocs', name: 'COCs'}` (JSON)
- Hub READS these via `loadJson()` — never via raw `getItem()`
- `pickup_dismissed` lives in **sessionStorage**, NOT localStorage — dismissal lasts one tab session only

**Per-subject changes:** all `nur2460_*` keys → subject namespace.

### 6.5 Primary grid (3 tool cards)

```css
.primary-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin: 24px 0;
}
.tool-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 24px;
  text-decoration: none;
  color: var(--text);
  display: flex; flex-direction: column;
  gap: 10px;
  transition: all .2s;
  position: relative; overflow: hidden;
}
.tool-card:hover {
  border-color: var(--accent);
  box-shadow: 0 8px 24px rgba(0,0,0,0.2);
  transform: translateY(-2px);
}
.tool-eyebrow {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.08em;
  color: var(--accent);
}
.tool-card h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 24px; font-weight: 400;
  margin: 0;
}
.tool-desc {
  font-size: 13.5px; color: var(--text2);
  line-height: 1.55;
  margin: 0; flex: 1;
}
.tool-meta {
  display: flex; gap: 16px; flex-wrap: wrap;
  font-size: 12px; color: var(--text3);
}
.tool-meta-item strong {
  color: var(--text);
}
.progress-row {
  display: flex; align-items: center; gap: 10px;
  margin-top: 8px;
}
.progress-bar {
  flex: 1; height: 6px;
  background: var(--surface3);
  border-radius: 99px; overflow: hidden;
}
.progress-fill {
  height: 100%;
  background: var(--accent);
  border-radius: 99px;
  transition: width .25s;
}
.progress-text {
  font-size: 11px; color: var(--text3);
  white-space: nowrap;
}
.tool-cta {
  font-size: 13px; font-weight: 600;
  color: var(--accent);
  margin-top: 8px;
}
@media (max-width: 900px) {
  .primary-grid { grid-template-columns: 1fr; }
}
```

### 6.6 Units grid

```css
.units-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 12px;
  margin: 24px 0;
}
.unit-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 18px;
  text-decoration: none;
  color: var(--text);
  transition: all .15s;
}
.unit-card:hover {
  border-color: var(--accent);
  transform: translateY(-1px);
}
.unit-num {
  font-size: 10px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.12em;
  color: var(--accent);
  margin-bottom: 4px;
}
.unit-card h3 {
  font-family: 'DM Serif Display', serif;
  font-size: 18px; font-weight: 400;
  margin: 0 0 4px;
}
.unit-range {
  font-size: 12px; color: var(--text3);
  margin-bottom: 12px;
}
.unit-progress-bar {
  height: 4px; background: var(--surface3);
  border-radius: 99px; overflow: hidden;
  margin-bottom: 6px;
}
.unit-progress-fill {
  height: 100%; background: var(--accent);
  border-radius: 99px;
  width: 0%;
  transition: width .25s;
}
.unit-progress-text {
  font-size: 11px; color: var(--text3);
}
```

### 6.7 Template types grid

```css
.types-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 8px;
  margin: 24px 0;
}
.type-row {
  display: grid;
  grid-template-columns: 36px 1fr auto;
  align-items: center;
  gap: 12px;
  padding: 14px 16px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 10px;
  text-decoration: none;
  transition: all .15s;
}
.type-row:hover {
  border-color: var(--accent);
}
.type-page {
  font-family: 'DM Serif Display', serif;
  font-size: 16px;
  color: var(--accent);
  text-align: center;
}
.type-name {
  font-size: 14px; font-weight: 500;
  color: var(--text);
}
.type-count {
  font-size: 11px; color: var(--text3);
  white-space: nowrap;
}
@media (max-width: 700px) {
  .types-grid { grid-template-columns: 1fr; }
}
```

### 6.8 Storage panel

```css
.storage-panel {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  margin: 32px 0 20px;
  overflow: hidden;
}
.storage-panel-head {
  display: flex; justify-content: space-between; align-items: center;
  padding: 14px 18px;
  cursor: pointer;
  user-select: none;
}
.storage-panel-title {
  font-size: 13px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.08em;
  color: var(--text2);
  margin: 0;
}
.storage-panel-caret {
  font-size: 14px; color: var(--text3);
  transition: transform .2s;
}
.storage-panel.open .storage-panel-caret { transform: rotate(90deg); }
.storage-panel-body {
  display: none;
  padding: 0 18px 18px;
  border-top: 1px solid var(--border-soft);
}
.storage-panel.open .storage-panel-body { display: block; }
.storage-actions {
  display: flex; gap: 8px; flex-wrap: wrap;
  margin: 14px 0;
}
.storage-btn {
  padding: 8px 14px;
  background: var(--surface2);
  border: 1px solid var(--border);
  color: var(--text);
  border-radius: 8px;
  cursor: pointer;
  font-size: 12px;
  transition: all .15s;
}
.storage-btn:hover {
  border-color: var(--accent);
}
.storage-btn.danger:hover {
  border-color: var(--nonreassuring);
  color: var(--nonreassuring);
}
.storage-status {
  font-size: 12px; color: var(--text3);
  margin: 8px 0;
}
.storage-keys-list {
  margin-top: 12px;
  font-family: 'SF Mono', Monaco, monospace;
  font-size: 11px; color: var(--text3);
  line-height: 1.5;
}
/* Note: MN renderKeysList outputs plain <span> rows (no nested .key/.key-name/.key-size).
   The selectors below were planned but never used in MN markup. Kept for completeness
   in case future implementations add the nested structure. */
.storage-keys-list .key {
  display: flex; justify-content: space-between;
  padding: 4px 0;
  border-bottom: 1px solid var(--border-soft);
}
.storage-keys-list .key-name { color: var(--text2); }
.storage-keys-list .key-size { color: var(--text3); }
```

**Storage panel JS** (verified canonical against MN):

> ✅ **VERIFIED canonical.** (Earlier guide versions had errors: export format was `{exportedAt, subject, version, data: {...}}` — actually MN uses `{_meta: {source, exportedAt}, [keyName]: value}` with each key at top level; values were stored as strings — actually MN parses them as JSON before storing; iteration was via `localStorage.length` prefix-loop — actually MN uses an explicit `SYNC_KEYS` whitelist for safety; filename was `elevated-mn-backup-` — actually `nur2460-backup-`. renderKeysList markup also differs.)

**SYNC_KEYS whitelist** (defined at top of Hub script — this is the safety list that gates export/import):
```javascript
var SYNC_KEYS = [
  'nur2460_atimn_progress',
  'nur2460_atimnTemplates_progress',
  'nur2460_fc_schedule',
  'nur2460_theme'
];
// (Pharm hub would add 'nur2460_atipharm_progress' here; PD hub uses its own atipd_* list)
```

Note: SYNC_KEYS deliberately omits `last_chapter`, `last_template`, `pickup_dismissed`, `bookmarks`, `nclex_done`, `tpl_filters`, `fc_filters` — those are session/UI state, not core progress. If you want full backup parity, add them explicitly to SYNC_KEYS.

**renderKeysList — list of synced keys in the panel** (no `.key-name` or `.key-size` children; just plain `<span>` rows):
```javascript
function renderKeysList() {
  if (!keysList) return;
  var html = '';
  SYNC_KEYS.forEach(function(k) {
    var v = localStorage.getItem(k);
    var size = v ? new Blob([v]).size : 0;
    var bytes = size < 1024 ? size + ' B' : (size / 1024).toFixed(1) + ' KB';
    html += '<span>' + k + ' · ' + (v ? bytes : 'empty') + '</span>';
  });
  keysList.innerHTML = html;
}
```

**Export backup** — produces a flat JSON object with values as parsed JSON:
```javascript
var exportBtn = document.getElementById('exportBtn');
if (exportBtn) exportBtn.addEventListener('click', function() {
  var backup = { _meta: { source: 'Elevated MN hub', exportedAt: new Date().toISOString() } };
  SYNC_KEYS.forEach(function(k) {
    var v = localStorage.getItem(k);
    backup[k] = v ? JSON.parse(v) : null;  // PARSED JSON, not raw string
  });
  var blob = new Blob([JSON.stringify(backup, null, 2)], { type: 'application/json' });
  var url = URL.createObjectURL(blob);
  var a = document.createElement('a');
  a.href = url;
  a.download = 'nur2460-backup-' + new Date().toISOString().slice(0,10) + '.json';
  document.body.appendChild(a); a.click(); document.body.removeChild(a);
  URL.revokeObjectURL(url);
  status.textContent = '✓ Backup downloaded.';
});
```

**Import backup** — respects SYNC_KEYS whitelist (only restores keys you know about):
```javascript
var importBtn = document.getElementById('importBtn');
var importFile = document.getElementById('importFile');
if (importBtn) importBtn.addEventListener('click', function() { importFile.click(); });
if (importFile) importFile.addEventListener('change', function(e) {
  var file = e.target.files[0];
  if (!file) return;
  var reader = new FileReader();
  reader.onload = function(ev) {
    try {
      var backup = JSON.parse(ev.target.result);
      var restored = 0;
      SYNC_KEYS.forEach(function(k) {
        if (backup[k] !== undefined && backup[k] !== null) {
          localStorage.setItem(k, typeof backup[k] === 'string' ? backup[k] : JSON.stringify(backup[k]));
          restored++;
        }
      });
      status.textContent = '✓ Restored ' + restored + ' key(s) from backup.';
      updateProgressUI();
      renderKeysList();
    } catch(err) {
      status.textContent = '✗ Import failed: ' + err.message;
    }
  };
  reader.readAsText(file);
});
```

**Reset all progress** — clears keys in SYNC_KEYS only (preserves theme, last-position, etc.):
```javascript
document.getElementById('resetBtn').addEventListener('click', function() {
  if (!confirm('Reset ALL Maternal-Newborn progress? This cannot be undone.')) return;
  SYNC_KEYS.forEach(function(k) {
    if (k !== 'nur2460_theme') localStorage.removeItem(k);  // preserve theme
  });
  status.textContent = '✓ All progress reset.';
  updateProgressUI();
  renderKeysList();
});
```

**Toggle panel open/close:**
```javascript
document.getElementById('storagePanelHead').addEventListener('click', function() {
  var panel = document.getElementById('storagePanel');
  panel.classList.toggle('open');
  if (panel.classList.contains('open')) renderKeysList();
});
```

**Modifier classes** (see PART 10.4):
- `.storage-panel.open` — collapse/expand state

**Per-subject changes:**
- `SYNC_KEYS` array must list every key the subject's files write that you want included in backup
- Filename prefix in download (`nur2460-backup-` for MN, `atipd-backup-` for PD, etc.)
- `_meta.source` text in export
- Reset confirmation message text
- Theme key name (preserved on reset)

### 6.9 Full Hub function catalog (~7 functions)

> ✅ **VERIFIED canonical against MN.** All listed function names exist in `Elevated ATI MN Hub.html`.

```
applyThemeUI()                  — Same as elsewhere
loadJson(key)                   — Read + JSON.parse value, returns {} on miss/error
countChecked(progressObj)       — Count entries where value > 0 (= chapters touched)
countDueCards()                 — Read FC schedule, count where dueDate <= today
updateProgressUI()              — Refresh subject card "X of N chapters" labels
renderKeysList()                — Build the list of storage keys with sizes
updatePickupPanel()             — Read last_chapter/last_template/fc_schedule, build pickup rows
```

---

### 6.10 Backup & Recovery Procedure

> *Consolidated from former Addendum F.6.*

#### F.6.1 User-side backup

User opens Hub → Storage panel → "Export backup" → JSON file downloads.

File contents (per PART 12.3):
```json
{
  "exportedAt": "2026-05-12T14:30:00.000Z",
  "subject": "mn",
  "version": 1,
  "data": {
    "nur2460_atimn_progress": "...",
    "nur2460_fc_schedule": "...",
    ...
  }
}
```

#### F.6.2 User-side restore

User → Storage panel → "Import backup" → select file → all keys overwrite current state.

#### F.6.3 Disaster recovery

If user reports "everything is gone":

```
1. Did they switch browsers or clear browser data?
   → localStorage is per-origin per-browser. Data only exists where set.

2. Did they have a backup?
   → Import → done.

3. No backup?
   → Recovery is limited to defaults (all unread, all unrated, no bookmarks).
   → The Book/Templates content itself is unaffected; only progress is lost.
```

#### F.6.4 Schema versioning for backups

Current `version: 1` in exports. If schema changes substantially, bump to `version: 2` and add import-side migration:

```javascript
document.getElementById('importFile').addEventListener('change', function(e) {
  var reader = new FileReader();
  reader.onload = function(evt) {
    var payload = JSON.parse(evt.target.result);
    if (payload.version === 1 && CURRENT_SCHEMA_VERSION === 2) {
      payload.data = migrateV1ToV2(payload.data);
    }
    Object.keys(payload.data).forEach(function(k) {
      localStorage.setItem(k, payload.data[k]);
    });
  };
  reader.readAsText(e.target.files[0]);
});
```

---

---

## PART 7 — BOOK FILE

This is where the bulk of work goes. The Book holds all chapter content but renders it via a hidden pool + modal pattern.

### 7.1 Document structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#d97706">
  <title>Elevated · ATI Maternal-Newborn Nursing Book</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>/* ~2000 lines of CSS */</style>
</head>
<body>

  <!-- Mobile-only floating buttons (hidden on desktop via display:none) -->
  <button class="sidebar-toggle" id="sidebarToggle" type="button" aria-label="Toggle navigation">☰</button>
  <a class="back-home-mobile" href="Elevated%20ATI%20MN%20Hub.html">← Back to Hub</a>
  <div class="sidebar-overlay" id="sidebarOverlay"></div>

  <div class="layout">
    <!-- SIDEBAR -->
    <aside class="sidebar" id="sidebar" aria-label="Book navigation">
      <!-- 7.2 — sidebar contents -->
    </aside>

    <!-- MAIN -->
    <main class="main-content">
      <!-- 7.3 — main contents -->
    </main>
  </div>

  <!-- CHAPTER MODAL OVERLAY -->
  <div class="modal-overlay" id="chapterModal" aria-hidden="true">
    <div class="modal" role="dialog" aria-labelledby="modalTitle">
      <div class="modal-header">
        <div class="modal-title-row">
          <div>
            <div class="modal-meta" id="modalMeta">Unit · Chapter</div>
            <h2 class="modal-title" id="modalTitle">Chapter</h2>
          </div>
          <button class="modal-close" id="modalClose" type="button" aria-label="Close chapter">×</button>
        </div>
        <div class="modal-controls">
          <button class="modal-fc-btn" id="modalFcBtn" type="button" title="Open flashcards for this chapter">
            🃏 <span>Flashcards for this chapter</span>
          </button>
          <div class="modal-tabs-wrap" id="modalTabsWrap">
            <nav class="modal-tabs" id="modalTabs" aria-label="Chapter sections"></nav>
          </div>
        </div>
      </div>
      <div class="modal-body" id="modalBody"></div>
    </div>
  </div>

  <!-- BOOKMARKS PANEL OVERLAY -->
  <div class="bookmarks-overlay" id="bookmarksOverlay" aria-hidden="true">
    <div class="bookmarks-panel" id="bookmarksPanel">
      <div class="bookmarks-header">
        <h2>⭐ Your Bookmarks</h2>
        <button class="bookmarks-close" id="bookmarksClose" type="button" aria-label="Close">×</button>
      </div>
      <div class="bookmarks-body" id="bookmarksBody">
        <div class="bookmarks-empty" id="bookmarksEmpty" hidden>
          <p>No bookmarks yet.</p>
          <p style="font-size:13px;margin-top:6px;">
            Click the ☆ button on any chapter section to bookmark it.
          </p>
        </div>
        <div id="bookmarksList"></div>
      </div>
    </div>
  </div>

  <!-- PRINT OVERLAY (dynamically populated) -->
  <div class="print-overlay" id="printOverlay" aria-hidden="true"></div>

  <!-- Tooltip popover for abbreviations (inserted at body level) -->
  <span class="abbr-tip-pop" id="abbrTipPop" hidden></span>

  <!-- 3 inline scripts -->
  <script>/* Script 1: Main book IIFE — see 7.21 */</script>
  <script>/* Script 2: BATCH 3 — NCLEX filter + answered tracking — see 7.12 */</script>
  <script>/* Script 3: Mid-read flashcard prompts — see 7.10 */</script>
</body>
</html>
```

### 7.2 Sidebar (complete)

**What this is:** Left rail showing units → chapters. Tap a chapter → opens chapter modal. Sticks at 280px on desktop; slides in from off-screen on mobile.

**Per-subject changes when porting:**
- `back-home` href → subject's Hub file
- `sb-course` text → "NUR 2460 · ATI" (or your subject's course code)
- `sb-title` text → subject's full title (e.g., "Maternal Newborn", "Nursing Care of Children")
- `sb-sub` text → edition number
- `.nav-section` count = subject's unit count (MN=4, PD=3, Pharm=13)
- `.nav-section-label` text = subject's unit names
- `.sidebar-item` count = subject's chapter count (MN=27, PD=44, Pharm=49)
- Each `data-section="chN"` references a valid chapter ID
- `.item-num` is two-digit zero-padded (`01`, `02`, …, `27`)

**Modifier class to preserve:** `.sidebar-item.populated` — every real chapter has this modifier (vs placeholder/empty). When rendering or copying elements, always preserve modifier classes (see PART 10.4).

```html
<aside class="sidebar" id="sidebar" aria-label="Book navigation">

  <div class="sidebar-header">
    <a class="back-home" href="Elevated%20ATI%20MN%20Hub.html">Back to Hub</a>
    <div class="sb-course">NUR 2460 · ATI</div>
    <div class="sb-title">Maternal Newborn</div>
    <div class="sb-sub">Edition 11 · Chunked Reference</div>
    <button id="themeToggle" type="button">
      <span id="themeIcon">☀️</span> <span id="themeLabel">Light Mode</span>
    </button>
  </div>

  <div class="sidebar-search">
    <input id="searchInput" type="text" placeholder="Search chapters &amp; content…" autocomplete="off">
    <div id="searchResults"></div>
  </div>

  <nav class="sidebar-list" aria-label="Chapters">

    <!-- Each unit is a collapsible nav-section -->
    <div class="nav-section collapsed" id="unit1">
      <div class="nav-section-label" data-toggle-section="unit1">
        Unit 1 — Antepartum <span class="caret">▾</span>
      </div>
      <a href="#ch1" class="sidebar-item populated" data-section="ch1">
        <span class="item-num">01</span>
        <span class="item-name">Contraception</span>
      </a>
      <a href="#ch2" class="sidebar-item populated" data-section="ch2">
        <span class="item-num">02</span>
        <span class="item-name">Infertility</span>
      </a>
      <!-- ... -->
    </div>

    <div class="nav-section collapsed" id="unit2">
      <div class="nav-section-label" data-toggle-section="unit2">
        Unit 2 — Intrapartum <span class="caret">▾</span>
      </div>
      <!-- ... -->
    </div>

    <!-- ... all 4 units ... -->
  </nav>
</aside>
```

**Sidebar styling:**
```css
.sidebar-header {
  padding: 18px 16px 14px;
  border-bottom: 1px solid var(--border);
  flex-shrink: 0;
}
.back-home {
  display: inline-block;
  font-size: 11px; font-weight: 600;
  color: var(--text2); text-decoration: none;
  letter-spacing: 0.03em;
  margin-bottom: 12px;
  transition: color .15s;
}
.back-home:hover { color: var(--accent); }
.sb-course {
  font-size: 10px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.12em;
  color: var(--text3);
  margin-bottom: 4px;
}
.sb-title {
  font-family: 'DM Serif Display', serif;
  font-size: 22px; font-weight: 400;
  color: var(--text);
  line-height: 1.1;
  margin-bottom: 2px;
}
.sb-sub {
  font-size: 11px; color: var(--text3);
  margin-bottom: 14px;
}
#themeToggle {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text2);
  padding: 6px 12px;
  border-radius: 6px;
  font-size: 11px; font-weight: 600;
  cursor: pointer;
  display: flex; align-items: center; gap: 6px;
  transition: all .15s;
}
#themeToggle:hover {
  border-color: var(--accent);
  color: var(--accent);
}

.sidebar-search {
  position: relative;
  padding: 0 12px 12px;
}
#searchInput {
  width: 100%;
  padding: 9px 12px;
  background: var(--surface2);
  border: 1px solid var(--border);
  color: var(--text);
  border-radius: 8px;
  font-size: 13px;
  font-family: inherit;
  transition: border-color .15s;
}
#searchInput:focus {
  outline: none;
  border-color: var(--accent);
}
#searchResults {
  position: absolute;
  top: 100%; left: 12px; right: 12px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  max-height: 320px;
  overflow-y: auto;
  z-index: 20;
  box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  display: none;
}
#searchResults.show { display: block; }
.search-result-item {
  display: block;
  padding: 10px 14px;
  border-bottom: 1px solid var(--border-soft);
  text-decoration: none;
  color: var(--text);
  font-size: 12px;
}
.search-result-item:hover { background: var(--surface2); }
.search-result-chapter {
  font-size: 10px; font-weight: 700;
  color: var(--accent);
  text-transform: uppercase; letter-spacing: 0.08em;
  margin-bottom: 2px;
}
.search-result-snippet { color: var(--text2); line-height: 1.4; }
.search-result-snippet mark {
  background: var(--accent-soft);
  color: var(--accent);
  padding: 0 2px;
}

.sidebar-list {
  flex: 1; overflow-y: auto;
  padding: 8px 0;
  scrollbar-width: thin;
  scrollbar-color: var(--border) transparent;
}

.nav-section { margin-bottom: 2px; }
.nav-section-label {
  padding: 14px 16px 4px;
  font-size: 10px; font-weight: 700;
  letter-spacing: .12em; text-transform: uppercase;
  color: var(--text3);
  cursor: pointer;
  display: flex; align-items: center; gap: 8px;
  user-select: none;
  transition: color .15s;
}
.nav-section-label:hover { color: var(--text2); }
.nav-section-label .caret {
  margin-left: auto;
  transition: transform .15s;
}
.nav-section.collapsed .caret { transform: rotate(-90deg); }
.nav-section.collapsed .sidebar-item { display: none; }

.sidebar-item {
  padding: 8px 16px;
  font-size: 13px; color: var(--text2);
  cursor: pointer;
  display: flex; align-items: center; gap: 8px;
  border-radius: 6px;
  margin: 0 8px;
  text-decoration: none;
  transition: background .12s, color .12s;
}
.sidebar-item:hover {
  background: var(--surface2);
  color: var(--text);
}
.sidebar-item.populated .item-num {
  color: var(--accent);
  font-weight: 600;
}
.sidebar-item:not(.populated) { opacity: 0.5; }
.item-num {
  font-size: 10px; font-weight: 700;
  letter-spacing: 0.04em;
  min-width: 18px;
}
.item-name {
  font-size: 13px;
  line-height: 1.3;
}
.sidebar-item.active {
  background: var(--accent-soft);
  color: var(--accent);
}
```

### 7.3 Main content area (complete)

```html
<main class="main-content">

  <div class="main-course">NUR 2460 · ATI Edition 11</div>
  <h1 class="main-title">Maternal <em>Newborn</em></h1>
  <p class="main-desc">
    Chapter-by-chapter chunked reference. Designed to replace the PDF for active study —
    every populated chapter has a TL;DR card, sectioned content, exercises, and
    abbreviation tooltips. Click a chapter to open it. Track your reading with
    the checkboxes — single tap = reviewed, double tap = complete.
  </p>

  <!-- Bookmarks button -->
  <button class="bookmarks-open-btn" id="bookmarksOpenBtn" type="button">
    ⭐ <span>Bookmarks</span>
    <span class="bookmarks-count-badge" id="bookmarksCountBadge">0</span>
  </button>

  <!-- Master print button -->
  <button class="compare-btn" id="masterPrintBtn">🖨️ Print Chapters</button>

  <div class="section-divider">Reading Progress</div>

  <!-- Unit accordions -->
  <div class="unit-accordion collapsed" id="unit1acc">
    <div class="unit-header" data-toggle-unit="unit1acc">
      <span class="unit-caret">▾</span>
      <span class="unit-title">Unit 1 — Antepartum</span>
      <button class="part-print-btn" data-print-unit="unit1acc" title="Print this unit as PDF">⎙</button>
      <span class="unit-count" id="unit1count">0 / 10 read</span>
      <div class="unit-bar-wrap">
        <div class="unit-bar-outer">
          <div class="unit-bar-partial" id="unit1barpartial" style="width:0%"></div>
          <div class="unit-bar-inner" id="unit1bar" style="width:0%"></div>
        </div>
      </div>
    </div>
    <div class="unit-body">
      <div class="planner-row populated" data-id="ch1">
        <div class="planner-check" data-toggle-check="ch1"></div>
        <span class="planner-num">1</span>
        <span class="planner-name" data-open-chapter="ch1">Contraception</span>
        <span class="planner-src">5 pages · 6 categories of methods</span>
        <button class="planner-go" data-open-chapter="ch1">Read</button>
      </div>
      <!-- ... one planner-row per chapter ... -->
      <div class="exam-reset">
        <button data-reset-unit="unit1acc">Reset Unit Progress</button>
      </div>
    </div>
  </div>
  <!-- ... one unit-accordion per unit ... -->

  <!-- CHAPTER POOL — hidden, contains all chapter content -->
  <div class="chapter-pool" id="chapterPool">
    <section class="chapter" id="ch1"> ... </section>
    <section class="chapter" id="ch2"> ... </section>
    <!-- ... -->
  </div>

  <footer class="page-footer">
    <p>ATI RN Maternal Newborn Nursing · 11th Edition · Chunked chapter-by-chapter reference</p>
    <p>Elevated · ATI Maternal-Newborn Companion · sleepyius.github.io/NUR2460/</p>
  </footer>
</main>
```

**Main content styling:**
```css
.main-content {
  margin-left: 280px;
  flex: 1; min-width: 0;
  padding: 36px 32px 80px;
  max-width: 820px;
}
.main-course {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.12em;
  color: var(--accent);
  margin-bottom: 8px;
}
.main-title {
  font-family: 'DM Serif Display', serif;
  font-size: 44px; font-weight: 400; line-height: 1.05;
  margin-bottom: 14px;
  color: var(--text);
  letter-spacing: -0.005em;
}
.main-title em {
  font-style: italic;
  color: var(--accent);
}
.main-desc {
  font-size: 14.5px; color: var(--text2);
  line-height: 1.6;
  margin-bottom: 28px;
  max-width: 680px;
}
.bookmarks-open-btn {
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--text);
  padding: 8px 14px;
  font-size: 13px;
  border-radius: 8px;
  cursor: pointer;
  display: inline-flex; align-items: center; gap: 8px;
  margin-right: 8px; margin-bottom: 18px;
  transition: all .15s;
}
.bookmarks-open-btn:hover { border-color: var(--accent); }
.bookmarks-count-badge {
  display: inline-block;
  background: var(--accent);
  color: var(--bg);
  font-size: 11px; font-weight: 700;
  padding: 1px 7px;
  border-radius: 99px;
  min-width: 18px;
  text-align: center;
}
.bookmarks-count-badge:empty { display: none; }
.compare-btn {
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--text);
  padding: 8px 14px;
  font-size: 13px;
  border-radius: 8px;
  cursor: pointer;
  margin-bottom: 18px;
  transition: all .15s;
}
.compare-btn:hover { border-color: var(--accent); }

.section-divider {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: var(--text3);
  margin: 32px 0 12px;
  padding-top: 12px;
  border-top: 1px solid var(--border-soft);
}

.unit-accordion {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 14px;
  margin-bottom: 14px;
  overflow: hidden;
}
.unit-header {
  padding: 18px 22px;
  display: flex; align-items: center; gap: 14px;
  cursor: pointer; user-select: none;
  transition: background .15s;
  flex-wrap: wrap;
}
.unit-header:hover { background: var(--surface2); }
.unit-caret {
  font-size: 12px; color: var(--text3);
  transition: transform .15s;
  flex-shrink: 0;
}
.unit-accordion.collapsed .unit-caret { transform: rotate(-90deg); }
.unit-title {
  font-family: 'DM Serif Display', serif;
  font-size: 18px; font-weight: 400;
  color: var(--text);
  flex: 1;
}
.part-print-btn {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text3);
  width: 28px; height: 28px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
  transition: all .15s;
}
.part-print-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.unit-count {
  font-size: 11px; color: var(--text3);
  white-space: nowrap;
}
.unit-bar-wrap {
  flex-basis: 100%;
  margin-top: 6px;
}
.unit-bar-outer {
  width: 100%; height: 8px;
  background: var(--bg);
  border-radius: 99px;
  overflow: hidden;
  position: relative;
}
.unit-bar-partial {
  position: absolute; top: 0; left: 0;
  height: 100%;
  background: var(--accent-soft);
  transition: width .25s;
}
.unit-bar-inner {
  position: absolute; top: 0; left: 0;
  height: 100%;
  background: var(--accent);
  transition: width .25s;
}
.unit-body {
  border-top: 1px solid var(--border);
  padding: 8px 0;
}
.unit-accordion.collapsed .unit-body { display: none; }

.planner-row {
  display: flex; align-items: center;
  padding: 10px 18px; gap: 12px;
  border-bottom: 1px solid var(--border);
  transition: background .1s;
}
.planner-row:last-of-type { border-bottom: none; }
.planner-row:hover { background: var(--surface2); }
.planner-row:not(.populated) { opacity: 0.5; }
.planner-row:not(.populated) .planner-go { pointer-events: none; }

.planner-check {
  width: 20px; height: 20px;
  border-radius: 6px;
  border: 2px solid var(--border);
  background: var(--bg);
  cursor: pointer;
  flex-shrink: 0;
  display: flex; align-items: center; justify-content: center;
  transition: all .15s;
  font-size: 12px; color: transparent;
}
.planner-check.reviewed {
  border-color: var(--accent);
  background: var(--accent-soft);
}
.planner-check.complete {
  border-color: var(--accent);
  background: var(--accent);
  color: var(--bg);
}
.planner-check.complete::after { content: '✓'; }

.planner-num {
  font-size: 11px; font-weight: 700;
  color: var(--text3);
  min-width: 18px;
}
.planner-name {
  flex: 1;
  font-size: 14px; color: var(--text);
  cursor: pointer;
}
.planner-name:hover { color: var(--accent); }
.planner-src {
  font-size: 11px; color: var(--text3);
  white-space: nowrap;
}
.planner-go {
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--accent);
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 12px; font-weight: 600;
  cursor: pointer;
  transition: all .15s;
}
.planner-go:hover {
  background: var(--accent);
  color: var(--bg);
  border-color: var(--accent);
}

.exam-reset {
  padding: 10px 18px;
  text-align: right;
  border-top: 1px solid var(--border-soft);
}
.exam-reset button {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text3);
  padding: 5px 12px;
  border-radius: 6px;
  font-size: 11px;
  cursor: pointer;
  transition: all .15s;
}
.exam-reset button:hover {
  border-color: var(--nonreassuring);
  color: var(--nonreassuring);
}
```

### 7.4 Chapter-pool pattern

```css
.chapter-pool {
  display: none;          /* THIS IS THE CRITICAL RULE — without it everything renders */
}
.chapter { /* container for one chapter's content */ }
```

The pool sits in the document so JS can `querySelector` chapters by ID. But `display: none` hides ALL of it — chapters only become visible inside the modal when opened.

**Critical structural rule:** The pool's outer `</div>` must be the LAST `</div>` before `</main>`. Any `<div>` opened inside a chapter must have a matching `</div>` before the next chapter starts. Imbalance → chapter-pool closes early → all subsequent chapters leak into the visible page.

**Verification snippet:**
```python
import re

def check_pool_integrity(content):
    pool_open = content.find('<div class="chapter-pool"')
    # Walk div depth from here
    depth = 0; i = pool_open; pool_close = -1
    while i < len(content):
        if content[i:i+4] == '<div':
            depth += 1; i = content.find('>', i) + 1
        elif content[i:i+6] == '</div>':
            depth -= 1; i += 6
            if depth == 0: pool_close = i; break
        else: i += 1
    pool_content = content[pool_open:pool_close]
    chapters_in_pool = len(re.findall(r'<section class="chapter" id="ch\d+">', pool_content))
    chapters_total = len(re.findall(r'<section class="chapter" id="ch\d+">', content))
    return chapters_in_pool == chapters_total, chapters_in_pool, chapters_total
```

### 7.5 Chapter content structure

Every chapter follows this exact pattern:

```html
<section class="chapter" id="ch1">

  <!-- BANNER (consumed by modal header — not a tab) -->
  <div class="chapter-banner">
    <div class="chapter-meta">Unit 1 · Antepartum · Chapter 1</div>
    <h2 class="chapter-name"><em>Contraception</em></h2>
    <p class="chapter-lede">
      Contraception decisions integrate client autonomy, medical history, and effectiveness.
      Methods range from natural (least effective) to surgical sterilization (most effective).
      Only condoms protect against STIs.
    </p>
  </div>

  <!-- TAB 1: TL;DR -->
  <section id="ch1-tldr" class="brief-card">
    <h2>TL;DR · One-glance summary</h2>
    <p class="tldr">
      Contraception choice = client autonomy + medical history. Highest effectiveness:
      <strong>LARCs (IUDs and implants)</strong> &gt; sterilization &gt; injectable &gt;
      pill/patch/ring &gt; barrier &gt; natural. <strong>Only condoms protect against STIs.</strong>
    </p>
    <div class="brief-grid">
      <div>
        <h3>The six categories</h3>
        <ul>
          <li><strong>Natural family planning</strong> — abstinence, withdrawal, calendar, BBT</li>
          <li><strong>Barrier</strong> — condoms, diaphragm, cervical cap, sponge</li>
          <li><strong>Hormonal</strong> — pill, patch, ring, injection</li>
          <li><strong>IUD</strong> — copper (10y) or hormonal (3-8y)</li>
          <li><strong>Surgical</strong> — tubal ligation, vasectomy</li>
          <li><strong>Emergency</strong> — levonorgestrel, ulipristal, copper IUD</li>
        </ul>
      </div>
      <div>
        <h3>Key contraindications</h3>
        <ul>
          <li><strong>Estrogen-containing:</strong> Smoker &gt;35, hx thromboembolism, breast cancer, migraine with aura</li>
          <li><strong>IUD:</strong> active PID, pregnancy, undiagnosed bleeding</li>
          <li><strong>DMPA injection:</strong> decreases bone density with prolonged use</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- TABS 2..N: content sections -->
  <section id="ch1-natural" class="content-section">
    <h2>Natural Family Planning</h2>
    <p class="section-lead">
      Fertility-awareness based methods — no hormones, no devices.
      Effectiveness depends entirely on adherence and accurate cycle tracking.
      <strong>None protect against STIs.</strong>
    </p>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">Abstinence</h3>
        <span class="condition-tag">Most effective method</span>
      </header>
      <p>Refraining from sexual intercourse eliminates the possibility of sperm entering the vagina.</p>
      <div class="finding-grid">
        <div class="finding-card">
          <h4>Advantages</h4>
          <ul>
            <li>100% effective when followed</li>
            <li>Eliminates STI risk</li>
            <li>No cost, no side effects</li>
          </ul>
        </div>
        <div class="finding-card">
          <h4>Disadvantages</h4>
          <ul>
            <li>Requires self-control</li>
            <li>High failure rate from non-adherence</li>
          </ul>
        </div>
      </div>
    </article>

    <!-- More condition-blocks -->

    <!-- Inline mid-read prompt (concept/warning/calc type) -->
    <aside class="mid-read"
      data-fc-id="fc-ch1-natural-calendar"
      data-fc-ch="1"
      data-fc-type="calc"
      data-fc-anchor="ch1-natural"
      data-fc-q="How do you calculate the fertile window using the calendar method?"
      data-fc-a="<strong>Start</strong> = shortest cycle length − <strong>18 days</strong><br><strong>End</strong> = longest cycle length − <strong>11 days</strong><br><em>Example:</em> 26-day shortest, 30-day longest → fertile days 8 through 19.">
      <div class="mid-read-q">How do you calculate the fertile window using the calendar method?</div>
      <button class="mid-read-reveal" type="button">Reveal answer</button>
      <div class="mid-read-a">
        <strong>Start</strong> = shortest cycle length − <strong>18 days</strong><br>
        <strong>End</strong> = longest cycle length − <strong>11 days</strong><br>
        <em>Example:</em> 26-day shortest, 30-day longest → fertile days 8 through 19.
      </div>
      <div class="mid-read-rate">
        <button data-rate="0">Hard<span class="mid-read-rate-small">+1 day</span></button>
        <button data-rate="3">Good<span class="mid-read-rate-small">extend</span></button>
        <button data-rate="5">Easy<span class="mid-read-rate-small">boost</span></button>
      </div>
    </aside>
  </section>

  <section id="ch1-barrier" class="content-section"> ... </section>
  <section id="ch1-hormonal" class="content-section"> ... </section>
  <section id="ch1-iud" class="content-section"> ... </section>
  <section id="ch1-surgical" class="content-section"> ... </section>

  <!-- ALS -->
  <section id="ch1-als" class="content-section">
    <h2>Active Learning Scenario</h2>
    <p class="section-lead">
      From the book — uses the <strong>ATI Basic Concept</strong> template.
      Practice answering before reviewing the key.
    </p>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">Scenario</h3>
      </header>
      <p><em>A nurse is teaching a client about combined oral contraceptives. The client expresses concerns about side effects. What information should the nurse include in the teaching? Use the ATI Active Learning Template: Basic Concept to complete this item.</em></p>
      <ul>
        <li><strong>Related Content:</strong> Describe at least 3 expected side effects</li>
        <li><strong>Underlying Principles:</strong> Explain the hormonal mechanism</li>
        <li><strong>Nursing Interventions:</strong> Identify essential teaching points</li>
      </ul>
    </article>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">Answer key</h3>
      </header>
      <div class="finding-grid">
        <div class="finding-card">
          <h4>Related Content (3 examples)</h4>
          <ul>
            <li>Breast tenderness</li>
            <li>Nausea (often resolves in 1-3 months)</li>
            <li>Breakthrough bleeding</li>
          </ul>
        </div>
        <div class="finding-card">
          <h4>Underlying Principles</h4>
          <p>Synthetic estrogen + progestin suppress LH/FSH → no ovulation. Side effects mirror pregnancy hormones.</p>
        </div>
      </div>
      <div class="kb-card">
        <h4>Nursing Interventions</h4>
        <ul>
          <li>Take at same time daily for max effectiveness</li>
          <li>Use backup contraception for first 7 days</li>
          <li>Report severe headaches, chest pain, leg pain (clot warning)</li>
          <li>No protection against STIs — use condoms</li>
        </ul>
      </div>
    </article>
  </section>

  <!-- EXERCISES -->
  <section id="ch1-exercises" class="content-section">
    <h2>Practice · Application Exercises</h2>
    <p class="section-lead">
      5 NCLEX-style questions covering Ch 1 core content.
      Click each exercise to reveal rationales and NCLEX category.
    </p>

    <article class="exercise" data-q-id="ch1-q1">
      <header class="exercise-q" data-toggle>
        <span class="q-num">Q1</span>
        <p>A nurse is teaching a client about combined oral contraceptives. Which of the following statements by the client indicates an understanding of the teaching?</p>
        <ol class="q-options">
          <li>A. "I should take the pill at the same time each day to maximize effectiveness."</li>
          <li>B. "I can skip pills as long as I take two the next day."</li>
          <li>C. "The pill protects me from sexually transmitted infections."</li>
          <li>D. "I should stop the pill if I notice any breast tenderness."</li>
        </ol>
        <span class="q-toggle">Show rationale ▾</span>
      </header>
      <div class="exercise-a">
        <p class="answer correct">
          <span class="ans-letter">A.</span> <strong>CORRECT.</strong>
          Taking COCs at the same time daily maintains stable hormone levels.
        </p>
        <p class="answer">
          <span class="ans-letter">B.</span> Skipping pills risks ovulation. Two pills the next day is not the correct catch-up.
        </p>
        <p class="answer">
          <span class="ans-letter">C.</span> COCs do <strong>NOT</strong> protect against STIs.
        </p>
        <p class="answer">
          <span class="ans-letter">D.</span> Breast tenderness is expected and not a reason to stop.
        </p>
        <span class="nclex-tag">NCLEX · Pharmacological &amp; Parenteral Therapies · Expected Actions/Outcomes</span>
      </div>
    </article>

    <!-- 4 more questions, same pattern -->
  </section>

  <!-- TEMPLATES BRIDGE -->
  <section id="ch1-templates" class="content-section tpl-bridge">
    <h2>ATI Templates · this chapter</h2>
    <ul>
      <li><a href="Elevated%20ATI%20MN%20Templates.html#ex-ch1-cocs">Combined Oral Contraceptives (COCs)</a></li>
      <li><a href="Elevated%20ATI%20MN%20Templates.html#ex-ch1-vasectomy">Vasectomy</a></li>
    </ul>
  </section>

</section><!-- /ch1 -->
```

### 7.6 Modal mechanism (full)

```javascript
function openChapter(chapterId, initialTabId) {
  var pool = document.getElementById('chapterPool');
  var chapter = pool.querySelector('#' + chapterId);
  if (!chapter) return;

  var modalOverlay = document.getElementById('chapterModal');
  var modalMeta = document.getElementById('modalMeta');
  var modalTitle = document.getElementById('modalTitle');
  var modalTabs = document.getElementById('modalTabs');
  var modalBody = document.getElementById('modalBody');

  // 1. Banner → modal header
  var meta = chapter.querySelector('.chapter-meta');
  var name = chapter.querySelector('.chapter-name');
  modalMeta.textContent = meta ? meta.textContent : '';
  modalTitle.innerHTML = name ? name.innerHTML : 'Chapter';

  // 2. Iterate direct child <section>s with IDs — these become tabs
  var sections = chapter.querySelectorAll(':scope > section[id]');
  modalTabs.innerHTML = '';
  modalBody.innerHTML = '';

  var firstId = null;
  sections.forEach(function(section, i) {
    if (i === 0) firstId = section.id;

    // Tab button
    var btn = document.createElement('button');
    btn.type = 'button';
    btn.className = 'tab-btn';
    btn.dataset.tabFor = section.id;
    btn.textContent = buildTabLabel(section, i);
    modalTabs.appendChild(btn);

    // Cloned panel
    var panel = section.cloneNode(true);
    panel.classList.add('tab-panel');
    modalBody.appendChild(panel);
  });

  // 3. Activate initial tab
  var activeTabId = (initialTabId && modalBody.querySelector('#' + initialTabId))
                    ? initialTabId : firstId;
  if (activeTabId) {
    var activeBtn = modalTabs.querySelector('[data-tab-for="' + activeTabId + '"]');
    if (activeBtn) activeBtn.classList.add('active');
    var activePanel = modalBody.querySelector('#' + activeTabId);
    if (activePanel) activePanel.classList.add('active');
  }

  // 4. Tab click → switch active
  modalTabs.querySelectorAll('.tab-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var targetId = btn.dataset.tabFor;
      modalTabs.querySelectorAll('.tab-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      modalBody.querySelectorAll('.tab-panel').forEach(function(p) { p.classList.remove('active'); });
      var panel = modalBody.querySelector('#' + targetId);
      if (panel) panel.classList.add('active');
      modalBody.scrollTop = 0;
      btn.scrollIntoView({ inline: 'nearest', block: 'nearest', behavior: 'smooth' });
    });
  });

  // 5. Re-bind interactive elements on cloned content
  bindAbbrs(modalBody);
  bindExercises(modalBody);
  bindMidReads(modalBody);
  injectBookmarkButtons(modalBody, chapterId);
  injectNclexFilterBar(modalBody, chapterId);

  // 6. Show modal
  modalOverlay.classList.add('show');
  modalOverlay.setAttribute('aria-hidden', 'false');
  document.body.classList.add('modal-open');
  modalBody.scrollTop = 0;

  // 7. Mobile: close sidebar
  if (window.innerWidth <= 900) closeSidebarPanel();

  // 8. Update tab strip fades after scroll
  setTimeout(function() {
    var btn = modalTabs.querySelector('[data-tab-for="' + activeTabId + '"]');
    if (btn) btn.scrollIntoView({ inline: 'nearest', block: 'nearest' });
    updateTabFade();
  }, 50);

  // 9. Record for "last chapter" cross-tool sync
  recordLastChapter(chapterId, activeTabId);

  // 10. Update URL hash without triggering scroll
  history.replaceState(null, '', '#' + activeTabId);
}

function buildTabLabel(section, index) {
  if (section.classList.contains('brief-card')) return 'TL;DR';
  if (section.classList.contains('tpl-bridge')) return 'Templates';
  if (section.id && /-exercises$/.test(section.id)) return 'Practice';
  var h2 = section.querySelector('h2');
  var label = h2 ? h2.textContent.trim() : ('Section ' + (index + 1));
  if (label.length > 28) label = label.substring(0, 26) + '…';
  return label;
}

function closeChapterModal() {
  var modalOverlay = document.getElementById('chapterModal');
  modalOverlay.classList.remove('show');
  modalOverlay.setAttribute('aria-hidden', 'true');
  document.body.classList.remove('modal-open');
  // Clear hash without scrolling
  history.replaceState(null, '', window.location.pathname + window.location.search);
}

// Close handlers
document.getElementById('modalClose').addEventListener('click', closeChapterModal);
document.getElementById('chapterModal').addEventListener('click', function(e) {
  if (e.target === this) closeChapterModal();  // click on overlay (not modal content)
});
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape' && document.getElementById('chapterModal').classList.contains('show')) {
    closeChapterModal();
  }
});

// Tab strip scroll → update fade
document.getElementById('modalTabsWrap').addEventListener('scroll', updateTabFade);
```

### 7.7 Brief-card (TL;DR)

```css
.brief-card {
  background: linear-gradient(135deg, var(--surface) 0%, var(--surface2) 100%);
  border: 1px solid var(--border);
  border-radius: 14px;
  padding: 28px;
  margin-bottom: 40px;
  position: relative;
  overflow: hidden;
}
.brief-card h2 {
  font-family: 'DM Sans', sans-serif;
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.15em;
  color: var(--accent);
  margin: 0 0 14px;
}
.brief-card .tldr {
  font-size: 17px; line-height: 1.55;
  color: var(--text);
  margin: 0 0 24px;
  font-weight: 400;
}
.brief-card .tldr strong { color: var(--accent2); }

.brief-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
.brief-grid h3 {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: var(--accent2);
  margin: 0 0 10px;
}
.brief-grid ul { margin: 0; padding-left: 18px; }
.brief-grid li {
  font-size: 13.5px; line-height: 1.55;
  margin-bottom: 6px;
  color: var(--text2);
}
.brief-grid li strong { color: var(--text); }

@media (max-width: 700px) {
  .brief-grid { grid-template-columns: 1fr; }
  .brief-card .tldr { font-size: 15px; }
}
```

### 7.8 Content sections & condition blocks

```css
.content-section {
  margin-bottom: 48px;
  scroll-margin-top: 100px;
}
.content-section h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 24px; font-weight: 400;
  margin: 0 0 8px;
  color: var(--text);
}
.section-lead {
  font-size: 14.5px; line-height: 1.6;
  color: var(--text2);
  margin: 0 0 18px;
  max-width: 680px;
}

/* Condition block — one topic/condition */
.condition-block {
  margin: 28px 0;
}
.condition-head {
  display: flex; flex-wrap: wrap; align-items: baseline;
  gap: 10px 14px;
  margin: 0 0 12px;
  padding-bottom: 10px;
  border-bottom: 1px solid var(--border-soft);
}
.condition-name {
  font-family: 'DM Serif Display', serif;
  font-weight: 400;
  font-size: 20px; line-height: 1.25;
  color: var(--text);
  margin: 0;
  flex: 1; min-width: 200px;
}
.condition-tag {
  font-size: 11px; font-weight: 600;
  color: var(--accent2);
  background: var(--accent-soft);
  padding: 4px 10px;
  border-radius: 6px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  white-space: nowrap;
}

/* Finding grid — bullet groups within a condition */
.finding-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
  gap: 12px;
  margin: 14px 0 0;
}
.finding-card {
  background: var(--surface2);
  border: 1px solid var(--border-soft);
  border-radius: 10px;
  padding: 14px 16px;
}
.finding-card h4 {
  font-size: 12px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.06em;
  color: var(--accent2);
  margin: 0 0 8px;
}
.finding-card ul { margin: 0; padding-left: 16px; }
.finding-card li {
  font-size: 13.5px; line-height: 1.55;
  margin-bottom: 4px;
  color: var(--text2);
}
.finding-card li strong { color: var(--text); }
.finding-card p {
  font-size: 13.5px; line-height: 1.55;
  color: var(--text2);
  margin: 0 0 8px;
}

/* Knowledge box — a single emphasis block */
.kb-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-left: 3px solid var(--accent);
  border-radius: 14px;
  padding: 20px 22px;
  margin: 18px 0;
  position: relative;
  transition: border-color .15s ease;
}
.kb-card h4 {
  font-size: 12px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.06em;
  color: var(--accent);
  margin: 0 0 10px;
}
.kb-card p {
  font-size: 14px; line-height: 1.6;
  color: var(--text);
  margin: 0 0 8px;
}
.kb-card ul { margin: 0; padding-left: 18px; }
.kb-card li {
  font-size: 14px; line-height: 1.55;
  margin-bottom: 4px;
}

/* Flag (warning indicator inside finding cards) */
.flag {
  color: var(--nonreassuring);
  font-weight: 600;
}
```

### 7.9 Inline mid-read prompts (3 types: concept / warning / calc)

These are MANUALLY placed in chapter content. They appear inline as content flows.

```html
<aside class="mid-read"
  data-fc-id="fc-ch1-spinnbarkeit"
  data-fc-ch="1"
  data-fc-type="concept"
  data-fc-anchor="ch1-natural"
  data-fc-q="What is the spinnbarkeit sign?"
  data-fc-a="The ability of cervical mucus to <strong>stretch between the fingers</strong>. Greatest stretch occurs at <strong>ovulation</strong> (thin, slippery, clear, stretchable mucus indicates fertile window).">

  <div class="mid-read-q">What is the spinnbarkeit sign?</div>
  <button class="mid-read-reveal" type="button">Reveal answer</button>
  <div class="mid-read-a">
    The ability of cervical mucus to <strong>stretch between the fingers</strong>.
    Greatest stretch occurs at <strong>ovulation</strong> (thin, slippery, clear, stretchable mucus indicates fertile window).
  </div>
  <div class="mid-read-rate">
    <button data-rate="0">Hard<span class="mid-read-rate-small">+1 day</span></button>
    <button data-rate="3">Good<span class="mid-read-rate-small">extend</span></button>
    <button data-rate="5">Easy<span class="mid-read-rate-small">boost</span></button>
  </div>
</aside>
```

**Four subtypes** via `data-fc-type` (revised in v3 — `priority` was discovered to have native CSS support):

- `concept` — factual recall (most common; ~84 instances in Pharm)
- `warning` — safety/danger flag (most common in Pharm: ~107 instances after inline batches)
- `calc` — calculation/formula (rare; 3 instances in Pharm)
- `priority` — highest-urgency, time-critical action (new in v3 Pharm work; 4 instances in Pharm: NTG attack protocol, torsades + IV magnesium, hemolytic transfusion reaction, IV potassium safety rules)

**Why `priority` exists separately from `warning`:** The Flashcards CSS already defined `.flashcard-priority` and `.browse-priority` classes with the `--prompt-priority` red color (`#e05c6a` dark / `#c0384a` light) — distinct from `warning`. This was used historically by the typed-prompt category but had no inline cards until v3 Pharm. Use `priority` sparingly — reserve for cards where the answer is *"do X immediately or someone dies"* (drug overdose protocols, transfusion-reaction actions, lethal interactions). For "don't do X" safety teaching (which is most safety content), `warning` is appropriate.

**Target density (per chapter):**

The MN model has 122 inline mid-reads + 54 typed prompts across 27 chapters = 176 prompts total, averaging **6.5 per chapter**. This density defines the intended pedagogical pace.

```
Inline mid-reads:  3–6 per chapter (place mid-paragraph at natural pause points)
Typed mid-prompts: 2 per chapter (one mid-chapter, one near end)
TOTAL:             5–8 prompts per chapter
```

**A chapter with zero inline mid-reads is NOT minimalist by design — it is incomplete.** When porting MN → PD initially, this density spec was not documented, and the result was PD chapters with 0 inline mid-reads (PD had only the 2-per-chapter typed prompts = 88 total, vs MN's 176). The bug only became visible when someone audited against MN.

**Distribution within each chapter:**
- At least 1 `warning` per chapter (safety-critical concept)
- 1–2 `concept` per chapter (definition/principle to anchor)
- 0–2 `calc` per chapter (only if chapter has math: drug dosing, FHR ranges, GA wheel, BMI, etc.)
- Distribute across the chapter's content sections — NOT all in one section
- Place mid-paragraph where they naturally fit, not as section dividers

**STARTER_DECK constraint:** Every inline `<aside class="mid-read">` should have a matching entry in the Flashcards file's STARTER_DECK array, so the user can load a pre-built deck without having to read every chapter first. The Hub's "Starter Cards" stat should equal STARTER_DECK length. After porting, verify these numbers match.

**CSS:**
```css
.mid-read {
  margin: 26px 0;
  padding: 20px 22px;
  background: linear-gradient(135deg, var(--surface), var(--surface2));
  border-left: 3px solid var(--accent2);
  border-radius: 0 12px 12px 0;
  position: relative;
}
.mid-read[data-fc-type="warning"] {
  border-left-color: var(--nonreassuring);
  background: linear-gradient(135deg, var(--surface), var(--nonreassuring-bg));
}
.mid-read[data-fc-type="calc"] {
  border-left-color: var(--prompt-content);
  background: linear-gradient(135deg, var(--surface), var(--prompt-content-bg));
}
.mid-read::before {
  content: 'QUICK CHECK';
  position: absolute; top: -10px; left: 16px;
  background: var(--surface);
  padding: 0 8px;
  font-size: 9px; font-weight: 700;
  letter-spacing: 0.15em;
  color: var(--accent2);
  text-transform: uppercase;
}
.mid-read[data-fc-type="warning"]::before {
  content: 'SAFETY ALERT';
  color: var(--nonreassuring);
}
.mid-read[data-fc-type="calc"]::before {
  content: 'CALCULATION';
  color: var(--prompt-content);
}
.mid-read-q {
  font-size: 14.5px; font-weight: 500;
  color: var(--text);
  margin-bottom: 12px;
  line-height: 1.5;
}
.mid-read-reveal {
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--accent2);
  padding: 6px 14px;
  font-size: 12px; font-weight: 600;
  border-radius: 6px;
  cursor: pointer;
  transition: all .15s;
}
.mid-read-reveal:hover {
  background: var(--accent-soft);
  border-color: var(--accent2);
}
.mid-read-a {
  display: none;
  margin-top: 12px;
  font-size: 14px; line-height: 1.6;
  color: var(--text);
  padding: 12px 16px;
  background: var(--bg);
  border-radius: 8px;
}
.mid-read.revealed .mid-read-a { display: block; }
.mid-read.revealed .mid-read-reveal { display: none; }
.mid-read-rate {
  display: none;
  margin-top: 12px;
  gap: 8px;
  flex-wrap: wrap;
}
.mid-read.revealed .mid-read-rate { display: flex; }
.mid-read-rate button {
  flex: 1; min-width: 90px;
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--text);
  padding: 8px 12px;
  border-radius: 6px;
  font-size: 13px; font-weight: 600;
  cursor: pointer;
  display: flex; flex-direction: column;
  align-items: center; gap: 2px;
  transition: all .15s;
}
.mid-read-rate-small {
  font-size: 10px; color: var(--text3);
  font-weight: 400;
}
.mid-read-rate button[data-rate="0"]:hover { border-color: var(--nonreassuring); color: var(--nonreassuring); }
.mid-read-rate button[data-rate="3"]:hover { border-color: var(--accent2); color: var(--accent2); }
.mid-read-rate button[data-rate="5"]:hover { border-color: var(--reassuring); color: var(--reassuring); }
.mid-read.rated {
  border-left-color: var(--reassuring);
  opacity: 0.85;
}
.mid-read.rated::after {
  content: '✓ in deck';
  position: absolute; top: -10px; right: 16px;
  background: var(--surface);
  padding: 0 8px;
  font-size: 9px; font-weight: 700;
  letter-spacing: 0.1em;
  color: var(--reassuring);
}
```

**JS handler:**
```javascript
function bindMidReads(root) {
  (root || document).querySelectorAll('.mid-read').forEach(function(aside) {
    if (aside.dataset.bound) return;
    aside.dataset.bound = '1';

    var reveal = aside.querySelector('.mid-read-reveal');
    if (reveal) {
      reveal.addEventListener('click', function() {
        aside.classList.add('revealed');
      });
    }

    aside.querySelectorAll('.mid-read-rate button').forEach(function(btn) {
      btn.addEventListener('click', function() {
        var rating = parseInt(btn.dataset.rate, 10);
        rateMidRead(aside, rating);
        aside.classList.add('rated');
      });
    });
  });
}

function rateMidRead(asideEl, rating) {
  var schedule = loadFcSchedule();
  var fcId = asideEl.dataset.fcId;
  var card = schedule[fcId] || {
    id: fcId,
    chapter: asideEl.dataset.fcCh,
    type: asideEl.dataset.fcType,
    anchor: asideEl.dataset.fcAnchor,
    prompt: asideEl.dataset.fcQ,
    answer: asideEl.dataset.fcA,
    reps: 0,
    ef: 2.5,
    interval: 1
  };
  sm2Update(card, rating);
  card.nextReview = new Date(Date.now() + card.interval * 86400000).toISOString();
  card.lastRated = new Date().toISOString();
  schedule[fcId] = card;
  saveFcSchedule(schedule);
}
```

### 7.10 Injected typed prompts (4 types: CONTENT / JUDGMENT / PRINCIPLE / PRIORITY)

These represent the **ATI clinical-judgment framework**. They're stored in a JavaScript object and injected by a separate script after the modal builds.

**Data structure:**
```javascript
var MID_PROMPTS = {
  "ch1": [
    {
      id: "ch1-p1",
      type: "PRIORITY",
      after: "ch1-hormonal",
      q: "A client missed two consecutive doses of combined oral contraceptives in the first week of the pack. What is the priority instruction?",
      a: "Take the most recent missed pill ASAP (even if 2 pills in one day), take the next pill at the regular time, use backup contraception for 7 days, and consider emergency contraception if there was unprotected intercourse in the past 5 days."
    },
    {
      id: "ch1-p2",
      type: "JUDGMENT",
      after: "ch1-hormonal",
      q: "A breastfeeding mother at 6 weeks postpartum wants combined oral contraceptives. What is the appropriate response?",
      a: "COCs are NOT recommended for breastfeeding mothers — estrogen decreases milk supply. Progestin-only pills (mini-pills), the IUD, ..."
    }
  ],
  "ch2": [
    {
      id: "ch2-p1",
      type: "CONTENT",
      after: "ch2-assessment",
      q: "What basal body temperature pattern indicates ovulation has occurred?",
      a: "A sustained rise of 0.4–0.8°F (0.2–0.4°C) above baseline for at least 3 days indicates ovulation occurred ~24-48 hours before the rise."
    },
    {
      id: "ch2-p2",
      type: "PRINCIPLE",
      after: "ch2-diagnostic",
      q: "Why is hysterosalpingography (HSG) typically performed in the follicular phase before ovulation?",
      a: "Performed in the follicular phase to avoid the possibility of disrupting an early pregnancy. The contrast dye flush itself may also have a therapeutic effect of clearing tubal blockages, potentially increasing fertility."
    }
  ],
  // ... 2 per chapter, all 27 chapters
};
```

**The 4 types:**
- **CONTENT** — factual recall ("What is X?")
- **JUDGMENT** — clinical decision-making ("What should the nurse do?")
- **PRINCIPLE** — underlying rationale ("Why is X done this way?")
- **PRIORITY** — triage ("What is the most important / first action?")

**Injection:**
```javascript
function injectAllPrompts() {
  Object.keys(MID_PROMPTS).forEach(function(chId) {
    MID_PROMPTS[chId].forEach(function(p) {
      var target = document.getElementById(p.after);
      if (!target) return;
      if (document.querySelector('[data-prompt-id="' + p.id + '"]')) return;
      var card = buildPromptCard(p);
      target.parentNode.insertBefore(card, target.nextSibling);
    });
  });
}

function buildPromptCard(p) {
  var card = document.createElement('div');
  card.className = 'mid-prompt mid-prompt-' + p.type.toLowerCase();
  card.setAttribute('data-prompt-id', p.id);

  var schedule = loadFcSchedule();
  var existing = schedule[p.id];
  if (existing) card.classList.add('rated');

  // Tag
  var tag = document.createElement('span');
  tag.className = 'mid-prompt-tag';
  tag.textContent = p.type;
  card.appendChild(tag);

  // Question
  var q = document.createElement('div');
  q.className = 'mid-prompt-q';
  q.innerHTML = p.q;
  card.appendChild(q);

  // Reveal button
  var btn = document.createElement('button');
  btn.className = 'mid-prompt-reveal';
  btn.type = 'button';
  btn.textContent = 'Reveal answer';
  btn.addEventListener('click', function() { card.classList.add('revealed'); });
  card.appendChild(btn);

  // Answer
  var ans = document.createElement('div');
  ans.className = 'mid-prompt-a';
  ans.innerHTML = p.a;
  card.appendChild(ans);

  // Rating row
  var rating = document.createElement('div');
  rating.className = 'mid-prompt-rating';
  var rLabel = document.createElement('span');
  rLabel.className = 'mid-prompt-rating-label';
  rLabel.textContent = 'Rate recall →';
  rating.appendChild(rLabel);

  [
    { label: 'Hard', value: 0, rate: 'hard' },
    { label: 'Good', value: 3, rate: 'good' },
    { label: 'Easy', value: 5, rate: 'easy' }
  ].forEach(function(r) {
    var rb = document.createElement('button');
    rb.className = 'mid-prompt-rate';
    rb.type = 'button';
    rb.setAttribute('data-rating', r.rate);
    rb.textContent = r.label;
    rb.addEventListener('click', function() {
      var resultCard = rateFlashcard(p.id, r.value, p);
      card.classList.add('rated');
      var ratedText = card.querySelector('.mid-prompt-rated');
      var days = resultCard.interval;
      if (ratedText) ratedText.textContent = '✓ Saved · next review in ' + days + (days === 1 ? ' day' : ' days');
    });
    rating.appendChild(rb);
  });
  card.appendChild(rating);

  // Rated status
  var rated = document.createElement('div');
  rated.className = 'mid-prompt-rated';
  if (existing) {
    var d = new Date(existing.nextReview);
    var now = new Date();
    if (d - now <= 0) rated.textContent = '✓ In review queue · due now';
    else {
      var days = Math.ceil((d - now) / 86400000);
      rated.textContent = '✓ In review queue · next review in ' + days + (days === 1 ? ' day' : ' days');
    }
  }
  card.appendChild(rated);

  return card;
}

function rateFlashcard(id, rating, promptData) {
  var schedule = loadFcSchedule();
  var card = schedule[id] || {
    id: id,
    chapter: id.split('-')[0].replace('ch', ''),
    type: promptData.type,
    anchor: promptData.after,
    prompt: promptData.q,
    answer: promptData.a,
    reps: 0, ef: 2.5, interval: 1
  };
  sm2Update(card, rating);
  card.nextReview = new Date(Date.now() + card.interval * 86400000).toISOString();
  card.lastRated = new Date().toISOString();
  schedule[id] = card;
  saveFcSchedule(schedule);
  return card;
}
```

**CSS for the 4 typed prompts:**
```css
.mid-prompt {
  margin: 24px 0;
  padding: 18px 20px;
  border-radius: 12px;
  border: 1px solid var(--border);
  background: var(--surface);
  position: relative;
}
.mid-prompt-tag {
  display: inline-block;
  font-size: 10px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.12em;
  padding: 3px 9px;
  border-radius: 5px;
  color: var(--bg);            /* the tag text is darkened against its colored bg */
  margin-bottom: 10px;
}

/* CONTENT (blue) */
.mid-prompt-content {
  border-left: 4px solid var(--prompt-content);
  background: var(--prompt-content-bg);
}
.mid-prompt-content .mid-prompt-tag { background: var(--prompt-content); }

/* JUDGMENT (purple) */
.mid-prompt-judgment {
  border-left: 4px solid var(--prompt-judgment);
  background: var(--prompt-judgment-bg);
}
.mid-prompt-judgment .mid-prompt-tag { background: var(--prompt-judgment); }

/* PRINCIPLE (teal) */
.mid-prompt-principle {
  border-left: 4px solid var(--prompt-principle);
  background: var(--prompt-principle-bg);
}
.mid-prompt-principle .mid-prompt-tag { background: var(--prompt-principle); }

/* PRIORITY (red) */
.mid-prompt-priority {
  border-left: 4px solid var(--prompt-priority);
  background: var(--prompt-priority-bg);
}
.mid-prompt-priority .mid-prompt-tag { background: var(--prompt-priority); }

.mid-prompt-q {
  font-size: 14.5px; line-height: 1.55;
  color: var(--text); font-weight: 500;
  margin-bottom: 12px;
}
.mid-prompt-reveal {
  background: var(--surface);
  border: 1px solid var(--border);
  color: var(--text);
  padding: 6px 14px;
  font-size: 12px; font-weight: 600;
  border-radius: 6px; cursor: pointer;
}
.mid-prompt-a {
  display: none;
  margin-top: 12px;
  padding: 12px 14px;
  background: var(--bg);
  border-radius: 8px;
  font-size: 14px; line-height: 1.6;
  color: var(--text);
}
.mid-prompt.revealed .mid-prompt-a { display: block; }
.mid-prompt.revealed .mid-prompt-reveal { display: none; }
.mid-prompt-rating {
  display: none;
  align-items: center; gap: 10px; flex-wrap: wrap;
  margin-top: 12px;
}
.mid-prompt.revealed .mid-prompt-rating { display: flex; }
.mid-prompt-rating-label {
  font-size: 11px; font-weight: 600;
  color: var(--text2);
  text-transform: uppercase; letter-spacing: 0.06em;
}
.mid-prompt-rate {
  background: var(--surface); border: 1px solid var(--border);
  color: var(--text);
  padding: 6px 14px;
  font-size: 12px; font-weight: 600;
  border-radius: 6px; cursor: pointer;
  transition: all .15s;
}
.mid-prompt-rate[data-rating="hard"]:hover { border-color: var(--nonreassuring); color: var(--nonreassuring); }
.mid-prompt-rate[data-rating="good"]:hover { border-color: var(--accent2); color: var(--accent2); }
.mid-prompt-rate[data-rating="easy"]:hover { border-color: var(--reassuring); color: var(--reassuring); }
.mid-prompt-rated {
  margin-top: 8px;
  font-size: 11px; color: var(--reassuring);
  font-weight: 600;
}
.mid-prompt.rated .mid-prompt-reveal,
.mid-prompt.rated .mid-prompt-rating { /* still visible for re-rate */ }
```

### 7.11 Active Learning Scenario (ALS)

ALS uses the same `content-section` structure but follows a strict 2-block pattern:
1. **Scenario block** — italicized prompt + list of sub-questions (Related Content / Underlying Principles / Nursing Interventions)
2. **Answer key block** — finding-grid for short answers + kb-card for longer ones

24 of 27 MN chapters have an ALS (chapters 7, 8, 13 do not — those PDF chapters don't contain one). Pharmacology chapters typically all have ALS; PD has them inconsistently.

The ALS section is identified by `id="chN-als"` and is rendered as a regular content-section tab with `<h2>Active Learning Scenario</h2>` (which truncates to "Active Learning Scenari…" in the tab label due to the 28-char limit).

### 7.12 Exercises with NCLEX filter

**Exercise HTML pattern** (5 per chapter):
```html
<article class="exercise" data-q-id="ch1-q1">
  <header class="exercise-q" data-toggle>
    <span class="q-num">Q1</span>
    <p>The question stem...</p>
    <ol class="q-options">
      <li>A. "Option A text"</li>
      <li>B. "Option B text"</li>
      <li>C. "Option C text"</li>
      <li>D. "Option D text"</li>
    </ol>
    <span class="q-toggle">Show rationale ▾</span>
  </header>
  <div class="exercise-a">
    <p class="answer correct"><span class="ans-letter">A.</span> <strong>CORRECT.</strong> Rationale...</p>
    <p class="answer"><span class="ans-letter">B.</span> Why incorrect...</p>
    <p class="answer"><span class="ans-letter">C.</span> Why incorrect...</p>
    <p class="answer"><span class="ans-letter">D.</span> Why incorrect...</p>
    <span class="nclex-tag">NCLEX · Pharmacological & Parenteral Therapies · Expected Actions/Outcomes</span>
  </div>
</article>
```

For SATA (Select All That Apply) questions, mark multiple answers as `.correct`:
```html
<p class="answer correct"><span class="ans-letter">A.</span> CORRECT. ...</p>
<p class="answer correct"><span class="ans-letter">C.</span> CORRECT. ...</p>
```

**CSS:**
```css
.exercise {
  background: var(--surface);
  border: 1px solid var(--border-soft);
  border-radius: 12px;
  margin-bottom: 14px;
  overflow: hidden;
}
.exercise-q {
  padding: 20px 24px;
  cursor: pointer;
  display: flex; flex-wrap: wrap; align-items: flex-start;
  gap: 10px 14px;
}
.q-num {
  flex-shrink: 0;
  font-size: 12px; font-weight: 700;
  color: var(--accent);
  background: var(--accent-soft);
  padding: 4px 10px;
  border-radius: 6px;
}
.exercise-q p {
  flex: 1; min-width: 200px;
  font-size: 14.5px; line-height: 1.5;
  color: var(--text);
  margin: 0;
}
.q-options {
  flex-basis: 100%;
  margin: 6px 0 0;
  padding-left: 34px;
}
.q-options li {
  font-size: 14px; line-height: 1.55;
  margin-bottom: 6px;
  color: var(--text2);
  list-style: none;
}
.q-toggle {
  margin-left: auto;
  font-size: 11px; font-weight: 600;
  color: var(--text3);
  text-transform: uppercase; letter-spacing: 0.06em;
}
.exercise.expanded .q-toggle::before {
  content: 'Hide rationale ▴';
}
.exercise:not(.expanded) .q-toggle::before {
  content: 'Show rationale ▾';
}

.exercise-a {
  display: none;
  padding: 0 24px 22px;
  border-top: 1px solid var(--border-soft);
  font-size: 14.5px; line-height: 1.6;
}
.exercise.expanded .exercise-a { display: block; }

.answer {
  padding: 8px 0;
  color: var(--text2);
}
.answer.correct { color: var(--reassuring); }
.ans-letter {
  font-weight: 700;
  display: inline-block;
  width: 18px;
}

.nclex-tag {
  display: inline-block;
  background: var(--surface2);
  border: 1px solid var(--border-soft);
  font-size: 11px; color: var(--text3);
  padding: 4px 10px;
  border-radius: 4px;
  margin-top: 12px;
  text-transform: uppercase; letter-spacing: 0.1em;
}

/* Answered tracking */
.exercise.answered {
  opacity: 0.7;
  border-color: var(--reassuring-bg);
}
.exercise.answered .q-num::after {
  content: ' ✓';
  color: var(--reassuring);
}

/* SATA badge */
.exercise.is-sata .q-num::after {
  content: ' SATA';
  font-size: 9px;
  margin-left: 4px;
}
```

**NCLEX filter bar JS** (injected into each exercises section):

```javascript
function injectNclexFilterBar(root, chapterId) {
  var section = root.querySelector('#' + chapterId + '-exercises');
  if (!section) return;
  if (section.querySelector('.nclex-filter')) return;  // already injected

  var bar = document.createElement('div');
  bar.className = 'nclex-filter';
  bar.innerHTML =
    '<button class="nclex-filter-btn active" data-filter="all">All</button>' +
    '<button class="nclex-filter-btn" data-filter="unanswered">Unanswered</button>' +
    '<button class="nclex-filter-btn" data-filter="sata">SATA only</button>' +
    '<button class="nclex-filter-btn" data-filter="answered">Done</button>';

  section.insertBefore(bar, section.querySelector('.section-lead').nextSibling);

  // Identify SATA questions and apply answered tracking
  var answered = loadNclexDone();
  section.querySelectorAll('.exercise').forEach(function(ex) {
    if (isSataQuestion(ex)) ex.classList.add('is-sata');
    var qId = ex.dataset.qId;
    if (qId && answered[qId]) ex.classList.add('answered');
  });

  bar.querySelectorAll('.nclex-filter-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      bar.querySelectorAll('.nclex-filter-btn').forEach(function(b) { b.classList.remove('active'); });
      btn.classList.add('active');
      applyNclexFilter(section, btn.dataset.filter);
    });
  });
}

function isSataQuestion(exerciseEl) {
  var correctCount = exerciseEl.querySelectorAll('.answer.correct').length;
  return correctCount > 1;
}

function applyNclexFilter(section, filter) {
  section.querySelectorAll('.exercise').forEach(function(ex) {
    var show = true;
    if (filter === 'unanswered') show = !ex.classList.contains('answered');
    else if (filter === 'sata') show = ex.classList.contains('is-sata');
    else if (filter === 'answered') show = ex.classList.contains('answered');
    ex.style.display = show ? '' : 'none';
  });
}

// When user reveals an exercise, mark answered
function bindExercises(root) {
  (root || document).querySelectorAll('.exercise-q[data-toggle]').forEach(function(header) {
    header.addEventListener('click', function() {
      var exercise = header.closest('.exercise');
      exercise.classList.toggle('expanded');
      if (exercise.classList.contains('expanded')) {
        var qId = exercise.dataset.qId;
        if (qId) {
          var done = loadNclexDone();
          done[qId] = true;
          saveNclexDone(done);
          exercise.classList.add('answered');
        }
      }
    });
  });
}

var NCLEX_DONE_KEY = 'nur2460_nclex_done';
function loadNclexDone() { try { return JSON.parse(localStorage.getItem(NCLEX_DONE_KEY) || '{}'); } catch(e) { return {}; } }
function saveNclexDone(o) { try { localStorage.setItem(NCLEX_DONE_KEY, JSON.stringify(o)); } catch(e) {} }
```

**Filter bar CSS:**
```css
.nclex-filter {
  display: flex; gap: 6px; flex-wrap: wrap;
  margin: 0 0 18px;
  padding: 10px 14px;
  background: var(--surface);
  border: 1px solid var(--border-soft);
  border-radius: 8px;
}
.nclex-filter-btn {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text2);
  padding: 5px 12px;
  font-size: 11px; font-weight: 600;
  text-transform: uppercase; letter-spacing: 0.06em;
  border-radius: 6px;
  cursor: pointer;
  transition: all .15s;
}
.nclex-filter-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.nclex-filter-btn.active {
  background: var(--accent);
  border-color: var(--accent);
  color: var(--bg);
}
```

### 7.13 Templates bridge

```html
<section id="ch1-templates" class="content-section tpl-bridge">
  <h2>ATI Templates · this chapter</h2>
  <ul>
    <li><a href="Elevated%20ATI%20MN%20Templates.html#ex-ch1-cocs">Combined Oral Contraceptives (COCs)</a></li>
    <li><a href="Elevated%20ATI%20MN%20Templates.html#ex-ch1-vasectomy">Vasectomy</a></li>
  </ul>
</section>
```

The exact class is `content-section tpl-bridge` (both classes). The `tpl-bridge` class is what `buildTabLabel()` uses to assign the "Templates" tab label.

```css
.tpl-bridge {
  background: var(--surface);
  border: 1px solid var(--border-soft);
  border-radius: 12px;
  padding: 20px 24px;
}
.tpl-bridge h2 {
  font-family: 'DM Sans', sans-serif;
  font-size: 12px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: var(--accent);
  margin: 0 0 14px;
}
.tpl-bridge ul {
  margin: 0; padding: 0;
  list-style: none;
}
.tpl-bridge li {
  border-bottom: 1px solid var(--border-soft);
}
.tpl-bridge li:last-child { border-bottom: none; }
.tpl-bridge a {
  display: block;
  padding: 12px 0;
  font-size: 14px;
  color: var(--text);
  text-decoration: none;
  transition: color .15s;
}
.tpl-bridge a:hover { color: var(--accent); }
.tpl-bridge a::after {
  content: ' →';
  color: var(--text3);
}
```

### 7.14 Bookmarks system

**Data shape:** `nur2460_bookmarks` is a JSON array of objects:
```javascript
[
  {
    chapterId: "ch3",
    sectionId: "ch3-als",
    label: "Ch 3 · Active Learning Scenario",
    addedAt: "2026-05-11T14:30:00.000Z"
  },
  // ...
]
```

**Star button injected into each section** (inside modal):
```javascript
function injectBookmarkButtons(root, chapterId) {
  var sections = root.querySelectorAll('.tab-panel');
  sections.forEach(function(section) {
    if (section.querySelector('.bookmark-btn')) return;  // already injected

    var sectionId = section.id;
    var h2 = section.querySelector('h2');
    if (!h2) return;
    var label = chapterId + ' · ' + h2.textContent.trim();

    var btn = document.createElement('button');
    btn.className = 'bookmark-btn';
    btn.type = 'button';
    btn.title = 'Bookmark this section';
    btn.setAttribute('aria-label', 'Bookmark');

    var bookmarks = loadBookmarks();
    var isBookmarked = bookmarks.some(function(b) {
      return b.chapterId === chapterId && b.sectionId === sectionId;
    });
    if (isBookmarked) btn.classList.add('active');
    btn.textContent = isBookmarked ? '★' : '☆';

    btn.addEventListener('click', function() {
      toggleBookmark(chapterId, sectionId, label);
      var stillBookmarked = loadBookmarks().some(function(b) {
        return b.chapterId === chapterId && b.sectionId === sectionId;
      });
      btn.classList.toggle('active', stillBookmarked);
      btn.textContent = stillBookmarked ? '★' : '☆';
      updateBookmarkUI();
    });

    h2.parentNode.insertBefore(btn, h2);
  });
}

var BOOKMARK_KEY = 'nur2460_bookmarks';
function loadBookmarks() { try { return JSON.parse(localStorage.getItem(BOOKMARK_KEY) || '[]'); } catch(e) { return []; } }
function saveBookmarks(b) { try { localStorage.setItem(BOOKMARK_KEY, JSON.stringify(b)); } catch(e) {} }

function toggleBookmark(chId, secId, label) {
  var bookmarks = loadBookmarks();
  var idx = bookmarks.findIndex(function(b) {
    return b.chapterId === chId && b.sectionId === secId;
  });
  if (idx >= 0) {
    bookmarks.splice(idx, 1);
  } else {
    bookmarks.push({
      chapterId: chId,
      sectionId: secId,
      label: label,
      addedAt: new Date().toISOString()
    });
  }
  saveBookmarks(bookmarks);
}

function updateBookmarkUI() {
  var count = loadBookmarks().length;
  var badge = document.getElementById('bookmarksCountBadge');
  if (badge) badge.textContent = count > 0 ? count : '';
}

function renderBookmarksList() {
  var list = document.getElementById('bookmarksList');
  var empty = document.getElementById('bookmarksEmpty');
  var bookmarks = loadBookmarks();
  if (bookmarks.length === 0) {
    list.innerHTML = '';
    empty.removeAttribute('hidden');
    return;
  }
  empty.setAttribute('hidden', '');
  list.innerHTML = '';
  bookmarks.sort(function(a, b) { return new Date(b.addedAt) - new Date(a.addedAt); });
  bookmarks.forEach(function(b) {
    var item = document.createElement('a');
    item.className = 'bookmark-item';
    item.href = '#' + b.sectionId;
    item.innerHTML =
      '<div class="bookmark-label">' + b.label + '</div>' +
      '<div class="bookmark-time">' + new Date(b.addedAt).toLocaleDateString() + '</div>';
    item.addEventListener('click', function(e) {
      e.preventDefault();
      document.getElementById('bookmarksOverlay').classList.remove('show');
      openChapter(b.chapterId, b.sectionId);
    });
    list.appendChild(item);
  });
}

document.getElementById('bookmarksOpenBtn').addEventListener('click', function() {
  renderBookmarksList();
  document.getElementById('bookmarksOverlay').classList.add('show');
});
document.getElementById('bookmarksClose').addEventListener('click', function() {
  document.getElementById('bookmarksOverlay').classList.remove('show');
});
document.getElementById('bookmarksOverlay').addEventListener('click', function(e) {
  if (e.target === this) this.classList.remove('show');
});
```

**Bookmarks panel CSS:**
```css
.bookmarks-overlay {
  position: fixed; inset: 0;
  background: rgba(0,0,0,0.6);
  backdrop-filter: blur(6px);
  z-index: 200;
  display: none;
  align-items: center; justify-content: center;
  padding: 20px;
}
.bookmarks-overlay.show { display: flex; }

.bookmarks-panel {
  background: var(--surface);
  border-radius: 12px;
  max-width: 560px; width: 100%;
  max-height: 80vh;
  overflow: hidden;
  display: flex; flex-direction: column;
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}
.bookmarks-header {
  padding: 18px 24px;
  border-bottom: 1px solid var(--border);
  display: flex; justify-content: space-between; align-items: center;
}
.bookmarks-header h2 {
  font-family: 'DM Serif Display', serif;
  font-size: 22px; font-weight: 400;
  margin: 0;
}
.bookmarks-close {
  background: transparent; border: none;
  color: var(--text2);
  font-size: 24px;
  cursor: pointer; padding: 0 6px;
}
.bookmarks-body {
  flex: 1; overflow-y: auto;
  padding: 12px 0;
}
.bookmarks-empty {
  padding: 40px 24px; text-align: center;
  color: var(--text2);
}
.bookmark-item {
  display: flex; justify-content: space-between; align-items: center;
  padding: 12px 24px;
  border-bottom: 1px solid var(--border-soft);
  text-decoration: none;
  color: var(--text);
  transition: background .12s;
}
.bookmark-item:hover { background: var(--surface2); }
.bookmark-label {
  font-size: 14px;
  flex: 1;
}
.bookmark-time {
  font-size: 11px;
  color: var(--text3);
}

.bookmark-btn {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text3);
  width: 28px; height: 28px;
  border-radius: 6px;
  cursor: pointer;
  font-size: 14px;
  margin-right: 10px;
  vertical-align: middle;
  display: inline-flex;
  align-items: center; justify-content: center;
  transition: all .15s;
}
.bookmark-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}
.bookmark-btn.active {
  border-color: var(--accent);
  color: var(--accent);
  background: var(--accent-soft);
}
```

### 7.15 Search system

The search input lives in the sidebar. Typing triggers a live filtered dropdown.

**HTML** (already in sidebar):
```html
<div class="sidebar-search">
  <input id="searchInput" type="text" placeholder="Search chapters & content…" autocomplete="off">
  <div id="searchResults"></div>
</div>
```

**JS:**
```javascript
function handleSearch(query) {
  var results = document.getElementById('searchResults');
  query = query.trim().toLowerCase();
  if (query.length < 2) {
    results.classList.remove('show');
    results.innerHTML = '';
    return;
  }
  var pool = document.getElementById('chapterPool');
  var chapters = pool.querySelectorAll('.chapter');
  var hits = [];
  var maxHits = 30;
  var escaped = escapeRegExp(query);
  var rx = new RegExp(escaped, 'gi');

  chapters.forEach(function(ch) {
    var chId = ch.id;
    var chName = ch.querySelector('.chapter-name');
    var chLabel = chName ? chName.textContent.trim() : chId;
    var sections = ch.querySelectorAll(':scope > section[id]');
    sections.forEach(function(sec) {
      if (hits.length >= maxHits) return;
      var secText = sec.textContent.toLowerCase();
      if (secText.indexOf(query) === -1) return;

      // Build snippet
      var idx = secText.indexOf(query);
      var start = Math.max(0, idx - 30);
      var end = Math.min(secText.length, idx + query.length + 50);
      var snippet = sec.textContent.substring(start, end);
      var hl = escapeHtml(snippet).replace(rx, function(m) { return '<mark>' + m + '</mark>'; });

      var h2 = sec.querySelector('h2');
      var secLabel = h2 ? h2.textContent.trim() : sec.id;

      hits.push({
        chapterId: chId,
        sectionId: sec.id,
        chapterLabel: chLabel,
        sectionLabel: secLabel,
        snippet: hl
      });
    });
  });

  if (hits.length === 0) {
    results.innerHTML = '<div class="search-result-item" style="color:var(--text3)">No results</div>';
  } else {
    results.innerHTML = hits.map(function(h) {
      return '<a class="search-result-item" href="#' + h.sectionId + '" data-ch="' + h.chapterId + '" data-sec="' + h.sectionId + '">' +
             '<div class="search-result-chapter">' + h.chapterLabel + ' → ' + h.sectionLabel + '</div>' +
             '<div class="search-result-snippet">…' + h.snippet + '…</div>' +
             '</a>';
    }).join('');
    results.querySelectorAll('.search-result-item').forEach(function(item) {
      item.addEventListener('click', function(e) {
        e.preventDefault();
        results.classList.remove('show');
        document.getElementById('searchInput').value = '';
        openChapter(item.dataset.ch, item.dataset.sec);
        setTimeout(function() {
          var modalBody = document.getElementById('modalBody');
          highlightInContainer(modalBody, query);
        }, 100);
      });
    });
  }
  results.classList.add('show');
}

// Highlight within rendered modal body
function highlightInContainer(container, query) {
  clearSearchHighlights(container);
  if (!query || query.length < 2) return;
  var rx = new RegExp(escapeRegExp(query), 'gi');

  function walk(node) {
    if (node.nodeType === 3) {  // text
      var text = node.nodeValue;
      if (rx.test(text)) {
        rx.lastIndex = 0;
        var frag = document.createDocumentFragment();
        var lastIdx = 0;
        var match;
        while ((match = rx.exec(text)) !== null) {
          if (match.index > lastIdx) {
            frag.appendChild(document.createTextNode(text.substring(lastIdx, match.index)));
          }
          var mark = document.createElement('mark');
          mark.className = 'search-hit';
          mark.textContent = match[0];
          frag.appendChild(mark);
          lastIdx = match.index + match[0].length;
        }
        if (lastIdx < text.length) {
          frag.appendChild(document.createTextNode(text.substring(lastIdx)));
        }
        node.parentNode.replaceChild(frag, node);
      }
    } else if (node.nodeType === 1 && !['SCRIPT','STYLE','MARK'].includes(node.tagName)) {
      Array.from(node.childNodes).forEach(walk);
    }
  }
  walk(container);
}

function clearSearchHighlights(container) {
  (container || document).querySelectorAll('mark.search-hit').forEach(function(m) {
    var parent = m.parentNode;
    parent.replaceChild(document.createTextNode(m.textContent), m);
    parent.normalize();
  });
}

function escapeRegExp(s) { return s.replace(/[.*+?^${}()|[\]\\]/g, '\\$&'); }
function escapeHtml(s) {
  return s.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;').replace(/"/g, '&quot;');
}

// Debounced input handler
var searchTimeout;
document.getElementById('searchInput').addEventListener('input', function(e) {
  clearTimeout(searchTimeout);
  var q = e.target.value;
  searchTimeout = setTimeout(function() { handleSearch(q); }, 150);
});

// Close dropdown when clicking outside
document.addEventListener('click', function(e) {
  if (!e.target.closest('.sidebar-search')) {
    document.getElementById('searchResults').classList.remove('show');
  }
});
```

**Search-result mark styling:**
```css
mark.search-hit {
  background: var(--accent-soft);
  color: var(--accent);
  padding: 0 2px;
  border-radius: 2px;
}
```

### 7.16 Abbreviation tooltips (ABBR_DICT, 263 entries)

The system auto-detects abbreviations in content text and wraps them with `<span class="abbr">` for hover tooltips.

**Dictionary** (sample — full list in PART 11 reference):
```javascript
const ABBR_DICT = {
  // Vitals/Assessment
  "HR": "Heart Rate",
  "BP": "Blood Pressure",
  "RR": "Respiratory Rate",
  "VS": "Vital Signs",
  "SpO2": "Oxygen Saturation",
  "BMI": "Body Mass Index",
  "DTRs": "Deep Tendon Reflexes",
  "LOC": "Level of Consciousness",
  "GCS": "Glasgow Coma Scale",

  // Fetal monitoring
  "FHR": "Fetal Heart Rate",
  "FHT": "Fetal Heart Tones",
  "EFM": "Electronic Fetal Monitoring",
  "NST": "Non-Stress Test",
  "CST": "Contraction Stress Test",
  "BPP": "Biophysical Profile",
  "AFI": "Amniotic Fluid Index",
  "AFV": "Amniotic Fluid Volume",
  "SVE": "Sterile Vaginal Exam",
  "SBP": "Systolic Blood Pressure",
  "DBP": "Diastolic Blood Pressure",

  // ... 243 more
};
```

**Wrapping logic:** Run after page load and after modal body is populated. Walks text nodes, replaces matched terms.

```javascript
function autoWrapAbbreviations(root) {
  if (!root) return;
  var keys = Object.keys(ABBR_DICT).sort(function(a, b) { return b.length - a.length; });  // longest first
  var rx = new RegExp('\\b(' + keys.map(escapeRegExp).join('|') + ')\\b', 'g');

  function walk(node) {
    if (node.nodeType === 3) {
      var text = node.nodeValue;
      if (!rx.test(text)) return;
      rx.lastIndex = 0;
      var frag = document.createDocumentFragment();
      var lastIdx = 0; var match;
      while ((match = rx.exec(text)) !== null) {
        if (match.index > lastIdx) {
          frag.appendChild(document.createTextNode(text.substring(lastIdx, match.index)));
        }
        var span = document.createElement('span');
        span.className = 'abbr';
        span.dataset.abbr = match[1];
        span.textContent = match[0];
        frag.appendChild(span);
        lastIdx = match.index + match[0].length;
      }
      if (lastIdx < text.length) {
        frag.appendChild(document.createTextNode(text.substring(lastIdx)));
      }
      node.parentNode.replaceChild(frag, node);
    } else if (node.nodeType === 1 &&
               !['SCRIPT','STYLE','MARK','SPAN','BUTTON','INPUT'].includes(node.tagName) &&
               !node.classList.contains('abbr')) {
      Array.from(node.childNodes).forEach(walk);
    }
  }
  walk(root);
}

function bindAbbrs(root) {
  (root || document).querySelectorAll('.abbr').forEach(function(span) {
    if (span.dataset.bound) return;
    span.dataset.bound = '1';

    function show(e) {
      var def = ABBR_DICT[span.dataset.abbr];
      if (!def) return;
      showTip(e, def);
    }
    function hide() {
      var pop = document.getElementById('abbrTipPop');
      pop.setAttribute('hidden', '');
    }
    span.addEventListener('mouseenter', show);
    span.addEventListener('mouseleave', hide);
    span.addEventListener('click', function(e) {
      var pop = document.getElementById('abbrTipPop');
      if (!pop.hasAttribute('hidden')) hide();
      else show(e);
    });
  });
}

function showTip(e, text) {
  var pop = document.getElementById('abbrTipPop');
  pop.textContent = text;
  pop.removeAttribute('hidden');
  var rect = e.target.getBoundingClientRect();
  var popWidth = 240;
  var x = rect.left + (rect.width / 2) - (popWidth / 2);
  x = Math.max(8, Math.min(window.innerWidth - popWidth - 8, x));
  var y = rect.top - 8;
  pop.style.left = x + 'px';
  pop.style.top = (y - pop.offsetHeight) + 'px';
}
```

**Tooltip popover styling:**
```css
.abbr {
  border-bottom: 1px dotted var(--accent2);
  cursor: help;
  color: inherit;
}
.abbr-tip-pop {
  position: fixed;
  background: var(--surface3);
  color: var(--text);
  border: 1px solid var(--border);
  border-radius: 8px;
  padding: 8px 12px;
  font-size: 12px;
  max-width: 240px;
  z-index: 300;
  box-shadow: 0 8px 24px rgba(0,0,0,0.3);
  pointer-events: none;
}
.abbr-tip-pop[hidden] { display: none; }
```

### 7.17 Print/PDF overlay (Brief vs Deep)

The print system opens a fullscreen overlay with formatted content, then triggers `window.print()`. Two modes:
- **Brief** — just the TL;DR card from each chapter
- **Deep** — everything

**HTML overlay:**
```html
<div class="print-overlay" id="printOverlay" aria-hidden="true"></div>
```

**JS:**
```javascript
function openPrintOverlay(scope, mode) {
  var overlay = document.getElementById('printOverlay');
  overlay.innerHTML = '';

  // Toolbar
  var toolbar = document.createElement('div');
  toolbar.className = 'print-toolbar';
  toolbar.innerHTML =
    '<div class="print-toolbar-left">' +
    '  <button class="print-mode-btn ' + (mode === 'brief' ? 'active' : '') + '" data-mode="brief">📋 Brief (TL;DRs)</button>' +
    '  <button class="print-mode-btn ' + (mode === 'deep' ? 'active' : '') + '" data-mode="deep">📚 Deep (Full content)</button>' +
    '</div>' +
    '<div class="print-toolbar-right">' +
    '  <button class="print-do-btn">🖨️ Print / Save PDF</button>' +
    '  <button class="print-close-btn">✕ Close</button>' +
    '</div>';
  overlay.appendChild(toolbar);

  // Content area
  var content = document.createElement('div');
  content.className = 'print-content';
  buildPrintContent(content, scope, mode);
  overlay.appendChild(content);

  // Show
  overlay.classList.add('show');
  overlay.setAttribute('aria-hidden', 'false');
  document.body.classList.add('printing');

  // Wire toolbar
  toolbar.querySelectorAll('.print-mode-btn').forEach(function(btn) {
    btn.addEventListener('click', function() {
      var newMode = btn.dataset.mode;
      openPrintOverlay(scope, newMode);  // rebuild
    });
  });
  toolbar.querySelector('.print-do-btn').addEventListener('click', function() {
    window.print();
  });
  toolbar.querySelector('.print-close-btn').addEventListener('click', closePrintOverlay);
}

function buildPrintContent(target, scope, mode) {
  var pool = document.getElementById('chapterPool');
  var chapters;
  if (scope === 'all') {
    chapters = pool.querySelectorAll('.chapter');
  } else if (scope === 'unit') {
    chapters = pool.querySelectorAll('.chapter[data-unit="' + scope + '"]');
  } else {
    chapters = [pool.querySelector('#' + scope)];
  }

  Array.from(chapters).forEach(function(ch) {
    if (!ch) return;
    var name = ch.querySelector('.chapter-name');
    var meta = ch.querySelector('.chapter-meta');
    var article = document.createElement('article');
    article.className = 'print-chapter';
    article.innerHTML =
      '<div class="print-chapter-meta">' + (meta ? meta.textContent : '') + '</div>' +
      '<h1 class="print-chapter-title">' + (name ? name.innerHTML : '') + '</h1>';

    if (mode === 'brief') {
      // Only TL;DR
      var brief = ch.querySelector('.brief-card');
      if (brief) article.appendChild(brief.cloneNode(true));
    } else {
      // Deep: all sections except templates bridge
      ch.querySelectorAll(':scope > section[id]').forEach(function(sec) {
        if (sec.classList.contains('tpl-bridge')) return;
        article.appendChild(sec.cloneNode(true));
      });
    }
    target.appendChild(article);
  });
}

function closePrintOverlay() {
  var overlay = document.getElementById('printOverlay');
  overlay.classList.remove('show');
  overlay.setAttribute('aria-hidden', 'true');
  document.body.classList.remove('printing');
}

// Trigger from master button
document.getElementById('masterPrintBtn').addEventListener('click', function() {
  openPrintOverlay('all', 'brief');
});

// Per-unit print buttons
document.querySelectorAll('[data-print-unit]').forEach(function(btn) {
  btn.addEventListener('click', function(e) {
    e.stopPropagation();
    var unitAcc = btn.dataset.printUnit;
    // Get all chapter IDs in this unit (from planner rows)
    openPrintOverlay(unitAcc, 'deep');
  });
});
```

**Print-overlay CSS:**
```css
.print-overlay {
  position: fixed; inset: 0;
  background: white;
  z-index: 500;
  display: none;
  overflow-y: auto;
}
.print-overlay.show { display: block; }

.print-toolbar {
  position: sticky; top: 0;
  background: var(--surface);
  border-bottom: 1px solid var(--border);
  padding: 14px 24px;
  display: flex; justify-content: space-between; align-items: center;
  gap: 12px;
  z-index: 1;
}
.print-mode-btn,
.print-do-btn,
.print-close-btn {
  background: var(--bg);
  border: 1px solid var(--border);
  color: var(--text);
  padding: 8px 14px;
  border-radius: 8px;
  font-size: 13px;
  cursor: pointer;
  transition: all .15s;
}
.print-mode-btn.active {
  background: var(--accent);
  border-color: var(--accent);
  color: var(--bg);
}
.print-do-btn { background: var(--accent); border-color: var(--accent); color: var(--bg); }

.print-content {
  padding: 40px 60px;
  background: white;
  color: #1a1a1a;
  font-family: 'DM Sans', sans-serif;
  max-width: 8.5in;
  margin: 0 auto;
  font-size: 13px;
  line-height: 1.5;
}
.print-chapter {
  page-break-after: always;
  margin-bottom: 40px;
}
.print-chapter-meta {
  font-size: 11px; font-weight: 700;
  text-transform: uppercase; letter-spacing: 0.1em;
  color: #888;
  margin-bottom: 6px;
}
.print-chapter-title {
  font-family: 'DM Serif Display', serif;
  font-size: 28px; font-weight: 400;
  margin: 0 0 24px;
  color: #111;
}

@media print {
  body.printing > *:not(.print-overlay) { display: none !important; }
  .print-toolbar { display: none !important; }
  .print-content { padding: 0; }
  .print-chapter { page-break-after: always; }
  .print-chapter:last-child { page-break-after: auto; }
  .brief-card { background: #f5f5f5 !important; color: #000 !important; border: 1px solid #ccc !important; }
  .mid-prompt,
  .mid-read,
  .bookmark-btn,
  .nclex-filter,
  .q-toggle { display: none !important; }
  .exercise-a { display: block !important; }
}
```

### 7.18 Cross-tool sync

Three sets of keys travel between tools:

**Last position:**
```javascript
// Book records last viewed chapter/section
function recordLastChapter(chapterId, sectionId) {
  var name = document.querySelector('#' + chapterId + ' .chapter-name');
  var label = name ? name.textContent.trim() : chapterId;
  localStorage.setItem('nur2460_last_chapter', chapterId + '|' + sectionId + '|' + label);
}

// Templates records last viewed example
function recordLastTemplate(exampleId, label) {
  localStorage.setItem('nur2460_last_template', exampleId + '|' + label);
}

// Hub reads these to populate pickup panel (see PART 6.4)
```

**Hook every chapter-open with this:**
```javascript
function _installCrossToolHook() {
  var origOpen = openChapter;
  window.openChapter = function(chId, secId) {
    origOpen(chId, secId);
    recordLastChapter(chId, secId);
  };
}
_installCrossToolHook();
```

**Shared keys** (used by Book, Templates, Hub, Flashcards):
- `nur2460_theme` — current theme ("light" or null)
- `nur2460_last_chapter` — last book position
- `nur2460_last_template` — last template viewed
- `nur2460_bookmarks` — bookmark list
- `nur2460_fc_schedule` — SM-2 flashcard schedule
- `nur2460_nclex_done` — answered questions tracking

### 7.19 Sidebar units (collapsible)

```javascript
document.querySelectorAll('.nav-section-label[data-toggle-section]').forEach(function(label) {
  label.addEventListener('click', function() {
    var sectionId = label.dataset.toggleSection;
    document.getElementById(sectionId).classList.toggle('collapsed');
  });
});

// Default: all collapsed on first load
// But if user has activity in a section, expand it
function expandSectionWithActivity() {
  var progress = loadProgress();
  Object.keys(progress).forEach(function(chId) {
    if (progress[chId] > 0) {
      var item = document.querySelector('.sidebar-item[data-section="' + chId + '"]');
      if (item) {
        var section = item.closest('.nav-section');
        if (section) section.classList.remove('collapsed');
      }
    }
  });
}
```

### 7.20 Reading progress tracking (3-state checkboxes)

Each chapter has a 3-state planner check: empty → reviewed → complete → empty.

**States:**
- **Empty** (border only, gray): not yet read
- **Reviewed** (filled with accent-soft tint, accent border): scanned/glanced
- **Complete** (filled with full accent, checkmark): thoroughly read

**JS:**
```javascript
var PROGRESS_KEY = 'nur2460_atimn_progress';  // BOOK key
// (Templates uses 'nur2460_atimnTemplates_progress' — camelCase!)
// (Pharm Book uses 'nur2460_atipharm_progress')
// (PD Book uses 'atipd_book_progress')

function loadProgress() { try { return JSON.parse(localStorage.getItem(PROGRESS_KEY) || '{}'); } catch(e) { return {}; } }
function saveProgress(p) { try { localStorage.setItem(PROGRESS_KEY, JSON.stringify(p)); } catch(e) {} }

function applyCheckState(checkEl, state) {
  checkEl.classList.remove('reviewed', 'complete');
  if (state === 1) checkEl.classList.add('reviewed');
  else if (state === 2) checkEl.classList.add('complete');
}

document.querySelectorAll('[data-toggle-check]').forEach(function(check) {
  check.addEventListener('click', function(e) {
    e.stopPropagation();
    var chId = check.dataset.toggleCheck;
    var progress = loadProgress();
    var current = progress[chId] || 0;
    var next = (current + 1) % 3;        // 0 → 1 → 2 → 0
    if (next === 0) delete progress[chId];
    else progress[chId] = next;
    saveProgress(progress);
    applyCheckState(check, next);
    updateUnitProgress(check.closest('.unit-accordion'));
  });
});

function updateUnitProgress(unitAcc) {
  if (!unitAcc) return;
  var rows = unitAcc.querySelectorAll('.planner-row.populated');
  var progress = loadProgress();
  var partial = 0, complete = 0;
  rows.forEach(function(row) {
    var id = row.dataset.id;
    var state = progress[id] || 0;
    if (state === 1) partial++;
    else if (state === 2) complete++;
  });
  var total = rows.length;
  var unitId = unitAcc.id;
  var bar = document.getElementById(unitId.replace('acc', 'bar'));
  var barPartial = document.getElementById(unitId.replace('acc', 'barpartial'));
  var countEl = document.getElementById(unitId.replace('acc', 'count'));
  if (bar) bar.style.width = (total ? (complete / total * 100) : 0) + '%';
  if (barPartial) barPartial.style.width = (total ? ((complete + partial) / total * 100) : 0) + '%';
  if (countEl) countEl.textContent = complete + ' / ' + total + ' read';
}

function updateAllUnitProgress() {
  document.querySelectorAll('.unit-accordion').forEach(updateUnitProgress);
}

function initProgress() {
  var progress = loadProgress();
  document.querySelectorAll('[data-toggle-check]').forEach(function(check) {
    var state = progress[check.dataset.toggleCheck] || 0;
    applyCheckState(check, state);
  });
  updateAllUnitProgress();
}

// Reset Unit Progress
document.querySelectorAll('[data-reset-unit]').forEach(function(btn) {
  btn.addEventListener('click', function() {
    var unitAccId = btn.dataset.resetUnit;
    var unitAcc = document.getElementById(unitAccId);
    if (!unitAcc) return;
    if (!confirm('Reset progress for ' + unitAcc.querySelector('.unit-title').textContent + '?')) return;
    var rows = unitAcc.querySelectorAll('.planner-row.populated');
    var progress = loadProgress();
    rows.forEach(function(row) { delete progress[row.dataset.id]; });
    saveProgress(progress);
    rows.forEach(function(row) {
      var check = row.querySelector('.planner-check');
      if (check) applyCheckState(check, 0);
    });
    updateUnitProgress(unitAcc);
  });
});
```

### 7.21 Full function catalog (49 functions in Book IIFE)

```
1.  applyThemeUI                  Sync theme icon/label to current state
2.  openSidebarPanel              Add .open to sidebar + show overlay
3.  closeSidebarPanel             Remove .open from sidebar + hide overlay
4.  loadProgress                  Parse PROGRESS_KEY from localStorage
5.  saveProgress                  Stringify and store progress
6.  applyCheckState               Set .reviewed/.complete classes on a check
7.  updateUnitProgress            Recalc one unit's bar fill & count
8.  updateAllUnitProgress         Loop all units
9.  initProgress                  Restore checks from saved state at load
10. showTip                       Position and reveal abbr tooltip
11. bindAbbrs                     Wire mouseenter/leave/click to abbr spans
12. bindExercises                 Wire click-to-reveal on exercise headers
13. updateTabFade                 Add/remove shadow-left/shadow-right on tabs wrap
14. buildTabLabel                 Choose tab label from section (TL;DR, Templates, Practice, h2 text)
15. openChapter                   Main modal-open logic
16. closeChapterModal             Hide modal, clear hash
17. autoWrapAbbreviations         Walk text nodes, wrap matched abbrs with <span class="abbr">
18. clearSearchHighlights         Remove <mark.search-hit> from container
19. highlightInContainer          Insert <mark.search-hit> around query matches
20. escapeRegExp                  Escape regex special chars
21. escapeHtml                    Escape HTML entities
22. handleSearch                  Live-search dropdown
23. buildPrintContent             Populate print-overlay content
24. openPrintOverlay              Show print overlay with mode toolbar
25. render                        (Templates only — render filtered example list)
26. closePrintOverlay             Hide print overlay
27. loadFcSchedule                Parse FC_SCHEDULE_KEY
28. saveFcSchedule                Stringify and store schedule
29. rateFlashcard                 Update card in schedule using sm2Update
30. buildPromptCard               Construct DOM for an injected typed prompt
31. injectAllPrompts              Iterate MID_PROMPTS and insert cards
32. recordLastChapter             Save chapterId|sectionId|label to localStorage
33. _installCrossToolHook         Wrap openChapter to call recordLastChapter
34. loadBookmarks                 Parse BOOKMARK_KEY
35. saveBookmarks                 Stringify and store bookmarks
36. toggleBookmark                Add/remove a bookmark
37. updateBookmarkUI              Update count badge
38. injectBookmarkButtons         Insert ☆ button before each h2 in modal
39. renderBookmarksList           Populate bookmarks panel
40. _withBookmarkInject           Wrap openChapter to call injectBookmarkButtons
41. loadNclexDone                 Parse NCLEX_DONE_KEY
42. saveNclexDone                 Stringify and store
43. isSataQuestion                Check if .answer.correct count > 1
44. applyNclexFilter              Hide/show exercises based on filter
45. injectNclexFilterBar          Insert filter UI into each exercises section
46. _withNclexInject              Wrap openChapter to call injectNclexFilterBar
47. loadSched                     (alias for loadFcSchedule — internal)
48. saveSched                     (alias for saveFcSchedule — internal)
49. sm2Update                     Apply SM-2 algorithm to a card
```

**SM-2 canonical implementation:**
```javascript
function sm2Update(card, rating) {
  // rating is 0 (Hard/fail), 3 (Good), 5 (Easy)
  if (rating >= 3) {
    if (card.reps === 0) card.interval = 1;
    else if (card.reps === 1) card.interval = 6;
    else card.interval = Math.round(card.interval * card.ef);
    card.reps = (card.reps || 0) + 1;
  } else {
    card.reps = 0;
    card.interval = 1;
  }
  card.ef = Math.max(1.3, (card.ef || 2.5) + 0.1 - (5 - rating) * (0.08 + (5 - rating) * 0.02));
  card.nextReview = new Date(Date.now() + card.interval * 86400000).toISOString();
  return card;
}
```

### 7.22 Reference template — full chapter skeleton

> Pasteable scaffold for a new chapter. Copy and replace placeholders with subject content. Required structural elements are explicitly noted.

Save the below structure for every chapter. Replace bracketed placeholders. Delete sections that don't apply (e.g., `chN-als` when source has none — see B.1.1).

```html
<section class="chapter" id="chN">

  <!-- ═══════════════════════════════════════════════════════════════
       BANNER (consumed by modal header, never a tab)
       ═══════════════════════════════════════════════════════════════ -->
  <div class="chapter-banner">
    <div class="chapter-meta">Unit [X] · [Unit Name] · Chapter [N]</div>
    <h2 class="chapter-name"><em>[Chapter Title]</em></h2>
    <p class="chapter-lede">
      [1-2 sentence framing of what this chapter covers and why it matters.]
    </p>
  </div>

  <!-- ═══════════════════════════════════════════════════════════════
       TAB 1: TL;DR (always first, always exists)
       Voice: punchy, formulaic, bolded keys. See A.1.2
       ═══════════════════════════════════════════════════════════════ -->
  <section id="chN-tldr" class="brief-card">
    <h2>TL;DR · One-glance summary</h2>
    <p class="tldr">
      [Lead sentence stating core concept as formula or ladder.]
      [Most important clinical implication.]
      <strong>[Critical warning or contraindication.]</strong>
    </p>
    <div class="brief-grid">
      <div>
        <h3>[Column 1 heading — e.g., "The six categories"]</h3>
        <ul>
          <li><strong>[Term]</strong> — [brief definition]</li>
          <li><strong>[Term]</strong> — [brief definition]</li>
          <li><strong>[Term]</strong> — [brief definition]</li>
        </ul>
      </div>
      <div>
        <h3>[Column 2 heading — e.g., "Key contraindications"]</h3>
        <ul>
          <li><strong>[Term]:</strong> [brief detail]</li>
          <li><strong>[Term]:</strong> [brief detail]</li>
        </ul>
      </div>
    </div>
  </section>

  <!-- ═══════════════════════════════════════════════════════════════
       TABS 2..N: Content sections (one per topic)
       Voice: clinical, terse, imperative actions. See A.1.4
       ═══════════════════════════════════════════════════════════════ -->
  <section id="chN-[topic1]" class="content-section">
    <h2>[Topic 1 Heading]</h2>
    <p class="section-lead">
      [1-2 sentence framing. End with warning if relevant.]
    </p>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">[Condition Name]</h3>
        <span class="condition-tag">[1-3 word qualifier]</span>
      </header>
      <p>[1-3 sentence definition / context.]</p>

      <div class="finding-grid">
        <div class="finding-card">
          <h4>[Card heading — e.g., "Risk Factors"]</h4>
          <ul>
            <li><strong>[Key term]</strong> — [detail]</li>
            <li><strong>[Key term]</strong> — [detail]</li>
          </ul>
        </div>
        <div class="finding-card">
          <h4>[Card heading — e.g., "Nursing Care"]</h4>
          <ul>
            <li>[Imperative verb] [object] [specifics]</li>
            <li>[Imperative verb] [object] [specifics]</li>
          </ul>
        </div>
      </div>
    </article>

    <!-- More condition-blocks as needed -->

    <!-- Optional: inline mid-read prompt (concept/warning/calc).
         Place where reader benefits from pausing on a tricky fact. -->
    <aside class="mid-read"
      data-fc-id="fc-chN-[short-name]"
      data-fc-ch="N"
      data-fc-type="concept"
      data-fc-anchor="chN-[topic1]"
      data-fc-q="[Question text]"
      data-fc-a="[Answer with <strong>key terms</strong> bolded]">
      <div class="mid-read-q">[Question text]</div>
      <button class="mid-read-reveal" type="button">Reveal answer</button>
      <div class="mid-read-a">[Answer with <strong>key terms</strong> bolded]</div>
      <div class="mid-read-rate">
        <button data-rate="0">Hard<span class="mid-read-rate-small">+1 day</span></button>
        <button data-rate="3">Good<span class="mid-read-rate-small">extend</span></button>
        <button data-rate="5">Easy<span class="mid-read-rate-small">boost</span></button>
      </div>
    </aside>
  </section>

  <!-- Repeat <section id="chN-[topic2]"> ... </section> for each topic.
       Number of topics is content-driven; no fixed count. -->

  <!-- ═══════════════════════════════════════════════════════════════
       TAB: ALS (if source PDF has one — present in 24/27 MN chapters)
       Voice: textbook for scenario, imperative for answer key. See A.1.5
       ═══════════════════════════════════════════════════════════════ -->
  <section id="chN-als" class="content-section">
    <h2>Active Learning Scenario</h2>
    <p class="section-lead">
      From the textbook — uses the <strong>ATI [Template Type]</strong> template.
      Practice answering before reviewing the key.
    </p>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">Scenario</h3>
      </header>
      <p><em>[The scenario as it appears in the textbook, italicized.]</em></p>
      <ul>
        <li><strong>Related Content:</strong> [What to describe]</li>
        <li><strong>Underlying Principles:</strong> [What to explain]</li>
        <li><strong>Nursing Interventions:</strong> [What to identify]</li>
      </ul>
    </article>

    <article class="condition-block">
      <header class="condition-head">
        <h3 class="condition-name">Answer key</h3>
      </header>
      <div class="finding-grid">
        <div class="finding-card">
          <h4>Related Content</h4>
          <ul>
            <li>[Bullet]</li>
            <li>[Bullet]</li>
            <li>[Bullet]</li>
          </ul>
        </div>
        <div class="finding-card">
          <h4>Underlying Principles</h4>
          <p>[Short explanation.]</p>
        </div>
      </div>
      <div class="kb-card">
        <h4>Nursing Interventions</h4>
        <ul>
          <li>[Imperative action]</li>
          <li>[Imperative action]</li>
          <li>[Imperative action]</li>
        </ul>
      </div>
    </article>
  </section>

  <!-- ═══════════════════════════════════════════════════════════════
       TAB: EXERCISES (always, exactly 5 questions)
       Voice: standard NCLEX patterns. See A.3
       ═══════════════════════════════════════════════════════════════ -->
  <section id="chN-exercises" class="content-section">
    <h2>Practice · Application Exercises</h2>
    <p class="section-lead">
      5 NCLEX-style questions covering Ch N core content. Click each exercise
      to reveal rationales and NCLEX category.
    </p>

    <article class="exercise" data-q-id="chN-q1">
      <header class="exercise-q" data-toggle>
        <span class="q-num">Q1</span>
        <p>[Question stem following Pattern 1, 2, 3, or 4 — see A.3.3]</p>
        <ol class="q-options">
          <li>A. "[Option A]"</li>
          <li>B. "[Option B]"</li>
          <li>C. "[Option C]"</li>
          <li>D. "[Option D]"</li>
        </ol>
        <span class="q-toggle">Show rationale ▾</span>
      </header>
      <div class="exercise-a">
        <p class="answer correct">
          <span class="ans-letter">A.</span> <strong>CORRECT.</strong>
          [Rationale: 1 sentence with the principle, 1 sentence with the detail.]
        </p>
        <p class="answer">
          <span class="ans-letter">B.</span> [Why incorrect — what's true instead.]
        </p>
        <p class="answer">
          <span class="ans-letter">C.</span> [Why incorrect.]
        </p>
        <p class="answer">
          <span class="ans-letter">D.</span> [Why incorrect.]
        </p>
        <span class="nclex-tag">NCLEX · [Category] · [Subcategory]</span>
      </div>
    </article>

    <!-- Q2 through Q5 — same structure. 1-2 should be SATA (multiple .correct). -->
  </section>

  <!-- ═══════════════════════════════════════════════════════════════
       TAB: TEMPLATES BRIDGE (always, even if no templates bridge here)
       ═══════════════════════════════════════════════════════════════ -->
  <section id="chN-templates" class="content-section tpl-bridge">
    <h2>ATI Templates · this chapter</h2>
    <ul>
      <li><a href="Elevated%20ATI%20[Subject]%20Templates.html#ex-chN-[name]">[Template Title]</a></li>
      <li><a href="Elevated%20ATI%20[Subject]%20Templates.html#ex-chN-[name]">[Template Title]</a></li>
    </ul>
    <!-- If 0 templates bridge to this chapter, use B.1.4 fallback copy. -->
  </section>

</section><!-- /chN -->
```

#### D.1.1 What to also do per chapter (NOT in HTML)

After completing the HTML above:

```javascript
// 1. Add to MID_PROMPTS data structure in Book Script 3:
MID_PROMPTS["chN"] = [
  {
    id: "chN-p1",
    type: "PRIORITY",    // pick per A.2 rubric
    after: "chN-[some-topic]",
    q: "[Question text]",
    a: "[Answer text with <strong>key terms</strong> bolded]"
  },
  {
    id: "chN-p2",
    type: "JUDGMENT",
    after: "chN-[some-topic]",
    q: "[Question text]",
    a: "[Answer text]"
  }
];

// 2. Add sidebar entry:
// In <nav class="sidebar-list">, find the right <div class="nav-section">,
// add <a href="#chN" class="sidebar-item populated" data-section="chN">
//   <span class="item-num">NN</span>
//   <span class="item-name">[Chapter Title]</span>
// </a>

// 3. Add planner row:
// In the corresponding <div class="unit-accordion">'s <div class="unit-body">,
// add a <div class="planner-row populated" data-id="chN"> ... </div>

// 4. Update unit count:
// The <span class="unit-count" id="unitXcount"> should reflect the new total
// (it'll auto-recalc once user marks chapters read).
```

---

### 7.23 Reference data — full ABBR_DICT (277 entries)

> Full abbreviation dictionary used by `bindAbbrs()` (PART 7.16). Subject-specific — MN dict shown here. Porters must rebuild this from their subject's terminology.

This is the complete abbreviation dictionary as it appears in the MN Book. Pharm and PD subjects share most of these but add subject-specific terms.

```javascript
const ABBR_DICT = {
  // Vitals & Assessment
  "HR": "Heart Rate",
  "BP": "Blood Pressure",
  "RR": "Respiratory Rate",
  "VS": "Vital Signs",
  "SpO2": "Oxygen Saturation",
  "BMI": "Body Mass Index",
  "DTRs": "Deep Tendon Reflexes",
  "LOC": "Level of Consciousness",
  "GCS": "Glasgow Coma Scale",
  "SBP": "Systolic Blood Pressure",
  "DBP": "Diastolic Blood Pressure",
  "MAP": "Mean Arterial Pressure",
  "PR": "Per Rectum",
  "I&O": "Intake and Output",
  "CBC": "Complete Blood Count",
  "BUN": "Blood Urea Nitrogen",
  "WBC": "White Blood Cell Count",
  "RBC": "Red Blood Cell",

  // Fetal Monitoring
  "FHR": "Fetal Heart Rate",
  "FHT": "Fetal Heart Tones",
  "EFM": "Electronic Fetal Monitoring",
  "NST": "Non-Stress Test",
  "CST": "Contraction Stress Test",
  "BPP": "Biophysical Profile",
  "AFI": "Amniotic Fluid Index",
  "AFV": "Amniotic Fluid Volume",
  "SVE": "Sterile Vaginal Exam",
  "EFW": "Estimated Fetal Weight",

  // Pregnancy/OB
  "LMP": "Last Menstrual Period",
  "EDD": "Estimated Date of Delivery",
  "EDC": "Estimated Date of Confinement",
  "GA": "Gestational Age",
  "TPAL": "Term, Preterm, Abortion, Living",
  "GTPAL": "Gravida, Term, Preterm, Abortion, Living children",
  "SAB": "Spontaneous Abortion",
  "IUFD": "Intrauterine Fetal Demise",
  "SGA": "Small for Gestational Age",
  "LGA": "Large for Gestational Age",
  "AGA": "Appropriate for Gestational Age",
  "LBW": "Low Birth Weight",
  "VLBW": "Very Low Birth Weight",
  "VBAC": "Vaginal Birth After Cesarean",
  "TOLAC": "Trial of Labor After Cesarean",
  "C/S": "Cesarean Section",
  "VBAC": "Vaginal Birth After Cesarean",
  "ROM": "Rupture of Membranes",
  "PROM": "Premature Rupture of Membranes",
  "PPROM": "Preterm Premature Rupture of Membranes",
  "SROM": "Spontaneous Rupture of Membranes",
  "AROM": "Artificial Rupture of Membranes",

  // Conditions
  "PIH": "Pregnancy-Induced Hypertension",
  "HTN": "Hypertension",
  "GDM": "Gestational Diabetes Mellitus",
  "DM": "Diabetes Mellitus",
  "HELLP": "Hemolysis, Elevated Liver enzymes, Low Platelets",
  "DIC": "Disseminated Intravascular Coagulation",
  "PE": "Pulmonary Embolism",
  "PPH": "Postpartum Hemorrhage",
  "UTI": "Urinary Tract Infection",
  "GBS": "Group B Streptococcus",
  "STI": "Sexually Transmitted Infection",
  "HSV": "Herpes Simplex Virus",
  "HPV": "Human Papillomavirus",
  "HIV": "Human Immunodeficiency Virus",
  "HBV": "Hepatitis B Virus",
  "CMV": "Cytomegalovirus",
  "RDS": "Respiratory Distress Syndrome",
  "TTN": "Transient Tachypnea of the Newborn",
  "MAS": "Meconium Aspiration Syndrome",
  "NAS": "Neonatal Abstinence Syndrome",
  "BPD": "Bronchopulmonary Dysplasia",
  "IVH": "Intraventricular Hemorrhage",
  "ROP": "Retinopathy of Prematurity",
  "NEC": "Necrotizing Enterocolitis",

  // Procedures
  "HSG": "Hysterosalpingography",
  "D&C": "Dilation and Curettage",
  "CST": "Contraction Stress Test",
  "NST": "Non-Stress Test",
  "BPP": "Biophysical Profile",
  "ECV": "External Cephalic Version",
  "I&O": "Intake and Output",
  "IUD": "Intrauterine Device",
  "LARC": "Long-Acting Reversible Contraception",
  "AROM": "Artificial Rupture of Membranes",
  "SROM": "Spontaneous Rupture of Membranes",
  "C/S": "Cesarean Section",

  // Other (clinical, anatomical, pharmacological)
  "AAP": "American Academy of Pediatrics",
  "ABG": "Arterial Blood Gas",
  "ABGs": "Arterial Blood Gases",
  "ACE": "Angiotensin-Converting Enzyme",
  "ACHES": "Abdominal pain, Chest pain, Headache, Eye changes, Severe leg pain",
  "ACOG": "American College of Obstetricians and Gynecologists",
  "ADH": "Antidiuretic Hormone",
  "ADLs": "Activities of Daily Living",
  "AED": "Automated External Defibrillator",
  "AFE": "Amniotic Fluid Embolism",
  "AFP": "Alpha-Fetoprotein",
  "ALT": "Alanine Aminotransferase",
  "AMA": "Against Medical Advice",
  "ANC": "Absolute Neutrophil Count",
  "APGAR": "Appearance, Pulse, Grimace, Activity, Respiration",
  "ARB": "Angiotensin Receptor Blocker",
  "ARDS": "Acute Respiratory Distress Syndrome",
  "ART": "Assisted Reproductive Technology",
  "ASD": "Atrial Septal Defect",
  "AST": "Aspartate Aminotransferase",
  "BFA": "Baby-Friendly Hospital",
  "BID": "Twice Daily",
  "BMP": "Basic Metabolic Panel",
  "BUBBLE-HE": "Breasts, Uterus, Bladder, Bowel, Lochia, Episiotomy, Homans, Emotional",
  "BV": "Bacterial Vaginosis",
  "BiPAP": "Bilevel Positive Airway Pressure",
  "C&S": "Culture and Sensitivity",
  "CAD": "Coronary Artery Disease",
  "CDC": "Centers for Disease Control and Prevention",
  "CHD": "Congenital Heart Disease",
  "CHF": "Congestive Heart Failure",
  "CMP": "Comprehensive Metabolic Panel",
  "CNS": "Central Nervous System",
  "COCs": "Combined Oral Contraceptives",
  "COPD": "Chronic Obstructive Pulmonary Disease",
  "CPAP": "Continuous Positive Airway Pressure",
  "CPD": "Cephalopelvic Disproportion",
  "CPR": "Cardiopulmonary Resuscitation",
  "CRP": "C-Reactive Protein",
  "CSF": "Cerebrospinal Fluid",
  "CT": "Computed Tomography",
  "CVA": "Cerebrovascular Accident (Stroke)",
  "DNR": "Do Not Resuscitate",
  "DPNB": "Dorsal Penile Nerve Block",
  "DPT": "Diphtheria, Pertussis, Tetanus",
  "DTAP": "Diphtheria, Tetanus, Pertussis Vaccine",
  "DVT": "Deep Vein Thrombosis",
  "ECG": "Electrocardiogram",
  "ECMO": "Extracorporeal Membrane Oxygenation",
  "EEG": "Electroencephalogram",
  "EGA": "Estimated Gestational Age",
  "EKG": "Electrocardiogram",
  "ELBW": "Extremely Low Birth Weight",
  "ESR": "Erythrocyte Sedimentation Rate",
  "ETT": "Endotracheal Tube",
  "FAS": "Fetal Alcohol Syndrome",
  "FASD": "Fetal Alcohol Spectrum Disorder",
  "FDA": "Food and Drug Administration",
  "FFP": "Fresh Frozen Plasma",
  "FSE": "Fetal Scalp Electrode",
  "FSH": "Follicle-Stimulating Hormone",
  "FTT": "Failure to Thrive",
  "FiO2": "Fraction of Inspired Oxygen",
  "GCT": "Glucose Challenge Test",
  "GERD": "Gastroesophageal Reflux Disease",
  "GI": "Gastrointestinal",
  "GIFT": "Gamete Intrafallopian Transfer",
  "GTD": "Gestational Trophoblastic Disease",
  "GU": "Genitourinary",
  "H&H": "Hemoglobin and Hematocrit",
  "HBIG": "Hepatitis B Immune Globulin",
  "HCP": "Healthcare Provider",
  "HDN": "Hemorrhagic Disease of the Newborn",
  "HF": "Heart Failure",
  "HFOV": "High-Frequency Oscillatory Ventilation",
  "HIE": "Hypoxic-Ischemic Encephalopathy",
  "HOB": "Head of Bed",
  "HbA1c": "Glycosylated Hemoglobin",
  "Hct": "Hematocrit",
  "Hgb": "Hemoglobin",
  "HgbA1c": "Glycosylated Hemoglobin",
  "ICP": "Intracranial Pressure",
  "ICSI": "Intracytoplasmic Sperm Injection",
  "IDA": "Iron Deficiency Anemia",
  "IM": "Intramuscular",
  "INR": "International Normalized Ratio",
  "IPV": "Inactivated Polio Vaccine",
  "ITP": "Immune Thrombocytopenic Purpura",
  "IU": "International Units",
  "IUGR": "Intrauterine Growth Restriction",
  "IUPC": "Intrauterine Pressure Catheter",
  "IV": "Intravenous",
  "IVF": "In Vitro Fertilization",
  "IVIG": "Intravenous Immunoglobulin",
  "L&D": "Labor and Delivery",
  "LDH": "Lactate Dehydrogenase",
  "LFTs": "Liver Function Tests",
  "LH": "Luteinizing Hormone",
  "LLQ": "Left Lower Quadrant",
  "LP": "Lumbar Puncture",
  "LPN": "Licensed Practical Nurse",
  "LUQ": "Left Upper Quadrant",
  "MAOI": "Monoamine Oxidase Inhibitor",
  "MAOIs": "Monoamine Oxidase Inhibitors",
  "MI": "Myocardial Infarction",
  "MMR": "Measles, Mumps, Rubella Vaccine",
  "MRI": "Magnetic Resonance Imaging",
  "MSK": "Musculoskeletal",
  "MTX": "Methotrexate",
  "MVU": "Montevideo Units",
  "MVUs": "Montevideo Units",
  "NG": "Nasogastric",
  "NICU": "Neonatal Intensive Care Unit",
  "NPO": "Nothing By Mouth",
  "NRP": "Neonatal Resuscitation Program",
  "NSAID": "Nonsteroidal Anti-Inflammatory Drug",
  "NSAIDs": "Nonsteroidal Anti-Inflammatory Drugs",
  "NTD": "Neural Tube Defect",
  "NTDs": "Neural Tube Defects",
  "OA": "Occiput Anterior",
  "OB": "Obstetrics",
  "OBGYN": "Obstetrics and Gynecology",
  "OCP": "Oral Contraceptive Pill",
  "OGTT": "Oral Glucose Tolerance Test",
  "OHSS": "Ovarian Hyperstimulation Syndrome",
  "OP": "Occiput Posterior",
  "OTC": "Over The Counter",
  "P/C ratio": "Protein to Creatinine Ratio",
  "PCN": "Penicillin",
  "PCOS": "Polycystic Ovary Syndrome",
  "PDA": "Patent Ductus Arteriosus",
  "PEEP": "Positive End-Expiratory Pressure",
  "PICC": "Peripherally Inserted Central Catheter",
  "PKU": "Phenylketonuria",
  "PO": "By Mouth (Per Os)",
  "PPD": "Postpartum Depression",
  "PPE": "Personal Protective Equipment",
  "PPHN": "Persistent Pulmonary Hypertension of the Newborn",
  "PPI": "Proton Pump Inhibitor",
  "PPV": "Positive Pressure Ventilation",
  "PRBC": "Packed Red Blood Cells",
  "PRN": "As Needed",
  "PT/PTT": "Prothrombin Time / Partial Thromboplastin Time",
  "PTT": "Partial Thromboplastin Time",
  "PaCO2": "Partial Pressure of Carbon Dioxide",
  "PaO2": "Partial Pressure of Oxygen",
  "QID": "Four Times Daily",
  "RBCs": "Red Blood Cells",
  "RLQ": "Right Lower Quadrant",
  "RN": "Registered Nurse",
  "ROM ": "Range of Motion",
  "RSV": "Respiratory Syncytial Virus",
  "RUQ": "Right Upper Quadrant",
  "Rh": "Rhesus factor",
  "RhoGAM": "Rh Immune Globulin",
  "SBAR": "Situation, Background, Assessment, Recommendation",
  "SC": "Subcutaneous",
  "SCD": "Sickle Cell Disease",
  "SIADH": "Syndrome of Inappropriate ADH",
  "SIDS": "Sudden Infant Death Syndrome",
  "SL": "Sublingual",
  "SLE": "Systemic Lupus Erythematosus",
  "SSRI": "Selective Serotonin Reuptake Inhibitor",
  "SSRIs": "Selective Serotonin Reuptake Inhibitors",
  "STAT": "Immediately (statim)",
  "STIs": "Sexually Transmitted Infections",
  "SVD": "Spontaneous Vaginal Delivery",
  "SubQ": "Subcutaneous",
  "T1DM": "Type 1 Diabetes Mellitus",
  "T2DM": "Type 2 Diabetes Mellitus",
  "TAB": "Therapeutic Abortion",
  "TID": "Three Times Daily",
  "TOF": "Tetralogy of Fallot",
  "TOR": "Time of Rupture",
  "TORCH": "Toxoplasmosis, Other, Rubella, CMV, Herpes",
  "TPN": "Total Parenteral Nutrition",
  "TSH": "Thyroid-Stimulating Hormone",
  "TXA": "Tranexamic Acid",
  "Tdap": "Tetanus, Diphtheria, Pertussis Booster",
  "UA": "Urinalysis",
  "UAP": "Unlicensed Assistive Personnel",
  "US": "Ultrasound",
  "VEAL CHOP": "Variable-Cord, Early-Head, Accelerations-OK, Late-Placenta",
  "VKDB": "Vitamin K Deficiency Bleeding",
  "VSD": "Ventricular Septal Defect",
  "VTE": "Venous Thromboembolism",
  "WIC": "Women, Infants, and Children program",
  "WNL": "Within Normal Limits",
  "ZIFT": "Zygote Intrafallopian Transfer",
  "aPTT": "Activated Partial Thromboplastin Time",
  "hCG": "Human Chorionic Gonadotropin",
  "hPL": "Human Placental Lactogen",
  "iNO": "Inhaled Nitric Oxide",
  "mEq": "Milliequivalents",
  "mEq/L": "Milliequivalents Per Liter",
  "mL": "Milliliters",
  "mU/min": "Milliunits Per Minute",
  "mcg": "Micrograms",
  "mg/dL": "Milligrams Per Deciliter",
};
```

### 7.24 Reference data — full MID_PROMPTS (54 typed prompts)

> Full typed-prompt data used by Script 3 mid-prompt injection (PART 7.10). Subject-specific — MN prompts shown here. Porters must write subject-specific prompts following the same structure.

All 54 typed mid-prompts as they appear in MN Book Script 3.

```javascript
var MID_PROMPTS = {
  "ch1": [
    {
      id: "ch1-p1",
      type: "PRIORITY",
      after: "ch1-hormonal",
      q: "A client missed two consecutive doses of combined oral contraceptives in the first week of the pack. What is the priority instruction?",
      a: "Take the most recent missed pill ASAP (even if 2 pills in one day), take the next pill at the regular time, use backup contraception for 7 days, and consider emergency contraception if there was unprotected intercourse in the past 5 days."
    },
    {
      id: "ch1-p2",
      type: "JUDGMENT",
      after: "ch1-hormonal",
      q: "A breastfeeding mother at 6 weeks postpartum wants combined oral contraceptives. What is the appropriate response?",
      a: "COCs are NOT recommended for breastfeeding mothers — estrogen decreases milk supply. Progestin-only pills (mini-pills), the IUD, implant, or DMPA are preferred non-estrogen methods."
    },
  ],
  "ch2": [
    {
      id: "ch2-p1",
      type: "CONTENT",
      after: "ch2-assessment",
      q: "What basal body temperature pattern indicates ovulation has occurred?",
      a: "A sustained rise of 0.4–1.0°F (0.2–0.5°C) above baseline for 3+ consecutive days. The dip just before, then sustained rise, confirms ovulation has occurred. Best used retrospectively, not predictively."
    },
    {
      id: "ch2-p2",
      type: "PRINCIPLE",
      after: "ch2-diagnostic",
      q: "Why is hysterosalpingography (HSG) typically performed in the follicular phase before ovulation?",
      a: "To avoid disrupting a potential early pregnancy and because minimal endometrial thickness in the follicular phase provides clearer imaging of tubal patency."
    },
  ],
  "ch3": [
    {
      id: "ch3-p1",
      type: "CONTENT",
      after: "ch3-vitals",
      q: "At what gestational week is the uterine fundus expected to be at the umbilicus?",
      a: "20 weeks gestation. The fundus rises ~1 cm/week from 20–36 wks (matching gestational age in cm), then drops slightly with lightening before delivery."
    },
    {
      id: "ch3-p2",
      type: "JUDGMENT",
      after: "ch3-systems",
      q: "A pregnant client at 28 weeks has a hemoglobin of 10.5 g/dL. Is this expected?",
      a: "Yes — physiologic anemia of pregnancy from plasma volume expanding faster than RBC mass. Diagnostic thresholds: Hgb < 11 g/dL (1st/3rd trimesters) or < 10.5 g/dL (2nd trimester). Review iron intake and supplementation."
    },
  ],
  "ch4": [
    {
      id: "ch4-p1",
      type: "CONTENT",
      after: "ch4-schedule",
      q: "What is the recommended frequency of prenatal visits at 36 weeks gestation?",
      a: "Weekly. Standard schedule: monthly until 28 wks → every 2 weeks from 28–36 wks → weekly from 36 wks until birth."
    },
    {
      id: "ch4-p2",
      type: "PRIORITY",
      after: "ch4-danger",
      q: "A client at 30 weeks reports decreased fetal movement for the past 4 hours. What is the priority action?",
      a: "Have the client perform a kick count after eating/hydrating (10 movements within 1–2 hours expected). If fewer than 10 movements in 2 hours, instruct her to come in immediately for NST/BPP. Never minimize this symptom."
    },
  ],
  "ch5": [
    {
      id: "ch5-p1",
      type: "CONTENT",
      after: "ch5-education",
      q: "How much folic acid is recommended daily for women of childbearing age and during pregnancy?",
      a: "400 mcg daily for women of childbearing age (to prevent NTDs before conception). 600 mcg daily during pregnancy. 4 mg daily for women with a previous NTD-affected pregnancy."
    },
    {
      id: "ch5-p2",
      type: "JUDGMENT",
      after: "ch5-risk",
      q: "A pregnant client states 'I don't eat meat or dairy.' What nutritional priority should be addressed?",
      a: "Vitamin B12 adequacy is the urgent concern — B12 deficiency in pregnancy can cause irreversible neurologic damage to the fetus. Also assess iron, complete protein, calcium, and zinc. Refer to dietitian; consider B12 supplementation."
    },
  ],
  "ch6": [
    {
      id: "ch6-p1",
      type: "JUDGMENT",
      after: "ch6-nst",
      q: "A 20-minute NST on a 34-week fetus shows 2 accelerations of 15 bpm above baseline, lasting 15 seconds each. Interpretation?",
      a: "REACTIVE (reassuring). Reactive NST at ≥ 32 wks requires ≥ 2 accelerations of 15 bpm × 15 seconds within 20 minutes. Before 32 wks: 10 bpm × 10 sec threshold."
    },
    {
      id: "ch6-p2",
      type: "PRIORITY",
      after: "ch6-bpp",
      q: "A biophysical profile (BPP) score returns at 4 out of 10. What is the immediate action?",
      a: "BPP ≤ 4 is highly suggestive of fetal asphyxia — prompt delivery is indicated. Notify provider immediately, prepare for cesarean delivery, initiate continuous EFM, ensure IV access, and obtain consent."
    },
  ],
  "ch7": [
    {
      id: "ch7-p1",
      type: "PRIORITY",
      after: "ch7-placenta-previa",
      q: "A client at 34 weeks reports painless, bright red vaginal bleeding. What is the FIRST action?",
      a: "Do NOT perform a vaginal exam (risk of disrupting placenta in previa). Place client on bedrest in side-lying position, initiate continuous FHR monitoring, assess maternal VS, establish IV access, type and crossmatch, prepare for cesarean. Painless bright red = placenta previa until proven otherwise."
    },
    {
      id: "ch7-p2",
      type: "JUDGMENT",
      after: "ch7-ectopic",
      q: "A client receives methotrexate for ectopic pregnancy. What is the priority client teaching?",
      a: "Avoid folic acid supplements (interferes with methotrexate), avoid NSAIDs (decrease efficacy), avoid alcohol, avoid sun exposure (photosensitivity), and report severe abdominal pain (could indicate rupture). Follow up beta-hCG levels weekly until negative."
    },
  ],
  "ch8": [
    {
      id: "ch8-p1",
      type: "CONTENT",
      after: "ch8-gbs",
      q: "When is GBS screening routinely performed during pregnancy?",
      a: "36 0/7 to 37 6/7 weeks gestation via vaginal-rectal swab. If positive (or unknown status with risk factors), intrapartum IV penicillin prophylaxis is required to prevent neonatal early-onset GBS disease."
    },
    {
      id: "ch8-p2",
      type: "PRIORITY",
      after: "ch8-hiv",
      q: "An HIV-positive client is in active labor with a viral load of 2,500 copies/mL. What is the critical intervention?",
      a: "Schedule/prepare for cesarean delivery (recommended if viral load > 1,000 copies/mL). IV zidovudine (ZDV) infusion during labor regardless of route. Continue ART. AVOID AROM, internal fetal scalp electrodes, and instrument delivery. Newborn receives ART prophylaxis within 6–12 hours of birth."
    },
  ],
  "ch9": [
    {
      id: "ch9-p1",
      type: "PRIORITY",
      after: "ch9-magsulfate",
      q: "A client on magnesium sulfate infusion has absent DTRs, RR of 10, and urine output of 25 mL/hr. Priority action?",
      a: "STOP the magnesium infusion immediately. Administer calcium gluconate 1 g IV (the antidote). Notify provider. Toxicity signs in order: loss of DTRs (first), RR < 12, urine output < 30 mL/hr, serum Mg > 7 mEq/L."
    },
    {
      id: "ch9-p2",
      type: "JUDGMENT",
      after: "ch9-gdm",
      q: "A pregnant client with type 1 DM has a fasting glucose of 60 mg/dL and reports shakiness. Next step?",
      a: "Treat hypoglycemia immediately: 15 g fast-acting carbohydrate (4 oz juice or glucose tablets). Recheck glucose in 15 minutes. Important physiology: insulin needs DECREASE in the 1st trimester (fetal glucose drain, nausea/vomiting), then INCREASE 2nd/3rd trimester. Reassess insulin regimen with provider."
    },
  ],
  "ch10": [
    {
      id: "ch10-p1",
      type: "CONTENT",
      after: "ch10-preterm",
      q: "At what gestational age is preterm labor diagnosed?",
      a: "Regular contractions causing cervical change between 20 0/7 and 36 6/7 weeks gestation. Late preterm: 34–36 6/7 wks. Most morbidity below 32 wks."
    },
    {
      id: "ch10-p2",
      type: "PRIORITY",
      after: "ch10-tocolytics",
      q: "A client at 31 weeks is in active preterm labor with regular contractions and cervix at 3 cm. Priority interventions?",
      a: "1) Betamethasone (corticosteroid) IM to accelerate fetal lung maturity — most important. 2) Tocolytics (terbutaline, nifedipine, indomethacin) to delay birth 48 hours for steroid effect. 3) Magnesium sulfate for fetal neuroprotection (< 32 wks). 4) IV access, continuous FHR, prepare for possible delivery."
    },
  ],
  "ch11": [
    {
      id: "ch11-p1",
      type: "CONTENT",
      after: "ch11-stages",
      q: "Name the 5 P's that affect the labor process.",
      a: "Powers (uterine contractions + maternal pushing), Passage (pelvic bones + soft tissue), Passenger (fetus — size, lie, attitude, position), Position (maternal positioning), Psyche (psychological response and support)."
    },
    {
      id: "ch11-p2",
      type: "JUDGMENT",
      after: "ch11-stages",
      q: "A multiparous client at 8 cm dilation states 'I feel pressure and need to push.' Action?",
      a: "Pressure at 8 cm is normal — do NOT allow pushing yet (causes cervical edema and tears). Encourage panting or 'hee-hee' breathing through contractions, reposition (side-lying or hands-and-knees), and re-examine to verify dilation. Only allow pushing when fully dilated (10 cm)."
    },
  ],
  "ch12": [
    {
      id: "ch12-p1",
      type: "PRIORITY",
      after: "ch12-anesthesia",
      q: "Ten minutes after epidural placement, maternal BP drops from 124/82 to 88/55. First action?",
      a: "Position client in LEFT LATERAL position (relieves aortocaval compression). Administer IV fluid bolus (LR). If BP doesn't improve, administer ephedrine or phenylephrine. Continuous FHR monitoring. Notify anesthesia. Hypotension from sympathetic blockade is the most common epidural complication."
    },
    {
      id: "ch12-p2",
      type: "CONTENT",
      after: "ch12-anesthesia",
      q: "What is the most common labor analgesia/anesthesia method used in the U.S.?",
      a: "Epidural block — continuous infusion of local anesthetic into the epidural space. Provides pain relief without complete sensory/motor loss, allowing some maternal movement and participation in pushing."
    },
  ],
  "ch13": [
    {
      id: "ch13-p1",
      type: "JUDGMENT",
      after: "ch13-patterns",
      q: "FHR shows LATE decelerations with each contraction. Interpretation and action sequence?",
      a: "Late decelerations = uteroplacental insufficiency (NONREASSURING). Apply LION: L — Left lateral position (or reposition), I — IV fluid bolus, O — Oxygen via face mask 10 L/min, N — Notify provider. Also: discontinue oxytocin if running; prepare for delivery if persistent."
    },
    {
      id: "ch13-p2",
      type: "CONTENT",
      after: "ch13-patterns",
      q: "Apply the VEAL CHOP mnemonic — what does each letter mean?",
      a: "V-E-A-L → C-H-O-P. Variable decel → Cord compression. Early decel → Head compression. Accelerations → Okay (reassuring). Late decel → Placental insufficiency."
    },
  ],
  "ch14": [
    {
      id: "ch14-p1",
      type: "PRIORITY",
      after: "ch14-fourth",
      q: "First nursing action in the 4th stage of labor (1st hour after birth)?",
      a: "Assess the FUNDUS (should be firm, midline, at or 1 cm below umbilicus). Massage if boggy. Then: assess lochia (heavy = saturating pad in 15 min), VS q15 min × 1 hr, encourage voiding (full bladder displaces uterus and causes atony), skin-to-skin contact, initiate breastfeeding."
    },
    {
      id: "ch14-p2",
      type: "CONTENT",
      after: "ch14-second",
      q: "Define a 3rd-degree perineal laceration.",
      a: "Extends through perineal skin, vaginal mucosa, perineal body muscle, AND external anal sphincter. Grading: 1st = skin only · 2nd = + perineal muscle · 3rd = + anal sphincter · 4th = through anal sphincter into rectal mucosa."
    },
  ],
  "ch15": [
    {
      id: "ch15-p1",
      type: "JUDGMENT",
      after: "ch15-bishop-ripening",
      q: "A client has a Bishop score of 4 prior to induction. What does this predict about the induction outcome?",
      a: "Bishop < 6 = UNFAVORABLE cervix → induction more likely to fail and require cesarean. Bishop ≥ 8 = favorable, success rate similar to spontaneous labor. With score 4: use cervical ripening (misoprostol PR or dinoprostone) first before oxytocin."
    },
    {
      id: "ch15-p2",
      type: "PRIORITY",
      after: "ch15-induction",
      q: "During oxytocin induction, the client has 6 contractions in 10 minutes (tachysystole) with Category II FHR tracing. First action?",
      a: "STOP the oxytocin infusion. Reposition (left lateral). Increase mainline IV fluid rate. Administer oxygen via face mask 10 L/min. If FHR doesn't improve, administer terbutaline 0.25 mg SC. Notify provider. Goal: < 5 contractions per 10 min averaged over 30 min."
    },
  ],
  "ch16": [
    {
      id: "ch16-p1",
      type: "PRIORITY",
      after: "ch16-prolapse",
      q: "Immediately after AROM, the FHR drops to 80 bpm with severe variable decelerations. First action?",
      a: "Suspect umbilical cord prolapse. Perform a sterile vaginal exam — if cord is palpable, manually elevate the presenting part OFF the cord (do NOT remove hand) and call for help. Place client in knee-chest or Trendelenburg position. Prepare for emergent cesarean. Administer O₂."
    },
    {
      id: "ch16-p2",
      type: "JUDGMENT",
      after: "ch16-dystocia",
      q: "Postpartum hemorrhage from a boggy uterus. Priority intervention sequence?",
      a: "1) FUNDAL MASSAGE first — firming the uterus stops atonic bleeding. 2) Empty bladder (insert catheter). 3) IV oxytocin (first-line uterotonic). 4) Methylergonovine 0.2 mg IM (avoid if hypertensive). 5) Misoprostol 800–1000 mcg PR. 6) Carboprost 0.25 mg IM (avoid in asthma). 7) Bimanual compression. 8) OR for surgical management if refractory."
    },
  ],
  "ch17": [
    {
      id: "ch17-p1",
      type: "CONTENT",
      after: "ch17-lochia",
      q: "How long does lochia rubra typically last, and what comes next?",
      a: "Lochia rubra: days 1–3 postpartum, dark red. Lochia serosa: days 4–10, pinkish-brown. Lochia alba: days 11–14 (up to 6 weeks), yellowish-white. Saturating a pad in 15 minutes at any stage = excessive."
    },
    {
      id: "ch17-p2",
      type: "JUDGMENT",
      after: "ch17-uterus",
      q: "At 24 hours postpartum, the fundus is 2 cm above the umbilicus and deviated to the right. Interpretation and action?",
      a: "Bladder distention is displacing the uterus. Have client void (or catheterize if unable). Recheck fundus position after voiding. Expected at 24 hr: fundus at or 1 cm below umbilicus, midline. Full bladder is the #1 cause of fundal displacement and a major cause of uterine atony."
    },
  ],
  "ch18": [
    {
      id: "ch18-p1",
      type: "CONTENT",
      after: "ch18-maternal-phases",
      q: "Describe the 'taking-in' phase of maternal postpartum adjustment.",
      a: "First 24–48 hours postpartum. Mother is DEPENDENT and PASSIVE, focused on her own physical needs (sleep, food, comfort). She frequently talks about the birth experience to integrate it. May appear disinterested in newborn — this is NORMAL. Allow recovery before pushing teaching."
    },
    {
      id: "ch18-p2",
      type: "JUDGMENT",
      after: "ch18-maternal-phases",
      q: "A client at 3 days postpartum makes critical comments about her newborn's appearance ('his head looks so cone-shaped'). What phase is she in?",
      a: "TAKING-HOLD phase (day 2–3 onward, lasts 10 days to weeks). Mother is regaining control, learning newborn care, may be critical of self and infant. Normal — provide positive reinforcement, gentle education, and reassurance about normal newborn features (molding, milia, lanugo)."
    },
  ],
  "ch19": [
    {
      id: "ch19-p1",
      type: "PRIORITY",
      after: "ch19-perineal-breast",
      q: "A breastfeeding mother at day 4 develops breast engorgement. Teaching priority?",
      a: "Continue or INCREASE breastfeeding frequency (engorgement resolves with effective drainage). Ensure proper latch. WARM compresses BEFORE feeding (facilitate let-down). COOL compresses AFTER feeding (reduce inflammation). Hand-express small amount if too engorged for baby to latch. NO routine pumping (overstimulates supply)."
    },
    {
      id: "ch19-p2",
      type: "CONTENT",
      after: "ch19-redflags",
      q: "Standard postpartum follow-up appointment timing after vaginal vs cesarean birth?",
      a: "Vaginal: 4–6 weeks postpartum. Cesarean: 2 weeks (incision check). Earlier if complications (e.g., BP recheck within 1 week if hypertensive disorder of pregnancy)."
    },
  ],
  "ch20": [
    {
      id: "ch20-p1",
      type: "PRIORITY",
      after: "ch20-hemorrhage-meds",
      q: "Thirty minutes postpartum, BP is 90/50, pulse 122, fundus boggy. First action?",
      a: "FUNDAL MASSAGE first to firm the uterus. Then notify provider, ensure 2 large-bore IVs running, administer oxytocin per protocol, monitor lochia (saturating pad in 15 min = severe hemorrhage), prepare second-line uterotonics. Rising pulse + falling BP = early hypovolemic shock."
    },
    {
      id: "ch20-p2",
      type: "JUDGMENT",
      after: "ch20-hemorrhage-meds",
      q: "Uterine atony unresponsive to oxytocin. Next medication AND key contraindication?",
      a: "Methylergonovine (Methergine) 0.2 mg IM — but CONTRAINDICATED in hypertension (causes vasoconstriction → severe HTN, stroke). If hypertensive, skip to misoprostol PR or carboprost (Hemabate) IM — but carboprost is CONTRAINDICATED in asthma (bronchospasm)."
    },
  ],
  "ch21": [
    {
      id: "ch21-p1",
      type: "CONTENT",
      after: "ch21-endometritis",
      q: "On what postpartum day does endometritis typically present, and what are the key findings?",
      a: "Day 3–4 postpartum. Findings: temperature ≥ 38°C (100.4°F) on 2 separate occasions, lower abdominal/uterine tenderness, FOUL-SMELLING dark/profuse lochia, elevated WBC, tachycardia. Treatment: IV broad-spectrum antibiotics until afebrile × 48 hours."
    },
    {
      id: "ch21-p2",
      type: "JUDGMENT",
      after: "ch21-mastitis",
      q: "A breastfeeding mother develops mastitis. Guidance regarding breastfeeding?",
      a: "CONTINUE breastfeeding — start on AFFECTED side first (helps drain the breast). Antibiotics safe in lactation (dicloxacillin, cephalexin). Fluids 3,000 mL/day. NO underwire bras. Warm compress before feeding. If abscess forms, incision and drainage; can resume BF on affected side post-drainage."
    },
  ],
  "ch22": [
    {
      id: "ch22-p1",
      type: "PRINCIPLE",
      after: "ch22-psychosis",
      q: "How does postpartum psychosis differ from postpartum depression?",
      a: "PSYCHOSIS (rare, 1–2/1000): onset 2–3 weeks postpartum, involves HALLUCINATIONS, DELUSIONS, PARANOIA, often with bipolar history, HIGH risk of harm to self/infant. Requires hospitalization. DEPRESSION (10–15%): within first year, persistent sadness, hopelessness, NO break with reality. Outpatient treatment with SSRIs and therapy."
    },
    {
      id: "ch22-p2",
      type: "PRIORITY",
      after: "ch22-care",
      q: "A postpartum mother quietly says 'I sometimes think about hurting my baby.' First action?",
      a: "Take this seriously — directly assess for specific plan, means, and timing. Do NOT leave her alone with the infant. Ensure infant safety, contact provider immediately, arrange psychiatric evaluation. This is a safety emergency. Stay calm, non-judgmental, document statement verbatim."
    },
  ],
  "ch23": [
    {
      id: "ch23-p1",
      type: "CONTENT",
      after: "ch23-apgar",
      q: "An Apgar score of 5 at 1 minute indicates what level of distress?",
      a: "MODERATE distress (4–6). Scoring: 0–3 = severe distress, 4–6 = moderate difficulty, 7–10 = minimal/no difficulty. Assessed at 1 minute and 5 minutes after birth. 5-minute score is more predictive of outcome."
    },
    {
      id: "ch23-p2",
      type: "JUDGMENT",
      after: "ch23-physical",
      q: "Distinguishing feature between caput succedaneum and cephalohematoma?",
      a: "Caput succedaneum CROSSES suture lines (scalp edema from pressure of vaginal birth); resolves in 3–4 days. Cephalohematoma does NOT cross suture lines (blood between periosteum and skull); resolves in 2–8 weeks. Cephalohematoma carries higher hyperbilirubinemia risk from RBC breakdown."
    },
  ],
  "ch24": [
    {
      id: "ch24-p1",
      type: "PRIORITY",
      after: "ch24-resp-id-thermo",
      q: "A newborn has audible mucus, becomes choking with color change. First action?",
      a: "SUCTION MOUTH FIRST, THEN nose with bulb syringe. Compress bulb BEFORE insertion (avoid blowing fluid down). Avoid center of mouth (stimulates gag reflex). Position on side to facilitate drainage. If unsuccessful, mechanical suction. Mouth-before-nose prevents aspiration when nose suction triggers a gasp."
    },
    {
      id: "ch24-p2",
      type: "CONTENT",
      after: "ch24-resp-id-thermo",
      q: "Newborn axillary temperature ranges — what threshold defines hypothermia?",
      a: "Normal: 36.5–37.5°C (97.7–99.5°F). HYPOTHERMIA: < 36.5°C (97.7°F). Goal core temp: 36.5–37°C (97.7–98.6°F). Best intervention: early skin-to-skin contact with parent. If unstable: radiant warmer set to maintain skin temp 36.5°C."
    },
  ],
  "ch25": [
    {
      id: "ch25-p1",
      type: "JUDGMENT",
      after: "ch25-breastfeeding",
      q: "A breastfeeding mother questions whether her milk supply is adequate. Her 1-week-old has 8 wet diapers/24 hr. Reassurance?",
      a: "Adequate hydration. Indicators of effective BF: ≥ 6 wet diapers/24 hr after day 4 (8 is excellent), ≥ 3 stools/day (yellow, seedy) for first month, weight gain ≥ 110 g/week (after initial 5–10% loss regained by 10–14 days), audible swallowing during feeds, content between feedings."
    },
    {
      id: "ch25-p2",
      type: "CONTENT",
      after: "ch25-milk-storage",
      q: "Breast milk storage durations — room temp, refrigerator, freezer, deep freezer?",
      a: "Room temperature: 8 hours. Refrigerator (sterile container): 8 days. Freezer compartment of refrigerator: 6 months. Deep freezer: 12 months. NEVER microwave thaw (destroys immunoglobulins, creates hot spots). Do NOT refreeze thawed milk. Discard unused portion after warming."
    },
  ],
  "ch26": [
    {
      id: "ch26-p1",
      type: "PRIORITY",
      after: "ch26-checkups-illness",
      q: "Parents ask when to introduce solid foods. Best response?",
      a: "NOT before 6 months of age (per AAP). Earlier introduction increases risk of food allergies and obesity; the digestive enzymes and swallow-coordination aren't fully developed before 6 mo. Exclusive breastfeeding (or formula) recommended until 6 months."
    },
    {
      id: "ch26-p2",
      type: "CONTENT",
      after: "ch26-cord-circ",
      q: "When should the umbilical cord typically fall off, and what bathing restriction applies?",
      a: "Cord falls off at about 10–14 days after birth. Until then: SPONGE BATHS ONLY (no immersion in tub). Keep cord dry, fold diaper away from cord, no gauze cover, no peroxide/alcohol. Notify provider if odor, drainage, or redness around cord base."
    },
  ],
  "ch27": [
    {
      id: "ch27-p1",
      type: "PRIORITY",
      after: "ch27-hypoglycemia",
      q: "A newborn at 3 hours of life has a blood glucose of 35 mg/dL and is jittery. Action?",
      a: "Healthy term newborns tolerate ≥ 30 mg/dL in the first 2 hours, but at 3 hours with symptoms, this is hypoglycemia requiring intervention. Initiate early feeding (breast or formula) if stable. If unstable or unable to feed, IV glucose. Recheck glucose in 30 minutes. Skin-to-skin promotes thermoregulation and BF. Intervene at < 40–45 mg/dL after the first 2 hours."
    },
    {
      id: "ch27-p2",
      type: "JUDGMENT",
      after: "ch27-substance-withdrawal",
      q: "Name three CNS findings of Neonatal Abstinence Syndrome (NAS).",
      a: "High-pitched shrill cry · incessant crying · irritability · tremors · hyperactivity with INCREASED Moro reflex · increased DTRs · increased muscle tone (hypertonicity) · disturbed sleep pattern · convulsions. NAS scoring system covers three clusters: CNS, metabolic/vasomotor/respiratory, and GI."
    },
  ],
};
```

---

### 7.25 Cross-Link Map (Book ↔ Templates)

> *Consolidated from former Addendum C.1.*

This is the real MN map. Every chapter's `tpl-bridge` points to these templates.

#### C.1.1 Full bridge map (all 27 MN chapters)

```
ch1   Contraception
   → ex-ch1-cocs              Combined Oral Contraceptives (Medication)
   → ex-ch1-vasectomy         Vasectomy (Therapeutic Procedure)

ch2   Infertility
   → ex-ch2-hsg               Hysterosalpingography (Diagnostic Procedure)
   → ex-ch2-infertility       Infertility (System Disorder)

ch3   Expected Physiological Changes
   → ex-ch3-skin-breast       Skin & Breast Changes (System Disorder)

ch4   Routine Antepartum Care
   → ex-ch4-uti               UTI Prevention During Pregnancy (Basic Concept)

ch5   Nutrition in Pregnancy
   → ex-ch5-nutrition         Inadequate Nutrition Risk Factors (System Disorder)

ch6   Antepartum Diagnostic Testing  (most cross-linked chapter)
   → ex-ch6-nst               Nonstress Test (Diagnostic Procedure)
   → ex-ch6-bpp               Biophysical Profile (Diagnostic Procedure)
   → ex-ch6-ultrasound        Ultrasound — Abdominal & Transvaginal (Diagnostic Procedure)
   → ex-ch6-amnio             Amniocentesis (Diagnostic Procedure)
   → ex-tissue-perfusion      Tissue Perfusion · Fetal Oxygenation (Concept Analysis)

ch7   Bleeding During Pregnancy  (heavy clinical content)
   → ex-ch7-methotrexate      Methotrexate (Medication)
   → ex-ch7-betamethasone     Betamethasone (Medication)
   → ex-ch7-rhogam            Rho(D) Immune Globulin (Medication)
   → ex-ch7-placenta-previa   Placenta Previa (System Disorder)
   → ex-ch7-abruption         Abruptio Placentae (System Disorder)
   → ex-ch7-spontaneous-ab    Spontaneous Abortion (System Disorder)
   → ex-ch7-ectopic           Ectopic Pregnancy (System Disorder)
   → ex-ch7-gtd               Gestational Trophoblastic Disease (System Disorder)
   → ex-ch7-vasa-previa       Vasa Previa (System Disorder)
   → ex-ch7-dc                Dilation & Curettage (Therapeutic Procedure)

ch8   Infections During Pregnancy
   → ex-ch8-gbs               Group B Streptococcus Prophylaxis (System Disorder)
   → ex-ch8-penicillin        Penicillin G (Medication)

ch9   Medical Conditions in Pregnancy
   → ex-ch9-magsulfate        Magnesium Sulfate (Medication)
   → ex-ch9-nifedipine        Nifedipine (Medication)
   → ex-ch9-cerclage          Cervical Cerclage (Therapeutic Procedure)
   → ex-ch9-gdm               Gestational Diabetes Mellitus (System Disorder)
   → ex-ch9-preeclampsia      Preeclampsia / Eclampsia (System Disorder)
   → ex-ch9-hellp             HELLP Syndrome (System Disorder)
   → ex-ch9-hyperemesis       Hyperemesis Gravidarum (System Disorder)
   → ex-ch9-gestational-htn   Gestational Hypertension (System Disorder)

ch10  Preterm Labor
   → ex-ch10-preterm-labor    Preterm Labor (System Disorder)
   → ex-ch10-pprom            Preterm PROM (System Disorder)
   → ex-ch10-terbutaline      Terbutaline (Medication)

ch11  Intrapartum Care
   → ex-ch11-vagexam          Vaginal Examination Intrapartum (Nursing Skill)
   → ex-ch11-oxytocin         Oxytocin / Pitocin (Medication)
   → ex-ch11-misoprostol      Misoprostol / Cytotec (Medication)
   → ex-ch11-amniotomy        Amniotomy / AROM (Therapeutic Procedure)

ch12  Pain Management
   → ex-ch12-nonpharm-pain    Nonpharmacological Pain Management (Basic Concept)
   → ex-ch12-epidural         Epidural Block (Therapeutic Procedure)
   → ex-ch12-butorphanol      Butorphanol / Stadol (Medication)

ch13  Fetal Assessment During Labor
   → ex-ch13-leopold          Leopold Maneuvers (Nursing Skill)
   → ex-ch13-internal-monitor Internal Fetal Monitoring (Therapeutic Procedure)
   → ex-ch13-decels           FHR Deceleration Patterns (Basic Concept)

ch14  Nursing Care During Stages of Labor
   → ex-ch14-fourth-stage     Fourth Stage of Labor Care (Basic Concept)
   → ex-ch14-fundal-massage   Fundal Massage (Nursing Skill)

ch15  Complications During Labor & Birth
   → ex-ch15-cesarean         Cesarean Birth (Therapeutic Procedure)
   → ex-ch15-forceps          Forceps-Assisted Birth (Therapeutic Procedure)
   → ex-ch15-vacuum           Vacuum-Assisted Birth (Therapeutic Procedure)

ch16  Postpartum Complications
   → ex-ch16-meconium         Meconium-Stained Fluid (Basic Concept)
   → ex-ch16-pph              Postpartum Hemorrhage (System Disorder)
   → ex-ch16-shoulder-dystocia Shoulder Dystocia (System Disorder)
   → ex-ch16-cord-prolapse    Umbilical Cord Prolapse (System Disorder)
   → ex-ch16-uterine-rupture  Uterine Rupture (System Disorder)

ch17  Postpartum Physiological Adaptations
   → ex-ch17-perineal         Postpartum Perineal Care (Basic Concept)

ch18  Postpartum Psychosocial Adaptations
   → ex-ch18-paternal         Paternal Adaptation (Basic Concept)
   → ex-attachment            Maternal-Newborn Attachment (Concept Analysis)

ch19  Nursing Care of Postpartum Client
   → ex-ch19-discharge        Discharge Teaching (Basic Concept)

ch20  Postpartum Hemorrhage / Thromboembolism
   → ex-ch20-dvt              Postpartum DVT (System Disorder)
   → ex-ch20-pp-hematoma      Postpartum Hematomas (System Disorder)

ch21  Postpartum Infections
   → ex-ch21-endometritis     Postpartum Endometritis (System Disorder)
   → ex-ch21-mastitis         Lactational Mastitis (System Disorder)

ch22  Postpartum Mood Disorders
   → ex-ch22-depression       Postpartum Depression (Basic Concept)
   → ex-ch22-pp-psychosis     Postpartum Psychosis (System Disorder)

ch23  Newborn Assessment
   → ex-ch23-physical         Newborn Physical Development (Basic Concept)
   → ex-ch23-newborn-vs       Newborn Vital Signs (Nursing Skill)
   → ex-ch23-apgar            Apgar Score (Basic Concept)
   → ex-ch23-reflexes         Newborn Reflexes (Basic Concept)

ch24  Newborn Nursing Care  (heavy nursing skill content)
   → ex-ch24-bulb             Bulb Syringe Use (Basic Concept)
   → ex-ch24-heel-stick       Newborn Heel Stick (Nursing Skill)
   → ex-ch24-vitamin-k        Vitamin K (Medication)
   → ex-ch24-erythromycin     Erythromycin Eye Ointment (Medication)
   → ex-ch24-cord-care        Umbilical Cord Care (Nursing Skill)
   → ex-ch24-circumcision     Circumcision Care (Nursing Skill)

ch25  Breastfeeding
   → ex-ch25-pump             Breast Pump & Milk Storage (Basic Concept)
   → ex-ch25-latch            Breastfeeding Latch (Nursing Skill)

ch26  Bottle Feeding & Newborn Hygiene
   → ex-ch26-bathing          Newborn Bathing (Basic Concept)

ch27  Newborn Complications
   → ex-ch27-hyperbili        Hyperbilirubinemia (System Disorder)
   → ex-ch27-rds              Respiratory Distress Syndrome (System Disorder)
   → ex-ch27-hypoglycemia     Neonatal Hypoglycemia (System Disorder)
   → ex-ch27-nas              Neonatal Abstinence Syndrome (System Disorder)
   → ex-ch27-phototherapy     Phototherapy (Therapeutic Procedure)
   → ex-ch27-ttn              Transient Tachypnea of Newborn (System Disorder)
   → ex-ch27-mas              Meconium Aspiration Syndrome (System Disorder)
```

#### C.1.2 Template type distribution by chapter

```
Chapter heavy in:    Best paired with:
─────────────────    ──────────────────────
ch6  diagnostic      → DP type templates
ch7  bleeding        → SD + MED templates
ch9  medical conds   → SD + MED templates
ch10 preterm         → SD + MED templates
ch16 PP complications → SD templates
ch24 newborn care    → NS + MED templates
ch27 newborn compl.  → SD + TP templates
```

#### C.1.3 Templates that bridge to multiple chapters

In MN, templates currently bridge to exactly one chapter each (the chapter the source PDF associated them with). If you'd like to bridge a template to multiple chapters:

**Pattern:** add the template's link to each chapter's `tpl-bridge` section. The template itself lives once in the Templates file under whichever type fits.

**Example use case:** "Cesarean Birth" template might logically bridge to ch15 (Complications During Labor) AND ch16 (Postpartum Complications). Currently bridges only to ch15.

#### C.1.4 Cross-link verification snippet

```python
"""Verify every tpl-bridge link in Book resolves to a template in Templates."""
import re
from pathlib import Path

book = Path('Elevated ATI MN Book.html').read_text()
templates = Path('Elevated ATI MN Templates.html').read_text()

# All template IDs in Templates file
tpl_ids = set(re.findall(r'<article class="example-card" id="(ex-[^"]+)"', templates))
print(f"Templates has {len(tpl_ids)} example cards")

# All Book tpl-bridge link targets
bridge_links = re.findall(r'Templates\.html#(ex-[^"]+)"', book)
unique_bridge = set(bridge_links)
print(f"Book has {len(bridge_links)} bridge links to {len(unique_bridge)} unique templates")

# Missing
missing = unique_bridge - tpl_ids
if missing:
    print(f"\n✗ Book references {len(missing)} non-existent templates:")
    for m in sorted(missing):
        print(f"   {m}")
else:
    print("\n✓ All bridge links resolve")

# Orphaned
orphaned = tpl_ids - unique_bridge
if orphaned:
    print(f"\nℹ {len(orphaned)} templates not referenced by any chapter:")
    for o in sorted(orphaned):
        print(f"   {o}")
```

---

### 7.26 Procedure — Add A New Abbreviation

> *Consolidated from former Addendum F.3.*

Use case: a new term appears in extracted content that should auto-tooltip.

#### F.3.1 Steps

1. Open Book file
2. Find `const ABBR_DICT = {`
3. Add entry in the appropriate alphabetical/categorical position:
   ```javascript
   "ACRONYM": "Full Term Expansion",
   ```
4. Make sure entry doesn't conflict with shorter substrings (e.g., adding "PT" might break "PTT" matching)
5. The `autoWrapAbbreviations()` function sorts keys by length descending so longer matches win — no manual ordering needed
6. Refresh Book — new abbreviation should auto-tooltip

#### F.3.2 Subject-specific dictionaries

Pharm has terms MN doesn't (e.g., "MAOI", "SSRI", "NSAID"). PD has terms specific to peds (e.g., "RSV", "FTT", "ADHD").

**Pattern options:**
- **Option A: Single shared ABBR_DICT** — every Book file has the same dictionary. Simpler but bloated.
- **Option B: Per-subject ABBR_DICT** — each Book file's dictionary has subject-specific terms. Currently used.

Currently each Book file has its own `const ABBR_DICT`. To add a term that should appear in ALL subjects, add it to ALL files.

#### F.3.3 Test after adding

```javascript
// In browser console on the Book page:
ABBR_DICT["NEW_ACRONYM"]    // Should return the definition
// Then visually: search content for that acronym, hover/tap to see tooltip
```

---

---

## PART 8 — TEMPLATES FILE

The Templates file mirrors Book in structure: same sidebar pattern, same theme system, same abbr tooltips. But content is organized by template **type**, not by chapter.

### 8.1 Document structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#d97706">
  <title>Elevated · ATI Maternal-Newborn Templates</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>/* ~30 KB of CSS */</style>
</head>
<body>
  <button class="sidebar-toggle" id="sidebarToggle">☰</button>
  <a class="back-home-mobile" href="Elevated%20ATI%20MN%20Hub.html">← Back to Hub</a>
  <div class="sidebar-overlay" id="sidebarOverlay"></div>

  <div class="layout">
    <aside class="sidebar" id="sidebar">
      <!-- Same header pattern as Book -->
      <div class="sidebar-header">
        <a class="back-home" href="Elevated%20ATI%20MN%20Hub.html">Back to Hub</a>
        <div class="sb-course">NUR 2460 · ATI</div>
        <div class="sb-title">MN Templates</div>
        <div class="sb-sub">105 worked examples · 8 types</div>
        <button id="themeToggle"><span id="themeIcon">☀️</span> <span id="themeLabel">Light Mode</span></button>
      </div>
      <div class="sidebar-search">
        <input id="searchInput" type="text" placeholder="Search templates…">
        <div id="searchResults"></div>
      </div>
      <nav class="sidebar-list">
        <!-- One nav-section per template type, each lists its examples -->
        <div class="nav-section">
          <div class="nav-section-label" data-toggle-section="bc">
            Basic Concept (14) <span class="caret">▾</span>
          </div>
          <a href="#ex-ch1-cocs" class="sidebar-item" data-example="ex-ch1-cocs">
            <span class="item-num">Ch1</span>
            <span class="item-name">Combined Oral Contraceptives</span>
          </a>
          <!-- ... -->
        </div>
        <!-- ... -->
      </nav>
    </aside>

    <main class="main-content">

      <div class="main-course">NUR 2460 · ATI Edition 11</div>
      <h1 class="main-title">MN <em>Templates</em></h1>
      <p class="main-desc">
        Worked examples for all 8 ATI Active Learning Template types.
        Each card shows a filled-in template — toggle Blank to test yourself.
      </p>

      <!-- Filter panel -->
      <div class="tpl-filter-panel">
        <div class="tpl-filter-search">
          <input id="tplFilterInput" type="text" placeholder="Filter examples…">
        </div>
        <div class="tpl-filter-chips">
          <button class="tpl-chip active" data-filter-type="all">All</button>
          <button class="tpl-chip" data-filter-type="bc">Basic Concept</button>
          <button class="tpl-chip" data-filter-type="dp">Diagnostic Procedure</button>
          <button class="tpl-chip" data-filter-type="gd">Growth & Dev</button>
          <button class="tpl-chip" data-filter-type="med">Medication</button>
          <button class="tpl-chip" data-filter-type="ns">Nursing Skill</button>
          <button class="tpl-chip" data-filter-type="sd">System Disorder</button>
          <button class="tpl-chip" data-filter-type="tp">Therapeutic Procedure</button>
          <button class="tpl-chip" data-filter-type="ca">Concept Analysis</button>
          <button class="tpl-chip-divider"></button>
          <button class="tpl-chip" data-filter-state="unread">Unread</button>
          <button class="tpl-chip" data-filter-state="studied">Studied</button>
        </div>
        <div class="tpl-filter-meta">
          <span id="tplFilterCount">105 of 105 examples</span>
          <button class="tpl-filter-clear" id="tplFilterClear">Clear filters</button>
          <button class="tpl-mode-toggle" id="tplModeToggle">Filled / <strong>Blank</strong></button>
        </div>
      </div>

      <!-- Master print -->
      <button class="compare-btn" id="masterPrintBtn">🖨️ Print Templates</button>

      <!-- 8 accordion sections, one per template type -->
      <div class="tpl-accordion" id="basic-concept-acc">
        <div class="tpl-acc-header" data-toggle="basic-concept-acc">
          <span class="acc-caret">▾</span>
          <span class="acc-name">Basic Concept</span>
          <span class="acc-count">14 examples</span>
          <button class="part-print-btn" data-print-section="basic-concept">⎙</button>
        </div>
        <div class="tpl-acc-body">
          <div class="acc-navigator">
            <h4>Examples in this type:</h4>
            <ul>
              <li><a href="#ex-ch1-cocs">Combined Oral Contraceptives</a></li>
              <!-- ... -->
            </ul>
          </div>
          <div class="example-stack" data-type-section="basic-concept">
            <!-- Cards will be moved here from template-pool at page init -->
          </div>
        </div>
      </div>
      <!-- ... 7 more accordions ... -->

      <!-- TEMPLATE POOL — hidden source of example cards -->
      <div class="template-pool" id="templatePool" style="display:none">
        <section class="template-section" data-section="basic-concept">
          <header class="template-banner">
            <h2>ATI Active Learning Template: Basic Concept</h2>
            <p>14 worked examples across the MN textbook</p>
          </header>
          <div class="template-body">
            <div class="example-stack">
              <article class="example-card" id="ex-ch1-cocs" data-ch="1" data-type="bc">
                <header class="ex-head">
                  <span class="ex-chip">Ch 1</span>
                  <h3 class="ex-title">Combined Oral Contraceptives (COCs)</h3>
                  <a class="ex-jump" href="Elevated%20ATI%20MN%20Book.html#ch1-hormonal">→ Read in book</a>
                  <button class="ex-expand-btn" type="button" title="Open full">⛶</button>
                </header>
                <!-- Field grid — Basic Concept template fields -->
                <div class="bc-grid">
                  <div class="bc-field">
                    <div class="bc-label">Related Content</div>
                    <div class="bc-value">
                      Hormonal contraception combining estrogen and progestin.
                      Suppresses ovulation by inhibiting LH/FSH surge.
                    </div>
                    <div class="bc-blank">_________________________________</div>
                  </div>
                  <div class="bc-field">
                    <div class="bc-label">Underlying Principles</div>
                    <div class="bc-value">...</div>
                    <div class="bc-blank">_________________________________</div>
                  </div>
                  <div class="bc-field">
                    <div class="bc-label">Nursing Interventions</div>
                    <div class="bc-value">...</div>
                    <div class="bc-blank">_________________________________</div>
                  </div>
                </div>
                <!-- Studied checkbox -->
                <footer class="ex-foot">
                  <label class="ex-studied">
                    <input type="checkbox" data-studied-id="ex-ch1-cocs"> Mark studied
                  </label>
                </footer>
              </article>
              <!-- ... 13 more bc cards ... -->
            </div>
          </div>
        </section>

        <section class="template-section" data-section="diagnostic-procedure">
          <header class="template-banner">
            <h2>ATI Active Learning Template: Diagnostic Procedure</h2>
            <p>6 worked examples</p>
          </header>
          <div class="template-body">
            <div class="example-stack">
              <article class="example-card" data-type="dp" id="ex-ch3-quad-screen">
                <!-- ... dp-grid fields ... -->
              </article>
            </div>
          </div>
        </section>
        <!-- ... all 8 sections ... -->
      </div>

      <!-- Example modal -->
      <div class="example-modal-overlay" id="exModalOverlay" aria-hidden="true">
        <div class="example-modal" id="exModal">
          <div class="example-modal-header">
            <h2 id="exModalTitle">Example</h2>
            <button class="example-modal-close" id="exModalClose">×</button>
          </div>
          <div class="example-modal-body" id="exModalBody"></div>
        </div>
      </div>

      <footer class="page-footer">
        <p>ATI RN Maternal Newborn · 11th Ed · Active Learning Templates worked examples</p>
      </footer>
    </main>
  </div>

  <span class="abbr-tip-pop" id="abbrTipPop" hidden></span>

  <script>/* Templates IIFE — see PART 11 reference */</script>
</body>
</html>
```

### 8.2 Template-pool with section wrappers

The pool MUST use `<section class="template-section" data-section="...">` wrappers around each template type's cards. This is what `bindAccordionList()` uses to find and relocate cards.

**At page init:**
```javascript
function studies() {
  // Move example cards from pool into their accordion bodies
  document.querySelectorAll('.template-section').forEach(function(section) {
    var sectionType = section.dataset.section;
    var acc = document.getElementById(sectionType + '-acc');
    if (!acc) return;
    var stack = acc.querySelector('.example-stack[data-type-section="' + sectionType + '"]');
    if (!stack) return;
    section.querySelectorAll('.example-card').forEach(function(card) {
      stack.appendChild(card);   // moves (not copies — only 1 instance exists)
    });
    // Update count
    var count = stack.querySelectorAll('.example-card').length;
    var countEl = acc.querySelector('.acc-count');
    if (countEl) countEl.textContent = count + ' example' + (count === 1 ? '' : 's');
  });
}
```

After this runs, the template-pool is empty of cards (they live in the accordions). Cards never duplicate.

### 8.3 The 8 template types

| Type | data-section | Field grid class | MN count | PD count |
|---|---|---|---|---|
| Basic Concept | `basic-concept` | `.bc-grid` | 14 | 12 |
| Diagnostic Procedure | `diagnostic-procedure` | `.dp-grid` | 6 | 4 |
| Growth & Development | `growth-development` | `.bc-grid` (uses bc-grid, NOT gd-grid) | 0 | 16 |
| Medication | `medication` | `.med-grid` | 15 | 18 |
| Nursing Skill | `nursing-skill` | `.ns-grid` | 4 | 6 |
| System Disorder | `system-disorder` | `.sd-grid` | 60 | 65 |
| Therapeutic Procedure | `therapeutic-procedure` | `.tp-grid` | 35 | 28 |
| Concept Analysis | `concept-analysis` | `.ca-grid` | 2 | 1 |

**Important correction:** Growth & Development uses `.bc-grid`, NOT `.gd-grid`. There is no `.gd-grid` class defined in MN (because MN has 0 G&D templates), but the convention from PD is to reuse `.bc-grid`.

### 8.4 Example card structure

```html
<article class="example-card" id="ex-ch3-skin-breast" data-ch="3" data-type="sd">
  <header class="ex-head">
    <span class="ex-chip">Ch 3</span>
    <h3 class="ex-title">Skin & Breast Changes</h3>
    <a class="ex-jump" href="Elevated%20ATI%20MN%20Book.html#ch3-physical">→ Read in book</a>
    <button class="ex-expand-btn" type="button" title="Open full">⛶</button>
  </header>

  <div class="sd-grid">
    <div class="sd-field"><div class="sd-label">Alterations in Health</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Pathophysiology</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Health Promotion</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Risk Factors</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Subjective Data</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Objective Data</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Lab Tests</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Diagnostic Procedures</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Nursing Care</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Medications</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Client Education</div><div class="sd-value">...</div></div>
    <div class="sd-field"><div class="sd-label">Complications</div><div class="sd-value">...</div></div>
  </div>

  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-ch3-skin-breast"> Mark studied
    </label>
  </footer>
</article>
```

**Each template type has its own grid class** with type-specific fields:
- `.bc-grid` — 3 fields: Related Content, Underlying Principles, Nursing Interventions
- `.dp-grid` — 9 fields: Description, Indications, Interpretation, etc.
- `.med-grid` — 11 fields: Class, Action, Therapeutic Use, Complications, Contraindications, etc.
- `.sd-grid` — 12 fields (System Disorder; see above)
- `.tp-grid` — 9 fields: Description, Indications, Considerations, etc.
- `.ns-grid` — 7 fields: Indications, Outcomes, Considerations, etc.
- `.ca-grid` — 4 fields: Concept Definition, Defining Characteristics, etc.

### 8.5 Filled/Blank toggle

**Per-card design (canonical, verified against MN):** Each `.example-card` has its own toggle. Mode is stored on the card via `data-mode="filled"` (default) or `data-mode="blank"`. CSS rules using the `[data-mode="blank"]` selector hide the content and show blank fields/lines. This is intentionally different from MN's Book mid-prompts (which use a global page-level toggle).

> ⚠️ **Common error**: An earlier version of this guide documented a fictional page-level `body.tpl-blank` class + single `#tplModeToggle` button. That design does NOT exist in MN. The per-card design below is the actual canonical implementation. Verified by direct inspection of `Elevated ATI MN Templates.html` (152 mode-toggle instances, 0 page-level toggle).

**HTML (one per card, placed inside the card header):**
```html
<div class="mode-toggle" role="tablist" aria-label="View mode">
  <button data-mode="filled" class="active" type="button">Filled</button>
  <button data-mode="blank" type="button">Blank</button>
</div>
```

**CSS (toggle button styling):**
```css
.mode-toggle {
  display: inline-flex;
  background: var(--surface2);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 3px;
}
.mode-toggle button {
  background: transparent;
  color: var(--text2);
  border: none;
  padding: 7px 16px;
  border-radius: 7px;
  font-family: inherit;
  font-size: 12px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.15s;
  min-width: 60px;
}
.mode-toggle button:hover { color: var(--text); }
.mode-toggle button.active { background: var(--accent); color: #fff; }
```

**CSS (blank-mode content hiding):**
```css
/* When card is in blank mode, hide content boxes and show blank lines */
.example-card[data-mode="blank"] .tp-box .content,
.example-card[data-mode="blank"] .tp-subbox .content { display: none; }

.example-card[data-mode="blank"] .tp-box,
.example-card[data-mode="blank"] .tp-subbox { min-height: 120px; }

.example-card[data-mode="blank"] .meta-value {
  display: inline-block;
  min-width: 120px;
  border-bottom: 1px dashed var(--border);
  color: transparent;
  height: 18px;
}

/* Some metadata always shows even in blank mode */
.example-card[data-mode="blank"] .meta-value.always-show {
  display: inline;
  color: var(--text);
  border-bottom: none;
}
```

**JS:**
```javascript
function bindModeToggles(scope) {
  scope.querySelectorAll('.mode-toggle').forEach(function(toggle) {
    var card = toggle.closest('.example-card');
    if (!card) return;
    toggle.querySelectorAll('button').forEach(function(btn) {
      btn.addEventListener('click', function() {
        var mode = btn.getAttribute('data-mode');
        toggle.querySelectorAll('button').forEach(function(b) { b.classList.remove('active'); });
        btn.classList.add('active');
        card.setAttribute('data-mode', mode);
      });
    });
  });
}
```

**Per-subject changes**: None to mechanism. Each card's content (in `.tp-box`, `.meta-value`, etc.) is subject-specific but the toggle works identically.

**Modifier classes to preserve** (see PART 10.4):
- `<button>` inside `.mode-toggle` carries `.active` class on the selected mode
- `<article class="example-card">` carries `data-mode="filled"` (default) or `data-mode="blank"` attribute

### 8.6 Template filter system

> ⚠️ **Earlier guide versions documented this section incorrectly** — claiming `{ type, state, query }` state shape with `.tpl-chip` and `#tplFilterCount` IDs. The actual MN implementation differs substantially. This is the verified canonical version.

**State shape** (stored as `nur2460_tpl_filters` for MN, `atipd_tpl_filters` for PD):
```javascript
var tplFilterState = {
  search: '',                  // text input
  types: [],                   // array of strings (multi-select)
  chapters: [],                // array of strings (multi-select, e.g., ['1','3','7'])
  status: 'all'                // 'all' | 'studied' | 'unstudied'
};
```

**HTML structure (the filter panel):**
```html
<div class="tpl-filter-panel" id="tplFilterPanel">
  <button class="tpl-filter-toggle" type="button" id="tplFilterToggle" aria-expanded="false">
    <span>🔍 Filter templates</span>
    <span class="tpl-filter-active-count" id="tplFilterActiveCount"></span>
    <span class="tpl-filter-chevron">▾</span>
  </button>
  <div class="tpl-filter-body" id="tplFilterBody" hidden>
    <div class="tpl-filter-row">
      <input type="text" class="tpl-filter-search" id="tplFilterSearch" placeholder="Search template name or chapter…">
    </div>
    <div class="tpl-filter-row">
      <div class="tpl-filter-label">Type</div>
      <div class="tpl-filter-chips" data-filter-group="type" data-multi="true">
        <button class="tpl-filter-chip" data-value="basic-concept" type="button">Basic Concept</button>
        <button class="tpl-filter-chip" data-value="system-disorder" type="button">System Disorder</button>
        <!-- ... 6 more type chips (one per ATI template type) -->
      </div>
    </div>
    <div class="tpl-filter-row">
      <div class="tpl-filter-label">Chapter</div>
      <div class="tpl-filter-chips tpl-filter-chips-numeric" data-filter-group="chapter" data-multi="true">
        <button class="tpl-filter-chip" data-value="1" type="button">1</button>
        <!-- ... one chip per chapter (MN=27, PD=44, Pharm=49) -->
      </div>
    </div>
    <div class="tpl-filter-row">
      <div class="tpl-filter-label">Status</div>
      <div class="tpl-filter-chips" data-filter-group="status">
        <button class="tpl-filter-chip active" data-value="all" type="button">All</button>
        <button class="tpl-filter-chip" data-value="unstudied" type="button">Unstudied</button>
        <button class="tpl-filter-chip" data-value="studied" type="button">Studied</button>
      </div>
    </div>
    <div class="tpl-filter-actions">
      <button class="tpl-filter-clear-btn" id="tplFilterClear" type="button" hidden>Clear all filters</button>
      <span class="tpl-filter-result-count" id="tplFilterResultCount"></span>
    </div>
  </div>
</div>
```

**Key DOM IDs** (all read by `applyTplFilterUI` / `applyTplFilters`):
- `#tplFilterPanel` — outer container
- `#tplFilterToggle` — collapse/expand button
- `#tplFilterActiveCount` — small badge showing count of active filters
- `#tplFilterBody` — collapsible content
- `#tplFilterSearch` — search input
- `#tplFilterClear` — "Clear all filters" button (shown only when filters active)
- `#tplFilterResultCount` — "X of Y templates match" text

**Modifier classes** (see PART 10.4):
- `.tpl-filter-chip.active` — currently-applied filter
- `.example-card.tpl-filtered-out` — card hidden by current filter (NOT `style.display:none`)
- `.template-section.tpl-section-empty` — entire section has no visible cards

**JS:**
```javascript
var TPL_FILTER_KEY = 'nur2460_tpl_filters';

function loadTplFilterState() {
  try {
    var saved = JSON.parse(localStorage.getItem(TPL_FILTER_KEY) || 'null');
    if (saved) return saved;
  } catch(e) {}
  return { search: '', types: [], chapters: [], status: 'all' };
}

function saveTplFilterState(s) {
  try { localStorage.setItem(TPL_FILTER_KEY, JSON.stringify(s)); } catch(e) {}
}

function tplCountActive() {
  var s = tplFilterState;
  var c = 0;
  if (s.search) c++;
  c += s.types.length;
  c += s.chapters.length;
  if (s.status !== 'all') c++;
  return c;
}

function applyTplFilters() {
  var q = (tplFilterState.search || '').toLowerCase().trim();
  var studied = getStudiedSet();
  var totalCount = 0, visibleCount = 0;

  document.querySelectorAll('.template-section').forEach(function(section) {
    var sectionType = section.id;
    section.classList.remove('tpl-section-empty');
    var sectionVisibleCount = 0;

    section.querySelectorAll('.example-card').forEach(function(card) {
      totalCount++;
      var cardId = card.id || '';
      var name = (card.querySelector('.example-name') || {}).textContent || '';
      var source = (card.querySelector('.example-source') || {}).textContent || '';
      var chMatch = source.match(/Ch\s*(\d+)/i);
      var chNum = chMatch ? chMatch[1] : '';

      var visible = true;
      if (q) {
        var hay = (name + ' ' + source).toLowerCase();
        if (hay.indexOf(q) === -1) visible = false;
      }
      if (visible && tplFilterState.types.length > 0) {
        if (tplFilterState.types.indexOf(sectionType) === -1) visible = false;
      }
      if (visible && tplFilterState.chapters.length > 0) {
        if (tplFilterState.chapters.indexOf(chNum) === -1) visible = false;
      }
      if (visible && tplFilterState.status !== 'all') {
        var isStudied = studied.has(cardId);
        if (tplFilterState.status === 'studied' && !isStudied) visible = false;
        if (tplFilterState.status === 'unstudied' && isStudied) visible = false;
      }

      card.classList.toggle('tpl-filtered-out', !visible);
      if (visible) { visibleCount++; sectionVisibleCount++; }
    });

    if (sectionVisibleCount === 0 && tplCountActive() > 0) {
      section.classList.add('tpl-section-empty');
    }
  });

  var countEl = document.getElementById('tplFilterResultCount');
  if (countEl) {
    if (tplCountActive() > 0) {
      countEl.innerHTML = '<strong>' + visibleCount + '</strong> of <strong>' + totalCount + '</strong> templates match';
    } else {
      countEl.innerHTML = '<strong>' + totalCount + '</strong> total templates';
    }
  }

  var active = tplCountActive();
  var badge = document.getElementById('tplFilterActiveCount');
  if (badge) badge.textContent = active > 0 ? active : '';
  var clearBtn = document.getElementById('tplFilterClear');
  if (clearBtn) clearBtn.hidden = (active === 0);
}

function applyTplFilterUI() {
  document.querySelectorAll('.tpl-filter-chips').forEach(function(group) {
    var groupName = group.getAttribute('data-filter-group');
    group.querySelectorAll('.tpl-filter-chip').forEach(function(chip) {
      var val = chip.getAttribute('data-value');
      var active = false;
      if (groupName === 'status')   active = (tplFilterState.status === val);
      else if (groupName === 'type')    active = tplFilterState.types.indexOf(val) !== -1;
      else if (groupName === 'chapter') active = tplFilterState.chapters.indexOf(val) !== -1;
      chip.classList.toggle('active', active);
    });
  });
  var searchInput = document.getElementById('tplFilterSearch');
  if (searchInput) searchInput.value = tplFilterState.search;
}
```

**Per-subject changes:**
- `TPL_FILTER_KEY` constant → subject namespace (MN: `nur2460_tpl_filters`, PD: `atipd_tpl_filters`)
- Chapter chip count in filter panel = subject's chapter count (MN=27, PD=44, Pharm=49)
- All 8 type chips stay the same (the 8 ATI template types are universal)

### 8.7 Example modal

```javascript
function openExampleModal(cardEl) {
  var overlay = document.getElementById('exModalOverlay');
  var modal = document.getElementById('exModal');
  var title = document.getElementById('exModalTitle');
  var body = document.getElementById('exModalBody');

  var titleEl = cardEl.querySelector('.ex-title');
  title.textContent = titleEl ? titleEl.textContent : 'Example';

  body.innerHTML = '';
  var clone = cardEl.cloneNode(true);
  // Strip the expand button (no point in modal)
  var expand = clone.querySelector('.ex-expand-btn');
  if (expand) expand.remove();
  body.appendChild(clone);

  // Wire abbrs in cloned content
  bindAbbrs(body);

  overlay.classList.add('show');
  overlay.setAttribute('aria-hidden', 'false');
  document.body.classList.add('modal-open');
}

function closeExampleModal() {
  var overlay = document.getElementById('exModalOverlay');
  overlay.classList.remove('show');
  overlay.setAttribute('aria-hidden', 'true');
  document.body.classList.remove('modal-open');
}

document.querySelectorAll('.ex-expand-btn').forEach(function(btn) {
  btn.addEventListener('click', function(e) {
    e.stopPropagation();
    var card = btn.closest('.example-card');
    openExampleModal(card);
  });
});
document.getElementById('exModalClose').addEventListener('click', closeExampleModal);
document.getElementById('exModalOverlay').addEventListener('click', function(e) {
  if (e.target === this) closeExampleModal();
});
```

### 8.8 Per-template and master print

```javascript
function injectPrintButtons() {
  document.querySelectorAll('.part-print-btn[data-print-section]').forEach(function(btn) {
    btn.addEventListener('click', function(e) {
      e.stopPropagation();
      printOneTemplate(btn.dataset.printSection);
    });
  });
  document.getElementById('masterPrintBtn').addEventListener('click', function() {
    openPrintOverlay('all');
  });
}

function printOneTemplate(sectionType) {
  var section = document.getElementById(sectionType + '-acc');
  if (!section) return;
  openPrintOverlay(sectionType);
}
```

### 8.9 Navigator list per accordion

> ⚠️ **Earlier guide versions documented this incorrectly** — claiming a `.acc-navigator ul > li > a` structure built by `buildAccNavigators()`. The actual MN implementation uses `.example-list-item` rows built by an init-time loop. This is the verified canonical version.

**What it is:** At the top of each accordion's body, a clickable bullet-list of every worked example in that template type. Clicking a list item opens that example in the modal.

**HTML (built dynamically at init; lives in `.unit-body` of each `.unit-accordion`):**
```html
<div class="example-list">
  <div class="example-list-header">
    Worked Examples · 14 <span class="example-list-hint">tap to open</span>
  </div>
  <div class="example-list-item" data-target="basic-concept-ex-0">
    <span class="example-bullet"></span>
    <span class="example-list-item-name">Combined Oral Contraceptives</span>
    <span class="example-list-item-status" data-status-icon="basic-concept-ex-0"></span>
  </div>
  <!-- ... one .example-list-item per example-card in this template type -->
</div>
```

**Initialization** (the actual pool→accordion population logic):
```javascript
// At init:
var pool = document.getElementById('templatePool');
document.querySelectorAll('.unit-accordion[data-template-id]').forEach(function(acc) {
  var templateId = acc.getAttribute('data-template-id');
  var template = pool.querySelector('#' + templateId);
  var body = acc.querySelector('.unit-body');
  if (!template || !body) return;

  var examples = template.querySelectorAll('.example-card');
  var placeholder = template.querySelector('.placeholder-card');

  if (examples.length > 0) {
    // Build bullet list navigator
    var listHtml = '<div class="example-list">';
    listHtml += '<div class="example-list-header">Worked Examples · ' + examples.length +
                ' <span class="example-list-hint">tap to open</span></div>';
    var exampleIds = [];
    examples.forEach(function(card, i) {
      var nameSpan = card.querySelector('.example-name');
      var name = nameSpan ? nameSpan.textContent.trim() : ('Example ' + (i + 1));
      var tabId = templateId + '-ex-' + i;
      exampleIds.push(tabId);
      listHtml += '<div class="example-list-item" data-target="' + tabId + '">';
      listHtml +=   '<span class="example-bullet"></span>';
      listHtml +=   '<span class="example-list-item-name">' + name + '</span>';
      listHtml +=   '<span class="example-list-item-status" data-status-icon="' + tabId + '"></span>';
      listHtml += '</div>';

      // Move the card from pool into this accordion's body
      card.classList.add('tab-panel');
      card.setAttribute('data-tab-id', tabId);
      // ... per-example checkbox injection happens here too (see 8.10)
    });
    listHtml += '</div>';
    body.innerHTML = listHtml;
    examples.forEach(function(card) { body.appendChild(card); });

    bindAccordionList(acc);
  }
});

function bindAccordionList(acc) {
  var items = acc.querySelectorAll('.unit-body .example-list-item');
  items.forEach(function(item) {
    item.addEventListener('click', function() {
      var targetId = item.getAttribute('data-target');
      items.forEach(function(i) { i.classList.remove('active'); });
      item.classList.add('active');
      openExampleModal(targetId);
    });
  });
}
```

**Key concepts:**
- The `templatePool` div holds hidden template structures (one per template type, identified by `[data-template-id]` matching `unit-accordion[data-template-id]`)
- At init, cards are MOVED (not cloned) from pool to their accordion's `.unit-body`
- Each card gets `data-tab-id="<templateId>-ex-<index>"` for modal lookup
- The list-items use `data-target` attribute that matches a card's `data-tab-id`
- `bindAccordionList()` wires click handlers; click opens `openExampleModal(targetId)`
- Note: the MN function does NOT use `acc-navigator`, `ex-title`, or `ul/li` — those were a guide error

**Modifier classes** (see PART 10.4):
- `.unit-accordion.collapsed` — default state for each accordion
- `.example-list-item.active` — last-clicked item (visual highlight)
- `.example-card.tab-panel` — added at init; signals "this card lives in an accordion now"

**Per-subject changes:** None to mechanism. Card counts per accordion type vary by subject.

### 8.10 Per-example studied checkboxes

Stored in `nur2460_atimnTemplates_progress` (note: camelCase `atimnTemplates`, not `ati_mn_templates`):
```javascript
function bindStudiedCheckboxes() {
  document.querySelectorAll('[data-studied-id]').forEach(function(cb) {
    var studied = getStudiedSet();
    cb.checked = !!studied[cb.dataset.studiedId];
    cb.addEventListener('change', function() {
      var s = getStudiedSet();
      if (cb.checked) s[cb.dataset.studiedId] = true;
      else delete s[cb.dataset.studiedId];
      localStorage.setItem('nur2460_atimnTemplates_progress', JSON.stringify(s));
      updateTemplateProgress();
      applyTplFilters();
    });
  });
}

function updateTemplateProgress() {
  // Used by Hub pickup panel + Templates header progress bar
  var s = getStudiedSet();
  var count = Object.keys(s).length;
  var total = document.querySelectorAll('.example-card').length;
  // Update UI
}
```

### 8.11 Full Templates function catalog (41 functions)

```
1.  studies                       Move cards from pool into accordions
2.  applyThemeUI                  Sync theme icon/label
3.  openSidebarPanel              Open sidebar on mobile
4.  closeSidebarPanel             Close sidebar on mobile
5.  showTip                       Position abbr tooltip
6.  bindAbbrs                     Wire abbr tooltip events
7.  bindModeToggles               Wire Filled/Blank toggle
8.  loadProgress                  Parse template progress
9.  saveProgress                  Save template progress
10. applyCheckState               Set check class
11. updateTemplateProgress        Recompute count + bar
12. updateAllTemplateProgress     Loop all sections
13. bindAccordionList             Build navigator lists
14. autoWrapAbbreviations         Wrap abbrs in text
15. initProgress                  Restore state at load
16. returnCardToAccordion         (Used by example modal — reattach card)
17. openExampleModal              Clone card into modal
18. closeExampleModal             Hide modal
19. cleanup                       Remove abbr tooltip listeners
20. escapeHtml                    Escape HTML
21. escapeRegExp                  Escape regex
22. clearSearchHighlights         Remove search marks
23. highlightInContainer          Add search marks
24. handleSearch                  Live-search dropdown
25. buildPrintContent             Build print payload
26. openPrintOverlay              Show print UI
27. render                        Rerender filtered list
28. closePrintOverlay             Hide print UI
29. handleHashNavigation          Scroll to #ex-id on load
30. highlightSidebarExample       Mark active sidebar item
31. loadTplFilterState            Parse filter state
32. saveTplFilterState            Save filter state
33. getStudiedSet                 Parse template progress
34. tplCountActive                Count chips active
35. applyTplFilters               Hide/show cards
36. applyTplFilterUI              Sync chip active states
37. initTplFilters                Wire filter controls
38. recordLastTemplate            Save last template viewed
39. handleHashFocus               Scroll & flash on hash change
40. injectPrintButtons            Wire per-section + master print
41. printOneTemplate              Open print overlay for one section
```

### 8.12 Reference templates — one per template type

> Pasteable scaffolds for the 8 ATI template types. Each shows the canonical structure of one worked-example card per type.

Each template type has a specific field grid. Below are reference cards with the canonical fields for each type.

#### D.2.1 Basic Concept (`.bc-grid` — 3 fields)

```html
<article class="example-card" id="ex-chN-[name]" data-ch="N" data-type="bc">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Concept Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn" type="button" title="Open full">⛶</button>
  </header>
  <div class="bc-grid">
    <div class="bc-field">
      <div class="bc-label">Related Content</div>
      <div class="bc-value">[Concept definition, mechanism, or contextual information.]</div>
      <div class="bc-blank">_________________________________</div>
    </div>
    <div class="bc-field">
      <div class="bc-label">Underlying Principles</div>
      <div class="bc-value">[The "why" — physiologic or pharmacologic basis.]</div>
      <div class="bc-blank">_________________________________</div>
    </div>
    <div class="bc-field">
      <div class="bc-label">Nursing Interventions</div>
      <div class="bc-value">[3-6 imperative actions, bullet-format if appropriate.]</div>
      <div class="bc-blank">_________________________________</div>
    </div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[name]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.2 Diagnostic Procedure (`.dp-grid` — 9 fields)

```html
<article class="example-card" id="ex-chN-[name]" data-ch="N" data-type="dp">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Procedure Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn" type="button">⛶</button>
  </header>
  <div class="dp-grid">
    <div class="dp-field"><div class="dp-label">Description of Procedure</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Indications</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Interpretation of Findings</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Client Education</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Nursing Actions (Pretest)</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Nursing Actions (Intratest)</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Nursing Actions (Posttest)</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Potential Complications</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
    <div class="dp-field"><div class="dp-label">Contraindications/Precautions</div><div class="dp-value">[...]</div><div class="dp-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[name]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.3 Growth & Development (uses `.bc-grid` — same as Basic Concept)

Growth & Development templates reuse the Basic Concept grid in MN. PD's G&D templates also use `.bc-grid`. There is no `.gd-grid` class.

Use the D.2.1 structure but set `data-type="gd"` and populate the same 3 fields (Related Content, Underlying Principles, Nursing Interventions) with developmentally-focused content.

#### D.2.4 Medication (`.med-grid` — 11 fields)

```html
<article class="example-card" id="ex-chN-[drug]" data-ch="N" data-type="med">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Generic Name] / [Brand Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn">⛶</button>
  </header>
  <div class="med-grid">
    <div class="med-field"><div class="med-label">Medication Class</div><div class="med-value">[Drug class]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Expected Pharmacologic Action</div><div class="med-value">[Mechanism of action]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Therapeutic Use</div><div class="med-value">[Indications]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Complications</div><div class="med-value">[Adverse effects, toxicity]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Contraindications/Precautions</div><div class="med-value">[...]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Interactions</div><div class="med-value">[Drug-drug, drug-food]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Medication Administration</div><div class="med-value">[Route, dose range, timing]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Evaluation of Medication Effectiveness</div><div class="med-value">[Therapeutic indicators]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Nursing Interventions</div><div class="med-value">[Pre/peri/post-admin actions]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Therapeutic Procedure</div><div class="med-value">[Related procedures, if any]</div><div class="med-blank">_____________</div></div>
    <div class="med-field"><div class="med-label">Client Education</div><div class="med-value">[Teaching points]</div><div class="med-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[drug]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.5 Nursing Skill (`.ns-grid` — 7 fields)

```html
<article class="example-card" id="ex-chN-[skill]" data-ch="N" data-type="ns">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Skill Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn">⛶</button>
  </header>
  <div class="ns-grid">
    <div class="ns-field"><div class="ns-label">Description of Skill</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Indications</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Outcomes/Evaluation</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Considerations (Pre, Intra, Post)</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Client Education</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Potential Complications</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
    <div class="ns-field"><div class="ns-label">Nursing Interventions</div><div class="ns-value">[...]</div><div class="ns-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[skill]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.6 System Disorder (`.sd-grid` — 12 fields)

The most-used template type. 60+ examples in MN.

```html
<article class="example-card" id="ex-chN-[disorder]" data-ch="N" data-type="sd">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Disorder Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn">⛶</button>
  </header>
  <div class="sd-grid">
    <div class="sd-field"><div class="sd-label">Alterations in Health</div><div class="sd-value">[Brief description of disorder]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Pathophysiology</div><div class="sd-value">[Disease mechanism]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Health Promotion / Disease Prevention</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Risk Factors</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Subjective Data</div><div class="sd-value">[Client report]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Objective Data</div><div class="sd-value">[Observed findings]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Lab Tests</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Diagnostic Procedures</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Nursing Care</div><div class="sd-value">[Interventions]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Medications</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Client Education</div><div class="sd-value">[Teaching points]</div><div class="sd-blank">_____________</div></div>
    <div class="sd-field"><div class="sd-label">Complications</div><div class="sd-value">[...]</div><div class="sd-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[disorder]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.7 Therapeutic Procedure (`.tp-grid` — 9 fields)

```html
<article class="example-card" id="ex-chN-[procedure]" data-ch="N" data-type="tp">
  <header class="ex-head">
    <span class="ex-chip">Ch N</span>
    <h3 class="ex-title">[Procedure Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn">⛶</button>
  </header>
  <div class="tp-grid">
    <div class="tp-field"><div class="tp-label">Description of Procedure</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Indications</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Outcomes/Evaluation</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Considerations (Pre/Intra/Post)</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Client Education</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Potential Complications</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Nursing Interventions</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Contraindications/Precautions</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
    <div class="tp-field"><div class="tp-label">Interpretation of Findings</div><div class="tp-value">[...]</div><div class="tp-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-chN-[procedure]"> Mark studied
    </label>
  </footer>
</article>
```

#### D.2.8 Concept Analysis (`.ca-grid` — 4 fields)

The rarest template type (2 in MN, 1 in PD).

```html
<article class="example-card" id="ex-[concept]" data-ch="N" data-type="ca">
  <header class="ex-head">
    <span class="ex-chip">Concept</span>
    <h3 class="ex-title">[Concept Name]</h3>
    <a class="ex-jump" href="Elevated%20ATI%20[Subject]%20Book.html#chN-[topic]">→ Read in book</a>
    <button class="ex-expand-btn">⛶</button>
  </header>
  <div class="ca-grid">
    <div class="ca-field"><div class="ca-label">Concept Definition</div><div class="ca-value">[...]</div><div class="ca-blank">_____________</div></div>
    <div class="ca-field"><div class="ca-label">Defining Characteristics</div><div class="ca-value">[...]</div><div class="ca-blank">_____________</div></div>
    <div class="ca-field"><div class="ca-label">Related Concepts</div><div class="ca-value">[...]</div><div class="ca-blank">_____________</div></div>
    <div class="ca-field"><div class="ca-label">Clinical Application</div><div class="ca-value">[...]</div><div class="ca-blank">_____________</div></div>
  </div>
  <footer class="ex-foot">
    <label class="ex-studied">
      <input type="checkbox" data-studied-id="ex-[concept]"> Mark studied
    </label>
  </footer>
</article>
```

**Note:** Concept Analysis cards may use a non-`chN`-prefixed ID (e.g., `ex-tissue-perfusion`, `ex-attachment`) because the concept spans multiple chapters.

---

### 8.13 Procedure — Add A New Template Type

> *Consolidated from former Addendum F.5.*

Use case: ATI introduces a new Active Learning Template type (rare but possible).

#### F.5.1 Steps

1. **Decide the code:** 2-letter lowercase identifier (e.g., `pp` for "Patient Population", `fs` for "Functional Status"). Don't conflict with existing 8.

2. **Update Templates file:**
   - Add a new `<section class="template-section" data-section="new-type-name">` inside `template-pool`
   - Add a new `<div class="tpl-accordion" id="new-type-name-acc">` in main content
   - Add a new chip to `.tpl-filter-chips`: `<button class="tpl-chip" data-filter-type="pp">New Type</button>`
   - Add CSS for `.pp-grid`, `.pp-field`, `.pp-label`, `.pp-value`, `.pp-blank` per D.3 pattern

3. **Add example cards** with `data-type="pp"`.

4. **Update Hub `types-grid`** to include the new type.

5. **Update stats:** Hub `<div class="stat-value">8</div>` becomes `<div class="stat-value">9</div>`.

#### F.5.2 Filter system extension

The filter system (B.6 chip array) already supports new types via `data-filter-type` — no JS changes needed beyond adding the chip.

#### F.5.3 CSS pattern for new grid

```css
.pp-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 10px;
}
@media (min-width: 700px) {
  .pp-grid { grid-template-columns: 1fr 1fr; }
}
.pp-field { /* inherit common .{type}-field styling */ }
.pp-label { /* inherit */ }
.pp-value { /* inherit */ }
.pp-blank { /* inherit */ }
```

---

---

## PART 9 — FLASHCARDS FILE

### 9.1 Document structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#d97706">
  <title>Elevated · ATI MN Flashcards</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display:ital,wght@0,400;1,400&family=DM+Sans:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>/* ~15 KB of CSS */</style>
</head>
<body>
  <button class="sidebar-toggle" id="sidebarToggle">☰</button>
  <a class="back-home-mobile" href="Elevated%20ATI%20MN%20Hub.html">← Back to Hub</a>
  <div class="sidebar-overlay" id="sidebarOverlay"></div>

  <div class="layout">
    <aside class="sidebar" id="sidebar">
      <div class="sidebar-header">
        <a class="back-home" href="Elevated%20ATI%20MN%20Hub.html">Back to Hub</a>
        <div class="sb-course">NUR 2460 · ATI</div>
        <div class="sb-title">Flashcards</div>
        <div class="sb-sub">SM-2 spaced repetition</div>
        <button id="themeToggle"><span id="themeIcon">☀️</span> <span id="themeLabel">Light Mode</span></button>
      </div>

    </aside>

    <main class="main-content">

      <!-- Deck stats — 3 metrics in horizontal flex layout (NOT a list in sidebar) -->
      <div class="deck-stats">
        <div class="deck-stat">
          <div class="deck-stat-value due" id="statDue">0</div>
          <div class="deck-stat-label">Due now</div>
        </div>
        <div class="deck-stat">
          <div class="deck-stat-value" id="statDeck">0</div>
          <div class="deck-stat-label">In deck</div>
        </div>
        <div class="deck-stat">
          <div class="deck-stat-value zero" id="statDone">0</div>
          <div class="deck-stat-label">Reviewed today</div>
        </div>
      </div>

      <!-- Session panel — live timer + counter -->
      <div class="session-panel" id="sessionPanel">
        <div class="session-stat" title="Time elapsed in this study session">
          <span class="session-stat-icon">⏱</span>
          <span><strong id="sessionTime">0:00</strong></span>
        </div>
        <div class="session-stat" title="Cards reviewed this session">
          <span class="session-stat-icon">📊</span>
          <span><strong id="sessionReviewed">0</strong> reviewed</span>
        </div>
        <div class="session-stat" title="Average seconds per card">
          <span class="session-stat-icon">⚡</span>
          <span><strong id="sessionAvg">—</strong>/card</span>
        </div>
        <button class="session-help-btn" type="button" id="kbdHelpBtn" title="Keyboard shortcuts (press ? anytime)">⌨ Shortcuts</button>
      </div>

      <!-- (Note: Filters live in the Browse tab; see PART 9.9 for the full filter-panel HTML.
            Tabs (Review vs Browse) are managed by PART 9.8.
            The stage div below is where the current flashcard renders during Review.) -->

      <div id="stage" class="stage"></div>

    <main class="main-content">

      <div class="main-course">NUR 2460 · ATI</div>
      <h1 class="main-title">Flashcards · <em>MN</em></h1>

      <!-- Tabs -->
      <div class="fc-tab-bar">
        <button class="fc-tab active" data-tab="review">▶ Review queue</button>
        <button class="fc-tab" data-tab="browse">📋 Browse all</button>
      </div>

      <!-- Review tab -->
      <div class="fc-tab-panel active" id="fc-tab-review">
        <div class="fc-progress-row">
          <div class="fc-progress-bar"><div class="fc-progress-fill" id="reviewProgressFill"></div></div>
          <div class="fc-progress-text" id="reviewProgressText">0 / 0 reviewed this session</div>
        </div>

        <div class="fc-card-container" id="fcCardContainer">
          <!-- Card rendered here -->
        </div>

        <div class="fc-empty" id="fcEmpty" hidden>
          <div class="fc-empty-icon">✓</div>
          <h2>No cards due right now</h2>
          <p>You're caught up! Check back later or open a chapter to rate more prompts.</p>
          <a href="Elevated%20ATI%20MN%20Book.html" class="fc-empty-cta">Open book →</a>
        </div>
      </div>

      <!-- Browse tab -->
      <div class="fc-tab-panel" id="fc-tab-browse">
        <div class="fc-browse-grid" id="fcBrowseGrid">
          <!-- Cards listed here -->
        </div>
      </div>

      <!-- Keyboard hint -->
      <div class="fc-kbd-hint">
        <kbd>Space</kbd> reveal · <kbd>1</kbd> hard · <kbd>2</kbd> good · <kbd>3</kbd> easy · <kbd>?</kbd> shortcuts
      </div>
    </main>
  </div>

  <script>/* Flashcards IIFE */</script>
</body>
</html>
```

### 9.2 Deck stats

> ✅ **VERIFIED canonical against MN.** (Earlier versions documented `.stat-row` lines inside the sidebar; MN actually uses horizontal `.deck-stat` cards at the top of `.main-content`. The "session timer" is a separate `.session-panel`, not a stat-row.)

```css
/* The 3-stat horizontal strip at the top of the main content */
.deck-stats {
  display: flex;
  gap: 10px;
  margin-bottom: 24px;
  flex-wrap: wrap;
}
.deck-stat {
  flex: 1;
  min-width: 120px;
  padding: 14px 16px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
}
.deck-stat-value {
  font-family: 'DM Serif Display', serif;
  font-size: 28px;
  line-height: 1;
  color: var(--accent2);
}
.deck-stat-value.due  { color: var(--nonreassuring); }  /* Due-now stat gets warning color */
.deck-stat-value.zero { color: var(--text3); }          /* Zero state — muted */
.deck-stat-label {
  font-size: 11px;
  color: var(--text2);
  text-transform: uppercase;
  letter-spacing: 0.1em;
  margin-top: 4px;
  font-weight: 500;
}

/* The session-panel directly below the deck-stats */
.session-panel {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 12px;
  margin: 0 0 14px;
  padding: 10px 14px;
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 8px;
  font-size: 13px;
  flex-wrap: wrap;
}
.session-stat {
  display: flex;
  align-items: center;
  gap: 6px;
  color: var(--text2);
}
.session-stat-icon {
  font-size: 14px;
  opacity: 0.8;
}
.session-help-btn {
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 6px;
  padding: 4px 10px;
  color: var(--text2);
  font-size: 12px;
  cursor: pointer;
  font-family: inherit;
}
```

**Deck stats logic** — what each ID shows:
- `#statDue` — count of cards whose `nextReview <= now`
- `#statDeck` — total card count (all entries in schedule)
- `#statDone` — cards reviewed today (any rating action in last 24h)

JS sets these via `updateStats()` (called on every rate / page-load):
```javascript
function updateStats() {
  var schedule = loadSchedule();
  var cards = Object.values(schedule);
  var now = Date.now();
  var due = cards.filter(function(c) { return new Date(c.nextReview || 0).getTime() <= now; }).length;
  var done = cards.filter(function(c) {
    if (!c.lastRated) return false;
    return (now - new Date(c.lastRated).getTime()) < 86400000;
  }).length;

  document.getElementById('statDue').textContent  = due;
  document.getElementById('statDeck').textContent = cards.length;
  document.getElementById('statDone').textContent = done;
}
```

### 9.3 SM-2 algorithm (canonical — same as Book)

See PART 7.21 — identical implementation. Cards reach Flashcards via `nur2460_fc_schedule` localStorage key.

**Schedule data shape:**
```javascript
// nur2460_fc_schedule
{
  "ch1-p1": {
    id: "ch1-p1",
    chapter: "1",
    type: "PRIORITY",
    anchor: "ch1-hormonal",
    prompt: "A client missed two consecutive doses...",
    answer: "Take the most recent missed pill ASAP...",
    reps: 2,
    ef: 2.4,
    interval: 6,
    nextReview: "2026-05-17T14:30:00.000Z",
    lastRated: "2026-05-11T14:30:00.000Z"
  },
  "fc-ch1-spinnbarkeit": { /* same shape */ },
  // ...
}
```

### 9.4 Card rendering

> ✅ **VERIFIED canonical against MN as of 2026-05-12.** (Earlier versions used a `.fc-card-*` naming convention that doesn't exist in MN — the correct prefix is `.flashcard-*`.)

The render function returns an HTML string that the calling code injects into `#stage`. The string includes the card itself plus a progress line below it.

```javascript
function buildFlashcardHTML(card) {
  var typeKey = (card.type || 'content').toLowerCase();
  var chLabel = (card.ch || 'ch?').toUpperCase().replace('CH', 'Ch ');
  var anchor = card.anchor || card.ch || 'ch1';

  return '' +
    '<div class="flashcard flashcard-' + typeKey + '" data-card-id="' + card.id + '">' +
      '<div class="flashcard-head">' +
        '<span class="flashcard-tag">' + escapeHtml(card.type || 'CONTENT') + '</span>' +
        '<span class="flashcard-ch">' + chLabel + '</span>' +
        '<span class="flashcard-due">' + dueLabel(card) + '</span>' +
      '</div>' +
      '<div class="flashcard-q">' + (card.q || '(question not stored — re-rate in chapter book)') + '</div>' +
      '<button class="flashcard-reveal" type="button" data-action="reveal">' +
        'Reveal answer<span class="kbd-hint">Space</span>' +
      '</button>' +
      '<div class="flashcard-a">' + (card.a || '(answer not stored)') + '</div>' +
      '<a class="flashcard-source-link" href="Elevated%20ATI%20MN%20Book.html#' + (card.anchor || '') + '" target="_self">📖 Open in book</a>' +
      '<div class="flashcard-rating">' +
        '<button class="flashcard-rate flashcard-rate-hard" type="button" data-action="rate" data-value="0">' +
          'Hard<span class="flashcard-rate-small">+1 day</span><span class="kbd-hint">1</span>' +
        '</button>' +
        '<button class="flashcard-rate flashcard-rate-good" type="button" data-action="rate" data-value="3">' +
          'Good<span class="flashcard-rate-small">extend</span><span class="kbd-hint">2</span>' +
        '</button>' +
        '<button class="flashcard-rate flashcard-rate-easy" type="button" data-action="rate" data-value="5">' +
          'Easy<span class="flashcard-rate-small">boost</span><span class="kbd-hint">3</span>' +
        '</button>' +
      '</div>' +
      '<div class="flashcard-footer">' +
        '<a class="flashcard-open" href="Elevated%20ATI%20MN%20Book.html#' + anchor + '">Open in chapter ↗</a>' +
        '<button class="flashcard-skip" type="button" data-action="skip">Skip →</button>' +
      '</div>' +
    '</div>' +
    '<div class="review-progress">' +
      'Card ' + (reviewIndex + 1) + ' of ' + reviewQueue.length + ' due today · ' +
      sessionRated + ' rated this session' +
    '</div>';
}
```

**Key facts:**
- The function returns a STRING; calling code does `stage.innerHTML = buildFlashcardHTML(card)`
- Class name pattern is `flashcard-` (NOT `fc-card-` — that was a guide error)
- Type modifier added at render: `.flashcard-concept`, `.flashcard-warning`, `.flashcard-calc`, etc. — see PART 10.4
- Reveal mechanism: clicking `.flashcard-reveal` adds `.revealed` class to `.flashcard` parent; CSS handles the visibility transition
- Cross-link: two links to Book file with anchor — `.flashcard-source-link` (top) and `.flashcard-open` (footer)
- `data-action` attribute on buttons drives event delegation: `reveal`, `rate`, `skip`
- `data-value` on rate buttons: `0` (Hard), `3` (Good), `5` (Easy) — these are the SM-2 quality scores

**Required helpers** (also in MN):
- `escapeHtml(str)` — HTML-escapes user-controlled strings
- `dueLabel(card)` — returns "Due now", "Due in 3 days", etc.
- Module-scope vars: `reviewIndex`, `reviewQueue`, `sessionRated` (see 9.7)

**Per-subject changes:**
- The Book href links contain the subject name (`Elevated%20ATI%20MN%20Book.html` → `...%20PD%20Book.html` for PD)
- All `.flashcard-*` class names stay the same
- Card data structures stay the same

### 9.5 Card styling

> ✅ **VERIFIED canonical against MN as of 2026-05-12.** (Earlier versions used `.fc-card-*` naming — that was a guide error. The correct prefix is `.flashcard-*`.)

The CSS uses a single base class `.flashcard` plus type modifiers (`.flashcard-content`, `.flashcard-warning`, etc.) for left-border color. The `.revealed` modifier toggles answer/rating visibility.

```css
.flashcard {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 28px 28px 24px;
  position: relative;
  border-left-width: 5px;
}

/* Type modifiers — set left-border color (added by buildFlashcardHTML) */
.flashcard-content   { border-left-color: var(--prompt-content); }
.flashcard-judgment  { border-left-color: var(--prompt-judgment); }
.flashcard-principle { border-left-color: var(--prompt-principle); }
.flashcard-priority  { border-left-color: var(--prompt-priority); }

/* Head row: type tag, chapter chip, due-date label */
.flashcard-head {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 18px;
  flex-wrap: wrap;
}
.flashcard-tag {
  display: inline-block;
  font-size: 10px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  padding: 3px 9px;
  border-radius: 5px;
  color: var(--bg);
}
.flashcard-content   .flashcard-tag { background: var(--prompt-content); }
.flashcard-judgment  .flashcard-tag { background: var(--prompt-judgment); }
.flashcard-principle .flashcard-tag { background: var(--prompt-principle); }
.flashcard-priority  .flashcard-tag { background: var(--prompt-priority); }

.flashcard-ch {
  font-size: 11px;
  color: var(--text3);
  font-weight: 600;
  background: var(--surface2);
  padding: 3px 8px;
  border-radius: 5px;
}
.flashcard-due {
  font-size: 11px;
  color: var(--text2);
  margin-left: auto;
  font-style: italic;
}

/* Question — DM Serif Display for readability */
.flashcard-q {
  font-family: 'DM Serif Display', serif;
  font-weight: 400;
  font-size: 19px;
  line-height: 1.4;
  color: var(--text);
  margin: 0 0 18px;
}

/* Reveal button — full width, accent color */
.flashcard-reveal {
  background: var(--accent);
  color: var(--bg);
  border: none;
  font-weight: 600;
  font-size: 14px;
  padding: 11px 22px;
  border-radius: 10px;
  cursor: pointer;
  transition: all .15s ease;
  width: 100%;
}
.flashcard-reveal:hover { background: var(--accent2); }

/* Answer — hidden by default; .revealed reveals it */
.flashcard-a {
  display: none;
  margin: 8px 0 16px;
  padding: 16px 18px;
  background: var(--surface2);
  border-radius: 10px;
  font-size: 15px;
  color: var(--text);
  line-height: 1.6;
}

/* The .revealed state machine */
.flashcard.revealed .flashcard-a       { display: block; }
.flashcard.revealed .flashcard-reveal  { display: none; }
.flashcard.revealed .flashcard-rating  { display: flex; }

/* Rating row — hidden by default; visible after reveal */
.flashcard-rating {
  display: none;
  align-items: center;
  gap: 8px;
  margin-top: 8px;
  flex-wrap: wrap;
}
.flashcard-rate {
  flex: 1;
  min-width: 80px;
  background: var(--surface2);
  border: 2px solid var(--border);
  color: var(--text);
  font-weight: 600;
  font-size: 13px;
  padding: 11px 12px;
  border-radius: 10px;
  cursor: pointer;
  transition: all .15s ease;
}
.flashcard-rate-hard:hover {
  border-color: var(--prompt-priority);
  background: var(--prompt-priority-bg);
  color: var(--prompt-priority);
}
.flashcard-rate-good:hover {
  border-color: var(--prompt-judgment);
  background: var(--prompt-judgment-bg);
  color: var(--prompt-judgment);
}
.flashcard-rate-easy:hover {
  border-color: var(--prompt-content);
  background: var(--prompt-content-bg);
  color: var(--prompt-content);
}
.flashcard-rate-small {
  display: block;
  font-size: 10px;
  font-weight: 500;
  color: var(--text3);
  margin-top: 3px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
}

/* Footer — open-in-chapter link + skip */
.flashcard-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 14px;
  padding-top: 14px;
  border-top: 1px solid var(--border-soft);
  gap: 10px;
  flex-wrap: wrap;
}
.flashcard-open {
  font-size: 12px;
  color: var(--accent);
  font-weight: 600;
}
.flashcard-open:hover { color: var(--accent2); }
.flashcard-skip {
  background: transparent;
  border: 1px solid var(--border-soft);
  color: var(--text3);
  font-size: 12px;
  padding: 6px 12px;
  border-radius: 7px;
  cursor: pointer;
}
.flashcard-skip:hover {
  color: var(--text2);
  border-color: var(--text3);
}

/* Cross-link to Book — visible at top */
.flashcard-source-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  padding: 7px 12px;
  margin: 10px 0 6px;
  background: transparent;
  border: 1px solid var(--border);
  border-radius: 6px;
  color: var(--text2);
  font-size: 12px;
  text-decoration: none;
  font-weight: 500;
  transition: all 0.15s;
}
.flashcard-source-link:hover {
  border-color: var(--accent);
  color: var(--accent);
}
```

**Modifier classes that drive states** (see PART 10.4):
- `.flashcard.revealed` — user clicked "Reveal answer"; CSS shows `.flashcard-a` and `.flashcard-rating`, hides `.flashcard-reveal`
- `.flashcard-{type}` — type modifier added by `buildFlashcardHTML()` at render time (controls left-border + tag color)

**Per-subject changes:** None to CSS. The 4 prompt-* CSS variables (set in PART 3.2) drive the colors.

### 9.6 Keyboard shortcuts

> ✅ **VERIFIED canonical against MN.** (Earlier versions referenced `.fc-card` which doesn't exist; correct selector is `.flashcard`. Earlier version was also missing the input-typing guard, `?` help overlay, and h/g/e letter shortcuts.)

The handler is a single `keydown` listener on `document`. It supports both digit and letter rating shortcuts, plus a `?` help overlay.

```javascript
document.addEventListener('keydown', function(e) {
  var overlay = document.getElementById('kbdHelpOverlay');
  var overlayOpen = overlay && overlay.classList.contains('show');

  // Help overlay: Escape closes it; ? toggles it
  if (e.key === 'Escape' && overlayOpen) {
    e.preventDefault();
    hideKbdHelp();
    return;
  }
  if (e.key === '?' || (e.shiftKey && e.key === '/')) {
    e.preventDefault();
    if (overlayOpen) hideKbdHelp(); else showKbdHelp();
    return;
  }
  if (overlayOpen) return;

  // Don't hijack typing in inputs
  if (isTypingInInput()) {
    if (e.key === 'Escape') {
      document.activeElement.blur();
      e.preventDefault();
    }
    return;
  }

  var stage = document.getElementById('stage');
  var card = stage ? stage.querySelector('.flashcard') : null;
  var revealed = card && card.classList.contains('revealed');
  var key = e.key.toLowerCase();

  // Space or Enter: reveal (if hidden) or rate-Good (if revealed)
  if (e.key === ' ' || e.key === 'Enter') {
    if (currentTab !== 'review') return;
    if (!card) return;
    if (!revealed) {
      e.preventDefault();
      card.classList.add('revealed');
    } else {
      e.preventDefault();
      var goodBtn = card.querySelector('[data-action="rate"][data-value="3"]');
      if (goodBtn) goodBtn.click();
    }
    return;
  }

  // Rating shortcuts (only when revealed): 1/h=Hard, 2/g=Good, 3/e=Easy
  if (currentTab === 'review' && card && revealed) {
    var ratingMap = { '1': 0, 'h': 0, '2': 3, 'g': 3, '3': 5, 'e': 5 };
    if (key in ratingMap) {
      var btn = card.querySelector('[data-action="rate"][data-value="' + ratingMap[key] + '"]');
      if (btn) {
        e.preventDefault();
        btn.click();
      }
    }
  }
});

// Helpers
function isTypingInInput() {
  var el = document.activeElement;
  return el && (el.tagName === 'INPUT' || el.tagName === 'TEXTAREA' || el.isContentEditable);
}
function showKbdHelp() { document.getElementById('kbdHelpOverlay').classList.add('show'); }
function hideKbdHelp() { document.getElementById('kbdHelpOverlay').classList.remove('show'); }
```

**Shortcut map:**
| Key | Action |
|---|---|
| `Space` / `Enter` | Reveal answer (or rate Good if already revealed) |
| `1` or `h` | Rate Hard |
| `2` or `g` | Rate Good |
| `3` or `e` | Rate Easy |
| `?` | Toggle keyboard help overlay |
| `Escape` | Close overlay / blur input |

**Required DOM:**
- `#stage` — contains the current `.flashcard`
- `#kbdHelpOverlay` — modal explaining shortcuts
- `currentTab` — module-scope variable holding current tab name (`'review'` or `'browse'`)

### 9.7 Session timer

> ✅ **VERIFIED canonical against MN.** (Earlier versions documented `updateSessionUI` + `#statTimer` + `#reviewProgressText`. The actual function is `updateSessionDisplay` and the elements are `#sessionTime`, `#sessionReviewed`, `#sessionAvg`.)

The timer accumulates **active** time (pauses when the tab is hidden). Three display elements update once per second.

```javascript
// Module-scope state
var sessionRated = 0;            // incremented each time the user rates a card
var sessionStartTime = Date.now();
var sessionActiveTime = 0;       // ms — accumulates only while tab is visible
var sessionLastActive = Date.now();
var sessionTimerInterval = null;

function updateSessionDisplay() {
  var now = Date.now();
  if (!document.hidden) {
    sessionActiveTime += (now - sessionLastActive);
  }
  sessionLastActive = now;

  var timeEl     = document.getElementById('sessionTime');
  var reviewedEl = document.getElementById('sessionReviewed');
  var avgEl      = document.getElementById('sessionAvg');

  if (timeEl)     timeEl.textContent     = formatSessionTime(sessionActiveTime);
  if (reviewedEl) reviewedEl.textContent = sessionRated || 0;
  if (avgEl) {
    if (sessionRated > 0) {
      var avgMs = sessionActiveTime / sessionRated;
      avgEl.textContent = Math.round(avgMs / 1000) + 's';
    } else {
      avgEl.textContent = '—';
    }
  }
}

function startSessionTimer() {
  if (sessionTimerInterval) return;
  sessionLastActive = Date.now();
  sessionTimerInterval = setInterval(updateSessionDisplay, 1000);
}

// Pause/resume on visibility change (prevents accumulating idle background time)
document.addEventListener('visibilitychange', function() {
  if (document.hidden) {
    var now = Date.now();
    sessionActiveTime += (now - sessionLastActive);
  }
  sessionLastActive = Date.now();
});

function formatSessionTime(ms) {
  var totalSec = Math.floor(ms / 1000);
  var min = Math.floor(totalSec / 60);
  var sec = totalSec % 60;
  return min + ':' + (sec < 10 ? '0' : '') + sec;
}
```

**Required DOM elements:**
- `#sessionTime` — formatted elapsed time (m:ss)
- `#sessionReviewed` — count of cards rated this session
- `#sessionAvg` — average seconds per card (or "—" if zero)

These typically live in a `#sessionPanel` container at the top of the Flashcards page.

**Key behavior:**
- Time only accumulates while the tab is visible (uses `visibilitychange` event)
- Average calculation uses `sessionActiveTime / sessionRated` — only meaningful after at least 1 rating
- `sessionRated` is incremented elsewhere (in `rateCard()` flow or after `rateCard` returns)
- No persistence — counter resets to 0 on every page load

### 9.8 Tabs (Review vs Browse)

> ✅ **VERIFIED canonical against MN.** (Earlier versions used `.fc-tab` and `.fc-tab-panel` class names — those don't exist in MN. The actual classes are `.tabs`, `.tab`, `.tab-count`.)

The Flashcards page has 2 tabs at the top: **Review** (default — shows one due card at a time) and **Browse** (grid of all cards). Active tab is tracked by `currentTab` module-scope variable.

**HTML:**
```html
<div class="tabs">
  <button class="tab active" data-tab="review" type="button">
    Review <span class="tab-count" id="tabCountDue">0</span>
  </button>
  <button class="tab" data-tab="browse" type="button">
    Browse <span class="tab-count" id="tabCountAll">0</span>
  </button>
</div>
```

**JS:**
```javascript
var currentTab = 'review';

function setTab(name) {
  currentTab = name;
  document.querySelectorAll('.tab').forEach(function(t) {
    t.classList.toggle('active', t.getAttribute('data-tab') === name);
  });
  if (name === 'review') renderReview();
  else renderBrowse();
}

// Wire up clicks
document.querySelectorAll('.tab').forEach(function(t) {
  t.addEventListener('click', function() { setTab(t.getAttribute('data-tab')); });
});
```

**Tab content panels** — there's no `.tab-panel` element in MN. Instead, the SAME `#stage` container shows different content depending on `currentTab`:
- `currentTab === 'review'` → `renderReview()` puts one flashcard in `#stage`
- `currentTab === 'browse'` → `renderBrowse()` puts a grid of card-summaries in `#stage` (plus the filter panel above it)

**Count badges** (`#tabCountDue` and `#tabCountAll`) update from `updateStats()` — see PART 9.2.

**Modifier classes** (see PART 10.4):
- `.tab.active` — currently-selected tab

**Per-subject changes:** None to mechanism.


### 9.9 Filter system

The Browse tab supports filtering by search text, unit, chapter, type, and review status. Filter state persists to localStorage.

**State shape** (stored as `nur2460_fc_filters`):
```javascript
var filterState = {
  search: '',                  // free text — matches stripped Q+A
  unit: 'all',                 // 'all' | unitId (e.g., 'unit1')
  chapters: [],                // array of chapter numbers as strings (multi-select)
  types: [],                   // array — ['concept', 'calc', 'warning', 'content', etc.] (multi-select)
  status: 'all'                // 'all' | 'new' | 'learning' | 'mature' | 'due'
};
```

**Status semantics:**
- `new` — never been rated (no `lastRated`)
- `learning` — rated, but `repetitions < 3`
- `mature` — `repetitions >= 3`
- `due` — `nextReview <= now`

**HTML structure** (lives inside the Browse tab):
```html
<div class="filter-panel" id="filterPanel">
  <button class="filter-toggle" id="filterToggle" type="button" aria-expanded="false">
    <span>🔍 Filter cards</span>
    <span class="filter-active-count" id="filterActiveCount"></span>
    <span class="filter-chevron">▾</span>
  </button>
  <div class="filter-body" id="filterBody" hidden>
    <div class="filter-row">
      <input type="text" class="filter-search" id="filterSearch" placeholder="Search Q or A…">
    </div>
    <div class="filter-row">
      <div class="filter-label">Unit</div>
      <select class="filter-select" id="filterUnit">
        <option value="all">All units</option>
        <option value="unit1">Unit 1 — …</option>
        <!-- ... one per unit -->
      </select>
    </div>
    <div class="filter-row">
      <div class="filter-label">Chapter</div>
      <div class="filter-chips filter-chips-numeric" data-filter-group="chapter" data-multi="true">
        <button class="filter-chip" data-value="1" type="button">1</button>
        <!-- ... one per chapter -->
      </div>
    </div>
    <div class="filter-row">
      <div class="filter-label">Type</div>
      <div class="filter-chips" data-filter-group="type" data-multi="true">
        <button class="filter-chip" data-value="concept" type="button">Concept</button>
        <button class="filter-chip" data-value="warning" type="button">Warning</button>
        <button class="filter-chip" data-value="calc" type="button">Calc</button>
        <!-- ... + the 4 typed-prompt types: content/judgment/principle/priority -->
      </div>
    </div>
    <div class="filter-row">
      <div class="filter-label">Status</div>
      <div class="filter-chips" data-filter-group="status">
        <button class="filter-chip active" data-value="all" type="button">All</button>
        <button class="filter-chip" data-value="new" type="button">New</button>
        <button class="filter-chip" data-value="learning" type="button">Learning</button>
        <button class="filter-chip" data-value="mature" type="button">Mature</button>
        <button class="filter-chip" data-value="due" type="button">Due</button>
      </div>
    </div>
    <div class="filter-actions">
      <button class="filter-clear-btn" id="filterClear" type="button" hidden>Clear all filters</button>
      <span class="filter-result-count" id="filterResultCount"></span>
    </div>
  </div>
</div>
```

> **Note:** Filter class names are `.filter-*` (no prefix). This is DIFFERENT from Templates which uses `.tpl-filter-*` prefix. Each file has its own filter implementation; they don't share classes.

**Core functions:**
```javascript
var FILTER_STATE_KEY = 'nur2460_fc_filters';  // (or 'atipd_fc_filters' for PD)

function loadFilterState() {
  try {
    var raw = localStorage.getItem(FILTER_STATE_KEY);
    if (raw) {
      var parsed = JSON.parse(raw);
      filterState = Object.assign(filterState, parsed);
    }
  } catch(e) {}
}

function saveFilterState() {
  try { localStorage.setItem(FILTER_STATE_KEY, JSON.stringify(filterState)); } catch(e) {}
}

function countActiveFilters() {
  var n = 0;
  if (filterState.search) n++;
  if (filterState.unit !== 'all') n++;
  if (filterState.chapters.length > 0) n++;
  if (filterState.types.length > 0) n++;
  if (filterState.status !== 'all') n++;
  return n;
}

function applyFilters(cards) {
  var q = (filterState.search || '').toLowerCase().trim();
  var now = Date.now();
  return cards.filter(function(c) {
    if (q) {
      var hay = stripHTML((c.q || '') + ' ' + (c.a || ''));
      if (hay.indexOf(q) === -1) return false;
    }
    var chNum = (c.ch || '').replace(/^ch/i, '');
    if (filterState.unit !== 'all') {
      if (chapterUnit(chNum) !== filterState.unit) return false;
    }
    if (filterState.chapters.length > 0) {
      if (filterState.chapters.indexOf(chNum) === -1) return false;
    }
    if (filterState.types.length > 0) {
      var t = (c.type || 'concept').toLowerCase();
      if (filterState.types.indexOf(t) === -1) return false;
    }
    if (filterState.status !== 'all') {
      var reps = c.repetitions || 0;
      var lastRated = c.lastRated;
      if (filterState.status === 'new' && lastRated) return false;
      if (filterState.status === 'learning' && reps >= 3) return false;
      if (filterState.status === 'mature' && reps < 3) return false;
      if (filterState.status === 'due') {
        if (new Date(c.nextReview).getTime() > now) return false;
      }
    }
    return true;
  });
}
```

**Per-subject changes:**
- `FILTER_STATE_KEY` constant → subject namespace
- Chapter chips count = subject's chapter count
- Unit dropdown options = subject's units (MN=4, PD=3, Pharm=13)
- Type chips: 3 inline types (concept/warning/calc) + 4 typed types (content/judgment/principle/priority) — same across all subjects

---

### 9.10 Full Flashcards function catalog (35+ functions)

> ✅ **VERIFIED canonical against MN.** All listed function names exist in `Elevated ATI MN Flashcards.html`.

```
applyThemeUI()                  — Same as elsewhere
loadSchedule(), saveSchedule()  — Read/write FC schedule (same key as Book)
loadStarterDeck()               — Load STARTER_DECK array into schedule with default values
rateCard(cardId, rate)          — Apply SM-2 to a card, save, advance to next
getDeck()                       — Return all scheduled cards
getDueCards()                   — Filter to cards where dueDate <= today
getReviewedToday()              — Count cards rated today
updateStats()                   — Refresh top-bar stats (due, reviewed, etc.)
escapeHtml(), dueLabel(date), buildFlashcardHTML(card)  — Render helpers
renderReview()                  — Render the Review tab (one card at a time)
renderBrowse()                  — Render the Browse tab (full card list)
setTab(tabName)                 — Switch between Review/Browse tabs
loadFilterState(), saveFilterState()  — Filter state persistence
chapterUnit(chNum)              — Map chapter number → unit slug (SUBJECT-SPECIFIC LOGIC)
stripHTML(str)                  — Remove HTML tags from a string (for searching)
applyFilters()                  — Apply filter state to which cards show
countActiveFilters()            — Count non-default filters
applyFilterStateToUI()          — Sync chip UI to current state
updateFilterCounters()          — Update result counter display
initFilterHandlers()            — Wire filter chip event handlers
formatSessionTime(seconds)      — Convert seconds → "MM:SS" string
updateSessionDisplay()          — Refresh session timer display
startSessionTimer()             — Begin ticking the session timer
isTypingInInput(e)              — Helper: are we inside a text input? (suppresses shortcuts)
showKbdHelp()                   — Show keyboard shortcuts modal
hideKbdHelp()                   — Hide keyboard shortcuts modal
```

---

## PART 10 — CSS REFERENCE

### 10.1 Complete `:root` variable list (29 vars)

```css
:root {
  /* Backgrounds (4) */
  --bg:                 #0f1117;
  --surface:            #181c27;
  --surface2:           #1e2336;
  --surface3:           #242a40;

  /* Borders (2) */
  --border:             #2a3050;
  --border-soft:        rgba(255,255,255,0.06);

  /* Subject accent (4) */
  --accent:             #fbbf24;    /* MN: amber-400 */
  --accent2:            #fcd34d;    /* lighter for hovers */
  --accent-soft:        rgba(251,191,36,0.12);
  --accent-stripe-bg:   rgba(251,191,36,0.25);

  /* Text (3) */
  --text:               #e8eaf2;
  --text2:              #8b92b8;
  --text3:              #555e85;

  /* FHR colors (6) */
  --reassuring:         #3db87a;
  --reassuring-bg:      rgba(61,184,122,0.10);
  --indeterminate:      #e8a838;
  --indeterminate-bg:   rgba(232,168,56,0.10);
  --nonreassuring:      #e05c6a;
  --nonreassuring-bg:   rgba(224,92,106,0.10);

  /* Clinical-judgment prompt colors (8) */
  --prompt-content:     #4fa3e0;
  --prompt-content-bg:  rgba(79,163,224,0.10);
  --prompt-judgment:    #a78bfa;
  --prompt-judgment-bg: rgba(167,139,250,0.10);
  --prompt-principle:   #14b8a6;
  --prompt-principle-bg:rgba(20,184,166,0.10);
  --prompt-priority:    #ef4444;
  --prompt-priority-bg: rgba(239,68,68,0.10);

  /* Misc (2) */
  --nav-bg:             rgba(15,17,23,0.92);
  --shadow:             0 8px 24px rgba(0,0,0,0.3);
}
```

**Subject swap** — only `--accent`, `--accent2`, `--accent-soft`, `--accent-stripe-bg` change per subject:

```css
/* MN */
--accent: #fbbf24; --accent2: #fcd34d;
--accent-soft: rgba(251,191,36,0.12); --accent-stripe-bg: rgba(251,191,36,0.25);

/* PD */
--accent: #60a5fa; --accent2: #93c5fd;
--accent-soft: rgba(96,165,250,0.12); --accent-stripe-bg: rgba(96,165,250,0.25);

/* Pharm */
--accent: #fb923c; --accent2: #fdba74;
--accent-soft: rgba(251,146,60,0.12); --accent-stripe-bg: rgba(251,146,60,0.25);
```

### 10.2 Theme attribute switching

```css
:root { /* dark mode defaults */ }
[data-theme="light"] { /* light mode overrides */ }
```

**NOT** `html.light` (class). The attribute selector matters because JS sets `document.documentElement.setAttribute('data-theme', 'light')`.

### 10.3 Master CSS structure (approximate line breakdown)

```
Lines 1-50      :root variables + [data-theme="light"]
Lines 50-100    * + html + body
Lines 100-150   .layout + .main-content
Lines 150-300   .sidebar* (header, search, list, item, nav-section)
Lines 300-400   .main-title + .main-desc + .main-course
Lines 400-450   .compare-btn + .bookmarks-open-btn
Lines 450-550   .unit-accordion + .unit-header + .unit-body
Lines 550-650   .planner-row + .planner-check
Lines 650-700   .exam-reset
Lines 700-750   .chapter-pool + .chapter + .chapter-banner
Lines 750-850   .brief-card + .brief-grid
Lines 850-950   .content-section + .section-lead
Lines 950-1050  .condition-block + .condition-head + .condition-name + .condition-tag
Lines 1050-1150 .finding-grid + .finding-card
Lines 1150-1200 .kb-card + .flag
Lines 1200-1300 .modal-overlay + .modal + .modal-header + .modal-title + .modal-close
Lines 1300-1400 .modal-tabs + .modal-tabs-wrap + .tab-btn + .tab-panel
Lines 1400-1450 .modal-body
Lines 1450-1500 .modal-fc-btn
Lines 1500-1600 .exercise + .exercise-q + .exercise-a + .q-num + .q-options + .answer + .ans-letter + .nclex-tag
Lines 1600-1650 .nclex-filter
Lines 1650-1750 .mid-read + .mid-read-q + .mid-read-a + .mid-read-rate
Lines 1750-1850 .mid-prompt + .mid-prompt-tag + 4 type variants
Lines 1850-1900 .abbr + .abbr-tip-pop
Lines 1900-1950 .bookmarks-* + .bookmark-btn
Lines 1950-1990 Mobile floating buttons + sidebar-overlay
Lines 1990-2000 @media (max-width:900px) + @media (max-width:600px) + @media print
```

### 10.4 Modifier classes — the state machine

Many of the classes listed in PARTs 6–9 have **modifier classes** that encode UI state. Porters and maintainers must preserve these modifiers when manipulating elements via JavaScript, and must include them in any rendered or generated HTML. This subsection documents the modifier patterns that aren't obvious from the base class names alone.

| Base class | Modifier | What it means |
|---|---|---|
| `.sidebar-item` | `.populated` | Chapter exists in pool (vs placeholder/empty) |
| `.planner-row` | `.populated` | Visible row, has chapter content |
| `.unit-accordion` | `.collapsed` | Default state; absence = expanded |
| `.nav-section` | `.collapsed` | Default state; absence = expanded |
| `.filter-chip` | `.active` | This filter is currently applied |
| `.tab-btn` | `.active` | This tab is selected |
| `.mode-toggle button` | `.active` | This mode is selected (filled or blank) |
| `.example-card` | `[data-mode="filled"]` / `[data-mode="blank"]` | Current view mode (attribute, not class) |
| `.mid-prompt` | `.mid-prompt-rated` | User has rated this prompt |
| section h2 | `.bookmarked` | User has bookmarked this section |
| `.exercise` | `.nclex-hidden` | Hidden by current NCLEX filter |
| `.tpl-filter-chip` | `.active` | Currently active filter |
| `.flashcard` | `.flashcard-{type}` | Type modifier added at render time |
| `.flashcard-rate` | `.flashcard-rate-hard` / `-good` / `-easy` | Which rating button |
| `.pickup-card` | `hidden` attribute | Hidden if no pickup data for this card |
| `.review-queue` | `.empty` | No flashcards due yet |

**Implications for code/audits/regex:**

When checking for the presence of a class via regex, use a substring pattern that allows modifiers:
- ✅ `class="[^"]*\bsidebar-item\b[^"]*"` — matches `class="sidebar-item populated"`, `class="sidebar-item"`, etc.
- ❌ `class="sidebar-item"` (exact) — will false-negative on every modifier-using element

This is the bug pattern that caused early PD audits to falsely report "missing components" — the audit regex was over-strict.

**Implications for porting:**

When rendering or copying elements, preserve modifiers. A common error is `cardEl.className = 'sidebar-item'` — this strips the `populated` modifier and breaks subsequent state checks. Use `classList.add()` / `classList.remove()` for individual modifiers, never assignment to `className` unless you know all modifiers.

### 10.5 Key naming convention (canonical)

Different files in the PD port used different naming conventions for the same logical key:

| File | Wrote | Should Have Been |
|---|---|---|
| PD Templates (initial) | `atipd_atimnTemplates_progress` | `atipd_templates_progress` |
| PD Hub (initial) | `atipd_tpl_progress` | `atipd_templates_progress` |
| PD Templates (after batch 1) | `atipd_templates_progress` ✓ | ✓ |
| PD Hub (after batch 1) | `atipd_templates_progress` ✓ | ✓ |

#### The canonical convention

Always use **snake_case**, **full word "templates"** (not "tpl" abbreviation), **no camelCase** in the middle.

```
{namespace_prefix}_{feature_name}_{purpose}

✓ atipd_templates_progress
✓ atipd_book_progress
✓ atipd_fc_schedule
✓ atipd_last_chapter
✓ atipd_last_template
✓ atipd_bookmarks
✓ atipd_nclex_done

✗ atipd_atimnTemplates_progress  (hybrid copy-paste)
✗ atipd_tpl_progress             (abbreviation inconsistent with siblings)
✗ atipdTemplatesProgress         (camelCase, breaks scan/grep patterns)
```

#### Why this matters

When code in one file writes to `foo_progress` and code in another file reads from `bar_progress`, they silently miss each other's data with no visible error. The browser doesn't warn you. This class of bug is hard to detect without explicit cross-file checks (CHECK 5 in the integrity sweep).

---

### 10.6 Example-card CSS reference

> Complete CSS reference for `.example-card` and child elements (TP/SD/BC/Med/etc. layout, .filled/.blank states, accent rules).

Each grid class needs its own CSS. Reference rules:

```css
/* Common card chrome */
.example-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: 20px 22px;
  margin-bottom: 14px;
  position: relative;
  transition: border-color .15s, box-shadow .15s;
}
.example-card.flash {
  border-color: var(--accent);
  box-shadow: 0 0 0 2px var(--accent-soft);
}
.example-card .ex-head {
  display: flex; flex-wrap: wrap; align-items: baseline;
  gap: 8px 12px;
  margin-bottom: 16px;
  padding-bottom: 10px;
  border-bottom: 1px solid var(--border-soft);
}
.example-card .ex-chip {
  font-size: 11px; font-weight: 600;
  color: var(--accent2);
  background: var(--accent-soft);
  padding: 3px 8px;
  border-radius: 4px;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  white-space: nowrap;
}
.example-card .ex-title {
  font-family: 'DM Serif Display', serif;
  font-weight: 400;
  font-size: 18px;
  margin: 0;
  flex: 1; min-width: 200px;
}
.example-card .ex-jump {
  font-size: 11px;
  color: var(--text3);
  text-decoration: none;
  white-space: nowrap;
}
.example-card .ex-jump:hover { color: var(--accent); }
.example-card .ex-expand-btn {
  background: transparent;
  border: 1px solid var(--border);
  color: var(--text3);
  width: 26px; height: 26px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 12px;
  transition: all .15s;
}
.example-card .ex-expand-btn:hover {
  border-color: var(--accent);
  color: var(--accent);
}

/* Grid layouts — each type has its own */
.bc-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
}
@media (min-width: 700px) {
  .bc-grid { grid-template-columns: 1fr 1fr 1fr; }
}

.sd-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 10px;
}
@media (min-width: 700px) {
  .sd-grid { grid-template-columns: 1fr 1fr; }
}

.med-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 10px;
}
@media (min-width: 700px) {
  .med-grid { grid-template-columns: 1fr 1fr; }
}

.tp-grid, .dp-grid, .ns-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 10px;
}
@media (min-width: 700px) {
  .tp-grid, .dp-grid, .ns-grid { grid-template-columns: 1fr 1fr; }
}

.ca-grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
}
@media (min-width: 700px) {
  .ca-grid { grid-template-columns: 1fr 1fr; }
}

/* Each {type}-field */
.bc-field, .sd-field, .med-field, .tp-field, .dp-field, .ns-field, .ca-field {
  background: var(--surface2);
  border: 1px solid var(--border-soft);
  border-radius: 8px;
  padding: 12px 14px;
}
.bc-label, .sd-label, .med-label, .tp-label, .dp-label, .ns-label, .ca-label {
  font-size: 10px; font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--accent2);
  margin-bottom: 6px;
}
.bc-value, .sd-value, .med-value, .tp-value, .dp-value, .ns-value, .ca-value {
  font-size: 13.5px;
  line-height: 1.5;
  color: var(--text);
}
.bc-value ul, .sd-value ul, .med-value ul, .tp-value ul, .dp-value ul, .ns-value ul, .ca-value ul {
  margin: 4px 0; padding-left: 16px;
}
.bc-value li, .sd-value li, .med-value li, .tp-value li, .dp-value li, .ns-value li, .ca-value li {
  margin-bottom: 3px;
}
.bc-blank, .sd-blank, .med-blank, .tp-blank, .dp-blank, .ns-blank, .ca-blank {
  font-family: 'SF Mono', Monaco, monospace;
  color: var(--text3);
  font-size: 12px;
  letter-spacing: 0.1em;
  display: none;       /* Toggled visible in body.tpl-blank mode */
}

/* Studied checkbox */
.ex-foot {
  margin-top: 14px;
  padding-top: 10px;
  border-top: 1px solid var(--border-soft);
}
.ex-studied {
  font-size: 12px;
  color: var(--text2);
  cursor: pointer;
  display: inline-flex;
  align-items: center;
  gap: 8px;
  user-select: none;
}
.ex-studied input[type="checkbox"] {
  appearance: none;
  -webkit-appearance: none;
  width: 16px; height: 16px;
  border: 2px solid var(--border);
  border-radius: 4px;
  cursor: pointer;
  position: relative;
  flex-shrink: 0;
  transition: all .15s;
}
.ex-studied input[type="checkbox"]:checked {
  background: var(--accent);
  border-color: var(--accent);
}
.ex-studied input[type="checkbox"]:checked::after {
  content: '✓';
  position: absolute; inset: 0;
  display: flex; align-items: center; justify-content: center;
  color: var(--bg);
  font-size: 11px;
}
```

---

---

## PART 11 — JAVASCRIPT REFERENCE

### 11.1 Where each function lives

**Book file — 3 inline scripts (in order):**
- Script 1 (main IIFE): functions 1-46 from PART 7.21
- Script 2 (BATCH 3 NCLEX): functions 41-46 + injection
- Script 3 (mid-read flashcard prompts): functions 27-31 + injection

**Templates file — 1 IIFE:** all 41 functions from PART 8.11
**Flashcards file — 1 IIFE:** ~25 functions (rendering, SM-2, keyboard, filters)
**Hub file — 1 IIFE:** ~10 functions (theme, pickup, progress display, storage panel)
**Index file — 1 IIFE:** just theme toggle

### 11.2 Module call order at page load

```javascript
(function() {
  'use strict';

  // 1. Theme — must come first to prevent FOUC
  (function() {
    var saved = localStorage.getItem('nur2460_theme');
    if (saved === 'light') document.documentElement.setAttribute('data-theme', 'light');
  })();

  // 2. Constants
  var ABBR_DICT = { ... };

  // 3. Function definitions
  function applyThemeUI() { ... }
  function loadProgress() { ... }
  // ... all functions ...

  // 4. DOMContentLoaded wiring
  document.addEventListener('DOMContentLoaded', function() {
    // Event listeners
    document.getElementById('themeToggle').addEventListener('click', ...);
    document.getElementById('searchInput').addEventListener('input', ...);
    // ... etc ...

    // Init
    applyThemeUI();
    initProgress();
    autoWrapAbbreviations(document.querySelector('.main-content'));
    bindAbbrs(document);
    bindExercises(document);

    // Cross-tool sync hook
    _installCrossToolHook();

    // Hash navigation
    if (location.hash) {
      var hash = location.hash.substring(1);
      var ch = hash.match(/^(ch\d+)/);
      if (ch) openChapter(ch[1], hash);
    }
  });

  // 5. Expose globals if needed
  window.openChapter = openChapter;
  window.closeChapterModal = closeChapterModal;
})();
```

### 11.3 LocalStorage utility pattern

Every load/save pair uses this pattern:
```javascript
function loadX() {
  try { return JSON.parse(localStorage.getItem(KEY) || 'DEFAULT'); }
  catch(e) { return DEFAULT_VALUE; }
}
function saveX(value) {
  try { localStorage.setItem(KEY, JSON.stringify(value)); }
  catch(e) { console.warn('Storage error', e); }
}
```

This protects against:
- Missing keys (returns default)
- Corrupted JSON (returns default)
- QuotaExceededError on save (silent fail with console warning)

### 11.4 Hub-specific functions

```javascript
function countDueCards() {
  try {
    var schedule = JSON.parse(localStorage.getItem('nur2460_fc_schedule') || '{}');
    var now = Date.now();
    var due = 0;
    Object.values(schedule).forEach(function(c) {
      if (!c.nextReview || new Date(c.nextReview).getTime() <= now) due++;
    });
    return due;
  } catch(e) { return 0; }
}

function updateBookProgressBar() {
  try {
    var p = JSON.parse(localStorage.getItem('nur2460_atimn_progress') || '{}');
    var read = Object.values(p).filter(function(v) { return v === 2; }).length;
    var total = 27;  // MN chapter count
    document.getElementById('bookProgress').style.width = (read / total * 100) + '%';
    document.getElementById('bookProgressText').textContent = read + ' / ' + total + ' read';
  } catch(e) {}
}

function updateTemplateProgressBar() {
  try {
    var p = JSON.parse(localStorage.getItem('nur2460_atimnTemplates_progress') || '{}');
    var studied = Object.keys(p).length;
    var total = 105;
    document.getElementById('tplProgress').style.width = (studied / total * 100) + '%';
    document.getElementById('tplProgressText').textContent = studied + ' / ' + total + ' studied';
  } catch(e) {}
}

function updateFcProgressBar() {
  var due = countDueCards();
  document.getElementById('fcProgressText').textContent = due + ' due now';
  // Bar uses different metric — % of cards mature
  try {
    var schedule = JSON.parse(localStorage.getItem('nur2460_fc_schedule') || '{}');
    var cards = Object.values(schedule);
    var mature = cards.filter(function(c) { return c.interval >= 21; }).length;
    var total = cards.length || 1;
    document.getElementById('fcProgress').style.width = (mature / total * 100) + '%';
  } catch(e) {}
}

function updateUnitCardProgress() {
  try {
    var p = JSON.parse(localStorage.getItem('nur2460_atimn_progress') || '{}');
    // MN unit ranges
    var units = {
      unit1: { range: [1, 10] },
      unit2: { range: [11, 14] },
      unit3: { range: [15, 22] },
      unit4: { range: [23, 27] }
    };
    Object.keys(units).forEach(function(u) {
      var r = units[u].range;
      var total = r[1] - r[0] + 1;
      var read = 0;
      for (var i = r[0]; i <= r[1]; i++) {
        if (p['ch' + i] === 2) read++;
      }
      var bar = document.querySelector('[data-unit-bar="' + u + '"]');
      var text = document.querySelector('[data-unit-text="' + u + '"]');
      if (bar) bar.style.width = (read / total * 100) + '%';
      if (text) text.textContent = read + ' / ' + total + ' read';
    });
  } catch(e) {}
}
```

---

## PART 12 — LOCALSTORAGE SCHEMA

### 12.1 All keys by subject

**MN (Maternal-Newborn)** — prefix `nur2460_atimn_` for Book, `nur2460_atimnTemplates_` for Templates, plus shared `nur2460_*` keys:
```
nur2460_atimn_progress           — Book chapter checkboxes (0/1/2 state per chapter)
nur2460_atimnTemplates_progress  — Templates studied state (set of example IDs)
nur2460_fc_schedule              — SHARED with Pharm
nur2460_last_chapter             — SHARED with Pharm
nur2460_last_template            — MN-specific (no Pharm Templates yet)
nur2460_bookmarks                — SHARED with Pharm
nur2460_nclex_done               — SHARED with Pharm
nur2460_theme                    — SHARED across all subjects
nur2460_tpl_filters              — Templates filter state
nur2460_pickup_dismissed         — Hub pickup panel dismissed flag
```

**PD (Pediatric)** — completely separate `atipd_` prefix:
```
atipd_book_progress              — Book chapter checkboxes
atipd_templates_progress         — Templates studied state
atipd_fc_schedule                — PD-specific schedule
atipd_last_chapter
atipd_last_template
atipd_bookmarks                  — PD-specific bookmarks
atipd_nclex_done                 — PD-specific NCLEX tracking
atipd_theme                      — PD has its own theme key (separate from MN/Pharm)
atipd_tpl_filters
atipd_pickup_dismissed
```

**Pharm (Pharmacology)** — `nur2460_atipharm_` prefix for Book progress, but SHARES other keys with MN:
```
nur2460_atipharm_progress        — Book chapter checkboxes
nur2460_fc_schedule              — SHARED with MN
nur2460_last_chapter             — SHARED with MN
nur2460_bookmarks                — SHARED with MN
nur2460_nclex_done               — SHARED with MN
nur2460_theme                    — SHARED with MN
nur2460_pickup_dismissed
```

### 12.2 Data shapes

**`*_progress` (chapter checkboxes)**:
```javascript
{
  "ch1": 2,     // 0 = unread (omitted), 1 = reviewed, 2 = complete
  "ch3": 1,
  "ch5": 2,
  // ...
}
```

**`*_atimnTemplates_progress` (studied examples)**:
```javascript
{
  "ex-ch1-cocs": true,
  "ex-ch3-skin-breast": true,
  // ...
}
```

**`*_fc_schedule` (SM-2 cards)**:
```javascript
{
  "ch1-p1": {
    id: "ch1-p1",
    chapter: "1",
    type: "PRIORITY",           // or CONTENT/JUDGMENT/PRINCIPLE for typed, or concept/warning/calc for inline
    anchor: "ch1-hormonal",     // section id to link back to
    prompt: "...",
    answer: "...",
    reps: 2,                    // consecutive successful reviews
    ef: 2.4,                    // easiness factor (default 2.5, min 1.3)
    interval: 6,                // days until next review
    nextReview: "2026-05-17T...",
    lastRated: "2026-05-11T..."
  },
  "fc-ch1-spinnbarkeit": { /* same shape */ },
  // ...
}
```

**`*_last_chapter`**:
```
String, pipe-delimited: "ch3|ch3-als|Expected Physiological Changes"
```

**`*_last_template`**:
```
String, pipe-delimited: "ex-ch1-cocs|Combined Oral Contraceptives"
```

**`*_bookmarks`**:
```javascript
[
  {
    chapterId: "ch3",
    sectionId: "ch3-als",
    label: "ch3 · Active Learning Scenario",
    addedAt: "2026-05-11T14:30:00.000Z"
  },
  // ...
]
```

**`*_nclex_done`**:
```javascript
{
  "ch1-q1": true,
  "ch1-q3": true,
  // ...
}
```

**`*_theme`**:
```
String: "light" or null/missing
```

**`*_tpl_filters`**:
```javascript
{ type: 'all', state: 'all', query: '' }
// type: 'all' | 'bc' | 'dp' | 'gd' | 'med' | 'ns' | 'sd' | 'tp' | 'ca'
// state: 'all' | 'unread' | 'studied'
```

### 12.3 Migration & export format

Storage panel exports as JSON:
```javascript
{
  exportedAt: "2026-05-11T14:30:00.000Z",
  subject: "mn",          // or "pd" or "pharm"
  version: 1,
  data: {
    "nur2460_atimn_progress": "{\"ch1\":2,...}",
    "nur2460_fc_schedule": "{...}",
    // ... all keys with matching prefix
  }
}
```

Import iterates `data` and calls `localStorage.setItem(k, v)` for each entry.

---

## PART 13 — SUBJECT PORTING

> This is the canonical recipe for building a new subject suite (or verifying an existing one). It absorbs the former Addendum J.3 (build sequence), J.4 (per-subject variation), and Addendum I (porting-leak prevention) into one procedural reference.

### 13.1 PDF → finished suite (high-level)

1. **Extract PDF text** with `pypdf` or `pdfminer`
2. **Identify unit & chapter boundaries** by ToC markers
3. **For each chapter, extract:** title, lead paragraph, numbered sections, Active Learning Scenario block, Application Exercises (5 NCLEX-style questions)
4. **Identify worked templates:** search PDF for "ATI Active Learning Template: {Type}", extract field-by-field content, categorize by type
5. **Write to Book file** in chapter-pool with the canonical structure
6. **Write to Templates file** in template-pool with `template-section` wrappers
7. **Cross-link:** each chapter's `chN-templates` section lists every template that references that chapter; each template's `.ex-jump` links back to source chapter section
8. **Build Hub** with stats, pickup, primary grid, units, types
9. **Validate:** JS lints clean on all 3 Book scripts; tag balance per chapter; all IDs unique; all cross-links resolve; bookmarks button visible; theme toggle works; mobile sidebar works at 375px width

The detailed phase-by-phase procedure is in 13.2 below. The full porting checklist (with sub-bullets) is in 13.10.

### 13.2 Build sequence (8 phases)

This is the procedural recipe. Follow it in order for a new subject (or to verify an existing one). Each step is a single, testable unit of work.

#### Phase 0: Choose subject-wide values (one-time)

Fill out this table before touching any file:

```
ITEM                      MN              PD              Pharm           New subject?
─────────────────────     ─────────       ─────────       ─────────       ─────────
Subject short name        MN              PD              Pharm           ___
Display name              Maternal-       Pediatric       Pharmacology    ___
                          Newborn         Nursing
Subject 2-letter code     atimn           atipd           atipharm        ___
Storage namespace         nur2460_*       atipd_*         nur2460_*       ___
                          (shared w/      (isolated)      (shared w/
                          Pharm)                          MN)
Accent color (dark)       #fbbf24         #38bdf8         #fb923c         ___
Accent color (light)      #d97706         #0284c7         #ea580c         ___
theme-color meta          #d97706         #3b82f6         #c2410c         ___
Chapter count             27              44              49              ___
Unit count                4               3               13              ___
Template count            105             167             —               ___
Starter cards count       122             188             —               ___
Source PDF                ATI MN 11th     ATI PD 11th     ATI Pharm 8th   ___
```

#### Phase 1: PDF extraction

Before writing any HTML, extract content from the subject's source PDF:

1. Use `pdfplumber` for column-aware extraction (NOT plain `pdftotext`)
2. Find chapter boundaries by searching for `^CHAPTER N$` pattern at line starts
3. For each chapter, extract:
   - Chapter title
   - All H2/H3 section titles
   - Active Learning Scenario (look for "Active Learning Scenario" header)
   - ALS answer key (look for "Active Learning Scenario Key")
   - 5 Application Exercises with rationales (look for "Application Exercises")
   - Template references (if the chapter has them — usually inferred from textbook context)
4. Save extracted data to JSON files for use in HTML generation

See [PD's pdfplumber workflow in conversation history] for the exact extraction pattern.

#### Phase 2: Build Book file (the biggest)

Order matters. Build in this sequence:

#### Step 2.1: Copy MN Book as starting template
- `cp "Elevated ATI MN Book.html" "Elevated ATI {SUBJECT} Book.html"`

#### Step 2.2: Update top-of-file metadata
Search and replace these specific elements:
- `<title>` tag — subject name
- `<meta name="theme-color">` content — subject color
- `<meta name="apple-mobile-web-app-title">` content — subject name
- Any obvious top-of-file text references to "MN" or "Maternal-Newborn"

#### Step 2.3: Update CSS palette
- In `:root` block: update `--accent`, `--accent2`, `--accent-soft`, `--accent-stripe-bg` to subject colors
- In `[data-theme="light"]` block: same variables for light mode
- Verify all 29+8 prompt-type variables are present in both blocks

#### Step 2.4: Update sidebar structure
- `.sidebar-header` text → subject name
- Remove all `.nav-section` blocks → add new ones for subject's units
- For each unit, add `.nav-section <h3>` + `.sidebar-item` per chapter

#### Step 2.5: Update planner/units grid (in main content)
- Remove all `.unit-accordion` → add new ones for subject's units
- For each unit, add the right number of `.planner-row` blocks

#### Step 2.6: Replace chapter-pool contents
This is the bulk of the work. For each chapter:
- `<section class="chapter" id="chN">` opening
- `<div class="chapter-banner">` with meta + name + lede
- `<section id="chN-tldr" class="brief-card">` — the TL;DR
- Multiple `<section id="chN-{topic}">` blocks — content sections (varies by chapter)
- **3–6 inline `<aside class="mid-read">` blocks** placed mid-paragraph inside content sections — see DETAILED SPEC BELOW. **A chapter with zero inline mid-reads is incomplete (this exact bug bit PD).**
- `<section id="chN-als" class="content-section">` — if PDF has an ALS for this chapter
- `<section id="chN-exercises" class="content-section">` — the 5 NCLEX-style questions
- `<section id="chN-templates" class="content-section tpl-bridge">` — list of related templates
- `</section>` closing chN

**Inline mid-read DETAILED SPEC (the part that was missing before):**
- **Density**: 3–6 per chapter, never zero. Target ≈ 4.5 (matches MN's 122 inlines / 27 chapters).
- **Type mix per chapter**: at least 1 `warning`, 1–2 `concept`, 0–2 `calc` (only if chapter has math)
- **Placement**: mid-paragraph at a natural pause point inside content sections, NOT between sections as dividers
- **Required attributes on `<aside>`**:
  - `class="mid-read"`
  - `data-fc-id="fc-chN-{shortname}"` — unique flashcard ID
  - `data-fc-ch="N"` — chapter number as string
  - `data-fc-type="concept"` or `"warning"` or `"calc"` (LOWERCASE)
  - `data-fc-anchor="chN-{section-id}"` — for cross-tool navigation
  - `data-fc-q="Question text"` — question (no HTML, plain text)
  - `data-fc-a="Answer with <strong>bolded</strong> terms"` — answer (HTML allowed)
- **Required child elements**:
  - `<div class="mid-read-q">` (question display)
  - `<button class="mid-read-reveal">Reveal answer</button>`
  - `<div class="mid-read-a">` (answer container, initially hidden)
  - `<div class="mid-read-rate">` with three rate buttons: `data-rate="0"` (Hard), `data-rate="3"` (Good), `data-rate="5"` (Easy)
- **STARTER_DECK matching**: Each inline `<aside class="mid-read">` should have a corresponding entry in the Flashcards STARTER_DECK array. After completing the Book, the Flashcards Hub stat "Starter Cards" should equal the inline mid-read count + any non-mid-read seed cards.

#### Step 2.7: Replace MID_PROMPTS data
- In Script 3 (the last inline script), replace `var MID_PROMPTS = {...}`
- For each chapter, 2 prompts (CONTENT/JUDGMENT/PRIORITY mix — see PART 14.2 for the mid-prompt selection rubric)
- Every `after:` ID must reference a section ID that exists in the chapter
- This is SEPARATE from Step 2.6 inline mid-reads — both are required, neither replaces the other.

#### Step 2.8: Update storage key constants
- `STORAGE_KEY` → subject's book progress key
- `FC_KEY` → subject's flashcard schedule key
- `LAST_CH_KEY` → subject's last-chapter key
- `BOOKMARK_KEY` → subject's bookmarks key
- `NCLEX_DONE_KEY` → subject's NCLEX-done key

#### Step 2.9: Verify
- Open in browser at localhost
- Click each chapter — modal opens, all tabs render
- Check mid-prompts have colored borders (CONTENT/JUDGMENT/PRINCIPLE/PRIORITY)
- Test sidebar search
- Test print overlay (Brief mode + Deep mode)
- Test theme toggle
- Test bookmarks
- Test mobile view (DevTools 375px)
- Run `node --check` on each inline script

#### Phase 3: Build Templates file

#### Step 3.1: Copy MN Templates as starting template
- `cp "Elevated ATI MN Templates.html" "Elevated ATI {SUBJECT} Templates.html"`

#### Step 3.2: Update top-of-file metadata (same as Book)
- `<title>`, theme-color, apple-mobile-web-app-title
- ★ **THE TITLE TAG IS EASILY MISSED — VERIFY EXPLICITLY** ★

#### Step 3.3: Update CSS palette (same approach as Book)

#### Step 3.4: Update sidebar header text

#### Step 3.5: Replace template-pool contents
- For each template type (Basic Concept, System Disorder, etc.), build the example cards
- Each card: `<div class="example-card" id="ex-chN-{name}" data-mode="filled">` + header + grid + mode-toggle + content
- Cards should `data-ch` reference valid chapter numbers in subject
- Each card's `.ex-jump` href should point to the subject's Book file

#### Step 3.6: Update accordion section titles (template-section)
- Each `<section class="template-section">` should have subject-relevant cards

#### Step 3.7: Update sidebar tpl-group structures
- Sidebar shows the 8 type groups with example counts

#### Step 3.8: Update storage key constants
- `STORAGE_KEY` → `{prefix}_templates_progress` (canonical snake_case form)
- `STUDIED_KEY` → same key (used for both purposes)
- `LAST_TPL_KEY` → `{prefix}_last_template`

#### Step 3.9: Verify
- All cards visible, filter works, mode toggle works
- Click "→ Read in book" link → opens Book at correct chapter
- Theme toggle works
- Mobile view OK
- `node --check` all 4 scripts

#### Phase 4: Build Flashcards file

#### Step 4.1: Copy MN Flashcards as starting template

#### Step 4.2: Update top-of-file metadata (same as before)

#### Step 4.3: Update CSS palette (same approach)

#### Step 4.4: Update sidebar/hero text

#### Step 4.5: Replace STARTER_DECK array
- Build the array of starter cards for the subject (200+ cards typical)
- Each card: `{ id: 'fc-chN-{name}', ch: 'chN', type: '...', anchor: 'chN', q: '...', a: '...' }`
- IDs must be valid chapter numbers
- Total count should match Hub's "Starter Cards" stat

#### Step 4.6: Update chapter filter chips
- ★ **EXPAND FROM MN'S 27 TO SUBJECT'S CHAPTER COUNT** ★
- Add `<button class="filter-chip" data-value="N" type="button">N</button>` for each chapter

#### Step 4.7: Update type filter chips
- ★ **MUST INCLUDE ALL 7 TYPES** ★
- 3 inline: concept, calc, warning (lowercase)
- 4 typed: CONTENT, JUDGMENT, PRINCIPLE, PRIORITY (uppercase)

#### Step 4.8: Update unit filter chips
- Replace MN's 4 OB units with subject's units
- `data-value` slugs (kebab-case) + visible labels with chapter ranges

#### Step 4.9: Update chapterUnit() JS function
- Replace MN ranges with subject's ranges

#### Step 4.10: Update "Load N starter cards" button
- ★ **TWO PLACES — VISIBLE TEXT AND TITLE ATTRIBUTE** ★
- Search for "Load 122" / "the 122 starter" — replace 122 with subject count
- Both occurrences in static HTML (NOT inside `<script>`)

#### Step 4.11: Update sidebar quick-filter buttons
- Same unit-filter changes as the main chip filter
- Same chapter range

#### Step 4.12: Update storage key constants
- `THEME_KEY`, `FC_KEY`, `FILTER_STATE_KEY`, `SYNC_KEYS`

#### Step 4.13: Verify
- Each filter works
- "Load starter cards" loads the subject's cards (not MN's)
- Chapter filter goes up to subject's max chapter
- Type filter shows all 7 types
- Keyboard shortcuts work
- Theme toggle works
- `node --check` script

#### Phase 5: Build Hub file

#### Step 5.1: Copy MN Hub as starting template

#### Step 5.2: Update top-of-file metadata

#### Step 5.3: Update hero text (subject name)

#### Step 5.4: Update CSS palette

#### Step 5.5: Update stats row (5 stats)
- Chapters / Units / Templates / Types / Starter Cards
- All values should match what other files actually have

#### Step 5.6: Update units-grid
- One `.unit-card` per subject unit (3 for PD, 13 for Pharm)
- Each card: `.unit-num` + `<h3>` name + `.unit-range`

#### Step 5.7: Update subject card hrefs in primary-grid
- All "Open X" links point to subject's files
- Anchor links `#chN` reference valid chapters

#### Step 5.8: Update storage key constants
- `THEME_KEY`, `BOOK_KEY`, `TPL_KEY`, `FC_KEY`, `PICKUP_DISMISS_KEY`, `LAST_CH_KEY_HUB`, `LAST_TPL_KEY_HUB`
- `TPL_KEY` should use canonical `{prefix}_templates_progress`

#### Step 5.9: Update SYNC_KEYS array
- ★ **MUST INCLUDE EVERY KEY WRITTEN BY OTHER FILES** ★
- For PD that's 10 keys; for MN/Pharm shared namespace, calculate carefully

#### Step 5.10: Verify
- Click each subject card → opens correct file
- Pickup panel shows correct data (after using other files)
- Export backup → download JSON; Import → restore
- Theme toggle works
- Mobile view OK
- `node --check` script

#### Phase 6: Update index.html

- Add subject card if it's a new subject
- Update theme/accent variables for the new subject
- Verify subject-card[data-subject="..."] selector exists

#### Phase 7: Cross-subject integrity sweep

Run the sweep script (PART 13.12) plus the integrity sweep covering:
- File sizes reasonable
- JS lint passes on every inline script
- HTML tag balance
- No MN namespace leakage outside migration blocks (if subject uses isolated namespace)
- Hub SYNC_KEYS = exactly the set of keys written by other files
- All cross-file URL references resolve
- Accent color consistent across all 4 files
- All chapters/units/template counts match Hub stats

---

### 13.3 Per-subject variation table

This is the explicit list of every value that must be subject-specific. Use this as a checklist. If a porter forgets even one item, bugs ensue.

#### J.4.1 Per-subject CONSTANTS (centralizable)

```
Subject 2-letter code:      "mn" / "pd" / "pharm" / etc.
Subject display name:       "Maternal-Newborn" / "Pediatric" / "Pharmacology"
Subject short name:         "MN" / "PD" / "Pharm"
Namespace prefix:           "nur2460_" / "atipd_" / etc. (decides if shared with another subject)
Accent color (dark):        #fbbf24 / #38bdf8 / #fb923c
Accent color (light):       (lighter shade)
theme-color meta:           (darker shade than accent for mobile chrome)
Chapter count:              integer
Unit count:                 integer (and the unit boundaries)
Template count:             integer
Starter cards count:        integer
```

#### J.4.2 Per-subject TEXT (visible to user)

```
<title>                                  4 files × 1 each = 4 places
<meta name="apple-mobile-web-app-title"> 4 files × 1 each = 4 places
Sidebar header text                      Book, Templates × 1 each = 2 places
Hero h1 / subtitle text                  Book?, Templates?, Flashcards, Hub × 1 each
"Load N starter cards" button text       Flashcards static HTML
"Add the N starter cards" tooltip        Flashcards static HTML
"Open the X book" CTA                    Hub (subject cards) × 1
Print toolbar title                      Book, Templates × 1 each
```

#### J.4.3 Per-subject CSS values

```
:root --accent                           4 files
:root --accent2 (lighter)                4 files
:root --accent-soft (low-opacity)        4 files
:root --accent-stripe-bg                 4 files
[data-theme="light"] --accent            4 files (different shade)
[data-theme="light"] --accent2           4 files
[data-theme="light"] --accent-soft       4 files
[data-theme="light"] --accent-stripe-bg  4 files (or omit, falls back)
The 8 prompt-type vars in :root          Book, Flashcards (Templates doesn't use them)
The 8 prompt-type vars in [data-theme="light"]   same
```

#### J.4.4 Per-subject DATA STRUCTURES

```
ABBR_DICT                  Book, Templates (may include subject-specific terms)
MID_PROMPTS                Book Script 3 (subject-specific content + chapter coverage)
STARTER_DECK               Flashcards (subject-specific cards)
chapter-pool contents      Book (entire chapters worth of content)
template-pool contents     Templates (entire cards)
Sidebar nav-section/items  Book (matches chapter count + unit structure)
Planner unit-accordion/rows  Book (matches chapter count + unit structure)
Sidebar tpl-group/header   Templates (matches template count per type)
Stats values (5)            Hub
Units grid cards            Hub (matches subject's unit count + ranges)
Chapter filter chips        Flashcards (1 through chapter count)
Sidebar quick-filter (chapter) Flashcards (matches above)
Unit filter chips           Flashcards (matches Hub's units)
Sidebar quick-filter (unit) Flashcards (matches above)
chapterUnit() function     Flashcards (returns subject's unit slugs)
```

#### J.4.5 Per-subject STORAGE KEYS

For each file, the constants that need subject-correct values:

```
HUB
  THEME_KEY              "nur2460_theme" or "atipd_theme"
  BOOK_KEY               "{prefix}_atimn_progress" / "atipd_book_progress" / etc.
  TPL_KEY                "{prefix}_templates_progress"
  FC_KEY                 "nur2460_fc_schedule" or "atipd_fc_schedule"
  PICKUP_DISMISS_KEY     "{prefix}_pickup_dismissed"
  LAST_CH_KEY_HUB        "{prefix}_last_chapter"
  LAST_TPL_KEY_HUB       "{prefix}_last_template"
  SYNC_KEYS array        all of the above + bookmarks + nclex_done + fc_filters + tpl_filters

BOOK
  STORAGE_KEY            "{prefix}_atimn_progress" / "atipd_book_progress" / etc.
  FC_KEY                 same as Hub's
  LAST_CH_KEY            "{prefix}_last_chapter"
  BOOKMARK_KEY           "{prefix}_bookmarks"
  NCLEX_DONE_KEY         "{prefix}_nclex_done"

TEMPLATES
  STORAGE_KEY            "{prefix}_templates_progress"  ← canonical snake_case
  STUDIED_KEY            same as STORAGE_KEY
  LAST_TPL_KEY           "{prefix}_last_template"
  TPL_FILTER_KEY         "{prefix}_tpl_filters"

FLASHCARDS
  THEME_KEY              same as Hub's
  FC_KEY                 same as Hub's
  FILTER_STATE_KEY       "{prefix}_fc_filters"
  SYNC_KEYS              should match Hub's (or be a subset)
```

#### J.4.6 Per-subject FILTER UI (Flashcards only — most error-prone)

```
Chapter filter chips     N buttons, data-value="1" through "N"
Unit filter chips        Subject's units + "All"
Type filter chips        7 buttons: 3 inline + 4 typed (UNIVERSAL — same for every subject)
Sidebar chapter quick-filter buttons  same chapter range
Sidebar unit quick-filter buttons     same unit list

chapterUnit() function   Subject-specific ranges:
                         MN:    1-9, 10-16, 17-22, 23-27
                         PD:    1-11, 12-41, 42-44
                         Pharm: 1-6, 7-16, 17-18, 19-24, 25-27, 28-30, 31-32, 33-34, 35-38, 39-40, 41-42, 43-48, 49
```

---

### 13.4 Chapter completeness checklist

```
[ ] <section class="chapter" id="chN">
[ ]   <div class="chapter-banner"> with .chapter-meta + .chapter-name + .chapter-lede
[ ]   <section id="chN-tldr" class="brief-card"> with .tldr + .brief-grid (2 columns)
[ ]   <section id="chN-{topic}" class="content-section"> × 2-7
[ ]     Each has .section-lead + condition-blocks
[ ]     3-6 inline <aside class="mid-read"> distributed across sections (see PART 7.9 for density spec)
[ ]   <section id="chN-als" class="content-section"> (24/27 MN chapters, 18+ for PD)
[ ]   <section id="chN-exercises" class="content-section">
[ ]     5 .exercise articles with data-q-id="chN-qK"
[ ]   <section id="chN-templates" class="content-section tpl-bridge">
[ ]     <ul> with at least 1 cross-link
[ ] </section>
```

### 13.5 Validation script (Python)

```python
import re
from pathlib import Path

def validate_book(path):
    content = Path(path).read_text()
    issues = []

    # Tag balance
    if content.count('<div') != content.count('</div>'):
        issues.append(f"div imbalance: {content.count('<div')} open vs {content.count('</div>')} close")
    if content.count('<section') != content.count('</section>'):
        issues.append(f"section imbalance")

    # Chapter pool integrity
    pool_open = content.find('<div class="chapter-pool"')
    if pool_open == -1:
        issues.append("No chapter-pool found")
        return issues

    # Walk div depth from pool
    depth = 0; i = pool_open; pool_close = -1
    while i < len(content):
        if content[i:i+4] == '<div':
            depth += 1; i = content.find('>', i) + 1
        elif content[i:i+6] == '</div>':
            depth -= 1; i += 6
            if depth == 0: pool_close = i; break
        else: i += 1

    if pool_close == -1:
        issues.append("Pool never closes")
    else:
        pool_content = content[pool_open:pool_close]
        chapters_in_pool = len(re.findall(r'<section class="chapter" id="ch\d+">', pool_content))
        chapters_total = len(re.findall(r'<section class="chapter" id="ch\d+">', content))
        if chapters_in_pool != chapters_total:
            issues.append(f"Only {chapters_in_pool}/{chapters_total} chapters inside the pool")

    # Each chapter has required sub-sections
    for ch_match in re.finditer(r'<section class="chapter" id="(ch\d+)">', content):
        ch_id = ch_match.group(1)
        ch_end = content.find('</section><!--', ch_match.end())
        if ch_end == -1:
            # Walk balanced section depth
            depth = 1; i = ch_match.end()
            while i < len(content) and depth > 0:
                next_open = content.find('<section', i)
                next_close = content.find('</section>', i)
                if next_close == -1: break
                if next_open != -1 and next_open < next_close:
                    depth += 1; i = next_open + 8
                else:
                    depth -= 1; i = next_close + 10
                    if depth == 0: ch_end = next_close
        if ch_end == -1: continue

        ch_content = content[ch_match.start():ch_end]
        required = [f'{ch_id}-tldr', f'{ch_id}-exercises', f'{ch_id}-templates']
        for r in required:
            if r not in ch_content:
                issues.append(f"{ch_id}: missing {r}")

    return issues
```

### 13.6 JS lint check

```bash
# Extract each script block and lint with node --check
python3 -c "
import re, subprocess, tempfile
with open('Elevated ATI MN Book.html') as f: content = f.read()
scripts = re.findall(r'<script>(.*?)</script>', content, re.DOTALL)
for i, s in enumerate(scripts):
    with tempfile.NamedTemporaryFile('w', suffix='.js', delete=False) as tf:
        tf.write(s); tf.flush()
        r = subprocess.run(['node', '--check', tf.name], capture_output=True, text=True)
        if r.returncode != 0: print(f'Script {i+1} ERROR:', r.stderr)
        else: print(f'Script {i+1}: OK')
"
```

### 13.7 What NOT to do

- **Don't put chapter content outside the chapter-pool.** It will render as visible page text.
- **Don't put `<section>` elements at the top level of the chapter (with IDs).** Only direct children of `.chapter` become tabs.
- **Don't use `<aside>` as a tab.** Only `<section>`. Mid-read prompts use `<aside class="mid-read">` because they're inline, not tabs.
- **Don't forget the `tpl-bridge` class on the templates section.** Without it, the tab label will be the truncated h2 instead of "Templates".
- **Don't use `html.light` instead of `[data-theme="light"]`.** The selector is an attribute, not a class.
- **Don't put script ordering wrong.** Main IIFE, then NCLEX, then mid-prompts.

### 13.8 Porting-leak categories

When a file is copy-pasted from one subject to another, leaks typically come from these categories:

1. **Hardcoded chapter ranges** — `Ch 1-27` (MN) vs `Ch 1-44` (PD)
2. **Hardcoded starter counts** — `122` (MN) vs `188` (PD) vs whatever Pharm becomes
3. **Hardcoded unit names** — "Antepartum, Intrapartum, Postpartum, Newborn" (MN) vs PD's 3 units vs Pharm's 13
4. **Hardcoded chapter→unit mapping function** — JS function returns `'antepartum'` for MN; must return PD/Pharm equivalents
5. **`<title>` tag** — browser tab; very visible but easy to miss
6. **Meta tags** — `theme-color`, `description`, `apple-mobile-web-app-title`
7. **localStorage keys** — `nur2460_*` vs `atipd_*` namespace mismatches
8. **SYNC_KEYS array** — what gets exported in backup
9. **Type filter chips** — must match what data structures actually emit (e.g., Flashcards filter must include CONTENT/JUDGMENT/PRINCIPLE/PRIORITY if Book has typed mid-prompts)
10. **Cross-file href URLs** — every `Elevated%20ATI%20XXX%20*.html` must point to a file that exists
11. **Hub stats display** — chapter count, unit count, template count, starter cards count
12. **Hub units-grid** — number and ranges of unit cards
13. **CSS `--accent` value** — should match across all 4 files
14. **Subject name in heading text** — "Maternal-Newborn" vs "Pediatric" vs "Pharmacology"
15. **Mid-read prompt CSS variables** — `--prompt-content`, etc. (8 variables)
16. **MID_PROMPTS data** — every prompt must be subject-relevant, not copy of source subject
17. **ALS sections** — must be from the correct PDF and present per chapter where source has one
18. **Chapter filter buttons** — numeric chips 1-N must match chapter count
19. **Quick-filter sidebar buttons** — same chapter range plus unit-specific buttons
20. **MID_PROMPTS `after:` anchors** — must reference section IDs that exist in the new Book

---

### 13.9 Per-file leak inventory

For each file, the exhaustive list of values that need subject-specific updating.

#### I.2.1 Hub leaks

```
LOCATION                            SOURCE VALUE        TARGET VALUE
─────────────────────────────────   ─────────────────   ───────────────────
<title>                              MN title            PD/Pharm title
<meta name="theme-color">            MN amber            PD blue / Pharm orange
<meta name="apple-mobile-web-app-title">  MN              Subject name
:root --accent                       #fbbf24             #38bdf8 / #fb923c
:root --accent2                      MN lighter          Subject lighter
:root --accent-soft                  MN soft             Subject soft
:root --accent-stripe-bg             MN stripe           Subject stripe
hero h1 subject name                 "Maternal..."       "Pediatric..." / "Pharm..."
hero subtitle/description            MN-specific         Subject-specific
.stat-value × 5                      27/4/105/8/122      44/3/167/8/188 (PD)
.stat-label × 5                      identical           identical (don't change labels)
.unit-card data-unit values          unit1-4             foundations/system-disorders/etc
.unit-num × N                        "Unit 1-4"          "Unit 1-3" / "Unit 1-13"
.unit-card h3 names                  MN unit names       Subject unit names
.unit-range × N                      MN chapter ranges   Subject chapter ranges
href "PD Book"/"PD Templates"/"PD Flashcards"  MN paths  Subject filename paths
href chapter anchors                 #ch1-27             #ch1-44 / #ch1-49
Subject-card "Open" subtitle text   "27 chapters..."    "44 chapters..." / "49 chapters..."
var THEME_KEY                        nur2460_theme       atipd_theme / nur2460_theme*
var BOOK_KEY                         nur2460_atimn_*     atipd_book_progress
var TPL_KEY                          nur2460_atimnTpl_*  atipd_templates_progress (snake_case!)
var FC_KEY                           nur2460_fc_schedule atipd_fc_schedule / nur2460_fc_schedule*
var PICKUP_DISMISS_KEY               nur2460_pickup_*    atipd_pickup_dismissed
var SYNC_KEYS array                  4 keys for MN       10 keys for PD (complete list)
LAST_CH_KEY_HUB                      nur2460_last_*      atipd_last_chapter
LAST_TPL_KEY_HUB                     nur2460_last_*      atipd_last_template

*Some keys are intentionally shared across MN+Pharm (per F.2.1 namespace decision).
```

#### I.2.2 Book leaks

```
LOCATION                            SOURCE VALUE        TARGET VALUE
─────────────────────────────────   ─────────────────   ───────────────────
<title>                              MN title            Subject title
<meta name="theme-color">            MN amber            Subject color
<meta name="apple-mobile-web-app-title">  MN             Subject name
:root --accent + 28 other vars       MN palette          Subject palette
:root :8 prompt-type vars (4 colors + 4 bgs)  ALWAYS NEEDED — same values across subjects
[data-theme="light"] vars            MN light palette    Subject light palette
Sidebar header text                  "MN" or "Maternal"  Subject abbreviation
nav-section x4                       MN units            Subject units (varies)
nav-section h3 names                 MN unit names       Subject unit names
.sidebar-item × N                    27 items            44 items (PD) / 49 (Pharm)
.unit-accordion × 4                  MN units            Subject units
planner-row × N                      27 rows             44 rows (PD) / 49 (Pharm)
.chapter sections × N                MN chapters         Subject chapters
chapter-banner per chapter           MN-content          Subject-content
chN-tldr per chapter                 MN-content          Subject-content
chN-{topic} sections per chapter     MN-content          Subject-content (most labor)
chN-als per chapter                  MN ALS from PDF     Subject ALS from PDF (NOT MN!)
chN-exercises per chapter            MN questions        Subject questions (NOT MN!)
chN-templates bridge per chapter     MN template links   Subject template links
MID_PROMPTS data                     MN 54 prompts       Subject N prompts (49 → 98 for Pharm)
MID_PROMPTS after: anchors           MN section IDs      Subject section IDs (different!)
const ABBR_DICT                      MN 277 entries      Subject N entries (may differ)
var STORAGE_KEY                      nur2460_atimn_*     atipd_book_progress / nur2460_atipharm_*
var FC_KEY                           nur2460_fc_schedule atipd_fc_schedule / nur2460_fc_schedule*
var LAST_CH_KEY                      nur2460_last_*      atipd_last_chapter
var BOOKMARK_KEY                     nur2460_bookmarks   atipd_bookmarks
var NCLEX_DONE_KEY                   nur2460_nclex_*     atipd_nclex_done
Print toolbar title                  MN-specific         Subject-specific
```

#### I.2.3 Templates leaks (these are commonly missed!)

```
LOCATION                            SOURCE VALUE        TARGET VALUE
─────────────────────────────────   ─────────────────   ───────────────────
<title>                              MN title (!!!)       Subject title
                                     ▲ MISSED IN PD INITIAL PORT - shows wrong tab name
<meta name="theme-color">            MN amber            Subject color
<meta name="apple-mobile-web-app-title">  MN              Subject name
:root --accent + palette             MN                  Subject
:root --accent-stripe-bg             MN/teal default     Subject value (see I.4)
Sidebar header subject name          MN                  Subject name
.template-section × 8                Generic OK          Generic OK (no subject value)
example-card per type                MN templates        Subject templates (different cards!)
example-card data-ch values          ch1-27 only         ch1-44 / ch1-49
.ex-jump href values                 → MN Book           → Subject Book
.template-pool tot count             105 (MN)            167 (PD) / TBD (Pharm)
Filter chapter ranges in chips       ch1-27              Actual subject range
JS quick-filter functions            MN logic            Subject logic
var STORAGE_KEY                      nur2460_atimnTpl_*  atipd_templates_progress  ← snake_case!
                                     ▲ NOT atipd_atimnTemplates_progress (hybrid bug)
                                     ▲ NOT atipd_tpl_progress (PD Hub had this!)
var STUDIED_KEY                      same                same
LAST_TEMPLATE_KEY                    nur2460_last_*      atipd_last_template
Cross-link to Hub                    MN Hub              Subject Hub
Cross-link to Book                   MN Book             Subject Book
```

#### I.2.4 Flashcards leaks (these are commonly missed!)

```
LOCATION                            SOURCE VALUE        TARGET VALUE
─────────────────────────────────   ─────────────────   ───────────────────
<title>                              MN title             Subject title
<meta name="theme-color">            MN amber            Subject color
<meta name="apple-mobile-web-app-title">  MN              Subject name
:root --accent + palette             MN                  Subject
:root :8 prompt-type vars            REQUIRED            REQUIRED (same values)
Sidebar header subject name          MN                  Subject name
Hero h1 subject name                 MN-specific         Subject-specific

CHAPTER FILTER CHIPS RANGE           1-27 (MN)           1-44 (PD) / 1-49 (Pharm)
                                     ▲ MISSED IN PD INITIAL PORT — chs 28-44 unfilterable

TYPE FILTER CHIPS                    3 inline types only Should include CONTENT/JUDGMENT/
                                                         PRINCIPLE/PRIORITY (typed mid-prompts)
                                     ▲ MISSED IN PD INITIAL PORT — typed prompts unfilterable

UNIT FILTER CHIPS                    4 MN units          3 PD units / N Pharm units
Unit filter chip data-value values   antepartum etc      foundations / system-disorders / etc
Unit filter chip labels              MN names + ranges   Subject names + ranges
Sidebar quick-filter buttons (unit)  4 MN buttons        Subject N buttons (same as above)

CHAPTER→UNIT MAPPING JS FUNCTION     MN ranges           Subject ranges
  function chapterUnit(chNum){
    if (n>=1&&n<=9) return 'antepartum';                 if (n>=1&&n<=11) return 'foundations';
    ...                                                  ...
  }
                                     ▲ MUST UPDATE — filters break without this

LOAD STARTER CARDS BUTTON
  - Visible button text "Load 122"   122 (MN hardcoded)  188 (PD) / TBD (Pharm)
                                     ▲ MISSED IN PD INITIAL PORT — shows wrong number
  - title attribute "Add the 122"    122 (MN hardcoded)  188 (PD) / TBD (Pharm)
                                     ▲ ALSO MISSED — tooltip shows wrong number
  - empty-state dynamic version       STARTER_DECK.length OK (JS-evaluated)

STARTER_DECK array contents          MN flashcards       Subject flashcards (different IDs!)
                                                         IDs use fc-chN-{topic} pattern
                                                         All chapter numbers must exist in
                                                         Subject Book

var THEME_KEY                        nur2460_theme       atipd_theme / nur2460_theme*
var FC_KEY                           nur2460_fc_schedule atipd_fc_schedule / nur2460_fc_schedule*
var FILTER_STATE_KEY                 nur2460_fc_filters  atipd_fc_filters
var SYNC_KEYS array                  4 MN keys           Subject keys (varies)
```

---

### 13.10 Porting checklist (run for every new subject)

When building or porting a subject suite, run through this checklist file-by-file. Tick each item as verified.

#### Hub
- [ ] `<title>` updated
- [ ] All meta tags updated (theme-color, description, apple-mobile-web-app-title)
- [ ] `:root` palette has subject `--accent` value
- [ ] `:root` has subject `--accent-stripe-bg` matching accent
- [ ] Hero h1 / subtitle / description show subject name (not source subject)
- [ ] All 5 stat values reflect subject's actual counts (chapters, units, templates, types, starter cards)
- [ ] `.unit-card` count matches subject's unit count
- [ ] `.unit-num`, `<h3>`, `.unit-range` text matches subject's units
- [ ] `.unit-card data-unit` slugs match subject (no `antepartum` if not MN)
- [ ] All `href` to other subject files use correct filenames (verify each exists)
- [ ] All anchor links `#chN` reference chapters that exist
- [ ] All `*_KEY` variables use correct namespace
- [ ] `SYNC_KEYS` includes EVERY key written by Book/Templates/Flashcards (no orphans)
- [ ] `chapterUnit()` JS function (if Hub has one) has subject's ranges

#### Book
- [ ] `<title>` updated
- [ ] All meta tags updated
- [ ] All 29 CSS variables present, 8 prompt-type ones not missing
- [ ] Light theme has all 29+ variables too
- [ ] Sidebar header shows subject name
- [ ] `.nav-section` count = unit count for subject
- [ ] Each `.nav-section <h3>` matches subject's unit name
- [ ] `.sidebar-item` count = chapter count for subject
- [ ] `.unit-accordion` and `.planner-row` counts match
- [ ] Every chapter has banner + TL;DR + relevant content sections + ALS (if PDF has one) + exercises + templates bridge
- [ ] All MID_PROMPTS entries reference valid section IDs in their chapter (use `after:`)
- [ ] All MID_PROMPTS content is subject-relevant (spot-check ch1, mid, last)
- [ ] All ALS content is from the SUBJECT's PDF (not source subject)
- [ ] All exercise Q&A is subject-relevant
- [ ] `STORAGE_KEY`, `FC_KEY`, `LAST_CH_KEY`, `BOOKMARK_KEY`, `NCLEX_DONE_KEY` use correct namespace
- [ ] Print toolbar title shows subject name

#### Templates
- [ ] `<title>` updated   ← **EASILY MISSED**
- [ ] All meta tags updated
- [ ] :root palette has subject values
- [ ] Sidebar header shows subject name
- [ ] All `example-card` are subject-relevant
- [ ] All `.ex-jump` href values point to subject Book
- [ ] All `data-ch` values are valid chapters in subject
- [ ] Filter chapter range matches subject
- [ ] `STORAGE_KEY` / `STUDIED_KEY` use canonical name `{prefix}_templates_progress` (NOT `_atisubjectTemplates_progress` and NOT `_tpl_progress`)
- [ ] Cross-link to Hub and Book uses correct filenames

#### Flashcards
- [ ] `<title>` updated
- [ ] All meta tags updated
- [ ] :root palette has subject values
- [ ] :root has 8 prompt-type CSS vars
- [ ] Sidebar/hero shows subject name
- [ ] **Chapter filter chips** range 1 to subject's chapter count (e.g., 1-44 for PD, not 1-27 MN)   ← **EASILY MISSED**
- [ ] **Type filter chips** include both inline types AND typed mid-prompt types if Book has them
  - Inline: concept, calc, warning
  - Typed: CONTENT, JUDGMENT, PRINCIPLE, PRIORITY
  - ← **EASILY MISSED**
- [ ] Unit filter chips match subject's units (count, data-value slugs, labels with chapter ranges)
- [ ] Sidebar unit quick-filter buttons match the chip filter
- [ ] `chapterUnit()` JS function returns subject's unit slugs for subject's chapter ranges
- [ ] **"Load N starter cards" button**: visible text + title attribute use ACTUAL subject count, not source subject's hardcoded number   ← **EASILY MISSED**
- [ ] STARTER_DECK contents are subject-relevant cards with valid `ch:` values
- [ ] STARTER_DECK length matches Hub's "Starter Cards" stat
- [ ] `THEME_KEY`, `FC_KEY`, `FILTER_STATE_KEY` use correct namespace
- [ ] `SYNC_KEYS` matches Hub's `SYNC_KEYS`

---

### 13.11 Static vs dynamic gotcha

A specific class of bug: a button or label LOOKS like it has a dynamic count via `' + STARTER_DECK.length + '`, but lives in STATIC HTML where that string isn't evaluated by JavaScript. The user sees the literal text `' + STARTER_DECK.length + '` in the UI.

#### How to identify

1. Open the file in a browser. Look at the button/label.
2. If you see `' + STARTER_DECK.length + '` as visible text → it's in static HTML. **Bug.**
3. If you see a NUMBER (correct or incorrect) → it's either:
   - Static HTML with hardcoded number (fix: hardcode the right number)
   - Static HTML with a JS-inserted number (fix: ensure JS injection ran)
   - JS-built innerHTML (correct as long as the string concatenation is inside a JS string literal)

#### Reliable rules

- **Inside `<script>...</script>` tag** → string concatenation IS evaluated.
- **Inside HTML attribute (e.g., `title="..."`)** → string concatenation is NOT evaluated; visible literal text.
- **Inside HTML body text** → string concatenation is NOT evaluated.

#### Solution patterns

**Option A — hardcode the subject's value** (simplest, works fine since file is per-subject):
```html
<span>Load 188 starter cards</span>
```

**Option B — JS injection on DOM ready**:
```javascript
document.querySelectorAll('[data-fill-starter-count]').forEach(el => {
  el.textContent = el.textContent.replace('{N}', STARTER_DECK.length);
});
```
With HTML:
```html
<span data-fill-starter-count>Load {N} starter cards</span>
```

**Option C — innerHTML build** (use only if button is dynamically rebuilt anyway):
```javascript
stage.innerHTML = '<button>Load ' + STARTER_DECK.length + ' starter cards</button>';
```

PD Flashcards uses Option C inside `stage.innerHTML = ...` for the empty-state button, AND Option A for the top deck-actions button (hardcoded 188). Both are valid; mixing them is fine.

---

### 13.12 Sweep script — detect this class of bug

Run before finalizing each subject's port:

```python
"""Detect porting leaks in a built subject suite"""
import re

SUBJECT = 'pd'  # or 'pharm' or whatever
FILES = {
    'Hub':        f'/path/to/Elevated ATI {SUBJECT.upper()} Hub.html',
    'Book':       f'/path/to/Elevated ATI {SUBJECT.upper()} Book.html',
    'Templates':  f'/path/to/Elevated ATI {SUBJECT.upper()} Templates.html',
    'Flashcards': f'/path/to/Elevated ATI {SUBJECT.upper()} Flashcards.html',
}
# Subject's expected counts
EXPECTED = {
    'chapter_count': 44,    # PD
    'unit_count': 3,        # PD
    'starter_count': 188,   # PD
    'subject_name_in_title': 'Pediatric',
    'source_subject_name': 'Maternal-Newborn',  # MN — should NOT appear in titles
    'source_chapter_max': 27,  # MN's chapter count — shouldn't be a hardcoded range
}

bugs = []
for name, path in FILES.items():
    with open(path) as f:
        c = f.read()
    
    # 1. Title tag
    m = re.search(r'<title>([^<]+)</title>', c)
    if m and EXPECTED['source_subject_name'] in m.group(1):
        bugs.append(f"{name}: <title> contains source subject name: {m.group(1)}")
    if m and EXPECTED['subject_name_in_title'] not in m.group(1):
        bugs.append(f"{name}: <title> missing subject name: {m.group(1)}")
    
    # 2. Hardcoded source counts in visible text (not CSS)
    # Look for "Load <number> starter" — should match expected starter_count
    for m in re.finditer(r'>Load (\d+) starter cards<', c):
        if int(m.group(1)) != EXPECTED['starter_count']:
            bugs.append(f"{name}: 'Load {m.group(1)} starter cards' should be {EXPECTED['starter_count']}")
    for m in re.finditer(r'title="Add the (\d+) starter cards', c):
        if int(m.group(1)) != EXPECTED['starter_count']:
            bugs.append(f"{name}: tooltip 'Add the {m.group(1)}' should be {EXPECTED['starter_count']}")
    
    # 3. Chapter filter chips in Flashcards
    if 'Flashcards' in name:
        m = re.search(r'<div class="filter-chips filter-chips-numeric" data-filter-group="chapter"[^>]*>(.*?)</div>', c, re.DOTALL)
        if m:
            chips = re.findall(r'data-value="(\d+)"', m.group(1))
            if len(chips) != EXPECTED['chapter_count']:
                bugs.append(f"{name}: chapter filter has {len(chips)} chips, expected {EXPECTED['chapter_count']}")
            if chips and int(chips[-1]) != EXPECTED['chapter_count']:
                bugs.append(f"{name}: chapter filter ends at {chips[-1]}, should end at {EXPECTED['chapter_count']}")
    
    # 4. Type filter completeness in Flashcards
    if 'Flashcards' in name:
        m = re.search(r'<div class="filter-chips" data-filter-group="type"[^>]*>(.*?)</div>', c, re.DOTALL)
        if m:
            types = re.findall(r'data-value="([^"]+)"', m.group(1))
            for required in ['concept', 'calc', 'warning', 'CONTENT', 'JUDGMENT', 'PRINCIPLE', 'PRIORITY']:
                if required not in types:
                    bugs.append(f"{name}: type filter missing '{required}'")
    
    # 5. Unstevaluated template-string leak (e.g. literal "' + X +'" in HTML)
    if "' + STARTER_DECK.length + '" in c:
        # Make sure all instances are inside <script>...</script>
        for m in re.finditer(r"' \+ STARTER_DECK\.length \+ '", c):
            pos = m.start()
            so = c.rfind('<script>', 0, pos)
            sc = c.rfind('</script>', 0, pos)
            if so <= sc:  # not inside script
                bugs.append(f"{name}: unevaluated JS template at pos {pos} (literal '{m.group(0)}' would show to user)")

if bugs:
    print(f"❌ {len(bugs)} bug(s) found:")
    for b in bugs:
        print(f"  - {b}")
else:
    print("✓ All checks pass")
```

Save this as `port_check.py` and run after every port-batch.

---

### 13.13 Quality Assurance Checklists

> *Consolidated from former Addendum B.6.*

#### B.6.1 Per-chapter QA checklist

Run this for every chapter before considering it done:

```
STRUCTURE
[ ] <section class="chapter" id="chN"> exists and is unique
[ ] <div class="chapter-banner"> with .chapter-meta + .chapter-name + .chapter-lede
[ ] <section id="chN-tldr" class="brief-card"> present
[ ] All content-sections have unique chN-{topic} IDs
[ ] <section id="chN-als" class="content-section"> if ALS exists in source
[ ] <section id="chN-exercises" class="content-section"> present
[ ] <section id="chN-templates" class="content-section tpl-bridge"> present
[ ] <div> tag balance: open count = close count
[ ] <section> tag balance: open count = close count
[ ] All inner <section> elements are direct children of .chapter (none nested)

CONTENT
[ ] TL;DR lead paragraph: 1-3 sentences, formulaic voice (A.1.2)
[ ] TL;DR brief-grid: 2 columns, 3-6 bullets each, bolded keys
[ ] Each content-section has .section-lead (1-2 sentences)
[ ] Each condition-block: header (with name + tag) + body + finding-grid
[ ] Finding-card headings: 1-3 word noun phrases
[ ] No placeholder text (TODO, TBD, Lorem, FIXME)
[ ] No "It is important to..." / "The nurse should consider..."

ALS (if present)
[ ] Scenario block: italicized prompt + 3 bulleted sub-questions
[ ] Answer key block: finding-cards + kb-card for nursing interventions
[ ] References ATI Active Learning Template type by name

EXERCISES
[ ] Exactly 5 exercises with data-q-id="chN-qK"
[ ] At least 3 NCLEX categories represented across the 5
[ ] 1-2 SATA questions (not 0, not 5)
[ ] Every option (A/B/C/D) has a rationale
[ ] NCLEX tag uses "NCLEX · Category · Subcategory" format
[ ] Question stems follow standard patterns (A.3.3)
[ ] Distractors are plausible and diverse (A.3.4)

MID-PROMPTS
[ ] Exactly 2 entries in MID_PROMPTS["chN"]
[ ] Types follow selection rubric (A.2.2-A.2.3)
[ ] `after` field points to a section that exists in chapter
[ ] Both prompts on same section only if chapter is short
[ ] Question stems match type (A.1.7)
[ ] Answers lead with action/answer, then rationale

INLINE MID-READS
[ ] 1+ <aside class="mid-read"> per ~200-400 words of body
[ ] Each has data-fc-id, data-fc-ch, data-fc-type, data-fc-anchor, data-fc-q, data-fc-a
[ ] Type is "concept", "warning", or "calc"
[ ] data-fc-anchor matches a section ID in the chapter

CROSS-LINKS
[ ] chN-templates lists every template that bridges to this chapter
[ ] Each <li><a> in templates bridge has correct hash anchor
[ ] If 0 templates bridge, use explanatory copy (not empty <ul>)

ABBR
[ ] All abbreviations used appear in ABBR_DICT
[ ] No new acronym introduced without dictionary entry
```

#### B.6.2 Per-suite QA checklist

After all chapters are done, run this for the whole suite:

```
FILES
[ ] 5 files present: index.html, Hub, Book, Templates, Flashcards
[ ] Filenames use exact case and spaces (URL-encoded as %20 in hrefs)
[ ] All 5 files load without console errors
[ ] All 5 files use same Google Fonts loader

CONSISTENCY
[ ] Same theme-color meta value across subject files
[ ] Same --accent palette across subject files
[ ] LocalStorage prefix consistent (nur2460_ vs atipd_)
[ ] Same ABBR_DICT or correctly-merged dictionary
[ ] Same versions of shared functions (SM-2, applyThemeUI, etc.)

NAVIGATION
[ ] Hub → Book → chapter modal works
[ ] Hub → Templates → example modal works
[ ] Hub → Flashcards → review works
[ ] Back-home button works from all 3 tools
[ ] Mobile hamburger works at 375px width
[ ] Mobile floating back-home button works
[ ] Theme toggle persists across all 5 files

CROSS-TOOL SYNC
[ ] Open chapter ch3-als in Book → return to Hub → pickup panel shows ch3
[ ] Rate a mid-prompt in Book → open Flashcards → card appears in queue
[ ] Bookmark a section in Book → bookmarks button shows count → click bookmark → modal opens
[ ] View an example in Templates → return to Hub → pickup shows that example

STORAGE
[ ] Export backup produces valid JSON
[ ] Import backup restores all keys
[ ] Reset all progress clears only subject's keys (not other subjects)
[ ] Storage panel lists all subject-prefixed keys with sizes

PRINT
[ ] Print Brief from Hub generates 1 page per chapter TL;DR
[ ] Print Deep from Hub generates full chapter content
[ ] Print per-unit button works from Book main page
[ ] Print preview shows clean layout (no sidebar, no buttons)

PROGRESS
[ ] Mark chapters as Reviewed/Complete in Book
[ ] Hub primary-grid Book card shows correct % and count
[ ] Unit cards on Hub show correct per-unit progress
[ ] Templates studied checkbox updates Templates progress bar

ACCESSIBILITY
[ ] All buttons have aria-label or visible text
[ ] All form inputs have <label> or aria-label
[ ] Modal has role="dialog" and aria-labelledby
[ ] Keyboard navigation works for sidebar items
[ ] Tab order is logical
[ ] Focus visible (default browser focus rings preserved)

PERFORMANCE
[ ] Book file under 2 MB (gzip-served by GitHub Pages)
[ ] No console errors on load
[ ] First Contentful Paint under 2s on mobile
[ ] Modal open under 200ms

CONTENT INTEGRITY
[ ] All chapters have exactly the expected sections (per B.6.1)
[ ] No duplicate chapter IDs
[ ] No duplicate example IDs in Templates
[ ] No flashcard ID collisions in shared schedules
[ ] All cross-links resolve (no 404s)
[ ] No "TODO" / "Lorem" / "FIXME" anywhere
```

#### B.6.3 Validation script for B.6.1

```python
#!/usr/bin/env python3
"""Run per-chapter QA against a Book file."""
import re
import sys
from pathlib import Path

def qa_check_chapter(book_path, chapter_num):
    content = Path(book_path).read_text()
    ch_id = f'ch{chapter_num}'
    issues = []

    # Locate chapter
    match = re.search(rf'<section class="chapter" id="{ch_id}">', content)
    if not match:
        return [f"Chapter {ch_id} not found"]
    start = match.start()
    # Walk to matching </section>
    depth = 1; i = match.end(); end = -1
    while i < len(content) and depth > 0:
        n_open = content.find('<section', i)
        n_close = content.find('</section>', i)
        if n_close == -1: break
        if n_open != -1 and n_open < n_close:
            depth += 1; i = n_open + 8
        else:
            depth -= 1; i = n_close + 10
            if depth == 0: end = n_close
    if end == -1:
        return [f"Chapter {ch_id} has unbalanced <section>"]
    ch_html = content[start:end]

    # Required sections
    required = [f'{ch_id}-tldr', f'{ch_id}-exercises', f'{ch_id}-templates']
    for r in required:
        if r not in ch_html:
            issues.append(f"Missing required section: {r}")

    # ALS is optional but worth noting
    if f'{ch_id}-als' not in ch_html:
        issues.append(f"NOTE: No {ch_id}-als (acceptable if source PDF has no ALS)")

    # Banner
    if 'chapter-banner' not in ch_html:
        issues.append("Missing chapter-banner")
    if 'chapter-meta' not in ch_html:
        issues.append("Missing chapter-meta")
    if 'chapter-name' not in ch_html:
        issues.append("Missing chapter-name")
    if 'chapter-lede' not in ch_html:
        issues.append("Missing chapter-lede")

    # Brief-card structure
    if 'brief-grid' not in ch_html:
        issues.append("TL;DR missing brief-grid")

    # Exercise count
    exercises = re.findall(r'<article class="exercise"', ch_html)
    if len(exercises) != 5:
        issues.append(f"Expected 5 exercises, found {len(exercises)}")

    # NCLEX tags
    nclex_tags = re.findall(r'<span class="nclex-tag">[^<]+</span>', ch_html)
    if len(nclex_tags) < 5:
        issues.append(f"Expected 5+ NCLEX tags, found {len(nclex_tags)}")

    # Categories diversity
    categories = set()
    for tag in nclex_tags:
        parts = tag.split('·')
        if len(parts) >= 2:
            categories.add(parts[1].strip())
    if len(categories) < 3:
        issues.append(f"Only {len(categories)} NCLEX categories (want 3+): {categories}")

    # Placeholder text check
    placeholders = ['TODO', 'Lorem', 'FIXME', 'TBD', 'Placeholder']
    for p in placeholders:
        if p in ch_html:
            issues.append(f"Contains placeholder: '{p}'")

    # Bad voice patterns
    bad_voice = [
        'It is important to',
        'The nurse should consider',
        'There are several factors',
        'It should be noted that',
    ]
    for v in bad_voice:
        if v in ch_html:
            issues.append(f"Voice issue: contains '{v}'")

    # Div balance within chapter
    if ch_html.count('<div') != ch_html.count('</div>'):
        issues.append(f"Div imbalance: {ch_html.count('<div')} open, {ch_html.count('</div>')} close")

    # Inner section balance
    inner_open = len(re.findall(r'<section[^>]*>', ch_html)) - 1  # subtract outer
    inner_close = ch_html.count('</section>') - 1                 # subtract outer
    if inner_open != inner_close:
        issues.append(f"Inner section imbalance: {inner_open} open, {inner_close} close")

    return issues

if __name__ == '__main__':
    book = sys.argv[1] if len(sys.argv) > 1 else 'Elevated ATI MN Book.html'
    max_ch = int(sys.argv[2]) if len(sys.argv) > 2 else 27
    all_clean = True
    for n in range(1, max_ch + 1):
        issues = qa_check_chapter(book, n)
        real_issues = [i for i in issues if not i.startswith('NOTE:')]
        if real_issues:
            all_clean = False
            print(f"\nch{n}:")
            for i in issues:
                print(f"  {i}")
        elif issues:  # only NOTEs
            print(f"ch{n}: clean ({len(issues)} note{'s' if len(issues) != 1 else ''})")
        else:
            print(f"ch{n}: ✓ clean")
    if all_clean:
        print(f"\n✓ All {max_ch} chapters passed QA")
        sys.exit(0)
    else:
        sys.exit(1)
```

Usage:
```bash
python3 qa_check.py "Elevated ATI MN Book.html" 27
```

#### B.6.4 Pre-deployment final pass

Before pushing to sleepyius.github.io/NUR2460:

```
[ ] Run B.6.3 script on all 3 subject Book files
[ ] Open each Hub, click pickup panel, verify it works
[ ] Open each tool on a mobile device or DevTools mobile emulator
[ ] Test theme toggle on every page
[ ] Test search on every Book
[ ] Test filter chips on every Templates
[ ] Test keyboard shortcuts on Flashcards (Space, 1, 2, 3, ?)
[ ] Test print Brief and Deep
[ ] Test export → reset → import round trip
[ ] Test bookmarks: add 5, close panel, reopen, verify all 5 present
[ ] Test cross-tool sync: rate a card in Book, see it in Flashcards
[ ] Check console for errors in production build
[ ] Verify Google Fonts loads (check Network tab)
[ ] Verify favicon and meta tags
[ ] Verify all 5 files are committed and pushed
```

---

### 13.14 Pdf Extraction Tooling (Reference)

> *Consolidated from former Addendum C.2.*

#### C.2.1 Library selection

For ATI PDFs (which are heavily formatted, multi-column, table-rich), use **pdfplumber** > pypdf > pdfminer.

```bash
pip install pdfplumber
```

**Why pdfplumber:**
- Better table detection than pypdf
- Preserves column order on multi-column pages
- Returns coordinates so you can post-process by region

**Fallback:** pypdf is simpler for text-only chapters but mangles tables.

**Don't use:** OCR libraries (Tesseract) for ATI PDFs — the source PDFs have selectable text, not scanned images. OCR introduces errors where none exist.

#### C.2.2 Chapter boundary detection

ATI chapter starts follow a pattern. For MN:

```python
import pdfplumber
import re

CHAPTER_PATTERN = re.compile(r'^CHAPTER\s+(\d+)\s*$', re.IGNORECASE | re.MULTILINE)
# Sometimes also "Chapter 1: ..." inline at top of page

def find_chapter_boundaries(pdf_path):
    """Return list of (chapter_num, start_page, end_page, title)."""
    boundaries = []
    with pdfplumber.open(pdf_path) as pdf:
        for page_num, page in enumerate(pdf.pages):
            text = page.extract_text() or ''
            # Try various chapter-start patterns
            m = CHAPTER_PATTERN.search(text)
            if m:
                ch_num = int(m.group(1))
                # Title is usually next non-empty line
                lines = text.split('\n')
                title = None
                for i, line in enumerate(lines):
                    if 'CHAPTER' in line.upper() and i + 1 < len(lines):
                        title = lines[i + 1].strip()
                        break
                boundaries.append((ch_num, page_num, None, title))

    # Fill end pages
    for i in range(len(boundaries) - 1):
        boundaries[i] = (
            boundaries[i][0], boundaries[i][1],
            boundaries[i + 1][1] - 1, boundaries[i][3]
        )
    if boundaries:
        last = boundaries[-1]
        boundaries[-1] = (last[0], last[1], None, last[3])  # last chapter goes to end

    return boundaries
```

#### C.2.3 Extracting Active Learning Template content

```python
ALS_MARKER = re.compile(r'Active Learning Template:\s*([A-Z][a-zA-Z\s&-]+)', re.IGNORECASE)
APP_EX_MARKER = re.compile(r'Application Exercises?', re.IGNORECASE)

def extract_chapter_sections(pdf_path, chapter_pages):
    """Extract TL;DR-worthy content + ALS + Application Exercises per chapter."""
    start, end = chapter_pages
    with pdfplumber.open(pdf_path) as pdf:
        text = ''
        for page in pdf.pages[start:end + 1] if end else pdf.pages[start:]:
            text += (page.extract_text() or '') + '\n'

    sections = {}
    # Find Application Exercises start
    app_match = APP_EX_MARKER.search(text)
    if app_match:
        body_text = text[:app_match.start()]
        exercises_text = text[app_match.start():]
        sections['exercises_raw'] = exercises_text
    else:
        body_text = text
        sections['exercises_raw'] = None

    # Find ALS
    als_match = ALS_MARKER.search(body_text)
    if als_match:
        sections['als_template_type'] = als_match.group(1).strip()
        sections['als_raw'] = body_text[als_match.start():]
        body_text = body_text[:als_match.start()]
    else:
        sections['als_template_type'] = None
        sections['als_raw'] = None

    sections['body_raw'] = body_text
    return sections
```

#### C.2.4 Parsing Application Exercises into Q&A pairs

ATI questions follow a numbered pattern. Each ends with rationale block starting "Application Exercises Key" or "Answer:" markers.

```python
QUESTION_NUM = re.compile(r'\n\s*(\d+)\.\s+', re.MULTILINE)
OPTION_PATTERN = re.compile(r'^\s*([A-D])\.\s+(.+?)$', re.MULTILINE)

def parse_exercises(exercises_raw):
    """Extract 5 questions with options and rationales."""
    # Strip header
    lines = exercises_raw.split('\n')
    # Find first "1." occurrence — start of questions
    questions = []
    matches = list(QUESTION_NUM.finditer(exercises_raw))
    for i, m in enumerate(matches):
        start = m.end()
        end = matches[i + 1].start() if i + 1 < len(matches) else len(exercises_raw)
        block = exercises_raw[start:end]

        # Identify stem (text before first option) and options
        first_opt = OPTION_PATTERN.search(block)
        if not first_opt:
            continue
        stem = block[:first_opt.start()].strip()
        options_text = block[first_opt.start():]
        options = OPTION_PATTERN.findall(options_text)

        questions.append({
            'num': int(m.group(1)),
            'stem': stem,
            'options': [(letter, text.strip()) for letter, text in options]
        })

    return questions[:5]   # Cap at 5 — ATI standard
```

#### C.2.5 Identifying SATA questions

```python
SATA_MARKERS = [
    r'select\s+all\s+that\s+apply',
    r'\(SATA\)',
    r'choose\s+all\s+that\s+apply',
    r'mark\s+all\s+that\s+apply',
]

def is_sata(question_stem):
    """True if question stem indicates SATA."""
    for marker in SATA_MARKERS:
        if re.search(marker, question_stem, re.IGNORECASE):
            return True
    return False
```

#### C.2.6 Common PDF extraction gotchas

**Gotcha 1: Multi-column pages**
ATI uses 2-column layout in some sections. pdfplumber's `extract_text()` reads left-to-right ALL the way across, mixing columns.

**Fix:** use `page.crop((x0, y0, x1, y1))` to extract one column at a time:
```python
page_width = page.width
left_col = page.crop((0, 0, page_width / 2, page.height))
right_col = page.crop((page_width / 2, 0, page_width, page.height))
text = left_col.extract_text() + '\n' + right_col.extract_text()
```

**Gotcha 2: Bullet characters get mangled**
The PDF's bullet characters (•) sometimes extract as garbage characters like `·` or `\uf0b7`.

**Fix:** normalize:
```python
def normalize_bullets(text):
    text = text.replace('\uf0b7', '•')
    text = text.replace('●', '•')
    text = text.replace('o ', '• ')  # Sometimes 'o' is used
    return text
```

**Gotcha 3: Tables broken into prose**
Tables with rows of "Finding | Normal | Abnormal" get extracted as a mess of words. Detect tables explicitly:

```python
def extract_tables_per_page(pdf_path):
    """Get structured tables back."""
    with pdfplumber.open(pdf_path) as pdf:
        for page in pdf.pages:
            tables = page.extract_tables()
            for table in tables:
                yield table   # list of lists
```

**Gotcha 4: Headers/footers repeat on every page**
ATI PDFs have "MATERNAL NEWBORN NURSING" at the top of every page, page numbers at the bottom.

**Fix:** crop to exclude header/footer regions before extracting:
```python
page_top = 60   # pts from top
page_bottom = page.height - 60
content = page.crop((0, page_top, page.width, page_bottom))
```

**Gotcha 5: Ligature errors**
"fi", "fl", "ff" sometimes extract as Unicode ligatures (\ufb01, \ufb02, \ufb00).

**Fix:**
```python
def fix_ligatures(text):
    text = text.replace('\ufb01', 'fi')
    text = text.replace('\ufb02', 'fl')
    text = text.replace('\ufb00', 'ff')
    text = text.replace('\ufb03', 'ffi')
    text = text.replace('\ufb04', 'ffl')
    return text
```

**Gotcha 6: Hyphenated line-break words**
"con-\ntraception" gets stored literally with the hyphen and newline. Should re-join.

**Fix:**
```python
def dehyphenate(text):
    # Join words split across line breaks
    return re.sub(r'(\w+)-\n(\w+)', r'\1\2', text)
```

#### C.2.7 Recommended pipeline

```python
def build_chapter_data(pdf_path, ch_num):
    """End-to-end: PDF → structured chapter data ready to template."""
    # 1. Find boundaries
    boundaries = find_chapter_boundaries(pdf_path)
    ch_bound = next((b for b in boundaries if b[0] == ch_num), None)
    if not ch_bound:
        raise ValueError(f'Chapter {ch_num} not found')

    # 2. Extract sections
    sections = extract_chapter_sections(pdf_path, (ch_bound[1], ch_bound[2]))

    # 3. Clean
    for key in ['body_raw', 'als_raw', 'exercises_raw']:
        if sections[key]:
            sections[key] = fix_ligatures(sections[key])
            sections[key] = normalize_bullets(sections[key])
            sections[key] = dehyphenate(sections[key])

    # 4. Parse exercises
    if sections['exercises_raw']:
        sections['exercises'] = parse_exercises(sections['exercises_raw'])

    # 5. Return
    return {
        'chapter_num': ch_num,
        'title': ch_bound[3],
        'pages': (ch_bound[1], ch_bound[2]),
        **sections
    }
```

#### C.2.8 Manual review steps (always required)

PDF extraction is never 100% reliable. After automated parsing, always:

```
[ ] Spot-check 3 random chapters: do extracted titles match PDF?
[ ] Check exercise count per chapter: every chapter has 5? If not, why?
[ ] Spot-check 3 random exercises: are options A/B/C/D extracted correctly?
[ ] Search extracted text for unicode garbage (\u, \\x)
[ ] Search for "Application Exercises" appearing INSIDE body text (should only appear once per chapter)
[ ] Verify ALS template type matches one of the 8 known types
[ ] Cross-check chapter count: PDF has N chapters, extraction returns N
```

---

### 13.15 Procedure — Add A New Chapter To An Existing Subject

> *Consolidated from former Addendum F.1.*

Use case: ATI publishes a new edition with an additional chapter, or you want to add a custom chapter.

#### F.1.1 Steps

1. **Open the subject's Book HTML file** (e.g., `Elevated ATI MN Book.html`)

2. **Add the chapter content inside the chapter-pool:**
   - Find `<div class="chapter-pool" id="chapterPool">`
   - Insert a new `<section class="chapter" id="chN">` block per D.1 reference template
   - Place it in chapter-number order

3. **Add the sidebar entry:**
   - Find the right `<div class="nav-section">` for the chapter's unit
   - Insert `<a href="#chN" class="sidebar-item populated" data-section="chN">` per D.1.1
   - Maintain chapter-number order

4. **Add the planner row:**
   - Find the unit's `<div class="unit-accordion">` → `<div class="unit-body">`
   - Insert `<div class="planner-row populated" data-id="chN">` per D.1.1
   - Maintain chapter-number order

5. **Add typed mid-prompts:**
   - In Book Script 3, find `var MID_PROMPTS = {`
   - Add a new `"chN": [...]` entry with 2 prompts per A.2 rubric

6. **Update unit count UI:**
   - In Hub HTML: find the `<div class="unit-card" data-unit="unitX">` for that unit
   - Update `<div class="unit-range">Ch X – Y</div>` to include the new chapter

7. **Cross-link templates (if any apply):**
   - Find templates relevant to the chapter
   - Add `<li><a href="...#ex-...">Title</a></li>` to the new chapter's `chN-templates` section
   - If templates exist that should also bridge to this chapter: add the link reference

8. **Verify:**
   - Run validation script (B.6.3) for `chN`
   - Run JS lint check on all 3 inline scripts
   - Open Hub: confirm chapter count updated, unit cards still work
   - Open Book: confirm sidebar shows the new chapter, modal opens, all tabs render

#### F.1.2 User data implications

Adding a chapter does NOT break existing user data:
- `nur2460_atimn_progress` is a sparse object — missing chapter IDs default to 0
- `nur2460_bookmarks` is an array — new bookmarks for the new chapter just append
- `nur2460_fc_schedule` is an object — new flashcard IDs (`chN-p1`, `chN-p2`) just appear

#### F.1.3 Chapter number reuse warning

**Anti-pattern:** removing chapter 15, adding new chapter 15 with different content.

Result: users who had `ch15: 2` in their progress still show "Chapter 15 — read" but the content is different. They never see the new chapter as "unread."

**Mitigation:** if a chapter changes substantially, use a new ID (`ch15v2` or renumber the entire downstream).

---

### 13.16 Procedure — Production Deployment

> *Consolidated from former Addendum F.7.*

#### F.7.1 GitHub Pages workflow

The site lives at `sleepyius.github.io/NUR2460/`.

```bash
# 1. Make changes locally
# 2. Verify with B.6 QA checklists
# 3. Commit and push
git add .
git commit -m "Update MN ch5 — add nutrition section"
git push origin main

# 4. Wait ~30 seconds for GitHub Pages rebuild
# 5. Hard-refresh browser to bypass cache (Cmd+Shift+R on Mac)
```

#### F.7.2 Cache busting

GitHub Pages serves files with `Cache-Control: max-age=600` by default. Users may see old content for 10 minutes after a push.

**Mitigation if urgent:** append a query string to internal links:
```html
<a href="Elevated%20ATI%20MN%20Book.html?v=20260512">...</a>
```

This is rarely needed for personal use.

#### F.7.3 Pre-push checklist

Before `git push`:

```
[ ] B.6.3 QA script passes on all modified Book files
[ ] B.6.4 final-pass checklist completed
[ ] File sizes look reasonable (Book < 2MB, Templates < 2MB)
[ ] No console.log statements left in JS
[ ] No commented-out code blocks (clean it up)
[ ] No "TODO" / "FIXME" / "TEMP" in any file
[ ] Tested on mobile browser (real device or DevTools at 375px)
[ ] Tested theme toggle (both modes)
[ ] Tested cross-tool sync (rate a card → see it in Flashcards)
```

#### F.7.4 Rollback strategy

If a push breaks production:

```bash
# Find the last known-good commit
git log --oneline

# Revert just the broken commit
git revert HEAD
git push

# OR reset hard (destructive; rewrites history)
git reset --hard <good-commit-sha>
git push --force
```

User data is unaffected by rollback (it's in localStorage, not in the repo).

---

### 13.17 User Flow Walkthroughs

> *Consolidated from former Addendum H.2.*

How features compose during real study sessions. Use these to sanity-check that the design supports actual workflow, not just technical correctness.

#### H.2.1 First-time user flow

> A new student opens the suite for the first time.

```
1. sleepyius.github.io/NUR2460/ → index.html loads
2. Sees 3 subject cards. Picks "Maternal-Newborn Nursing"
3. Hub loads. No pickup panel (no saved state).
4. Hero + stats visible: "27 Chapters · 4 Units · 105 Worked Templates"
5. Decides to read Ch 1 — clicks "ATI Chapter Book"
6. Book loads. Sidebar shows all 27 chapters.
7. Clicks Ch 1 "Contraception" in sidebar.
8. Modal opens with tabs: TL;DR · Natural · Barrier · Hormonal · IUD · Surgical · ALS · Practice · Templates
9. Reads TL;DR. Switches to Natural tab. Reads.
10. Hits an abbreviation "BBT" — taps it, sees tooltip "Basal Body Temperature".
11. Encounters inline mid-read prompt about calendar method.
    Clicks "Reveal answer". Reads. Clicks "Good" → card scheduled.
12. Continues to Hormonal tab. Encounters typed mid-prompt (PRIORITY type, blue border).
    Reads question, reveals, rates "Hard" → card scheduled with 1-day interval.
13. Clicks star (☆) next to "Hormonal Methods" h2 — bookmarks it.
14. Star becomes filled (★). Bookmarks badge appears showing "1".
15. Clicks Practice tab. Sees 5 NCLEX-style questions. Opens Q1.
    → Answer is marked as "answered" in tracking
16. Closes modal (× or Esc).
17. Back on Book main page. Sees Ch 1 row.
    Taps the planner-check → first tap = "reviewed" (faded fill)
18. Goes to Hub.
19. Pickup panel now visible: "Pick up where you left off" with Ch 1 link.
20. Total: ~5 minutes for one chapter overview, 1 bookmark, 2 cards in deck.
```

#### H.2.2 Daily review flow

> Returning user with multiple chapters in progress.

```
1. Opens Hub. Pickup panel shows:
   - Continue reading: Ch 3 · Active Learning Scenario (last position)
   - Review queue: 12 cards due now
   - Last template: Combined Oral Contraceptives

2. Clicks "Review queue" → Flashcards page opens.
3. First card: ch1-p1 PRIORITY type. Reads question. Presses Space → reveals.
4. Rates "Good" (presses 2). Card scheduled 6 days out.
5. Next card: fc-ch2-bbt CONTENT inline type. Wrong answer this time.
   Rates "Hard" (presses 1). Card reset to 1-day interval.
6. After 10 cards, session timer shows 4:23. Decides to stop.
7. Clicks "Back to Hub". Hub still shows pickup panel.
8. Clicks "Continue reading" → Book opens with Ch 3 modal at ALS tab.
9. Finishes ALS. Closes modal.
10. Taps planner-check on Ch 3 twice → "complete" state (full accent, checkmark).
11. Unit 1 progress bar updates: now showing 3/10 complete.
12. Closes browser tab. State persists.
```

#### H.2.3 Pre-exam cramming flow

> The night before an exam.

```
1. Opens Hub. Sees 2/27 chapters complete, 18 cards due.
2. Decides to print all chapter TL;DRs for offline review.
3. Opens Book. Clicks master print button "🖨️ Print Chapters".
4. Print overlay opens with toolbar: Brief / Deep mode + Print + Close.
5. Confirms "Brief" mode. Sees 27 chapters of TL;DRs only.
6. Clicks "Print / Save PDF". Browser print dialog opens.
7. Saves as PDF.
8. Closes print overlay.
9. Wants to drill on weak topics. Opens Flashcards.
10. Filters: Chapter = "All", Type = "PRIORITY" (highest-risk recall)
11. Drills 30 cards. Stops at 8:14 elapsed.
12. Wants to see template patterns. Opens Templates.
13. Filter chips: Type = "System Disorder" (most clinical content).
14. Toggles Filled/Blank → Blank mode. Tries to fill in mentally for 5 cards.
15. Toggles back to Filled. Marks studied for each.
16. Templates progress bar updates: now showing 28/105 studied.
```

#### H.2.4 Returning after extended absence

> Student didn't open the app for 2 weeks during clinical rotation.

```
1. Opens Hub. Pickup panel shows "Review queue: 47 cards due now"
2. Clicks it. Flashcards page loads.
3. Sees session timer reset (new session).
4. Cards arrive in order of overdue-ness (longest overdue first).
5. Many cards rated "Hard" because memory is stale.
6. After 30 minutes, ~20 cards reviewed. Many are reset to 1-day interval.
7. Notes which chapter the cards came from. Decides to re-read Ch 9 (Medical Conditions).
8. Opens Book, navigates to Ch 9 in sidebar.
9. Modal opens at TL;DR (default first tab).
10. Re-reads. Bookmark from 2 weeks ago is still there (★).
11. Clicks bookmark button → bookmarks panel opens.
12. Sees 8 bookmarks. Clicks Ch 9 Preeclampsia bookmark → modal opens at that section.
13. Re-reads section. Tries the typed mid-prompt again, rates "Good".
```

#### H.2.5 Templates → Book cross-reference flow

> Student is studying medications and wants to cross-reference.

```
1. Opens Hub. Clicks "ATI Templates".
2. Templates page loads with 8 accordions.
3. Filters: Type = "Medication". Other types collapse.
4. Filter count updates: "15 of 105 examples".
5. Scrolls to "Oxytocin / Pitocin" card.
6. Clicks the ⛶ expand button → example modal opens with full card.
7. In the modal, clicks "→ Read in book" link.
8. Browser navigates to Book#ch11-oxytocin.
9. Book opens, modal opens for Ch 11, tab focused on Oxytocin section.
10. Reads the section. Sees typed mid-prompt.
11. Closes modal. Back-button to Templates? No — they came via direct link.
12. Click "Back to Hub" → Hub → Templates.
13. Templates loads, filter state preserved (still "Medication" filter active).
14. Continues to next card.
```

#### H.2.6 Bookmarks-driven study flow

> Student uses bookmarks as a personal study list.

```
1. While reading Book, encounters 5 sections marked "weak — need review".
2. Bookmarks each (taps ☆ next to h2).
3. Closes Book.
4. Later — opens Book. Clicks bookmarks button (⭐ Bookmarks · 5).
5. Bookmarks panel opens. Sees the 5 sections with most recent first.
6. Clicks the oldest one → modal opens at that section.
7. Studies it. Unbookmarks (taps ★ → ☆). Closes modal.
8. Bookmarks badge updates to "4".
9. Continues until all 5 are studied. Badge → 0 (hidden).
```

#### H.2.7 Cross-tool sync verification flow

> Demonstrates how features compose across tools.

```
Setup: fresh state (cleared localStorage).

1. Open MN Book. Open Ch 1.
2. On TL;DR section, click the bookmark button.
3. Open Hormonal section. Rate the typed PRIORITY prompt as "Hard".
4. Open Practice. Click Q1 to reveal rationale.
5. Close modal.
6. Go to Hub.

Verify Hub now shows:
   ✓ Pickup panel: "Continue reading: Ch 1 · Practice" (where you last were)
   ✓ Pickup panel: "Review queue: 1 card due now"
   ✓ Book card progress bar: shows planner status if you marked any chapter

7. Click "Review queue" → Flashcards.
8. Verify: 1 card visible, type=PRIORITY, prompt matches what you rated.
9. Go back to Book.
10. Click bookmarks button.
11. Verify: bookmark from step 2 visible, click it → modal opens at TL;DR.
12. Switch theme (sun icon).
13. Go to Hub. Verify theme is still light/dark across all pages.
```

If any of these fail, the cross-tool sync is broken. See PART 7.18.

---

### 13.18 Testing On Actual Devices

> *Consolidated from former Addendum H.5.*

Recommended test rotation when shipping changes:

```
1. Desktop Chrome at 1440px width
   - Verify desktop sidebar visible, modal centers correctly
   - Tab strip visible (no scroll needed for typical chapter)

2. Desktop Chrome at 1000px width
   - Still desktop layout (above 900px breakpoint)
   - Slight margin reduction

3. DevTools mobile emulator at 375px (iPhone SE)
   - Hamburger button visible, back-home button visible
   - Sidebar slides in from left
   - Modal goes ~full-width with small margin
   - Tab strip should scroll horizontally if 8+ tabs

4. DevTools mobile emulator at 414px (iPhone Pro Max)
   - Same as 375px but slightly more breathing room

5. Real iPhone (Safari) at any size
   - This is the primary user device
   - Test scroll, tap, theme toggle, modal close (×, overlay, swipe back)
   - Test from cold cache vs warm cache
   - Test from GitHub Pages (production) vs localhost

6. Real Android (Chrome) at typical size
   - Verify Google Fonts loads
   - Verify localStorage persists
   - Test back button behavior

7. Print preview (Chrome / Safari)
   - Verify Brief mode looks clean
   - Verify Deep mode is readable
   - No giant images, no orphaned headers
```

If a change passes all 7, it's safe to push.

---

---

## PART 14 — EDITORIAL STANDARDS

> Standards for the content (voice, mid-prompt rubric, NCLEX rubric). Consolidated from former Addendum A so the canonical reference for "how should this be worded?" lives in the main guide, not in a separate appendix.

### 14.1 Content-writing voice guide

#### A.1.1 General principles

The suite is built for **fast clinical recall**, not casual reading. The voice is:
- **Terse** — every word earns its place; cut hedging
- **Clinical** — use the actual medical terminology, don't paraphrase down
- **Active** — verb-first construction ("Assess fundal tone" not "The nurse should assess fundal tone")
- **Mobile-respectful** — favor short sentences; readers scan on phones
- **Second-person only in TL;DR cards** — main content stays third-person clinical

**What to AVOID:**
- "It is important to remember that..." → cut entirely
- "The nurse should consider..." → just state the action
- "There are several factors that may contribute to..." → list the factors
- Long sentences with multiple commas — break them
- Empty intensifiers ("very", "really", "extremely") — replace with specifics

#### A.1.2 TL;DR card voice

The TL;DR is the most carefully voiced part of any chapter. Pattern:

**Lead paragraph** (1-3 sentences, ~40-80 words):
- Sentence 1: the core concept stated as a formula or ladder
- Sentence 2: the most important clinical implication
- Sentence 3 (optional): a single critical contraindication or warning

**Real MN samples:**

> Contraception choice = client autonomy + medical history. Highest effectiveness: **LARCs (IUDs and implants)** > sterilization > injectable > pill/patch/ring > barrier > natural. **Only condoms protect against STIs.** Hormonal methods carry thromboembolic, stroke, and hypertension risks — screen carefully. Smokers > 35 yo cannot take estrogen-containing methods.

> Infertility is a couple's diagnosis — both partners must be assessed. Semen analysis comes first (cheap, non-invasive, 40% of cases are male). Female workup is invasive (hormones, ultrasound, HSG, hysteroscopy, laparoscopy). Allergy to seafood/iodine = contraindication to HSG dye. Treatment ladder: lifestyle → medication → ART.

> Pregnancy signs ladder: presumptive (felt by client) → probable (seen by examiner) → positive (only pregnancy explains it). Only positive signs confirm: heart tones, fetal movement palpated by examiner, fetal visualization. Nägele's rule: LMP − 3 months + 7 days + 1 year. Supine hypotensive syndrome from vena caval compression — fix with left-lateral position.

**TL;DR voice tells:**
- Uses `>` for hierarchies/ladders inline
- Uses `=` for equivalence/definitions
- Uses `—` (em dash, not hyphen) for clinical implications
- Drops articles ("Semen analysis comes first" not "The semen analysis comes first")
- Uses arrows `→` for sequences
- Bolds the **key noun or critical warning**, not whole phrases

**Brief-grid columns** (2 columns, 3-6 bullets each):

Each column has:
- An `<h3>` heading in ALL CAPS or sentence case (consistent within chapter)
- Bullets in `<strong>bold term</strong> — definition format

Sample structure:
```
The six categories               Key contraindications
- Natural family planning —      - Estrogen-containing:
  abstinence, withdrawal,           Smoker >35, hx thrombo-
  calendar, BBT                     embolism, breast cancer,
- Barrier — condoms,                migraine with aura
  diaphragm, cervical cap...     - IUD: active PID, pregnancy,
- Hormonal — pill, patch,           undiagnosed bleeding
  ring, injection
```

#### A.1.3 Section lead voice

The `<p class="section-lead">` after each `<h2>` is a 1-2 sentence orientation. Pattern:
- Frame what's covered
- State the key clinical takeaway for this section
- End with a warning or differentiator if relevant

**Real MN samples:**

> Fertility-awareness based methods — no hormones, no devices. Effectiveness depends entirely on adherence and accurate cycle tracking. **None protect against STIs.**

> Pelvic, hormonal, and breast exam findings change predictably over the 40 weeks. Knowing the timeline lets you distinguish expected changes from complications.

> Postpartum is a 6-week recovery period. Most maternal mortality happens in the first 7 days — fundal tone, lochia, and BP screening are non-negotiable.

#### A.1.4 Condition-block voice

A condition-block has 3 parts: header, body paragraph, finding-grid.

**The body paragraph** is 1-3 sentences. It defines or contextualizes the condition. Should answer "what is this?" without going into details that belong in the finding-grid.

**The finding-grid cards** each have:
- A 1-3 word heading (`<h4>`) — usually a single noun: "Risk Factors", "Assessment", "Nursing Care", "Complications"
- Bullets in this style:
  - `<strong>Key term</strong> — definition or detail`
  - `<strong>Clinical action</strong> if condition present`
  - `Specific number, time, or threshold` (e.g., "Notify provider if BP > 140/90")

**Don't:**
- Write full sentences in bullets unless required for clinical accuracy
- Mix tense across bullets in the same card
- Use "consider", "may want to", "could" — be definitive

#### A.1.5 ALS (Active Learning Scenario) voice

Two-block structure: scenario + answer key.

**Scenario block:**
- The scenario itself is `<em>italicized</em>` and reads as it would in the textbook
- Sub-questions are bulleted: Related Content, Underlying Principles, Nursing Interventions
- No commentary — the scenario stands alone

**Answer key block:**
- Each sub-question gets its own finding-card or kb-card
- Same bullet style as condition-blocks (terse, bolded keys)
- For nursing interventions, use imperative verbs: "Take...", "Monitor...", "Report..."

#### A.1.6 NCLEX rationale voice

Each exercise's rationale block must explain **every option**, not just the correct one. Pattern per option:

**For the correct answer:**
```
A. CORRECT. [1 sentence stating the principle] [1 sentence with the specific clinical detail].
```

**For incorrect answers:**
```
B. [1 sentence explaining why this is wrong, often by stating what's true instead].
```

**Don't:**
- Say "Incorrect" then re-explain the right answer (already covered above)
- Use "This is wrong because..." (cut "because")
- Skip an option (every A/B/C/D needs a rationale, even if brief)

**Real MN sample (Ch 1 Q1):**

> A. **CORRECT.** Taking COCs at the same time daily maintains stable hormone levels.
> B. Skipping pills risks ovulation. Two pills the next day is not the correct catch-up.
> C. COCs do **NOT** protect against STIs.
> D. Breast tenderness is expected and not a reason to stop.

#### A.1.7 Mid-read prompt voice

**The question** should be:
- One sentence
- Open-ended enough to require thought, not just yes/no
- Use clinical scenario framing for JUDGMENT/PRIORITY types

**Question stems to use:**
- `What is...` → CONTENT
- `What action should the nurse take first when...` → PRIORITY
- `Why is...` → PRINCIPLE
- `A client [scenario]. What is the appropriate nursing response?` → JUDGMENT
- `How do you calculate...` → calc type (inline)

**The answer** should be:
- 2-5 sentences
- Lead with the action/answer, then the rationale
- Bold the most critical phrase

**Real MN samples:**

CONTENT (ch2-p1):
> Q: What basal body temperature pattern indicates ovulation has occurred?
> A: A **sustained rise of 0.4–1.0°F (0.2–0.5°C) above baseline for 3+ consecutive days**. The dip just before, then sustained rise, confirms ovulation has occurred. Best used **retrospectively, not predictively.**

PRIORITY (ch1-p1):
> Q: A client missed two consecutive doses of combined oral contraceptives in the first week of the pack. What is the priority instruction?
> A: **Take the most recent missed pill ASAP** (even if 2 pills in one day), take the next pill at the regular time, **use backup contraception for 7 days**, and consider emergency contraception if there was unprotected intercourse in the past 5 days.

JUDGMENT (ch1-p2):
> Q: A breastfeeding mother at 6 weeks postpartum wants combined oral contraceptives. What is the appropriate response?
> A: COCs are **NOT recommended** for breastfeeding mothers — estrogen decreases milk supply. Progestin-only pills (mini-pills), the IUD, implant, or DMPA are preferred non-estrogen methods.

#### A.1.8 Tone calibration cheatsheet

| Section | Tone |
|---|---|
| TL;DR lead | Punchy, formulaic, second-person if needed |
| Brief-grid bullets | Telegraphic, bolded keys |
| Section lead | Orientational, 1-2 sentences |
| Condition body | Definitional, 1-3 sentences |
| Finding card bullets | Imperative or telegraphic |
| ALS scenario | Textbook voice (italicized) |
| ALS answer key | Imperative for actions, formulaic for principles |
| NCLEX rationale | One sentence per option, lead with the principle |
| Mid-read CONTENT | Factual, lead with the answer |
| Mid-read PRIORITY | Imperative, lead with the action |
| Mid-read JUDGMENT | Conditional, frame the decision |
| Mid-read PRINCIPLE | Explanatory, "because..." reasoning |

---

### 14.2 Mid-prompt selection rubric

Each chapter gets **exactly 2 typed mid-prompts** stored in `MID_PROMPTS`. The question is: which 2 of the 4 types?

#### A.2.1 Actual MN distribution

Across all 27 MN chapters:

```
CONTENT:    18 prompts  (67% of chapters use it)
JUDGMENT:   17 prompts  (63%)
PRIORITY:   17 prompts  (63%)
PRINCIPLE:   2 prompts  (rare — ch2, ch22 only)
```

**Most common pairings:**
```
CONTENT + JUDGMENT    9 chapters
JUDGMENT + PRIORITY   8 chapters
CONTENT + PRIORITY    8 chapters
CONTENT + PRINCIPLE   1 chapter  (ch2)
PRINCIPLE + PRIORITY  1 chapter  (ch22)
```

#### A.2.2 Selection logic

**Default rule:** pick 2 from {CONTENT, JUDGMENT, PRIORITY}. PRINCIPLE is the exception, not a default option.

**Use PRIORITY when:**
- The chapter has a time-critical action (postpartum hemorrhage, eclampsia, prolapsed cord)
- There's a "what does the nurse do FIRST" question worth highlighting
- Missed/late drug dosing has acute consequences
- Used in: ch1 (missed COC pills), ch15 (preeclampsia escalation), ch20 (postpartum hemorrhage)

**Use JUDGMENT when:**
- A clinical scenario has multiple reasonable responses and one is correct
- The chapter involves teaching, counseling, or client education decisions
- There's a contraindication that requires recognizing context
- Used in: ch1 (breastfeeding + COCs), ch3 (presumed normal vs concerning findings), ch6 (genetic counseling)

**Use CONTENT when:**
- There's a specific named pattern, calculation, formula, or number worth recalling
- The chapter is foundational (anatomy, terminology, normal values)
- Used in: ch2 (BBT pattern), ch3 (Nägele's rule), ch11 (FHR baseline ranges)

**Use PRINCIPLE only when:**
- The "why" is non-obvious and clinically important
- The principle ties multiple chapters together
- Rare — reserve for chapters where mechanism-of-action matters
- Used in MN: ch2 (HSG timing in follicular phase), ch22 (newborn thermoregulation principles)

#### A.2.3 Decision flowchart

```
Is there a time-critical action in this chapter?
├── YES → one prompt is PRIORITY
│   └── Second prompt:
│       ├── Has a clinical decision point? → JUDGMENT (PRIORITY+JUDGMENT)
│       └── Has a named pattern/formula?  → CONTENT  (CONTENT+PRIORITY)
│
└── NO → Is the chapter foundational (anatomy/terminology)?
    ├── YES → one prompt is CONTENT
    │   └── Second prompt:
    │       ├── Mechanism worth knowing?  → PRINCIPLE (CONTENT+PRINCIPLE, rare)
    │       └── Decision point exists?    → JUDGMENT  (CONTENT+JUDGMENT)
    │
    └── NO → both prompts are JUDGMENT-class
        └── Pair with PRIORITY (JUDGMENT+PRIORITY, most common for complication chapters)
```

#### A.2.4 Anchor placement (`after` field)

Each prompt has an `after: "chN-section-id"` field that determines where in the chapter the card injects.

**Placement rules:**
- After the section the prompt is most relevant to (NOT at the start or end of chapter)
- If both prompts share a relevant section, they CAN both have the same `after` value (will stack)
- Avoid placing both on TL;DR — let prompts appear mid-chapter where reader is engaged
- Don't place on `chN-exercises` (the practice section already has questions)

**Real MN examples:**
- ch1: both prompts `after: "ch1-hormonal"` (hormonal section is the hottest topic)
- ch2: p1 `after: "ch2-assessment"`, p2 `after: "ch2-diagnostic"` (spread across sections)
- ch20: both `after: "ch20-hemorrhage"` (postpartum hemorrhage section dominates the chapter)

#### A.2.5 Writing the 2 prompts together

The 2 prompts should not duplicate each other. Aim for:
- Different sections of the chapter
- Different cognitive levels (recall vs decision)
- Different clinical situations even within the same chapter

**Bad pairing:** two prompts both asking "what is X?" with different X values
**Good pairing:** one prompt asks "what is the pattern?" (CONTENT), the other asks "what's the priority intervention when you see this pattern?" (PRIORITY)

---

### 14.3 NCLEX question rubric

Each chapter has exactly 5 NCLEX-style practice exercises in `chN-exercises`.

#### A.3.1 NCLEX Category distribution

The actual MN distribution across all 5×27 = 135 exercises (plus extras): 189 NCLEX-tagged questions distributed as:

```
Health Promotion & Maintenance        61 (32%)
Reduction of Risk Potential           48 (25%)
Pharmacological & Parenteral          23 (12%)
Physiological Adaptation              20 (11%)
Psychosocial Integrity                11 (6%)
Safety & Infection Control             9 (5%)
Basic Care & Comfort                   4 (2%)
[other / blank tags]                  13 (7%)
```

#### A.3.2 Per-chapter category mix

The 5 questions in a chapter should hit **at least 3 different NCLEX categories**. Don't make all 5 the same category.

**Recommended chapter mix:**
- 2 questions on the dominant clinical category for that chapter
- 1 question on Pharmacological & Parenteral (if any meds are in chapter)
- 1 question on Health Promotion (teaching/education)
- 1 question on Reduction of Risk OR Safety & Infection Control

**Adjust by chapter type:**
- Antepartum chapters lean Health Promotion + Reduction of Risk
- Intrapartum chapters lean Reduction of Risk + Physiological Adaptation
- Postpartum chapters lean Safety + Health Promotion
- Newborn chapters lean Health Promotion + Physiological Adaptation + Basic Care

#### A.3.3 Question stem patterns

**Pattern 1: "A nurse is [verb]ing a client about/with [condition]. Which of the following [statements/findings/actions] indicates..."**

> A nurse is teaching a client about combined oral contraceptives. Which of the following statements by the client indicates an understanding of the teaching?

**Pattern 2: "A nurse is caring for a client who [scenario]. The nurse should [action]?"**

> A nurse is caring for a client who is 32 weeks gestation with preeclampsia. Which of the following findings should the nurse report to the provider?

**Pattern 3: "A nurse is [planning/preparing] [intervention] for a client who [scenario]. Which of the following [actions/medications/considerations]..."**

> A nurse is preparing to administer magnesium sulfate to a client with severe preeclampsia. Which of the following findings would indicate magnesium toxicity?

**Pattern 4: SATA — "A nurse is caring for a client who [scenario]. Which of the following actions should the nurse take? (Select all that apply.)"**

#### A.3.4 Distractor (wrong answer) rules

The 3 incorrect options should be:
- **Plausible** — a student might pick them without solid knowledge
- **Diverse in their wrongness** — don't make all 3 wrong for the same reason
- **Educational** — each wrong answer teaches something when rationaled

Common distractor flavors:
- **Right action, wrong indication** — "Position client supine" when they need left-lateral
- **Right concept, wrong specifics** — "BP > 130/80" when threshold is 140/90
- **Outdated practice** — "Routine episiotomy" (no longer recommended)
- **Common misconception** — "COCs protect against STIs" (false but believed)
- **Right idea, wrong timing** — "Notify provider" when independent action is needed first

**Don't:**
- Make one option obviously absurd
- Use absolutes ("never", "always") in the correct answer
- Have two answers that are clinically identical
- Use the same distractor pattern in all 5 questions of a chapter

#### A.3.5 SATA (Select All That Apply) usage

**Frequency:** ~36% of MN exercises are SATA. That's a high rate matching NCLEX testing trends.

**When to use SATA in a chapter:**
- 1-2 of the 5 questions per chapter
- The topic has multiple correct interventions or assessments (not a single right answer)
- The student should recognize *which subset* of options applies (not just one)

**SATA structure:**
- 4-6 options (more than standard 4)
- 2-4 correct answers among them
- All wrong answers should be plausible
- Don't make all options correct (defeats the test)
- Don't make only 1 correct (use standard multiple choice instead)

**SATA stem variants:**
- "Which of the following should the nurse include in client teaching? (Select all that apply.)"
- "Which of the following findings would the nurse expect? (SATA)"
- "Which of the following are risk factors for [condition]? (SATA)"

#### A.3.6 NCLEX tag formatting

```html
<span class="nclex-tag">NCLEX · Health Promotion & Maintenance · Antepartum Care</span>
```

Format: `NCLEX · {Category} · {Subcategory}`

**Notice:** the actual MN files use `&amp;` in HTML for ampersands inside tags. Standardize either way but be consistent.

**Subcategory examples by category:**
- Health Promotion & Maintenance: Antepartum Care, Newborn Care, Family Planning, Developmental Stages
- Reduction of Risk Potential: Diagnostic Tests, Lab Values, Potential Complications
- Pharmacological & Parenteral Therapies: Medication Administration, Expected Actions/Outcomes, Adverse Effects, Contraindications/Side Effects
- Physiological Adaptation: Fluid & Electrolyte, Hemodynamics, Pathophysiology
- Psychosocial Integrity: Coping, Grief, Crisis Intervention
- Safety & Infection Control: Standard Precautions, Error Prevention
- Basic Care & Comfort: Nutrition, Mobility, Personal Hygiene

#### A.3.7 Quality checks per chapter exercises

```
[ ] Exactly 5 exercises
[ ] At least 3 different NCLEX categories represented
[ ] 1-2 SATA questions (not all, not none)
[ ] Every option (A/B/C/D) has a rationale, including correct
[ ] Rationales lead with the principle, not "because"
[ ] No two questions test the exact same fact
[ ] At least one question integrates content from the ALS or templates
[ ] NCLEX tag follows "NCLEX · Category · Subcategory" format
[ ] Question stems use consistent grammar ("A nurse is...")
```

---

## PART 15 — COMMON PITFALLS

### Pitfall 1: Chapter content leaks onto page

**Symptom:** Visible chapter text appears at the bottom of the main content area instead of being hidden in the pool.
**Cause:** `<div>` imbalance in a chapter → pool closes early.
**Fix:** Run tag-balance check (PART 13.4). The chapter whose `</div>` count is short is the one that broke the pool.

### Pitfall 2: Modal opens but only some tabs show

**Symptom:** Chapter modal opens but is missing TL;DR, Practice, or Templates tab.
**Cause:** That subsection wasn't a direct `<section>` child of `.chapter`, OR it was missing the `id` attribute.
**Fix:** `openChapter()` uses `:scope > section[id]`. Confirm structure.

### Pitfall 3: Theme toggle doesn't work

**Symptom:** Click theme button, page doesn't change.
**Causes:**
- CSS uses `html.light` instead of `[data-theme="light"]`
- JS toggles wrong selector
- THEME_KEY localStorage key is wrong (different per subject — see PART 12)

### Pitfall 4: Templates page is broken

**Symptom:** Accordions are empty even though template-pool has cards.
**Cause:** `studies()` (the function that moves cards from pool to accordions) wasn't called, OR the `data-section` on a card doesn't match an accordion's `id`.
**Fix:** Verify `<section class="template-section" data-section="X">` matches `<div class="tpl-accordion" id="X-acc">`.

### Pitfall 5: Bookmarks button never appears

**Symptom:** Stars don't show next to section h2s in modal.
**Cause:** `injectBookmarkButtons()` was not called in the `openChapter` flow.
**Fix:** Ensure step 5 of `openChapter()` calls `injectBookmarkButtons(modalBody, chapterId)`.

### Pitfall 6: NCLEX filter bar duplicates

**Symptom:** Multiple filter bars appear in exercises after reopening chapter.
**Cause:** Forgot the `if (section.querySelector('.nclex-filter')) return;` guard.
**Fix:** Always check for existing element before injecting.

### Pitfall 7: Abbreviation tooltips wrap inside other tooltips

**Symptom:** Hovering shows nested or weird tooltips.
**Cause:** `autoWrapAbbreviations` walked into an already-wrapped span.
**Fix:** Walk function excludes `node.classList.contains('abbr')` from recursion.

### Pitfall 8: Mobile sidebar doesn't close on navigation

**Symptom:** Open hamburger, tap a chapter; sidebar stays open over the modal.
**Cause:** `openChapter()` missing the `if (window.innerWidth <= 900) closeSidebarPanel();` line.

### Pitfall 9: SM-2 ratings get lost

**Symptom:** Rate a card, refresh page, the card is back.
**Cause:** Wrong localStorage key (e.g., used `nur2460_atimn_fc_schedule` instead of `nur2460_fc_schedule`).
**Fix:** See PART 12 — the FC schedule key is `nur2460_fc_schedule`, shared across MN and Pharm.

### Pitfall 10: Search dropdown stays open after click

**Symptom:** Click a search result, dropdown remains visible.
**Cause:** Missing `results.classList.remove('show')` in click handler.

### Pitfall 11: Mid-read prompt rates as "rated" but isn't in flashcards

**Symptom:** Card shows ✓ in chapter, but Flashcards page doesn't show it.
**Cause:** `rateMidRead` didn't save to `nur2460_fc_schedule` (wrong key) or didn't include `nextReview`.

### Pitfall 12: Print overlay prints everything, not just chapter

**Symptom:** Browser print includes sidebar and main page.
**Cause:** Missing `@media print { body.printing > *:not(.print-overlay) { display: none !important; } }`.
**Fix:** Verify the print stylesheet includes the body.printing scope.

---

### 15.1 Overarching lesson from the PD port

The PD port found 5+ bugs during a second-pass audit that escaped the first-pass audit:

1. Wrong `<title>` in Templates ("Maternal-Newborn" — wrong tab name)
2. Chapter filter only 1-27 in Flashcards (couldn't filter ch28-44 individually)
3. Type filter missing 4 typed types in Flashcards (CONTENT/JUDGMENT/PRINCIPLE/PRIORITY unfilterable)
4. "Load 122 starter cards" hardcoded text in Flashcards (showed MN count)
5. `title` attribute had matching MN-count hardcode in Flashcards

**Root cause: my first-pass audit was guided by what I expected to see, not by a checklist.** When auditing a port, I should run every item in I.3 mechanically, not rely on judgment about what's "likely to be wrong." This addendum exists so future ports don't repeat this pattern.

When the porter says "it looks fine" — they haven't run the checklist. Run the checklist.


### 15.2 Edge Cases — Chapter Structure

> *Consolidated from former Addendum B.1.*

#### B.1.1 Chapter with no Active Learning Scenario (ALS)

**Reality check:** in MN, chapters 7, 8, and 13 have no ALS in the source PDF. The build must accommodate this.

**Rule:** If the PDF doesn't contain an "Active Learning Template" prompt for that chapter, omit `chN-als` entirely. Don't fabricate one.

**Structural impact:**
```html
<section class="chapter" id="ch7">
  <div class="chapter-banner">...</div>
  <section id="ch7-tldr" class="brief-card">...</section>
  <section id="ch7-{topic}" class="content-section">...</section>
  <!-- NO ch7-als here -->
  <section id="ch7-exercises" class="content-section">...</section>
  <section id="ch7-templates" class="content-section tpl-bridge">...</section>
</section>
```

**Modal effect:** the chapter modal shows one fewer tab. `openChapter()` handles this automatically — it just renders whatever direct child `<section>` elements exist.

**Hub-level effect:** the chapter is still counted as "populated" (the planner-row uses `.populated` class as long as TL;DR exists). No special case needed.

#### B.1.2 Chapter with very few content sections (2-3 topics)

**When does this happen:** Short chapters covering a single procedure or concept (e.g., Pharm chapters on a single drug class).

**Rule:** No minimum required count beyond `chN-tldr` + `chN-exercises` + `chN-templates`. A chapter with just 2 content-sections is valid.

**Modal effect:** tab strip has 5 tabs total (TL;DR + 2 content + Practice + Templates). Fits without horizontal scroll on most screens.

**Don't:** artificially split a short topic into multiple thin sections just to bulk up tab count. Better one solid section than three flimsy ones.

#### B.1.3 Chapter with many content sections (8+ topics)

**When does this happen:** Long chapters that genuinely have many independent topics (e.g., MN Ch 23 — Newborn Assessment has 9 content sections).

**Rule:** No upper limit. Modal tab strip scrolls horizontally.

**Visual concern:** at 8+ tabs, users may not notice some tabs exist off-screen. Mitigations already built-in:
- Edge gradient shadows indicate "more content this way"
- `updateTabFade()` updates them on scroll
- Tab clicks `.scrollIntoView()` so active tab is always visible

**Build consideration:** if a chapter has 8+ tabs, consider whether some logically merge. But don't force-merge just to reduce count — readability per tab matters more than tab count.

#### B.1.4 Chapter with 0 templates bridging to it

**When does this happen:** A chapter covers content that doesn't get its own Active Learning Template in the source PDF. Some foundational chapters or transition chapters fall into this.

**Rule:** Always include `chN-templates` section, but with explanatory copy instead of links.

**Structural pattern:**
```html
<section id="ch7-templates" class="content-section tpl-bridge">
  <h2>ATI Templates · this chapter</h2>
  <p style="color: var(--text2); font-size: 14px;">
    No ATI templates directly reference this chapter's content.
    Related templates may appear in adjacent chapters covering
    [related topic].
  </p>
</section>
```

**Don't:** omit `chN-templates` entirely. The modal expects this tab.

#### B.1.5 Chapter with fewer than 5 NCLEX exercises

**When does this happen:** PDF source has only 3 or 4 questions for that chapter.

**Rule:** Write additional questions to reach 5, following A.3 (NCLEX rubric). Don't ship a chapter with fewer than 5.

**Why:** Consistency across the suite. Users expect 5 per chapter for study planning.

**Exception:** If the chapter is genuinely too short to support 5 distinct questions, document it in `chN-exercises` with a note: "This chapter is brief; review companion chapter chX for additional practice." (Rare — use sparingly.)

#### B.1.6 SATA-only chapter or all-multiple-choice chapter

**Rule:** No chapter should have 5 SATA questions, and no chapter should have 0. Aim for 1-2 SATA per chapter (matches the ~36% MN rate).

**Detection:** `isSataQuestion(ex)` counts `<p class="answer correct">` elements. >1 = SATA.

#### B.1.7 Mid-prompt only on TL;DR section

**Anti-pattern:** placing both typed mid-prompts `after: "chN-tldr"`.

**Why bad:** prompts visually cluster at the very top of the chapter; reader hits them before engaging with content; both have to compete for attention.

**Fix:** spread prompts across the chapter body. See A.2.4.

**Exception:** very short chapters (3 content-sections or fewer) — both prompts can sit `after: "chN-tldr"` because there isn't room to spread them.

#### B.1.8 Inline mid-read absence

**Reality check:** not every section needs an inline mid-read aside. MN Ch 1 has 5 mid-reads spread across the chapter; MN Ch 7 has 1.

**Rule:** add `<aside class="mid-read">` where the content has a genuinely tricky fact, calculation, or warning worth pausing on. Don't add them by quota.

**Heuristic:**
- 1 mid-read per 200-400 words of body content
- At least 1 `data-fc-type="warning"` per high-acuity chapter (PIH, eclampsia, hemorrhage, sepsis)
- At least 1 `data-fc-type="calc"` per chapter with calculations (BBT, fertile window, Nägele, oxytocin titration)

#### B.1.9 Chapter without exercises at all

**Reality check:** the source PDF has questions for every chapter, so this shouldn't happen.

**Rule:** if you encounter this, do NOT ship the chapter. It would orphan the Practice tab.

**Recovery:** write 5 NCLEX-style questions matching the chapter content (A.3).

#### B.1.10 Duplicate chapter IDs across files

**Anti-pattern:** Pharm and MN both having `ch1`, then a flashcard like `ch1-p1` collides between subjects.

**Why not a problem:** localStorage keys are subject-namespaced. `nur2460_atimn_progress` and `nur2460_atipharm_progress` are different stores. SAME for `atipd_*`.

**However:** `nur2460_fc_schedule` IS shared between MN and Pharm. The flashcard IDs are `chN-p1` style — if both subjects have `ch1-p1`, they WILL collide.

**Fix:** flashcard IDs should be subject-prefixed when the schedule is shared:
- MN: `mn-ch1-p1`
- Pharm: `pharm-ch1-p1`

OR keep separate schedules (`nur2460_atipharm_fc_schedule`).

**Current state in MN file:** uses unprefixed `ch1-p1` — this works because Pharm Flashcards hasn't been built yet. When Pharm Flashcards is added, this needs resolving.

#### B.1.11 Banner-less chapter

**Anti-pattern:** chapter missing `<div class="chapter-banner">`.

**Modal effect:** modal header shows blank meta and "Chapter" as title.

**Fix:** every chapter MUST have the banner with:
```html
<div class="chapter-banner">
  <div class="chapter-meta">Unit X · UnitName · Chapter N</div>
  <h2 class="chapter-name"><em>Chapter Title</em></h2>
  <p class="chapter-lede">Brief 1-2 sentence framing.</p>
</div>
```

#### B.1.12 Empty or placeholder content

**Anti-pattern:** chapter has TL;DR + ALS + Exercises but content-sections are stubbed ("TODO: write content").

**Rule:** never ship placeholder content. Either complete it or remove the chapter from the build.

**Detection:** validation script can grep for "TODO", "Lorem", "Placeholder", "TBD", "FIXME".

---

### 15.3 Edge Cases — Templates

> *Consolidated from former Addendum B.2.*

#### B.2.1 Template type with 0 examples in a subject

**Reality check:** MN has 0 Growth & Development templates (G&D is a peds topic). PD has 1 Concept Analysis template; MN has 2.

**Rule:**
- Still include the accordion in the Templates file (for consistency across subjects)
- Show "0 examples" in the accordion count
- Don't error on empty `.example-stack`

**Pattern:**
```html
<div class="tpl-accordion" id="growth-development-acc">
  <div class="tpl-acc-header">
    <span class="acc-caret">▾</span>
    <span class="acc-name">Growth & Development</span>
    <span class="acc-count">0 examples</span>
  </div>
  <div class="tpl-acc-body">
    <div class="acc-empty">
      No examples of this template type for Maternal-Newborn.
      Growth & Development templates appear primarily in Pediatric content.
    </div>
  </div>
</div>
```

#### B.2.2 Template example referenced in 2+ chapters

**When does this happen:** a single template (e.g., Combined Oral Contraceptives) is clinically relevant in chapter 1 (contraception) AND chapter 9 (drug therapy in pregnancy).

**Rule:** the template-card has ONE primary chapter (`data-ch="1"` and the `.ex-chip` shows "Ch 1"). The OTHER chapter's `tpl-bridge` can still link to it.

**Result:** `Elevated MN Book.html#ch1-hormonal` and `Elevated MN Book.html#ch9-meds` both have an `<li>` linking to `Elevated MN Templates.html#ex-ch1-cocs` — the template appears in both bridges but only lives once.

#### B.2.3 Example with no source-chapter link

**When does this happen:** a template covers cross-cutting content that doesn't map cleanly to one chapter.

**Rule:** still set `data-ch=""` to empty AND omit the `.ex-jump` link. Use `data-ch="0"` to indicate "no specific chapter".

```html
<article class="example-card" id="ex-newborn-feeding" data-ch="0" data-type="bc">
  <header class="ex-head">
    <span class="ex-chip">General</span>
    <h3 class="ex-title">Newborn Feeding (General)</h3>
    <!-- no .ex-jump link -->
    <button class="ex-expand-btn">⛶</button>
  </header>
  ...
</article>
```

#### B.2.4 Filled/Blank toggle with sparse content

**When does this happen:** an example has some `.{type}-value` fields filled but some empty (because the source PDF didn't have that field for that example).

**Rule:** empty value fields should still have a placeholder so Blank mode shows consistent underlines.

```html
<div class="bc-field">
  <div class="bc-label">Underlying Principles</div>
  <div class="bc-value"><em>Not specified in source content</em></div>
  <div class="bc-blank">_________________________________</div>
</div>
```

**Don't:** omit the field entirely. The template structure expects all standard fields per type.

---

### 15.4 Edge Cases — Flashcards

> *Consolidated from former Addendum B.3.*

#### B.3.1 Empty schedule on first load

**Symptom:** user opens Flashcards before rating any prompts in Book.

**Behavior:** schedule is `{}`. `getNextDueCard()` returns null. UI shows `#fcEmpty` with "No cards due right now" message and a link to open the book.

**Don't:** error or show empty card frame. Empty state has its own UI.

#### B.3.2 Card with no `nextReview` field

**Symptom:** a card object in schedule lacks `nextReview` (from older save format or partial write).

**Rule:** treat as due now. `getNextDueCard()`:
```javascript
if (!c.nextReview) return true;  // treat as due
```

#### B.3.3 Card type that isn't in the standard 4 + 3

**Symptom:** schedule contains a card with `type: "foobar"`.

**Rule:** render it with the generic accent-colored chip (`.fc-card-type-other` class). Don't crash.

```css
.fc-card-type-other { background: var(--text3); }
```

```javascript
var typeClass = ['CONTENT','JUDGMENT','PRINCIPLE','PRIORITY','concept','warning','calc']
                  .indexOf(card.type) >= 0
                  ? 'fc-card-type-' + card.type.toLowerCase()
                  : 'fc-card-type-other';
```

#### B.3.4 LocalStorage full / quota exceeded

**Symptom:** `setItem()` throws `QuotaExceededError`.

**Rule:** `try/catch` every save. On failure, log a warning but don't crash.

**Recovery suggestion to user:** Storage panel "Reset all progress" button OR export + manually edit + import.

---

### 15.5 Edge Cases — Ui

> *Consolidated from former Addendum B.4.*

#### B.4.1 Very long chapter title in modal header

**Symptom:** Chapter name overflows on mobile.

**CSS handling:**
```css
.modal-title {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;     /* on mobile only */
}
@media (max-width: 600px) {
  .modal-title { white-space: nowrap; }
}
@media (min-width: 601px) {
  .modal-title { white-space: normal; }
}
```

#### B.4.2 Very long tab labels

`buildTabLabel()` already truncates to 28 chars with `…`. But if h2 has rich HTML, the truncation should be of the text content, not HTML.

```javascript
function buildTabLabel(section, index) {
  if (section.classList.contains('brief-card')) return 'TL;DR';
  if (section.classList.contains('tpl-bridge')) return 'Templates';
  if (section.id && /-exercises$/.test(section.id)) return 'Practice';
  var h2 = section.querySelector('h2');
  var label = h2 ? h2.textContent.trim() : ('Section ' + (index + 1));
  // ALWAYS use textContent, never innerHTML, for the truncation source
  if (label.length > 28) label = label.substring(0, 26) + '…';
  return label;
}
```

#### B.4.3 Bookmarks count badge with 100+ items

**Symptom:** badge widens and overlaps the button text.

**CSS handling:**
```css
.bookmarks-count-badge {
  min-width: 18px;
  max-width: 30px;
  overflow: hidden;
  text-overflow: ellipsis;
}
```

For 100+ bookmarks: display "99+" instead of actual count.

```javascript
function updateBookmarkUI() {
  var count = loadBookmarks().length;
  var badge = document.getElementById('bookmarksCountBadge');
  if (!badge) return;
  if (count === 0) { badge.textContent = ''; return; }
  badge.textContent = count > 99 ? '99+' : count;
}
```

#### B.4.4 Print overlay with very long content

**Symptom:** Print preview is one giant page; browser doesn't paginate well.

**Rule:** every `.print-chapter` has `page-break-after: always` in print CSS. Each chapter renders on its own page set.

**Don't:** disable page-breaks to "save paper". Pagination is critical for readability.

#### B.4.5 Theme toggle in middle of modal interaction

**Symptom:** user opens modal in dark mode, toggles to light, sees text contrast issues.

**Rule:** test every CSS variable in BOTH modes for every component. See ADDENDUM C.4 for contrast verification.

**Fix pattern:** any text on a colored background should use `var(--bg)` (auto-flips with theme), not a hardcoded color.

#### B.4.6 Search query matches inside HTML markup

**Anti-pattern:** searching for "class" matches `class="exercise"` in HTML, returning false hits.

**Fix:** `handleSearch()` uses `textContent` not `innerHTML` for matching. Already handled in v2 PART 7.15.

---

### 15.6 Edge Cases — Data Integrity

> *Consolidated from former Addendum B.5.*

#### B.5.1 User imports a backup from different subject

**Symptom:** user exports MN backup, imports it on PD Hub.

**Behavior:** keys with `nur2460_` prefix get written but PD reads `atipd_` keys. The MN data is "there" but PD won't see it.

**Rule:** import doesn't validate subject match. Could be a feature (cross-subject sync) or a bug.

**Recommendation:** warn the user before importing:
```javascript
var payload = JSON.parse(reader.result);
if (payload.subject && payload.subject !== CURRENT_SUBJECT) {
  if (!confirm('This backup is from ' + payload.subject + ' but you\'re on ' + CURRENT_SUBJECT + '. Import anyway?')) return;
}
```

#### B.5.2 Corrupted JSON in localStorage

**Recovery:** every `loadX()` function uses `try/catch` and returns default empty object. Corruption = silent reset for that key.

**User-facing recovery:** Storage panel shows the corrupted key with its size. User can delete it via "Reset all progress" or by manually opening DevTools.

#### B.5.3 Schema version drift

**Reality check:** v1 schedule shape may differ from v2 (new fields added).

**Rule:** when loading, fill in missing fields with defaults:
```javascript
function loadFcSchedule() {
  var raw = localStorage.getItem(SCHED_KEY) || '{}';
  var s;
  try { s = JSON.parse(raw); } catch(e) { return {}; }
  Object.values(s).forEach(function(c) {
    if (typeof c.reps === 'undefined') c.reps = 0;
    if (typeof c.ef === 'undefined') c.ef = 2.5;
    if (typeof c.interval === 'undefined') c.interval = 1;
  });
  return s;
}
```

---

### 15.7 Subject Deviation Log

> *Consolidated from former Addendum C.3.*

#### C.3.1 Why subjects deviate

Each subject was built at a different stage of the project's evolution. Earlier subjects (PD) used different localStorage conventions than later ones (Pharm). Rather than retrofit, the deviations were preserved to avoid breaking existing user data.

#### C.3.2 LocalStorage prefix differences

| Subject | Book progress key | Theme key | FC schedule | Bookmarks | NCLEX done |
|---|---|---|---|---|---|
| MN | `nur2460_atimn_progress` | `nur2460_theme` | `nur2460_fc_schedule` (shared) | `nur2460_bookmarks` (shared) | `nur2460_nclex_done` (shared) |
| Pharm | `nur2460_atipharm_progress` | `nur2460_theme` (shared with MN) | `nur2460_fc_schedule` (shared with MN) | `nur2460_bookmarks` (shared with MN) | `nur2460_nclex_done` (shared with MN) |
| PD | `atipd_book_progress` | `atipd_theme` (separate!) | `atipd_fc_schedule` (separate) | `atipd_bookmarks` (separate) | `atipd_nclex_done` (separate) |

#### C.3.3 Why MN and Pharm share keys

MN and Pharm were built second/third. The decision was: a student studying both subjects in the same week wants:
- ONE bookmarks list (cross-subject)
- ONE flashcard queue (cross-subject review)
- SAME theme everywhere

So MN+Pharm share `nur2460_fc_schedule`, `nur2460_bookmarks`, `nur2460_nclex_done`, `nur2460_theme`.

#### C.3.4 Why PD is fully separate

PD was built first as the proof-of-concept. By the time MN was started, the convention had shifted to namespace prefixing. Rather than migrate PD users, PD keeps its own namespace.

**Result:** PD theme toggle is independent of MN/Pharm theme. PD bookmarks don't appear in MN/Pharm.


#### C.3.5 Cross-subject schedule sharing — the contamination trap

**Problem (discovered late in v3):** When two subjects share a localStorage `fc_schedule` key (MN and Pharm both use `nur2460_fc_schedule`), the Hub's "in deck" counter naively reads `Object.keys(schedule).length` and gets a number that includes:

1. Entries the current subject's user has actually rated (correct)
2. **Orphan entries** from past subjects that previously shared this key
3. Cards added through subject Y's Flashcards page if subject Y also uses the same key

PD originally shared `nur2460_fc_schedule` with MN, then was split off to `atipd_fc_schedule` via a migration that **COPIED** entries (so PD users wouldn't lose progress). The copy-without-delete left ~359 PD card entries as orphans in `nur2460_fc_schedule`. Once Pharm joined MN in sharing that key, the Pharm Hub's counter read those orphans and displayed 359 instead of the user's actual Pharm progress.

**Why "just delete after copy" doesn't work:** at the time of the original PD split, the migration couldn't tell which entries were PD-origin vs. MN-origin since both used the same `fc-chN-{slug}` ID scheme. Deleting all entries would have wiped MN users' progress too.

**The fix (now standard in v3):** every Hub that reads a shared schedule must embed its subject's `VALID_IDS` Set, extracted at build time from that subject's `STARTER_DECK`:

```javascript
var FC_KEY   = 'nur2460_fc_schedule';

// ===== Valid card IDs for this subject's deck (from STARTER_DECK) =====
var VALID_IDS = new Set(['fc-ch1-foo', 'fc-ch1-bar', /* ...all 260 IDs... */]);

// One-time cleanup: drop any entries whose IDs aren't in this subject's deck
try {
  var __sched = loadJson(FC_KEY);
  var __cleaned = false;
  for (var __k in __sched) {
    if (!VALID_IDS.has(__k)) { delete __sched[__k]; __cleaned = true; }
  }
  if (__cleaned) {
    try { localStorage.setItem(FC_KEY, JSON.stringify(__sched)); } catch (e) {}
  }
} catch (e) {}

function countDueCards() {
  var schedule = loadJson(FC_KEY);
  // ...
  for (var k in schedule) {
    if (!VALID_IDS.has(k)) continue;  // skip cross-subject entries
    // count normally
  }
}
```

**Architectural rules for future subject builds:**
- If a new subject will SHARE a schedule key with an existing subject, embed its `VALID_IDS` in the Hub from day one. Never assume the schedule contains only your subject's cards.
- If a new subject will have its OWN schedule key (like PD): write the split migration as a **MOVE BY MEMBERSHIP**, not a bulk copy. Iterate entries, move each to the new key only if it's in the new subject's deck, and explicitly delete from source.
- Always include a `VALID_IDS` filter in `countDueCards` even if the schedule isn't shared today. Future architectural changes may share it tomorrow.
- ID schemes between subjects sharing a key MUST be designed to avoid collision. MN+Pharm verified zero collision.

**Where this is implemented in v3:**
- MN Hub: `VALID_IDS = Set` of MN's 122 STARTER_DECK IDs
- Pharm Hub: `VALID_IDS = Set` of Pharm's 260 STARTER_DECK IDs
- PD Hub: no filter needed today (PD has its own `atipd_fc_schedule`), but adding the same pattern is recommended for symmetry.

#### C.3.5 Template key inconsistency

The Templates page progress key is even more inconsistent:
- MN: `nur2460_atimnTemplates_progress` (camelCase mid-key!)
- PD: `atipd_templates_progress`
- Pharm: not built yet

The MN key was a typo that became permanent. **Don't fix this** — fixing it breaks existing user data.

#### C.3.6 Flashcard ID collision risk

When MN and Pharm share `nur2460_fc_schedule`, their card IDs MUST not collide. Both subjects use `chN-p1` / `chN-p2` for typed prompts and `fc-chN-{name}` for inline mid-reads.

**Collision scenarios:**
- MN ch1-p1 vs Pharm ch1-p1 → SAME KEY → one overwrites the other

**Current mitigation:** When building Pharm, ALL flashcard IDs must be prefixed:
- Pharm `MID_PROMPTS["ch1"][0].id = "pharm-ch1-p1"` (not `ch1-p1`)
- Pharm inline mid-reads: `data-fc-id="fc-pharm-ch1-{name}"`

**Implementation needed:** when adding Pharm Flashcards, prefix IDs OR migrate to separate schedule key. See decision below.

#### C.3.7 Decision matrix for new subjects

When adding a new subject (e.g., Community Health, Mental Health):

**Option A: Share with MN+Pharm namespace**
- Use `nur2460_` prefix
- Share bookmarks, theme, fc_schedule, nclex_done
- Pro: cross-subject continuity
- Con: card IDs must be globally unique (subject prefix required)

**Option B: Fully separate namespace (like PD)**
- Use `ati{subj}_` prefix
- Own bookmarks, theme, fc_schedule, etc.
- Pro: no collision risk
- Con: students lose cross-subject features

**Recommendation:** Option A for any subject within the NUR 2460 curriculum (which is what the suite was built for). Option B only if launching a separate course's suite.

#### C.3.8 Migration path for unifying PD with MN/Pharm

If you ever want to merge PD into the shared namespace:

```javascript
// Migration script — run once, on PD Hub
(function migratePDToShared() {
  var migrations = [
    ['atipd_bookmarks', 'nur2460_bookmarks'],   // merge into shared
    ['atipd_nclex_done', 'nur2460_nclex_done'],
    ['atipd_fc_schedule', 'nur2460_fc_schedule'],  // requires ID prefixing first
    ['atipd_theme', 'nur2460_theme']
  ];

  migrations.forEach(function(pair) {
    var oldKey = pair[0], newKey = pair[1];
    var oldData = localStorage.getItem(oldKey);
    if (!oldData) return;
    var existing = localStorage.getItem(newKey);
    if (!existing) {
      localStorage.setItem(newKey, oldData);
    } else {
      // Merge logic per key type
      try {
        var oldObj = JSON.parse(oldData);
        var newObj = JSON.parse(existing);
        if (Array.isArray(oldObj)) {
          // Bookmarks — concat with dedup
          var merged = newObj.concat(oldObj.filter(function(b) {
            return !newObj.some(function(n) { return n.chapterId === b.chapterId && n.sectionId === b.sectionId; });
          }));
          localStorage.setItem(newKey, JSON.stringify(merged));
        } else {
          // Objects — old wins (PD data preserved)
          Object.assign(newObj, oldObj);
          localStorage.setItem(newKey, JSON.stringify(newObj));
        }
      } catch(e) {}
    }
  });
})();
```

**Don't run this without explicit user consent** and a backup export first.

---

### 15.8 Procedure — Update Existing Content Without Breaking User Data

> *Consolidated from former Addendum F.4.*

Use case: fixing a typo, adding a missed risk factor, correcting a wrong rationale.

#### F.4.1 Safe changes (no user data impact)

These can be made freely:
- Text content within sections
- HTML formatting changes that don't alter IDs
- CSS adjustments
- Adding new abbreviations
- Adding new mid-reads (they're inline)
- Adding new condition-blocks within an existing section
- Adding new finding-cards within a condition-block

#### F.4.2 Changes that affect user data

These need extra care:

**Changing a chapter ID** (`ch5` → `ch5b`):
- Old key `progress.ch5: 2` becomes orphan
- User loses "read" status for that chapter
- **Mitigation:** include a migration in Book load script:
  ```javascript
  (function migrateChapterIds() {
    var p = JSON.parse(localStorage.getItem('nur2460_atimn_progress') || '{}');
    var migrations = { 'ch5': 'ch5b' };
    var changed = false;
    Object.keys(migrations).forEach(function(oldId) {
      if (oldId in p) {
        p[migrations[oldId]] = p[oldId];
        delete p[oldId];
        changed = true;
      }
    });
    if (changed) localStorage.setItem('nur2460_atimn_progress', JSON.stringify(p));
  })();
  ```

**Changing a section ID within a chapter** (`ch5-nutrition` → `ch5-diet`):
- Bookmarks pointing to the old section ID won't open
- **Mitigation:** add to bookmark migration:
  ```javascript
  (function migrateBookmarkIds() {
    var b = JSON.parse(localStorage.getItem('nur2460_bookmarks') || '[]');
    var migrations = { 'ch5-nutrition': 'ch5-diet' };
    var changed = false;
    b.forEach(function(bm) {
      if (bm.sectionId in migrations) {
        bm.sectionId = migrations[bm.sectionId];
        changed = true;
      }
    });
    if (changed) localStorage.setItem('nur2460_bookmarks', JSON.stringify(b));
  })();
  ```

**Removing or renaming a flashcard prompt** (`ch5-p1` removed):
- Schedule entry for that ID becomes orphan
- User's review history is "lost" for that prompt
- **Mitigation:** option 1 — leave it (orphans don't break anything); option 2 — purge:
  ```javascript
  (function purgeRemovedPrompts() {
    var validIds = new Set();
    Object.keys(MID_PROMPTS).forEach(function(ch) {
      MID_PROMPTS[ch].forEach(function(p) { validIds.add(p.id); });
    });
    // Also add inline mid-read IDs
    document.querySelectorAll('.mid-read[data-fc-id]').forEach(function(el) {
      validIds.add(el.dataset.fcId);
    });
    var s = JSON.parse(localStorage.getItem('nur2460_fc_schedule') || '{}');
    Object.keys(s).forEach(function(id) {
      if (!validIds.has(id)) delete s[id];
    });
    localStorage.setItem('nur2460_fc_schedule', JSON.stringify(s));
  })();
  ```

**Removing a template** (an `ex-chN-{name}` deleted):
- `nur2460_atimnTemplates_progress` has stale entry
- Pickup panel might point to non-existent ID
- **Mitigation:** purge studied entries for removed IDs:
  ```javascript
  (function purgeRemovedTemplates() {
    var validIds = new Set();
    document.querySelectorAll('.example-card[id^="ex-"]').forEach(function(el) {
      validIds.add(el.id);
    });
    var s = JSON.parse(localStorage.getItem('nur2460_atimnTemplates_progress') || '{}');
    Object.keys(s).forEach(function(id) {
      if (!validIds.has(id)) delete s[id];
    });
    localStorage.setItem('nur2460_atimnTemplates_progress', JSON.stringify(s));
  })();
  ```

#### F.4.3 Migration script template

```javascript
// Place inside Book Script 1 (Main IIFE), before DOMContentLoaded listener
(function runDataMigrations() {
  var MIGRATION_VERSION_KEY = 'nur2460_atimn_migration_version';
  var current = parseInt(localStorage.getItem(MIGRATION_VERSION_KEY) || '0', 10);
  var migrations = [
    // Version 1: rename ch5-nutrition section
    function v1() {
      var b = JSON.parse(localStorage.getItem('nur2460_bookmarks') || '[]');
      b.forEach(function(bm) {
        if (bm.sectionId === 'ch5-nutrition') bm.sectionId = 'ch5-diet';
      });
      localStorage.setItem('nur2460_bookmarks', JSON.stringify(b));
    },
    // Version 2: purge orphan flashcards
    function v2() {
      // ... migration logic
    }
  ];
  for (var v = current; v < migrations.length; v++) {
    try {
      migrations[v]();
      localStorage.setItem(MIGRATION_VERSION_KEY, String(v + 1));
    } catch(e) {
      console.warn('Migration v' + (v + 1) + ' failed:', e);
      break;
    }
  }
})();
```

This pattern lets you ship migrations safely — each user runs them once.

---

### 15.9 Subject-Specific Structural Variations

> *Consolidated from former Addendum H.3.*

The Hub layout adapts per subject. Below are the verified structures for each.

#### H.3.1 MN (Maternal-Newborn)

```
Stats:        27 Chapters · 4 Units · 105 Worked Templates · 8 Template Types · 122 Starter Cards
Theme color:  #d97706 (amber dark)
Accent:       #fbbf24 (amber-400)
Prefix:       nur2460_atimn_*  for Book progress
              nur2460_atimnTemplates_*  for Templates
              nur2460_*  (shared) for theme, bookmarks, FC, NCLEX

Units (4):
  Unit 1  Antepartum     Ch 1 – 10
  Unit 2  Intrapartum    Ch 11 – 14
  Unit 3  Postpartum     Ch 15 – 22
  Unit 4  Newborn        Ch 23 – 27

Template type counts:
  Basic Concept:           14
  Diagnostic Procedure:    6
  Growth & Development:    0  (peds-only topic)
  Medication:              15
  Nursing Skill:           4
  System Disorder:         60
  Therapeutic Procedure:   35
  Concept Analysis:        2  (Tissue Perfusion, Attachment)
```

#### H.3.2 PD (Pediatric)

```
Stats:        44 Chapters · 3 Units · 167 Worked Templates · 8 Template Types · 188 Starter Cards
Theme color:  (use a darker blue, e.g. #2563eb)
Accent:       #60a5fa (blue-400)
Prefix:       atipd_*  ALL keys (no sharing with MN/Pharm)

Units (3):
  Unit 1  Foundations               Ch 1 – ?
  Unit 2  System Disorders          Ch ? – ?
  Unit 3  Other Specific Needs      Ch ? – 44

Template type counts:
  Basic Concept:           ~12
  Diagnostic Procedure:    ~4
  Growth & Development:    16  (largest of any subject)
  Medication:              ~18
  Nursing Skill:           ~6
  System Disorder:         ~65
  Therapeutic Procedure:   ~28
  Concept Analysis:        1
```

**Note:** specific chapter counts within units 1-2 weren't extracted; verify against PD Hub if precision needed.

#### H.3.3 Pharm (Pharmacology)

```
Stats:        49 Chapters · 13 Units · 50 Worked Templates · 5 Template Types Used · 260 Starter Cards (98 typed + 162 inline)
Light-mode:   --accent #ea580c (burnt orange, universal light)  --accent2 #0f766e (teal)
Dark-mode:    --accent #fb923c (orange-400)  --accent2 #fdba74 (orange-300)
              --accent-soft rgba(251,146,60,0.12)
Prefix:       nur2460_atipharm_*  for Pharm-specific keys (book/templates progress)
              SHARES nur2460_fc_schedule, nur2460_fc_filters, nur2460_theme,
                     nur2460_last_template, nur2460_tpl_filters,
                     nur2460_bookmarks, nur2460_nclex_done, nur2460_last_chapter with MN

Sidebar unit filter groupings (6, consolidated from 13 source units):
  Principles      Ch 1 – 6     (Unit 1)
  Nervous         Ch 7 – 16    (Unit 2)
  Resp/Cardio     Ch 17 – 27   (Units 3-5)
  GI/Repro/MSK    Ch 28 – 38   (Units 6-9)
  Endo/Immune     Ch 39 – 42   (Units 10-11)
  Infection/Other Ch 43 – 49   (Units 12-13)

Units (13, full granularity in Book):
  Unit 1   Pharmacological Principles    Ch 1 – 6
  Unit 2   Nervous System                Ch 7 – 16
  Unit 3   Respiratory                   Ch 17 – 18
  Unit 4   Cardiovascular                Ch 19 – 24
  Unit 5   Hematologic                   Ch 25 – 27
  Unit 6   GI & Nutrition                Ch 28 – 30
  Unit 7   Reproductive                  Ch 31 – 32
  Unit 8   Joint & Bone                  Ch 33 – 34
  Unit 9   Pain & Inflammation           Ch 35 – 38
  Unit 10  Endocrine                     Ch 39 – 40
  Unit 11  Immune                        Ch 41 – 42
  Unit 12  Infection                     Ch 43 – 48
  Unit 13  Other Medications             Ch 49

Template counts (50 worked examples across 5 used types):
  Medication             41   (drug-specific scenarios; the dominant type for Pharm)
  System Disorder         3
  Nursing Skill           3
  Therapeutic Procedure   2
  Basic Concept           1
  Diagnostic Procedure    0   (not used in Pharm — clinical procedures live in MN/PD)
  Growth and Development  0   (not applicable)
  Concept Analysis        0   (not used)

Flashcards (260 cards, 2 sources, sharing nur2460_fc_schedule with MN):

  Source 1 — Typed mid-prompts (98 cards, 2 per chapter × 49 chapters):
    Injected dynamically via JS MID_PROMPTS dict after each chN-tldr anchor.
    ID scheme: fc-chN-pN  (e.g., fc-ch11-p1)
    Type breakdown:
      concept    58   (CONTENT/JUDGMENT/PRINCIPLE source prompt types)
      warning    39   (PRIORITY source prompt type — safety/decision urgency)
      calc        1   (ch3 dosage-calc prompt)

  Source 2 — Inline mid-reads (162 cards, variable density across 49 chapters):
    Static <aside class="mid-read"> elements embedded inside chN-tldr sections.
    ID scheme: fc-chN-{slug}  (e.g., fc-ch12-naloxone-half-life)
    Type breakdown (approximate):
      warning   ~96   (chapter-specific safety/timing catches)
      concept   ~50   (differentiations, mechanisms, ranges)
      priority  ~14   (highest-urgency: NTG attack, torsades, hemolytic reaction, etc.)
      calc       ~2   (ch3 pediatric safe-dose, microdrip shortcut)

  Density variance (Pharm content is heterogeneous, NOT a flat 3 per chapter):
    Heavy (4-5):  ch5, ch9, ch10, ch13, ch14, ch19-23 (multiple), ch25, ch27,
                  ch28, ch32, ch35, ch39, ch43, ch44, ch47
    Standard (3): most chapters
    Light (2):    ch3, ch17, ch29, ch30, ch38, ch49 (less novel content)

  ID collision safety: 0 overlap with MN (122 IDs use fc-chN-{semantic-slug}).
  Pharm IDs use either fc-chN-pN or fc-chN-{slug}. Verified across MN and Pharm.

ALS coverage: All 49 chapters now have an Active Learning Scenario (ch3 has a custom-authored
              dosage-calc scenario since the source PDF skips it).
              ch5 has an extra ch5-als-2 (warfarin + St. John's wort) from a prior content addition.
```


##### H.3.3.5 Ch5 dual-content note (v3 cleanup)

Pharm ch5 (Adverse Effects, Interactions, and Contraindications) was originally extracted with **two complete content sets** from the source PDF — same chapter authored twice with different emphases. Earlier work renamed duplicate IDs to be unique but left H2 headings duplicated. v3 cleanup renamed the H2s to disambiguate. The two halves were intentionally preserved (both contribute unique content):

**First half** (sections in document order):
1. ch5-tldr (TL;DR · One-glance summary)
2. ch5-types ("Types of Adverse Reactions — Overview")
3. ch5-anaphylaxis ("Anaphylaxis — Recognition and Response")
4. ch5-interactions ("Drug Interactions — Mechanisms")
5. ch5-pregnancy ("Pregnancy and Lactation Considerations")
6. ch5-als ("Active Learning Scenario · Gentamicin + Naproxen")
7. ch5-exercises ("Practice · Application Exercises (Set 1)" — 5 NCLEX questions)

**Second half** (supplementary content):
8. ch5-reactions ("Adverse Reactions — Common Patterns")
9. ch5-special ("Serious & Special Reactions" — SJS/TEN, Black Box, Teratogenic)
10. ch5-interactions-2 ("Drug Interactions — CYP450 and Foods")
11. ch5-als-2 ("Active Learning Scenario · Warfarin + St. John's Wort")
12. ch5-exercises-2 ("Practice · Application Exercises (Set 2)" — 5 more NCLEX questions)

ch5 inline mid-reads (5 cards) anchor to `ch5-tldr` and draw from BOTH halves' content:
- fc-ch5-anaphylaxis-first-line, fc-ch5-biphasic-monitor → from first half
- fc-ch5-sjs-culprits, fc-ch5-cyp450-inducers, fc-ch5-cyp450-inhibitors-grapefruit → from second half

##### H.3.3.6 Pharm inline mid-read density (v3 retrospective)

162 inline mid-reads across all 49 chapters, **variable density** by content richness:

| Density | Card count | Chapters |
|---|---|---|
| Heavy | 4–5 each | ch5, ch9, ch10, ch13, ch14, ch19, ch20, ch21, ch23, ch25, ch27, ch28, ch32, ch35, ch39, ch43, ch44, ch47 (18 chapters) |
| Standard | 3 each | most chapters (25) |
| Light | 2 each | ch3, ch17, ch29, ch30, ch38, ch49 (6 chapters) |

**Why variable density (not the flat 3-per-chapter of the MN model):** Pharm content is heterogeneous — ch5 (adverse effects) alone justifies 5 distinct safety cards; ch3 (dosage calc) has 2 useful formulas and not much else. Flat density would underuse rich chapters and force filler in thin ones. SM-2 mixes everything in the queue regardless, so uneven coverage doesn't disadvantage the student.

**Authoring pipeline (followed for sub-batches A–E, 33+30+34+33+29 cards):**
1. Extract each chapter's TL;DR text via Python script
2. Draft cards in JSON file (`pharm_inline_batch_X.json`) — one card = `{id, ch, type, anchor, q, a}`
3. Insert `<aside class="mid-read">` blocks into Pharm Book just before each chapter's closing `</section>` of `chN-tldr`
4. Append matching entries to STARTER_DECK in Pharm Flashcards (with comma-boundary check)
5. Validate: `node --check` on every script block; cross-file ID parity check

**Lesson from sub-batch A insertion bug:** When appending to a JS array literal, ALWAYS verify whether the last existing entry has a trailing comma. The Flashcards STARTER_DECK initially had no trailing comma; appending new entries on new lines without a separator produced two adjacent objects → JS SyntaxError → "Uncaught Error: Script error" → entire page broke. Fix is either (a) add the missing comma, (b) insert with leading comma, or (c) rewrite the array boundary explicitly. The pipeline now does an explicit boundary check before each insertion.

#### H.3.4 Hub layout adaptation per subject

**Stats row:** always 5 stats. If a count is unknown (subject not finished), display "—" instead of 0.

**Units-grid:** auto-adapts via `grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))`.
- 3 units → single row of 3
- 4 units → single row of 4 (tight) or 2x2 on narrow screens
- 13 units → multiple rows (wrap)

**Types-grid:** always 8 rows (one per template type). 2-column on desktop, 1-column on mobile.

#### H.3.5 Adapting the storage panel per subject

The Storage panel reads all keys matching the subject prefix. The prefix depends on subject:

```javascript
// MN Hub:
var PREFIX = 'nur2460_';   // shows MN-specific + shared keys

// PD Hub:
var PREFIX = 'atipd_';     // shows PD-specific keys only

// Pharm Hub:
var PREFIX = 'nur2460_';   // shows Pharm + shared keys (overlap with MN)
```

**Implication:** MN Hub and Pharm Hub both show overlapping keys in their storage panel. This is intentional — both subjects use the same shared keys for theme, bookmarks, flashcards.

**Resetting:** "Reset all progress" only clears keys matching the prefix. So:
- MN reset clears `nur2460_atimn_progress`, but NOT `nur2460_fc_schedule` (since the latter is shared)... unless the prefix check is just `'nur2460_'`, in which case it clears EVERYTHING with that prefix including Pharm's data.

**This is a known quirk** — see G.5.5. Resetting MN may wipe Pharm flashcard progress because they share `nur2460_fc_schedule`. Users should export backup first.

#### H.3.6 Per-subject Book Script 3 (mid-prompts) location

The mid-prompts script must be the LAST inline script in the Book, after the NCLEX filter script. Order in Book file:

```
<script>/* Main IIFE — 49 functions */</script>
<script>/* BATCH 3 NCLEX filter + answered tracking */</script>
<script>/* Mid-read flashcard prompts (MID_PROMPTS injection) */</script>
</body>
```

When building a new subject's Book, copy this script ORDER. Inverting it causes injectAllPrompts() to fire before buildPromptCard() is defined, throwing a ReferenceError.

#### H.3.7 Cross-subject Flashcards strategy

**Current state (resolved — Option A shipped):**
- MN: `nur2460_fc_schedule` (shared)
- Pharm: `nur2460_fc_schedule` (shared — same key as MN)
- PD: `atipd_fc_schedule` (still separate; PD remains in its own namespace)

**The decision matrix that was considered:**

Option A — Shared schedule (MN+Pharm cards in one queue):
- Card IDs must be unambiguous across both subjects. ✅ This holds in our case:
  - MN uses `fc-chN-{semantic-slug}` (e.g., `fc-ch1-naegele`, `fc-ch1-spinnbarkeit`)
  - Pharm uses `fc-chN-pN` (e.g., `fc-ch11-p1`, `fc-ch11-p2`)
  - Verified: 0 ID overlap between MN (122 cards) and Pharm (98 cards)
- Separate Flashcards files each contribute to the same shared schedule.

Option B — Separate schedules:
- Pharm Flashcards uses `nur2460_atipharm_fc_schedule`
- No ID prefixing needed
- Two separate Flashcards files, two separate queues

**Chosen:** Option A — matches §C.3.3's rationale ("one queue across subjects studied in same week")
and matches MN's live implementation. The ID schemes were already non-colliding so no prefixing
was required. Earlier guide language preferring Option B is superseded by this section.

**For PD** — if you ever want to fold PD into the shared namespace, see §C.3.8 migration path
and additionally prefix PD card IDs (PD uses `fc-ch1-{slug}` which DOES collide with MN's pattern).

---

---

## PART 16 — QUICK REFERENCE CHEATSHEET

### Chapter section IDs
```
chN-tldr        — TL;DR (brief-card)
chN-{topic}     — content sections (named by topic)
chN-als         — Active Learning Scenario
chN-exercises   — Practice questions
chN-templates   — Templates bridge
```

### Tab label rules
```
brief-card    → "TL;DR"
tpl-bridge    → "Templates"
*-exercises   → "Practice"
other         → h2 text, truncated to 28 chars + "…"
```

### Subject accents (--accent only)
```
MN     #fbbf24  amber-400
PD     #60a5fa  blue-400
Pharm  #fb923c  orange-400
Index  #a78bfa  purple-400
```

### Light-mode accents
```
--accent   #ea580c (burnt orange)
--accent2  #0f766e (teal)
```

### Breakpoints
```
≤ 900px   primary mobile (sidebar → off-screen + hamburger)
≤ 600px   tight phones (button size tweaks only)
```

### LocalStorage keys (subject prefixes)
```
MN/Pharm     nur2460_*
PD           atipd_*
Hub progress reads from subject-specific keys
```

### 3 inline scripts in Book (in order)
```
1. Main IIFE (49 functions)
2. NCLEX filter + answered tracking
3. Mid-read flashcard prompts (MID_PROMPTS injection)
```

### 4 typed mid-prompt categories
```
CONTENT    blue  #4fa3e0   factual recall
JUDGMENT   purp  #a78bfa   decision-making
PRINCIPLE  teal  #14b8a6   rationale
PRIORITY   red   #ef4444   triage
```

### 3 inline mid-read types
```
concept    yellow accent   factual recall
warning    red             safety alert
calc       blue            calculation
```

### 8 Template types
```
basic-concept           .bc-grid    3 fields
diagnostic-procedure    .dp-grid    9 fields
growth-development      .bc-grid    (reuses bc-grid)
medication              .med-grid   11 fields
nursing-skill           .ns-grid    7 fields
system-disorder         .sd-grid    12 fields
therapeutic-procedure   .tp-grid    9 fields
concept-analysis        .ca-grid    4 fields
```

### Required Hub sections (in order)
```
1. page-header   (back link + theme toggle)
2. hero          (h1 + sub)
3. stats         (5-column grid)
4. pickup-panel  (3 cards, conditionally shown)
5. primary-grid  (3 tool cards)
6. units-grid    (one card per unit)
7. types-grid    (one row per template type)
8. future-card
9. storage-panel (collapsed)
10. footer
```

### Keyboard shortcuts (Flashcards)
```
Space   reveal answer
1       Hard (rating 0)
2       Good (rating 3)
3       Easy (rating 5)
?       help
```

### Cross-tool sync localStorage keys
```
nur2460_last_chapter      Hub pickup panel reads, Book updates
nur2460_last_template     Hub pickup, Templates updates
nur2460_fc_schedule       Book writes (rate prompts), Flashcards reads
nur2460_bookmarks         Book writes, Book displays
nur2460_nclex_done        Book writes (reveal answer)
nur2460_theme             All tools read+write
```

### SM-2 rating values
```
Hard   0       reps=0, interval=1
Good   3       interval *= ef (or 1, 6 for first reviews)
Easy   5       interval *= ef (same as Good, but ef increases)
```

### Critical "do not" list
```
❌  Don't use html.light (use [data-theme="light"])
❌  Don't put chapter content outside chapter-pool
❌  Don't use <aside> as a tab (use <section>)
❌  Don't put inline mid-prompts inside chapter-banner
❌  Don't break the 3-script order in Book
❌  Don't use a single prefix for PD localStorage (it's atipd_, not nur2460_)
❌  Don't put scripts before the body content
❌  Don't forget the .tpl-bridge class on chN-templates
❌  Don't define .gd-grid (Growth & Dev uses .bc-grid)
❌  Don't forget to call injectAllPrompts() after main IIFE
```

---

# ADDENDUM A → CONSOLIDATED

> **NOTE:** Addendum A (Editorial Standards) has been promoted to **PART 14 — EDITORIAL STANDARDS** in the main body of the guide:
> - A.1 (Content-writing voice guide) → PART 14.1
> - A.2 (Mid-prompt selection rubric) → PART 14.2
> - A.3 (NCLEX question rubric) → PART 14.3

---

# ADDENDUM B → CONSOLIDATED

> **NOTE:** Addendum B (Structural edge cases & QA) has been consolidated:
> - B.1 (Chapter structure edge cases) → **PART 15.X Edge Cases — Chapter Structure**
> - B.2 (Templates edge cases) → **PART 15.X Edge Cases — Templates**
> - B.3 (Flashcards edge cases) → **PART 15.X Edge Cases — Flashcards**
> - B.4 (UI edge cases) → **PART 15.X Edge Cases — UI**
> - B.5 (Data integrity edge cases) → **PART 15.X Edge Cases — Data Integrity**
> - B.6 (QA checklists) → **PART 13.X Quality Assurance Checklists**

---

# ADDENDUM C → CONSOLIDATED

> **NOTE:** Addendum C (Reference data) has been consolidated:
> - C.1 (Cross-link map Book↔Templates) → **PART 7.X Cross-Link Map**
> - C.2 (PDF extraction tooling) → **PART 13.X PDF Extraction Tooling**
> - C.3 (Subject deviation log) → **PART 15.X Subject Deviation Log**
> - C.4 (Light-mode color contrast verification) → **PART 3.X Light-Mode Color Contrast Verification**

---

# ADDENDUM D → CONSOLIDATED

> **NOTE:** Addendum D (Reference Templates) has been consolidated:
> - D.1 (Full chapter skeleton) → **PART 7.22 Reference template — full chapter skeleton**
> - D.2 (Example-card templates per type) → **PART 8.12 Reference templates — one per template type**
> - D.3 (Example-card CSS reference) → **PART 10.6 Example-card CSS reference**

---

# ADDENDUM E → CONSOLIDATED

> **NOTE:** Addendum E (Reference Data) has been consolidated:
> - E.1 (Full ABBR_DICT, 277 entries) → **PART 7.23 Reference data — full ABBR_DICT**
> - E.2 (Full MID_PROMPTS, 54 prompts) → **PART 7.24 Reference data — full MID_PROMPTS**

---

# ADDENDUM F → CONSOLIDATED

> **NOTE:** Addendum F (Maintenance procedures) has been consolidated:
> - F.1 (Add a new chapter to an existing subject) → **PART 13.X**
> - F.2 (Add a new subject from scratch) → DISCARDED — duplicated by **PART 13.2 Build sequence (8 phases)**
> - F.3 (Add a new abbreviation) → **PART 7.X Procedure — Add A New Abbreviation**
> - F.4 (Update existing content without breaking user data) → **PART 15.X**
> - F.5 (Add a new template type) → **PART 8.X Procedure — Add A New Template Type**
> - F.6 (Backup & recovery) → **PART 6.X Backup & Recovery Procedure**
> - F.7 (Production deployment) → **PART 13.X Procedure — Production Deployment**

---

# ADDENDUM G — UNCERTAINTY LOG

What I'm confident about vs what I'm guessing about. This addendum exists because v1 of this guide had errors I didn't flag. v2 was audited against the working MN files, but extrapolation to PD, Pharm, and unbuilt subjects has limits.

If you find a claim that's wrong, you can use this log to estimate how badly I screwed up. Things in the "low confidence" zone are higher-risk for errors than things in the "verified" zone.

---

## G.1 HIGH CONFIDENCE — directly extracted from working MN files

These claims were verified by reading the actual MN Book / Templates / Hub files with grep / regex / parsing. If they're wrong, the source files are also wrong.

**v3 spot-check (2026-05-13):** Random sample verified against current MN files. All sampled claims match EXCEPT:
- "29 CSS variables in :root" → **Actual count is 21** (and 21 more overrides under `[data-theme="light"]` — possibly the original count summed both, but the v2 wording said "in :root"). Treat as 21 unique design tokens, with light-mode overrides for nearly all of them.
- Theme-color meta `#d97706` ✓ confirmed
- ABBR_DICT 277 entries ✓ confirmed exactly
- MID_PROMPTS 54 entries ✓ confirmed exactly
- MID_PROMPTS type distribution `{PRIORITY: 17, JUDGMENT: 17, CONTENT: 18, PRINCIPLE: 2}` ✓ matches exactly
- Inline mid-read types `{concept: 98, warning: 20, calc: 4}` ✓ matches exactly
- Breakpoints 900px and 600px ✓ confirmed present

So §G.1's general accuracy holds — one specific quantitative claim (CSS var count) is off.

```
✓ The 29 CSS variables in :root (extracted via regex from MN Book CSS)
✓ Light-mode color values (extracted from [data-theme="light"] rules)
✓ Subject accent colors for MN (#fbbf24 amber)
✓ Font families: DM Serif Display + DM Sans (verified in <head>)
✓ Font size scale (extracted: 8px, 9px, ..., 44px range)
✓ Border-radius scale (extracted: 2px, 3px, ..., 99px range)
✓ The 2 mobile breakpoints: 900px and 600px
✓ The @media (max-width:900px) block content for sidebar transformation
✓ The data-theme="light" attribute mechanism (not html.light)
✓ Theme-color meta value (#d97706 for MN)
✓ The 3 inline script order in Book (main IIFE → NCLEX → mid-prompts)
✓ The 49 function names in Book IIFE
✓ The 41 function names in Templates IIFE
✓ Chapter-pool display:none pattern
✓ Modal mechanism: clone direct child <section>[id] elements as tabs
✓ buildTabLabel() rules (brief-card→TL;DR, tpl-bridge→Templates, etc.)
✓ ABBR_DICT structure and the 277-entry count
✓ MID_PROMPTS data structure with all 54 prompts
✓ Mid-prompt type distribution: CONTENT 18, JUDGMENT 17, PRIORITY 17, PRINCIPLE 2
✓ Inline mid-read types: concept (98), warning (20), calc (4)
✓ NCLEX category distribution in MN exercises
✓ SATA frequency: ~36% of MN exercises
✓ LocalStorage key names for MN (extracted from JS)
✓ The 8 template types and their grid class names
✓ The full Book↔Templates cross-link map (ADDENDUM C.1)
✓ SM-2 algorithm implementation (extracted from rateCard)
✓ The 5-file architecture per subject
✓ Sidebar layout: 280px width, position fixed, transform on mobile
✓ Mobile floating buttons (hamburger top:66px, back-home top:14px)
✓ tab-strip scroll/fade mechanism
```

---

## G.2 MEDIUM CONFIDENCE — extracted but possibly incomplete

These were extracted from MN but I may have missed edge cases or only sampled.

**v3 status:** These are meta-disclaimers about incompleteness, not specific claims to verify. The v3 work didn't change the underlying state — MN files are unmodified except for the theme-persistence add in Book and Templates (§3.4). The caveats below still apply equally.

```
~ Specific CSS rules for components I extracted (.brief-card, .modal, etc.)
  → I extracted the rules but the file has 2000 lines of CSS; minor rules may be missed

~ The exact JavaScript implementation of every function
  → I summarized 49 functions; some line-by-line implementation may differ from
    what I wrote in PART 7. The function NAMES and basic LOGIC are correct.

~ The print-overlay HTML structure and CSS
  → I described the overall pattern but didn't fully extract the print CSS.
    @media print rules may have nuances I missed.

~ The exact order of items in the sidebar nav
  → Pattern is correct, but specific item ordering wasn't fully extracted

~ Exact event handler bindings
  → I documented the major listeners but smaller ones (focus, blur, etc.)
    may exist that I didn't catalog

~ The unit-bar-partial vs unit-bar-inner two-layer progress bar
  → Documented the concept but may have the exact CSS percentages wrong

~ Specific abbreviation tooltip positioning math
  → showTip() formula may differ slightly from what I described
```

---

## G.3 EXTRAPOLATED — applied from MN to PD/Pharm without verification

These claims about PD and Pharm were originally based on PATTERN MATCHING from MN. **v3 scrub (2026-05-13):** all seven claims have been verified against current PD and Pharm files. Verdicts inline.

### G.3.1 "PD uses atipd_ prefix" → **VERIFIED & EXPANDED**

PD uses **12 distinct `atipd_*` keys**: `atipd_book_progress`, `atipd_bookmarks`, `atipd_fc_filters`, `atipd_fc_schedule`, `atipd_last_chapter`, `atipd_last_template`, `atipd_nclex_done`, `atipd_pickup_dismissed`, `atipd_templates_progress`, `atipd_theme` (legacy — salvage-only after v3), `atipd_tpl_filters`, `atipd_tpl_progress`.

**Exception (v3 change):** `atipd_theme` is now legacy. PD's theme is read/written under the canonical `nur2460_theme` after v3 unification. `atipd_theme` still appears in PD Hub and PD Flashcards but only inside the one-time salvage migration block that copies legacy values to the canonical key.

### G.3.2 "Pharm shares nur2460_fc_schedule with MN" → **VERIFIED**

`Pharm Flashcards FC_KEY = 'nur2460_fc_schedule'` confirmed in source. Pharm and MN share the same SM-2 review queue, but ID schemes prevent collisions (MN uses `fc-chN-{slug}`, Pharm uses `fc-chN-pN` for typed and `fc-chN-{slug}` for inline; the slugs are subject-specific words so no collision). Verified in §H.3.3 of v3.

### G.3.3 "PD has its own theme key (atipd_theme)" → **WAS TRUE / SUPERSEDED in v3**

Originally true. **In v3 the theme key was unified across all 13 files to `nur2460_theme`** (§3.4 v3 change). PD Hub and PD Flashcards now use the canonical key with a one-time salvage migration from `atipd_theme`. PD's OTHER `atipd_*` keys (book/templates/fc/filters/bookmarks) remain separate per §C.3.3 — only `_theme` was unified.

### G.3.4 "All 8 template types use the same grid pattern with type-specific class names" → **CORRECTED**

**Both MN and PD support 8 template types** (Medication, System Disorder, Therapeutic Procedure, Nursing Skill, Basic Concept, Concept Analysis, Diagnostic Procedure, Growth and Development). However, the **CSS grid classes actually used differ between subjects**:

- **MN Templates grid classes (7):** `bc-grid`, `ca-grid`, `dp-grid`, `med-grid`, `ns-grid`, `sd-grid`, `tp-grid`
- **PD Templates grid classes (4):** `bc-grid`, `med-grid`, `sd-grid`, `tp-grid`

So PD's Concept Analysis, Diagnostic Procedure, Nursing Skill, and Growth & Development templates **fall back to `bc-grid`** (the generic flexible grid) rather than using type-specific grids. The grid CSS itself is the same; the *application* is more uniform in PD. This may reflect a deliberate simplification when PD was built — single fallback class is easier to maintain.

### G.3.5 "Growth & Development uses .bc-grid (no .gd-grid exists)" → **VERIFIED**

Confirmed in PD Templates: 24 occurrences of `bc-grid`, 0 occurrences of `gd-grid`. G&D references exist (10 occurrences of "Growth and Development" label) but they all use `bc-grid` for layout. There is no separate `gd-grid` CSS class in PD.

### G.3.6 "PD has 167 worked templates, 188 starter cards" → **PARTIAL — templates correct, cards count grew**

- **Templates: 167 — VERIFIED** (counted `class="example-card"` occurrences in PD Templates).
- **Cards: WAS 188 in v2 — NOW 359** (PD Flashcards `STARTER_DECK` has 359 entries). Cards were added between v2 writing and v3 — the count grew significantly. The current v3 changelog reflects 359.

### G.3.7 "Pharm has 49 chapters, 13 units" → **VERIFIED**

Pharm Book: 49 chapters (counted `<section class="chapter" id="chN">`); 13 units (counted `data-toggle-section="unitN"` patterns — unit1 through unit13). Both numbers exact.

---

## G.4 INFERRED / GUESSED — not extracted, applied from general knowledge

These claims are based on web standards or general best practices, not extracted from the files. The files may do things differently.

**v3 status:** Not exhaustively scrubbed. A few items below are now easier to verify because v3 work touched related code, but most are still informed guesses. Treat as guidance, not gospel.

```
? "The body uses 15px font-size as default"
  → Inferred from common practice. Actual MN body font-size may be set on
    html instead of body, or use rem units.

? "Modal max-width: 980px"
  → Extracted but may vary in some edge cases (mobile vs desktop)

? "Hover transitions all use 0.15s ease"
  → A common value extracted, but individual rules use varied timing
    (0.12s, 0.15s, 0.2s, 0.25s appear elsewhere)

? "Container queries are not used"
  → Inferred from lack of @container in extraction. May be wrong.

? "All paths in href use URL-encoded spaces (%20)"
  → Pattern matches what I saw; haven't verified every link

? "Sidebar items have a specific 32px height"
  → Calculated from padding + line-height, not measured

? "The tooltip popover positioning algorithm"
  → My JS in PART 7.16 is a reasonable implementation but may differ
    from the actual MN showTip() in subtle ways

? "The exact Hub JS (pickup panel update, storage panel toggles)"
  → I wrote plausible implementations but Hub JS was less thoroughly extracted
    than Book JS. The actual hub code may be cleaner/different.

? "performance: file under 2MB is fine on mobile"
  → General guidance, not specific to your devices
```

---

## G.5 SPECIFIC CLAIMS THAT MAY BE WRONG

**v3 scrub status (2026-05-13):** All 8 items were verified against working MN/Pharm files. Verdicts inline below: **VERIFIED** = claim was correct as written, **CORRECTED** = claim is updated with the actual finding, **WRONG** = original claim is refuted entirely.

### G.5.1 The "studies()" function name in Templates → **WRONG**

**Original claim:** A `studies()` function moves cards from pool to accordions at init.

**Actual finding:** There is no `studies()` function. The actual function that wires accordion items to the modal is **`bindAccordionList(acc)`**. More importantly, **there is no pool-to-accordion movement at all** — items are already inside their accordions at page load. `bindAccordionList` attaches a click handler that calls `openExampleModal(targetId)` and marks the clicked item active. The "card pool" mental model was incorrect; cards live in their accordion `.example-list-item` containers from page load. Skipping this misunderstanding fixed a class of bugs in later subject ports.

### G.5.2 The "returnCardToAccordion()" function → **VERIFIED**

`returnCardToAccordion` does exist in MN Templates as a named function. The Templates function catalog entry is accurate.

### G.5.3 Hub stats: "Starter Cards" count → **CORRECTED**

**Original claim:** "MN has 122 starter cards" with ambiguity on what 122 represents.

**Actual finding:**
- **The Hub tile's "in deck" number is DYNAMIC** — it reads `nur2460_fc_schedule` from localStorage and shows how many cards the user has actually rated/added to their queue (0 for a fresh visit).
- **The STARTER_DECK array in MN Flashcards contains 122 cards** — these are all of MN's inline mid-reads (data-fc-id markers in Book that get injected into the deck).
- **MN Book also has a `MID_PROMPTS` dict with 54 typed prompts** (formats: PRIORITY, JUDGMENT, CONTENT, PRINCIPLE) injected after each `chN-tldr` anchor.
- **Total MN learning content: 176 prompts** (122 inline + 54 typed), averaging 6.5 per chapter across 27 chapters.
- The v2 guide section §H.3.3 was correct that Pharm has 260 cards = 98 typed + 162 inline; same architecture applies to MN as 54 typed + 122 inline.

### G.5.4 The pickup-panel dismiss state → **CORRECTED**

**Original claim:** Dismissing sets `nur2460_pickup_dismissed: '1'` in localStorage and panel stays hidden permanently.

**Actual finding:** **The key uses `sessionStorage`, not `localStorage`**. Source comment confirms: `// Honor dismissal for this session (sessionStorage so reappears on next visit)`. So the panel auto-reappears on next browser session — the dismissal is intentionally NOT permanent. This is actually better UX than a permanent dismiss.

### G.5.5 Theme persistence across tools → **VERIFIED (and expanded in v3)**

**Original claim:** `nur2460_theme` is shared across MN+Pharm; uncertain for Pharm.

**v3 status:** **Now shared across ALL 13 files** (index, MN ×4, PD ×4, Pharm ×4). Theme unification was a deliberate v3 change documented in §3.4. Salvage migrations remove legacy `elevated_theme`, `atipd_theme`, `nur2460_pharm_theme` keys on first visit.

### G.5.6 Print overlay scope handling → **CORRECTED**

**Original claim:** Print supports 'all', 'unit', and single-chapter scopes.

**Actual finding:** `openPrintOverlay(scope, title)` is the entry point. The scope parameter accepts:
- `'all'` — used by the `masterPrintBtn` to print all templates
- A specific template-id string (passed via `data-print-template` attribute on per-template print buttons)

**There is no 'unit' scope** in either MN Book or MN Templates. The Book's `buildPrintContent` and `openPrintOverlay` handle full-document printing, not unit-scoped. If unit printing is desired, it would need to be added.

The toggle inside the overlay does support **two render modes** — `'brief'` and `'deep'` (NOT scope-level; these are styling-density modes within whichever scope is active).

### G.5.7 Flashcards "Browse" tab → **VERIFIED**

The Browse tab exists exactly as described. Source confirms:
```html
<button class="tab" data-tab="browse" type="button">Browse <span class="tab-count">...</span></button>
```
With full filter UI (`browse-filters`), per-card listings (`browse-item`), and per-card-type styling (`browse-priority`, `browse-warning`, etc.). Filter options: chapter dropdown, type dropdown, and sort dropdown (`due-asc`, `due-desc`, `ch-asc`). The "Browse" tab is real and active in MN, PD, and Pharm Flashcards.

### G.5.8 The "tpl-mode-toggle" exact text → **CORRECTED**

**Original claim:** Class is `tpl-mode-toggle` with `Filled / <strong>Blank</strong>` (inactive option bolded).

**Actual finding:**
- **Class is `mode-toggle`** (no `tpl-` prefix). 163 occurrences in MN Templates (~152 instances × extra references).
- **Default active button is "Filled"** (not Blank); `<button data-mode="filled" class="active" type="button">Filled</button>` followed by `<button data-mode="blank" type="button">Blank</button>`.
- **Visual emphasis is via CSS** (`.mode-toggle button.active{background:var(--accent);color:#fff}`), NOT via `<strong>` markup.
- Both labels are plain text inside `<button>` elements. Same pattern across all 152 example-card mode toggles in MN Templates.

---

## G.6 THINGS THAT WOULD INCREASE CONFIDENCE

If I were rebuilding this guide for v3, here's what would help:

1. **Run B.6.3 QA script on actual files** to validate v2's claims about chapter structure
2. **Extract every CSS rule** by file, not just sample rules
3. **Run `node --check` on the actual JS** from each file and document any parse oddities
4. **Open each file in browser and inspect with DevTools** to verify computed styles match documented values
5. **Test cross-tool sync end-to-end** on a real device with mobile dimensions
6. **Diff PD and MN structure** at the regex level to find actual deviations vs assumed deviations
7. **Build a smoke test suite** (Playwright or similar) that opens each file and checks for console errors, broken links, missing elements

Currently none of these were done for v2. The guide is built on regex extraction of MN files, supplemented by my reading of structures during the original suite build. That's enough to build a new subject suite that matches MN, but it's not enough to guarantee 100% accuracy.

---

## G.7 HOW TO USE THIS LOG

When rebuilding a subject from this guide:

- **For G.1 claims:** trust them. They're verified.
- **For G.2 claims:** trust them but verify if you're doing something exotic.
- **For G.3 claims:** verify before relying. Open the relevant existing file (e.g., open PD Templates if doing G&D work) and grep for the pattern.
- **For G.4 claims:** treat as "default behavior, may differ in your case." Test each before committing.
- **For G.5 specific claims:** these are flagged as suspect. Verify before using.

When you find an error: flag it. I'll update the guide. The point of this addendum is to make trust calibrated, not blind.

---

## G.8 ERRORS FIXED FROM v1

For reference, here's what v1 of this guide got wrong that v2 corrected (also detailed in `Build_Guide_v1_AUDIT.md`):

```
v1 ERROR                              v2 FIX
─────────────────────────────────     ────────────────────────────────
Theme uses html.light class           [data-theme="light"] attribute
Light mode is cool gray               Warm cream (#faf7f2 base)
13 CSS variables                       29 CSS variables (added FHR + 4 prompt types)
Simple "nur2460_" prefix for all      Complex per-subject prefixes
Templates use JSON scripts            <section class="template-section"> wrappers
Script order: anywhere                Main IIFE → NCLEX → mid-prompts (specific order)
Index uses subject accents            Index has its own --accent: purple
No documentation of                   PART 7.10 documents 4 typed mid-prompts
  4-type ATI clinical framework
No abbreviation tooltips               PART 7.16 + 277-entry ABBR_DICT
No bookmarks system                    PART 7.14 fully documented
No NCLEX filter / answered tracking    PART 7.12 with SATA detection
No search system                       PART 7.15 with highlight injection
No print overlay                       PART 7.17 Brief vs Deep modes
No cross-tool sync                     PART 7.18 with all shared keys
No mobile sidebar mechanics            PART 4.2-4.3 transformX pattern
No templates filter system             PART 8.6 chips + search + state
No "Reset Unit Progress"               PART 7.20
No storage panel export/import          PART 6.8
No template-section wrappers           PART 8.2 with studies() pattern
No mid-prompt DOM HTML pattern         PART 7.10 with buildPromptCard
No Filled/Blank toggle mechanism       PART 8.5
.gd-grid documented as existing        Corrected: G&D uses .bc-grid
```

v2 has its own potential errors, listed in G.3-G.5 above. v3 should fix them by direct file inspection.

---

# ADDENDUM H → CONSOLIDATED

> **NOTE:** Addendum H (Mobile quirks, user flows, subject variations) has been consolidated:
> - H.1 (iOS Safari quirks) → **PART 4.X iOS Safari Quirks**
> - H.2 (User flow walkthroughs) → **PART 13.X User Flow Walkthroughs**
> - H.3 (Subject-specific structural variations) → **PART 15.X Subject-Specific Structural Variations**
> - H.4 (Index-page cross-subject view) → **PART 5.X Index-Page Cross-Subject View Notes**
> - H.5 (Testing on actual devices) → **PART 13.X Testing On Actual Devices**

---

# ADDENDUM I → CONSOLIDATED

> **NOTE:** The entire Addendum I (Porting-Leak Prevention) has been consolidated:
> - I.1 (Porting-leak categories) → **PART 13.8**
> - I.2 (Per-file leak inventory) → **PART 13.9**
> - I.3 (Porting checklist) → **PART 13.10**
> - I.4 (Static vs dynamic gotcha) → **PART 13.11**
> - I.5 (Sweep script) → **PART 13.12**
> - I.6 (Key naming convention) → **PART 10.5**
> - I.7 (Overarching lesson from PD port) → **PART 15.1**

---

# ADDENDUM J → CONSOLIDATED

> **NOTE:** All of Addendum J (The MN Model: Build Narrative) has been consolidated into the main body of the guide:
> - J.1 (4-file inventory + data flow) → **PART 1.1**
> - J.2.1 (Theme system) → **PART 3.4** (already canonical there)
> - J.2.2–J.2.5 (Sidebar, modal, tabs, progress) → **PART 7.2, 7.4, 7.6, 7.20**
> - J.2.6–J.2.12 (mid-reads, abbrs, exercises, search, print, bookmarks, pickup) → **PART 7.9–7.18**
> - J.2.13–J.2.15 (Templates filter, filled/blank, accordion) → **PART 8.5, 8.6, 8.9**
> - J.2.16–J.2.19 (SR reviewer, filter, keyboard, timer) → **PART 9.3–9.9**
> - J.2.20 (Hub pickup + storage) → **PART 6.4, 6.8**
> - J.2.21 (Modifier classes) → **PART 10.4**
> - J.3 (Build sequence 8 phases) → **PART 13.2**
> - J.4 (Per-subject variation table) → **PART 13.3**
> - J.5.1-7 (Book + Templates function catalog) → Already canonical in **PART 7.21, 8.11**
> - J.5.8 (Flashcards function catalog) → **PART 9.10**
> - J.5.9 (Hub function catalog) → **PART 6.9**
> - J.6 (Key design decisions) → **PART 2.1**

The lesson from this entire exercise: **a checklist beats judgment**. If you find yourself thinking "looks fine," consult the checklist instead. Many bugs that escaped two prior audits were caught the moment a checklist was run.

