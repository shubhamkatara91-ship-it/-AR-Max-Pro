# AR Max Pro — deployment handoff

This repository is the dedicated home for AR Max Pro. The reviewed v1.12 source archive is available locally, but the complete source tree has not yet been committed to this repository.

## Latest QA on the supplied v1.12 archive

- Node.js syntax checks passed for all **13 JavaScript files** checked by `backend/package.json`.
- Static test suite: **19/19 passed** (`node --test backend/tests/static.test.js`).
- These are source/static checks only. API runtime tests, PostgreSQL integration tests, production health checks, and physical Android device QA remain outstanding.

## Release gates

1. Upload the complete v1.12 source tree, preserving `backend/`, `frontend/`, `scripts/`, `assets/`, `.github/workflows/`, `Dockerfile`, and `render.yaml` at repository root.
2. Review Render costs and approve recurring charges before provisioning the dedicated PostgreSQL database, API service, and scheduled backup job. No paid cloud resources are authorized by this repository setup alone.
3. Configure `AR_MAX_PRO_API` as a GitHub Actions secret only after the API is deployed and its HTTPS `/api/health` endpoint is healthy.
4. Run the Android debug workflow to produce a test APK. A signed release additionally requires Android keystore secrets in GitHub Actions.

## Security

Never commit `.env` files containing real secrets, database URLs, private keys, Android keystores, or cloud credentials. Configure secrets only in the relevant provider dashboard.

## Current status

- Dedicated repository verified; deployment handoff committed.
- Latest local source QA: 13/13 JavaScript syntax checks and 19/19 static tests passed.
- Full source tree upload pending.
- Dedicated API/PostgreSQL deployment pending; no production API URL exists yet.
- Android APK build pending; this build environment has no configured Android SDK/Gradle toolchain.
