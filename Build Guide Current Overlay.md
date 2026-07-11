# Elevated ATI Build Guide Current Overlay

Status: current 2026-07 design-canon overlay for the archived Build Guide.
Mode: DESIGN-CANON / HOLD-CONTENT.
Scope: documentation, design shell, visual QA, style consistency, navigation/count QA, and template rollout planning only.

This file does not approve ATI educational content population. It exists so future work can continue from the current design decisions without relying on one long chat history.

## Current Reading Rule

1. Use the archived Build Guide branch `codex-build-guide-archive-20260707` as the deep historical spec.
2. Layer `MN Design Canon Checklist.md` on top as the current design-shell canon.
3. Layer the latest user instruction on top of both documents.
4. If the archived Build Guide recommends content expansion while mode is `DESIGN-CANON / HOLD-CONTENT`, pause and report that content population is not active.

## Current Objective

Build the durable shell/foundation before further content work. The accepted design canon is dual-reference:

- AMS guides modern UI polish, modal behavior, navigation behavior, compactness, responsive control placement, and general visual refinement.
- MN guides instructional structure, template geometry, information hierarchy, mobile behavior, box relationships, connector lines, and how dense template material stays readable.
- When AMS and MN differ, choose the pattern that improves learner usability, clarity, scanability, and long-term consistency across books.

## Accepted Template Canon Snapshot

- Main template landing pages should use MN's spacing rhythm, typography scale, search panel treatment, progress rows, footer/reset treatment, and measured landmark alignment.
- Opened template modals should keep the larger AMS-style title treatment while using MN's readable body text, calmer controls, source-line structure, box spacing, and mobile stacking behavior.
- `Open chapter` links belong on their own line below the source chapter/title line.
- Internal source labels such as `ALS in book` should not appear in learner-facing source lines.
- A5 Growth and Development should preserve MN's outer section card, inner boxes, connector behavior, and progress bar.
- A7 Medication should preserve the official MN/ATI medication skeleton, including Purpose of Medication, official left/right body columns, and the Nursing Interventions to Client Education connector.
- A9 Nursing Skill should preserve the official six-box skeleton and keep source sections routed into the correct boxes instead of removing empty official slots.
- A11 System Disorder should preserve the official skeleton. Assessment remains a 2-by-2 inner grid, and Patient-Centered Care uses the stacked five-box layout at narrow/tablet/mobile widths for readability.
- A13 Therapeutic Procedure follows the shared procedure-family narrow/mobile rules with plain MN-style vertical stacking for Considerations.
- A15 Concept Analysis is simple; keep its tokens, spacing, and responsive behavior consistent with the accepted template system.
- Low-priority controls such as `Reset All Progress` should use MN's quiet text-button treatment: transparent background, inherited font, 11px size, and normal weight.

## Rollout Rules

- Do not roll out to all books in one run.
- Work one book template file at a time.
- Within each book, work one template family or one visual defect at a time when risk is nontrivial.
- Preserve each book's accent color, subject identity, template counts, and existing educational content.
- Do not add templates, flashcards, prompts, cards, sections, enrichment, or ATI educational content while content population is paused.
- Use recovered screenshots only as QA/reference context, not public content.
- Validate with static checks, script parsing, and visual comparison before committing.
- Commit and push a checkpoint before moving to the next book or a larger rollout step.

## Current Rollout Status

AMS Templates is the active prototype for this design-canon pass. The latest accepted AMS/MN work established:

- main template landing-page alignment;
- source-line and modal header rhythm;
- quiet text/control token matching;
- A5 Growth and Development mobile/card behavior;
- A7 Medication structure and connector behavior;
- A9 Nursing Skill official-box preservation;
- A11 System Disorder Assessment and stacked Patient-Centered Care behavior;
- A13 procedure-family narrow/mobile behavior;
- A15 visual-token consistency.

MN has been changed only when explicitly approved during this prototype work, such as adding Previous/Next navigation to MN template modals and applying the stacked five-box Patient-Centered Care narrow layout.

## Next Recommended Action

After this documentation checkpoint is committed and pushed, choose the next book/template rollout target and apply only one focused design-shell pass. Do not start a multi-book rollout in the same run.
