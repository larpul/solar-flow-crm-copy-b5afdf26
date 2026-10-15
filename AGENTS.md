# Base44 Dev Environment

## Overview
This is a Vite + React frontend app that uses the `@base44/sdk` to communicate with the Base44 managed API. There is no local backend or database — all data goes through the SDK.

## Setup
- Run with: `docker compose -f docker-compose.base44.yml up -d --build`
- The Vite dev server runs on port 5173 inside the container, mapped to host port 3000.
- No lockfile exists; `npm install` runs on container startup.
- No external credentials or secrets are required to boot the app.

## Verification
- After starting, curl `http://localhost:3000/` — it should return the Vite HTML shell.
- The app has no routes defined (empty PAGES object), so it renders a blank layout by design.
