# CRM 22.1 — two UI regression failures: bounded diagnostic assignment (November 7, 2026)

**Status:** Rob approved preparation of this next Codex investigation. Publication is NOT execution. Codex begins only after Rob's usual explicit start instruction. The November 7 broad-regression STOP remains in force until then.

## Baseline and question
Review the completed broad offline regression on exact merged `DarkPiglet/Weekly-Logger-Search-Application` `master` commit `d0ee8bd5747c2250524e5f7d53a3ed4408fb9954`. GoGreen 158/158, CRM Data 70/70 eligible, CRM UI 135/139 and two separate scheduled-backup cases 2/2 passed. The other four CRM UI cases consist of **two unresolved assertion failures** and **two fixture-incompatible/deferred cases**, not four proven application defects. Preserve the earlier initial SQLite error-14 environmental failure and successful bounded rerun.

Investigate **only**:
1. `AcceptanceFeedbackTests.RevisedEditorLayoutContainsSearchContactDateAndSiteNotes`: observed `contactCards.Visible == false` where the test expected true.
2. `CompanySelectionUsesAccordionAndLoadsFirstSiteWhileSearchKeepsMatchesExpanded`: observed first displayed row index `0`, expected `1`.

Determine independently for each whether the result is (a) a reproducible product defect, (b) an outdated/incorrect assertion, (c) a test setup, UI lifecycle, timing, visibility or data-fixture issue, or (d) unresolved. Do not presume either the code or test is wrong.

## Authorized diagnostic work
- Read this complete controlling assignment, the current/top status and relevant entries in both shared and project handoffs, and applicable AGENTS.md. Do not reread unrelated historical archives.
- Verify source identity and use a fresh disposable isolated, non-elevated Dev checkout of the pinned commit; if remote `master` has advanced, remain pinned and report the difference. Preserve the protected original checkout.
- Inspect the two test bodies, setup and fixtures, relevant WinForms event/visibility and selection logic, and intended behavior as supported by current UI requirements and nearby tests. For `Visible`, account for parent visibility, handle creation and test lifecycle; for row index, distinguish displayed order, zero-based indexing, filtering, and first-site selection. Do not silently redefine expected behavior.
- Reproduce each failing case using only verified wholly fictional schema-compatible fixtures and safe contained test execution. Use known short disposable TEMP/TMP paths and the previously successful non-sandboxed Dev test-runner context if necessary. Record exact command, environment, result and diagnostic evidence; make at most one evidence-driven environmental rerun per distinct issue. No test or application source edits are authorized, including temporary tracked-file edits.
- Compare the expected behavior with independently supported application requirements. Where ambiguity remains, label it **DECISION REQUIRED**, state the alternatives and their user-visible tradeoffs; do not make a speculative fix.
- Continue the other independent diagnostic case even if one is blocked. Do not rerun the whole regression or reopen the two fixture-incompatible cases; preserve them as deferred. Report for each: observed/expected, reproducibility, root-cause confidence, code/test locations, classification, minimal proposed correction (if justified), impact and smallest targeted verification set. A proposed test-only correction is not automatically preferred over a product fix.
- Publish a concise, factual diagnostic result to both current handoffs, with exact source identity, test evidence, PASS/FAIL/BLOCKED/NOT VERIFIED labels, unchanged source/test status, and independently refetch the remote publications. If handoff publication is blocked, preserve the report and explicitly state which publication is unverified.

## Safety and stopping rules
No application or test source modification, source commit/push/merge, release, packaging or deployment. Documentation-only handoff publication is permitted. No access, read, hash, copy or modification of `Database/CRM_seed.sqlite`, operational/customer/production/USB/Z:/recovery/profile databases or secrets. No real Graph/M365 login, mailbox draft/send, carrier transaction, live geocoding, or external side effect. Use only approved fictional data and mocks. Keep the two fixture-incompatible cases, live email/shipping, manual UI acceptance and workplace crash as **DEFERRED / NOT VERIFIED**. Do not claim full regression PASS or release readiness. Stop for Rob/Priya review of the diagnostic findings; any corrective implementation and its tests require a separate authorization.

## Pre-publication review
Checked for unnecessary tightening (routine safe inspection and contained reruns permitted), unnecessary loosening (no source changes or protected data access), ambiguous test classifications, false PASS claims, scope drift, identity, fixture safety, failure continuation, documentation verification and clear STOP. No further material drafting issue identified; this review is not evidence of Codex execution.
