# SMAC Tournament Manager

A single-file web app for running a martial arts tournament for **Southern Martial Arts, Inc. (SMAC)**. It handles competitor registration, roster management, division assignments, scoring, and a printable awards sheet.

The whole app lives in one file, `smac_app.html`. There is no build step and no server to run.

## Features

- **Register**: Enter competitor details (name, age, gender, contact info, rank/belt, instructor, school/club) and choose events (Kata, Sparring, Weapons). Waivers are not handled in the app; they are collected when competitor tickets are sold. Each competitor is assigned a bib number automatically.
- **Roster**: Search and review everyone registered, edit or remove entries, and import registrations from a spreadsheet.
- **Divisions & Scoring**: View competitors grouped by division for each event, enter placings (1st, 2nd, 3rd), and print the current view for ring coordinators.
- **Results**: Automatic point totals per competitor across events with overall rankings (ties share a rank), plus a printable awards sheet.
- **Settings**: Edit the tournament name, subtitle, date, and location; customize scoring points per place (default 5 / 4 / 3); edit division lists; back up and restore all data.
- **Light and dark themes**: Follows your device setting.

## Importing registrations

The roster can import from Excel or CSV files. Columns are matched automatically by header name (for example "First Name", "Last Name", "Age", "Rank", "Instructor", "School", "Kata", "Sparring", "Weapons"), and you can adjust the column mapping before confirming the import.

## Exports

- Roster to CSV or Excel (`.xlsx`, with Registration, Results and Divisions sheets)
- Results to Excel
- Full backup to JSON, restorable from Settings

## Using the app

Open `smac_app.html` in any modern browser, or host it as a static page (for example with GitHub Pages).

### Where data is stored

| Where it runs | Data storage | File exports |
| --- | --- | --- |
| Published on claude.ai | Synced to a shared database, so it is available on any computer you are signed in to | Available |
| Any other host, or opened directly from disk | Saved in that browser's local storage only ("Saved on this computer only") | Disabled (the export buttons are greyed out) |

Because browser-only storage can be cleared, use **Settings → Export full backup** regularly if you run the app on the claude.ai-hosted version, and treat any other host as single-computer use.

## Tech notes

- Plain HTML, CSS and JavaScript in one file
- [SheetJS](https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js) (loaded from cdnjs) for Excel import and export
- Google Fonts (Bebas Neue, Work Sans)
- Storage and file downloads use the claude.ai runtime when available and fall back to browser local storage otherwise

## Customizing

Default tournament details, scoring points and division lists are defined near the top of the script in `smac_app.html` (`defaultState()` and the `*_DIVISIONS` lists). Colors are CSS variables at the top of the `<style>` block.
