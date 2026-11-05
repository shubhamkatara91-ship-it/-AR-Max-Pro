# AR Max Pro — deployment handoff

This repository is the dedicated home for AR Max Pro. The complete v1.12 source tree still needs to be uploaded before a server deployment or Android build can run.

## Release gates

1. Upload the complete reviewed v1.12 source tree, preserving `backend/`, `frontend/`, `scripts/`, `assets/`, `.github/workflows/`, `Dockerfile`, and `render.yaml` at repository root.
2. Review Render costs before provisioning the dedicated PostgreSQL database, API service, and scheduled backup job. No paid cloud resources are authorized by this repository setup alone.
3. Configure `AR_MAX_PRO_API` as a GitHub Actions secret only after the API is deployed and its HTTPS `/api/health` endpoint is healthy.
4. Run the Android debug workflow to produce a test APK. A signed release APK additionally requires the Android keystore secrets to be configured in GitHub Actions.

## Security

Never commit `.env` files containing real secrets, database URLs, private keys, Android keystores, or cloud credentials. Configure secrets only in the relevant provider dashboard.

## Current status

- Dedicated repository verified.
- Source tree upload pending.
- API deployment pending; no production API URL exists yet.
- Android APK build pending; no installable APK has been produced yet.
