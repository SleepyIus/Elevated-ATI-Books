# MN Design Canon Checklist

Status: Supporting implementation checklist synchronized to private master Build Guide Parts 49-225, the completed v4 AI execution specification, the completed Pediatric section-first design-polish phase, and the active MN/MH/AMS retrospective canon-delta audit.
Scope: Design, structure, navigation, and learning-workflow patterns only. This is not ATI educational content and should not be used as permission to add content in DESIGN-CANON / HOLD-CONTENT mode.

Current authority: private master Build Guide Part 49 contains the complete canon and the newest later continuation contains the active focused state. Use `Build Guide Current Overlay.md` for the repository-safe active-state mirror and this file for checklist-based implementation QA. If an older checklist or archived guide conflicts, follow the latest user instruction and the newest authoritative private-master section.

Recovery rule: the private `Elevated_ATI_Build_Guide_v3.md` Part 49 is self-contained for migration, `Build Guide Current Overlay.md` is its repository-safe current-state mirror, and this checklist is supporting evidence. No active task, pending visual approval, accepted rule, or next action may live only in chat history.

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
  - Template typography canon: opened-template titles should use the larger AMS-scale title treatment, with AMS-style header padding/divider rhythm. Uniformity is role-based rather than one-style-for-everything: the same semantic role must match across MN, MH, and AMS, while primary titles, nested titles, A5 child titles, and compact A7 Purpose titles retain their intentional distinctions. Use MN A7 Medication's `Complications` box as the readable body-text canon for A1 Basic Concept, A3 Diagnostic Procedure, A5 Growth and Development, A7 Medication, and A9 Nursing Skill: actual text in both main and nested boxes uses 16px DM Sans with 1.6 line-height and normal weight. Direct primary strips use DM Serif Display `15px / 24px`, A3 nested strips use `13.5px / 21.6px`, A5 child strips use `14px / 22.4px`, and A7 Purpose strips use `15px / 17.25px`. Keep role-specific heading treatments intact. Validate computed styles on rendered `p`, `li`, list, and table descendants, not only their parent `.content`, because child rules can silently restore smaller text.
  - A7 Medication metadata-label canon: all four existing labels must compute as DM Sans `10px`, `700` weight, `16px` line height, and `1.4px` letter spacing. Treat the labels as existing structural text: do not add, remove, rename, or reorder a metadata row to resolve a visual mismatch.
  - Template mobile canon: follow MN's per-template responsive behavior instead of one broad collapse rule. A1 Basic Concept and A11 System Disorder may collapse at tablet width; A3/A9/A13 procedure grids and A7 Medication collapse at phone width; A5 Growth and Development keeps two child columns until true mobile, then drops connectors and becomes one column; when the A5 Health Promotion connector strip is hidden on mobile, preserve a normal gap between the parent Health Promotion box and the child boxes such as Immunizations. A15 Concept Analysis uses its own approximately 720px one-column breakpoint, official two-row metadata (`Student Name` and `Concept Analysis`), 14px box gap/corners, 16px/1.6 body typography, and natural content heights. On mobile, remove AMS-only fixed desktop min-heights so template boxes can size naturally. A5 should inherit MN's `gd-grid` spacing, radius, body sizing, and outer `tpl-group` section card around inner growth/development boxes rather than adding AMS-only fixed-height or transparent-wrapper overrides. For opened template modals, procedure grids must also respond to the template card width, not only the browser viewport, so side-by-side or narrow modal panes cannot keep a cramped two-column ATI desktop grid; use the measured narrow-card class as the durable fallback when viewport-only or container-query rules are not enough. For AMS rollout specifically, A3/A9/A13 opened procedure templates should stack at tablet/split-screen widths as a safeguard against squeezed two-column boxes and letter-by-letter wrapping.
  - Growth and Development box-sizing canon: A5 sibling boxes remain equal within each wide grid row through normal grid stretching, but row height must be driven by the tallest box's actual content. Do not use fixed `260px`/`300px` minimum heights that create large empty regions in sparse books or remain active after the grid stacks at split-pane/mobile widths. Stacked A5 boxes should use their natural content height. Keep the Expected Growth and Development divider and its child boxes inside MN's bordered, padded `surface2` outer group; only the Health Promotion tree uses the intentionally transparent outer wrapper needed for its parent-to-child connectors.
  - A5 Health Promotion parent-content inset canon: its parent content uses `14px 16px` padding so the first rendered line begins `14px` below the header divider; retain its existing parent frame, connector tree, and child-box geometry.
  - System Disorder template canon: A11 uses MN's official top-row, assessment, safety, and patient-care skeleton. The preserved labels are top row: `Alterations in Health (Diagnosis)`, `Pathophysiology Related to Client Problem`, `Health Promotion and Disease Prevention`; Assessment: `Risk Factors`, `Expected Findings`, `Laboratory Tests`, `Diagnostic Procedures`; Safety: `Safety Considerations` plus `Complications`; Patient-Centered Care: `Nursing Care`, `Medications`, `Client Education`, `Therapeutic Procedures`, `Interprofessional Care`. Use strict title-first routing so top-row boxes cannot consume Assessment or Patient-Centered Care source sections. Empty official A11 boxes and groups remain visible in filled mode as structural placeholders; do not add `sd-no-assessment` or hide `tpl-group-visible-0` groups for A11. On wide screens, keep Safety Considerations and Complications as one grouped right rail with two equal, content-aware rows: each row must grow to the larger content requirement instead of using shrinkable fractional rows, `min-height:0`, or forced `height:100%` constraints that can clip text. At narrow/tablet template-card widths, explicitly override A11's higher-specificity desktop tracks so both the outer grid and filled top row use one column; never combine a one-column area map with two-column tracks. Return the Safety rail to natural vertical stacking, stack the other major A11 regions, and keep Assessment as MN's 2-by-2 inner grid even at narrow/phone widths. In that stacked safety state, the Safety group MUST retain `14px 14px 16px` outer padding; its group label and Safety area MUST begin `15px` from the group edge, and its first list-item text MUST begin `19px` from the group edge. Patient-Centered Care may preserve the original ATI five-box geometry on wide screens, but at narrow/tablet/mobile template-card widths both MN and AMS should use the stacked five-box layout for readability. Filled-mode desktop grid rules must not override this staged narrow-card/mobile behavior.
  - Medication template canon: A7 Medication should preserve MN's official visual skeleton in filled mode: the metadata order is `Student Name`, the existing `Medication` or `Medication / Device` label, `Category Class`, then `Review Module Chapter`; retain an empty dashed Category Class writing line when no current source-supported value exists. The metadata card keeps MN's `18px` lower margin before the Purpose group. The Purpose of Medication group keeps both inner boxes with a `10px` outer inset and `10px` inner gap; at a shared outer width, this produces the user-selected wider equal columns used by Pediatric. The regular medication body keeps the Pediatric-selected left/right official box columns: left `Complications`, `Contraindications/Precautions`, `Interactions`, and `Evaluation of Medication Effectiveness`; right `Medication Administration`, `Nursing Interventions`, and `Client Education`. Do not leave Evaluation as a trailing direct full-width box after the two-column body. Keep special `Medication / Device` layouts structurally distinct unless the user authorizes a specific form change. Its shared MN corner hierarchy is `16px` for the outer Purpose group, `11px` for its inner official boxes, and `14px` for direct medication-body boxes with `13px` direct-header caps; inner Purpose header strips remain square and are clipped by their `11px` frames. Direct A7 medication-body title strips use the MN-rendered `47px` stack: `11px 16px` padding and `24px` line height; do not let a generic compact `10px` header override shorten them. The outer `.med-grid` remains one column at desktop and tablet so Purpose stays above the medication body; only the body changes from two columns above `680px` to one stacked column at `680px` and below. At narrow template-card widths, stack those columns cleanly while preserving the Nursing Interventions to Client Education connector line instead of hiding empty official boxes.
  - A7 Purpose-header canon: within regular Medication Purpose groups, `Expected Pharmacological Action` and `Therapeutic Use` use Pediatric-selected `15px` DM Serif Display type, `10px 16px` padding, `17.25px` line height, and a `38.25px` rendered strip height inside their existing `11px` clipped frames. This is distinct from A7 direct-body headers, which retain their `47px` shared stack. The special Medication / Device form is unchanged unless separately authorized.
  - A7 Purpose-label canon: `Purpose of Medication` uses the metadata-label typography role across MN, MH, and AMS: DM Sans `10px / 16px`, weight `700`, `1.4px` letter spacing, uppercase. It must not inherit the generic group-label weight `900`.
  - A7 typography approval gate: the user visually approved the Part 219 three-book typography comparison on 2026-08-16. Across MN, MH, and AMS, same-role A7 text is accepted as uniform while the compact Purpose title remains intentionally distinct from direct medication-body titles. This approval does not begin A9 or authorize content population, staging, commit, or push.
  - A7 focused-review gate: user visual approval was recorded on 2026-08-10 for the current A7 Medication alignment in Parts 146-152. This approval is scoped to A7 and does not close the broader Section 6 review or authorize a new family.
  - Nursing Skill template canon: A9 should preserve MN's official six-box skeleton in filled mode: `Description of Skill`, `Indications`, `Outcomes/Evaluation`, `Considerations` with visible `Nursing Interventions (pre, intra, post)` and `Client Education` inner boxes, `Potential Complications`, and lower `Nursing Interventions`. The direct metadata card MUST leave an `18px` lower boundary before the A9 grid; retain the grid's `14px` direct-box gap and do not trade one for the other. Direct A9 title strips MUST use `15px` DM Serif Display, `24px` line height, `11px 16px` padding, and a one-line `47px` rendered height; explicit A9 line height is required so broader card rules cannot compact the band. Nested A9 title strips MUST use `13.5px` DM Serif Display, `21.6px` line height, `9px 14px` padding, and a one-line `40.59375px` rendered height. The two nested Considerations boxes use the same 16px DM Sans, 1.6 line-height body typography as the direct A9 boxes. A9 uses book-accent bullets, muted body text, and the book's solid primary text color for bold emphasis, including `Pre:`, `Intra:`, and `Post:`. Match MN's rounded A9 corner family exactly: 16px for the Considerations group, 14px for direct boxes with 13px header caps, and 11px for nested boxes with 10px header caps. Preserve the two-column procedure grid at MN's desktop and split-pane sizes, and collapse it to one column only at the 680px phone breakpoint. A9-specific grid-area rules must match the active column count so an implicit 2px column or oversized Considerations row cannot form. For AMS source sections, route `Steps`/technique text into the pre/intra/post subbox and safety-care text into lower `Nursing Interventions`; reserve `Potential Complications` for actual complication/risk/adverse sections. Do not apply `tp-grid-lean`, `tp-grid-no-description`, or `tp-grid-no-interventions` to A9 when empty official boxes are being preserved, because those classes remove grid slots and cause visible empty boxes to auto-place out of order.
  - A9 focused-review gate: user visual approval was recorded on 2026-08-11 for the current A9 Nursing Skill alignment. This approval is limited to A9 and does not close the broader Section 6 review or approve A11 System Disorder.
  - MH A9 retrospective evidence: all six current MH Nursing Skill cards now use the current MN role contract: `18px` metadata boundary, `14px` direct gap, `10px` nested gap, `47px` direct title stack, `40.59375px` nested title stack, DM Sans `16px / 25.6px` body/descendant text, and the `16px / 14px / 11px` group/direct/nested corner hierarchy. Above `680px`, Potential Complications uses a coordinated connector: a `34px x 3px`, `right:-24px`, `z-index:-1` bridge overlaps `10px` beneath each box, while a `14px x 3px`, `right:-14px`, `z-index:0` segment fills only the open gap so the relationship is visibly flush without drawing over either box. At `680px` and below both horizontal layers are hidden. All 60 Filled/Blank states pass; fresh user visual approval remains pending and does not authorize MH A11 or content work.
  - Procedure-family box-sizing canon: at wide and split-pane widths, A3/A9/A13 may preserve equal left/right rows, but each paired row must grow to the larger real content requirement. AMS A3 is the accepted content-imbalance exception: `Indications` and `Interpretation of Findings` form a natural-height role stack with an exact `14px` gap, while the wide spanning Considerations relationship and lower Potential Complications-to-Nursing Interventions row remain intact; do not move unused row space between those two short cards. Direct Considerations subboxes use natural minimum heights and must not shrink inside a constrained flex parent or clip overflow. When A3/A9/A13 are narrow, the Considerations area becomes a plain MN-style vertical stack and A3's stacked rows return to automatic sizing. Remove desktop subgrid, fixed heights, and nested min-heights for direct subboxes, diagnostic `considerations-top`, and client-education boxes. A9/A13 may hide their horizontal Potential Complications-to-Nursing Interventions connector when the procedure grid becomes one column; A3 is the official-relationship exception and rotates that bridge vertically using the behind-box overlap canon below.
  - Template box-spacing canon: opened-template major/sibling boxes use a `14px` gap, nested grouped boxes use a `10px` gap, and metadata-to-first-primary-content uses an `18px` boundary. Growth and Development is no longer a `20px/12px` exception: its same-level section, parent-to-child, child-to-child, responsive stacked, and visible connector-strip relationships use `14px` at every breakpoint. Do not leave per-template one-off gap overrides unless the template has a measured official geometry reason.
  - Modal top-stack canon: every opened MN/MH/AMS template uses a natural-height title-banner role before its Worked Example stack. `.modal-title-row` must not have a fixed height or minimum height: one-line titles collapse to their actual kicker/title/actions stack, while two-line and longer titles expand naturally. Titles must never be shrunk, clamped, hidden, or capped to mask wrapping. Preserve the responsive header padding (`28px 32px 22px` at regular widths and `16px 18px 0` at `600px` and below), the `14px` title-row margin, and the established first Worked Example inset (`28px` desktop, `46px` split-pane/tablet from `28px` body padding plus `18px` card inset, and `20px` phone). The chapter jump is its own source row in every book: `display:inline-block`, `margin-top:2px`, and medium `600` weight. Preserve the responsive source-to-navigation row gap (`10px` tablet, `14px` split/phone, including the navigation's `2px` margin), `16px` example-header bottom padding, `18px` divider-to-metadata spacing, and natural title/source wrapping.
  - Template landing rhythm canon: use MN's main-page hero text metrics and a fixed five-line hero description rhythm so the print button, `Templates` divider, search panel, and first accordion land consistently across books. Match MN's rendered divider-to-search and search-to-first-accordion spacing; when every lower landmark shares the same measured offset, fix the single upstream hero-height source instead of tuning each lower box separately. At desktop and split-pane widths, every collapsed template accordion renders at 92px outer height with a 90px header, 18px 22px header padding, 14px flex gap, and an 8px progress track. Keep the accordion header controls as direct flex children in MN order: caret, title, A-page badge, row print button, studied count, progress track. The A-page badge uses `surface2` over the transparent header/group surface so its box remains visibly distinct, and main accordion separation comes from the grid's single `14px` gap with no duplicate group margin. This preserves page-badge and print-control placement across pane widths. If a print button needs tiny visual adjustment after the section landmarks align, use non-layout paint adjustment such as `transform`, not font or margin changes that can move the downstream divider/search/card stack. When another book's DOM/CSS structure differs, use measured rendered offsets rather than copying similar-looking CSS values. Do not add extra wrappers around the lower `Templates` stack if they change MN's natural margin-collapsing rhythm. For rollout books, generate the main template groups as MN-style `unit-accordion` / `unit-header` / `unit-body` blocks rather than hybrid book-specific wrapper classes; keep the Growth and Development main accordion row visually consistent with the other template rows, including the progress bar.
  - Template utility text canon: low-priority controls such as `Reset All Progress` should match MN's quiet text-button treatment: transparent background, inherited font family, 11px size, and normal weight. Do not let shared action-button classes make utility text look bold or boxed.
  - Template visual-token canon: repeated template controls and metadata should inherit MN's quiet treatment: DM Sans UI text, normal/medium weights for low-priority buttons and source links, 10px metadata labels with 0.14em tracking and 700 weight, 14px metadata values, border-soft metadata cards, and no extra bolding unless a template heading or learner-facing emphasis needs it. Preserve each book's accent color and template-specific geometry/navigation.
  - Template Student Name writing-line canon: every worked template card keeps the Student Name value empty and renders it as an inline writing line in both Filled and Blank modes. Use a `120px` minimum width, `18px` height, and `1px dashed` current-border-color bottom edge; keep the line inside its metadata value cell at desktop, split-pane/tablet, and phone widths.
  - Flashcards shell: explicitly reopened for design-canon review on 2026-08-21, with MN as the rule-setting reference. Preserve the due queue, Review/Browse views, filters, session metrics, keyboard shortcuts, source links, and scheduling.
  - Flashcards sidebar canon: reuse the finalized same-subject Templates sidebar chrome without copying template-specific navigation content. Keep the fixed `280px` rail, shared header rhythm and theme control, bordered `10px 16px` search block, `8px 0 24px` scroll-list padding, explicit thin/`6px` scrollbar treatment, rounded inset navigation rows, and subject accent identity. Match the Templates rail typography exactly: DM Sans interface text, DM Serif Display sidebar title, unitless `1.6` rail line height, `10px`/`800` uppercase section labels with `0.12em` tracking, and `13px`/`600` primary navigation names; keep Back to Hub, course label, subtitle, theme control, and search text at their Templates metrics. At `900px` and below, use the Templates mobile rail contract: Back to Hub fixed left, `40px` menu control fixed right, `92px` main top inset, blurred overlay, search focus on open, synchronized icon/label/`aria-expanded`, hidden/inert closed drawer, overlay or Escape close, and focus restoration. Every drawer open resets its scroll list to `scrollTop=0`; never reopen a narrow sidebar at a stale mid-list position. Retain flashcard-specific Unit/Retrieval/Status filters, labels, counts, destinations, storage, and learner state.
  - Flashcards sidebar unit-label canon: beneath the retained `Unit` section heading, each learner-visible quick-filter row uses `[subject-specific unit title] (Ch X–Y)`. Omit a redundant `Unit N ·` prefix from the row while preserving the exact title and authorized chapter range. Keep internal unit IDs, `data-value` attributes, main filter chips, course/unit identity, filter migration, storage, schedules, history, and all learner state unchanged. Apply this display grammar retrospectively to completed Flashcards and prospectively when a future shell gains its unit sidebar.
  - Flashcards narrow vertical-rhythm canon: at every content viewport at or below `900px`, both fixed utility controls begin `14px` from the top; the menu control is exactly `40px` high and therefore ends at `54px`; and `.main-content` begins with a `92px` top inset so the hero starts at `92px`. This preserves a fixed `38px` clear interval from the menu bottom to the hero and must remain identical across phone, tablet, and split-pane comparison widths. Do not substitute content-dependent margins or a smaller subject-specific inset.
  - Flashcards narrow utility-control canon: at every content viewport at or below `900px`, Back to Hub is fixed at `top 14px / left 14px` and includes the left-arrow cue; use `11px/600` DM Sans text, `0.03em` tracking, `8px 14px` padding, a `1px` current-border-color edge, `8px` corners, and flex alignment with a `5px` arrow/text gap. The hamburger is fixed at `top 14px / right 14px`, exactly `40px x 40px`, with an `18px` icon, the same border/surface/`8px` corners, and centered flex alignment. Do not reverse these controls by subject or omit the Back to Hub arrow.
  - Flashcards taxonomy canon: each card has exactly one primary retrieval target—`Recall`, `Recognize`, `Act`, or `Apply`—separate from secondary attributes, source certainty, clinical priority, and learner mastery. Secondary attributes may overlap and use `Warning`, `Numeric`, `Sequence`, `Comparison`, `Mnemonic`, and `Calculation`; `Calculation` is reserved for cards that actually require computation. Keep secondary attributes in a collapsed advanced filter area so the primary workflow stays compact. A legacy `Warning` flag preserves the prior alert designation but must not be presented as newly source-certified safety or priority evidence. Render textual labels as well as distinct accessible colors in Review and Browse. Join taxonomy metadata to the stable card ID at read time so existing schedule/history records are preserved; migrate compatible legacy filter choices into a versioned filter-state key without rewriting the learner schedule.
  - Flashcards retrieval-decision canon: classify the **observable task in the existing question**, never the urgency or importance of its answer and never by a blind keyword rewrite. `Recall` is direct retrieval of a fact, definition, name, list, timing, or relationship without cue interpretation. `Recognize` identifies or classifies a finding, pattern, category, or explicit contrast from presented cues. `Act` selects an immediate or priority action, response, teaching, intervention, hold/report/stop behavior, or next nursing step in the stated condition. `Apply` uses a rule, formula, ordered method, comparison, or changing inputs to solve a case or computation. If two labels remain materially plausible after reviewing the whole card and same-subject source anchor, stop the affected card group for user direction; do not force a classification.
  - Flashcards secondary-attribute canon: attributes are independent of the primary retrieval target and use OR semantics when multiple values are selected. `Warning` preserves an existing legacy alert designation only; `Numeric` requires a clinically meaningful number, threshold, dose, timing, or value already present; `Sequence` requires genuinely ordered steps; `Comparison` requires an explicit contrast; `Mnemonic` requires a named learning aid or acronym; and `Calculation` requires the learner to compute rather than merely recall a number. Do not invent a warning, source-certainty, safety, or priority claim while tagging.
  - Flashcards record-and-state canon: every card preserves stable `id`, chapter/unit field, source `anchor`, question, answer, order, and recoverable legacy type. Review and Browse must render the same canonical records; reveal state is not mastery, and Hard/Good/Easy changes scheduling only. Existing schedule/history keys and records remain byte-compatible. New metadata may be hydrated by stable ID or migrated through an explicitly versioned schema; compatible old UI filters may migrate to a versioned filter key, but learner schedules may not be rewritten. CSV, source links, search, keyboard controls, dark/light themes, filters, badges, and review/browse handoff must all consume the same record model.
  - Flashcards exact-Book-jump canon: every learner-facing flashcard provides a clearly labeled Book action that opens the same-subject Book at the card's exact preserved source `anchor`, never merely at the Book root or at an inferred chapter. The current shared Review-card label is `📖 Open in book`; an established legacy `Open Book` control may remain until that subject's design-parity phase when it already resolves every card anchor. Preserve any existing `Open in chapter ↗` footer link; when both controls appear, both must resolve to the same card anchor. Full gates must verify every card-to-Book anchor before visual approval.
  - Flashcards visual-token canon: preserve each subject's accent and course identity while matching MN's shared dark surfaces and role-based typography. Use DM Sans for body/UI text and DM Serif Display for display headings/questions. Approved corner roles are hero `18px`, review card `16px`, stats/tabs `12px`, filter/reveal/rating/browse cards `10px`, primary/session/mobile utility controls `8px`, sidebar rows `7px`, retrieval labels `5px`, and fully rounded secondary pills. Hero titles use `32px/1.1`; review questions use DM Serif Display `19px/1.4`; retrieval labels use `10px/700/0.12em`; secondary pills use compact `9px/700` text. Desktop uses an `820px` maximum main column with `36px 32px 80px` padding beside the `280px` rail; at `900px` and below use the established `92px` top inset and at `600px` and below use `16px` horizontal main padding.
  - Flashcards review-metadata-row canon: keep retrieval, secondary-attribute, and chapter labels together in a wrapping left lane, and keep the due label in a nonshrinking upper-right lane. Crowded metadata may wrap naturally inside the label lane, but `due now`/future-due text must remain aligned with the first metadata line and may not be forced below the complete tag set. Preserve every label at its approved typography; do not solve crowding by shrinking, clamping, hiding, truncating, or adding horizontal scrolling.
  - Flashcards shared-feature retrospective-propagation canon: every new or changed shared Flashcards feature begins with an applicability matrix covering every current Flashcards HTML, including products whose earlier audit or user review is already complete. Mark each product `Implemented`, `Not applicable` with an exact structural reason, or `Deferred` with a blocking condition. A shared feature is not objectively complete until every applicable previously completed product is updated and passes fresh focused regression; `Not applicable` becomes a mandatory activation gate when that product later gains the missing surface. Record the matrix, product hashes, validation, and any new activation gate in the private master, overlay, handoff, and owning automation before advancing the queue.
  - Flashcards Focus Deck canon: Focus membership is a versioned, subject-local list of stable card IDs and remains separate from reveal state, mastery, and the normal scheduling record. Learners may add or remove a card from either Review or Browse, revisit the same canonical records in the Focus tab, and start a Focus review of all matching cards or only those due now. Hard/Good/Easy continues to change scheduling only and never removes Focus membership; deck reset preserves Focus, while Hub progress export/import and reset-all include it. Browse and Focus handoff must preserve the complete filtered queue. Skip and Shuffle remain disabled with an explanation for one-card queues. Shuffle is session-only: the first shuffle captures the current remaining order, repeated shuffle may reshuffle it, Restore order keeps the current card visible while restoring the remaining pre-shuffle order, and neither action may rewrite canonical card order, schedule/history, membership, or progress. Preserve the approved `C`, `S`, and `Shift+S` keyboard contracts. Any product that lacks the canonical Review/Browse surface receives a mandatory activation gate rather than a partial implementation.
  - Flashcards AFK automation canon: MN is a pattern reference, never a clinical-content donor. Process exactly one target subject and one bounded phase per heartbeat run in the order MH, PD, Pharm, then AMS; phases are preflight/inventory, design parity, retrieval-taxonomy migration, full QA, and a fresh two-pane MN-left/target-right user-review handoff. Preserve every target question, answer, source anchor, card ID, order, subject identity, and learner-state record. Routine objective phases may advance only after their complete gate passes; automated QA is never user visual approval. Stop for ambiguous classification, missing/unreadable same-subject source anchors, clinical-content needs, unsupported facts, subjective/new-canon decisions, learner-state risk, unexpected tracked changes, continuity conflict, or missing fresh evidence.
  - Night Shift automation canon: Night Shift is an explicitly activated temporary profile of the existing guarded heartbeat, never a competing automation. The current migration queue remains primary; shell work is secondary only after a safe no-work or user-review boundary and may never bypass a safety, continuity, learner-state, clinical-content, destructive-action, unexpected-change, missing-evidence, or subjective-canon stop. One run owns one product and at most two adjacent bounded phases. Construct and fully gate under a fresh `/private/tmp` path, then promote the exact passing result as an unlinked repository draft. The ordered shell dependency is Book → Hub → Templates → Flashcards; global-index linkage, publication, content population, commit, and push remain separately gated. New shells contain zero clinical records or inferred content and are born with every applicable approved shared feature. `I am back` safely checkpoints, reports, disables the shell-secondary profile, and restores the exact ordinary queue recovery point.
  - Flashcards full-gate canon: rebuild fresh isolated-storage payloads from exact product files under `/private/tmp`, use only `127.0.0.1`, normalize browser zoom to `100%`, and require two identical measurements at least `250ms` apart. Validate `2240 x 1000`, `1440 x 1000`, `768 x 1000`, `390 x 844`, and exact `901/900` plus `601/600` breakpoint pairs. Scan all records for required fields, exact count/order/payload parity, unique IDs, same-subject anchor resolution, script/runtime integrity, Review/Browse, reveal/rating, every primary/secondary filter and union, CSV, source links, keyboard controls, themes, drawer behavior, print, accessibility state, horizontal overflow, storage-key preservation, versioned filter migration, HTTP, focused diffs, and `git diff --check`. QA artifacts remain temporary; no stage, commit, push, publish, branch switch, learner-data deletion, or content population is authorized.
  - Placeholder/new-husk canon: existing subjects must be measured and preserved rather than replaced. A new subject requires explicit identity, edition, accent, four collision-free paths, isolated storage, `placeholderOnly=true`, and no donor payload. Construct one authorized surface per batch in Book, Hub, Templates, then Flashcards order; use only defined non-educational empty states, keep unavailable links disabled, and never infer content-population permission from a completed shell.
  - Empty-box/content-population canon: only a current explicit user instruction may activate one bounded content batch for one subject and one surface. Every learner-facing content unit in the focused diff requires an exact private same-subject provenance location and destination route; inference, model memory, web material, donor content, and broad topic similarity cannot close a source gap. Required official boxes remain visible and machine-flagged when source support is absent. Default caps are two Book chapters, three Template cards, or twelve Flashcards, with Hub synchronization handled separately; authorization expires at close, blocker, or cap and returns the project to HOLD-CONTENT.
  - Deterministic build-pipeline canon: each work order selects one lane and owns one subject, one surface, one primary file, and one bounded objective. New/recreated placeholder suites use validated manifest, Book, Templates, Flashcards, then Hub; existing repairs start directly with the named surface. Every batch follows authority/mode, work order, preflight, baseline, temporary preparation, focused implementation, static QA, rendered/behavior QA, focused diff, continuity, approval gate, and handoff. Objective QA never becomes user visual approval or permission for another surface, content batch, commit, or push.
  - Objective QA canon: define a complete requirement-backed matrix before editing; every required row must be `PASS` or justified `NOT_APPLICABLE`, with zero `FAIL` or `BLOCKED` rows. Use structured parsing, complete payload/ID/count/order/link checks, isolated storage, keyboard/accessibility checks, and rendered QA at `1440 x 1000`, `768 x 1000`, and `390 x 844` plus exact breakpoints. Clipping requires more than 1px objective overflow and two identical readings at least 250ms apart; screenshots are supplemental and remain under `/private/tmp`. An unchanged out-of-scope mismatch may remain documented in a focused pass, but full surface/suite conformance and user visual approval require their own explicit gates.
  - Recovery/operations canon: keep one durable work order with exact authority, mode/lane/scope, primary file/targets, editable/supporting/forbidden files, baseline, QA/approval gates, Git state, automation preservation, status, and one next action. Recover only from current files/configurations, resume from the first unpassed phase, classify blockers explicitly, keep v3 append-only and v4 requirement IDs stable, and never infer stage/commit/push/merge/switch/reset/revert/delete authority from edit permission. Final automation handoff is Batch 16-only and may change status fields only after exact configuration capture and verification.

- [ ] Use completion gates before calling a shell done.
  - Static structure pass: required elements exist and redundant elements are removed.
  - Rendered visual QA: spacing, sizing, font hierarchy, blur, modal width, and responsive behavior are checked in browser.
  - Navigation/count QA: links, anchors, progress counts, and local-storage keys are verified.
  - Canon documentation: accepted patterns and unresolved questions are recorded before rollout.

- [x] Pediatric visual parity uses the Part 115 section-first gate, not the superseded family-first completion claim.
  - [x] Section 0 MN reference contract passed without a product edit: 101 mapped roles, ten typography properties, 49 container/layout properties, 36 stable repeated state captures, 24 screenshots, three required viewports, zero browser warning/error events, and zero unexpected missing selectors.
  - [x] Section 1 landing upper half passed: the Back-to-Hub/menu pair, hero spacing, eyebrow, title, copy, print control, first divider, and narrow main gutter now follow MN's measured contract. The one-line Pediatric phone title versus MN's two-line title is the documented subject-wording wrap exception; all shared values and controls remain within the 1px gate.
  - [x] Section 2 search/discovery panel passed: the visible panel, label, input, placeholder, and focus treatment match MN at desktop, tablet, and phone. Pediatric retains its blue accent; its existing hidden result-count behavior remains unaltered and is not a rendered-role mismatch.
  - [x] Section 3 accordion list passed: all eight rows match MN's title/badge/print/progress typography and geometry; A-page badges retain visible `surface2` contrast, the only row separation is the `14px` grid gap, and every `8px` rail/control remains contained at desktop, tablet, and phone.
  - [x] Section 4 landing lower half passed: the existing Pediatric reset now uses MN's lower-landing control contract; the user-requested two-line Pediatric footer uses MN's divider, spacing, type, and footprint contract with Pediatric-specific metadata and Hub destination; its terminal padding is `91px` at desktop and `71px` below the established `900px` breakpoint; and both corresponding reference modes have matched scroll endpoints.
  - [x] Comparison harness contract: Wide desktop overlay uses one shared full available-width canvas capped at `1440px`, while Split-pane is reserved for responsive checks. An active overlay must use equal iframe widths and mirror MN scrolling immediately; it must not infer desktop parity from a half-width responsive pane.
  - [x] Section 5 Fixed/Responsive Sidebar passed. The vertical-stack, status-legend, scrollbar-treatment, responsive drawer, overlay, focus, inert-state, and keyboard-interaction subgates are complete. At desktop, `768px`, and `390px`, same-role header, theme control, progress strip, search panel/input, section label, all eight sidebar-group geometry, both `Reviewed`/`Checked` legend items, and the sidebar scrollbar match within `1px` where geometry applies. The user visually confirmed the focused scrollbar and drawer behavior. The shared contract uses `normal` line height for the theme control and search input, `500` legend weight, `8px 0 24px` sidebar-list padding, and an explicit `thin`/`6px` scrollbar with transparent track, `var(--border)` thumb, and `3px` thumb radius.
  - [x] Section 6 A1 Worked Example lower-control subgate passed. The modal header MUST keep metadata, check, Print, and mode toggle as direct first-row children, followed by a full-width navigation row; the modal check uses zero padding, Print is `30px` inline-flex with `6px 12px` padding, and mode controls use normal line-height. Preserve the Pediatric blue selected-state accent. Subsequent vertical placement MUST be content-driven by each book's existing subtitle/source wrapping, not padded to imitate another book's content.
  - [x] Section 6 A1 source-link subgate passed. The existing `Open chapter` link MUST use an unbroken `white-space:nowrap` label on its own line below the source text, with `width:max-content` and no inserted inline separator. Its label, href, chapter route, and source text MUST remain unchanged; at desktop, tablet, and phone it MUST remain wholly inside the source container without horizontal overflow.
  - [x] Section 6 shared primary title-strip subgate passed. Every direct primary template box header except A5 Expected Growth and Development group headings MUST use the MN `47px` band: `11px` top/bottom padding, `24px` line height, and the existing one-pixel divider. A5's eight direct group headings MUST use the distinct MN `14px / 22.4px / 45.3984375px` contract with the same `11px` vertical padding; its Health Promotion parent heading remains on the `47px` primary band. Nested headers and the intentionally compact A7 Medication Purpose headers MUST retain their separate accepted geometry; do not flatten them into the primary-box rule.
  - [x] Section 6 shared primary-spacing subgate passed. Across Pediatric A1, A3, A5, A7, A9, A11, A13, and A15, `dl.template-meta` MUST have an `18px` boundary before the first primary content group, and primary template-box grids MUST use a `14px` relationship gap. A7 Purpose retains its explicit `10px` inset / `10px` inner gap. The former A5 `20px/12px` wording is superseded as the current MN/MH/AMS canon by Part 215; the protected Pediatric product was not reopened in that cross-book batch and requires its own separately authorized audit before any product change.
  - [x] Section 6 A11 System Disorder focused review passed. The user visually approved the current A11 alignment in Part 172, including the existing top-row/Patient-Centered Care `16px` DM Sans at `1.6`, Assessment and Complications `13px` / `1.5`, Safety `13px` / `1.55`, and the responsive Safety inset contract. This scoped approval does not approve another family or the remaining Section 6 review.
  - [x] Section 6 A13 direct-copy typography subgate passed. Pediatric A13 direct `.tp-box > .content` and every rendered `p`, `li`, `ul`, `ol`, `table`, `th`, and `td` descendant MUST use MN's DM Sans `16px / 25.6px / 400` contract with normal letter spacing and `5px` list-item rhythm; `strong` remains `700`. Its primary title strips MUST retain the `47px` / `15px` / `24px` contract. A parent-container reading alone is not a pass because a child selector may override it. Automated QA is not user visual approval.
  - [x] Section 6 A13 complete box-role subgate passed. Every current A13 card MUST keep the direct role at the existing `15px / 24px` primary heading and `16px / 25.6px` body contract, while nested Considerations `.tp-subbox > .content` and all rendered descendants MUST use the distinct MN nested role: `13.5px / 21.6px` heading with `9px 14px` padding, DM Sans `13px / 19.5px / 400` body copy with `12px 14px 14px` padding, and an `11px` frame. The Considerations parent MUST use `14px` padding, a `10px` gap, and a `16px` frame. Audit all direct and nested containers plus their actual rendered descendants in every card and in Filled and Blank modes; a screenshot sample or parent-only computed-style check is insufficient. Automated QA is not user visual approval.
  - [x] Section 6 A13 focused user visual confirmation passed after the descendant-level and true-endpoint corrections in Parts 175-178; the user confirmed the corrected endpoint is fixed before the active review advanced to A15.
  - [x] Section 6 all-family true-endpoint subgate passed. Every Pediatric `.modal-body` MUST retain `40px` computed bottom padding and reach its true maximum scroll position in Filled and Blank modes at desktop, tablet, and phone. The complete 179-card matrix produced 1,074 stable states within `39.125-40.921875px`, with zero unaccepted overflow or endpoint failures. The established A13 Complications horizontal connector and A7 Medication Nursing Interventions vertical connector are exact-role relationship exceptions only; they MUST NOT be generalized to hide clipping.
  - [x] Section 6 A15 Concept Analysis focused user visual confirmation passed in Part 179. The user confirmed that the current A15 comparison appears in order, completing the focused visual-review sequence for all eight Pediatric families. This remains distinct from automated QA.
  - [x] Section 6 final cross-surface handoff passed in Part 180. Desktop `1440 x 1000`, tablet `768 x 1000`, and phone `390 x 844` retained `0px` horizontal overflow; the responsive drawer, search and keyboard clear, labelled modal and focus restoration, Filled/Blank tabs, same-family Blank-mode navigation, single-card print, A1 family print, and full-template print passed. The product retains one parsed inline script, 179 unique card IDs, canonical counts `12/9/5/13/9/116/9/6`, 179 chapter links resolving to 42 existing anchors, stable storage keys, byte-identical temporary payload parity, and the prior 1,074-state true-endpoint pass. Automated QA remains distinct from the user's focused visual approvals.
  - Audit in this order: landing upper half; search/discovery panel; eight collapsed accordion rows; lower landing/footer; fixed/responsive sidebar; common modal/card top; shared card frames/boxes; rendered card content typography; final responsive/interaction/print handoff.
  - Typography is mandatory in every relevant section. Compare computed font family, size, weight, line height, letter spacing, and color for the actual rendered descendants, including headings, labels, inputs, placeholders, counts, metadata, box headings, `p`, `li`, direct text, `strong`, and nested content.
  - Search is a visual and functional gate. Compare the divider, panel, icon, input, placeholder, focus state, background, border, radius, padding, dimensions, responsive width, and filtering behavior.
  - Compare shared control/container display, tracks, dimensions, margin, padding, gap, alignment, background, border, radius, focus, and hover. Same-role geometry must be within 1px unless wrapping or a documented subject-specific exception explains the difference.
  - No section passes from no-clipping evidence alone. Require separate style, geometry, responsive, interaction/accessibility, and visual-comparison passes at desktop, split-pane/tablet, phone, and exact breakpoints.
  - Correct shared primitives before family-specific exceptions, rebuild the byte-identical local comparison after each completed section, and keep automated QA distinct from user approval.

- [x] Current surface priority.
  - Templates: Pediatric's section-first visual parity, all eight focused family approvals, all-family endpoint regression, final cross-surface handoff, and pushed commit `acef952` are complete. Parts 181-204 open and advance the targeted MN/MH/AMS retrospective because the earlier approvals predate the full section-first and rendered-descendant method. Batch 0 inventory and Batches 1-4 landing-page, fixed/responsive sidebar, modal-top, and shared-box rendered QA are complete; focused Batches 5A MH A1, 5B AMS A1, corrected 5C MH A3, corrected 5D AMS A3, and corrected 5E MH A5 are objectively passed. AMS A1, MH A3, the current Part 197 AMS A3 repair, and corrected MH A5 have user visual approval. Part 204 requires visible spacing-consistency review across all remaining families and a final A1/A3 cross-book spacing regression. No Pharmacology rollout is active.
  - Retrospective queue: `[x]` landing page; `[x]` sidebar; `[x]` modal top; `[x]` shared box system; `[~]` A1/A3/A5 (`AMS A1`, `MH A3`, and corrected `AMS A3` user visually approved; `MH A1` and corrected `MH A5` objectively passed; MH A5 user review and AMS A5 audit remain pending); `[ ]` A7/A9; `[ ]` A11/A13/A15; `[ ]` responsive/print/payload/integrity.
  - Landing-page evidence: stable repeated desktop, tablet, and phone measurements now align MN/MH/AMS introduction typography, Reset Progress geometry, footer role geometry, accordion spacing/corners, responsive Back to Hub/menu controls, and horizontal containment. MH alone required a landing CSS correction; learner content, counts, IDs, links, storage, order, and accent remain unchanged. Automated QA is not user approval.
  - Sidebar evidence: stable repeated desktop measurements align fixed-panel geometry, theme/progress/search/list roles, all eight family controls, `500` legend weight, and scrollbar treatment across MN/MH/AMS. At tablet and phone widths, a closed drawer MUST set `aria-hidden=true` and `inert`, its menu control MUST set `aria-expanded=false`, opening MUST focus sidebar search, and overlay or Escape closure MUST restore focus to the menu control. Batch 2 passes those states with `0px` horizontal overflow in all six book/viewport combinations. Automated QA is not user approval.
  - Modal-top evidence: MN and MH retain the accepted desktop modal-top contract. AMS now matches the `127.99px` desktop header, `28/32/22px` header padding, `34/37.4px` title, `8px` action gap, top-aligned example row, `20px` checkbox, `30px` Print control, and `37.5px` mode toggle. Its full-screen breakpoint is `600px`, and the phone modal uses `20/18/40px` body padding. Stable desktop/tablet/phone measurements, Filled/Blank and Previous/Next interaction, Escape/focus behavior, reopening, and zero overflow pass. Automated QA is not user approval.
  - Shared box-system evidence: all 352 current MN/MH/AMS cards were measured in both modes at all three required widths, for 2,112 stable card-mode states. Standard shared direct titles remain DM Serif Display `15px / 24px` with `11px 16px` padding and a `47px` one-line height; standard direct descendants remain DM Sans `16px / 25.6px`; major and nested gaps remain `14px` and `10px`; and the accepted corner hierarchy remains intact where applicable. Exact A3/A9/A13 horizontal and A7 vertical relationship connectors are decoration exceptions only. Family-specific differences and MN A7 tablet header stretch remain pending in Batches 5-7. Automated QA is not user approval.
  - Batch 5A MH A1 evidence: every one of the 13 MH A1 cards passed Filled and Blank at `1440 x 1000`, `768 x 1000`, and `390 x 844`, for 78 stable states. The scoped A1 grid uses the accepted `14px` gap, `14px` box corners, `280px` desktop Filled minimum, `120px` Blank minimum, `11px 16px` title padding, natural-height narrow Filled boxes, and 3/2/1 responsive tracks. Direct title and body typography remain DM Serif Display `15px / 24px` and DM Sans `16px / 25.6px`. No unaccepted overflow or activation failure occurred; automated QA is not user approval.
  - Batch 5B AMS A1 evidence: every one of the 21 AMS A1 cards passed Filled and Blank at `1440 x 1000`, `768 x 1000`, and `390 x 844`, for 126 stable states. The scoped A1 grid uses the accepted `14px` gap, `14px` box corners, `280px` desktop Filled minimum, `120px` Blank minimum, `11px 16px` title padding, natural-height narrow Filled boxes, and 3/2/1 responsive tracks. Direct title and body typography remain DM Serif Display `15px / 24px` and DM Sans `16px / 25.6px`. No unaccepted visible overflow or activation failure occurred. Automated QA remains objective evidence, and the user separately visually approved the current AMS A1 comparison on `2026-08-15`.
  - Batch 5C MH A3 evidence: every one of the six MH A3 cards passed Filled and Blank at `1440 x 1000`, `768 x 1000`, and `390 x 844`, for 36 stable box-system states. The scoped A3 grid uses the accepted `14px` major gap, `14px` direct corners, `11px 16px` direct-title padding, `16px` Considerations frame with `14px` padding and `10px` inner gap, `11px` nested frames, and `9px 14px` nested-title padding. Direct title/body roles remain DM Serif Display `15px / 24px` and DM Sans `16px / 25.6px`; nested title/body roles remain `13.5px / 21.6px` and `16px / 25.6px`. User review subsequently found a stable 2px Previous/Next top offset that the first automated pass missed. The A3-scoped `5px` navigation top margin now aligns MN and MH exactly at `top 211.578px / bottom 252.773px / height 41.195px`. A later user review found MH's metadata-to-first-box gap at `12px` against MN's `18px`; the A3-scoped metadata margin now aligns both at `18px`, with identical split-pane landmarks and all six cards passing Filled/Blank plus standalone desktop/tablet/phone target-box checks. Automated QA is objective evidence; the user separately visually approved the corrected current MH A3 comparison in Part 192.
  - Batch 5D AMS A3 evidence: every one of the eight AMS A3 cards passed Filled and Blank at `1440 x 1000`, `768 x 1000`, and `390 x 844`, for 48 stable states after the A3-scoped metadata/direct/nested-box correction. Part 195 then reopened the family because the prototype Indications card stretched to `496.90625px`, leaving `361.71875px` of empty interior. Natural-height cards removed the interior void, but fresh user review exposed a `144.1875px` external gap between the `79px` GI Endoscopy Indications and Interpretation cards because desktop equal-row tracks survived the responsive stack. Part 197 groups Indications and Interpretation in a natural-height A3 role stack and resets stacked rows to automatic sizing. Every one of the 48 responsive Filled/Blank states now has an exact `14px` Indications-to-Interpretation gap, two stable reads, and zero text or structural-box overflow. The desktop `14px` relationship connector and visible Blank writing lines remain intentional exceptions. Automated QA is objective evidence; the user visually approved this current repaired state in Part 198.
  - Batch 5E MH A5 history is superseded by Parts 215-216 for current spacing geometry. All seven MN A5 cards, six MH A5 cards, and the AMS A5 prototype fixture now retain `18px` metadata spacing and exact `14px` same-level section, parent-to-child, child-to-child, responsive stacked, and visible connector-strip boundaries. Filled and Blank validation at seven widths produced 196 twice-stable states with correct four/two/one-column behavior, correct connector visibility, and zero objective overflow. Current exact payload hashes are MN `7982cea4edee4e0621ca9f4be30f1bc142fa129352c9cbf57f59a701da149bef`, MH `a716b3c4d9ca61b66702ca05a1e9097933664be4a5ce99b8321db6dac51fcab0`, and AMS `2bf9355dee1525c13a8d1b447d1c3e811d61e2ecdbbfeeabb8a468fb3e3bc679`. The user visually approved this normalized cross-book state in Part 216.
  - Hubs: current-complete for this shell pass; reopen only for a concrete defect or approved rollout need.
  - Books: current-complete for the chapter-modal navigation shell pass; reopen only for a concrete visual/navigation defect.
  - Flashcards: paused; do not resume until the user explicitly reopens flashcard shell work.
  - Current clipping-heartbeat completion state: the four-batch MH rollout queue, all 16 Build Guide AI-spec polishing batches, all 24 MN/MH/AMS template-family clipping items, all three shell items, and the final cross-book integrity gate are complete under private master Parts 79-100. The clipping heartbeat remains paused after the user completed and approved the overall template visual review on 2026-07-17. All 24 MN, MH, and AMS template-family items have objectively passed their collapsed-header, Filled/Blank, and desktop/split-pane/phone gates; the user completed and approved the overall template visual review on 2026-07-17. The Bishop Score repair remains clear across the completed 46-card MN A1 family pass. MH A15 retained all five official boxes, two metadata rows, its `500px 500px` desktop grid, and its accepted one-column split-pane/tablet and phone layouts across all six cards. AMS A1 retained all 21 visible cards, including the existing prototype fixture, three official boxes, three metadata rows, three equal desktop columns, and one-column split-pane/tablet and phone layouts. AMS A3 retained all eight visible cards, including its prototype fixture, seven direct/nested boxes, three metadata rows, a two-column desktop procedure grid, and one-column tablet/phone layouts; its 14px Potential Complications connector is visible geometry across the desktop gap, not clipped content. AMS A5 retained its prototype fixture, eight official boxes, two groups, three metadata rows, four-column desktop rows, two-column split-pane/tablet rows, and one-column phone layout; its visible parent-to-child connector stems remain contained relationship geometry, not clipped content. AMS A7 retained all 16 visible cards, nine official boxes, four metadata rows, its two-column desktop medication body, and its stacked split-pane/tablet and phone body; the Nursing Interventions-to-Client Education connector remains contained relationship geometry, not clipped content. AMS A9 retained all four visible cards, seven official direct/nested boxes, the Considerations parent, three metadata rows, its `500px 500px` desktop procedure grid, and its accepted one-column split-pane/tablet and phone layouts; the 14px Potential Complications connector remains contained desktop relationship geometry and is hidden by the established narrow rule. AMS A11 retained all 16 visible cards, the three-box top row, four-box Assessment group, Safety/Complications rail, five-box Patient-Centered Care group, and three metadata rows; desktop preserved its wide rail layout while tablet and phone used contained outer/top stacks, two-column Assessment, natural Safety stacking, and adaptive Patient-Centered Care tracks. AMS A13 retained all 17 visible cards, seven official direct/nested boxes, the Considerations parent, three metadata rows, its `500px 500px` desktop procedure grid, and one-column split-pane/tablet and phone layouts; the 14px Potential Complications connector remains contained desktop relationship geometry and is hidden by the established narrow rule. AMS A15 retained its one visible prototype fixture, five official boxes, the three current rendered metadata rows, its `500px 500px` desktop grid, two `359px` split-pane/tablet tracks, and its accepted one-column phone layout; paired rows, content, controls, and sibling boxes remained contained. This clipping-only pass did not change source-line metadata or establish a new metadata-row canon decision. The MN, MH, and AMS landing shells, fixed/responsive sidebars, eight collapsed family headers per book, landing controls, and representative modal chrome objectively passed stable desktop/tablet/phone clipping QA with zero confirmed clipping and no product repair; the user completed and approved the overall template visual review on 2026-07-17. Build Guide polishing Batches 1-16 are passed, including the v4 inventory/skeleton, Execution Contract, Manifest And File Contract, Global Design Canon, Hub Specification, Book Specification, Templates Specification, Flashcards Specification, Placeholder And New-Husk Protocol, Empty-Box And Content-Population Protocol, Deterministic Build Pipeline, QA Specification, and Recovery And Operations, plus Canon Reconciliation And Complete Traceability and v4-Only Cold-Start Validation. The v4 AI execution specification is complete and cold-start validated with 1617 unique requirements. The user-approved MN Student Name alignment now gives all 197 worked cards the shared 120px by 18px dashed writing line in both Filled and Blank modes without changing metadata labels or learner content. The clipping matrix and final cross-book integrity gate are complete; no clipping item is active. Each clipping run owns one book/template family, scans every card in collapsed/Filled/Blank states, requires stable repeated overflow evidence before editing, makes at most one repair, and cannot call automated QA user visual approval. The completion gates and handoffs have passed: both automations are paused, and every protected configuration field is preserved.
  - Pediatric rollout history (superseded by the Batch 10 completion update below): `ati-pediatric-templates-design-polish` owned `Elevated ATI PD Templates.html` during Batches 0-10. Batch 0 passed without a product edit: SHA-256 `f6e66b9ee8f76f6c2ce0cbdb3687ed63ffea336a7c11b915d8336e3df370f1c5`, one parsed inline script, 179 cards, 179 unique IDs, exact family counts `12/9/5/13/9/116/9/6`, canonical family order, 179 resolving chapter links, unique static IDs, required shell landmarks, stable storage keys, exact temporary payload parity, and a live PD-versus-MN comparison at `http://127.0.0.1:8765/elevated-ati-template-compare-pd-mn.html`. Desktop, tablet, and phone landing states had `0px` horizontal overflow; search, A1 expansion, Filled/Blank, same-family navigation, print controls, and modal close passed; stable desktop and phone modals kept every measured control inside with `0px` horizontal page/modal overflow. Batch 1 A1 passed after one focused CSS correction: every one of its 12 cards now uses the accepted `14px` grid gap and computed `16px/1.6` body typography across 72 stable Filled/Blank responsive states, with exact three-box and metadata order, contained Student Name lines, intact Blank structure, and zero objective overflow. Batch 2 A3 passed after one cohesive CSS correction: all nine cards retained exact metadata/box relationships and now use a `14px` gap, computed `16px/1.6` body typography, natural-height Considerations, contained desktop connector, usable Blank writing areas, and an exact 860px one-column transition. Ninety stable Filled/Blank states across desktop, tablet, phone, 861px, and 860px had zero objective overflow; the post-A3 hash was `93170cc2db6587f3d9954a3b2e3657b5ff51ebd8040b98f3997322cfba941837`. Batch 3 A5 passed after one cohesive CSS correction: all five cards preserve the bordered Expected Growth group and transparent Health Promotion tree; use `20px/12px` spacing, computed `16px/1.6` body typography, natural Filled heights, exact 4/2/1 tracks around 1100px and 600px, leak-free Blank mode, and `120px` writing areas. Seventy stable Filled/Blank states across seven viewports had exact labels/relationships, contained Student Name lines, and zero objective overflow; the post-A5 hash was `77b8cb40a3fb917b592e2b9f950c6673c89dc223ffaa812bcc2f5b3a019906c6`. Batch 4 A7 passed after one cohesive CSS correction: all 13 cards retain the permanent nine-box skeleton, four metadata labels, and Student Name line; use a `14px` body gap, computed `16px/1.6` body typography, content-driven Filled heights, permanent empty slots, `120px` Blank writing areas, the exact 680px stack transition, and a visible contained Nursing Interventions connector. One hundred thirty stable Filled/Blank states across five viewports had zero answer leakage and zero objective clipping; post-A7 PD Templates SHA-256 was `a2de1a39fc2c1d2c7ba2ba7435a7239286b53dec546c3c090a31234eae13dbad`. Shared landing-header and Filled/Blank semantics plus Previous/Next mode preservation are explicitly queued for the common shell/modal Batch 9. Batch 5 A9 Nursing Skill passed after one cohesive CSS and renderer-guard correction: all nine cards preserve the permanent six-region skeleton, three metadata rows, two nested Considerations boxes, `14px` gap/connector, computed `16px/1.6` body typography, the `14px/16px/11px` corner hierarchy, natural Filled heights, `120px` Blank writing areas, and the exact 681/680 transition. Ninety stable Filled/Blank states across five viewports had zero narrow overflow and zero unexpected wide overflow; the post-A9 PD Templates SHA-256 was `453dfc05a412e5676b5856130dbb4884025a5b7fde5a88aa070630d40f40dc69`. Batch 6 A11 System Disorder passed after one cohesive CSS and exact-routing correction: all 116 cards preserve the permanent 14-region skeleton, strict title-first routing, permanent empty regions, equal content-aware Safety rows, natural height and wrapping, the exact 901/900 A11 transition, 2-by-2 narrow Assessment, and stacked five-box Patient-Centered Care. The final 1,160 stable Filled/Blank states across desktop, tablet, phone, 901px, and 900px had zero hidden regions, unequal wide rows, geometry failures, or objective clipping; the post-A11 PD Templates SHA-256 was `3647ee5d223bfebd865a6977b48bfc17d518b12c69fd8ab6f90e6dbb0cde8b87`. Batch 7 A13 Therapeutic Procedure passed after one cohesive grid/renderer correction: all nine cards preserve the permanent official structure, exact metadata, `14px` relationship gap and connector, natural Filled heights, `120px` Blank writing areas, and exact 901/900 responsive transition. Ninety stable Filled/Blank states had zero objective clipping after repair; current PD Templates SHA-256 is `58646dec8910cf1cad12a4bab50bb159b466fdd4d514dd37b804105037513998`. Batch 8 A15 Concept Analysis passed after one cohesive metadata, spacing, typography, natural-height, corner, and responsive correction: all six cards preserve the exact two-row metadata and five official boxes; use `14px` gaps/corners, computed DM Sans `16px/1.6` body text, natural Filled heights, `120px` Blank writing areas, equal paired wide rows, and the exact 721/720 transition. Sixty stable Filled/Blank states across five viewports had zero objective clipping; current PD Templates SHA-256 is `f7dd6120ade44347d7c13f935032bf126aec1e6253885fa1e1c60650fcbe724e`. Batch 9 landing shell/sidebar/modal chrome subsequently passed. Each family batch owns one family, scans every card in collapsed/Filled/Blank states at desktop, split-pane/tablet, and phone widths, and includes objective clipping checks. The completed Build Guide and clipping automations remain paused and unchanged. Automated QA is not user visual approval.

  - Pediatric Batch 9 completion update (supersedes the preceding Pediatric rollout bullet's older active-item/current-hash sentences): the shared landing/sidebar/modal behavior passes with resolving accordion/drawer relationships, synchronized expanded/inert/focus state, keyboard-operable landing rows, contained/restored modal focus, unique and cleared modal clones, synchronized Filled/Blank tab state, and Blank preservation through progress plus Previous/Next. All eight landing headers now use direct caret, title, A-page badge, row print, studied count, and progress children. Desktop and tablet match MN at `89.59375px` header / `91.59375px` outer height and a `24.5px` borderless print control; adaptive phone rows remain contained. Stable desktop/tablet/phone measurements retained `0px` horizontal page, open-drawer, header, modal-shell, and modal-body overflow. Current PD Templates SHA-256 is `72a1f358462d5098eaeb1d6dd2c0a963c2dd1f2f7f40e5784804347813f2a96d`. Batch 10 subsequently passed as recorded below. Automated QA is not user approval.

  - Pediatric Batch 10 completion update (supersedes every preceding Pediatric active-item sentence): `PD_TEMPLATE_DESIGN_STATUS: READY_FOR_USER_VISUAL_REVIEW`. Batches 0-10 are objectively passed. The current 179-card product hash remains `72a1f358462d5098eaeb1d6dd2c0a963c2dd1f2f7f40e5784804347813f2a96d`; scripts, unique IDs, family order/counts, links, storage keys, exact temporary payload parity, all eight representative family modal types in Filled/Blank mode, stable desktop/tablet/phone shell states, Student Name writing lines, accepted connector geometry, drawers, search restoration, same-family Blank-mode navigation, focus restoration, duplicate-ID checks, HTTP comparison availability, empty browser warning/error logs, and guide consistency pass. `ati-pediatric-templates-design-polish` is paused with its protected configuration preserved. User visual approval remains pending, content population remains paused, and no product rollout is active.

  - Pediatric user-review navigation correction: the user identified that the narrow PD comparison pane omitted MN's visible `Back to Hub` control. Pediatric now has a separate responsive link to `Elevated ATI PD Hub.html` at its established 860px off-canvas breakpoint, paired with the menu on the opposite side and excluded from print. Wide desktop retains the sidebar Hub link. Stable `1440 x 1000`, `768 x 1000`, and `390 x 844` checks found the correct visibility, destination, spacing, no overlap, and `0px` horizontal page overflow. Current PD Templates SHA-256 is `5bab1082071db7390a55da58f88333018a778289f7872e1d6d42d2edc4afbbff`; the 179-card payload contract remains unchanged and user visual review continues.

  - Pediatric section-first Section 0 completion: the exact current MN and Pediatric payloads were measured through a nine-section, 101-role contract at desktop, split-pane/tablet, and phone widths. All 36 state captures repeated identically, 24 screenshots remain outside the repository, browser warning/error logs were empty, and the final selector map has zero unexpected gaps. The contract confirmed landing hero typography/spacing differences and search panel/input/placeholder/result-count differences, assigning them to Sections 1 and 2 respectively. No product file changed, and automated QA is not user approval.

  - Pediatric section-first Section 1 completion: the focused landing upper-half correction sets the shared MN typography/spacing and control contract without modifying search/discovery, accordion, sidebar, modal, cards, or learner content. Stable desktop/tablet/phone measurements, screenshots, one inline-script parse, 179 cards/unique IDs, exact `12/9/5/13/9/116/9/6` counts, storage keys, and `git diff --check` pass. Pediatric's current SHA-256 is `17a954117f6a16e618c44c51043ea2297f879a0ba885f229d56417b238d5682d`; automated QA is not user approval. Section 2 Search and Discovery Panel is the only active item.

  - Pediatric section-first Section 2 completion: the focused search-only correction aligns the visible filter panel, label, input, placeholder, focus ring, and responsive geometry to MN without changing accordion rows, cards, or learner content. Stable desktop/tablet/phone measurements, one inline-script parse, 179 cards/unique IDs, exact `12/9/5/13/9/116/9/6` counts, storage keys, temporary payload parity, and `git diff --check` pass. Pediatric's current SHA-256 is superseded by the Section 3 record below; automated QA is not user approval.
  - Pediatric section-first Section 3 completion: the focused shared-accordion correction restored MN-visible A-page badge contrast, a single `14px` inter-row gap, matching title/badge/print/progress typography, and the `8px` inner rail without changing learner content or registry state. All eight rows passed stable desktop/tablet/phone measurements and click-plus-Enter open/close behavior. Static parsing, 179 cards/IDs, exact `12/9/5/13/9/116/9/6` counts, family order, local HTML links, storage keys, temporary payload parity, and `git diff --check` pass. Pediatric's recorded SHA-256 is superseded by the Section 4 record below; automated QA is not user approval.
  - Pediatric user-review accordion entrance correction: the perceived oversized row spacing was objectively a `6px` search-to-first-row offset, not the seven inter-row gaps. MN measured a `12px` entrance boundary while Pediatric measured `18px`; Pediatric now keeps its existing hidden result-count behavior and restores MN's `-6px` hidden-count layout contribution only in that state. Both panes now measure eight `92px` rows, seven `14px` row gaps, and a `12px` entrance boundary; Pediatric retains 179 cards and 179 unique IDs. The recorded SHA-256 is superseded by the Section 4 record below. Automated QA is not user approval.
  - Pediatric section-first Section 4 completion: the user-requested lower-landing correction gives the existing Pediatric reset MN's unboxed `11px` treatment and gives the Pediatric footer MN's `60px` lead-in, `30px` padding, one-pixel divider, `13px` type, and `99px` footprint. A follow-up user review added MN's two footer roles with Pediatric-specific subject, edition, page-range, and Hub metadata, replacing the prior standalone `Open PD Book` footer link. The endpoint correction sets Pediatric terminal padding to `91px` at desktop and `71px` below `900px`; the restored Wide desktop overlay harness now verifies equal frame width, equal `1105px` endpoint range, and exact `520px` scroll lock in the local wide canvas. 179 cards and 179 unique IDs remain. Current Pediatric SHA-256 is `9b157a0f0a10df9eee90968a23c1e4a9033847b0b037c2875c9395edb0b06400`. Automated QA is not user approval. Its former Section 5 active-item statement is superseded by Part 130; Section 6 is current.

## Recovery Documentation Canon

- [ ] Keep each design run to one focused book/template defect or one documentation batch.
- [ ] For clipping QA, require the exact book/family/card ID, stable selector, viewport, current payload parity, and more than 1px of measured overflow or a matching out-of-container bounding box before editing. Inspect each visible collapsed accordion header, but exclude its intentionally hidden body along with inactive tabs, intentional scrolling, deliberate line clamps, closed off-canvas elements, and comparison chrome.
- [ ] Normalize browser zoom to 100%, wait for fonts/assets and settled layout, then require two identical measurements at least 250ms apart. Do not edit from unstable measurements.
- [ ] Never fix clipping by shrinking typography below canon, adding ellipses or line clamps, hiding content, broadening `overflow:hidden`, or adding a scrollbar. Repair the responsible container, grid/flex track, wrapping, or responsive geometry.
- [ ] After a clipping repair, repeat the same selector/viewport measurements and verify sibling boxes, scripts, counts, IDs, payload parity, responsive behavior, and `git diff --check` before advancing the matrix.
- [ ] For every remaining family batch, measure actual visible box-to-box boundaries in addition to computed CSS `gap`. Do not assume MN is correct when visible boundaries differ. Rebuild both product payload copies and every embedded comparison iframe cache key after any spacing change before asking for visual review.
- [x] A3 official connector canon is responsive, overlapped, and behind the cards rather than removable or front-layered: `Potential Complications` and `Nursing Interventions` use a centered `34px × 3px` horizontal bridge in two columns and a centered `3px × 34px` vertical bridge when stacked. Both orientations span the exact visible `14px` gap, extend `10px` beneath each adjacent box, and use `z-index:-1` so the box surfaces mask the overlap and the visible segment appears flush with both borders. MN, MH, and AMS preserve this relationship in Filled and Blank modes without changing A9/A13.
- [x] AMS A5 follows the Parts 215-216 normalized A5 spacing contract: `18px` metadata boundary and exact `14px` same-level section, parent/child, sibling, stacked, and visible connector-strip relationships at every breakpoint. Filled/Blank checks across all seven widths pass with zero overflow, and the user visually approved the cross-book normalization.
- [x] MH A7 follows the accepted Medication role hierarchy: `18px` metadata boundary, `14px` Purpose-to-body and peer body row/column gaps, and `10px` nested Purpose inset/inner spacing. Direct body boxes use `14px` frames with `13px` header caps and the shared `47px` title stack (`11px 16px`, `24px` line height); the intentionally compact Purpose role uses a `16px` group, `11px` clipped inner frames, and `38.25px` square title strips (`10px 16px`, `17.25px` line height). Its body remains two columns through `681px` and stacks at `680px` and below. All 12 cards passed 120 twice-stable Filled/Blank states with zero objective overflow; fresh user visual approval is pending.
- [x] AMS A5 received fresh user visual approval. AMS A7 now uses an `18px` metadata-to-Purpose boundary while preserving the accepted `14px` primary/body and `10px` Purpose inset/inner spacing. All 16 cards passed 96 Filled/Blank desktop/tablet/phone states with zero overflow; AMS A7 fresh user visual approval remains pending.
- [ ] Store before/after screenshots only for confirmed defects under `/private/tmp`; never add generated clipping-QA artifacts to the repository.
- [ ] Allow the resumed heartbeat to continue only known tracked changes documented in the recovery snapshot; stop on unexpected, contradictory, or concurrently owned changes.
- [ ] After every completed batch, update the private master Build Guide and `Build Guide Current Overlay.md` with current status, files, validation, pending approval, Git state, and one next action.
- [ ] Never commit or push from a heartbeat without the user's explicit instruction.
- [ ] Update this checklist whenever an accepted canon rule changes; update `AMS Prototype MN Canon Audit.md` whenever AMS audit status or evidence changes.
- [ ] Keep `codex-build-guide-archive-20260707` immutable as the July 4 baseline.
- [ ] Before ending, verify that a new task can resume from files alone without opening an older task.

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

- [ ] Use MN as the primary structural/mobile reference and AMS as the polished visual reference.
- [ ] Work one book and one focused template/design defect per batch; do not infer a broad rollout from an older recommendation.
- [ ] Do not add ATI educational content in DESIGN-CANON / HOLD-CONTENT mode.
- [ ] Preserve each book's accent color, subject identity, existing content, and official ATI template box relationships.
- [ ] Do not commit or push without the user's explicit instruction.
- [x] Preserve the official A9 Potential Complications-to-Nursing Interventions relationship responsively in MN, MH, and AMS. Wide state uses a centered horizontal two-layer bridge; stacked state uses a centered vertical two-layer bridge. The long layer extends beneath both box surfaces at `z-index:-1`, while a `14px` gap-only layer at `z-index:0` keeps the visible segment flush without drawing over either surface. Position that visible layer at `gap + border`, currently `right:-15px` or `bottom:-15px`, so it begins and ends at the outer edges of the two `1px` card borders. Use each book's accepted overlap token: `10px` for MN/MH and `8px` for AMS. The displayed MN/MH treatment received fresh user visual approval in Part 225.
- [ ] Before future implementation, compare proposed AMS changes against this checklist and mark each item Done, Partial, or Not done based on actual file evidence.

## Part 226 Current Gate — MH A11 Visual Review

- The accepted A11 hierarchy is now explicit in MH: `18px` metadata-to-grid separation; `14px` major-region gaps; `10px` inner group gaps; a `2fr/1fr` wide outer division; `14px` primary, `16px` group, and `11px` nested corners.
- Role typography remains intentionally differentiated. The three direct top-row boxes use DM Serif Display `15px/24px` titles and DM Sans `16px/25.6px` copy. Patient-Centered Care uses nested `13.5px/21.6px` titles with primary explanatory `16px/25.6px` copy. Assessment and Complications retain dense `13px/19.5px` copy; Safety remains `13px` at `1.55`.
- At the exact MH `861/860px` transition, the outer grid/top row/Patient-Centered Care change from 2:1/three/three columns to one/one/one column. Assessment deliberately stays 2-by-2, and Safety changes from equal content-aware rows to natural vertical stacking.
- Every one of the 12 MH A11 cards passed Filled and Blank at `1440`, `861`, `860`, `768`, and `390px`: 120 twice-stable responsive states and 24 twice-stable print states with no role, geometry, breakpoint, containment, or overflow failure. The official 14-region skeleton and all identity-bearing data remain unchanged.
- Current exact-payload comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a11-canon-fix`. MH A11 is objectively passed and pending fresh user visual approval. MH A13 has not begun.
- Content population remains paused. ATI source support used: none; design-only change. No stage, commit, or push occurred; all four automations remain paused and unchanged.

## Part 229 Current Gate — MH A11 End-Space Visual Review

- MH A11 uses a dedicated `24px` trailing card margin in addition to the shared `40px` modal bottom padding, yielding an approximately `64px` visible endpoint after Patient-Centered Care without changing the official 14-region skeleton.
- All 12 cards passed Filled and Blank at `1280px` and narrow split-pane width: 48 endpoint states with zero modal horizontal-overflow failures. Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a11-end-space-guides-2`.
- MH A11 remains objectively passed and pending fresh user visual approval. MH A13 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 230 Current Gate — MN/MH A11 Matched End-Space Review

- MN and MH A11 now both use a `24px` trailing card margin in addition to shared `40px` modal bottom padding. At narrow comparison width, the existing `18px` card inset produces approximately `82px` of visibly matched endpoint space in each pane.
- All 65 MN cards passed Filled and Blank at `1280px` and narrow split-pane width: 260 endpoint states with no modal horizontal-overflow failures. The current comparison measures MN `81.96px` and MH `82.25px`.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a11-end-space-both-guides-2`. MH A11 remains pending fresh user visual approval. MH A13 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 231 Current Gate — Wait Before MH A13

- MH A11 System Disorder and the matched MN/MH endpoint treatment are objectively passed and user visually approved.
- The approved endpoint uses a `24px` trailing card margin plus the shared `40px` modal bottom padding. No product file changed while recording approval.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a11-end-space-both-guides-2`. MH A13 has not begun and requires a separate explicit instruction. Content population remains paused. ATI source support used: none; design-only change.

## Part 232 Current Gate — MH A13 Visual Review

- MH A13 now uses the accepted Therapeutic Procedure role system: `18px` metadata separation; `14px` direct gaps; `10px` nested gaps; `14px / 16px / 11px` direct/group/nested corners; `47px` primary title bands; role-matched nested titles; and readable `16px / 25.6px` body text.
- Potential Complications remains officially connected to Nursing Interventions in both orientations. The long `34px` bridge overlaps `10px` beneath each box at `z-index:-1`; the exact `14px` gap segment meets the outer border edges at `right:-15px` wide or `bottom:-15px` stacked. The family changes from horizontal at `861px` to vertical at `860px`.
- All ten cards passed 100 twice-stable Filled/Blank responsive states and 20 twice-stable print states. Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-canon-fix-2`.
- MH A13 is objectively passed and pending fresh user visual approval. MH A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 235 Current Gate — MH A13 Top-Stack Vertical Parity

- Therapeutic Procedure chapter jumps use the accepted MN source-row role: inline-block, `600` weight, and `2px` top margin beneath the explicit line break. This preserves a full second-row line box before navigation.
- At the focused split width, MH and MN now share the same example-header bounds, navigation bounds, metadata starting edge, `18px` header-to-metadata distance, `16px` header bottom padding, and `18px` header bottom margin. Natural title and metadata wrapping may change later endpoints; do not shrink, clamp, or hide text to force equal content-dependent heights.
- All ten MH A13 cards passed 100 stable Filled/Blank states at `1440`, exact `861/860`, `768`, and `390px` with no spacing, connector, Blank, or overflow failure. Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-top-stack-parity-3`.
- MH A13 remains objectively passed and pending fresh user visual approval. MH A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 236 Current Gate — MN/MH A13 Connector Visual Review

- MN and MH A13 both preserve the official Potential Complications-to-Nursing Interventions relationship. Wide uses a centered `34px x 3px` long layer and `14px x 3px` visible gap layer; stacked uses `3px x 34px` and `3px x 14px` equivalents across the exact `14px` gap.
- The long layer extends `10px` under each adjacent surface at `z-index:-1`, while the gap-only layer stays flush with the two outer border edges. All 22 MN A13 cards now carry both relationship classes; no learner content changed.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a13-connector-both-sides-final`. Fresh user visual confirmation is pending. MH A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 237 Current Gate — MN/MH A13 Endpoint Visual Review

- Therapeutic Procedure modal cards in MN and MH now use a scoped `24px` trailing margin plus the shared `40px` modal bottom padding, matching the user-approved A11 endpoint treatment.
- The current narrow comparison measures `64.09px` visible endpoint space on MN and `63.88px` on MH after Nursing Interventions, twice-stably and with zero horizontal overflow.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a13-end-space-both-final`. Fresh user visual confirmation is pending. MH A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 238 Current Gate — Wait Before MH A15

- MH A13 Therapeutic Procedure is objectively passed and user visually approved, including top-stack alignment, typography, spacing/corners, the official responsive connector, and the approximately `64px` endpoint.
- The displayed MN A13 connector and endpoint treatment are also user visually approved. No product file changed while recording approval.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a13-end-space-both-final`. MH A15 has not begun and requires a separate explicit instruction. Content population remains paused. ATI source support used: none; design-only change.

## Part 239 Current Gate — MH A15 Visual Review

- MH A15 now follows the accepted Concept Analysis contract across all six cards: `18px` metadata-to-grid spacing; five official boxes in the order Defining Characteristics, Antecedents, Negative Consequences, Related Concepts, Exemplars; exact `14px` peer gaps/corners; DM Serif Display `15px / 24px` primary strips with `11px 16px` padding and `47px` one-line height; DM Sans `16px / 25.6px / 400` rendered descendants; natural Filled heights; `120px` Blank writing areas; equal paired wide rows; and an exact `721px` two-column / `720px` one-column transition.
- The family passed 60 twice-stable responsive states and 12 twice-stable print states with no official-order, typography, spacing, Blank, containment, or overflow failure. Learner content, labels, counts, IDs, chapter links, storage, order, accent, and subject identity remain unchanged.
- Current exact-payload comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a15-canon-fix-2`. MH A15 is objectively passed and pending fresh user visual approval. AMS A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 240 Current Gate — MN/MH A15 Endpoint Visual Review

- Concept Analysis modal cards in MN and MH now use the established endpoint contract: a scoped `24px` trailing card margin plus the shared `40px` modal bottom padding.
- The current split comparison measures MN `63.88px` and MH `64.27px` after Exemplars twice-stably. All 15 MN/MH A15 cards passed both modes at split-pane and exact phone-family widths: 60 endpoint states with exact `14px` peer gaps and no horizontal overflow.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a15-end-space-both-final`. Fresh user visual confirmation is pending. AMS A15 has not begun. Content population remains paused. ATI source support used: none; design-only change.

## Part 241 Current Gate — Wait Before AMS A15

- MH A15 Concept Analysis is objectively passed and user visually approved, including spacing, banner geometry, role typography, corners, Blank behavior, responsive geometry, and the approximately `64px` endpoint.
- The displayed MN/MH A15 endpoint treatment is also user visually approved. No product file changed while recording approval.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=a15-end-space-both-final`. AMS A15 has not begun and requires a separate explicit instruction. Content population remains paused. ATI source support used: none; design-only change.

## Part 242 Current Gate — AMS A15 Visual Review

- AMS A15 now follows the accepted Concept Analysis contract: `18px` metadata spacing; five official boxes in order; exact `14px` peer gaps/corners; DM Serif Display `15px / 24px` banners with `47px` one-line height; DM Sans `16px / 25.6px / 400` rendered copy; natural Filled heights; `120px` Blank areas; equal wide pairs; exact `721/720px` transition; and `24px` card margin plus `40px` modal padding.
- The single retained AMS prototype fixture passed 10 twice-stable responsive states and two print states with correct order, typography, spacing, Blank behavior, endpoint space, and no horizontal overflow. Learner content and identity-bearing data remain unchanged.
- Current exact-payload comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-canon-fix`. AMS A15 is objectively passed and pending fresh user visual approval. No later batch began. Content population remains paused. ATI source support used: none; design-only change.

## Part 243 Historical Gate — Cross-Book Modal Top-Stack Visual Review (Superseded by Part 352)

- Historical evidence: MN, MH, and AMS temporarily used a `100.4px` minimum title row above `600px` and a `104.8px` minimum at `600px` and below. The user explicitly superseded that fixed two-line reservation in Part 352 after it produced visible empty space on a one-line MN A1 title.
- The first Worked Example edge is exact across books at all required widths: `28px` desktop, `46px` split-pane/tablet, and `20px` phone. AMS now includes the missing `18px` tablet card inset already used by MN/MH.
- Twice-stable Filled/Blank rendered checks, scripts, counts, IDs, links, payload parity, and diff integrity pass. Current comparisons: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=top-stack-uniform-final` and `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=top-stack-uniform-final`. Fresh user visual confirmation is pending. Content population remains paused. ATI source support used: none; design-only change.

## Part 244 Current Gate — Full Worked-Example Top-Stack Visual Review

- User grid review correctly rejected Part 243 as incomplete. MH still rendered `Open chapter` inline at weight `800`, whereas MN and AMS render it as a separate `inline-block` row with a `2px` top offset and weight `600`. That shortened the MH A15 example header by exactly `3px` and shifted navigation, metadata, and every box below it.
- The established source-jump role is now global across MH, replacing the former A13-only exception. At the current `557/558px` split width, MN and MH now repeat the exact same landmarks twice: banner bottom `135.796875px`, example header `155.796875–356.5703125px`, navigation `298.375–339.5703125px`, metadata `374.5703125–457.8671875px`, and first box edge `475.8671875px`. Filled and Blank remain identical.
- The same MN/MH role chain is twice-stable at `1440px` and `768px`; phone checks retain the same source-row styles while natural title and metadata wrapping may expand their own content boxes. All 71 current MH cards retain chapter links and inherit the shared selector. Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=top-stack-source-row-final`. Fresh user visual confirmation is pending. Content population remains paused. ATI source support used: none; design-only change.

## Part 245 Current Gate — AMS A15 Visual Review

- The user visually approved the Part 244 gridded MN/MH state. The complete MN/MH modal top stack is now accepted from title banner through first box, including the separate chapter-jump row and natural content wrapping.
- No product file changed while recording approval. Part 244's exact landmarks, Filled/Blank parity, responsive evidence, 71-card/link coverage, payload hash, scripts, IDs, links, storage, and diff integrity remain current.
- Approved MN/MH comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=top-stack-source-row-final`. AMS A15 remains objectively passed and pending separate fresh user visual approval. Content population remains paused. ATI source support used: none; design-only change.

## Part 246 Current Gate — AMS A15 Official Metadata Review

- Concept Analysis metadata canon is exactly two ordered pairs: `Student Name` and `Concept Analysis`. `Review Module Chapter` must not render inside the A15 metadata box, although it remains valid for other AMS template families.
- AMS A15 now enforces that existing canon in the shared metadata builder. Filled and Blank both render two pairs at `83.296875px`, matching MN A15; other families retain their source row.
- The historical clipping-only checkpoint that recorded three current AMS A15 metadata rows is superseded by this official two-row canon enforcement; it remains history, not current design authority.
- Current exact-payload comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-official-meta-final`. AMS A15 is objectively passed and pending fresh user visual confirmation of this correction. Content population remains paused. ATI source support used: none; design-only change.

## Part 247 Current Gate — Final Cross-Book Regression Not Begun

- AMS A15 is objectively passed and user visually approved with the official two-row metadata, accepted top stack, five-box structure, role typography, spacing/corners, Blank geometry, breakpoint, and endpoint.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-official-meta-final`. No product file changed while recording approval.
- The next permitted design-canon batch is the final cross-book template regression and integrity handoff. It has not begun and requires a separate explicit instruction. Content population remains paused. ATI source support used: none; design-only change.

## Part 248 Current Gate — Final Regression Tranche 1 Pending Visual Review

- MN A13 Therapeutic Procedure canon requires six direct regions in official order: Description, Indications, Outcomes/Evaluation, Considerations, Potential Complications, and Nursing Interventions. Considerations contains exactly two nested roles: Nursing Interventions (pre, intra, post) and Client Education.
- Four legacy MN cards violated that skeleton by nesting Outcomes/Evaluation. They are now normalized without changing learner text; all 22 MN A13 cards pass the official structure inventory. Focused Blank evidence is `120px` direct boxes, `91px` nested boxes, exact `14px` gaps, and zero overflow.
- Cross-book representative regression covers 276 Filled/Blank states at desktop, tablet/split-pane, and phone widths. Exact `14px` peer gaps, endpoint padding, and zero content/modal overflow pass throughout.
- Final completion remains blocked by objective AMS legacy differences: A9/A13 metadata boundary `12px`, A11 metadata boundary `14px`, and A13's front-layer connector that fails to rotate at stacked widths. These are queued as later cohesive family repairs, not silently accepted as canon.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=final-a13-skeleton-repair-248`. MN A13's corrected skeleton is objectively passed and pending fresh user visual approval. Content population remains paused. ATI source support used: none; design-only change.

## Part 249 Current Gate — MN A13 Skeleton Approved

- The user visually approved the Part 248 MN A13 repair. The full 22-card A13 structure inventory is accepted with six official direct regions and exactly two nested Considerations roles.
- Part 248's `120px` direct Blank boxes, `91px` nested Blank boxes, `14px` peer gaps, zero overflow, and exact payload integrity remain current.
- This approval does not waive the documented AMS A9/A11/A13 mismatches. AMS A9 Nursing Skill is the next gated family and requires a separate explicit instruction. Content population remains paused. ATI source support used: none; design-only change.

## Part 250 Current Gate — AMS A9 Matches Metadata Canon

- AMS A9 Nursing Skill now matches the accepted `18px` metadata-to-grid role across all four cards in Filled and Blank.
- The family retains the established `14px` peer gap, `14px/11px` corner hierarchy, role-matched typography, endpoint space, and official behind-box connector with the exact `935/934px` horizontal-to-vertical transition.
- Forty twice-stable states at `1440`, `935/934`, `768`, and `390px` pass with zero card/grid/modal overflow. AMS A9 is objectively passed and pending fresh user visual approval.
- AMS A11 and A13 remain separate later gates. Content population remains paused. ATI source support used: none; design-only change.

## Part 251 Current Gate — Uniform Modal Endpoint Canon

- Screen endpoint spacing is a shell invariant, not a family exception: every direct modal example card must end with `24px` trailing card margin plus `40px` modal bottom padding, for exactly `64px` of visible breathing room at the true scroll endpoint.
- Print must reset the screen-only card margin to `0`; it must not inherit the endpoint guard into paginated output.
- The old A11/A13/A15-only exceptions are superseded. MN, MH, and AMS now use the shared rule across A1/A3/A5/A7/A9/A11/A13/A15.
- Recurrence evidence: first and last examples in all eight families, Filled and Blank, at `1440`, `768`, and `390px` produced `276/276` twice-stable passes with exact `24px + 40px = 64px` endpoints and no horizontal overflow.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=global-endpoint-64-final`. Fresh user visual confirmation is pending. Content population remains paused. ATI source support used: none; design-only change.

## Part 252 Current Gate — Resumable Family Regression / AMS A11 Next

- Validation must enforce role values on the rendered descendants and the actual title-strip geometry, not only parent `.content` styles or the presence of boxes. AMS A9 proved that a family can retain correct structure, gaps, corners, and connector while its primary strips, nested strips, and direct/nested copy still violate the recorded canon.
- AMS A9 now exactly enforces its existing canon: direct strips `15px / 24px`, `11px 16px`, `47px`; nested strips `13.5px / 21.6px`, `9px 14px`, `40.59375px`; direct and nested descendants DM Sans `16px / 25.6px / 400`; direct content `14px 16px 16px`; nested content `12px 14px 14px`; Considerations `14px` inset, `10px` gap, `16px` corners; direct/nested corners `14px / 11px`.
- All four cards passed `40/40` twice-stable Filled/Blank responsive states at `1440`, exact `935/934`, `768`, and `390px`, including the two-layer connector, exact `18px` metadata and `14px` peer spacing, overflow, and the shell endpoint invariant. Automated QA is not user visual approval.
- The next active objective family is AMS A11. Subsequent retrospective runs follow the file-backed queue recorded in private master Part 252 and the overlay, one book/family at a time, with resumable checkpoints and no concurrent file ownership. Content population remains paused. ATI source support used: none; design-only change.

## Part 253 Current Gate — AMS A11 Matches System Disorder Canon

- AMS A11 now enforces the recorded A11 contract across all 16 cards: `18px` metadata, `14px` major gaps, `10px` nested gaps, `14px/16px/11px` corners, `47px` direct strips, `40.59375px` nested strips, and role-matched rendered descendants.
- Wide cards use the accepted `2fr/1fr` outer division and two equal content-aware Safety rows. The exact AMS card-width transition is wide at `935px` and stacked at `934px`; stacked Safety preserves `14px 14px 16px` padding and natural flow.
- All `224/224` true Filled/Blank responsive states and `32/32` print states passed twice with official 3/4/1/5 box counts, dashed `120px x 18px` Student Name line, no Blank leakage, zero overflow, and correct screen/print endpoints. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a11-canon-fix`. AMS A11 is objectively passed and pending fresh user visual approval. AMS A13 is next. Content population remains paused. ATI source support used: none; design-only change.

## Part 254 Current Gate — AMS A13 Screen Canon / Print Visibility Pending

- AMS A13 screen roles now match the accepted Therapeutic Procedure contract: 18px metadata; 14px peers; 10px nested spacing; 14px/16px/11px direct/group/nested corners; 47px direct and 40.59375px nested title stacks; 16px / 25.6px rendered descendants; and 14px Considerations inset.
- The official Potential Complications-to-Nursing Interventions connector must remain two-layered: a long layer behind the boxes plus a border-edge segment, horizontal for card widths above 820px and centered vertical at 820px and below, across an exact 14px visible gap.
- All 170/170 twice-stable Filled/Blank screen states pass across all 17 cards at 1440, exact viewport 935/934, 768, and 390px. Automated QA is not user visual approval.
- Print canon additionally requires that the complete #templateModal ancestor chain remain visible while non-modal page content is suppressed. The current global child selector hides the page ancestor and yields zero print rects, so Batch 2 remains **IN_PROGRESS** until that shell guard is repaired and all 34 A13 print states pass.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a13-canon-fix. Content population is paused. ATI source support used: none; design-only change.

## Part 255 Current Gate — AMS A13 Complete / MN A1 Next

- Modal print isolation must preserve the modal's complete ancestor chain. When the modal is nested under page and main wrappers, hide non-modal siblings at each ancestor rather than hiding the body-level page ancestor.
- AMS A13 passes 34/34 twice-stable Filled/Blank print states with visible page/main/modal/card geometry, hidden controls, transparent Blank answers, zero screen-endpoint guards, official structure, and zero horizontal overflow.
- Post-print-repair screen regression passes 170/170 twice-stable states across all 17 cards at 1440, exact 935/934, 768, and 390px. Automated QA is not user visual approval.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a13-print-canon-final. AMS A13 is objectively passed and pending fresh user visual approval. Batch 3 MN A1 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 256 Current Gate — MN A1 Complete / MH A1 Next

- MN A1 Basic Concept uses exactly three official direct roles in order: Related Content, Underlying Principles, and Nursing Interventions. The family contract is `18px` metadata, `14px` peer gaps/corners, DM Serif Display `15px / 24px / 400` strips with `11px 16px` padding, DM Sans `16px / 25.6px` rendered descendants, and `120px` Blank boxes.
- The exact responsive transition is two columns at `601px` and one column at `600px`; desktop remains three columns. The shared modal top stack and `24px` card margin plus `40px` shell-padding endpoint remain required, while longer title/source content may expand naturally.
- All 46 cards passed `460/460` twice-stable Filled/Blank screen states at `1440`, `768`, exact `601/600`, and `390px`, plus `92/92` twice-stable print states. Official order, metadata/Student Name, title/body roles, Blank hiding, endpoint reset, top-stack boundaries, and overflow all pass. No product correction was needed. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a1-objective-pass-2`. MN A1 is objectively passed and pending fresh user visual approval. Batch 4 MH A1 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 257 Current Gate — MH A1 Complete / AMS A1 Next

- MH A1 follows the same Basic Concept role contract as MN A1: three official direct boxes in order; `18px` top boundaries; `14px` peer gaps and corners; DM Serif Display `15px / 24px / 400` strips with `11px 16px` padding; DM Sans `16px / 25.6px / 400` rendered descendants; and `120px` Blank boxes.
- Exact MH responsive transitions are three columns at `901px`, two at `900px`, two at `601px`, and one at `600px`. The shared top stack, separate source-jump row, dashed `120px x 18px` Student Name line, and approximately `64px` screen endpoint remain mandatory.
- Print isolation must keep `body > .page.template-layout > .template-main > #templateModal` visible and hide only non-modal siblings at each ancestor level. This rule repaired MH's zero-geometry print failure and is now a recurring shell check for any book whose modal is nested under page/main wrappers.
- All 13 MH A1 cards passed `182/182` twice-stable screen states and `26/26` twice-stable print states. Official order, roles, Blank hiding, endpoint behavior, modal controls, and overflow pass. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a1-print-guard`. MH A1 is objectively passed and pending fresh user visual approval. Batch 5 AMS A1 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 258 Current Gate — AMS A1 Complete / MN A3 Next

- AMS A1 follows the shared Basic Concept role contract: three official direct boxes in order; `18px` Worked Example-to-metadata and metadata-to-grid boundaries; `14px` peer gaps and corners; DM Serif Display `15px / 24px / 400` strips with `11px 16px` padding; DM Sans `16px / 25.6px / 400` rendered descendants with `14px 16px 16px` padding; and `120px` Blank boxes.
- Exact AMS A1 responsive transitions are three columns at `901px`, two at `900px`, two at `601px`, and one at `600px`. The dashed `120px x 18px` Student Name line, source-jump row on learner-facing records, `24px + 40px` screen endpoint roles, and print reset remain mandatory.
- All 21 A1 records, including the intentionally hidden prototype fixture, passed `294/294` twice-stable screen states and `42/42` twice-stable print states. The prototype intentionally has no source jump; its geometry still passes. Official order, title/body roles, Blank hiding, endpoint behavior, print ancestor chain, controls, and overflow pass. No product correction was needed. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a1-objective-pass`. AMS A1 is objectively passed and pending fresh user visual approval. Batch 6 MN A3 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 259 Current Gate — MN A3 Complete / MH A3 Next

- A3's grid and official Potential Complications-to-Nursing Interventions connector must change orientation at the same breakpoint. Exact `681px` remains two-column with a centered `34px x 3px` behind-box connector; exact `680px` is one-column with a centered `3px x 34px` behind-box connector. General tablet rules must not reopen A3 columns after the connector rotates.
- The connector retains `10px` overlap hidden beneath each adjacent box, `z-index:-1`, and exactly `14px` of visible line between borders. The official order remains five direct boxes plus two nested Considerations roles; top boundaries are `18px`, peer gaps `14px`, nested gap `10px`, and corners `14px/16px/11px`.
- All 15 MN A3 cards passed `150/150` twice-stable Filled/Blank screen states at `1440`, `768`, exact `681/680`, and `390px`, plus `30/30` twice-stable print states. Role typography, Student Name, Blank geometry, endpoint/reset, controls, official structure, and overflow all pass. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a3-objective-pass`. MN A3 is objectively passed and pending fresh user visual approval. Batch 7 MH A3 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 260 Current Gate — MH A3 Complete / AMS A3 Next

- MH A3 follows the shared Diagnostic Procedure contract: five direct roles and two nested Considerations roles in official order; exact 18px/14px/10px boundaries; 14px/16px/11px corners; direct 15px / 24px and nested 13.5px / 21.6px DM Serif Display strips; DM Sans 16px / 25.6px / 400 descendants; and the dashed 120px x 18px Student Name line.
- The exact MH A3 responsive transition is two columns with a centered 34px x 3px behind-box connector at 861px, then one column with a centered 3px x 34px connector at 860px. Both preserve 10px hidden overlap, z-index:-1, and exactly 14px visible line between borders.
- Modal print must suppress the modal header, example controls, mode switch, family navigation strip, and Blank answers while preserving the complete page/main/modal/card chain. The A3 navigation omission is now repaired with an A3-scoped print rule.
- All six MH A3 cards passed 60/60 twice-stable screen states and 12/12 twice-stable print states. Structure, role typography, Blank behavior, approximately 64px screen endpoint / zero print reset, connector geometry, controls, and overflow pass. Automated QA is not user visual approval.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a3-print-nav-fix-260. MH A3 is objectively passed and pending fresh user visual approval. Batch 8 AMS A3 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 261 Current Gate — AMS A3 Complete / MN A5 Next

- AMS A3 follows the shared Diagnostic Procedure contract across all eight records: five direct and two nested roles in official order; exact `18px/14px/10px` boundaries; `14px/16px/11px` corners; direct `15px / 24px` and nested `13.5px / 21.6px` DM Serif Display strips; DM Sans `16px / 25.6px / 400` descendants; and the dashed `120px x 18px` Student Name line.
- The exact AMS A3 transition is horizontal at card width `821px` and stacked at `820px`. Its centered bridge remains `34px x 3px` wide or `3px x 34px` stacked, with `10px` hidden overlap, `z-index:-1`, and exactly `14px` visible line between box borders.
- Modal print suppresses the example controls, mode switch, family navigation strip, and Blank answers while preserving the complete page/main/modal/card chain. The A3 navigation omission is now repaired with an A3-scoped print rule.
- All eight AMS A3 records passed `112/112` twice-stable screen states and `16/16` twice-stable print states. Structure, role typography, Blank behavior, approximately `64px` screen endpoint / zero print reset, connector geometry, controls, and overflow pass. Automated QA is not user visual approval.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a3-print-nav-fix-261`. AMS A3 is objectively passed and pending fresh user visual approval. Batch 9 MN A5 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 262 Current Gate — MN A5 Parent Role / Blank Completeness

- A5's Health Promotion parent is a direct learner-answer role, not a typography exception. Its `.content` and rendered `p/li/ul/ol` descendants must use DM Sans `16px / 25.6px / 400`, matching the other A5 body copy while retaining `14px 16px` parent padding. The old `13px / 19.5px` rendering is repaired.
- Blank-mode completeness applies to the parent and all eight child answer regions. It is not sufficient for only `.tpl-group-body > .tp-box > .content` to collapse: `.health-promotion-group > .hp-parent > .content` must also expose no learner answer.
- All seven current MN A5 cards objectively leak the parent answer in Blank mode at stable heights `79.188–232.156px` while every child content is `0px`. Batch 9 remains IN_PROGRESS and must resume with an A5-scoped Blank parent repair before the family can pass.
- Current in-progress comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a5-parent-typography-fix-262`. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Resume MN A5 automatically at the Health Promotion Blank-answer leak; the user personally does not need to do anything and must not commit or push now.

## Part 263 Current Gate — MN A5 Complete / MH A5 Next

- A5 Blank-mode completeness is now enforced on the Health Promotion parent as well as all eight child answer regions. `.health-promotion-group > .hp-parent > .content` is hidden only in Blank mode, and the parent retains a `120px` writing surface. Filled parent content remains DM Sans `16px / 25.6px / 400` with `14px 16px` padding.
- All seven MN A5 cards passed `98/98` twice-stable Filled/Blank screen states at `1440`, exact `1101/1100`, `768`, exact `601/600`, and `390px`, plus `14/14` twice-stable print states. The exact `18px/14px` boundaries, four/two/one-column transitions, title/body roles, `14px/16px` corners, Student Name line, nine Blank writing surfaces, endpoint/reset, controls, official structure, and zero-overflow contract all pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a5-blank-canon-final-263`. MN A5 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 10 MH A5 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Continue automatically with MH A5; the user personally does not need to do anything and must not commit or push now.

## Part 264 Current Gate — Heartbeat Paused / MN A5 Visual Review

- `ati-retrospective-template-spacing-heartbeat` is **PAUSED** at the user's request with its name, complete prompt, heartbeat kind, 30-minute schedule, and target task preserved. Batch 10 MH A5 has not begun.
- Objective queue Batches 0 through 9 are complete. Automated QA is not user visual approval; all pending fresh visual gates remain pending.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a5-blank-canon-final-263`. MN A5 remains objectively passed and pending fresh user visual approval. Batch 10 MH A5 remains the next objective item only after a separate instruction to resume.
- Branch `main`, HEAD `acef952339eab701e18762152f73ccddb9494419`, `0` ahead / `0` behind, the six expected tracked modifications, current product hashes, and clean `git diff --check` remain unchanged. Nothing is staged, committed, or pushed. Content population is paused. ATI source support used: none; design-only change.
- `ati-build-guide-ai-spec-polish`, `ati-template-clipping-qa`, and `ati-pediatric-templates-design-polish` remain paused and unchanged.

**Next Recommendation:** The user should visually review MN A5 and report approval or the first mismatch; the user should not commit or push yet.

## Part 265 Current Gate — Nested Section-Title Rails Pending Visual Review

- Canon rule: a true outer label governing nested boxes uses the A5 centered section rail—`display:flex`, centered alignment, `14px` side gaps, `11px / 700 / .16em` uppercase role text, zero label padding, and `1px` border-color rails on both sides. Apply this to A3/A9/A13 `Considerations`, A7 `Purpose of Medication`, and A11 `Assessment`, `Safety Considerations`, and `Patient-Centered Care`, including the AMS A3 `.considerations-top` wrapper variant.
- Exclusion rule: do not convert A5 `Health Promotion`, because it is a titled parent box with official parent/child connectors. Do not convert A1 or A15, because their boxes are direct peers rather than nested-group children. Preserve A5 `Expected Growth and Development` as the reference rail.
- MN, MH, and AMS implementation passed `90/90` representative Filled/Blank responsive states at exact `1440`, `768`, and `390px`, with positive-width `1px` rails, exact `14px` gaps, zero padding, and zero overflow. Source inventory covered all `242` cards in the five qualifying families; exclusions matched no new rail selector.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-section-rails-mh-mn.html?v=section-title-rails-265`. The cross-book correction is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval.
- Content population is paused. ATI source support used: none; design-only change. The retrospective heartbeat remains paused, Batch 10 MH A5 has not begun, no stage/commit/push occurred, and the protected automations remain paused and unchanged.

**Next Recommendation:** The user should visually review the open A11 rail comparison and report approval or the first mismatch; the user should not commit or push yet.

## Part 266 Current Gate — Nested Section-Title Rails User Approved

- The user visually approved the Part 265 centered rail treatment. A3/A9/A13 `Considerations`, A7 `Purpose of Medication`, and A11 `Assessment`, `Safety Considerations`, and `Patient-Centered Care` are now accepted cross-book canon with the recorded `11px / 700 / .16em`, `14px` side-gap, zero-padding, and `1px` rail geometry.
- A5 `Health Promotion`, A1, and A15 remain intentionally excluded; A5 `Expected Growth and Development` remains the reference. No product file changed while recording approval.
- Content population is paused. ATI source support used: none; design-only change. The retrospective heartbeat remains paused, Batch 10 MH A5 has not begun, no stage/commit/push occurred, and the protected automations remain paused and unchanged.

**Next Recommendation:** Wait for a separate user instruction before resuming MH A5; the user should not commit or push yet.

## Part 267 Current Gate — MH A5 Complete / Visual Review

- A5 responsive canon uses four columns through `1101px`, two columns from exact `1100px` through `601px`, and one column at `600px` and below. The connector strip follows four/two spans and hides in the single-column state.
- Non-Health-Promotion A5 groups use `14px 14px 16px` padding. The Health Promotion parent body and descendants use DM Sans `16px / 25.6px / 400`.
- A5 Blank completeness applies to the Health Promotion parent and all eight child answers. Every answer is hidden while nine `120px` writing surfaces remain.
- All six MH A5 cards passed `84/84` twice-stable Filled/Blank responsive states plus `12/12` nonempty print renders. Accepted `18px/14px` boundaries, top-stack roles, section rail, title/body typography, `14px` corners, Student Name, endpoint, controls, official structure, and zero overflow pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a5-canon-batch10`. MH A5 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** The user should visually review MH A5 and report approval or the first mismatch; the user should not commit or push yet.

## Part 268 Current Gate — MH A5 User Approved

- The user visually approved the Part 267 MH A5 comparison. The recorded six-card A5 responsive, typography, Blank-writing, connector, corner, endpoint, top-stack, and print contract is now accepted for MH A5.
- No product file changed while recording approval. Part 267's `84/84` responsive and `12/12` print evidence remains current.
- Content population is paused. ATI source support used: none; design-only change. The retrospective heartbeat and protected automations remain paused.

**Next Recommendation:** Wait for a separate user instruction before beginning AMS A5; the user should not commit or push yet.

## Part 269 Current Gate — Heartbeat Active / AMS A5 Next

- `ati-retrospective-template-spacing-heartbeat` is **ACTIVE** on its preserved 30-minute schedule. Part 268 is the recovery baseline and Batch 11 AMS A5 is the only active next family.
- AMS A5 must be evaluated against the user-approved cross-book A5 contract: four/two/one columns at exact `1101/1100` and `601/600px`; `18px/14px` spacing roles; `14px` connector strip; `14px 14px 16px` non-Health-Promotion padding; DM Sans `16px / 25.6px / 400` Health Promotion parent copy; nine `120px` Blank writing surfaces; accepted top stack, corners, endpoint, typography, and print behavior.
- Content population is paused. ATI source support used: none; design-only change. The three protected automations remain paused and unchanged. Automated QA is not user visual approval.

**Next Recommendation:** Let the heartbeat begin AMS A5 automatically; the user personally does not need to act, commit, or push.

## Part 270 Current Gate — AMS A5 Complete / MN A7 Next

- The accepted cross-book A5 contract is now confirmed in AMS: four columns through `1101px`, two columns from exact `1100px` through `601px`, and one column at `600px` and below; `18px` top boundaries; `14px` peer and parent/child gaps; `14px` connector strip; `14px 14px 16px` non-Health-Promotion padding; and accepted rail, corner, Student Name, and endpoint roles.
- Health Promotion parent content and descendants use DM Sans `16px / 25.6px / 400` with `14px 16px` padding. Blank completeness applies to the parent and all eight child answers: every answer is hidden while nine exact `120px` writing surfaces remain.
- The AMS A5 prototype passed `14/14` twice-stable Filled/Blank screen states across all seven required widths. Filled/Blank print produced `4` and `3` control-free pages; all seven page renders preserve official structure without clipping or answer leakage.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a5-canon-batch11`. AMS A5 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 12 MN A7 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Continue automatically with MN A7 Medication; the user personally does not need to do anything and must not commit or push now.

## Part 271 Current Gate — MN A7 Complete / MH A7 Next

- A7 Blank geometry is now explicit canon: every regular Purpose and direct writing surface remains exactly `120px`; Blank suppresses the Filled last-box `flex-grow` alignment behavior and aligns medication columns at their natural start. Filled equal-bottom alignment remains unchanged.
- The intentional Medication / Device card remains an approved structural exception and must not be converted into the regular two-Purpose/seven-direct layout.
- All 18 MN A7 cards passed `180/180` twice-stable Filled/Blank states at `1440`, `768`, exact `681/680`, and `390px`, plus `36/36` nonempty print PDFs. The established `18px/14px/10px` roles, centered Purpose rail, metadata, DM Serif/DM Sans typography, exact `681/680px` transition, behind-box Nursing Interventions-to-Client Education connector, approximately `64px` endpoint, hidden Blank answers, and zero overflow remain required.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a7-blank-geometry-batch12`. MN A7 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 13 MH A7 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat begin MH A7 Medication; the user personally does not need to do anything and must not commit or push now.

## Part 272 Current Gate — MH A7 Complete / AMS A7 Next

- The A7 Blank-writing canon now passes in MH as well as MN: regular Purpose and direct writing surfaces are exactly `120px`, Blank columns use natural-start alignment, and only Blank suppresses the Filled last-box equal-bottom growth rule.
- All 12 MH A7 cards passed `120/120` twice-stable Filled/Blank states at `1440`, `768`, exact `681/680`, and `390px`, plus `24/24` nonempty three-page print PDFs. The established `18px/14px/10px` spacing roles, approved centered Purpose rail, metadata, DM Serif Display/DM Sans typography, exact breakpoint, behind-box Nursing Interventions-to-Client Education connector, `24px + 40px` endpoint, hidden Blank answers, and zero overflow remain required.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a7-blank-geometry-batch13-4`. MH A7 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 14 AMS A7 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat begin AMS A7 Medication; the user personally does not need to do anything and must not commit or push now.

## Part 273 Current Gate — AMS A7 Complete / MN A9 Next

- The cross-book A7 Blank-writing canon now passes in AMS as well as MN/MH: all regular Purpose and direct writing surfaces are exactly 120px at every width, Blank columns use natural-start alignment, and only Blank suppresses Filled last-box equal-bottom growth.
- AMS A7 now also uses the accepted 16px Purpose outer, 11px nested, and 14px direct corners; 0px nested and 13px direct title-band top corners; and 6px list rhythm. The official two-Purpose/seven-direct structure, approved centered Purpose rail, and Filled learner content remain unchanged.
- All 16 AMS A7 records passed 160/160 twice-stable Filled/Blank states at 1440, exact 935/934, 768, and 390px, plus 32/32 nonempty print PDFs totaling 97 pages. Exact 18px/14px/10px roles, four metadata rows, Student Name, DM Serif Display/DM Sans typography, behind-box connector, approximately 64px endpoint, hidden Blank answers, and zero overflow remain required.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a7-canon-batch14. AMS A7 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 15 MN A9 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat begin MN A9 Nursing Skill; the user personally does not need to do anything and must not commit or push now.

## Part 274 Current Gate — MN A9 Complete / MH A9 Next

- A9 Nursing Skill uses two columns with the official horizontal Potential Complications-to-Nursing Interventions connector through exact `681px`; at `680px` and below it uses one column with the connector rotated vertically. A later tablet rule must never reopen two columns after that family transition.
- A9 spacing and hierarchy remain exact: `18px` metadata boundary, `14px` peer boxes, `10px` nested Considerations boxes, `14px` direct corners, `11px` nested corners, the user-approved centered Considerations rail, DM Serif Display `15px / 24px / 400` direct and `13.5px / 21.6px / 400` nested titles, and DM Sans `16px / 25.6px / 400` body descendants.
- In stacked Blank mode, all five direct boxes and both nested Considerations boxes remain exact `120px` writing surfaces with answers hidden. Wide compact nested Blank geometry remains intentional so the spanning Considerations group preserves the accepted equal-row contract.
- All 15 MN A9 cards passed `150/150` twice-stable post-repair Filled/Blank states at `1440`, `768`, exact `681/680`, and `390px`, plus `30/30` nonempty print PDFs. The behind-box connector, official order, `24px + 40px` endpoint, hidden Blank answers, typography, corners, and zero-overflow contract pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a9-canon-batch15`. MN A9 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 16 MH A9 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat begin MH A9 Nursing Skill; the user personally does not need to do anything and must not commit or push now.

## Part 275 Current Gate — MH A9 Complete / MN A11 Next

- The A9 stacked Blank-writing canon now passes in MH as well as MN: at `680px` and below, all five direct boxes and both nested Considerations boxes remain exact `120px` writing surfaces with answers hidden. Wide compact nested Blank geometry remains intentional.
- All six MH A9 cards passed `60/60` twice-stable post-repair Filled/Blank states at `1440`, `768`, exact `681/680`, and `390px`, plus `12/12` nonempty print PDFs. The accepted `18px/14px/10px` spacing roles, three metadata rows, official order, centered Considerations rail, DM Serif Display direct/nested title hierarchy, DM Sans body descendants, `14px/11px` corners, wide/stacked behind-box connector, `24px + 40px` endpoint, hidden Blank answers, and zero overflow remain required.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a9-canon-batch16`. MH A9 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. Batch 17 MN A11 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat begin MN A11 System Disorder; the user personally does not need to do anything and must not commit or push now.

## Part 276 Current Gate — MN A11 In Progress / Legacy Safety Normalization Next

- A11 System Disorder uses a three-column official top row at `901px` and above and a single-column stacked top row at exact `900px` and below. General tablet rules must not reopen the A11 row after this transition.
- All 65 MN A11 cards passed `260/260` twice-stable Filled/Blank states across exact `900px` and `768px` after the top-stack repair. The accepted `18px` metadata boundary, `14px` outer/top gaps, `10px` Assessment/Patient inner gaps, three stacked top boxes, two-column Assessment, one-column Patient-Centered Care, hidden Blank answers, `24px + 40px` endpoint, and zero overflow remain required.
- Safety wrapper normalization is not yet complete. `45` A11 cards use the canonical direct Safety structure; `20` legacy cards retain a direct `.tpl-group-label` plus `.tpl-group-body` wrapper that stretches both grid rows and bypasses the approved outer Safety rail/equal two-row relationship. The next run must normalize the visible relationship while preserving every learner node, official label, box, and relationship, then rerun the complete family at `1440`, exact `901/900`, `768`, `390px`, and print.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a11-in-progress-276`. Batch 17 remains in progress. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the next heartbeat resume MN A11 and normalize the 20 legacy Safety wrappers; the user personally does not need to do anything and must not commit or push now.

## Part 277 Current Gate — MN A11 Legacy Safety Repaired / Blank Safety Geometry Next

- The A11 Safety hierarchy now covers both source structures without replacing learner nodes. Canonical Safety keeps its direct normalized structure. Legacy Safety keeps its official outer label and two existing child boxes; the outer label renders as the approved centered section rail, the rail-to-body relationship is `10px`, and the body—not the rail—is the equal two-row relationship with a `14px` peer-box gap.
- Wide canonical Safety keeps two equal rows separated by `14px`. In the stacked A11 state, canonical Safety remains a nested relationship and therefore uses the accepted `10px` internal group gap. Legacy and canonical labels, boxes, order, and content remain unchanged.
- Blank writing geometry is an unresolved objective gate at `900px` and below. Every direct and nested A11 answer surface, including canonical Safety Considerations and Complications, must remain exactly `120px` with answers hidden. Current representative evidence is `.sd-safety-main` `31.594px` and Complications `42.594px`; this must be repaired before Batch 17 can objectively pass.
- The post-legacy-repair matrix passed all 65 cards in Filled and per-card Blank at `1440px` and `901px`, and all 65 cards in Filled at `900px`. Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a11-safety-in-progress-277`. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Resume MN A11 at exact `900px` Blank and restore both Safety writing surfaces to `120px`, then complete the remaining responsive and print matrix; the user personally does not need to act, commit, or push.

## Part 278 Current Gate — MN A11 Screen Canon Passed / Print Completion Next

- A11 stacked Blank Safety now follows the same writing-surface contract as every other direct or nested Blank role: canonical `.sd-safety-main`, direct Safety Complications, and both normalized legacy Safety children are exact `120px` at `900px` and below. Wide and Filled geometry are unchanged.
- All 65 A11 cards pass Filled and Blank at `1440`, exact `901/900`, `768`, and `390px`: `650/650` twice-stable states. Preserve the `45` canonical/`20` legacy structures, `18px/14px/10px` spacing, accepted rails/typography/corners, hidden answers, Student Name geometry, source/navigation stack, exact responsive columns, `24px + 40px` endpoint, and zero overflow.
- Print is not complete: `35/130` valid nonempty PDFs exist. Resume only the remaining outputs with `/private/tmp/run-mn-a11-print-b17-resume.zsh`, then validate all print, script, count, unique-ID, link, storage, payload, HTTP, and diff gates before objective completion.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a11-blank-safety-in-progress-278`. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Resume the MN A11 print audit without changing product geometry; the user personally does not need to act, commit, or push.

## Part 279 Current Gate — MN A11 Objectively Complete / MH A11 Next

- A11 print canon now explicitly removes both source-row study controls in `printing-modal`: the injected `.tpl-print-btn` and progress `.example-check` must not appear. The correction is scoped to MN System Disorder print and does not affect the screen stack or other families.
- All 65 MN A11 cards retain the complete Part 278 `650/650` twice-stable responsive screen pass, including exact `120px` canonical/legacy stacked Blank Safety roles, `18px/14px/10px` spacing, accepted typography/corners/rails, hidden answers, endpoint, and containment.
- All 130 Filled/Blank PDFs pass: `682` total pages, valid nonempty files, no Print/Mode/Previous/Next control text, and visually clean first/final Filled/Blank source rows and endpoints. Preserve this control-free print contract in every later A11 regression.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a11-canon-batch17`. MN A11 is objectively passed and pending fresh user visual approval; Batch 18 MH A11 is next. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Begin MH A11 on the next heartbeat and apply the same complete screen/print contract; the user personally does not need to act, commit, or push.

## Part 281 Current Gate — MN A11 User Visually Approved / MH A11 Next

- The user reviewed the final MN A11 comparison and explicitly approved it. Batch 17 MN A11 is now **OBJECTIVELY PASSED AND USER VISUALLY APPROVED** across all 65 cards.
- Preserve the complete approved A11 contract: exact `901/900px` top-row transition; canonical and normalized legacy Safety roles; `18px/14px/10px` spacing; accepted rails, typography, and corners; exact `120px` stacked Blank writing surfaces; hidden answers; `24px + 40px` endpoint; zero overflow; and control-free modal print.
- Part 279 evidence remains current: `650/650` responsive states and `130/130` PDFs totaling `682` pages. No product file changed while recording approval.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a11-canon-batch17`. Content population is paused. ATI source support used: none; design-only change. All automations remain paused; Batch 18 MH A11 has not begun.

**Next Recommendation:** Wait for the user's separate instruction before beginning MH A11; the user personally does not need to act, commit, or push.

## Part 282 Current Gate — MH A11 Complete / MN A13 Next

- MH A11 now conforms to the approved System Disorder contract across all 12 cards: exact `901/900px` wide-to-stack transition; `18px` metadata, `14px` major, and `10px` nested roles; `14px/11px` corner hierarchy; official centered Assessment, Safety Considerations, and Patient-Centered Care rails; hidden Blank answers; and the `24px + 40px` endpoint.
- At exact `900px` and below, the outer grid, three-box top row, and five-box Patient-Centered Care body are each single-column. All 14 official Blank roles are exact `120px` writing surfaces, including the Safety pair; Safety answer children are hidden. Exact `901px` and above retain the approved wide `2/3/3` relationship.
- All 12 cards passed `120/120` twice-stable Filled/Blank screen states at `1440`, exact `901/900`, `768`, and `390px`; `24/24` four-page print PDFs passed representative visual inspection with Blank answers and A11 study controls absent. Counts, unique source IDs, links, storage, exact payload parity, HTTP, and `git diff --check` pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a11-canon-batch18`. MH A11 is objectively passed and pending fresh user visual approval; automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change. All automations remain paused; Batch 19 MN A13 has not begun.

**Next Recommendation:** The user should visually review MH A11 and report approval or the first mismatch; the user should not commit or push yet.

## Part 283 Current Gate — MH A11 User Visually Approved / MN A13 Next

- The user reviewed the final MH A11 comparison and explicitly approved it. Batch 18 MH A11 is now **OBJECTIVELY PASSED AND USER VISUALLY APPROVED** across all 12 cards.
- Preserve the complete approved cross-book A11 contract: exact `901/900px` transition; official Assessment, Safety, and Patient-Centered Care roles; `18px/14px/10px` spacing; `14px/11px` corners; exact `120px` stacked Blank writing surfaces; hidden answers; uniform `24px + 40px` endpoint; zero overflow; and control-free modal print.
- Part 282 evidence remains current: `120/120` responsive states and `24/24` four-page PDFs. No product file changed while recording approval.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a11-canon-batch18`. Content population is paused. ATI source support used: none; design-only change. All automations remain paused; Batch 19 MN A13 has not begun.

**Next Recommendation:** Wait for the user's separate instruction before beginning Batch 19 MN A13; the user personally does not need to act, commit, or push.

## Part 284 Current Gate — MN A13 Complete / Fresh User Visual Review

- MN A13 now preserves the approved Therapeutic Procedure relationship at every responsive boundary. Exact card width `681px` is the horizontal two-column state; exact `680px` through `601px` is a full-width stacked state with the centered `3px x 34px` behind-box connector plus `3px x 14px` border-edge segment; exact `600px` and below remains the accepted phone stack.
- All 22 cards passed Filled/Blank at `1440`, `768`, exact `681/680`, exact `601/600`, and `390px`: `616/616` twice-stable measurements. Preserve official six-role order, two nested Considerations boxes, `18px/14px/10px` spacing, `14px/16px/11px` corners, role typography, hidden Blank answers, five exact `120px` direct Blank surfaces, accepted compact nested writing geometry, approximately `64px` endpoint, and zero overflow.
- Print passed `44/44` card/mode PDFs totaling `84` pages with Worked Example/source, official metadata, all roles, Blank reduction, no study controls, and no visible clipping. Counts, IDs, sidebar/source links, scripts, runtime errors, storage, exact product/temporary/HTTP parity, and diff whitespace pass at MN SHA-256 `db5e819f5f748f5f46164814df8e0ef5764ff48390a5d2f6139c202c2efe191b`.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mn-a13-canon-batch19-final`. MN A13 is objectively passed and pending fresh user visual approval. Content population is paused. ATI source support used: none; design-only change. All automations remain paused; Batch 20 MH A13 has not begun.

**Next Recommendation:** The user should visually review MN A13 and report approval or the first mismatch; the user should not commit or push yet.

## Part 285 Current Gate — MH A13 Blank Screen Repaired / Print Controls Next

- MH A13 Blank now uses the accepted five exact `120px` direct writing surfaces across all 10 cards. In the wide state, the Considerations parent derives to `254px` from two compact `93.203125px` nested roles and the exact `10px` internal relationships; stacked states retain compact nested writing roles. Filled geometry is unchanged.
- Twice-stable Filled/Blank screen validation passes at `1440`, exact MH `861/860` transition, `768`, exact `681/680`, exact `601/600`, and `390px`. Preserve the official order, hidden Blank answers, zero overflow, direct/nested role hierarchy, and accepted behind-box `34px x 3px` wide / `3px x 34px` stacked connector.
- Print remains incomplete as a canon gate even though `20/20` PDFs are valid and the repaired content geometry passes. A13 printing must hide the progress checkbox and Previous/Next modal navigation; those controls remain visible on page 2 under the current selector scope.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-blank-canon-batch20`. MH A13 is in progress and is not yet an objective pass. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Apply one A13 print-only control-hiding correction on the next run, regenerate all 20 PDFs, and finish Batch 20; the user should not commit or push yet.

## Part 286 Current Gate — MH A13 Blank Screen User Approved / Print Controls Still Open

- The user visually approved the repaired MH A13 Blank screen contract: five exact `120px` direct surfaces across all 10 cards, compact nested Considerations roles, hidden answers, accepted connector behavior, and responsive containment.
- Preserve this geometry. Batch 20 remains in progress solely because A13 print must still suppress the progress checkbox and Previous/Next modal navigation and then pass regenerated `20/20` PDFs plus final integrity.
- Current comparison remains `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-blank-canon-batch20`. Content population is paused. ATI source support used: none; design-only change. Automated QA is not user visual approval of the unfinished print surface.

**Next Recommendation:** Resume only the documented A13 print-control gate when the user instructs; the user should not commit or push yet.

## Part 287 Current Gate — MH A13 Nested Blank Repaired / Fresh Review Required

- Part 286 approval is withdrawn. Stacked A13 Blank nested official roles must never collapse to title strips: both `Nursing Interventions (pre, intra, post)` and `Client Education` require exact `120px` writing surfaces when the family is stacked. Modal print requires the same exact `120px` nested Blank surfaces. Wide on-screen compact nested geometry remains intentional.
- All 10 MH A13 cards now retain five exact `120px` direct and two exact `120px` stacked nested Blank surfaces, answers hidden, accepted connector layering, and zero overflow. Responsive checks pass `1440`, exact `861/860`, `768`, exact `681/680`, exact `601/600`, and `390px`.
- Regenerated print passes `20/20` valid nonempty three-page PDFs and visibly preserves both nested writing surfaces. Progress and Previous/Next study controls remain visible in A13 print and are the only objective Batch 20 gate.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-nested-blank-batch20-2`. MH A13 remains in progress and pending fresh user visual review. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** The user should review the corrected nested Blank comparison and report approval or the first mismatch; the user should not commit or push yet.

## Part 288 Current Gate — Automated Resume Contract

- The guarded retrospective heartbeat is **ACTIVE** every 30 minutes and resumes Batch 20 MH A13 from Part 287/288.
- Do not disturb the repaired five direct and two stacked nested exact `120px` Blank roles. Wide on-screen nested Blank roles remain intentionally compact. Complete the print-only study-control suppression, regenerate all 20 PDFs, and repeat the family integrity gate before advancing.
- Batches 21–24 remain ordered after Batch 20. A new book is not automatically required when that queue is empty; it may begin only if final objective evidence proves a canon-defined, design-only need with no educational-content or subjective decision.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-nested-blank-batch20-2`. Automated QA is not user visual approval. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the heartbeat resume Batch 20 at the print-control gate; the user personally does not need to do anything and must not commit or push now.

## Part 289 Current Gate — Automation Halted

- The guarded retrospective heartbeat is **PAUSED** by explicit user instruction. Its Part 287/288 recovery baseline and 30-minute schedule remain preserved.
- Batch 20 MH A13 remains in progress at the isolated print-control gate. Do not disturb the repaired direct or stacked nested Blank writing surfaces. Automated QA is not user visual approval.
- No new book began. Content population is paused. ATI source support used: none; design-only change. The three protected automations remain **PAUSED** and unchanged.

**Next Recommendation:** Wait for the user's separate instruction before resuming Batch 20; the user personally does not need to commit or push.

## Part 290 Canon Gate — Fresh Render-First Objective Equivalence

- Batch 20 MH A13 is **OBJECTIVELY PASSED**. Preserve five direct exact `120px` Blank roles, two stacked nested exact `120px` Blank roles, intentionally compact wide nested roles, the `18px/14px/10px` spacing system, `14px/11px` direct/nested corners, role typography, official connector/order, hidden answers, and endpoint. A13 print now retains the source row but omits progress, injected print, and Previous/Next controls.
- Completed evidence covers all 10 cards, both modes, `1440`, exact `861/860`, `768`, exact `681/680`, exact `601/600`, and `390px`: `180/180` twice-stable rendered states. Print is `20/20` freshly named three-page Letter PDFs (`60` pages), with every page rasterized and no controls, clipping, or overlap. Integrity remains `71` MH cards/unique IDs, exact family counts, 10 A13 cards, 71 resolving links, no duplicate static IDs, parsing script, unchanged storage, exact payload parity, HTTP `200`, and clean diff.
- **Required objective-pass evidence from Part 290 forward:** compare code/DOM roles and payloads; collect two identical computed-style and visible-boundary readings at least `250ms` apart for every card, Filled/Blank, and required width; inspect fresh screenshots; generate fresh versioned PDFs and rasterize representative/complete matrices as proportionate to risk; verify print text/control absence; then verify scripts, counts, IDs, links, storage, payload parity, HTTP, and `git diff --check`.
- **Freshness guard:** QA filenames, output directories, iframe cache keys, and URLs must be unique to the current run. A pre-existing output must never satisfy a current validation gate. This rule is mandatory because the Part 290 print audit detected and rejected a stale-PDF false pass.
- Routine objective passes may advance the queue without per-family user review. Never call an objective or automated pass user visual approval. Stop for the user on evidence disagreement, subjective/new canon choice, or the final representative cross-book handoff.
- Current comparison is `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-canon-batch20-final`. Batch 21 MN A15 is next. Content population is paused. ATI source support used: none; design-only change. All four automations remain paused.

**Next Recommendation:** Begin Batch 21 MN A15 under the fresh render-first objective gate; the user personally does not need to act, commit, or push.

## Part 291 Automation Gate — Fresh Render-First Queue Resumed

- The retrospective heartbeat is **ACTIVE** every 30 minutes and starts from Part 290 with Batch 21 MN A15. Each run is restricted to one book/family and may advance only after the complete fresh render-first evidence matrix passes; an unfinished family resumes on the next run.
- Preserve the Part 290 freshness guard: unique current-run QA paths/cache keys/URLs, two stable rendered readings at least `250ms` apart, fresh screenshots/raster evidence, and actual newly generated PDFs. Never accept a prior artifact as current proof. Automated QA is not user visual approval.
- Stop for conflicting evidence, a subjective or new-canon choice, missing evidence, or the final representative cross-book review. The current comparison remains `http://127.0.0.1:8766/elevated-ati-template-compare-mh-mn.html?v=mh-a13-canon-batch20-final`.
- The three protected automations remain **PAUSED** and byte-unchanged. Content population is paused. ATI source support used: none; design-only change. Nothing was staged, committed, or pushed.

**Next Recommendation:** Let the active heartbeat begin Batch 21 MN A15 under this checklist; the user personally does not need to act, commit, or push.

## Part 292 Checklist Gate — MN A15 Objective Pass

- Batch 21 **MN A15 Concept Analysis** is **OBJECTIVELY PASSED** with no product edit. Preserve the verified two-column-through-`721px` / one-column-at-`720px` breakpoint, `14px` peer corners, DM Serif Display `15px/24px/400` title role with `11px 16px` padding, DM Sans `16px/25.6px/400` body role with `14px 16px 16px` padding, and five exact `120px` Blank writing surfaces with all five answer bodies hidden.
- Required evidence passed all nine cards, both modes, and `1440`, `768`, exact `721/720`, and `390px`: `90/90` twice-stable rendered states, 36 fresh screenshots, 18 fresh PDFs/28 pages, and 28 fresh rasters. Endpoint, overflow, and Blank geometry pass; representative outputs are legible and unclipped.
- Integrity remains `197` MN cards/unique card IDs, `269` unique DOM IDs, nine A15 cards, nine resolving source links, four parseable scripts, unchanged storage keys, exact payload parity, HTTP `200`, and clean diff. Automated QA is not user visual approval.
- Current comparison is `http://127.0.0.1:8766/elevated-ati-template-compare-mn-a15-mh-b21-292.html?v=mn-a15-b21-292-compare-fresh`. Batch 22 **MH A15 Concept Analysis** is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the active heartbeat begin Batch 22 MH A15; the user personally does not need to act, commit, or push.

## Part 293 Current Gate — MH A15 Objective Pass / Control-Free Print Canon

- MH A15 follows the accepted Concept Analysis contract across all six cards: two columns through exact `721px`, one column at `720px` and below; `18px` metadata separation; `14px` peer gap and corners; DM Serif Display `15px/24px/400` titles with `11px 16px` padding; DM Sans `16px/25.6px/400` bodies with `14px 16px 16px` padding; and five exact `120px` hidden-answer Blank writing surfaces.
- Modal print must retain the Worked Example source row while suppressing A15 progress, injected print, mode, and Previous/Next navigation controls. Part 293 extends the established A11/A13 scoped control-free rule to Concept Analysis after twice-stable first/final evidence showed `.example-check` and `.template-modal-nav` visible in the pre-repair print surface.
- All six cards pass `60/60` twice-stable Filled/Blank screen states at `1440`, `768`, exact `721/720`, and `390px`. Fresh print passes `12/12` nonempty PDFs totaling 20 pages; all 20 pages were rasterized; representative first/final Blank and longest Filled renders retain official structure and writing geometry without study controls, clipping, or overlap.
- MH integrity passes `71` cards/unique IDs, exact counts `13/6/6/12/6/12/10/6`, `92` unique DOM IDs, six A15 IDs/progress keys, six resolving source links, one parsing script, unchanged storage, exact payload parity, HTTP `200`, and `git diff --check`. Current MH SHA-256 is `fb71575b0746719aa240a48f9d4e3742e525ecba7a1a65c245414a2067cbf2be`.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-mh-a15-mn-b22-293-post.html?v=mh-a15-b22-293-post-repair`. MH A15 is objectively passed; automated QA is not user visual approval. Batch 23 AMS A15 is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the active heartbeat begin Batch 23 AMS A15; the user personally does not need to act, commit, or push.

## Part 294 Checklist Gate — AMS A15 Objective Pass / Control-Free Print Canon

- AMS A15 follows the accepted Concept Analysis contract on its single source-neutral fixture: two columns through exact `721px`, one column at `720px` and below; `18px` metadata separation; `14px` peer gap and corners; DM Serif Display `15px/24px/400` titles with `11px 16px` padding; DM Sans `16px/25.6px/400` bodies with `14px 16px 16px` padding; exactly two official metadata rows; and five exact `120px` hidden-answer Blank writing surfaces.
- Modal print must retain the Worked Example/source row while suppressing A15 progress, injected print, mode, and Previous/Next navigation controls. Part 294 extends the established A11/A13/MH-A15 control-free rule to AMS A15 after fresh twice-stable evidence showed `.example-check` and `.template-modal-nav` visible before repair.
- Filled/Blank screen passes `10/10` twice-stable states at `1440`, `768`, exact `721/720`, and `390px`. Fresh print passes two nonempty PDFs totaling four pages; all four pages were rasterized and inspected; official roles, Blank writing geometry, and horizontal containment remain intact without study controls, clipping, or overlap.
- AMS integrity passes `84` cards/unique IDs, exact labeled counts `21/8/1/16/4/16/17/1`, `105` unique DOM IDs, one A15 fixture, five official titles in order, `76` resolving source links, one parsing product script, one parsing comparison script, unchanged storage, exact temporary/HTTP payload parity, HTTP `200`, and `git diff --check`. Current AMS SHA-256 is `8321c142e9d62e247d1e098b56702d8ed187492facfd4c451f56eaa4fb21f213`.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-a15-mn-b23-294.html?v=ams-a15-b23-294-post-2`. AMS A15 is objectively passed; automated QA is not user visual approval. Batch 24 final cross-book integrity handoff is next. Content population is paused. ATI source support used: none; design-only change.

**Next Recommendation:** Let the active heartbeat begin Batch 24 final cross-book integrity audit; the user personally does not need to act, commit, or push.

## Part 295 Checklist Gate — Final Cross-Book Canon Pass

- [x] Batches 0–24 objectively complete; user visual approval remains a separate state.
- [x] MN/MH/AMS representative A15 Filled/Blank render-first scan passed at `1440`, `768`, and `390px`, twice stable with zero overflow, hidden Blank answers, visible writing surfaces, and exact `64px` endpoint.
- [x] MN A15 print now suppresses progress, injected print, mode, and Previous/Next controls under the accepted A11/A13/MH/AMS print canon while retaining the Worked Example/source row.
- [x] Six fresh Letter PDFs (`MN 3/1`, `MH 2/1`, `AMS 3/1` Filled/Blank pages) and every raster pass control, clipping, overlap, structure, and Blank-writing checks.
- [x] Final integrity passes exact current family counts, unique IDs (`270/92/105`), resolving links (`197/71/76`), parseable scripts (`4/1/1`), unchanged storage, exact payload parity, HTTP `200`, and `git diff --check`.
- [x] Final hashes: MN `2aa966a6c94a5b59fb37a7d530a4fc6d23b5bda6aad94b4ece6aa7d73e7e10c9`; MH `fb71575b0746719aa240a48f9d4e3742e525ecba7a1a65c245414a2067cbf2be`; AMS `8321c142e9d62e247d1e098b56702d8ed187492facfd4c451f56eaa4fb21f213`.
- [ ] Final representative cross-book user visual approval remains pending at `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-final-cross-book-a15-b24-295.html?v=b24-295-final`.
- [x] Retrospective heartbeat paused at SHA-256 `644a0219a75eec685b801e8669f3da6d14bfd7bda7b7ffc543ea3b32407d0bc1`; protected automations paused and byte-unchanged; no stage/commit/push/new book.

**Next Recommendation:** The user should personally review the final cross-book comparison and report approval or the first mismatch; the user should not commit or push yet.

## Part 296 Checklist Gate — One Template Pair At A Time

- [x] Replace the three-column final-review page with a two-pane comparison.
- [x] Step 1 loads exact current MN A15 Tissue Perfusion and MH A15 Mental Health representative cards.
- [x] Global Filled/Blank controls synchronize both panes; fresh visual checks passed both modes; default restored to Filled.
- [ ] User approval or first mismatch for MN A15 Filled.
- [ ] MN A15 Blank review, only after the Filled step is resolved.
- [ ] Next template/pair, only after MN A15 is resolved.
- [x] No product or canon values changed; Batches 0–24 remain objectively complete; automations remain paused; no stage/commit/push.

Current comparison: `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-review-mn-a15-vs-mh-b24-296.html?v=b24-296-two-pane`.

**Next Recommendation:** The user should review only the MN A15 Filled comparison and report approval or the first mismatch; the user should not review another template yet.

## Part 297 Checklist Gate — MN A15 Filled Approved

- [x] MN A15 Filled user visually approved against MH.
- [x] Shared `64px` endpoint retained (`24px` trailing card guard + `40px` shell padding); confirmed cross-family, not A15-specific.
- [ ] MN A15 Blank user visual review.
- [ ] Next template family/pair, only after MN A15 Blank is resolved.
- [x] No product change; automations remain paused; no stage/commit/push.

**Next Recommendation:** The user should switch the current comparison to Blank and review only MN A15 Blank; no other template should be reviewed yet.

## Part 298 Checklist Gate — MN A15 Resolved / MH A15 Active

- [x] MN A15 Filled user visually approved.
- [x] MN A15 Blank user visually approved.
- [x] Shared `64px` endpoint retained.
- [x] MH A15 versus MN two-pane page loads exact payloads and synchronizes both modes.
- [ ] MH A15 Filled user visual review.
- [ ] MH A15 Blank, only after Filled is resolved.
- [x] No product change; automations paused; no stage/commit/push.

Current comparison: `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-review-mh-a15-vs-mn-b24-298.html?v=b24-298-two-pane`.

**Next Recommendation:** The user should review only MH A15 Filled and report approval or the first mismatch; no other mode or template should be reviewed yet.

## Part 299 Checklist Gate — MH A15 Filled Approved

- [x] MH A15 Filled user visually approved against MN.
- [ ] MH A15 Blank user visual review.
- [ ] Next template/pair, only after MH A15 Blank is resolved.
- [x] No product change; automations paused; no stage/commit/push.

**Next Recommendation:** The user should switch the current comparison to Blank and review only MH A15 Blank; no other template should be reviewed yet.

## Part 300 Checklist Gate — MH A15 Resolved / AMS A15 Active

- [x] MH A15 Filled user visually approved.
- [x] MH A15 Blank user visually approved.
- [x] AMS A15 versus MN two-pane page loads exact payloads and synchronizes both modes.
- [ ] AMS A15 Filled user visual review.
- [ ] AMS A15 Blank, only after Filled is resolved.
- [x] No product change; automations paused; no stage/commit/push.

Current comparison: `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-review-ams-a15-vs-mn-b24-300.html?v=b24-300-two-pane`.

**Next Recommendation:** The user should review only AMS A15 Filled and report approval or the first mismatch; no other mode should be reviewed yet.

## Part 301 Checklist Gate — AMS A15 Filled Approved

- [x] AMS A15 Filled user visually approved against MN.
- [ ] AMS A15 Blank user visual review.
- [ ] Final representative visual-review completion, only after Blank is resolved.
- [x] No product change; automations paused; no stage/commit/push.

**Next Recommendation:** The user should switch the current comparison to Blank and review only AMS A15 Blank; no other action should be taken yet.

## Part 302 Checklist Gate — Final Representative Review Approved

- [x] MN A15 Filled and Blank user visually approved.
- [x] MH A15 Filled and Blank user visually approved.
- [x] AMS A15 Filled and Blank user visually approved.
- [x] Shared `64px` endpoint retained.
- [x] Final representative cross-book visual handoff complete without retroactively relabeling other automated passes.
- [x] All 25 objective batches complete; no additional book objectively necessary.
- [x] Retrospective and protected automations paused; no stage/commit/push.

**Next Recommendation:** Perform a read-only final diff/status review, then wait for separate user authorization before any commit or push; the user does not need to inspect another template.

## Part 352 Current Gate — Natural Modal Title-Row Shared Canon

- [x] User explicitly rejected the fixed two-line title reservation after reviewing MN A1 `Fourth Stage of Labor Care` at the exact `557px` split pane.
- [x] MN, MH, and AMS no longer define or apply regular/mobile modal title-row minimum heights.
- [x] One-line MN and PD A1 title banners both measure `87.390625px` at the reported split width in Filled and Blank.
- [x] Longer MN titles expand naturally; `Skin and Breast Changes During Pregnancy` increases from a one-line `56.390625px` row to an `87.1875px` two-line row without shrinking, clamping, hiding, or a maximum.
- [x] MH and AMS representative one-line rows compute natural/auto minimums and load without browser script errors.
- [x] Product/temporary parity, focused diffs, HTTP, and `git diff --check` pass; automations remain paused; nothing staged, committed, pushed, or populated.
- [x] User visually approved the corrected PD A1 versus MN A1 title banner in Part 353.

Current comparison: `http://127.0.0.1:8766/pd-a1-user-review-352/pd-a1-vs-mn-review-352.html?v=pd-a1-review-352-fixed`.

**Next Recommendation:** The user should review the corrected one-line MN A1 banner and report approval or the first remaining mismatch; do not advance the family queue or commit/push first.

## Part 353 Current Gate — Full MN/MH/AMS Natural Title-Row Audit

- [x] MN: all 197 cards across A1/A3/A5/A7/A9/A11/A13/A15 passed Filled and Blank at `1440px`, `768px`, and `390px`.
- [x] MH: all 71 cards across all eight families passed the same responsive Filled/Blank matrix.
- [x] AMS: all 84 cards, including all eight prototype fixtures, passed the same responsive Filled/Blank matrix.
- [x] The combined audit covers 2,112 responsive states and 4,224 twice-stable measurements. Every title row computes natural/zero minimum height and `max-height:none`; every title/actions stack remains contained, collision-free, and free of artificial row excess.
- [x] One-line desktop titles collapse to the actual `62.9922px` shared row where applicable. Split-pane and phone titles expand only when wrapping requires it, up to `166.375px`, with no clamp, shrink, hiding, or fixed reservation.
- [x] The corrected PD A1 versus MN A1 comparison is explicitly user-approved. Review advances exactly one family to PD A3 versus MN A3.
- [ ] Fresh user visual approval of PD A3 versus MN A3.

Current comparison: `http://127.0.0.1:8766/pd-a3-user-review-353/pd-a3-vs-mn-review-353.html?v=pd-a3-review-353`.

**Next Recommendation:** The user should review PD A3 against the finalized MN A3 reference and report approval or the first visible mismatch; do not advance the family queue or commit/push first.

## Part 354 Current Gate — PD A3 Approved / PD A5 Active

- [x] PD A3 Diagnostic Procedure versus finalized MN A3 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A5 Growth and Development versus finalized MN A5.
- [x] Fresh A5 comparison uses exactly two panes: MN `Newborn Physical Development` fixed left and PD `Toddler (1–3 years)` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Expected Growth and Development / Health Promotion / Immunizations alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A5 versus MN A5.

Current comparison: `http://127.0.0.1:8766/pd-a5-user-review-354/pd-a5-vs-mn-review-354.html?v=pd-a5-review-354`.

**Next Recommendation:** The user should review PD A5 against the finalized MN A5 reference and report approval or the first visible mismatch; do not advance to PD A7, commit, push, or start content population first.

## Part 355 Current Gate — PD A5 Approved / PD A7 Active

- [x] PD A5 Growth and Development versus finalized MN A5 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A7 Medication versus finalized MN A7.
- [x] Fresh A7 comparison uses exactly two panes: MN `Methotrexate (Trexall)` fixed left and PD `Digoxin (Lanoxin)` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Purpose of Medication / Medication Administration / Nursing Interventions alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A7 versus MN A7.

Current comparison: `http://127.0.0.1:8766/pd-a7-user-review-355/pd-a7-vs-mn-review-355.html?v=pd-a7-review-355`.

**Next Recommendation:** The user should review PD A7 against the finalized MN A7 reference and report approval or the first visible mismatch; do not advance to PD A9, commit, push, or start content population first.

## Part 356 Current Gate — PD A7 Approved / PD A9 Active

- [x] PD A7 Medication versus finalized MN A7 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A9 Nursing Skill versus finalized MN A9.
- [x] Fresh A9 comparison uses exactly two panes: MN `Fundal Massage` fixed left and PD `Seizure Precautions` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Description of Skill / Considerations / Nursing Interventions alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A9 versus MN A9.

Current comparison: `http://127.0.0.1:8766/pd-a9-user-review-356/pd-a9-vs-mn-review-356.html?v=pd-a9-review-356`.

**Next Recommendation:** The user should review PD A9 against the finalized MN A9 reference and report approval or the first visible mismatch; do not advance to PD A11, commit, push, or start content population first.

## Part 357 Current Gate — PD A9 Approved / PD A11 Active

- [x] PD A9 Nursing Skill versus finalized MN A9 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A11 System Disorder versus finalized MN A11.
- [x] Fresh A11 comparison uses exactly two panes: MN `Placenta Previa` fixed left and PD `Sickle Cell Anemia` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Alterations in Health / Assessment / Patient-Centered Care alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A11 versus MN A11.

Current comparison: `http://127.0.0.1:8766/pd-a11-user-review-357/pd-a11-vs-mn-review-357.html?v=pd-a11-review-357`.

**Next Recommendation:** The user should review PD A11 against the finalized MN A11 reference and report approval or the first visible mismatch; do not advance to PD A13, commit, push, or start content population first.

## Part 358 Current Gate — PD A11 Approved / PD A13 Active

- [x] PD A11 System Disorder versus finalized MN A11 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A13 Therapeutic Procedure versus finalized MN A13.
- [x] Fresh A13 comparison uses exactly two panes: MN `Leopold Maneuvers` fixed left and PD `Phototherapy for Neonatal Hyperbilirubinemia` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Description of Procedure / Considerations / Nursing Interventions alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping, including the long PD phone title.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A13 versus MN A13.

Current comparison: `http://127.0.0.1:8766/pd-a13-user-review-358/pd-a13-vs-mn-review-358.html?v=pd-a13-review-358`.

**Next Recommendation:** The user should review PD A13 against the finalized MN A13 reference and report approval or the first visible mismatch; do not advance to PD A15, commit, push, or start content population first.

## Part 359 Current Gate — PD A13 Approved / PD A15 Active

- [x] PD A13 Therapeutic Procedure versus finalized MN A13 is explicitly user-approved.
- [x] The next review advances exactly one family to PD A15 Concept Analysis versus finalized MN A15.
- [x] Fresh A15 comparison uses exactly two panes: MN `Maternal-Newborn Attachment` fixed left and PD `Respiratory Distress` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Defining Characteristics / Antecedents / Related Concepts alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural `min-height:0px`, containment, and collision-free wrapping.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of PD A15 versus MN A15.

Current comparison: `http://127.0.0.1:8766/pd-a15-user-review-359/pd-a15-vs-mn-review-359.html?v=pd-a15-review-359`.

**Next Recommendation:** The user should review PD A15 against the finalized MN A15 reference and report approval or the first visible mismatch; do not advance to Pharm A1, commit, push, or start content population first.

## Part 360 Current Gate — PD A15 Approved / Pharm A1 Active

- [x] PD A15 Concept Analysis versus finalized MN A15 is explicitly user-approved; all seven Pediatric family reviews are approved.
- [x] The next review advances exactly one family to Pharm A1 Basic Concept versus finalized MN A1.
- [x] Fresh Pharm A1 comparison uses exactly two panes: MN `Fourth Stage of Labor Care` fixed left and Pharm `Principles of Antimicrobial Therapy` fixed right.
- [x] No pair selector; ten retained controls; options collapsed by default; Filled/Blank, Related Content / Underlying Principles / Nursing Interventions alignment, Sync Once/Scroll, Guides, and linked Vertical Guides pass.
- [x] Exact `720px / 720px` desktop panes and responsive `768px` / `390px` one-column layouts have zero horizontal overflow. Responsive measurements are twice-stable; both title rows retain natural expansion, containment, and collision-free wrapping, including the long Pharm phone title.
- [x] Exact payload parity, HTTP `200`, wrapper integrity, clean Filled/top/options-collapsed handoff, paused automations, and no stage/commit/push pass.
- [ ] Fresh user visual approval of Pharm A1 versus MN A1.

Current comparison: `http://127.0.0.1:8766/pharm-a1-user-review-360/pharm-a1-vs-mn-review-360.html?v=pharm-a1-review-360`.

**Next Recommendation:** The user should review Pharm A1 against the finalized MN A1 reference and report approval or the first visible mismatch; do not advance to Pharm A3, commit, push, or start content population first.
