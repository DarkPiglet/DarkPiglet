# CRM 22.1 — GoGreen monthly email sending: read-only code investigation
Date: 2026-11-03. Authorized by Rob to publish this investigation handoff. This document is the controlling assignment for this investigation only. It does not revive the canceled CRM migration.

## Goal
Establish whether the CRM's GoGreen Monthly Drafts feature ever gained production-capable batch email sending through Microsoft Graph, versus only draft creation and isolated single-email test sending. Do not assume that the code exists or that tests demonstrate production readiness.

## Evidence and scope
- November 2026 monthly drafts were created using CRM 22.1 and emails were sent using the existing Outlook macro, not a demonstrated CRM batch-send action.
- Previous notes describe Graph draft creation, a successful isolated email send, and draft-related automated tests. Treat all as leads, not proof of production batch sending.
- Read the current CRM 22.1 source and inspect available historical refs/branches/commits relevant to Test22, Test22.1, GoGreenMonthlyDrafts, Graph send methods, and the order-processing send path. Search actual code and history, not just branch names.
- Identify files, methods, commits/refs, invocation paths and UI gates for sending; distinguish Graph sendMail, draft creation, draft send, test-only sends, and bulk processing. Identify whether batch loop, selection, safeguards, error handling, throttling/retry, success verification and resumption exist. Report evidence and gaps; do not infer a capability merely from a method name.
- Check whether Last Interaction and Last Follow-Up for both Site and Contact are updated at draft creation or only after confirmed successful sending. The REQUIRED future behavior is only after successful send; report any deviation without fixing it.
- Identify current suppression controls (boxes 30 days, labels 14 days, 90-day cap, per-run override) and how any sending code would interact with them. Do not change these controls.

## Execution constraints
Read-only research only. No source, database, settings, handoff, or test changes by Codex; no branch checkout, reset, merge, commit, push, or worktree changes. No live email, Graph calls, authentication changes, CRM launch, network-dependent tests, database writes, or production data access. Read-only Git history inspection is allowed in an accessible isolated context; prefer remote evidence. Do not touch protected original working checkouts or assume Dev identity. If Dev-owned checkout access is needed, verify the approved Dev execution context and stop if unavailable; never alter permissions, ownership or safe.directory. Do not create new clones or modify working trees. Stop and report missing source/ref/access rather than broadening scope.

## Deliverable
Return a concise evidence-based report: repository/ref coverage (including missing refs), source file and method references, what each implementation actually does, classification (complete / partial or disabled / only drafts and isolated test sends / insufficient evidence), differences from working 22.1, specific risks to timestamps and safeguards, and the smallest justified next step with tradeoffs. Clearly distinguish confirmed facts from inference. No implementation, merge, or deployment; stop for Rob/Priya review.

## Standing handoff procedure
Read this document and applicable AGENTS.md, current shared handoff, and project handoff for context. Older migration instructions are historical and do not authorize work. Do not treat this read-only assignment as authorization to resume any canceled project.
