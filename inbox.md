# Inbox: found outside the wiki

Lines Claude adds during work when it finds something the wiki lacks or has wrong. The nightly update files each one
into the wiki and removes it. Format: `- YYYY-MM-DD · what · source/reference`.

- 2026-11-16 · Owner's rule: any false positive or false negative in a test blocks (never treated or reported as passed, never merged on) until it's explained or fixed; e2e run now fails on any failed journey or recorded bug; coverage index fails on unsure readings · notes; mac-app CLAUDE.md, PR #661, issues #657, #660
- 2026-11-16 · Owner's rule: one area per PR/merge; changes across areas go in separate PRs unless there's a real dependency, which the PR must name · notes; mac-app CLAUDE.md (PR #664)
- 2026-11-17 · Owner's rule: Claude reaches outside services (Google Cloud, Firestore, Stripe, etc.) through GitHub Actions workflows (repo secrets such as FIREBASE_SERVICE_ACCOUNT, keyless sign-in on staging) and MCP connectors. A credential saved in the session environment is a last resort. Writing a small workflow just to get access (e.g. a read-only report) is the normal route, not app code; propose it as soon as a direct call fails. Sessions can't read GitHub secrets, so gcloud in a session container fails with CREDENTIALS_MISSING when nothing is saved on the environment; that's expected, not a broken key · notes; mac-app #550, PR #671 (CSP reports workflow)
