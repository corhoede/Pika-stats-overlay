# Pika Stats DLL (Minecraft 1.8 / tested on Lunar)

Windows overlay for Minecraft 1.8 that reads players from the current world/TAB list and shows per-player stats with cache-first loading.

## What this project does
- Reads players from the active Minecraft world and TAB list.
- Shows a live overlay table with:
  - Level
  - Rank
  - Name
  - Wins / WLR / FKDR / WS (or Practice columns)
  - Guild
  - UUID copy action
- Uses cache-first rendering so rows appear quickly.
- Updates missing/stale stats through Pika API requests.
- Supports optional nick resolve/unick flow through local resolver/DB setup.

## Main features
- TAB-driven loading flow (with optional auto-reload).
- Strong generation/cycle guards to prevent old-world data commits.
- Per-player incremental UI updates (no full-list blocking).
- Persistent SQLite cache for faster repeated loads.
- Dark theme UI with sorting and settings controls.

## Build (quick)
Run:
- `scripts/build_project2.bat`

Build output:
- `PlayerReader_project2.dll` (latest project build)
- `PlayerReader_main.dll` (current stable main copy)
- `releases/main/PlayerReader_main.dll`
- `releases/main/VERSION_MAIN.txt`

## Build (CMake)
Example:
- `cmake -S . -B build`
- `cmake --build build --config Release`


