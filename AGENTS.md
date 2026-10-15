# Base44 Dev Environment

## Overview
This is a Vite + React frontend app that uses the `@base44/sdk` to communicate with the Base44 managed API. There is no local backend or database — all data goes through the SDK.

## Why the initial commit failed to start
Commit `be7c220` ("first commit") contained only the application source — no `docker-compose.base44.yml`, no lockfile, and no `.base44/environment.json`. The platform had no runbook to start the dev server, so the update failed. The fix is the dev-environment config in this branch.

## Setup
- Run with: `docker compose -f docker-compose.base44.yml up -d --build`
- The Vite dev server runs on port 5173 inside the container, mapped to host port 3000.
- `npm install` runs on container startup (no lockfile is committed; the anonymous `/app/node_modules` volume keeps installs isolated from the host bind mount).
- No external credentials or secrets are required to boot the app.

## Verification
- After starting, curl `http://localhost:3000/` — it should return the Vite HTML shell.
- The app has no routes defined (empty `PAGES` object in `src/pages/index.jsx`), so it renders a blank layout by design. This is expected, not an error.
- `npm run build` (vite build) succeeds with no errors.
