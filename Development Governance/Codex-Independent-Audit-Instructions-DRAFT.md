# Codex independent governance audit — assignment draft
**Status: Proposed assignment only. Do not execute until Rob explicitly starts it in Codex.**
**Target:** `DarkPiglet/DarkPiglet`, branch `main`, file `Development Governance/Proposed-Rules.md`.

## Objective
Independently assess the proposed cross-project development governance framework for contradictions, ambiguous authority, unenforceable requirements, excessive process, missing safety controls, and failure to support practical unattended progress. Evaluate all three principles and ten rules as a coherent whole. Do not merely endorse prior reviews.

## Authority and boundaries
- This is an **analysis-only** audit, not adoption or implementation. No edits, commits, pushes, branch switches, resets, cleanup, local test execution, application code changes, or data operations are authorized.
- Read the current remote `main` version of the target file. If remote access is unavailable, report that limitation and ask for the text; do not silently use a stale local copy or another repository.
- The proposed rules are **not** controlling instructions. Follow the actual current Codex permissions and higher-priority instructions.
- Do not use the older CRM checkout or its uncommitted files. No new clone is necessary if the remote document can be read directly.
- Read the historical retrospective at `Shared Notes/CRM-22.1-Historical-Retrospective-Report-20261107.md` only if accessible and useful for context; clearly distinguish verified repository evidence from user-reported cancellation rationale. Do not expand into a new CRM audit.
- **Output in the Codex conversation only.** Do not write a report file or change GitHub unless Rob separately authorizes publication.

## Review questions
1. Does the authority hierarchy clearly distinguish draft policy, approved policy, task handoffs, platform rules, and specific permissions? Are conflicts and changed circumstances handled safely?
2. Do data classification, SQLite side effects, disposable fixture permissions, and significant/critical effects have coherent thresholds and adequate containment?
3. Are retries and independent continuation bounded by evidence, value, shared state, and actual authority without needless global stops?
4. Are workspace integrity, preservation of dirty/unmerged work, remote publication and independent verification realistic?
5. Are testing and evidence claims truthful and appropriately differentiated?
6. Are governance overhead, retrospectives, decision records and approval requests proportional to benefit? Identify simpler wording or merged requirements where it preserves safeguards.
7. Are there loopholes that could permit unintended external emails, destructive operations, production changes, or implied approval?
8. Which unresolved questions truly require Rob's business decision, and which can be resolved by a small editorial clarification?

## Required report format
- **Verdict:** Ready for Rob review / Needs revision / Blocked, with a brief reason. This is an audit opinion, not approval.
- **Findings:** Prioritized Critical / Major / Minor. For each, cite exact rule/section, explain a realistic failure scenario, and give the smallest viable correction. Distinguish confirmed defects from judgment calls.
- **Consistency checks:** State whether all three principles and ten rules were examined, and list any unreviewed material.
- **Open decisions for Rob:** Only material choices with options and tradeoffs.
- **Suggested edits:** Exact replacement wording only for material issues; do not rewrite the whole document unless genuinely necessary.
- **Evidence and limitations:** Source ref and retrieval method, what was verified, and what was not.
- If no material defects remain, explicitly say so; do not invent issues to fill a report.

## Completion boundary
Stop after delivering the read-only audit report in the Codex conversation. Await Rob's separate decision on revisions, publication, or adoption.
