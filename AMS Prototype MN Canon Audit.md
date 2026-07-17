# AMS Prototype MN Canon Audit

Status: Design-canon / HOLD-CONTENT audit only.
Date: 2026-07-04.
Scope: Current AMS prototype compared against the MN design canon. This document does not add ATI educational content and does not approve rollout to MN or other books.

Continuity notice (2026-07-15): this file preserves AMS audit evidence and batch history; it is not the current task selector or an independent source of required canon. Private master Build Guide Part 49 consolidates the accepted current conclusions from this audit and is the complete migration reference. Heartbeat continuation has resumed from the current MH queue under Part 49; all older AMS-only heartbeat recommendations in this audit are historical. Update this file only when AMS comparison evidence, audit status, or rollout readiness changes.

Clipping-readiness update (2026-07-17): all 24 MN, MH, and AMS template-family items plus the MN, MH, and AMS landing shell/sidebar/modal chrome items have completed objective clipping QA. The AMS shell passed eight repeated desktop, split-pane/tablet, and phone states with no product repair: page and modal horizontal overflow stayed at `0px`, all eight collapsed headers and their visible children stayed contained, both opened responsive sidebars measured `280px` with `0px` horizontal row/control overflow, and the representative Basic Concept modal's title, labels, buttons, navigation, and borders stayed inside their containers. Tablet and phone modal-body vertical scrolling was intentional; the existing phone example-name line clamps behind the open modal were excluded by the clipping gate. Final cross-book integrity also passed with unchanged MN/MH/AMS payload hashes, parseable scripts, 352 cards and 352 unique IDs, canonical family order/counts, exact standalone/comparison parity, required breakpoints/landmarks, and complete responsive summaries. The clipping automation is paused, and user visual approval remains pending. This audit remains supporting evidence; private master Part 98 and the current overlay select the waiting state.

## Files Reviewed

- `MN Design Canon Checklist.md`
- `Elevated ATI AMS Hub.html`
- `Elevated ATI AMS Book.html`
- `Elevated ATI AMS Templates.html`
- `Elevated ATI AMS Flashcards.html`

## High-Level Finding

AMS now has a strong hub and book foundation, but it is not yet fully MN-canon as a complete study system. The book file carries most of the modern interaction work: modal chapters, tabs, TL;DR sections, Related ATI Template bridges, chapter-to-chapter modal navigation, bookmarks, highlights, search, NCLEX done state, print modes, and source-linked practice surfaces.

The weakest areas are the companion tools. `Elevated ATI AMS Templates.html` and `Elevated ATI AMS Flashcards.html` are useful starter pages, but they are still flatter than MN's template and flashcard systems. They do not yet match MN's deeper template geometry, modal worked-example behavior, review/browse flashcard workflow, session metrics, keyboard support, and durable progress loop.

## Evidence Snapshot

- AMS Hub: 1,023 lines; includes 96 chapters, 14 units, 76 worked templates, pickup panel, review queue, unit progress, template type overview, storage tools, and shared local storage keys.
- AMS Book: 33,867 lines; includes 96 chapters, 96 TL;DR cards, 404 content sections, 540 condition blocks, 1,724 finding cards, 52 knowledge cards, 1,317 exercises, 4 ALS cards, 96 template bridges, modal chapter navigation, bookmarks, highlights, NCLEX done state, print modes, and flashcard scheduling hooks.
- AMS Templates: 1,090 lines; includes 76 worked template cards, search, type filters, chapter filters, and source links back to AMS Book anchors.
- AMS Flashcards: 2,243 lines; includes 208 starter cards, search, unit/chapter/type filters, reveal buttons, and source links back to AMS Book anchors.

## Canon Checklist

| MN canon item | AMS status | File evidence | Critical note |
| --- | --- | --- | --- |
| Connected study system | Partial | Hub links Book/Templates/Flashcards; Book links Templates and Flashcards; Templates/Flashcards link back to Book | The loop exists structurally, but Templates and Flashcards are not yet MN-depth tools. |
| Hub as dashboard | Done | AMS Hub has stats, primary tools, unit map, pickup panel, review queue, template overview, and storage tools | This is the strongest current match to MN's hub pattern. |
| Book chapters as modal study workspaces | Done | `chapterModal`, modal header, modal tabs, modal body, flashcard button, previous/next chapter buttons | The AMS book has the expected modal workspace behavior. |
| TL;DR-first chapter structure | Done | 96 `.brief-card` sections | Each chapter has a TL;DR entry point. |
| Tabs as navigational compression | Done | `buildTabLabel()` maps TL;DR, Templates, Practice, and section headings into modal tabs | Tabs are generated from chapter sections rather than being decorative. |
| Dense content hierarchy | Partial | 540 `.condition-block`, 1,724 `.finding-card`, 52 `.kb-card` | Structure exists, but user-observed small-box arrangement still needs visual QA and cleanup. |
| Template visual geometry | Partial | AMS Templates now uses the MN-like sidebar plus 8 accordion template-type navigator, 76 compact example rows, hidden card content, modal worked examples, Filled/Blank mode, progress buttons, progress bars, and status filtering | Major hub/navigation mismatch is corrected; full MN connector-map geometry inside each template example is still not copied. |
| Book-to-template links | Done | 96 `tpl-bridge` sections in AMS Book; links target AMS Templates anchors | The bridge pattern is broadly implemented. |
| Template-to-book links | Done | Template cards use `template-link` back to AMS Book anchors | Source-jump behavior exists. |
| Book-to-flashcard links | Partial | Modal flashcard button routes to AMS Flashcards by chapter; mid-prompt cards save into `atiams_fc_schedule` | The book side is strong; the standalone flashcard page does not yet fully consume the review-loop design. |
| Flashcards as first-class companion tool | Partial | 208 starter cards, filters, reveal actions, source links | Missing MN-level review/browse tabs, due review workflow, session metrics, keyboard shortcuts, and mature SM-2 page behavior. |
| Local progress state across suite | Partial | Hub and Book use book progress, template progress, flashcard schedule, last chapter/template, bookmarks, NCLEX done, highlights; AMS Templates now stores template reviewed/checked progress and last template | Flashcards still uses a lighter standalone review state than MN. |
| Learner memory tools | Partial | Book has bookmarks, pill bookmarks, highlights, notes/tombstones, search highlights, and print modes | Suite-wide memory is not equally deep in Templates/Flashcards. |
| Prompt canon caution | Not done | AMS Book contains both `.mid-prompt` and `.mid-read` systems | This needs deliberate cleanup before rollout so old and new prompt generations are not mixed accidentally. |
| Latest Batch 2 practice design | Partial | AMS Book has styled exercises and Practice tabs | Must be visually checked against the user's latest Batch 2 page 15 item 16 direction before calling this complete. |
| ALS design | Partial | 4 `.als-card` instances and ALS-specific styles | ALS exists but is sparse and not yet enough evidence for an all-chapter canon. |
| Common button label consistency | Partial | AMS has consistent core labels in many places, but Templates/Flashcards use simpler standalone labels | Needs a label audit before rollout. |

## Completed Items

- Hub dashboard structure is substantially complete for AMS.
- Book modal structure is substantially complete for AMS.
- TL;DR-first chapter opening pattern is complete across 96 chapters.
- Chapter modal previous/next navigation is implemented.
- Related ATI Template bridges are present across all 96 chapters.
- Book-to-template and template-to-book source links are present.
- Book-side bookmarks, highlights, print, search, NCLEX done, and progress state are present.
- AMS Book has enough condition/finding/card hierarchy to support MN-style dense content, pending visual refinement.

## Partial Or Risk Items

- Small-box arrangement still needs a visual pass because the existence of `.condition-block` and `.finding-card` does not prove the boxes are grouped cleanly on screen.
- Practice/Application Exercises cannot be marked done until checked against the final Batch 2 page 15 item 16 design.
- ALS design exists but is too sparse to treat as a finished canon pattern.
- Prompt/review design is mixed: `.mid-prompt` and `.mid-read` both remain in AMS Book.
- Local progress is strong in Hub/Book, lighter in Templates/Flashcards.

## Not Done Items

- AMS Templates still needs full MN connector-map geometry if the prototype review confirms that pattern should be copied.
- AMS Flashcards does not yet match MN's first-class review engine.
- AMS Flashcards does not yet provide MN-style review/browse tabs, due queue workflow, session metrics, keyboard support, or mature SM-2 review UI.

## Recommended Next Action

Continue AMS prototype work only. Do not touch MN and do not roll out to other books yet.

Next focused batch:

1. Visually QA AMS Book small-box arrangement and Practice tab design against the Batch 2 comments.
2. Resolve the prompt generation split by choosing one AMS practice/review visual system.
3. Review the AMS Templates prototype and decide whether the remaining MN connector-map geometry should be copied exactly or adapted.
4. Upgrade AMS Flashcards toward MN's review-loop shell without adding new cards.
5. Re-run this audit and mark each row Done, Partial, or Not done again based on file evidence and visual QA.

## Batch Update: 2026-07-04 AMS Book Visual Normalization

Completed in AMS Book only:

- Tightened `.finding-grid.wide-box-grid` so dense small-box groups use more compact columns in modal content.
- Normalized both early and late Practice/Application Exercise markup into one connected quiz-bank shell.
- Fixed direct-hash Practice loading so NCLEX filter and Mark done controls inject reliably.
- Extended Mark done support to later exercise markup that uses heading labels instead of `.q-num`.
- Visually normalized older `.mid-read` prompt styling to match the newer typed prompt system more closely.

Validation:

- Checked chapter 92 dense content at `#ch92-prostate-testicular`: small boxes now render as three compact columns at the desktop modal width tested.
- Checked chapter 92 Practice at `#ch92-exercises`: six Mark done controls inject and the question/option well renders as a connected shell.
- Checked chapter 21 Practice at `#ch21-exercises`: five Mark done controls inject in the earlier exercise markup.
- Browser console reported no errors or warnings during this pass.
- `git diff --check` passed.

Still not done:

- AMS Templates still needs review for whether the remaining MN connector-map geometry should be copied exactly.
- AMS Flashcards still needs the MN review-loop shell upgrade.
- The prompt split is visually softened, but the underlying old/new prompt code paths still need a later structural cleanup before rollout.

## Batch Update: 2026-07-04 AMS Templates MN Shell Prototype

Completed in AMS Templates only:

- Added a MN-style template operating layer around the existing 76 AMS template cards.
- Grouped cards into 6 template-type containers with group-level progress bars and counts.
- Added Filled/Blank mode controls that preserve template structure while hiding answer text in Blank mode.
- Added a modal study view for worked examples, using the existing card content without adding educational material.
- Added reviewed/checked progress buttons, progress persistence, status filtering, visible result counts, and reset progress.
- Preserved existing template-to-book links and recorded the last opened template for hub continuity.

Validation:

- `git diff --check` passed.
- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- Headless Chrome validation passed against `Elevated ATI AMS Templates.html`.
- Browser evidence: 6 generated type groups, 76 template cards, 76 action controls, 76 visible cards on first load, Blank mode active state works, modal opens with the selected template, reviewed progress saves and filters to 1 of 76, and console logs reported no errors.
- Screenshot reviewed at `/private/tmp/ams-templates-prototype.png`; the modal, Blank mode, and progress state rendered coherently at desktop width.

Still not done:

- AMS Templates has not copied MN's full connector-map geometry.
- AMS Flashcards still needs the MN review-loop shell upgrade.
- AMS Book prompt code paths still need later structural cleanup before rollout.

## Corrective Batch Update: 2026-07-04 AMS Templates MN Hub Match

Reason for correction:

- User correctly identified that the first AMS Templates prototype still did not match the MN template design. The earlier pass copied the feature layer but left the page reading like a grouped card grid, while MN Templates is fundamentally a sidebar plus accordion row navigator with modalized examples.

Completed in AMS Templates only:

- Added a fixed MN-style left sidebar with back link, course/title block, suite progress strip, legend, and template-type navigation.
- Reframed the main page away from the AMS card-grid/stats presentation and toward MN's plain study-page header plus template accordion flow.
- Converted the visible template hub into 8 ATI template-type accordions, including placeholders for the 2 currently unpopulated template types.
- Changed the visible worked-example surface from full cards to compact MN-style rows: bullet, example name, and reviewed/checked status icon.
- Kept all 76 existing AMS worked-template cards hidden in the accordion bodies and opened them through the modal, matching MN's page-to-modal interaction model more closely.
- Synced sidebar active state, reviewed/checked row icons, group progress bars, and suite progress summary.

Validation:

- `git diff --check` passed.
- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- Desktop headless Chrome validation passed: 8 generated accordions, all 8 collapsed initially, 76 compact example rows, 76 hidden cards, 2 placeholders, sidebar present, stats strip hidden, medication accordion opens from sidebar, row opens modal, progress icon updates, and console logs reported no errors.
- Desktop page screenshot reviewed at `/private/tmp/ams-templates-mn-page.png`; visible page now shows the sidebar plus accordion row navigator instead of a card grid.
- Modal screenshot reviewed at `/private/tmp/ams-templates-mn-correction.png`; modal continues to render the worked example cleanly.
- Mobile headless Chrome validation passed: sidebar hidden, main margin reset to 0, 8 accordions, 76 rows, modal width fits at 390 px, no horizontal overflow, and no console errors.

Still not done:

- The internal worked-example content still uses AMS card/section geometry rather than MN's full ATI template connector-map layouts.
- AMS Flashcards still needs the MN review-loop shell upgrade.
- AMS Book prompt code paths still need later structural cleanup before rollout.

## Corrective Batch Update: 2026-07-04 AMS Templates Filter And Modal Header Cleanup

Reason for correction:

- User noted that the type filter duplicated the accordion structure, the chapter filter added clutter, the page-level Filled/Blank buttons were not useful, and the individual template modal needed to follow the MN worked-example upper design more closely.

Completed in AMS Templates only:

- Removed the visible type filter from the template hub.
- Removed the visible chapter filter from the template hub.
- Kept the search box as the primary cross-template lookup tool.
- Removed the page-level Filled/Blank controls.
- Updated the build notice so it no longer references chapter filters.
- Reworked the modal upper area toward MN's individual template design: template identity line above the large title, worked-example label, repeated worked-example title, chapter/source line with Open chapter link, and a progress check control in the worked-example header.
- Hid the duplicate bottom action strip inside the modal so the upper header becomes the main control surface.

Validation:

- `git diff --check` passed.
- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- Desktop headless Chrome validation passed: search box present, visible type filters 0, visible chapter filters 0, visible Filled/Blank controls 0, search for "asthma" filtered to 3 of 76 rows across 2 groups, modal opened, modal header order matched the MN pattern, bottom actions were hidden, and console logs reported no errors.
- Screenshot reviewed at `/private/tmp/ams-templates-modal-upper-v2.png`; modal top now places ATI template identity above the title and the worked-example header below it.

## Corrective Batch Update: 2026-07-04 AMS Templates MN Individual Template Redo

Reason for correction:

- User noted the page still did not follow the MN individual template design and that the chapter filter still appeared under search. The prior change hid controls but did not fully remove the chapter filter markup, and the modal still lacked MN's meta panel plus structured template boxes.

Completed in AMS Templates only:

- Removed the chapter filter row from the HTML completely.
- Confirmed the type filter row is also absent from the HTML.
- Removed the obsolete Filled/Blank event hookup and left no Filled/Blank controls in AMS Templates.
- Added a global `[hidden]` safety rule so hidden UI cannot be accidentally re-shown by `.chips` display styling.
- Rebuilt the modal body to better match MN's individual template design: ATI identity line, title, worked-example header, progress check, source/Open chapter row, meta panel with Student Name / Concept / Review Module Chapter, and three structured content boxes.
- Converted the modal content boxes from simple stacked AMS sections into MN-like boxed columns with header bands and larger learner-facing text.

Validation:

- `git diff --check` passed.
- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- Source check confirmed 0 `data-filter="type"`, 0 `data-filter="chapter"`, and 0 `data-template-mode` controls remain in AMS Templates.
- Desktop headless Chrome validation passed: search remains present, search for "asthma" filters to 3 of 76 rows across 2 groups, modal opens, 3-row meta panel renders, 3 structured content boxes render in columns, bottom action strip is hidden, and console logs reported no errors.
- Screenshot reviewed at `/private/tmp/ams-templates-mn-redo-modal.png`; modal now visually follows MN's individual template structure more closely.
- Mobile headless Chrome validation passed: modal width fits at 342 px, meta panel and content boxes collapse to one column, no horizontal overflow, and no console errors.

## Canonization Update: 2026-07-04 AMS Templates A1 Basic Concept

Reason for canonization:

- User reviewed the AMS A1 Basic Concept prototype and approved the design direction as acceptable for this design-canon phase.
- Content enrichment is intentionally deferred. The A1 shell is canonized for layout and workflow only, not for MN-level content density.

Canonized A1 pattern:

- Use the MN-style individual template modal shell: ATI identity line, large title, worked-example header, source/Open chapter row, progress checkbox, print, Filled/Blank toggle, and compact modal controls.
- Use the official ATI A1 Basic Concept body structure: one meta strip followed by exactly three aligned columns: Related Content, Underlying Principles, and Nursing Interventions.
- Use AMS accent colors for AMS templates. Do not copy MN orange accent into AMS.
- Keep A1 boxes equal-width and aligned on desktop, collapsing to one column on small screens.
- Keep Previous/Next navigation available in the modal, scoped to the current ATI template type so A1 examples move only among A1 examples.

Implementation evidence:

- `Elevated ATI AMS Templates.html` includes explicit A1 canon selectors on `data-template-type="basic-concept"`.
- `modalNavState(id, type)` scopes previous/next movement to the active ATI template type.
- Prototype-only A5/A15 fixtures remain separate and do not affect normal template count.

Validation:

- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- `git diff --check` passed for AMS Templates.
- Browser validation passed on AMS A1: modal opened, A1 rendered as three equal columns, AMS green accent appeared on title/toggle/bullets, normal template count remained 76, Previous was disabled on the first A1, and Next opened the next A1.

Still deferred:

- MN-level content enrichment for A1 is not part of DESIGN-CANON / HOLD-CONTENT mode.
- A3 Diagnostic Procedure has started as the next template-type canon pass and should be reviewed before being called canonized.
- Other template types should not inherit A1's three-column body; each should be matched against its own official ATI template geometry.

## Prototype Update: 2026-07-04 AMS Templates A3 Diagnostic Procedure

Reason for prototype:

- User provided the official A3 Diagnostic Procedure template and MN A3 screenshot as the next design reference.
- A3 must not inherit the A1 three-column body. Its layout needs to follow the official ATI A3 geometry while staying inside the MN-style modal shell and AMS accent system.

Prototype A3 pattern:

- Use the same individual template modal shell accepted during the A1 pass.
- Use the official A3 Diagnostic Procedure body structure: full-width Description of Procedure, left-column Indications / Interpretation of Findings / Potential Complications, right-side Considerations group with Nursing Interventions (pre, intra, post) and Client Education, then lower-right Nursing Interventions.
- Keep the connector from Potential Complications to Nursing Interventions.
- Preserve the official A3 boxes even when a current AMS card has an unpopulated slot, because content enrichment is paused and the design shell still needs to be testable.
- Use AMS accent colors for AMS templates. Do not copy MN orange accent into AMS.
- Keep Previous/Next navigation scoped to Diagnostic Procedure examples.

Implementation evidence:

- `Elevated ATI AMS Templates.html` includes explicit A3 selectors on `data-template-type="diagnostic-procedure"`.
- A3 now labels the second left-column box as `Interpretation of Findings`, matching the official ATI A3 template.
- The A3 layout uses tighter diagnostic-procedure-specific spacing and box sizing instead of the A1 three-column canon.
- Diagnostic Procedure no longer collapses empty official A3 boxes in Filled mode, so sparse current AMS examples do not distort the template geometry.
- Adjacent A3 boxes now preserve the official larger Considerations container while aligning its internal rows to MN's pattern: the Considerations label plus Nursing Interventions (pre, intra, post) aligns with Indications, Client Education aligns with Interpretation of Findings, and the lower Potential Complications / Nursing Interventions pair remains aligned.
- A3 now uses the shared A3/A9 lower-box connector rule so Potential Complications visibly connects to Nursing Interventions without being clipped by the card border.

Validation:

- Official A3 PDF was rendered and visually checked against the AMS/MN pattern.
- MN A3 screenshot was used as the modal-layout comparison reference.
- Full browser validation is still pending for this A3-specific pass.

## Prototype Update: 2026-07-04 AMS Templates A5 Growth and Development

Reason for prototype:

- User moved the canon pass to A5 Growth and Development, but AMS does not currently have source-verified learner-facing A5 examples.
- The official A5 template PDF is available locally and was used for layout verification.
- In DESIGN-CANON / HOLD-CONTENT mode, A5 should be tested as a prototype fixture only until AMS-specific content support is approved.

Prototype A5 pattern:

- Use the same individual template modal shell accepted during the A1/A3 passes.
- Use the official A5 Growth and Development body structure: four aligned Expected Growth and Development boxes, then a full-width Health Promotion parent box with four aligned child boxes beneath it.
- Preserve the connector strip between Health Promotion and the four child boxes.
- Keep boxes in the same official row aligned at the bottom whenever possible: the four top growth boxes align with each other, and the four lower health-promotion child boxes align with each other.
- Use AMS accent colors for AMS templates. Do not copy MN orange accent into AMS.
- Keep the A5 item marked as a prototype fixture so it does not affect the normal AMS template count or imply source-verified AMS content.

Implementation evidence:

- `Elevated ATI AMS Templates.html` includes explicit A5 selectors on `data-template-type="growth-development"`.
- The A5 prototype fixture is populated with neutral layout stress-test lines only, not ATI educational content.
- The A5 fixture remains `data-prototype-fixture="true"` and is available for design testing through prototype-fixture review.

Validation:

- Official A5 PDF was rendered and visually checked against the AMS/MN pattern.
- Script compilation and count validation should be repeated after each A5 design iteration.

## Prototype Update: 2026-07-04 AMS Templates A1/A3 Filled Fixtures

Reason for prototype:

- User requested fully populated prototypes for all template types, starting again with A1 and A3 because some current AMS examples have empty official boxes.
- In DESIGN-CANON / HOLD-CONTENT mode, the safe approach is to use neutral prototype fixtures for visual QA rather than adding real AMS educational content.

Prototype A1 pattern:

- Add a prototype-only A1 Basic Concept fixture with all three official boxes populated: Related Content, Underlying Principles, and Nursing Interventions.
- Use neutral layout stress-test lines to evaluate column density, wrapping, and bottom alignment.

Prototype A3 pattern:

- Add a prototype-only A3 Diagnostic Procedure fixture with every official slot populated: Description of Procedure, Indications, Interpretation of Findings, Considerations with Nursing Interventions (pre, intra, post), Client Education, Potential Complications, and lower Nursing Interventions.
- Preserve the larger official Considerations parent container and the left/right alignment preference from the A3 canon pass.
- Route `Nursing Interventions (pre, intra, post)` to the nested Considerations subbox, and route plain `Nursing Interventions` to the lower-right official box. Do not let one steal the other's content.
- Use deliberately uneven text lengths in paired A3 boxes during prototype testing so left/right height alignment can be judged under real density stress.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes `tpl-ams-prototype-basic-concept-layout` and `tpl-ams-prototype-diagnostic-procedure-layout`.
- Both fixtures remain `data-prototype-fixture="true"` so normal AMS counts are not affected.
- Fixture text is design-only and neutral; it does not add learner-facing ATI content.
- A3 prototype routing was corrected so the nested pre/intra/post subbox is populated separately from the lower-right Nursing Interventions box.

Validation:

- Script compilation passed.
- Normal AMS template count remained 76.
- Static routing validation confirmed that `Nursing Interventions (pre, intra, post)` maps to the nested Considerations subbox and plain `Nursing Interventions` maps to the lower-right box.

## Prototype Update: 2026-07-04 AMS Templates A7 Medication

Reason for prototype:

- User approved proceeding from A3 to A7 and provided the official A7 Medication PDF plus an MN medication example screenshot.
- A7 must be tested as a design prototype with every official box populated before any real AMS content enrichment occurs.

Prototype A7 pattern:

- Use the MN-style individual template modal shell and AMS accent colors.
- Use the official A7 Medication body structure: Purpose of Medication group with Expected Pharmacological Action and Therapeutic Use, then a wider left column containing Complications, Contraindications/Precautions, Interactions, and Evaluation of Medication Effectiveness, plus a narrower right column containing Medication Administration, Nursing Interventions, connector, and Client Education.
- Include `Category Class` in the medication meta strip. Use a blank field for real AMS cards when no source-supported category is present; use `Prototype Class` only for the prototype fixture.
- Preserve the vertical connector between Nursing Interventions and Client Education only. Match MN: use a neutral `var(--text3)` connector on the Nursing Interventions box, allow medication body boxes to avoid overflow clipping, extend the line slightly behind both boxes, and let the boxes mask it so only the segment in the gap remains visible.
- Use deliberately uneven text lengths across purpose and body boxes to stress-test wrapping, box height, bottom alignment, and connector behavior.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes `tpl-ams-prototype-medication-layout`.
- The A7 fixture remains `data-prototype-fixture="true"` and does not affect normal AMS template count.
- Medication-specific modal CSS now scopes A7 spacing, column proportions, dense text sizing, box radius, and the neutral behind-the-box Nursing Interventions-to-Client Education connector to `data-template-type="medication"`.
- The medication meta builder now adds a `Category Class` row for medication templates.

Validation:

- Official A7 PDF was rendered and visually checked against the MN medication screenshot.
- Script compilation and count validation should be repeated after each A7 design iteration.

Still deferred:

- Content enrichment for A3 remains out of scope in DESIGN-CANON / HOLD-CONTENT mode.
- A3 visual review was completed during the AMS prototype pass and the shared A3/A9/A13 procedure-family geometry is approved for AMS design-canon use.
- Other template types should continue to use their own official ATI template geometry rather than inheriting A3's labels.

## Prototype Update: 2026-07-04 AMS Templates A9 Nursing Skill

Reason for prototype:

- User provided the official A9 Nursing Skill PDF plus an MN Nursing Skill example screenshot.
- A9 must be tested as a design prototype with every official box populated before real AMS content enrichment occurs.

Prototype A9 pattern:

- Use the MN-style individual template modal shell and AMS accent colors.
- Use the official A9 Nursing Skill body structure: full-width Description of Skill, left-column Indications and Outcomes/Evaluation, right-side Considerations group containing Nursing Interventions (pre, intra, post) and Client Education, then lower Potential Complications connected to lower Nursing Interventions.
- Treat the Considerations area as a true parent container with two smaller stacked subboxes inside it: Nursing Interventions (pre, intra, post) and Client Education.
- Preserve the neutral `var(--text3)` connector between Potential Complications and Nursing Interventions, following the shared A3/A9/A13 connector convention.
- A3 Diagnostic Procedure and A9 Nursing Skill share the same official procedure-grid geometry; only the box labels differ. Keep their lower Potential Complications to Nursing Interventions connector aligned the same way.
- Use deliberately uneven text lengths across left/right and lower boxes to stress-test wrapping, box height, bottom alignment, and connector behavior.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes `tpl-ams-prototype-nursing-skill-layout`.
- The A9 fixture remains `data-prototype-fixture="true"` and does not affect normal AMS template count.
- Nursing Skill-specific modal CSS now scopes A9 max width, gap, connector overlap, dense text sizing, and official A9 box sizing to `data-template-type="nursing-skill"`.
- The A9 builder now routes the phased Nursing Interventions section into the Considerations parent and reserves the separate Nursing Interventions section for the lower-right official A9 box.
- The shared A3/A9 connector rule is explicitly scoped so later grid changes do not remove the Potential Complications to Nursing Interventions line.
- The shared connector is drawn as a neutral gap connector between the lower boxes to avoid clipping or accidental lines across the box interiors.

Validation:

- Official A9 PDF was rendered and visually checked against the MN Nursing Skill screenshot.
- Script compilation and count validation should be repeated after each A9 design iteration.

Still deferred:

- Content enrichment for A9 remains out of scope in DESIGN-CANON / HOLD-CONTENT mode.
- A9 visual review was completed during the AMS prototype pass and the shared A3/A9/A13 procedure-family geometry is approved for AMS design-canon use.
- A11 System Disorder has also completed prototype review and should be treated as an approved special-case A11 layout.

## Canonization Update: 2026-07-04 AMS Template Typography

Reason for canonization:

- User asked whether AMS template fonts were uniform with the other books before continuing with more template types.
- AMS and MN already share the same core font families, but AMS had scattered literal font sizes across the template modal, A1, and A3 overrides.

Canonized typography pattern:

- Use `DM Sans` for interface text, metadata, labels, controls, and template body copy.
- Use `DM Serif Display` for modal titles, worked-example titles, and ATI template box headings.
- Keep micro-labels uppercase with consistent letter spacing.
- Use one shared modal title scale, one worked-example title scale, one meta label/value scale, one box-heading scale, and one dense-template body scale.
- Allow dense official ATI template layouts, such as A1 and A3, to use the dense body scale while preserving the same font families and heading hierarchy.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now defines template typography tokens for modal titles, worked-example titles, metadata, box headings, body text, dense body text, and letter spacing.
- A1 and A3 now use those tokens instead of hard-coded local body sizes.
- A3 retains its official layout and larger Considerations container while using the shared typography scale.

Validation:

- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- `git diff --check` passed for AMS Templates and this audit file.

Still deferred:

- This canon is currently applied only to AMS Templates. It should be visually approved on A1 and A3 before rollout to other books.

## Canonization Update: 2026-07-04 AMS Shared Template Width

Reason for canonization:

- User identified that individual ATI template modals were not using the same width and that narrow layouts were wasting usable space.
- The design preference is to widen all template types consistently while preserving each official ATI internal box layout.

Canonized width pattern:

- Use one shared individual-template sheet width token for all AMS template types: `--tpl-template-width`.
- Current prototype value: `1000px`.
- Use a wider modal shell so the shared template sheet has breathing room without filling the entire viewport.
- Keep each template type's official internal geometry intact; A1, A3, A5, A7, A9, system disorder, concept analysis, and future template types should differ by internal layout, not by outer sheet width.
- On mobile, keep the template sheet responsive at full available width.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now defines `--tpl-template-width:1000px`.
- The modal shell now uses `width:min(1080px,100%)`.
- `.modal-template-card` uses `width:min(100%, var(--tpl-template-width))` and `max-width:var(--tpl-template-width)`.
- Template-specific max-width overrides now point back to the shared token instead of fixed per-type widths.

Still deferred:

- Visual approval is still needed after reviewing several template types side by side, especially dense layouts such as A1, A5, A7, and A9.

## Canonization Update: 2026-07-04 AMS Template Safe Insets

Reason for canonization:

- User identified that template text was too close to box edges and could be cut off or visually crowded as real content becomes denser.
- The A9 Considerations prototype showed this risk most clearly because the nested subboxes were being forced into equal-height halves.

Canonized spacing pattern:

- Use shared template box padding tokens: `--tpl-box-pad-x` and `--tpl-box-pad-y`.
- Dense template layouts should still be compact, but not use cramped 12px side padding.
- Nested boxes, especially A9 Considerations subboxes, should grow with content instead of clipping longer text.
- Preserve official ATI geometry and MN-style visual hierarchy while prioritizing readable inner spacing.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now defines `--tpl-box-pad-x:16px` and `--tpl-box-pad-y:14px`.
- Dense A1, A3, A5, A7, and A9 box content now uses the shared safe inset tokens.
- A9 Considerations subboxes no longer use forced equal-half flex sizing; they can grow with content while retaining the parent Considerations structure.

Still deferred:

- Visual approval is needed on A9 and A7 after refresh to confirm the new spacing still feels compact enough.

## Prototype Update: 2026-07-04 AMS Templates A11 System Disorder

Reason for prototype:

- User approved the A7/A9 spacing review and asked to move to the next template.
- A11 System Disorder is structurally complex and is the next best stress test for the AMS template canon.

Source support:

- Official ATI template source used: `/Users/markjuliusgearhart/Downloads/ATI Templates/A11 System Disorder.pdf`.
- The PDF is a multi-page ATI template bundle; page 11 was rendered and visually checked as the A11 System Disorder form.

Prototype A11 pattern:

- Use the shared widened template sheet and safe inset tokens.
- Use the official A11 top row: Alterations in Health (Diagnosis), Pathophysiology Related to Client Problem, and Health Promotion and Disease Prevention.
- Use the official Assessment block with Risk Factors, Expected Findings, Laboratory Tests, and Diagnostic Procedures in a 2-by-2 grouped area.
- Use the official Safety Considerations and Complications boxes, but optimize the AMS layout so Safety aligns with Assessment and Complications aligns with Patient-Centered Care.
- Use the official Patient-Centered Care geometry: Nursing Care over Therapeutic Procedures on the left, Medications as the tall center box, and Client Education over Interprofessional Care on the right.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes `tpl-ams-prototype-system-disorder-layout`.
- The A11 fixture remains `data-prototype-fixture="true"` and uses only neutral prototype text.
- The System Disorder builder now assigns explicit grid-area classes for the five official Patient-Centered Care boxes.
- System Disorder CSS now preserves official A11 geometry, including desktop and mobile stacking behavior.

Still deferred:

- A11 visual review was completed during the later space-optimization pass and is approved for AMS design-canon use.
- Real AMS System Disorder content enrichment remains paused in DESIGN-CANON / HOLD-CONTENT mode.

## Prototype Update: 2026-07-04 AMS Templates A11 Space Optimization

Reason for update:

- User reviewed the A11 prototype against the MN screenshot and official A11 template and identified poor space optimization.
- This is a design/canon issue only: no educational content was added.

Approved A11 refinement:

- Preserve the official A11 box identities and the MN-style visual shell.
- Keep Safety Considerations and Complications visually grouped: Safety Considerations is the larger right-side parent/shadow area, and Complications sits inside it as the lower child.
- Reduce obvious wasted space where possible, but do not separate Complications from the Safety Considerations parent.
- Give the grouped Safety/Complications rail a balanced width for dense safety text: wider than the narrow MN-style strip, but not so wide that it overwhelms the Patient-Centered Care block.
- Align the top and bottom of the nested Complications box with the top and bottom of the Patient-Centered Care block when the desktop A11 grid is shown.
- Keep the bottom of the grouped right rail visually balanced against Patient-Centered Care where the official A11 geometry allows.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now renders A11 Complications inside the Safety Considerations group using the `sd-complications` class.
- The System Disorder grid preserves the official parent-child relationship while using the lower desktop row for the nested Complications box, so its top and bottom align with Patient-Centered Care.
- The A11 right rail now uses a balanced middle-width column so Safety Considerations and Complications have more readable space without dominating the layout.
- Mobile stacking keeps Safety Considerations and its nested Complications together before Patient-Centered Care.

Still deferred:

- User approved the optimized A11 layout after the Safety Considerations and Complications rail was aligned with Patient-Centered Care.
- A11 is approved for AMS design-canon use as a special-case system-disorder layout.

## Prototype Update: 2026-07-04 AMS Templates A13 Therapeutic Procedure

Reason for prototype:

- User provided the official A13 Therapeutic Procedure PDF and MN-style screenshot as the next template-type prototype.
- This is a design/canon task only; no AMS educational content was added.

Source support:

- Official ATI template source used: `/Users/markjuliusgearhart/Downloads/ATI Templates/A13 Therapeutic Procedure.pdf`.
- The PDF is a one-page letter-size A13 Therapeutic Procedure form and was rendered locally for layout verification.

Prototype A13 pattern:

- Use the shared widened template sheet and safe inset tokens.
- Preserve the official A13 field order: Student Name, Procedure Name, and Review Module Chapter.
- Use the official A13 full-width Description of Procedure panel.
- Use the official two-column body: Indications over Outcomes/Evaluation on the left, and Considerations on the right.
- Keep Considerations as a parent/shadow area with two stacked child boxes: Nursing Interventions (pre, intra, post) and Client Education.
- Use the official bottom row: Potential Complications on the left connected to Nursing Interventions on the right.
- Follow the same left/right bottom alignment and neutral connector convention approved for A3 and A9.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes `tpl-ams-prototype-therapeutic-procedure-layout`.
- A13 now has explicit `therapeutic-procedure` CSS using the shared A3/A9 procedure grid discipline.
- The procedure builder now routes A13's phase-based Nursing Interventions (pre, intra, post) into the Considerations parent and keeps the lower Nursing Interventions box separate.
- The Potential Complications connector rule now explicitly includes A13.
- The A13 fixture remains `data-prototype-fixture="true"` and uses only neutral prototype text.

Approval status:

- User approved the A13 direction after confirming it belongs to the shared A3/A9/A13 procedure-family geometry with A13-specific labels.
- A13 is approved for AMS design-canon use.

## Prototype Update: 2026-07-04 AMS Templates A15 Concept Analysis

Reason for prototype:

- User provided the official A15 Concept Analysis PDF and MN-style screenshot as the final template-type prototype in this pass.
- This is a design/canon task only; no AMS educational content was added.

Source support:

- Official ATI template source used: `/Users/markjuliusgearhart/Downloads/ATI Templates/A15 Concept Analysis.pdf`.
- The PDF is a one-page letter-size A15 Concept Analysis form and was rendered locally for layout verification.

Prototype A15 pattern:

- Use the shared widened template sheet and safe inset tokens.
- Preserve the official A15 field order: Student Name and Concept Analysis.
- Use the official full-width Defining Characteristics panel.
- Use the official two paired rows: Antecedents with Negative Consequences, then Related Concepts with Exemplars.
- Keep paired boxes aligned top and bottom when they occupy the same row.
- Use the MN modal shell and AMS accent/spacing discipline without adding connectors, because A15 does not use connector lines.

Implementation evidence:

- `Elevated ATI AMS Templates.html` now includes a source-backed `tpl-ams-prototype-concept-analysis-layout` fixture.
- A15 now has explicit `concept-analysis` CSS using the official five-box geometry.
- The A15 fixture remains `data-prototype-fixture="true"` and uses only neutral prototype text.

Approval status:

- User approved the A15 prototype after the source-backed concept-analysis fixture was added.
- A15 is approved for AMS design-canon use.

## Final QA Update: 2026-07-05 AMS Templates Prototype Set

Reason for update:

- User asked to proceed with the recommended final QA before restarting heartbeat automation.
- This is a design/canon readiness check only; no educational content was added.

Approved AMS template set:

- A1 Basic Concept.
- A3 Diagnostic Procedure.
- A5 Growth and Development.
- A7 Medication.
- A9 Nursing Skill.
- A11 System Disorder.
- A13 Therapeutic Procedure.
- A15 Concept Analysis.

Final QA evidence:

- `Elevated ATI AMS Templates.html` script parsing passed with the bundled Node runtime.
- `git diff --check` passed for AMS Templates and this audit file.
- Static count check passed: 84 total template cards, 8 prototype fixtures, and 76 normal AMS templates.
- Prototype fixture IDs are present for all approved template types.
- Structure sweep confirmed each prototype fixture contains its expected official ATI section set.
- Old template hub type/chapter filters and nonfunctional Filled/Blank card tags are absent.
- AMS orange styling was not found; the remaining word "orange" appears only in source-supported tuberculosis medication content.
- In-app browser visual verification against the direct `file://` URL was blocked by browser URL policy, so this final pass used static and script-level verification rather than a new rendered screenshot pass.

Next heartbeat recommendation:

- Restart the heartbeat in DESIGN-CANON / HOLD-CONTENT mode only after this QA note is committed or intentionally left as the current working baseline.
- Next heartbeat should roll the approved AMS template design canon to one next book template file at a time, without touching MN and without adding educational content.

## Rollout Update: 2026-07-05 Pharm Templates Canon Rollout

Reason for rollout:

- User approved the AMS Templates prototype set as the current template-design canon and asked to proceed with the optimal one-book-at-a-time rollout path.
- Pharm was selected as the next non-MN template file after MH and PD. This was a design/canon migration only.

Completed in Pharm Templates only:

- Replaced the older Pharm template shell with the approved AMS/MN-canon template shell: fixed left navigation, template-type accordions, compact worked-example rows, progress strip, search, modal worked examples, Filled/Blank modal mode, print, and same-type Previous/Next navigation.
- Preserved all existing Pharm worked-template content while converting it from old `example-card` markup into canon `template-card` markup.
- Preserved Pharm identity and accent color instead of importing AMS/MH/PD colors.
- Corrected stale subject identity in the Pharm sidebar/header.
- Kept A5 Growth and Development as an empty Pharm template-type group rather than inventing educational content.

Validation:

- Static count check passed: 249 total Pharm template cards.
- Type distribution preserved: A1 = 1, A3 = 3, A5 = 0, A7 = 141, A9 = 18, A11 = 35, A13 = 9, A15 = 42.
- Script compilation passed with the bundled Node runtime: 1 inline script parsed successfully.
- Source sweep confirmed no stale MH/PD subject labels, no old `exampleModal`, and the canon `templateModal` plus `buildMnTemplateLayout()` are present.
- Rendered localhost validation passed for the Pharm shell: Pharm heading, Pharm search placeholder, 249 cards outside the modal, hidden empty state on first load, and A5 empty group present.
- Rendered modal validation passed for representative A1, A7, A11, and A13-family examples: generated canon layouts appeared as `bc-grid`, `med-grid`, `sd-grid`, and `tp-grid`; medication connector and system-disorder safety grouping rendered where expected; Previous/Next same-type navigation appeared in the modal; no text-edge overflow was detected in sampled boxes. The procedure-family connector line can extend behind boxes by design and may register as non-text scroll width.

Still deferred:

- Pharm educational enrichment remains paused in DESIGN-CANON / HOLD-CONTENT mode.
- This Pharm-only note is superseded by the full non-MN template rollout completion audit below.

## Rollout Completion Audit: 2026-07-05 Non-MN Template Files

Reason for audit:

- User asked to proceed with the current best path before restarting heartbeat automation.
- This was a design/canon verification pass only; no educational content, templates, cards, prompts, or enrichment were added.

Files checked:

- `Elevated ATI AMS Templates.html`
- `Elevated ATI MH Templates.html`
- `Elevated ATI PD Templates.html`
- `Elevated ATI Pharm Templates.html`
- `Elevated ATI MN Templates.html` was intentionally not touched.

Completion evidence:

- All current non-MN template files now use the approved template-canon shell: fixed template navigation, template-type accordion grouping, compact worked-example rows, search, modal worked examples, Filled/Blank modal mode, print, and same-type Previous/Next navigation.
- All current non-MN template files contain `templateModal`, `buildMnTemplateLayout()`, and same-type Previous/Next navigation.
- No current non-MN template file contains the old `exampleModal` shell.
- Correct subject H1 labels are now confirmed:
  - AMS: Adult Med-Surg Templates.
  - MH: Mental Health Nursing Templates.
  - PD: Pediatric Templates.
  - Pharm: Pharmacology Templates.
- Cleanup made during this pass: corrected the MH template hub H1 from the stale AMS label to the MH subject label.

Count evidence:

- AMS Templates: 84 total template cards, 8 actual prototype fixtures, 76 normal template cards.
- MH Templates: 71 total template cards, 0 actual prototype fixtures.
- PD Templates: 179 total template cards, 0 actual prototype fixtures.
- Pharm Templates: 249 total template cards, 0 actual prototype fixtures.

Validation:

- Script parsing passed for all four current non-MN template files.
- Static canon-feature sweep passed for all four current non-MN template files.
- Subject-label sweep passed after the MH H1 cleanup.
- This pass did not perform educational source verification because no educational content was authored.

Current decision:

- Template-canon rollout is complete for all current non-MN template files in the repo.
- Do not restart the older heartbeat prompt that says to begin one-book-at-a-time template-canon rollout unless it is updated, because there is no remaining non-MN template file to roll out in the current repo.

Next recommendation:

- Move next to a Flashcards design-canon audit/rollout plan, because flashcards are the next shared public shell likely to benefit from canon alignment.
- Start with an audit-only pass across AMS, MH, PD, and Pharm Flashcards.
- Keep content population paused: do not add flashcards or educational content during DESIGN-CANON / HOLD-CONTENT mode.

## Flashcards Design-Canon Audit: 2026-07-05

Reason for audit:

- User approved proceeding to the next design-canon surface after template rollout completion.
- This was a flashcard shell and workflow audit only; no educational flashcard content was authored.

Files checked:

- `Elevated ATI MN Flashcards.html` as read-only reference.
- `Elevated ATI AMS Flashcards.html`.
- `Elevated ATI MH Flashcards.html`.
- `Elevated ATI PD Flashcards.html`.
- `Elevated ATI Pharm Flashcards.html`.

MN flashcard canon evidence:

- MN uses a first-class review engine rather than a static card grid.
- Canon elements include fixed flashcard sidebar navigation, Review/Browse tabs, due counts, SM-2 scheduling, reveal/rate controls, session metrics, keyboard shortcuts, source links back to the book, starter deck loading, CSV export, filter panel, status filters, and durable local progress.

Audit findings:

- AMS Flashcards is the only current non-MN flashcard file still on the older flat shell. It has 208 inline `<article class="flashcard">` cards, search/chapter/type chips, reveal buttons, and source text, but it lacks the MN-style sidebar, Review/Browse tabs, SM-2 scheduler, due queue, session metrics, keyboard shortcut panel, starter deck loader, and CSV export.
- MH Flashcards already uses the MN-style flashcard shell with 593 starter deck items, subject-specific schedule/filter keys, sidebar, Review/Browse tabs, SM-2 scheduling, session metrics, keyboard shortcuts, source links, starter deck loading, and CSV export.
- PD Flashcards already uses the MN-style flashcard shell with 747 starter deck items, subject-specific schedule/filter keys, sidebar, Review/Browse tabs, SM-2 scheduling, session metrics, keyboard shortcuts, source links, starter deck loading, and CSV export.
- Pharm Flashcards already uses the MN-style flashcard shell with 702 starter deck items, subject-specific schedule key, sidebar, Review/Browse tabs, SM-2 scheduling, session metrics, keyboard shortcuts, source links, starter deck loading, and CSV export.

Cleanup completed during audit:

- Updated MH CSV export filename from the old `NUR2460` label to an MH-specific filename.
- Updated PD CSV export filename from the old `NUR2460` label to a PD-specific filename.
- Updated Pharm CSV export filename from the old `NUR2460` label to a Pharm-specific filename.
- Updated Pharm filter persistence to use `atipharm_fc_filters`, while preserving non-destructive migration bridges from legacy Pharm/shared filter keys so existing filter state is not stranded.

Validation target for this batch:

- Script parsing should pass for all five flashcard files.
- Feature matrix should confirm that MH, PD, and Pharm remain MN-style review engines after cleanup.
- AMS should remain unchanged in this batch except as the documented next rollout target.

Status after user correction:

- Flashcards are paused because the user clarified that template uniformity is not complete yet.
- Do not begin the AMS Flashcards shell migration until templates are accepted as uniform.
- Return to template design-canon work only.

## Template Top Hero Canon Update: 2026-07-05

Reason for update:

- User identified that MN Templates has a clearer top instructional block and page-level Print Templates action than the other template hubs.
- Flashcards are paused until template uniformity is complete.

Files updated:

- `Elevated ATI AMS Templates.html`.
- `Elevated ATI MH Templates.html`.
- `Elevated ATI PD Templates.html`.
- `Elevated ATI Pharm Templates.html`.

Read-only reference:

- `Elevated ATI MN Templates.html`.

Completed:

- Added MN-style top guidance to the non-MN template hubs: eight ATI Active Learning templates, expand behavior, tab study behavior, and single-tap/double-tap progress behavior.
- Added a page-level `Print Templates` button to each non-MN template hub.
- Added a `Templates` divider before the template/search area so the top area reads like MN before the template list begins.
- Added a page-level print handler for each non-MN template hub without changing modal print behavior.
- Preserved each subject's accent color, subject identity, and existing template content.

Content status:

- No ATI educational content was added.
- No template content was enriched.
- MN was not edited.

Validation target:

- Static sweep should confirm each non-MN template hub has `masterPrintBtn`, `.compare-btn`, `.section-divider`, the MN-style progress guidance sentence, and the page-level print handler.
- Script parsing should pass for all four edited template files.

Next recommendation:

- Visually QA the top hero/print area on AMS, MH, PD, and Pharm Templates.
- If the top area is accepted, continue template uniformity only for remaining design issues; keep flashcards paused.

## Template Sidebar Search Canon Update: 2026-07-05

Reason for update:

- User compared the MN sidebar search/progress strip against PD and requested the MN design be applied to the other books.
- This is a design-only template uniformity update.

Files updated:

- `Elevated ATI AMS Templates.html`.
- `Elevated ATI MH Templates.html`.
- `Elevated ATI PD Templates.html`.
- `Elevated ATI Pharm Templates.html`.

Read-only reference:

- `Elevated ATI MN Templates.html`.

Completed:

- Matched the MN sidebar search placeholder pattern: `Search templates & examples…` without a leading search emoji inside the field.
- Tightened the non-MN sidebar search input padding and radius to match the MN treatment.
- Matched the lighter MN sidebar progress-text weight while preserving each book's accent color for reviewed/checked indicators.

Content status:

- No ATI educational content was added.
- No template examples were added or enriched.
- MN was not edited.

Next recommendation:

- Visually QA the sidebar progress/search strip on AMS, MH, PD, and Pharm Templates.
- Continue template uniformity only; keep flashcards paused.

## MN Template Width Backport: 2026-07-05

Reason for update:

- User identified that the approved template width/space optimization had been applied outside MN but not backported to MN.
- MN is explicitly approved for this focused design-canon update.

File updated:

- `Elevated ATI MN Templates.html`.

Reference:

- Current approved AMS Templates modal geometry.

Completed:

- Widened the MN individual-template modal workspace to the approved shared 1080 px modal width.
- Added an MN template modal width token so the widened shell is explicit and reusable.
- Ensured template examples pulled into the modal use the full available modal body width.
- Preserved MN accent color, content, sidebar, accordion behavior, and template structure.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static CSS check should confirm `--template-modal-width:1080px` and `width:min(var(--template-modal-width),100%)`.
- Visual QA should confirm MN template examples have more horizontal room while still collapsing properly on mobile.

## Non-MN Template Width Rollout: 2026-07-05

Reason for update:

- User reviewed the larger MN template display and approved that wider inner sheet feel for the rest of the books.
- The non-MN books already had the 1080 px modal shell but retained the narrower 880 px inner template sheet.

Files updated:

- `Elevated ATI AMS Templates.html`.
- `Elevated ATI MH Templates.html`.
- `Elevated ATI PD Templates.html`.
- `Elevated ATI Pharm Templates.html`.

Reference:

- Current MN rendered modal/card width after the MN width backport.

Completed:

- Increased the shared non-MN `--tpl-template-width` token from 880 px to 1000 px.
- Preserved each book's accent color, subject identity, modal shell, template content, and template-type-specific layout rules.
- Kept mobile behavior responsive because `.modal-template-card` still uses `width:min(100%, var(--tpl-template-width))`.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static CSS check should confirm all non-MN template files now define `--tpl-template-width:1000px`.
- Visual QA should confirm AMS, MH, PD, and Pharm individual template modals now use the larger MN-like display without horizontal overflow.

## MN Sidebar Header Alignment: 2026-07-05

Reason for update:

- User identified that the MN sidebar header still used the old course-code identity line while the other template books use the cleaner ATI subject-code convention.

File updated:

- `Elevated ATI MN Templates.html`.

Completed:

- Changed the MN sidebar identity line from `NUR 2460 · ATI` toward the shared ATI subject-code convention.
- Matched the visible MN sidebar version date to the current template-family header convention used by AMS, MH, PD, and Pharm: `v3.1.0 · 2026-07-01`.
- Preserved MN accent color, subject subtitle, template content, modal behavior, and navigation behavior.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static markup check should confirm the MN sidebar header now uses the current template sidebar course-label canon and `v3.1.0 · 2026-07-01`.

## Template Sidebar Course Label Cleanup: 2026-07-05

Reason for update:

- User identified that labels such as `ATI MN · ATI` repeat ATI unnecessarily.
- The cleaner canonical sidebar identity is the subject code alone.

Files updated:

- `Elevated ATI AMS Templates.html`.
- `Elevated ATI MH Templates.html`.
- `Elevated ATI PD Templates.html`.
- `Elevated ATI Pharm Templates.html`.
- `Elevated ATI MN Templates.html`.

Completed:

- Removed the redundant trailing `· ATI` from all template sidebar course labels.
- Current sidebar labels are `ATI AMS`, `ATI MH`, `ATI PD`, `ATI Pharm`, and `ATI MN`.
- Preserved each book's accent color, subtitle, version line, template content, modal behavior, and navigation behavior.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static markup check should confirm no template sidebar `sb-course` label still ends in `· ATI`.

## MN Main Hero Alignment: 2026-07-05

Reason for update:

- User preferred the newer non-MN template hero pattern: subject-specific eyebrow plus subject-specific template title.
- MN still used the older course-code hero line and generic `ATI Templates` title.

File updated:

- `Elevated ATI MN Templates.html`.

Completed:

- Changed the MN main hero eyebrow to `MN Active Learning Templates`.
- Changed the MN main hero title to `Maternal Newborn Templates`.
- Preserved MN accent color, sidebar, search, print action, template content, modal behavior, and navigation behavior.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static markup check should confirm the MN main hero no longer uses the older course-code eyebrow or generic `ATI Templates` title.

## Template Modal Overlay And Size Alignment: 2026-07-05

Reason for update:

- User identified that individual template modal sizing and the background blur/overlay treatment were not uniform across books.
- User preferred MN's taller modal size and the newer four-book overlay treatment.

Files updated:

- `Elevated ATI AMS Templates.html`.
- `Elevated ATI MH Templates.html`.
- `Elevated ATI PD Templates.html`.
- `Elevated ATI Pharm Templates.html`.
- `Elevated ATI MN Templates.html`.

Completed:

- Updated AMS, MH, PD, and Pharm template modals to use MN's taller modal height cap: `calc(100vh - 80px)`.
- Updated MN's modal overlay background to match the newer four-book dark overlay treatment while preserving the existing blur amount.
- Preserved each book's accent color, template content, modal controls, print controls, navigation, and template layouts.

Content status:

- No ATI educational content was added.
- No template content was enriched.

Validation target:

- Static CSS check should confirm AMS, MH, PD, and Pharm modals use `max-height:calc(100vh - 80px)`.
- Static CSS check should confirm MN uses the shared dark modal overlay background.

## Four-Surface MN Canon Roadmap: 2026-07-05

Reason for roadmap:

- User wants MN to remain the structural/design reference across each book's four public HTML surfaces.
- Templates have received the deepest pass so far and should not keep reopening unless a concrete visual defect appears.
- Flashcards are paused by user direction until the template and book/hub surfaces are more uniform.

Global rules:

- Current mode remains `DESIGN-CANON / HOLD-CONTENT`.
- Do not add ATI educational content, flashcards, prompts, templates, sections, or enrichment.
- Use MN as the design/structure reference, but do not edit MN unless the user explicitly asks.
- Preserve each book's accent color, subject identity, existing educational content, and source links.
- Treat edits as design, layout, navigation, wording-consistency, and QA changes only.

Roadmap checklist:

| Order | Surface | Current status | Next action |
| --- | --- | --- | --- |
| 1 | Templates | Pinned | Keep the approved AMS/MN template canon stable; only fix concrete regressions. |
| 2 | AMS Book vs MN Book | Static/interaction-code pass complete; rendered browser QA deferred | Proceed to AMS Hub recheck now; rerun rendered modal QA later when the browser connector is available or if the user reports a concrete Book visual defect. |
| 3 | AMS Hub vs MN Hub | Static structure recheck complete; rendered/user visual QA pending | Only reopen if rendered QA or user review identifies a concrete hub visual mismatch. |
| 4 | AMS Flashcards vs MN Flashcards | Paused | Do not proceed until the user explicitly resumes flashcard design work. |
| 5 | Other books | Pending | Roll out only after AMS Book and AMS Hub are accepted as the updated cross-book baseline. |

Trackable checklist:

- [x] Pin Templates as the approved template-design baseline.
- [x] Pause Flashcards until template/book/hub uniformity is stable.
- [x] Start AMS Book vs MN Book with static evidence instead of assumptions.
- [x] Finish AMS Book modal static/interaction-code QA: shell, tabs, controls, close button, keyboard flow, scroll behavior.
- [ ] Run rendered AMS Book modal browser QA when connector access is available or a concrete visual defect is reported.
- [x] Finish AMS Book TL;DR and dense-card hierarchy static QA against MN.
- [x] Finish AMS Book Related ATI Template link/bridge static QA against MN and the approved template canon.
- [x] Finish AMS Book ALS presentation static QA using existing AMS ALS content only.
- [x] Finish AMS Book Practice/Application Exercises static QA, preserving the approved newer AMS exercise design where it is better than MN.
- [x] Finish AMS Hub static structure recheck against MN after the Book static pass.
- [ ] Run rendered/user visual AMS Hub QA if a concrete visual mismatch is reported or before cross-book hub rollout.
- [ ] Keep other-book rollout on hold until AMS Book and Hub are accepted.

First active batch:

- Start with an evidence-first AMS Book vs MN Book audit.
- Record static differences before editing.
- Only implement design-only corrections that are clearly supported by MN or by the already approved AMS template canon.

## AMS Book MN-Canon Audit Pass 1: 2026-07-05

Status:

- Completed for modal/control and Practice/Application Exercises static inspection; continued by Pass 2.

Static evidence gathered:

| Pattern | MN Book | AMS Book | Design meaning |
| --- | ---: | ---: | --- |
| Chapters | 27 | 96 | Counts match each book's source scope. |
| TL;DR sections | 27 | 96 | Both books have TL;DR coverage for every chapter. |
| Template bridge sections | 27 | 96 | Both books have chapter-level template bridge coverage. |
| Exercise sections | 27 | 96 | Both books use `-exercises` sections for Practice/Application Exercises. |
| Chapter modal | 1 | 1 | Both books use a single modal workspace system. |
| Brief cards | 35 | 104 | AMS has comparable TL;DR/card scaffolding, scaled to 96 chapters. |
| Condition blocks | 633 | 570 | AMS uses fewer condition blocks relative to chapter count; dense-box hierarchy needs visual QA. |
| Finding cards | 561 | 1742 | AMS relies heavily on finding-card style; check whether this creates clutter or weak hierarchy. |
| Knowledge cards | 189 | 65 | MN uses more knowledge-card patterning; AMS may need design-only hierarchy alignment where existing content supports it. |
| Mid-read prompts | 1011 | 54 | AMS does not use MN's mid-read rhythm at the same density; do not add prompts in HOLD-CONTENT mode, but standardize existing prompt styling. |
| Mid-prompt markers | 47 | 47 | Both contain the older prompt marker class; resolve style duplication carefully without adding prompts. |
| ALS cards | 137 | 22 | AMS has fewer ALS-specific card instances; only restyle existing ALS content in this mode. |
| Template bridges | 62 | 105 | AMS bridge count is healthy; verify visual consistency and placement. |
| Application Exercises text markers | 68 | 96 | AMS appears to have one Practice/Application Exercises marker per chapter. |

Initial findings:

- Templates are not the next active surface; keep them pinned unless the user reports a specific defect.
- AMS Book already has the required core shell: chapter modal, TL;DR, Templates, Practice/Application Exercises, bookmarks, highlights, NCLEX filter, and chapter navigation.
- The likely Book risks are design consistency rather than missing educational material: dense-card hierarchy, prompt class consistency, ALS card styling, Practice tab layout, and small-box spacing/alignment.

Next implementation target:

- Inspect AMS Book modal/chapter CSS against MN Book and make the first small design-only correction if there is a clear mismatch that does not alter educational content.

Pass 1 modal/control inspection:

- MN and AMS use the same base chapter modal shell: full-screen overlay, `max-width:980px` modal, 16px radius, shared title/meta sizing, shared tab strip behavior, and shared body padding.
- AMS intentionally adds chapter Previous/Next controls inside the modal action row. This is an approved user-requested improvement and should be preserved rather than removed to match MN exactly.
- AMS adds mobile overflow protection around the modal header/body. This is a safe design robustness improvement and should be preserved unless visual QA shows a regression.
- No AMS Book HTML change was made from this modal pass because the clear differences are either approved AMS improvements or mobile safety guards.

Pass 1 Practice/Application Exercises inspection:

- MN uses the older compact exercise row pattern.
- AMS uses the newer approved Application Exercises pattern: question chip, boxed options, clearer answer/rationale toggle copy, and a separated answer panel.
- This is a known design preference from Batch 2 page 15 item 16, so the AMS pattern should be preserved and visually QA'd rather than reverted to MN.

Updated next implementation target:

- Run representative rendered visual QA on AMS Book modal behavior before moving back to the AMS Hub recheck.

## AMS Book MN-Canon Audit Pass 2: 2026-07-05

Status:

- Static AMS Book design pass complete.
- No public HTML change was made in this pass.
- No ATI educational content was added or rewritten.

Static evidence gathered:

| Pattern | AMS Book count | Design finding |
| --- | ---: | --- |
| TL;DR brief cards | 96 | One per chapter; CSS matches the MN brief-card pattern. |
| Related ATI Template bridge sections | 96 | One per chapter; CSS matches MN, with AMS also allowing the existing `h2` bridge heading. |
| Active Learning Scenario sections | 96 | One per chapter; base ALS card styling matches MN. |
| Practice/Application Exercises sections | 96 | One per chapter; AMS keeps the newer approved exercise design from Batch 2 page 15 item 16. |

Design decisions:

- TL;DR cards do not need an AMS HTML edit because the AMS and MN card rules use the same structure, spacing, heading hierarchy, and mobile behavior.
- Related ATI Template bridges do not need an AMS HTML edit because AMS already has chapter-level bridge coverage and preserves the approved template-canon connection.
- ALS presentation does not need an AMS HTML edit because the base ALS card presentation matches MN and uses existing AMS ALS content only.
- Dense-card hierarchy is acceptable as an AMS-approved improvement over MN: AMS preserves the MN card/pill hierarchy while keeping the later approved wide grids, equal-height card behavior, text-wrap protection, and clearer list dividers for scanability.
- Practice/Application Exercises should not be reverted to MN because AMS is using the newer user-approved answer/rationale layout.

Remaining AMS Book QA:

- Rendered modal QA was not completed in this batch because automated in-app browser navigation to the local AMS Book file was blocked, and the later localhost browser-tab attempt reset the browser connector.
- Static/interaction-code QA should be completed before leaving the Book pass.
- Rendered modal visual pass for representative chapters should be rerun later when browser connector access is available or if the user reports a concrete Book visual defect.
- Then return to the AMS Hub recheck against MN.

## AMS Book MN-Canon Modal QA Pass 3: 2026-07-05

Status:

- Static/interaction-code QA complete.
- No public HTML change was made in this pass.
- No ATI educational content was added or rewritten.
- Rendered in-app browser QA remains deferred because the browser connector reset after a timed-out localhost tab attempt, and the selected `file://` tab was blocked by browser-tool URL policy.

Static/interaction evidence verified:

| Area | Evidence in AMS Book | Finding |
| --- | --- | --- |
| Modal shell | `.modal-overlay`, `.modal`, `.modal-header`, `.modal-body` | AMS has the same core modal workspace pattern and scroll containment expected from the MN Book reference. |
| Close behavior | `.modal-close`, overlay click handler, Escape key handler | Close affordances are wired in code and should remain visually checked later. |
| Tabs | `.modal-tabs-wrap`, `.modal-tabs`, `buildTabLabel`, tab click binding | AMS keeps the chapter tab model and maps TL;DR, Templates, Practice, and content tabs into the modal. |
| Previous/next chapter controls | `.modal-chapter-nav`, `getAdjacentChapterId`, `navigateModalChapter`, `updateModalChapterNav` | The user-approved previous/next chapter controls are present and preserve active tab family when moving chapters. |
| Hash/open flow | `openChapter`, `openChapterFromHash`, `hashchange` handler | Direct chapter links route through the modal instead of relying on page scroll. |
| Scroll/mobile safeguards | mobile rules for `.modal-overlay`, `.modal`, `.modal-tabs-wrap`, `.modal-chapter-nav` | AMS includes additional mobile overflow protection; keep unless visual QA reveals a regression. |
| Bookmark/highlight hooks | bookmark injection around `openChapter`, highlight reapply observer | Existing study tools are attached to the modal opening flow without adding content. |
| NCLEX filter hooks | `injectNclexFilterBar`, `.nclex-filter-chip`, `.nclex-hidden` | Practice filtering is wired for the rendered modal; visual confirmation remains deferred. |

Decision:

- Do not reopen Templates or Flashcards from this pass.
- Do not edit AMS Book without a concrete visual defect.
- Proceed to the AMS Hub recheck against MN as the next best design-canon task.

Next Recommendation:

- Recheck AMS Hub against MN with focus on hero alignment, stat box count/labels, Pick up where you left off, card queue, primary tool blocks, spacing, and removal of redundant template-type stats.

## AMS Hub MN-Canon Static Recheck: 2026-07-05

Status:

- Static structure recheck complete.
- No public HTML change was made in this pass.
- No ATI educational content was added or rewritten.
- Rendered/user visual QA remains pending.

Static evidence verified:

| Area | AMS Hub evidence | MN canon comparison |
| --- | --- | --- |
| Hero/topbar | Topbar, subject mark, hero eyebrow, two-line hero title, subject subcopy | Matches MN structure while preserving AMS subject identity and accent. |
| Stat row | Four boxes only: Chapters, Units, Worked Templates, Starter Cards | Matches MN count pattern; redundant Template Types stat is absent. |
| Pick up where you left off | Continue reading, Review queue, Last template cards | Matches MN card pattern and local-state intent. |
| Review queue | Review queue panel with due count and empty state | Matches MN review-queue placement while preserving AMS current zero-card status. |
| Primary tools | ATI Chapter Book, ATI Templates, Flashcards cards | Matches MN three-tool dashboard structure; Flashcards remains paused for further design work. |
| Unit map | Unit cards with ranges and progress bars | Matches MN unit-map pattern, scaled to AMS 14 units. |
| Template types section | Lower template-type section remains present | Matches MN; this is separate from the removed redundant stat box. |
| Storage/footer | Storage panel and footer present | Matches MN support/utility structure. |

Decision:

- Treat AMS Hub as statically aligned with MN for the current design-canon stage.
- Do not edit AMS Hub without a concrete visual defect; the remaining differences are subject-specific labels, counts, copy, and accent values.
- Keep Flashcards paused.

Next Recommendation:

- Ask for or perform rendered visual QA on AMS Hub if needed; otherwise move to deciding the next non-flashcard surface for cross-book rollout after AMS Book and AMS Hub are accepted.

## MH Hub MN-Canon Parity Pass: 2026-07-05

Status:

- Updated Mental Health Hub structure toward the approved MN/AMS/PD/Pharm hub pattern.
- No ATI educational content was added or rewritten.
- Flashcards remain paused; only existing local review-queue status is surfaced.
- Templates remain pinned; template links/counts are navigation/status only.

Evidence:

- Added three-card pickup row, review queue, primary tools label, unit-map label, and lower template-type navigation.
- Wired existing MH storage keys: `nur2460_atimh_progress`, `atimh_templates_progress`, `atimh_fc_schedule`, `nur2460_last_chapter`, and `atimh_last_template`.
- Preserved MH accent, subject identity, chapter/unit/template counts.

Next Recommendation:

- Visual QA Mental Health Hub against MN/AMS/PD/Pharm, then continue the Book-surface parity checklist. Do not resume Flashcards until hub/book/template uniformity is accepted.

## Shell-First Canon Plan: 2026-07-05

User goal clarified:

- Build durable shells for each book first.
- Educational-content population will happen later in a separate workflow.
- Codex should own the HTML/CSS/JS frame quality, canon consistency, navigation behavior, layout discipline, and QA.
- Claude or a later content-focused workflow can populate teachable material once shells are stable.

Current design-canon interpretation:

| Surface | Current status | Next action |
| --- | --- | --- |
| Templates | Pinned/approved as the current template design canon | Do not reopen unless a concrete defect is reported. |
| Hubs | Active shell surface | Finish rendered MH Hub visual QA, then continue hub parity across books as needed. |
| Books | Next major shell surface | Compare AMS/MH/PD/Pharm book shells to MN after hub parity is accepted. |
| Flashcards | Paused | Do not resume until Hub, Book, and Templates shells are uniform. |

Shell completion gates:

- Static structure check: required MN-derived shell parts exist and redundant pieces are removed.
- Rendered visual QA: spacing, font scale, blur, modal width, card count, and responsive behavior are checked.
- Navigation/count QA: links, anchors, progress counters, and local-storage keys are verified.
- Canon documentation: accepted decisions and remaining rollout limits are recorded.

Next Recommendation:

- Complete rendered Mental Health Hub QA against the MN/AMS/PD/Pharm hub pattern. If no concrete defect appears, move to the Book-shell parity checklist while keeping Flashcards paused and Templates pinned.

## MH Hub Rendered Shell QA: 2026-07-05

Status:

- Rendered Mental Health Hub QA complete through local browser preview.
- Removed the stale "Recently added / Planned additions" future panel from MH Hub because Templates already exist and Flashcards are paused.
- No ATI educational content was added or rewritten.

Rendered evidence:

| Check | Result |
| --- | --- |
| Four-stat hub pattern | Pass: Chapters, Units, Worked Templates, Starter Cards only. |
| Redundant Template Types stat | Pass: absent from the stat row. |
| Pickup panel | Pass: Continue Reading, Review Queue, and Last Template cards render. |
| Primary tools | Pass: ATI Chapter Book, ATI Templates, and Flashcards cards render. |
| Unit map | Pass: 6 units render with progress structure. |
| Template-type navigation | Pass: 8 template types render in the lower section. |
| Storage/local state | Pass: storage controls and local-state wiring exist. |
| Stale future/planned panel | Pass: removed. |
| Horizontal overflow | Pass at 1280 x 900 preview. |

Validation performed:

- Browser-rendered QA through localhost preview.
- JavaScript parse check passed.
- Whitespace diff check passed.

Next Recommendation:

- Begin the Book-shell parity checklist next. Compare AMS, MH, PD, and Pharm Book HTML against MN's approved shell patterns and make design-only fixes. Keep Templates pinned and Flashcards paused unless the user explicitly reopens them.

## Book-Shell Parity Matrix: 2026-07-05

Current mode: DESIGN-CANON / HOLD-CONTENT.

Scope:

- Compare the five chapter-book shells against the approved MN/AMS dual-reference canon.
- Keep Templates pinned unless a concrete template-shell defect appears.
- Keep Flashcards paused.
- Do not add educational content, new study cards, prompts, or enrichment.

Initial findings:

| File | Shell status | Action |
| --- | --- | --- |
| MN Book | Baseline structure for chapter-book flow; now includes the shared modal previous/next chapter controls. | Added previous/next navigation to close the remaining approved chapter-modal shell gap. |
| AMS Book | Core shell features present; intro copy was still older and less MN-like. | Updated intro copy to the shared MN/MH/PD chapter-book description. |
| MH Book | Core shell features and shared intro copy present. | No immediate change needed. |
| PD Book | Core shell features and shared intro copy present. | No immediate change needed. |
| Pharm Book | Core shell features present; intro copy used variant wording; template bridge sections are not populated. | Updated intro copy to shared wording; template bridges remain deferred because adding sections is not allowed during HOLD-CONTENT mode. |

Validation performed:

- Static shell matrix confirmed sidebar search, print, bookmarks, highlights/notes, modal tabs, and flashcard button wiring exist across the five chapter-book files.
- AMS, MN, MH, PD, and Pharm now include modal previous/next chapter controls.
- Static matrix confirmed all five chapter-book files have previous/next controls, direct modal chapter opening, URL hash sync, and the shared MN-style intro copy.
- Script parse passed for all five chapter-book files.
- Rendered spot-check passed for MN, AMS, MH, PD, and Pharm: selecting Next inside the open chapter modal now changes the modal content, keeps the TL;DR tab active, enables Previous, and syncs the URL hash.
- No ATI educational content was added or rewritten.

Next Recommendation:

- Treat the chapter-book modal navigation shell as current-complete, then continue with a hub-shell parity pass across the five books. Keep Templates pinned and Flashcards paused unless the user explicitly reopens those surfaces.

## Hub-Shell Parity Closeout: 2026-07-05

Current mode: DESIGN-CANON / HOLD-CONTENT.

Status:

- Hub-shell parity is current-complete for this pass.
- Templates remain pinned as the approved template design canon.
- Flashcards remain paused by user direction.
- No ATI educational content, cards, prompts, templates, or enrichment were added.

Action completed:

- Normalized AMS Hub to the shared MN/MH/PD/Pharm hub shell vocabulary: `topbar-home`, `topbar-brand`, `topbar-brand-mark`, and `hero-eyebrow`.
- Preserved AMS subject identity, accent color, counts, and learner-facing copy.
- Kept the approved four-stat hub pattern only: Chapters, Units, Worked Templates, Starter Cards.
- Kept the lower template-type navigation section, because that is separate from the redundant Template Types stat box and matches the MN-style hub shell.

Validation performed:

- Static matrix confirmed all five Hub files expose the shared topbar, hero, stat row, pickup panel, review queue, primary tools, unit map, template-type navigation, and storage/footer shell pieces.
- Static count check confirmed all five Hub stat rows use exactly: Chapters, Units, Worked Templates, Starter Cards.
- Redundant Template Types stat is absent across the Hub stat rows.
- JavaScript parse check passed for all five Hub files.
- Rendered AMS Hub spot QA passed in local browser preview: shared topbar, four stat cards, pickup panel, and no old AMS-only hub class hits.

Next Recommendation:

- Treat Hub, Book, and Templates shells as current-complete for this design-canon pass. Do not reopen Templates or Flashcards unless the user reports a concrete shell defect or explicitly resumes that surface. The next best action is a final five-book shell matrix and then commit/push the current design-shell batch when approved.
