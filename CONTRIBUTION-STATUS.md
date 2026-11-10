# X Bulk Scheduler — contribution tracker

Baseline: upstream `main` at `df0f2570100748b7cc6c13836f201d163e57d70f`. This is a contribution progress report, not a claim that changes have been merged, deployed or fully verified. All PRs are against upstream `main`; unresolved items stay open.

| Issue | Current status | Work done or remaining |
|---|---|---|
| [#1](https://github.com/eleven-smg/x-bulk-scheduler/issues/1) | Partial, draft [PR #68](https://github.com/eleven-smg/x-bulk-scheduler/pull/68) | Synthetic race model demonstrates a lost update; no production conflict safeguard or real-environment verification. |
| [#8](https://github.com/eleven-smg/x-bulk-scheduler/issues/8) | Partial, draft [PR #68](https://github.com/eleven-smg/x-bulk-scheduler/pull/68) | Synthetic notification-ordering and A→B→A models pass; real manager and browser notification behavior remains unverified. |
| [#9](https://github.com/eleven-smg/x-bulk-scheduler/issues/9) | [PR #69](https://github.com/eleven-smg/x-bulk-scheduler/pull/69) open | Manual non-destructive review process and synthetic decision-model tests; no real account evidence or userscript integration. |
| [#10](https://github.com/eleven-smg/x-bulk-scheduler/issues/10) | Partial, draft [PR #67](https://github.com/eleven-smg/x-bulk-scheduler/pull/67) | A synthetic oEmbed delayed-callback and restart test passes. Real timing and in-flight composer/picker cancellation remain unverified; the request is not aborted. |
| [#11](https://github.com/eleven-smg/x-bulk-scheduler/issues/11) | Partial, draft [PR #71](https://github.com/eleven-smg/x-bulk-scheduler/pull/71) | Single-attempt synthetic safeguard; live editor, non-text attachments and late rerenders remain unverified. |
| [#12](https://github.com/eleven-smg/x-bulk-scheduler/issues/12) | Partial, draft [PR #72](https://github.com/eleven-smg/x-bulk-scheduler/pull/72) | Synthetic WAT/boundary and ambiguity checks; live scheduling intentionally blocked until the actual X picker timezone is verified. |
| [#13](https://github.com/eleven-smg/x-bulk-scheduler/issues/13) | [PR #63](https://github.com/eleven-smg/x-bulk-scheduler/pull/63) open | Inline search and synthetic test; installed userscript, experimental build, real X and manual screen-reader checks not run. |
| [#14](https://github.com/eleven-smg/x-bulk-scheduler/issues/14) | [PR #66](https://github.com/eleven-smg/x-bulk-scheduler/pull/66) open | Inline caption controls and synthetic failure/keyboard test pass; live/installed and manual screen-reader checks remain. Queue writes may partially fail and are not atomic. |
| [#15](https://github.com/eleven-smg/x-bulk-scheduler/issues/15) | Partial, draft [PR #74](https://github.com/eleven-smg/x-bulk-scheduler/pull/74) | Inline creation, community addition and session assignment tested with synthetic data; planning, detailed listing and deletion still use native prompts. Cross-tab/async storage and installed/screen-reader checks remain. |
| [#16](https://github.com/eleven-smg/x-bulk-scheduler/issues/16) | Partial, draft [PR #70](https://github.com/eleven-smg/x-bulk-scheduler/pull/70) | Synthetic keyboard and selected axe checks pass; full focus order, screen-reader and installed/device checks remain. |
| [#17](https://github.com/eleven-smg/x-bulk-scheduler/issues/17) | Partial, draft [PR #73](https://github.com/eleven-smg/x-bulk-scheduler/pull/73) | Safe test plan; reviewed preview-only extension and installed test environment unavailable. |
| [#18](https://github.com/eleven-smg/x-bulk-scheduler/issues/18) | Partial, draft [PR #73](https://github.com/eleven-smg/x-bulk-scheduler/pull/73) | Installation guidance only; real Tampermonkey installation and safe operation not verified. |
| [#54](https://github.com/eleven-smg/x-bulk-scheduler/issues/54) | Partial, draft [PR #73](https://github.com/eleven-smg/x-bulk-scheduler/pull/73) | Device plan only; actual desktop and phone testing remains. |
| [#55](https://github.com/eleven-smg/x-bulk-scheduler/issues/55) | Partial, [PR #64](https://github.com/eleven-smg/x-bulk-scheduler/pull/64) open | Checklist and pinned-source comparison prepared; actual installed userscript/extension and deployment provenance not verified. |
| [#56](https://github.com/eleven-smg/x-bulk-scheduler/issues/56) | [PR #65](https://github.com/eleven-smg/x-bulk-scheduler/pull/65) open | Safe, separately authorized single-target acceptance checklist proposed; no real post scheduled or sent. |
| [#57](https://github.com/eleven-smg/x-bulk-scheduler/issues/57) | Blocked | Independently established saved examples and an explicitly authorized account are required. |

Several code PRs modify the same userscript on separate branches; maintainers may need to resolve overlaps after merging. Draft PRs are incomplete and must not be treated as production-ready.

## Validation so far

- Search: `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium npm run test:search` passed (one synthetic browser test; all requests intercepted). `node --check src/x-bulk-scheduler.user.js` passed. Live X and manual screen-reader checks were not run.
- Captions: `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/captions.browser.test.js` passed with synthetic storage and intercepted requests. Real-X, installed userscript and screen-reader tests were not run.
- Stop: synthetic delayed-callback/restart test passed; one observed click-to-notice time was 29 ms. The request stayed pending and real-world timing and other cancellation boundaries remain unverified.
- Release provenance: pinned raw source and the Git object at the baseline matched byte-for-byte, SHA-256 `f6785efc5469d9a57e3de3a7cf2c3129fdb1d3e76c6ea2bfadf49fa5d68fac08`; an intentionally modified copy was detected as different. Installed/deployed artifacts were not checked.
- Safe scheduling: documentation review and `node --check` only; no X account actions, live schedule, post, Like, follow, or deletion performed.

- Storage model: three deterministic synthetic tests passed; no real manager notifications or production conflict guarantees were verified.
- Legacy review: two synthetic decision-model tests passed; no real account evidence or queue edits were performed.
- Accessibility: selected axe/keyboard checks passed at 390×844 and 1280×800. The initial test timed out due to a locator retaining an old accessible name; the corrected test passed. No manual screen-reader testing was performed.
- Composer: synthetic single-attempt/draft regression passed. The 500 ms observation window and non-text draft limitations leave the issue open.
- Picker: synthetic WAT boundary and ambiguous-control tests passed in Honolulu and Tokyo timezones. Live scheduling in the proposal is blocked until real picker verification.
- Environment plan: initial documentation check used the wrong path; the corrected whitespace check passed. No installation or physical device was tested.
- Community settings: synthetic validation, cancellation and synchronous storage-failure test passed. Legacy planning, listing and deletion prompts, cross-tab/async failure handling and installed/screen-reader checks remain.

## Exact validation commands and scope

All commands below ran against separate branches based on the baseline above. The browser tests used intercepted requests and synthetic in-memory storage, never an authenticated X account. Commands with `NODE_PATH` use the locally installed Playwright/axe packages; the corresponding PR test guide describes installing those tools elsewhere.

| Contribution | Command | Result |
|---|---|---|
| Search #13 | `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium npm run test:search` | Passed: 1 synthetic browser test. |
| Captions #14 | `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/captions.browser.test.js` | Passed: 1 synthetic browser test. |
| Stop #10 | `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/stop-delay.browser.test.js` | Passed: 1 synthetic browser test; observed 29 ms to notice, not request abort. |
| Storage #1/#8 | `node --test tests/storage-notifications.model.test.js` | Passed: 3 model tests; the model deliberately demonstrates a lost update. |
| Legacy review #9 | `node --test tests/legacy-review.model.test.js` | Passed: 2 synthetic model tests. |
| Accessibility #16 | `NODE_PATH=/tmp/xbs-a11y/node_modules:/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/panel-accessibility.browser.test.js` | Passed on rerun: 1 test across two viewports. Initial locator timeout was a test error, documented in PR #70. |
| Composer #11 | `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/composer-insertion.browser.test.js` | Passed: 1 synthetic browser test; real editor and late rerenders unverified. |
| Picker #12 | `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/schedule-picker.browser.test.js` | Passed: 1 synthetic browser test across two timezones; actual X picker unverified. |
| Community settings #15 | `NODE_PATH=/data/briefing-tools/node_modules PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH=/usr/local/bin/chromium node --test tests/community-settings.browser.test.js` | Passed: 1 synthetic browser test; legacy prompts and asynchronous/cross-tab behavior remain. |
| Release #55 | `git show <baseline>:src/x-bulk-scheduler.user.js`, `sha256sum` and `cmp` against the commit-pinned public raw file; compare an altered copy | Passed: pinned files matched; modified copy differed. No installed artifact verified. |
| Acceptance #56 and environment plan #17/#18/#54 | `node --check src/x-bulk-scheduler.user.js` and documentation review/whitespace check | Passed after correcting an initial wrong-path documentation check; no real installation or post test. |

`node --check src/x-bulk-scheduler.user.js` and `git diff --check` passed for the code branches. No real X posting, scheduling, likes, follows, deletions or live draft changes were performed. PRs are not merged; CI was not monitored.
