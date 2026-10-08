# Manual verification: pre-launch retest findings (2026-10-08)

Setup: Chrome/Edge desktop, Claude side panel OPEN (about 1291 x 775). New tab.
Site: https://zetahrms-saas.com:8085/ERPSaasUI

Already verified by you (ready to raise): A2, D1 (+ Partner page), E1, C1 (Contact page only).

| # | Bug | Steps | Bug if you see | Result |
|---|---|---|---|---|
| 1 | P5-1 FAQ chips go to home | Open /faq. Click the chip "Partners" near the top. | You land on the HOME page instead of the Partners section of FAQ | [ ] yes [ ] no |
| 2 | Figures differ (P2-8 + India page) | Note the 4 counters on /home (2,000+ / 20+ / 25+ / 200,000+). Open /country/in and read its counters. Read the top blue banner text. Open the India chooser in the header and count countries. | India page shows different figures (e.g. 656+ customers, 7+ countries); banner says 16 countries but the chooser lists 15 | [ ] yes [ ] no |
| 3 | P5-2 Privacy date | Open /privacy-policy, scroll to the end. | "Last updated: November 14, 2021" | [ ] yes [ ] no |
| 4 | P3-1 Module boxes misaligned | Open /products, scroll to the row Inventory / Procurement / Sales & Distribution. | The grey "MODULES" boxes are at different heights (step down left to right) | [ ] yes [ ] no |
| 5 | P2-2 Bahrain hidden | On /home click "India" in the top bar (country chooser). Look at the MIDDLE EAST column. | The list ends at Oman; Bahrain only appears after scrolling inside the list | [ ] yes [ ] no |
| 6 | P2-3 "MEA, MEA" | On /home left menu click "Customers". Click the 2nd person (N. Inogamova). Read the line under the quote. | "Payroll Specialist MEA, MEA Regional Operations" | [ ] yes [ ] no |
| 7 | P2-4 Name cut off | Same Customers section. Look at the names under the 4 photos. | Third name shows "Narges Fattah ..." (cut with dots) | [ ] yes [ ] no |
| 8 | P2-1 Escape does not close menu | On /home press Tab until "What we Offer" is highlighted, press Enter (menu opens), then press Escape. | The menu stays open after Escape | [ ] yes [ ] no |
| 9 | P2-7 + P5-3 "Tap" wording on desktop | /home Solution Finder card, bottom right. Then /zenita above the 3 tier cards. | "Tap an option to continue" and "Tap a tier - Zenita will explain it" on a desktop page | [ ] yes [ ] no |
