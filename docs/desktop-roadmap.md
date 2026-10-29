# Desktop Distribution — Public Roadmap

**Status: architecture and feasibility; not a released product.**

Pelagium's existing offline Docker laboratory proved that a personal reading journal can work without external servers. The next objective is to **remove the operational burden from the reader**.

## Intended reader experience

1. Download a signed/verified Windows installer.
2. Install with an ordinary graphical setup.
3. Open Pelagium as a regular desktop application.
4. Create or import a personal journal.
5. Continue reading and editing without a VPS, domain, Docker commands or internet access for core functions.

A new journal must not require possession of any old encrypted-backup key. Recovering an older encrypted archive, however, still requires its matching key. An accessible old journal may support a separately implemented portable export.

## Engineering milestones

| Milestone | Purpose | State |
|---|---|---|
| DESKTOP-1 | Review reuse of React/FastAPI, local storage and packaging | In design |
| DESKTOP-2 | Bundle backend and database with automatic lifecycle | Not started |
| DESKTOP-3 | Build complete offline-capable Windows installer | Not started |
| DESKTOP-4 | Provide graphical import/export/backup and recovery | Not started |
| DESKTOP-5 | Independently test Windows installation, offline use and updates | Not started |

## Important unresolved choices

- SQLite compatibility with models, migrations and concurrency vs. bundling PostgreSQL.
- A native shell (such as Tauri) and a packaged Python backend, with a restricted local communication boundary.
- User-private data location and failure-safe upgrades.
- Installer size, included Windows WebView prerequisites, signing, integrity and software updates.

No source code, secrets, database samples or private infrastructure details are published as part of this roadmap.

The online beta follows a **separate** security and deployment review.
