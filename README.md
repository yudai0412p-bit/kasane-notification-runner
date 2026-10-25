# KASANE notification runner

This public repository contains only the GitHub Actions scheduler for KASANE notifications.

- Runs every five minutes, including the exact top-of-hour boundary used by KASANE's 23:00 JST cutoff.
- Calls the private KASANE site's due-notification and nightly-summary endpoints.
- Stores the Sites bypass token only as the encrypted Actions secret `KASANE_SITES_TOKEN`.
- Contains no KASANE application source, task data, user data, or credentials.
- Supports a manual run through `workflow_dispatch` for operational checks.

The private KASANE site rejects unauthenticated requests. The workflow supplies the bypass token at runtime through an HTTP header; the value is never committed to this repository.
