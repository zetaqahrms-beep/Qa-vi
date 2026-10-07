# Project Brief: Zeta HRMS Mobile App `[HRMS]`

> Fill in the TODOs and confirm the pre-filled details. Every prompt for this project uses this brief.

- **What it is:** ZETA HRMS employee self-service (ESS) mobile app. Leave, attendance, payroll and related HR flows
- **Where AI is used:** TODO (e.g. writing Flutter code, generating test cases, in-app AI features, UI text/translations)
- **Users:** employees and managers. TODO: confirm/add roles
- **Tech stack (confirm):**
  - Flutter / Dart (package `zeta_ess`, in `ZetaEssMobile/`)
  - State management: Riverpod (manual Notifier / AsyncNotifier)
  - Errors: fpdart `FutureEither` + `handleApiCall`
  - Sizing: `flutter_screenutil` (`.w/.h/.r/.sp`)
  - Localization: `easy_localization` `.tr()`
  - Multi-tenant API via `UserContext`
- **Languages:** English, Arabic (RTL), Hindi, Malayalam
- **Rules:** never invent employee/payroll data; flag missing info; all user-facing text localized in all 4 languages
