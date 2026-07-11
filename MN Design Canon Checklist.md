# MN Design Canon Checklist

Status: Read-only design canon extracted from the four MN HTML files.
Scope: Design, structure, navigation, and learning-workflow patterns only. This is not ATI educational content and should not be used as permission to add content in DESIGN-CANON / HOLD-CONTENT mode.

## Core Canon

- [ ] Treat MN as a connected study system, not just a visual style reference.
  - Canon pattern: Hub -> Book -> Prompt -> Flashcard -> Review -> Source jump -> Template practice -> Progress memory.
  - AMS implication: future AMS work should preserve the learning loop, not only copy tabs or cards.

- [ ] Keep the hub as a dashboard, not a landing page.
  - Canon pattern: primary tools, subject stats, unit progress, template-type overview, pickup panel, review queue, and storage controls.
  - Hub stat strip canon: use exactly four high-level counters only: Chapters, Units, Worked Templates, and Starter Cards. Do not include Template Types in the top stat strip because template-type detail belongs in its dedicated lower section.
  - AMS implication: hub changes should prioritize continuation, progress visibility, and tool relationships.

- [ ] Keep book chapters as modal study workspaces.
  - Canon pattern: fixed/sidebar navigation opens chapter modals with a header, chapter metadata, section tabs, scrollable modal body, and cross-tool controls.
  - AMS implication: chapter modal work should support reading, jumping, reviewing, and source-linked practice from the same workspace.

- [ ] Preserve the TL;DR-first chapter structure.
  - Canon pattern: each chapter starts with a one-glance summary before deeper content sections.
  - AMS implication: do not bury chapter orientation behind dense sections or practice content.

- [ ] Use tabs as navigational compression, not decoration.
  - Canon pattern: tabs are generated from chapter sections and include TL;DR, major content sections, Templates, and Practice.
  - AMS implication: tabs should reflect the learner's workflow and content hierarchy, not arbitrary labels.

- [ ] Preserve the condition-block / finding-card hierarchy for dense content.
  - Canon pattern: major concepts use `condition-block`; subordinate comparisons/details use `finding-card`; compact explanatory add-ons use `kb-card`.
  - AMS implication: small boxes should be grouped into meaningful clusters, not scattered as equal-weight fragments.

- [ ] Treat templates as visual learning geometry.
  - Canon pattern: template pages use gray group containers, inner header-strip boxes, filled/blank modes, connector lines, and modalized worked examples.
  - AMS implication: ALS/template redesign should preserve relationship mapping, not flatten everything into generic cards.

- [ ] Preserve cross-links between Book and Templates.
  - Canon pattern: every MN chapter has a template bridge, and template examples link back to source book anchors.
  - AMS implication: Related ATI Template links should be part of chapter workflow, with consistent source-jump behavior.

- [ ] Preserve cross-links between Book and Flashcards.
  - Canon pattern: book prompts can become review cards; flashcards link back to exact book anchors.
  - AMS implication: practice/review should be connected to source locations whenever possible.

- [ ] Treat flashcards as a first-class companion tool.
  - Canon pattern: review/browse tabs, due counts, filters, session metrics, keyboard shortcuts, source links, and SM-2 scheduling.
  - AMS implication: even if full flashcard work is deferred, design decisions should not block later review-loop integration.

- [ ] Keep local progress state consistent across the suite.
  - Canon pattern: shared theme, book progress, template progress, flashcard schedule, pickup state, last chapter, last template, bookmarks, NCLEX done state, and highlights.
  - AMS implication: any shared-control or label change should use consistent wording across all books.

- [ ] Preserve learner memory tools.
  - Canon pattern: bookmarks, pill-level bookmarks, highlights, notes, print modes, search highlighting, and pickup links.
  - AMS implication: navigation improvements should account for returning to precise concepts, not only chapters.

## Shell-First Build Canon

- [ ] Treat the current project goal as shell construction before content population.
  - Canon intent: build durable frames that can safely receive educational content later.
  - HOLD-CONTENT implication: do not add or enrich ATI educational content while building shells.

- [ ] Define each book as four coordinated shells.
  - Hub shell: topbar, hero, four stat cards, pickup panel, review queue status, primary tools, unit map, template-type navigation, storage controls, and subject accent identity.
  - Book shell: chapter navigation, modal study workspace, TL;DR-first flow, tabs, next/previous chapter movement, template bridges, practice area, bookmarks/highlights/notes, print, and progress memory.
  - Templates shell: MN-approved navigation sidebar, search, progress strip, template-type accordions, official A1-A15 geometry, filled/blank mode, print, previous/next within type, source jumps, and book-specific accent.
  - Template source-line canon: keep source/chapter text visually separate from the `Open chapter` link; the link should sit on its own line, and internal labels such as `ALS in book` should not appear in the learner-facing source line.
  - Template typography canon: opened-template titles should use the larger AMS-scale title treatment, with AMS-style header padding/divider rhythm; keep main template box body text at MN's normal readable body scale, and reserve compact text for nested/sub-boxes and dense grouped areas.
  - Template mobile canon: follow MN's per-template responsive behavior instead of one broad collapse rule. A1 Basic Concept and A11 System Disorder may collapse at tablet width; A3/A9/A13 procedure grids and A7 Medication collapse at phone width; A5 Growth and Development keeps two child columns until true mobile, then drops connectors and becomes one column; when the A5 Health Promotion connector strip is hidden on mobile, preserve a normal gap between the parent Health Promotion box and the child boxes such as Immunizations. A15 Concept Analysis uses its own narrow one-column breakpoint. On mobile, remove AMS-only fixed desktop min-heights so template boxes can size naturally. A5 should inherit MN's `gd-grid` spacing, radius, body sizing, and outer `tpl-group` section card around inner growth/development boxes rather than adding AMS-only fixed-height or transparent-wrapper overrides. For opened template modals, procedure grids must also respond to the template card width, not only the browser viewport, so side-by-side or narrow modal panes cannot keep a cramped two-column ATI desktop grid; use the measured narrow-card class as the durable fallback when viewport-only or container-query rules are not enough. For AMS rollout specifically, A3/A9/A13 opened procedure templates should stack at tablet/split-screen widths as a safeguard against squeezed two-column boxes and letter-by-letter wrapping.
  - System Disorder template canon: A11 uses MN's official top-row, assessment, safety, and patient-care skeleton. The preserved labels are top row: `Alterations in Health (Diagnosis)`, `Pathophysiology Related to Client Problem`, `Health Promotion and Disease Prevention`; Assessment: `Risk Factors`, `Expected Findings`, `Laboratory Tests`, `Diagnostic Procedures`; Safety: `Safety Considerations` plus `Complications`; Patient-Centered Care: `Nursing Care`, `Medications`, `Client Education`, `Therapeutic Procedures`, `Interprofessional Care`. Use strict title-first routing so top-row boxes cannot consume Assessment or Patient-Centered Care source sections. Empty official A11 boxes and groups remain visible in filled mode as structural placeholders; do not add `sd-no-assessment` or hide `tpl-group-visible-0` groups for A11. At narrow/tablet template-card widths, stack the major A11 regions and the top-row boxes. Keep Assessment as MN's 2-by-2 inner grid even at narrow/phone widths. Patient-Centered Care may preserve the original ATI five-box geometry on wide screens, but at narrow/tablet/mobile template-card widths both MN and AMS should use the stacked five-box layout for readability. Filled-mode desktop grid rules must not override this staged narrow-card/mobile behavior.
  - Medication template canon: A7 Medication should preserve MN's official visual skeleton in filled mode: the Purpose of Medication group keeps both inner boxes, and the medication body keeps the left/right official box columns instead of collapsing to only the sections that currently have source text. At narrow template-card widths, stack those columns cleanly while preserving the Nursing Interventions to Client Education connector line instead of hiding empty official boxes.
  - Nursing Skill template canon: A9 should preserve MN's official six-box skeleton in filled mode: `Description of Skill`, `Indications`, `Outcomes/Evaluation`, `Considerations` with visible `Nursing Interventions (pre, intra, post)` and `Client Education` inner boxes, `Potential Complications`, and lower `Nursing Interventions`. For AMS source sections, route `Steps`/technique text into the pre/intra/post subbox and safety-care text into lower `Nursing Interventions`; reserve `Potential Complications` for actual complication/risk/adverse sections. Do not apply `tp-grid-lean`, `tp-grid-no-description`, or `tp-grid-no-interventions` to A9 when empty official boxes are being preserved, because those classes remove grid slots and cause visible empty boxes to auto-place out of order.
  - Procedure-family mobile box canon: when A3/A9/A13 are narrow, the Considerations area should become a plain MN-style vertical stack. Remove desktop subgrid, fixed heights, and nested min-heights for direct subboxes, diagnostic `considerations-top`, and client-education boxes.
  - Template box-spacing canon: opened-template major/sibling boxes use a 14px gap, nested grouped boxes use a 10px gap, and Growth/Development keeps its MN-specific 20px section gap with 12px child-box/mobile connector spacing. Do not leave per-template one-off gap overrides unless the template has a real connector or official geometry reason.
  - Template landing rhythm canon: use MN's main-page hero text metrics and a fixed five-line hero description rhythm so the print button, `Templates` divider, search panel, and first accordion land consistently across books. Match MN's rendered divider-to-search and search-to-first-accordion spacing; when every lower landmark shares the same measured offset, fix the single upstream hero-height source instead of tuning each lower box separately. If a print button needs tiny visual adjustment after the section landmarks align, use non-layout paint adjustment such as `transform`, not font or margin changes that can move the downstream divider/search/card stack. When another book's DOM/CSS structure differs, use measured rendered offsets rather than copying similar-looking CSS values. Do not add extra wrappers around the lower `Templates` stack if they change MN's natural margin-collapsing rhythm. For rollout books, generate the main template groups as MN-style `unit-accordion` / `unit-header` / `unit-body` blocks rather than hybrid book-specific wrapper classes; keep the Growth and Development main accordion row visually consistent with the other template rows, including the progress bar.
  - Template utility text canon: low-priority controls such as `Reset All Progress` should match MN's quiet text-button treatment: transparent background, inherited font family, 11px size, and normal weight. Do not let shared action-button classes make utility text look bold or boxed.
  - Template visual-token canon: repeated template controls and metadata should inherit MN's quiet treatment: DM Sans UI text, normal/medium weights for low-priority buttons and source links, 10px metadata labels with 0.14em tracking and 700 weight, 14px metadata values, border-soft metadata cards, and no extra bolding unless a template heading or learner-facing emphasis needs it. Preserve each book's accent color and template-specific geometry/navigation.
  - Flashcards shell: paused until Hub, Book, and Templates are uniform; later shell should preserve due queue, review/browse views, filters, session metrics, source links, and scheduling.

- [ ] Use completion gates before calling a shell done.
  - Static structure pass: required elements exist and redundant elements are removed.
  - Rendered visual QA: spacing, sizing, font hierarchy, blur, modal width, and responsive behavior are checked in browser.
  - Navigation/count QA: links, anchors, progress counts, and local-storage keys are verified.
  - Canon documentation: accepted patterns and unresolved questions are recorded before rollout.

- [ ] Current surface priority.
  - Templates: pinned as approved design canon unless a concrete defect appears.
  - Hubs: current-complete for this shell pass; reopen only for a concrete defect or approved rollout need.
  - Books: current-complete for the chapter-modal navigation shell pass; reopen only for a concrete visual/navigation defect.
  - Flashcards: paused; do not resume until the user explicitly reopens flashcard shell work.
  - Next best step: final five-book shell matrix, then commit/push the current design-shell batch when approved.

## Prompt Canon Caution

- [ ] Do not blindly copy all MN prompt styles.
  - Evidence: MN Book contains an older `.mid-read` prompt system and a newer typed prompt direction (`content`, `judgment`, `principle`, `priority` style variables/classes).
  - AMS implication: decide the canonical prompt/practice design before rollout; do not mix generations accidentally.

- [ ] Treat practice design as current-user-directed, not inherited by default.
  - Canon pattern: MN's exercise system is valuable, but AMS Batch 2 comments specify a newer Application Exercises design.
  - AMS implication: practice tab redesign should follow the latest Batch 2 page/item direction, while retaining MN's source-linked and progress-aware workflow logic.

## Quantitative Evidence From MN

- MN Hub: dashboard with primary tools, stats, pickup panel, review queue, unit progress, template-type overview, and storage tools.
- MN Book: 27 chapters, 27 TL;DR cards, 273 content sections, 610 condition blocks, 548 finding cards, 177 knowledge cards, 92 ATI deep-dive blocks, 976 mid-read prompts, 827 exercises, 119 ALS cards, and 27 template bridges.
- MN Templates: 197 worked examples and 637 template group containers, with filled/blank modes, modal examples, filters, progress, print, and source links.
- MN Flashcards: starter deck workflow, review/browse tabs, filter system, session timer, keyboard shortcuts, source links, and SM-2 scheduling.

## AMS Prototype Review Checklist

- [ ] Does the AMS hub feel like a study dashboard rather than a landing page?
- [ ] Does the AMS book modal support a complete study session rather than only reading?
- [ ] Are small boxes grouped by concept hierarchy instead of arranged as loose fragments?
- [ ] Are tabs meaningful and stable across chapters?
- [ ] Are template links visible, useful, and connected to book anchors?
- [ ] Does the ALS design preserve relationship mapping and learner workflow?
- [ ] Does the Practice/Application Exercises design match the latest Batch 2 requested design?
- [ ] Are common button labels consistent across books?
- [ ] Does progress state remain understandable across hub, book, templates, and flashcards?
- [ ] Are deferred rollout items clearly separated from safe AMS prototype work?

## Guardrails

- [ ] Do not touch MN during the AMS prototype phase unless explicitly approved.
- [ ] Do not roll the AMS prototype to all books until reviewed.
- [ ] Do not add ATI educational content in DESIGN-CANON / HOLD-CONTENT mode.
- [ ] Do not treat AMS as the sole canon; use AMS for modern UI polish and MN for instructional structure and workflow depth.
- [ ] Before future implementation, compare proposed AMS changes against this checklist and mark each item Done, Partial, or Not done based on actual file evidence.
