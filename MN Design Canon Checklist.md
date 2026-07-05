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
