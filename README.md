# AR Max Pro — deployment handoff

This repository is the dedicated home for AR Max Pro. The reviewed v1.12 source archive is available locally, but the complete source tree has not yet been committed to this repository.

## QA completed on the local v1.12 source

- Node.js syntax checks passed for **14 JavaScript files** across backend, frontend, and scripts.
- Static test suite: **21/21 passed** (`node --test backend/tests/static.test.js`).
- These are static/source checks only. API runtime tests, PostgreSQL integration tests, production health checks, and physical Android device QA remain outstanding.

## Release gates

1. Upload the complete reviewed v1.12 source tree, preserving `backend/`, `frontend/`, `scripts/`, `assets/`, `.github/workflows/`, `Dockerfile`, and `render.yaml` at repository root.
2. Review Render costs before provisioning the dedicated PostgreSQL database, API service, and scheduled backup job. No paid cloud resources are authorized by this repository setup alone.
3. Configure `AR_MAX_PRO_API` as a GitHub Actions secret only after the API is deployed and its HTTPS `/api/health` endpoint is healthy.
4. Run the Android debug workflow to produce a test APK. A signed release APK additionally requires Android keystore secrets in GitHub Actions.

## Security

Never commit `.env` files containing real secrets, database URLs, private keys, Android keystores, or cloud credentials. Configure secrets only in the relevant provider dashboard.

## Current status

- Dedicated repository verified; handoff README committed.
- Local source QA rerun: 14/14 JavaScript syntax checks and 21/21 static tests passed.
- Full source tree upload pending.
- API deployment pending; no production API URL exists yet.
- Android APK build pending; Android SDK/Gradle are not configured in the current build environment.
