# AR Max Pro v1.13.16 — deployment handoff

This repository is the dedicated home for AR Max Pro. The latest reviewed source archive is v1.13.16. The complete source tree is **not yet committed** to this repository; the verified ZIP is maintained separately until it can be transferred intact.

## Verified local checks (2026-11-07)

- Backend unit suite: **47/47 passed**, 0 failed, 0 skipped.
- Backend JavaScript syntax checks: passed via `npm run check`.
- Source archive integrity: `unzip -t` passed.
- These results are local source checks. They do not establish production API, database, live-feed, or device functionality.

## Deployment configuration

- Render workspace: `My Workspace`.
- Existing AR Max Pro PostgreSQL 17 Free database: `ar-max-pro-db`, Singapore region, status reported as available.
- The database currently has an empty IP allowlist. The hosted database query connection was blocked by that policy. Do not open it to all IPs; connect the deployed service using the private/internal database connection in the same region.
- The only currently listed Render web service was `opus-pro-api`; it is not AR Max Pro and must not be modified for this deployment.
- Local v1.13.16 `render.yaml` was revised to use a Free web service only and reference an existing database URL. Do not create paid resources.

## Remaining release gates

1. Transfer and commit the complete v1.13.16 source tree, including binary assets, into this repository.
2. Create the AR Max Pro Free web service from the committed source and configure its database connection using Render's private connection details.
3. Run the full API test suite and PostgreSQL integration test against the deployed service/database; verify health and migrations.
4. Obtain an authorized BDG feed/API endpoint and documented response schema before enabling live synchronization. Do not scrape private endpoints or bypass authentication.
5. Generate the Android native project, install/configure the Android SDK and Gradle toolchain, then build and test an APK/AAB on a real device.

## Security and operational notes

- Never commit real `.env` files, database URLs, API keys, signing keys, or keystores.
- Do not expose the database with a public all-IP allowlist.
- Prediction outputs are estimates, not guaranteed future results.
- The Free PostgreSQL database is scheduled to expire on **2026-12-05**; export and verify a backup/migration before that date.
- No paid service or resource is authorized.

## Current status

The 47 backend unit tests and syntax checks pass locally. No AR Max Pro production deployment, live BDG feed, PostgreSQL integration result, Android APK/AAB, or physical-device QA is claimed yet.
