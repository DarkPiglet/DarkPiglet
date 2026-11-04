# CRM 22.1 — Approved next task, November 4, 2026

Rob approved a bounded follow-up. Codex shall start only when Rob gives his normal execution instruction. The completed three-stage review remains authoritative for evidence and unresolved risks.

1. Investigate the two failing zero-Agreement exporter tests. Requirement: zero Agreement records means a header-only Excel table with zero data rows inside the table. Verify technical feasibility, then apply only the smallest justified exporter correction. Preserve unrelated worksheet data and existing formulas; do not change tests to accept an unwanted blank table row. If infeasible, report and stop this correction.
2. Address the third exporter test's missing Agreement precondition using the minimum valid fictional Agreement in a disposable copy of the approved fictional SQLite fixture. Do not modify the original fixture or operational data.
3. Re-run only the three affected exporter cases. Report each result with evidence.
4. Attempt the two previously blocked duplicate-integrity tests: `DuplicateScanAndConfirmedMergeOperationsPreserveRelationships` and `CrossCompanySiteMergeRollsBackWithoutChanges`. Use a prebuilt offline test assembly or a narrowly verified offline build confined to the approved test workspace. If dependencies or safe paths are unavailable, report BLOCKED without expanding access.
5. Verify changed-file scope, output isolation, unchanged protected hashes, data integrity, and targeted regression results. Preserve other uncommitted source and test changes.

Use the existing verified Dev workspace, branch, approved fictional fixture and isolated test/output settings. No live services, production data, broad tests, unrelated edits, source commits, merges, packaging or deployment. Report unexpected access needs individually. Publish results to both handoffs and stop for Rob/Priya review.

Separate future tasks, not approved here: RC Log/Agreement readability formatting; Alias border/contrast; actual GoGreen 125%/150% display scaling; office-only email testing and successful-send date behavior; broad Settings redesign.
