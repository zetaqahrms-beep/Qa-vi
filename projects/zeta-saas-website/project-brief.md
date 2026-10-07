# Project Brief: Zeta SaaS Website

## Overview
- **What it is:** The public marketing website for Zeta Software Pvt Ltd's ERP and HRMS products — an Angular single-page app served under `/ERPSaasUI`.
- **Problem it solves:** Presents 21 product modules, 8 industries and 2 consulting services to prospective buyers, and collects sales, partner, support and consultation enquiries.
- **Current status:** In development, deployed at `https://zetahrms-saas.com:8085/ERPSaasUI`. Pre-launch — no real customers use it yet. 145 defects raised in Jira project ZNW to date, guarded by 634 automated tests.

## Users
- **Who uses it:** Prospective buyers evaluating ERP/HRMS software; prospective reseller partners; existing customers seeking support. (inferred, confirm)
- **Their goals:** Compare products, understand deployment options, contact sales, apply to become a partner, raise a support request.
- **Regions & languages:** 15 countries have dedicated pages and dialling codes — UAE, Saudi Arabia, Qatar, Kuwait, Bahrain, Oman, India, Sri Lanka, Malaysia, Singapore, Mauritius, Kenya, Uganda, Egypt, UK — plus an "Other" option. English only.

## Where AI is used
- **AI tasks:** Writing bug-hunt prompts that a browser-extension AI runs against the live site; drafting Jira bug reports; verifying findings before they are raised.
- **Who consumes AI output:** A person reads it — the tester, working alone. No application code parses it.
- **Most urgent prompt to build first:** The bug-hunt prompt (`docs/PROMPT-*.md`). Its measurement errors are what make the verification step necessary, so improving it reduces review work. Second priority: the Jira bug report format.

## Voice & style
- **Tone:** Formal, precise, factual. State the measurement, then the defect in one sentence. Roughly 200 words per ticket.
- **Words / claims to avoid:** Never name the correct value unless a requirement defines it — name the defect instead. No severity reasoning in ticket bodies. Never write that a ticket was closed early, or that a fault is "still" present.

## Technical
- **Platforms:** Web only. Desktop-first; verified at 1291×775, 1440×900 and 1280×650.
- **Tech stack:** Angular SPA (`app-root`, `app-sub-page-shell`), utility-class CSS, served by Microsoft-IIS/10.0 on port 8085. Backend at `/ERPSaasUIBackend` — ASP.NET Core (inferred, confirm) — with routes under `/api/` plus a `/health` endpoint outside it.
- **Test framework:** Playwright (specs, page objects, locators), black-box against the live site. Personal tool run by hand. (confirm)
- **Code conventions:** TODO: What are the website's own source conventions? Testing is black-box and the application source is not available here.
- **APIs & integrations:** `/ERPSaasUIBackend/api/*` returns JSON. The marketing pages make no API calls on load — content ships inside the JavaScript bundles.
- **Key data entities:** product module (title, path, family); industry (name, path); country (code, name, dialling code); enquiry (name, email, company, dialling code, phone, product, message).
- **Routing note:** Addresses use path form with no hash. This flipped to hash on 29 Sep 2026 and back to path on 5 Oct 2026 — check before relying on either.

## Output formats
- **Formats needed:** Markdown for prompts and manual-check documents. Plain text for Jira: `STEPS TO REPRODUCE` / `ACTUAL RESULT` / `EXPECTED RESULT`, with no notes sections.

## Rules & constraints
- **Must always:** Verify a finding on the live site before raising it. Search Jira for a duplicate first. Guard every raised bug with an automated test. State where the mouse pointer was for any layout measurement.
- **Forms (updated 2026-10-07):** Submitting forms with clearly marked test data is allowed — the receiving teams (sales, general, help desk, partner) know test emails will arrive and use them to confirm routing. Mark every submission "QA TEST – please ignore", submit each enquiry type once per test run, and record the submit time so emails can be matched.
- **Must never:** Sign in anywhere, or type a password. No load testing, scanners, injection payloads or rapid repeated requests — security and performance testing is passive only.
- **Must never:** Report a missing footer. It is absent by design on every page except home, support, partner and contact.
- **Must never:** Set a Jira ticket to Fixed — that is the developer's status. Never write to Jira without explicit approval for that specific issue.
- **Compliance / privacy:** Four demo accounts with plain-text passwords ship in browser storage, and the partner portal renders without sign-in. Both were ruled acceptable pre-launch demo data while no customers exist. No real personal data is present on the site.

## Open questions
- TODO: Does this brief cover the public marketing site only, or also the customer and partner portals under `/login/`?
- TODO: What is the application's own source stack and repository? The test framework is black-box and has no access to it.
- TODO: Is `zetahrms-saas.com:8085` the production host, or a test server configured differently? Several findings — compression, app-pool idle timeout — depend entirely on the answer.
- TODO: Which company name is correct, "Zeta Software" or "Zeta Softwares"? Both appear on the site today.
- TODO: Is there a written brand, tone or style guide for the site's own copy?
- TODO: What is the intended launch date, and which countries launch first?
- TODO: Who owns the deployment and can answer server-configuration questions?
