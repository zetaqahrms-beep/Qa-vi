# Project Brief: FinanceAI

## Overview
- **What it is:** A personal finance web app for tracking income, expenses, transfers, accounts, budgets and reports in Indian rupees, with optional AI help (Gemini).
- **Problem it solves:** One private place to record and understand your own money (where it goes, what is owed on cards/loans, how much is left), without bank logins.
- **Current status:** In development, used personally on one PC (localhost:3000). Built: accounts (8 types), transactions, transfers, categories, budgets, reports, dashboard, CSV/Excel import and export, backup/restore, multi-row entry, type/voice entry, "Ask about your money", Investment Ideas, recurring payments (EMI), account reset/delete, sign-in, light/dark themes.

## Users
- **Who uses it:** Only the owner (personal use); the app supports separate user accounts, but no other users are planned.
- **Their goals:** Record transactions quickly (typing, voice, several rows at once, or Excel import), see balances and spending, track card/loan dues, get safe, educational savings/investment guidance.
- **Regions & languages:** India only; English only; ₹ INR, en-IN number format (e.g. ₹1,50,000.00).

## Where AI is used
- **AI tasks:** (1) In-app Gemini prompts, the most important: reading typed/voice sentences into a transaction proposal, wording answers to money questions, explaining Investment Ideas, a short Insights comment, category suggestions. (2) Writing/fixing code with Claude Code. (3) Later: test cases, UI text, docs.
- **Who consumes AI output:** App code parses it (transaction proposal JSON, category JSON). The user reads it (money answers, investment explanation, insights), but only after the app checks every amount against its own calculated figures.
- **Most urgent prompt to build first:** Typed/voice transaction reading (sentence → transaction proposal JSON), used by "Add a transaction by typing" on the Dashboard.

## Voice & style
- **Tone:** Simple, friendly, beginner-level English; short sentences; no jargon. Numbers, amounts and dates always exact. Gently encouraging about saving. If a finance term is needed, explain it in one short line.
- **Words / claims to avoid:** Never joke about debt, losses or overspending. Never "guaranteed returns", "risk-free", "sure-shot", "will definitely grow". No personalised investment advice. No specific fund/stock/company recommendations. No invented or estimated amounts, percentages or returns.

## Technical
- **Platforms:** Web (desktop and mobile browser) plus a Node.js backend, running locally on one Windows PC.
- **Tech stack:** Node.js (CommonJS), Express 5, better-sqlite3 (SQLite file), dotenv, csv-parse, xlsx (SheetJS CDN build), nodemon (dev). Frontend: vanilla HTML/CSS/JS, no framework; theme settings in public/css/theme.css.
- **Code conventions:** Code split into services/ (business logic, every function takes userId first, every query scoped by user_id), routes/ (thin Express routers), public/js/ (one file per screen area), and database/ (schema.js; migrations.js with a verified safety copy, a before/after check and rollback). Errors use RequestError → JSON { success, message, errors }; unexpected errors are logged on the server only. Money is rounded with roundMoney, dates are "YYYY-MM-DD", and code has beginner-friendly comments.
- **Testing:** tests/*.test.js run with `npm test` against temporary databases only, never the real one.
- **APIs & integrations:**
  - **Gemini REST generateContent:** key in an x-goog-api-key header, GEMINI_API_KEY/GEMINI_MODEL in .env; not configured on this PC yet.
  - **Email (optional):** Brevo or Resend, for password reset codes; not configured.
  - **Browser Web Speech API:** voice input.
  - **Files:** CSV/Excel import and export.
- **Key data entities:**
  - **user:** email, password hash, recovery code hash.
  - **account:** name, type (bank, cash, wallet, upi, investment, credit_card, loan, other), opening_balance, currency (INR), is_active. Asset vs liability class; the balance is calculated from transactions, never stored.
  - **category:** name, type (income/expense).
  - **transaction:** date, description (= "Paid To", or "Purpose" for transfers; optional), amount > 0, type (income/expense/transfer), account_id, category_id (not for transfers), to_account_id (transfers only).
  - **budget:** expense category, monthly amount.
  - **recurring_commitment:** name, type (emi, loan_payment, subscription, insurance, rent, other), amount, frequency, start_date, installments or end_date, payment account, optional liability account, optional expense category.
  - **user_settings:** accent colour, text size.

## Output formats
- **Formats needed:**
  - **Typed/voice transaction:** strict JSON { intent: create_expense | create_income | create_transfer | unknown, amount: number, description, date: "YYYY-MM-DD", category, account, to_account }. Account and category names may come only from the lists provided.
  - **Category suggestion:** JSON { category } (one of the given names or "").
  - **Money answers:** plain text, 1–4 short sentences, ₹ amounts exactly as given.
  - **Investment explanation:** plain text, 4–7 short sentences or bullets, ending "This is general information, not financial advice."
  - **Code:** JavaScript (CommonJS) / HTML / CSS following the conventions above.

## Rules & constraints
- **Must always:**
  - **Figures come from FinanceAI:** every amount, total, balance and investment range is calculated by FinanceAI's own code. Gemini only words, explains or proposes.
  - **The user confirms first:** a proposed transaction is saved only when the user presses Add Transaction.
  - **Leave unknowns empty:** anything not in the user's sentence is left blank, never guessed.
  - **AI text is checked:** any amount or percentage not in the calculated figures is rejected, and FinanceAI's own answer is shown instead.
  - **Real data is protected:** tests use temporary databases; the real database is changed only after a verified safety copy.
- **Must never:**
  - **No writes from the AI:** Gemini never writes to the database or runs SQL; it reads only through approved read-only functions (at most 25 transactions).
  - **No invented numbers or promises:** never invent amounts, percentages, returns or dates; never promise profits.
  - **No secrets exposed:** never log or return the API key.
  - **No real data in prompts or tests:** never put real financial data into examples, tests or prompts.
- **Compliance / privacy:**
  - **Data stays local:** personal financial data lives only in the local SQLite file (secure_delete on); `.env`, the database and safety copies are excluded from Git.
  - **What Gemini receives:** the question, plus only the calculated figures, or the sentence plus account/category names.
  - **Investment content:** labelled as educational, not financial advice, returns not guaranteed.

## Open questions
- TODO: Which Gemini model should GEMINI_MODEL use, and when will the key be added to .env?
- TODO: Should Excel/backup exports rename the "Description" column to "Paid To / Purpose" (this would affect older backups)?
- TODO: Should recurring payments (EMI) be included in backups, and later create transactions or reminders automatically?
- TODO: Should spoken input in Indian English with mixed Hindi/Tamil words ("Hinglish") be supported by the typed/voice transaction prompt?
