# Project Brief: ZetaMobile

## Overview
- **What it is:** Appium 3 + WebdriverIO 9 automated test framework (`zetamobile`, package.json) for Zeta's ESS Android app `com.zeta.zeta_ess`.
- **Problem it solves:** manual regression of an HR self-service app is slow, and bugs need reproducible evidence before they are raised in Jira (project MAB).
- **Current status:** in active daily use, local only. 21 spec files, 24 screen objects, 60 tools, 76 docs; app under test 3.1.7 (versionCode 27) on an Android 15 emulator.

## Users
- **Who uses it:** Vishnu, junior automation tester — the only operator. A separate Claude account consumes this brief for prompt engineering and direction.
- **Their goals:** see where the project is heading, decide what to test next, and get evidence-backed findings he can check by hand.
- **Regions & languages:** English only, in scope. Arabic tooling exists (`tools/verify-arabic-status-bar.js`, `tools/restore-english.js`) but Arabic is out of scope now.

## Where AI is used
- **AI tasks:** planning and project direction; prompt engineering. In practice AI also writes and fixes framework code, runs suites and drafts bug text (inferred, confirm).
- **Who consumes AI output:** a person reads it — Vishnu alone. No code parses it.
- **Most urgent prompt to build first:** project direction review — what is covered, what is missing, what to test next.

## Voice & style
- **Tone:** plain English, short sentences, evidence first. No lessons (English, prompt and coding coaching happens only in the Qa-vi workspace).
- **Words / claims to avoid:** "fixed", "passed" or "missing" without evidence; use CANNOT TELL instead. No overstated impact, no invented severity, no verdict about the app from a single tool failure.

## Technical
- **Platforms:** Android emulator (`Medium_Phone`, Android 15, `emulator-5554`). The old app `com.zeta.hrms` 1.0.19 has its own `.env` block and guards but is out of scope now. iOS not in scope.
- **Tech stack:** Node ESM; WebdriverIO 9.31; Appium 3.7.0 with `uiautomator2` 8.6.1; Mocha via `@wdio/mocha-framework`; dotenv; imapflow + mailparser for email checks. No database, no hosting, no CI — everything runs on one Windows PC.
- **Code conventions:** five layers — `screens/` (locators + actions, never assertions), `fixtures/` (set up state), `data/` (values only), `tools/` (one-off investigations), `tests/` (assertions). Wait for the thing you need, never a fixed pause (`docs/waiting.md`). Accessibility id first; the app is Flutter, so labels are doubled ("X\nX") and there are no resource-ids on most controls. Comments explain why, citing the run that proved it. Commit locally, never push.
- **APIs & integrations:** Appium/WebDriver and adb to the emulator; IMAP (QA Gmail) to read notification emails; Jira MAB through a connector, read freely, write only when asked.
- **Key data entities:** account: user, password (requester + approver L1/L2/L3). testUser: activationUrl, username, password, pin, company. app: packageName, activity. leave request: type, from/to dates, days, status ("Pending By <approver>"). change request: type, requested date, old/new values, status. email expectation: subject pattern, recipient, required words.

## Output formats
- **Formats needed:** chat summary first (default); markdown reports in `docs/`; Jira-ready Steps / Actual / Expected text on request; JavaScript code and local commits.

## Rules & constraints
- **Must always:** state evidence before a verdict; report a bug in chat, let Vishnu confirm by hand, only then Jira; search MAB for duplicates before raising; commit locally; prefer read-only probes; say CANNOT TELL when a run proves nothing.
- **Must never:** push to a remote; change HRMS admin configuration; touch production; raise or transition a Jira issue unasked; re-check Closed bugs; print credentials; use a real person's credentials.
- **Compliance / privacy:** test accounts and test server only. The QA mailbox receives other people's mail — filter to `zeta.qa.hrms+` test users and never read or quote the rest. `.env` is git-ignored and holds live test credentials.

## Open questions
- TODO: what is the expected page size / pagination requirement for the current pagination testing task?
- TODO: may AI create test data (extra leave or request records) to fill a multi-page list, and up to what limit?
- TODO: will the framework ever be handed to other testers or moved to CI, or does it stay a one-person local tool?
- TODO: does the old app (`com.zeta.hrms` 1.0.19) come back into scope, and when?
- TODO: is iOS planned at all, or is Android the permanent scope?
- TODO: which prompt should be built second, after the project direction review?
