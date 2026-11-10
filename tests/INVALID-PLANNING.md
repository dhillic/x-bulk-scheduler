# Invalid planning inputs

This partial fix rejects malformed 24-hour start times and non-integer or out-of-range timing values before touching the queue. Gap 0–1440 minutes, days 1–366 and daily cap 1–1000 are conservative implementation bounds, not verified X limits; previously stored values outside these ranges will need correction. Malformed input leaves the existing plan and settings unchanged in the synthetic test.

This does not fix the baseline's host-local date arithmetic, past times, midnight spillover, per-day cap calculation, plan concurrency or actual X scheduling. No claim of full planning safety or issue closure is made.

Install Node, Playwright and Chromium, then run `node --test tests/invalid-planning.synthetic.test.js`. Set `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH` if necessary. The browser test intercepts requests and uses fictional in-memory data; it performs no real X actions.
