# AMS Prototype MN Canon Audit

Status: Design-canon / HOLD-CONTENT audit only.
Date: 2026-07-04.
Scope: Current AMS prototype compared against the MN design canon. This document does not add ATI educational content and does not approve rollout to MN or other books.

Continuity notice (2026-07-15): this file preserves AMS audit evidence and batch history; it is not the current task selector or an independent source of required canon. Private master Build Guide Part 49 consolidates the accepted current conclusions from this audit and is the complete migration reference. Heartbeat continuation has resumed from the current MH queue under Part 49; all older AMS-only heartbeat recommendations in this audit are historical. Update this file only when AMS comparison evidence, audit status, or rollout readiness changes.

Clipping-readiness update (2026-07-17): all 24 MN, MH, and AMS template-family items plus the MN, MH, and AMS landing shell/sidebar/modal chrome items have completed objective clipping QA. The AMS shell passed eight repeated desktop, split-pane/tablet, and phone states with no product repair: page and modal horizontal overflow stayed at `0px`, all eight collapsed headers and their visible children stayed contained, both opened responsive sidebars measured `280px` with `0px` horizontal row/control overflow, and the representative Basic Concept modal's title, labels, buttons, navigation, and borders stayed inside their containers. Tablet and phone modal-body vertical scrolling was intentional; the existing phone example-name line clamps behind the open modal were excluded by the clipping gate. Final cross-book integrity also passed with unchanged MN/MH/AMS payload hashes, parseable scripts, 352 cards and 352 unique IDs, canonical family order/counts, exact standalone/comparison parity, required breakpoints/landmarks, and complete responsive summaries. The clipping automation is paused, and user visual approval remains pending. This audit remains supporting evidence; private master Part 98 and the current overlay select the waiting state.

Retrospective sidebar update (2026-08-14): fresh current-payload desktop, tablet, and phone measurements confirm that AMS now shares MN's fixed-sidebar geometry, `500` legend weight, scrollbar treatment, and `0px` horizontal overflow. The responsive drawer now synchronizes its menu control and panel through `aria-controls`, `aria-expanded`, `aria-hidden`, and inert closed state; opening focuses sidebar search, while overlay or Escape closure restores focus to the menu control. Both responsive viewports repeated identical closed/open/Escape measurements at least `300ms` apart. This is automated objective evidence, not user visual approval; private master Part 183 and the current overlay advance the active retrospective item to Batch 3 modal-top QA.

Retrospective modal-top update (2026-08-14): fresh current-payload rendering confirmed a stable AMS-only modal-top mismatch against the accepted MN/MH role contract. AMS now matches the desktop `127.99px` header, `28/32/22px` header padding, `34/37.4px` title, `8px` action gap, top-aligned example row, `20px` checkbox, `30px` Print control, and `37.5px` mode toggle; full-screen behavior now begins at `600px`, and the phone body uses `20/18/40px` padding. Repeated desktop, tablet, and phone measurements show zero overflow. Open, Filled/Blank, same-family Previous/Next, Escape close, and reopen pass on the current AMS payload, whose 84 unique cards and `21/8/1/16/4/16/17/1` family counts remain unchanged. This is automated objective evidence, not user visual approval; private master Part 184 and the current overlay advance the active retrospective item to Batch 4 shared box-system QA.

Retrospective shared box-system update (2026-08-14): all 84 current AMS cards were rendered in Filled and Blank modes at `1440 x 1000`, `768 x 1000`, and `390 x 844`, producing 504 stable card-mode states with no activation or card-ID errors. No AMS-wide shared primitive mismatch met the correction gate, so the product file was unchanged in Batch 4. Existing family-specific title-strip, descendant typography, gap, and corner measurements remain evidence for the dedicated A1/A3/A5, A7/A9, and A11/A13/A15 batches. Greater-than-1px readings were limited to the exact established horizontal procedure and vertical medication relationship connectors, not clipped text or controls. This is automated objective evidence, not user visual approval; private master Part 185 and the current overlay advance the active retrospective item to Batch 5 A1/A3/A5 QA.

Retrospective A1 update (2026-08-15): every one of AMS's 21 A1 cards was rendered in Filled and Blank modes at `1440 x 1000`, `768 x 1000`, and `390 x 844`, producing 126 stable card-mode states. A scoped A1 correction now matches MN's 3/2/1 track pattern, `14px` gap and corners, `280px` desktop Filled minimum, `120px` Blank minimum, and `11px 16px` direct-title padding while preserving AMS typography, content, IDs, counts, links, storage, order, and accent. Search, same-family navigation, mode switching, Print presence, close/reopen behavior, scripts, payload parity, and visible-overflow checks pass. AMS retains 84 unique cards and `21/8/1/16/4/16/17/1` family counts. Automated QA remains objective evidence, and the user separately visually approved the current AMS A1 comparison on `2026-08-15`; private master Part 188 and the current overlay advance the next small audit to Batch 5C MH A3 compared with MN.

Retrospective A3 update (2026-08-15): every one of AMS's eight A3 cards was rendered in Filled and Blank modes at `1440 x 1000`, `768 x 1000`, and `390 x 844`, producing 48 stable card-mode states. A scoped A3 correction now matches MN's `18px` metadata-to-first-box gap, `14px` direct corners, `11px 16px` direct-title padding, `14px 16px 16px` direct content padding, `16px`/`25.6px` direct body typography, `16px`/`14px` Considerations radius/padding, `11px` nested corners, `9px 14px` nested titles, and `12px 14px 14px` nested content. Search, Filled/Blank switching, same-family Previous/Next, Print presence, close/reopen behavior, reversible progress, scripts, payload parity, and visible-overflow checks pass. The established `14px` complications connector extension and visible Blank-mode writing lines were excluded as intentional geometry rather than clipping. AMS retains 84 unique cards, `21/8/1/16/4/16/17/1` family counts, 76 resolving chapter links, and eight prototype fixtures; the current standalone and comparison payloads share SHA-256 `665099d4ed16c59ada4a2190fce92bf2361930b65aab3a614c3bfb7e7a9c307d`. Automated QA remains objective evidence; the user separately visually approved the corrected current AMS A3 comparison on `2026-08-15`, as recorded in private master Part 194. The next focused audit is MH A5 Growth and Development compared with MN.

Retrospective A3 short-box correction update (2026-08-15): focused user review reopened AMS A3 because the prototype Indications card stretched to `496.90625px`, leaving `361.71875px` of empty interior below its final line. AMS A3 Indications and Outcomes now use `align-self:start; height:auto`, preserving the established equal-row procedure grid and spanning Considerations relationship while allowing short direct cards to use natural height. Repeated after-state measurements reduce the same Indications card to `135.1875px`, with `133px / 133px` client/scroll height, `498px / 498px` client/scroll width, and `17px` natural bottom space. All eight A3 cards again passed Filled and Blank at desktop, tablet, and phone for 48 stable states with zero text clipping and zero structural-box clipping. AMS retains 84 unique cards, exact family counts `21/8/1/16/4/16/17/1`, 76 resolving chapter links, and eight prototype fixtures; product/comparison parity is SHA-256 `3935b72377252f336f5199909f1b41b05a72979eef79fad2d8628dbad2920077`. This repaired state is objectively corrected and pending fresh user visual approval; MH A5 must not begin until that confirmation is recorded. Automated QA is not user approval.

Retrospective A3 stack-flow correction update (2026-08-16): fresh user review found that Part 195 moved the unused equal-row space outside the compact cards, leaving a `144.1875px` gap between the `79px` GI Endoscopy `Indications` and `Interpretation of Findings` cards in the split-pane comparison. AMS A3 now groups those two official roles in a natural-height left stack with the canonical `14px` internal gap, retains the wide two-column/spanning-Considerations relationship and lower complication/intervention connector, and explicitly resets stacked A3 rows to automatic sizing. The same reported state now measures exactly `14px`; all eight A3 cards pass Filled and Blank at `1440 x 1000`, `768 x 1000`, and `390 x 844` for 48 stable states with an exact `14px` role gap, zero text/structural-box overflow, and no activation failure. AMS retains 84 unique cards, exact family counts `21/8/1/16/4/16/17/1`, all eight A3 IDs, and its required storage keys; product/local/HTTP payload parity is SHA-256 `68e27f00f3a566a3b18254ec33181b3adc74f27d76e0c8208e6d8cb0abe3b49b`. This repaired state remains pending fresh user visual approval; MH A5 must not begin until that confirmation is recorded. Automated QA is not user approval.

Retrospective A3 stack-flow approval update (2026-08-16): the user reviewed the Part 197 comparison and confirmed that the current `14px` Indications-to-Interpretation correction fixed the issue. AMS A3 is now objectively passed and user visually approved in its current stack-flow state. MH A5 remains the next queued batch and was not started while recording this approval.

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

## Part 205 — AMS A5 Spacing-Consistency Evidence

- Status: objectively passed; fresh user visual approval pending.
- Scope: design-only A5 Growth and Development spacing repair in `Elevated ATI AMS Templates.html`; the one prototype fixture, learner content, counts, IDs, storage, links, order, and AMS accent remain unchanged.
- Before: `14px` metadata boundary at every width; at `600px` and `390px`, the visible outer group boundary remained `20px` while every stacked child and Health Promotion boundary was `12px`.
- After: `18px` metadata boundary at every width; `20px` outer/connector spacing above `600px`; exact `12px` outer, parent-to-child, and child-to-child boundaries at `600px` and below. Four/two/one-column transitions and connector visibility remain intact.
- Rendered evidence: Filled and Blank at `1440`, `1101`, `1100`, `768`, `601`, `600`, and `390px`; 14 stable states with two identical readings more than `300ms` apart and zero card/page horizontal overflow.
- Payload evidence: AMS product/local SHA-256 `a0c94f188c86e9e5d16a094a332e4d921228eb0e8a8f2679224764a624111581`; MN product/local SHA-256 `e39b030ab7b695ff7641b181addcb8cbb28294c91d9a96ec09f50bbb3039e512`; comparison inner iframe cache key `ams-a5-spacing-fix`.
- Next gate: user visual review of the repaired AMS-versus-MN A5 comparison before A7 begins.

## Part 206 — AMS A5 Approval and A7 Spacing Evidence

- AMS A5 is objectively passed and user visually approved.
- AMS A7 scope: design-only metadata spacing in `Elevated ATI AMS Templates.html`; no learner content, Medication structure, connector, card, count, ID, link, storage key, order, or accent changed.
- Before: all 16 cards used a stable `14px` metadata-to-Purpose boundary. The existing `14px` Purpose-to-body/body-box spacing and `10px` Purpose inset/inner gap were already uniform.
- After: metadata-to-Purpose is `18px`; all other accepted A7 spacing roles remain unchanged.
- Rendered evidence: all 16 cards, Filled and Blank, at `1440`, `768`, and `390px`; 96 stable post-repair states with repeated readings and zero card/page horizontal overflow.
- Integrity: one script, 84 cards/unique IDs, exact counts `21/8/1/16/4/16/17/1`, storage keys, HTTP 200, `git diff --check`, and product/local/HTTP SHA-256 `fcc3575ee774d4871832eacdcf2a0117178fd89e88a3d30554b3473764ae93c4` pass.
- Next gate: user visual review of the `ams-a7-spacing-fix` comparison before another family begins.

## Part 207 — AMS A3 Responsive Connector Evidence

- AMS A3 now preserves the official Potential Complications-to-Nursing Interventions connector at every responsive state: horizontal across the existing `14px` two-column gap and vertical `3px × 14px` across the stacked `14px` gap.
- Representative Filled/Blank wide/narrow measurements and the live AMS-versus-MN split comparison pass with centered geometry and zero overflow. AMS product, temporary, and HTTP-served payloads are byte-identical at SHA-256 `016c9c601aa45446993a7eaa1ca5ae3f8d6c8723bd0c4d3171c1d876f975c056`.
- Fresh user visual approval of this retroactive A3 repair is pending. AMS A7 remains objectively passed and paused at its prior visual gate until A3 is approved or the user reports a remaining defect.

## Part 211 — AMS A3 Full-Family Connector Regression Evidence

- Status: objectively passed after full-family regression; fresh user visual approval remains pending and is not inferred from automation.
- Scope: all eight AMS A3 Diagnostic Procedure cards, including the retained prototype fixture, in Filled and Blank. No AMS product correction was required and no learner content, official role, card, count, ID, link, storage key, order, or accent changed.
- Rendered evidence: `1440 x 1000`, exact `821px/820px` card-width transition at `935/934 x 1000`, `901 x 1000`, exact `900 x 1000` procedure-family viewport breakpoint, `768 x 1000`, and `390 x 844`; 112 states with two identical readings at least `270ms` apart.
- Geometry: wide cards retain the official two-column relationship, exact `14px` boundary, centered `14px x 3px` horizontal bridge, and matched lower-box centers. The exact `820px` card width and all narrower states retain the official stacked order and centered `3px x 14px` vertical bridge across the exact `14px` gap.
- Completeness: `18px` metadata boundary, Student Name/Procedure Name/Review Module Chapter roles, controls, `1 / 8` through `8 / 8` navigation, diagnostic left-stack order, typography, `14px/11px` corners, bottom endpoints, and card/content/page/modal overflow checks pass.
- Integrity: one script parses; 84 cards and 84 unique card IDs remain with exact counts `21/8/1/16/4/16/17/1`; all eight A3 IDs, 76 current chapter links, and storage keys remain; direct runtime warning/error logs are empty; `git diff --check` passes.
- Payload evidence: AMS product, temporary, and HTTP-served SHA-256 remains `016c9c601aa45446993a7eaa1ca5ae3f8d6c8723bd0c4d3171c1d876f975c056`; the MN reference remains byte-identical across product/temporary/HTTP at `eec09db6a7e6488ac0db5291eb3005378311fb8cc43c2ab8d3f8f1c262c8abda`.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a3-official-connector-fix-ams-batch2`; fresh inner iframe cache keys load both repaired A3 cards, and split-pane geometry repeats centered `3px x 14px` connectors across exact `14px` gaps.
- Next objective queue item: Batch 3, MN A7 only. AMS A3 and AMS A7 visual approvals remain pending for the user's return.

## Part 213 — AMS A3 Behind-Box Connector Evidence

- Fresh user review rejected the front-layer `3px x 14px` stacked connector and restored the intended illusion: the bridge extends beneath both boxes and sits behind their surfaces.
- AMS A3 now uses the existing `10px` overlap token in both orientations. Wide: centered `34px x 3px`, `right:-24px`, `z-index:-1`. Stacked: centered `3px x 34px`, `bottom:-24px`, `z-index:-1`. The box backgrounds hide the 10px penetration at both ends, leaving the visible segment flush across the exact `14px` gap.
- All eight AMS A3 cards passed Filled and Blank at `935/934px`, the exact `821px/820px` card-width transition: 32 twice-stable states with correct orientation, exact visible gap, centered geometry, official order, and no objective content/page overflow. The intentional hidden pseudo-element overlap is the only box scroll-boundary extension.
- The same A3-only correction and full-family validation passed in MN and MH, for 116 total cross-book states. A9 and A13 were not changed.
- Current AMS product/local/HTTP SHA-256 is `54c58f6c872afa41fce7cf3d2872b73ab809ad3bde29756776476880478ecea1`. Direct runtime logs are empty, comparison cache keys are fresh, and `git diff --check` passes.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a3-connector-behind-boxes`. Fresh user visual approval remains pending. The retrospective heartbeat remains paused and MN A7 has not begun.

## Part 215 — AMS A5 Normalized Gap Evidence

- The user superseded the previously approved A5 `20px/12px` exception with the common cross-template spacing hierarchy. AMS A5 now retains the accepted `18px` metadata boundary and uses `14px` for same-level section, parent-to-child, child-to-child, responsive stacked, and visible connector-strip relationships.
- The one AMS A5 prototype fixture passed Filled and Blank at `1440`, `1101`, `1100`, `768`, `601`, `600`, and `390px`. All 14 states repeated identically, retained the 4/2/1 relationship tracks, showed the connector only above `600px`, measured exact `14px` visible boundaries, and had zero card/box/page overflow.
- Cross-book companion evidence covers seven MN and six MH A5 cards for 196 total twice-stable states. Learner content, official labels/relationships, card counts, IDs, links, storage keys, order, and AMS identity remain unchanged.
- AMS product, temporary, and HTTP-served payloads are byte-identical at SHA-256 `2bf9355dee1525c13a8d1b447d1c3e811d61e2ecdbbfeeabb8a468fb3e3bc679`; scripts, 84 cards/unique IDs, counts `21/8/1/16/4/16/17/1`, links, storage, direct runtime logs, and `git diff --check` pass.
- Current three-pane comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a5-gap-14-normalization-2`. Fresh user visual approval is pending; MH A7 has not begun.

## Part 216 — AMS A5 User Visual Approval

- The user reviewed the Part 215 normalized three-pane comparison and confirmed that everything appears in order. AMS A5, together with MN and MH A5, is objectively passed and user visually approved under the `18px / 14px / 10px` role hierarchy.
- No AMS product or learner-facing file changed in this approval record. Part 215's seven-width Filled/Blank evidence, exact payload SHA-256 `2bf9355dee1525c13a8d1b447d1c3e811d61e2ecdbbfeeabb8a468fb3e3bc679`, counts, unique IDs, links, storage, scripts, and runtime evidence remain current.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a5-gap-14-normalization-2`. MH A7 has not begun and requires a separate explicit instruction.

## Part 219 — AMS A7 Typography-Role Repair

- Cross-book role inventory confirmed that AMS A1, A3, and A5 already match the MN typography roles. AMS A7 body text, rendered descendants, metadata labels/values, and compact Purpose titles also matched; the remaining defect was limited to the Purpose label weight and the seven regular medication-body title stacks.
- Before repair, all 16 AMS A7 cards rendered `Purpose of Medication` at weight `900` instead of the shared metadata-label weight `700`. Their regular body titles incorrectly inherited the compact Purpose stack: `17.25px` line height and `10px` vertical padding instead of the primary `24px` line height and `11px` padding.
- One A7-only selector split preserves Purpose at DM Serif Display `15px / 17.25px` with `10px 16px` padding while restoring regular body titles to `15px / 24px` with `11px 16px` padding. The Purpose label now uses DM Sans `10px / 16px / 700`, `1.4px` letter spacing, uppercase. AMS corners and layout were deliberately not changed in this typography batch.
- All 16 cards passed Filled and true Blank at `1440` and `390px`: 64 twice-stable post-repair states with zero typography-role failure, Blank answer leakage, or overflow. A1/A3/A5 representative desktop/mobile regression also passed.
- One inline script parses; AMS retains 84 cards and unique IDs with counts `21/8/1/16/4/16/17/1`, current links and storage keys. Product, temporary, and HTTP-served SHA-256 is `05e930cf58e77ff4f52a590688cad1370cc449d5e9b78632a5a714335c2bf9a2`; `git diff --check` passes.
- Current three-pane comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a7-typography-uniform`. Fresh user visual approval of the role-based typography is pending; MH A9 did not begin.

## Part 220 — AMS A7 Typography User Approval

- The user reviewed the three-book Part 219 comparison and confirmed that the typography appears in order. AMS A7 typography is objectively passed and user visually approved against the MN/MH role system.
- The approved state retains the compact Purpose titles, regular `15px / 24px` body-title role, DM Sans `16px / 25.6px` body text, semantic strong weights, and the corrected `Purpose of Medication` label role without flattening the intentional hierarchy.
- No AMS product or learner-facing file changed in this approval record. Part 219's all-card Filled/Blank evidence, exact SHA-256 `05e930cf58e77ff4f52a590688cad1370cc449d5e9b78632a5a714335c2bf9a2`, script/count/ID/link/storage integrity, payload parity, and `git diff --check` remain current.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=a7-typography-uniform`. MH A9 has not begun.

## Part 223 — AMS A9 Responsive Connector Evidence

- The cross-book A9 correction now preserves the official Potential Complications-to-Nursing Interventions relationship in AMS at every responsive state. Wide AMS keeps a centered `30px x 3px` long bridge with an `8px` hidden overlap beneath each box plus a `14px x 3px` visible gap segment. Stacked AMS uses the corresponding centered `3px x 30px` long bridge and `3px x 14px` gap segment.
- All four AMS A9 cards passed Filled and Blank at `1280`, exact `935/934`, and `390px`: 32 twice-stable states with the correct horizontal-to-vertical transition, exact `14px` visible gap, centered geometry, official order, and zero objective overflow or Blank leakage.
- The single inline script parses; AMS remains at 84 cards and unique IDs with counts `21/8/1/16/4/16/17/1`. Product, temporary, and HTTP-served payloads are byte-identical at SHA-256 `5eab823be0a69efba4c5aabfb5e77cc1cc53f995253f89f4f627cea0b067e4ed`; `git diff --check` passes.
- This cross-book design-only repair does not begin AMS A11, alter learner content, or change labels, boxes, counts, IDs, links, storage keys, order, or AMS identity.

## Part 224 — AMS A9 Connector Border-Edge Evidence

- Magnified user review exposed a one-pixel layering defect shared by the A9 visible gap segment: `right:-14px` / `bottom:-14px` positioned its first row over the source card's `1px` border because the pseudo-element is positioned from the padding edge.
- AMS A9 now uses `right:-15px` wide and `bottom:-15px` stacked while retaining an exact `14px` visible segment and the existing `8px` behind-box overlap layer. The cap meets the outer border edge without painting over the border.
- All four AMS A9 cards passed Filled and Blank at `1280/935/934/390px`: 32 twice-stable states with correct orientation, centered geometry, exact `14px` gaps, `-15px` visible-layer offsets, and zero objective content/page overflow.
- The single inline script parses. AMS product, temporary, and HTTP payloads are byte-identical at SHA-256 `8e0206c92d7a1c15889188c82d052eff1ea494d74d97a2ea5f5c2b1e0f4ced0e`; `git diff --check` passes. No learner content or identity-bearing data changed.

## Part 242 — AMS A15 Concept Analysis Canon Evidence

- Status: objectively passed; fresh user visual approval pending.
- Before: the retained A15 prototype used `12px` metadata spacing, compact `38.25px / 17.25px` banners, `10px` corners, `24px` body line-height, rigid `112px/240px` Filled minimums, collapsed `40.25px` stacked Blank boxes, and `0px` trailing margin. The existing `14px` peer gap and exact `721/720px` breakpoint were already correct.
- After: AMS A15 uses the accepted `18px` metadata boundary, `14px` gaps/corners, DM Serif Display `15px / 24px` and `47px` title bands, DM Sans `16px / 25.6px / 400` body roles, natural Filled heights, `120px` Blank areas, equal wide pairs, exact breakpoint, and the approved `24px` card margin plus `40px` modal padding endpoint.
- Rendered evidence: Filled and Blank at `1440`, `768`, exact `721/720`, and `390px`, plus both print modes; 12 twice-stable states with official five-box order, correct responsive geometry, Blank hiding, endpoint space, and zero modal/card/grid horizontal overflow.
- Integrity: one script, 84 cards and unique card IDs, exact counts `21/8/1/16/4/16/17/1`, one A15 fixture, 76 links, storage, product/temporary/HTTP SHA-256 `2c4dbf8001a209b367d99a60b78825b2aa80ca654d58ea87a33f98b185a54a33`, HTTP `200`, and `git diff --check` pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-canon-fix`. Fresh user visual approval is pending; no later batch began.

## Part 243 — AMS Cross-Book Modal Top-Stack Evidence

- AMS now shares MN/MH's modal title reservation: `100.4px` minimum title row and `165.4px` minimum banner at regular widths; `104.8px` title row and `135.8px` banner on phones. The minimum covers the two-line title role and the phone's two-line kicker role while allowing longer titles to grow naturally.
- AMS's missing split-pane/tablet Worked Example inset is repaired with the same `18px` modal-card padding already used by MN/MH from `601px` through `900px`. The banner-to-header boundary is now exact across all three books: `28px` at `1440`, `46px` at `768`, and `20px` at `390px`.
- Filled/Blank banner geometry is stable. AMS retains 84 cards and counts `21/8/1/16/4/16/17/1`; its script, IDs, links, storage, and diff integrity pass. AMS product/temporary parity is exact at SHA-256 `7261da7516f5e98cc9f779c861d7fe81d4de961512fae05efd8e1fd3a1000e3b`.
- Current exact-payload comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=top-stack-uniform-final`. Fresh user visual confirmation of the shared top stack remains pending; no later batch began.

## Part 246 — AMS A15 Official Two-Row Metadata Evidence

- The rendered AMS A15 metadata defect was one extra `Review Module Chapter` pair. The official A15 Concept Analysis structure and established MN/MH canon require only `Student Name` and `Concept Analysis`.
- The AMS metadata builder now appends and populates the source row only for non-Concept-Analysis families. This is a renderer-only correction; learner content, links, titles, official five-box structure, counts, IDs, storage, accent, and AMS identity are unchanged.
- Filled and Blank both render the exact two official pairs in order. AMS and MN A15 metadata boxes each measure `83.296875px`. Other AMS families retain Review Module Chapter because the guard is scoped to `concept-analysis`.
- One script parses; AMS remains at 84 cards and exact family counts `21/8/1/16/4/16/17/1`, with intact runtime IDs, links, and storage. Product and temporary payloads match at SHA-256 `10fecff338140f04a5ee3f43bbebf70d6fcbb9b2f47f65b9c92b2641f39626c2`; HTTP is `200`; `git diff --check` passes.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-official-meta-final`. AMS A15 is objectively passed and pending fresh user visual approval of the corrected metadata; no later batch began.

## Part 247 — AMS A15 User Visual Approval

- The user reviewed the Part 246 comparison and confirmed that everything appears in order. AMS A15 is objectively passed and user visually approved, including the official `Student Name` plus `Concept Analysis` metadata pair, top stack, five-box structure, typography, spacing, corners, Blank behavior, breakpoint, and endpoint.
- No AMS product file changed while recording approval. Part 246's rendered and integrity evidence remains current, including exact product/temporary SHA-256 `10fecff338140f04a5ee3f43bbebf70d6fcbb9b2f47f65b9c92b2641f39626c2`.
- Approved comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a15-official-meta-final`. The final cross-book regression has not begun; content population remains paused.

## Part 248 — Final Regression AMS Findings

- The final representative regression measured AMS at `1440`, `768`, and `390px`, first and last card of every current family, Filled and Blank. Across 84 AMS states, peer row/column gaps remain exact `14px`, endpoint padding is at least `40px`, and content/modal horizontal overflow is zero.
- The run confirms A1/A3/A5/A7/A15 retain their documented accepted roles. It also establishes that final AMS canon readiness is not complete: A9 Nursing Skill and A13 Therapeutic Procedure retain a `12px` metadata-to-grid boundary, while A11 System Disorder retains `14px`, rather than the accepted `18px` boundary.
- AMS A13 also retains a legacy connector. Wide states use only a `14px x 3px` segment at `right:-14px`, `z-index:0`, rather than the accepted long behind-box bridge plus border-edge layer. At `768px` and `390px`, the relationship stacks but that segment remains horizontal instead of rotating to a centered vertical connector. This is objective evidence, not user visual approval.
- Part 248 repaired MN A13 skeleton outliers only; it did not alter AMS. AMS remains byte-identical to its Part 247 product/temporary payload at SHA-256 `10fecff338140f04a5ee3f43bbebf70d6fcbb9b2f47f65b9c92b2641f39626c2`, with 84 cards, exact counts `21/8/1/16/4/16/17/1`, unique IDs, intact links/storage, parsed script, HTTP `200`, and passing `git diff --check`.
- The next AMS work is a gated retrospective family pass, beginning with one family only after the current MN A13 visual review. Content population remains paused. ATI source support used: none; design-only change. Nothing was staged, committed, or pushed; all four automations remain paused and unchanged.

## Part 249 — AMS Retrospective Gate Advanced to A9

- The user visually approved the separate MN A13 repair from Part 248. The prerequisite visual gate is therefore complete; no AMS product file changed in this approval record.
- AMS A9 Nursing Skill is now the next permitted retrospective family. Its measured `12px` metadata boundary remains an objective defect against the accepted `18px` role. AMS A11 and A13 remain later, separate gates and must not be combined into A9 without explicit authority.
- Content population remains paused. ATI source support used: none; design-only change. Nothing was staged, committed, or pushed; all four automations remain paused and unchanged.

## Part 250 — AMS A9 Metadata Boundary Evidence

- Before repair, every AMS A9 Nursing Skill card measured a stable `12px` metadata-to-grid boundary in Filled and Blank at `1440`, exact `935/934`, `768`, and `390px`. The accepted cross-book metadata role is `18px`.
- One A9-scoped selector now sets `18px`. No learner text, official relationship, box, card, count, ID, link, storage key, order, accent, AMS identity, connector selector, or later family changed.
- All four A9 cards pass 40 twice-stable post-repair states with exact `18px` metadata, `14px` peer gaps, `14px/11px` corners, DM Serif Display `15px / 17.25px / 400` title roles, DM Sans `16px / 24px / 400` body roles, endpoint space, and zero card/grid/modal overflow.
- Connector regression passes unchanged. Wide `935px` uses the two-column `821px` card, exact `14px` box gap, `30px x 3px` bridge at `z-index:-1`, and `14px x 3px` edge segment at `z-index:0`. Stacked `934px`, `768px`, and `390px` use centered `3px x 30px` and `3px x 14px` layers across the exact `14px` gap.
- One AMS script and one comparison script parse. AMS retains 84 cards and unique IDs, exact family counts `21/8/1/16/4/16/17/1`, four A9 cards, 76 links, and storage key `atiams_templates_progress`. Product, temporary, and HTTP payloads are byte-identical at SHA-256 `ae3f940c09039a29eeaf61f53745c2d39290e93e9588f489f6a7385f0bb5887a`; HTTP is `200`; `git diff --check` passes.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a9-meta-18-final`. AMS A9 is objectively passed and pending fresh user visual approval. AMS A11 and A13 remain separate gates. Content population remains paused. ATI source support used: none; design-only change.

## Part 251 — AMS Global Endpoint Evidence

- AMS no longer relies on per-family endpoint exceptions. Every direct modal example card now receives the shared `24px` screen margin before the `40px` shell padding, yielding the exact `64px` endpoint used by MN and MH; print resets the added margin to `0`.
- AMS A9's first and last cards join the full cross-book recurrence matrix: all eight families, first/last examples, Filled/Blank, and `1440/768/390px` widths passed `276/276` twice-stable states with exact endpoint geometry and no horizontal overflow.
- AMS retains 84 cards and counts `21/8/1/16/4/16/17/1`; its script parses and product/temporary payloads are byte-identical at SHA-256 `317a1e6433ddfc3cd78680fbc3cc5e92a9f272562720d6795b87ff94a6058187`. HTTP and `git diff --check` pass.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=global-endpoint-64-final`. AMS A9 remains objectively passed and pending fresh user visual approval; AMS A11 and A13 remain separate later gates. Content population remains paused. ATI source support used: none; design-only change.

## Part 252 — AMS A9 Full Role Repair And Resumable Audit Gate

- User review correctly rejected the earlier parent-level typography pass. Stable before evidence found primary A9 strips at `15px / 17.25px`, `10px 16px`, `38.25px`; nested strips at `13.5px / 21.6px`, `10px 16px`, `42.59375px`; direct copy at `16px / 24px`; nested copy at `13px / 19.5px`; and a `10px` Considerations inset.
- One cohesive A9-only correction now matches the accepted MN role system: primary strips `15px / 24px`, `11px 16px`, `47px`; nested strips `13.5px / 21.6px`, `9px 14px`, `40.59375px`; all rendered direct/nested descendants DM Sans `16px / 25.6px / 400`; nested content `12px 14px 14px`; group inset/gap/corners `14px / 10px / 16px`; direct/nested corners `14px / 11px`.
- All four cards passed Filled and Blank at `1440`, exact `935/934`, `768`, and `390px`: `40/40` twice-stable states. Metadata remains `18px`; peers remain `14px`; overflow is zero; the two-layer bridge is horizontal through `935px` and centered vertical at `934px` and below; the root endpoint retains `24px` card margin plus `40px` shell padding.
- AMS integrity passes at product/temporary SHA-256 `80f79405a5824d31df5f731c20ae36cd0e7cdfe9f296607b182ecd67c9885b15`: one parsed script, `84` cards and unique IDs, exact counts `21/8/1/16/4/16/17/1`, four A9 cards, `76` links, HTTP `200`, and clean diff whitespace.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a9-typography-role-final-2`. Fresh user visual approval remains pending. The next objective family is AMS A11; AMS A13 remains later. Runs use the private master Part 252 resumable ownership/recovery contract. Content population remains paused. ATI source support used: none; design-only change.

## Part 253 — AMS A11 Full Canon Repair And Objective Pass

- Before repair, all 16 A11 cards retained a `14px` metadata boundary, compact `38.25px` title strips, `10px/8px` corners, legacy group padding, a narrow fractional outer rail, and shrinkable Safety rows. Official section identities and order were intact.
- One A11-only correction now applies the accepted `18px` metadata boundary; `14px/10px` major/nested gaps; `14px/16px/11px` direct/group/nested corners; `15px / 24px` direct and `13.5px / 21.6px` nested title roles; `16px / 25.6px` direct and Patient-Centered Care descendants; and `13px` dense Assessment, Safety, and Complications roles.
- Wide cards use the `2fr/1fr` outer division, three equal top columns, and two equal content-aware Safety rows. The exact card-width transition is `935/934px`; stacked Safety uses natural flow with `14px 14px 16px` padding.
- All 16 cards passed true Filled and true Blank at seven responsive widths: `224/224` twice-stable states. Structure remains exactly 3 top, 4 Assessment, 1 Complications, and 5 Patient-Centered Care boxes with the official order, dashed `120px x 18px` Student Name line, no Blank leakage, zero overflow, and the `24px + 40px` endpoint. Print passed `32/32` states with `0px` print endpoint guards.
- AMS remains at `84` cards and unique source IDs with exact counts `21/8/1/16/4/16/17/1`, `16` A11 cards, `76` resolving links, and unchanged storage. Product/temporary SHA-256 is `4600ece245a0d170d2be9291b067fae984b0c8923d96be404ae15907ee8ea04d`; scripts parse, HTTP is `200`, and `git diff --check` passes.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a11-canon-fix`. AMS A11 is objectively passed and pending fresh user visual approval. AMS A13 is next. Content population remains paused. ATI source support used: none; design-only change.

## Part 254 — AMS A13 Screen Canon Repair / In-Progress Print Gate

- Before repair, all 17 A13 cards used a 12px metadata boundary, compact title roles, 8px direct/group corners, 10px Considerations padding, 13px / 19.5px nested copy, and only a front-layer horizontal 14px x 3px connector.
- One A13-only screen correction now applies 18px metadata; 14px/10px peer/nested gaps; 14px/16px/11px direct/group/nested corners; direct 15px / 24px, 11px 16px, 47px title stacks; nested 13.5px / 21.6px, 9px 14px, 40.59375px stacks; DM Sans 16px / 25.6px / 400 rendered descendants; and a 14px Considerations inset.
- The official connector now uses a 34px x 3px long behind-box layer plus 14px x 3px border-edge segment wide, and centered 3px x 34px plus 3px x 14px layers stacked at card width 820px and below. All 17 cards passed Filled/Blank at 1440, exact 935/934, 768, and 390px: 170/170 twice-stable screen states with exact gap, geometry, endpoint, and zero overflow.
- Print remains unresolved. The global body.printing-modal child selector hides the page ancestor containing the modal, yielding zero print rects. The one-correction rule prevented a second repair this run, so AMS A13 is **IN_PROGRESS**, not objectively passed.
- Integrity passes for the screen checkpoint: AMS SHA-256 84a885863f18c02d1dbd96395b1ad537b21fc8ad309606fcf387203a8128c5c9, one parsed script, 84 cards/unique IDs, exact counts 21/8/1/16/4/16/17/1, 17 A13 cards, 80 resolving static links, unchanged storage, HTTP 200, and clean diff whitespace.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a13-canon-fix. Fresh user visual approval remains pending. Content population is paused. ATI source support used: none; design-only change.

## Part 255 — AMS A13 Print Repair And Objective Pass

- The global AMS modal-print guard now preserves the nested page/main/modal ancestor chain and hides only its non-modal siblings. Retained page and main wrappers become block layout with zero print margin/padding, while existing modal/card print rules remain intact.
- All 17 A13 cards passed Filled and Blank print validation: 34/34 twice-stable states with nonzero geometry, exact 5 direct and 2 nested boxes, official relationship order, hidden controls, transparent Blank answers, 0px card margin/body padding, and zero card/body/document overflow.
- The full screen matrix was repeated after the print correction: 170/170 twice-stable Filled/Blank states at 1440, exact 935/934, 768, and 390px retain the accepted A13 spacing, corner, typography, connector, endpoint, and overflow contract.
- AMS integrity passes at SHA-256 ad7dae1645a144b7baf0a6e4900e1b8507021074c081d6ff18ba9487e6eb1aae: one parsed script, 84 cards/unique IDs, exact counts 21/8/1/16/4/16/17/1, 17 A13 cards, 80 resolving static links, unchanged storage, HTTP 200, and clean diff whitespace.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a13-print-canon-final. AMS A13 is objectively passed and pending fresh user visual approval. MN A1 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 258 — AMS A1 Objective Regression Pass

- All 21 AMS A1 records, including the hidden prototype fixture, passed true Filled and Blank screen validation at `1440`, exact `901/900`, `768`, exact `601/600`, and `390px`: `294/294` twice-stable states. The family retains official three-box order, exact `18px` top boundaries, `14px` peer gaps/corners, accepted direct title and body roles, `120px` Blank geometry, responsive three/two/one-column flow, `24px + 40px` endpoint roles, and zero overflow.
- The 20 learner-facing A1 records retain the separate source-jump row. The hidden prototype fixture intentionally has no source jump; its template geometry, modes, endpoints, and responsive states still passed and were not changed.
- Print passed all 21 records in both modes: `42/42` twice-stable states with nonzero ancestor/card geometry, three print columns, exact official structure, hidden controls and Blank answers, zero endpoint guards, and zero overflow. No AMS product correction was required.
- AMS remains SHA-256 `ad7dae1645a144b7baf0a6e4900e1b8507021074c081d6ff18ba9487e6eb1aae`: one parsed product script, `84` cards/unique source IDs, exact counts `21/8/1/16/4/16/17/1`, `76` nonempty static links, `107` unique static document IDs outside the transient modal clone, unchanged storage, exact temporary/HTTP payload parity, HTTP `200`, and clean diff whitespace.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a1-objective-pass`. AMS A1 is objectively passed and pending fresh user visual approval. MN A3 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 261 — AMS A3 Objective Regression Pass

- AMS A3's screen canon already matched MN across all eight records. The only objective defect was a print-only navigation strip that remained visible after other controls were suppressed; one A3-scoped rule now hides `.template-modal-nav`.
- Filled and Blank screen validation passed `112/112` twice-stable states at `1440`, exact `935/934`, exact `901/900`, `768`, and `390px`. The five-direct/two-nested official structure, `18px/14px/10px` spacing, `14px/16px/11px` corners, role typography, Student Name, Blank geometry, approximately `64px` endpoint, and zero overflow pass.
- The official long connector remains entirely behind the relationship boxes: `34px x 3px` at card width `821px`, centered `3px x 34px` at `820px`, `10px` hidden overlap, `z-index:-1`, and exact `14px` visible gap.
- Print passed all eight records in both modes: `16/16` twice-stable states with nonzero ancestor geometry, two columns, official structure, hidden controls and Blank answers, zero endpoint guards, and zero overflow.
- AMS remains `84` source cards/unique IDs with exact counts `21/8/1/16/4/16/17/1`, eight A3 records, `76` nonempty links, no duplicate static IDs, and unchanged storage. Product/temporary/HTTP parity is SHA-256 `b37a2a8dabe50e0a0c35f7256158e69adcb8152120b7983acfa670a4fa05071d`; loaded scripts execute, HTTP is `200`, and diff whitespace is clean.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a3-print-nav-fix-261`. AMS A3 is objectively passed and pending fresh user visual approval. MN A5 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 265 — AMS Nested Section-Title Rail Evidence

- AMS now shares the A5 centered section-title rail with MN/MH for true nested-group labels in A3, A7, A9, A11, and A13. The role is exact: `11px / 700 / .16em` uppercase text, `14px` side gaps, zero label padding, and positive-width `1px` border-color rails.
- AMS A3 uses an extra `.considerations-top` wrapper; the shared rule explicitly covers it. Filled and Blank at exact `1440`, `768`, and `390px` retain the `Considerations` label, exact role geometry, and zero overflow.
- A5 `Health Promotion`, A1, and A15 remain excluded by structure; A5 retains only its existing `Expected Growth and Development` rail. No learner content, official relationship, card, box, order, ID, link, storage key, accent, or AMS identity changed.
- AMS retains `84` source cards and unique IDs with exact family counts `21/8/1/16/4/16/17/1`, `76` source chapter links, no duplicate document IDs, and unchanged `atiams_templates_progress` / `atiams_last_template` storage. Its script parses; product and exact temporary payload are byte-identical at SHA-256 `481f2c712dc395454c4abd6732786e45e5de471eaebbaa5d4c7e050d28cda259`; HTTP is `200`; `git diff --check` passes.
- Current cross-book comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-section-rails-mh-mn.html?v=section-title-rails-265`. The correction is objectively passed and pending fresh user visual approval. Content population is paused. ATI source support used: none; design-only change.

## Part 266 — AMS Nested Section-Title Rails User Approval

- The user visually approved the Part 265 cross-book rail comparison. AMS A3, A7, A9, A11, and A13 nested section-title rails are now **OBJECTIVELY PASSED AND USER VISUALLY APPROVED**, including the AMS A3 `.considerations-top` wrapper variant.
- A5 `Health Promotion`, A1, and A15 remain intentionally excluded. No AMS product file changed while recording approval; the Part 265 hash, rendered evidence, integrity results, and comparison remain current.
- Content population is paused. ATI source support used: none; design-only change. The retrospective heartbeat remains paused, Batch 10 MH A5 has not begun, and nothing was staged, committed, or pushed.

## Part 270 — AMS A5 Cross-Book Canon Repair And Objective Pass

- Stable before evidence on the source-neutral AMS A5 prototype found one cohesive family defect: non-Health-Promotion groups used `14px` bottom padding; Health Promotion parent copy rendered at `13px / 19.5px` without top padding; Blank children remained `200px`; and the Health Promotion answer leaked in Blank mode.
- One A5-only correction now applies `14px 14px 16px` non-Health-Promotion padding, DM Sans `16px / 25.6px / 400` Health Promotion parent copy with `14px 16px` padding, hidden Blank parent content, and nine exact `120px` Blank writing surfaces.
- Filled and Blank at exact `1440`, `1101`, `1100`, `768`, `601`, `600`, and `390px` passed `14/14` twice-stable states. The four/two/one-column transitions, `18px/14px` spacing, centered rail, connector strip and behind-box layering, corners, Student Name, approximately `64px` endpoint, and zero overflow all match the approved MN/MH A5 contract.
- Control-free print produced `4` Filled and `3` Blank letter pages. All seven rendered pages preserve title, metadata, rail, official parent/child structure, connector, writing surfaces, and horizontal containment without clipping or Blank answer leakage.
- AMS retains `84` source cards and unique IDs with exact family counts `21/8/1/16/4/16/17/1`, exactly one A5 prototype, `76` nonempty links, and unchanged storage keys. Product, exact temporary payload, and HTTP payload are byte-identical at SHA-256 `4767ee64df5ffecee1beb54d6cb93e50fc281933907dc21262ac06e99bc6491c`; scripts parse, HTTP is `200`, comparison parity passes, and diff whitespace is clean.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a5-canon-batch11`. AMS A5 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. MN A7 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 273 — AMS A7 Medication Canon Repair And Objective Pass

- Stable before evidence across all 16 A7 records found one cohesive family defect: Blank surfaces were 112/116/148/170px at wide widths and 40.25/49px after the narrow override, while corners and list rhythm still used the legacy 10px/8px, 7px, and 5px roles.
- One A7-only correction gives all nine Blank writing surfaces exact 120px geometry at every width, uses natural-start Blank alignment, suppresses only Blank last-box growth, and restores the accepted 16px/11px/14px outer/nested/direct corners, 0px/13px nested/direct title-band top corners, and 6px list rhythm. Filled content, learner text, and official structure remain unchanged.
- Filled and Blank at 1440, exact 935/934, 768, and 390px passed 160/160 twice-stable states. The 18px/14px/10px spacing roles, four metadata rows, Student Name line, centered Purpose rail, role-matched typography, exact row/stack transition, behind-box 34px x 3px connector, approximately 64px endpoint, hidden Blank answers, and zero overflow pass.
- Print produced 32/32 nonempty letter PDFs totaling 97 pages at 3–4 pages per record. AMS retains 84 source cards and unique IDs with exact family counts 21/8/1/16/4/16/17/1, all 16 A7 records, 76 links, no duplicate static IDs, and unchanged storage keys. Product, exact temporary payload, and HTTP payload are byte-identical at SHA-256 ede17c7891d03528eeb564da9a4ac437d457a62519f23451f5b7ebab89fcb980; scripts parse, HTTP is 200, and diff whitespace is clean.
- Current comparison: http://127.0.0.1:8766/elevated-ati-template-compare-ams-mn.html?v=ams-a7-canon-batch14. AMS A7 is objectively passed and pending fresh user visual approval. Automated QA is not user visual approval. MN A9 is next. Content population is paused. ATI source support used: none; design-only change.

## Part 294 — AMS A15 Fresh Render-First Objective Pass

- Fresh print evidence on the single source-neutral A15 fixture `tpl-ams-prototype-concept-analysis-layout` found one existing-canon defect: `.example-check` and `.template-modal-nav` remained visible as `flex` in twice-stable print-media readings. One A15-scoped print-only correction now suppresses progress, injected print, mode, and Previous/Next navigation controls while preserving the Worked Example/source row. Screen geometry, learner content, official labels/relationships, cards, boxes, order, counts, IDs, links, storage, accent, identity, and all other families are unchanged.
- Filled and Blank at `1440`, `768`, exact `721/720`, and `390px` pass `10/10` twice-stable states. The `18px` metadata boundary, `14px` peer gap/corners, DM Serif Display `15px/24px/400` title role, DM Sans `16px/25.6px/400` body role, official two-row metadata, five-role order, five hidden-answer exact `120px` Blank surfaces, exact `64px` endpoint, and zero horizontal overflow pass.
- Fresh current-run evidence under `/private/tmp/ams-a15-b23-294` includes four post-repair screen screenshots, two nonempty Letter PDFs totaling four pages, and four inspected PDF rasters. Printed study controls and browser headers are absent; Filled content remains visible, Blank answers remain hidden, and the official structure is legible without clipping or overlap.
- AMS retains `84` source cards and `84` unique card IDs with exact labeled family counts `21` Basic Concept, `8` Diagnostic Procedure, `1` Growth and Development, `16` Medication, `4` Nursing Skill, `16` System Disorder, `17` Therapeutic Procedure, and `1` Concept Analysis; `105` unique static IDs; one A15 fixture; five official A15 titles in order; `76` resolving links; one parsing product script; one parsing comparison script; and unchanged `nur2460_theme`, `atiams_templates_progress`, and `atiams_last_template` storage keys. Product, exact temporary payload, and HTTP payload are byte-identical at SHA-256 `8321c142e9d62e247d1e098b56702d8ed187492facfd4c451f56eaa4fb21f213`; HTTP is `200`; direct runtime logs are empty; and `git diff --check` passes.
- Current comparison: `http://127.0.0.1:8766/elevated-ati-template-compare-ams-a15-mn-b23-294.html?v=ams-a15-b23-294-post-2`. It opens valid MN and AMS A15 surfaces and reports **Completed AMS A15 loaded**. Batch 23 AMS A15 is objectively complete; automated QA is not user visual approval. Batch 24 final cross-book integrity handoff is next. Content population is paused. ATI source support used: none; design-only change.

## Part 295 — Final Cross-Book Integrity Evidence

- Batch 24 is objectively complete. AMS A15 remained unchanged in the final run and passed the fresh three-book representative screen gate in Filled/Blank at `1440`, `768`, and `390px`: stable geometry, hidden Blank answers, usable `120px` surfaces, zero overflow, and exact `64px` endpoint. Automated QA is not user visual approval.
- Final AMS print evidence is fresh: a nonempty three-page Filled PDF and one-page Blank PDF plus all four inspected rasters contain no Print/Filled/Blank/Previous/Next/browser-header labels, preserve the source/metadata/five official roles, and show no clipping or overlap.
- AMS integrity remains `84` cards with exact labeled counts `21/8/1/16/4/16/17/1`, `105` unique IDs, `76` resolving links, one parseable script, unchanged storage, and exact product/temporary/HTTP parity at SHA-256 `8321c142e9d62e247d1e098b56702d8ed187492facfd4c451f56eaa4fb21f213`. Cross-book integrity also passes MN/MH counts, IDs, links, scripts, storage, HTTP `200`, and `git diff --check`.
- Final comparison: `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-final-cross-book-a15-b24-295.html?v=b24-295-final`. The retrospective heartbeat is paused at SHA-256 `644a0219a75eec685b801e8669f3da6d14bfd7bda7b7ffc543ea3b32407d0bc1` pending final representative cross-book user visual review; protected automations remain paused and byte-unchanged. No new book is objectively necessary.

**Next Recommendation:** The user should personally review the final cross-book comparison and report approval or the first mismatch; the user should not commit or push yet.

## Part 300 — AMS A15 User Review Active

- MN A15 and MH A15 are now user visually approved in Filled and Blank. The final one-template/two-pane review is AMS A15 against approved MN.
- Current comparison: `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-review-ams-a15-vs-mn-b24-300.html?v=b24-300-two-pane`. Exact AMS loads left and MN right; the intended fixture/reference cards and synchronized Filled/Blank modes passed fresh visible checks. Leave Filled selected.
- AMS A15 objective evidence from Parts 294–295 remains current. Review only AMS Filled now; Blank follows only after Filled is resolved. Automated QA is not user visual approval.
- No product file changed. Hashes, objective completion, paused automations, recovery, and no-stage/no-commit/no-push state remain current.

**Next Recommendation:** The user should review only AMS A15 Filled and report approval or the first mismatch; no other mode should be reviewed yet.

## Part 301 — AMS A15 Filled User Visual Approval

- The user explicitly approved AMS A15 Filled against the approved MN reference. AMS A15 Blank is the final representative mode awaiting user visual review.
- Continue at `http://127.0.0.1:8766/cross-book-b24-295/elevated-ati-review-ams-a15-vs-mn-b24-300.html?v=b24-300-two-pane`; switch to Blank and review only AMS.
- No product or objective evidence changed. Hashes, paused automations, recovery, and no-stage/no-commit/no-push state remain current.

**Next Recommendation:** The user should switch the current comparison to Blank and review only AMS A15 Blank; no other action should be taken yet.

## Part 302 — AMS A15 Blank / Final Representative Approval

- The user explicitly approved AMS A15 Blank. AMS A15 is now user visually approved in Filled and Blank; MN A15 and MH A15 were likewise approved in both modes through Parts 297–300.
- The final representative cross-book visual handoff is complete. Preserve all distinctions for automated passes outside these explicitly reviewed representatives.
- No product file changed. AMS remains SHA-256 `8321c142e9d62e247d1e098b56702d8ed187492facfd4c451f56eaa4fb21f213`; MN/MH hashes and all Part 295 objective evidence remain current.
- All automations remain paused; no stage, commit, push, or new book occurred.

**Next Recommendation:** Perform a read-only final diff/status review, then wait for separate user authorization before any commit or push; the user does not need to inspect another template.
