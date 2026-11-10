# Synthetic community-settings test

Run with Node.js 20+, Playwright 1.65.0 and compatible Chromium:

```sh
mkdir -p /tmp/xbs-browser-test
npm install --prefix /tmp/xbs-browser-test --no-save playwright@1.65.0
/tmp/xbs-browser-test/node_modules/.bin/playwright install chromium
NODE_PATH=/tmp/xbs-browser-test/node_modules node --test tests/community-settings.browser.test.js
```

Set `PLAYWRIGHT_CHROMIUM_EXECUTABLE_PATH` to use a compatible system Chromium.
The test intercepts all page requests and uses fictional storage. It checks
keyboard cancellation, input validation, synchronous storage errors, retention
of existing data and unrelated settings, and that the test does not create a
community plan or enable posting.

Planning, detailed listing and collection deletion remain in the old native
prompt menu; this is not a complete replacement for hosts without prompts.
Cross-tab writes and asynchronous manager failures are not proven safe. The
installed userscript, real X and screen-reader behavior were not tested.
