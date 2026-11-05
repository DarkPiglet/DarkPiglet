# CRM 22.1 — Word acceptance plan and Z transfer blocked
Date: 2026-11-04
Status: WORD DRAFT STRUCTURALLY VALID; VISUAL QA NOT VERIFIED; Z TRANSFER NOT RUN; STOP

## Result

Executed only the explicitly started `CRM-22.1-Word-Test-Plan-Z-Transfer-Authorized-20261104.md` assignment. Package and protected-worktree preflight passed, an actual prior Rob-approved Word plan was identified with exact historical provenance, and a clean editable thirteen-case CRM 22.1 draft was generated and structurally validated. The required DOCX visual render could not be produced because the configured bundled document runtime contains no LibreOffice `soffice.exe`, while Microsoft Word COM is not installed. The document workflow explicitly prohibits substituting the user's installed desktop LibreOffice for the missing bundled renderer. Therefore visual QA is **NOT VERIFIED**, the draft was not delivered, no destination was created on `Z:`, and neither the DOCX nor ZIP was copied.

## Preflight and preservation PASS

- Execution identity: `DESKTOP-UH85JC0\Dev`.
- Preserved workspace/branch: `C:\Users\Dev\CRM-22.1-Maintenance-20261103` / `codex/crm-22-1-maintenance-20261103`.
- Project HEAD/upstream remained `80c651798a9e57a0ee3ecb30b8a3cd3ba018f239`; original baseline remained `dd223e6f228c236c85b89b1246b587b2a0d1f5c2`.
- Index remained empty, `git diff --check` passed, and the tracked dirty-diff SHA-256 remained `44C77B0A4F047B196FBE7CE86AAE0D8CD62FD3FD5A1813B66DAC1BE62D68A8FE`. The same twelve tracked modified and five untracked source/test paths remain unstaged, uncommitted and unpushed.
- Source archive remained exactly 56,534,127 bytes with SHA-256 `DC24A04897F8FEC00C8A990D6A8BF9546AEF6B8BB5A9B6AE5B43B6D0595E5A54`. It was not rebuilt, modified, repackaged, renamed, extracted, launched or substituted.
- No CRM, GoGreen, Excel, Word or LibreOffice process remained. No application source, database, settings, credentials, profile, package, USB content or production/customer data changed.

## Prior Word plan provenance PASS

The actual prior plan is `Z:\CRM Test 22 Manual Acceptance Test Plan.docx`, 74,720 bytes, modified October 16, 2026 at 08:00:08 Pacific, SHA-256 `58D09BB0D0522CA6BBADB207781F05E5E389668CB585630EE3338E275E913F3B`. The permanent historical index routes this Test 22 evidence to `Handoff-history-001.md`, whose recorded path, byte count and hash match exactly. The retained document has one portrait Letter section, 62 paragraphs and seven tables; it establishes the title/subtitle, package-identification table, numbered case headings, two-column Action/Expected Result tables, checkbox result lines, blank actual-result/notes fields and final decision table. Its prior recorded results, notes and two screenshots were treated only as historical evidence and were not copied into the new draft. The source hash remained exact after inspection.

## Draft creation and structural validation PASS

- Task-local draft: `C:\Users\Dev\source\repos\DarkPiglet\Test\.codex-artifacts\crm22.1-word-z-transfer-20261104\CRM-22.1-Manual-Acceptance-Test-Plan-20261105.docx`
- Draft size: 41,415 bytes
- Draft SHA-256: `12A3AE71AE483F6D87B9B5A4E6B7DA673639DB0C904D62841A5CC30DA12EDFA1`
- `python-docx` open: PASS; OOXML ZIP integrity: PASS; one portrait Letter section; 174 paragraphs; 16 tables.
- All thirteen IDs `CRM221-A01` through `CRM221-A13` are present. Each case has purpose, classification, preconditions, detailed operator steps, expected results, blank actual result, blank pass/fail and notes fields. Package identity and final signoff are present.
- Coverage includes contact cards; Site Information/Alias; Order Boxes enablement; Excel review/cancel/approve/same-name replacement/locked-destination preservation; Quick Lookup; FedEx/UPS recording; GoGreen UI; 100/125/150 percent scaling; zero-record all-or-nothing exports; export formatting and workbook preservation; Graph-ID display; draft-only observation; and separately gated live-send/date-update requirements.
- Monthly email cases are labeled unresolved/deferred rather than preclaimed PASS. Live send defaults to NOT RUN and requires Rob's separate explicit authorization for one named message.
- No old result text, screenshots, media, comments or tracked changes are present; exact tracked insert/delete element counts are zero. The only retained custom XML is an empty Word bibliography store. Accessibility audit reported zero high-severity findings and three medium findings for form-style tables without semantic header rows.

## Visual validation BLOCKED

The required packaged `render_docx.py` was run against both the retained template and new draft. Both attempts produced zero page PNGs because no bundled `soffice.exe` is present. Runtime discovery confirmed bundled Python, Node and Poppler, but no bundled LibreOffice. Microsoft Word COM is also unregistered. The installed desktop LibreOffice under `C:\Program Files\LibreOffice` was not used because the applicable document workflow explicitly requires the bundled renderer and forbids that fallback. Consequently clipping, overlap, table pagination, glyph rendering and final page count are **NOT VERIFIED**. The draft is retained only as resumable evidence and is not a delivered test plan.

## Z drive and transfer

- `Z:` exists as an NTFS fixed drive labeled `VM-Share`, matching the historically used exchange drive. It had approximately 473 GB free, and the exact prior approved Word plan was present at its recorded path.
- Because the DOCX failed the mandatory visual-QA gate, destination writability was not probed, no new destination directory was created, and no overwrite decision was required.
- ZIP copy: **NOT RUN**. DOCX copy: **NOT RUN**. Destination size/hash/readability verification: **NOT RUN**.
- The source ZIP and retained Word template remain unchanged. USB was not touched.

## Smallest safe remedy and STOP

Resume only in a document-authoring environment whose configured workspace dependencies include the supported bundled LibreOffice renderer. Re-render and inspect every draft page at 100 percent, correct any layout issue, re-run structural/privacy checks, then reverify the unchanged source ZIP and `Z:` identity/writability before creating a new no-overwrite nonproduction destination and copying both files. Do not silently use another archive or skip visual QA.

**STOP for Rob/Priya review. Do not transfer this unrendered draft, begin the separate maintenance investigation, modify source, rebuild/package, merge, deploy, release or use production data without separate explicit authorization.**
