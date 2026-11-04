# CRM 22.1 — Stage 3 Comprehensive Interactive UI Regression — AUTHORIZED
Date: 2026-11-03. Authorization: Rob approved proceeding after Stage 1 Site Information and Stage 2 Contact Information completion reports. This authorizes TESTING ONLY, not fixes or packaging.

## Preflight (read-only)
1. Identify the exact existing isolated CRM 22.1 workspace and its current uncommitted changes. Preserve all Stage 1, Stage 2, and earlier maintenance changes; do not reset, switch branches, merge, commit, or overwrite files.
2. Inspect the latest Stage 1 and Stage 2 completion reports, including limitations. Confirm that the UI test targets the actual modified source, not an older executable.
3. Investigate how earlier Codex interactive WinForms testing was accomplished (GUI session, harness, permissions, profile and DB paths). Reuse the simplest proven approach. Do not create a new framework or request broad/full access.
4. Before launching CRM, establish and verify a completely fictional schema-24 SQLite test DB, and isolated application settings, local-app-data, logs, output, token/cache, and user profile paths. Verify all effective paths, including fallback/recovery paths. No production, USB, Z:, recovery or operational seed data may be read/copied; no real customer data or credentials. Prevent all live Graph/email, carrier, pickup, or other external side effects. If isolation cannot be demonstrated, do NOT launch.

## Execute only if isolation is proven
Perform genuine interactive WinForms testing (not build-only or source inspection) and save evidence using fictional records:
- Site Information: edit, save, cancel, nullable dates, close/reopen and DB persistence, revisions/audit.
- Contact Information cards: add, edit, delete, cancel, identity/association, validation, close/reopen and DB persistence, revisions/audit.
- Order form: new generation, same-name safe replacement, failure preserving original.
- UPS and FedEx tracking: recording dialog, dates, tracking/confirmation and correct fictional association.
- GoGreen: checkbox text and adjacent month/folder selector at 100%, 125%, 150% scaling and resize.
- History: Graph ID hidden from UI but retained where needed internally.
- Quick Lookup: visible and hidden-field matches, navigation, highlighting, tooltips and scrolling.
Check tab order, keyboard use, focus, error handling and unintended writes across areas. Confirm changes persist in SQLite after closing and reopening; inspect fictional DB rows and audit history rather than inferring from screen display.
Run focused automated regressions and offline Release build with CRMIncludeOperationalSeed=false. Inspect build output for operational DB, credentials or other sensitive files. Screenshots/evidence must contain only fictional data.

## Stop and report
If interactive UI cannot safely run, stop that test path and record exact reproducible blocker and NOT VERIFIED (never PASS). Continue only independent safe offline checks. For defects, document reproduction, severity and smallest proposed fix; do not edit application source without new authorization. Report each of the seven areas PASS / FAIL / NOT VERIFIED, evidence, DB checks, test counts, build results, remaining gaps, and package-readiness recommendation. No packaging, deployment, production access, live sends, application-source commits/pushes or merges. Publish documentation-only completion handoff if permitted, verify publication, then STOP for Rob/Priya review.