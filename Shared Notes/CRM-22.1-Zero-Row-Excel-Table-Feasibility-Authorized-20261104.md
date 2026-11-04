# CRM 22.1 — Zero-row Excel table feasibility investigation
Date: 2026-11-04
Status: **Rob approved investigation only. Codex execution begins only on his explicit start instruction.**

## Question to resolve
When the Agreement export has zero data records, Rob requires visible column headers and **no blank data record inside the exported Excel table**. Ordinary empty worksheet rows below the table do not count. Identify the smallest safe method to meet this requirement **without replacing ClosedXML if possible**. Do not assume the prior two failures prove an actual Excel-visible defect, or that replacing the entire workbook library is necessary.

## Verified starting evidence
- The November 4 exporter follow-up reported three targeted PASS and two FAIL. Duplicate-integrity and fictional Agreement fixture problems are resolved; do not reopen them.
- Current exporter `Data/CRMWorkbookExporter.vb` creates new tables across the header and one blank starter row (`Range(1, 1, 2, ...).CreateTable()`), then writes records and resizes to `Math.Max(dataStart, newLastRow)`. Therefore zero rows leave the starter row.
- The approved ClosedXML 0.105 probe showed a header-only range expands on create and also on ClosedXML reload after a raw OOXML header-only patch. This proves the **ClosedXML object model observation**, but does not independently establish what real Excel displays or accepts for a raw header-only OOXML table.
- Source and test changes in the local Dev worktree are uncommitted and must be preserved.

## Authorized bounded investigation
1. Preflight current shared/project handoffs, both AGENTS.md files, and the completion report. Verify established Dev identity/workspace/branch, expected dirty inventory and permitted fictional test routes. No clone, reset, switch, or source commits.
2. Read-only inspect the exact installed ClosedXML version's supported table APIs, known zero-row behavior and relevant existing exporter code/tests. Evaluate these minimal options in order:
   - Keep ClosedXML and change only the zero-row handling, without a phantom data **record**;
   - Generate a valid header-only Excel table by a carefully bounded final OOXML step on a disposable workbook, if supported; check whether a subsequent ClosedXML pass reintroduces the row;
   - Use a header-only worksheet range without an Excel table **only if** that preserves required consumer behavior (filters, formatting, future re-export, and formulas), clearly noting any functional change;
   - Evaluate a different library/writer or version **only if** lower-impact paths cannot meet the user requirement.
3. If needed, create **only disposable fictional workbooks and scripts** within a fresh ignored isolated test root. Compare actual OOXML table/auto-filter references, worksheet cell values, reopening behavior and formula/layout preservation. Do not infer real Excel behavior solely from ClosedXML reloading. If an interactive Excel check is essential but cannot be safely authorized/isolated, report NOT VERIFIED rather than bypassing it.
4. Recommend **one** smallest viable approach with precise technical reasoning, impact on existing files, formatting/formulas, version compatibility, and exactly which assertions would need to measure true workbook behavior. An assertion change is permitted as a *proposal* only if it preserves the no-phantom-row requirement; do not silently weaken tests.
5. Give a short PASS/FAIL/NOT VERIFIED feasibility matrix and next separately approvable minimal implementation/test plan. No implementation in this assignment.

## Boundaries and finish
Preserve all existing uncommitted code and tests. No code/project/package/dependency changes, live Excel production files, customer/production/USB/Z:/recovery data, Graph/email/carriers, real credentials, network package installs, Git source commits, merges, packaging or deployment. Confine disposable artifacts and any exploratory offline commands to previously verified Dev test isolation, with `CRMIncludeOperationalSeed=false`. Mandatory permission prompts still require their normal approval; unexpected permissions stop only the affected operation. Existing Alias, export readability, GoGreen DPI, office email and successful-send semantics remain separate.
Publish a concise investigation result in shared/project handoffs, independently refetch, then **STOP for Rob/Priya review**. Do not automatically implement the recommended option.
