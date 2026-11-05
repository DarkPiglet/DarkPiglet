# CRM 22.1 — Word QA and Z transfer follow-up blocked
Date: 2026-11-04
Status: NO PERMITTED RENDERER; VISUAL QA NOT RUN; Z TRANSFER NOT RUN; STOP

## Result

Executed only the explicitly started bounded follow-up authorized by the November 4 current shared handoff at `661949e861fe38e1726b0465c8d02d78e15f3147`. Preserved the completed Word-plan draft and package work and investigated renderer availability read-only. The configured managed document runtime still contains no bundled LibreOffice `soffice.exe`. The only discovered LibreOffice remains the desktop installation under `C:\Program Files\LibreOffice`, which the applicable document workflow explicitly forbids as a fallback. No permitted renderer/environment was available, so the mandatory stop condition applied before page rendering, `Z:\docs transfer` checks, or copying.

## Preflight PASS

- Execution identity: `DESKTOP-UH85JC0\Dev`.
- Candidate ZIP exists unchanged at `C:\Users\Dev\CRM-22.1-Maintenance-20261103\artifacts\CRM22.1-TestCandidate-20261104\Run-01\CRM-22.1-TEST-CANDIDATE-win-x64-20261104-NOT-FOR-PRODUCTION.zip`.
- ZIP size: 56,534,127 bytes.
- ZIP SHA-256: `DC24A04897F8FEC00C8A990D6A8BF9546AEF6B8BB5A9B6AE5B43B6D0595E5A54`.
- Existing thirteen-case draft exists unchanged at `C:\Users\Dev\source\repos\DarkPiglet\Test\.codex-artifacts\crm22.1-word-z-transfer-20261104\CRM-22.1-Manual-Acceptance-Test-Plan-20261105.docx`.
- DOCX size: 41,415 bytes.
- DOCX SHA-256: `12A3AE71AE483F6D87B9B5A4E6B7DA673639DB0C904D62841A5CC30DA12EDFA1`.
- Project HEAD/upstream remained `dcaec840be0703394536d9bd89af07dd9f41d9cf`; the index was empty; `git diff --check` passed; tracked dirty-diff SHA-256 remained `44C77B0A4F047B196FBE7CE86AAE0D8CD62FD3FD5A1813B66DAC1BE62D68A8FE`.

## Renderer investigation BLOCKED

- Workspace dependency loader returned managed bundle `26.1026.10807` with bundled Python, Node, Poppler, override and fallback paths, but no LibreOffice path.
- A recursive read-only search of `C:\Users\Dev\.cache\codex-runtimes\codex-primary-runtime` found **zero** `soffice.exe` files.
- `C:\Program Files\LibreOffice\program\soffice.exe` exists, but it was not executed, added to PATH, copied, configured or otherwise used. The document workflow requires the absolute bundled LibreOffice resolved by the workspace dependency loader and forbids the desktop installation even when the bundled renderer is absent.
- No software was installed and no environment, PATH, permissions, configuration or DOCX content was altered.
- Page-by-page rendering and visual inspection: **NOT RUN**. Clipping, overlap, table layout, headings, pagination and final page readability remain **NOT VERIFIED**.

## Conditional Z transfer NOT RUN

The authorization permitted `Z:\docs transfer` identity, existence, writability, space and destination-name checks only after visual QA passed. Because no permitted renderer existed, those conditional checks were not started. No destination directory was created, no existing destination file was inspected for replacement, and neither the ZIP nor DOCX was copied. Source/destination comparison is **NOT RUN**. `Z:` and USB were not touched in this follow-up.

## Preservation and STOP

No CRM, GoGreen, Excel, Word or LibreOffice process remained. No application source/test/database/settings/profile/package/DOCX edit, build, test, packaging, deployment, release, maintenance work, software installation or permission bypass occurred. All application/test changes remain unstaged, uncommitted and unpushed.

**STOP for Rob review. Rob may separately choose manual visual review or provide a permitted managed document-rendering environment. Do not transfer the visually unverified DOCX or begin any later phase without separate explicit authorization.**
