## Purpose

Concise instructions to help an AI coding assistant be immediately productive in this repository.

## Big picture
- This repo contains cryptocurrency analysis assets: raw API data, cleaned datasets, Power BI artifacts (measures/DAX), and final outputs.
- Major folders: `Raw_Data`, `Clean_Data`, `REPORT`, `RESULT` — follow these locations when reading or writing data and outputs.
- Power BI is the primary presentation layer; many analytical expressions are implemented as DAX in `Clean_Data/READme.md`.

## Key files to read first
- [README.md](README.md): project overview and data layout.
- [Clean_Data/READme.md](Clean_Data/READme.md): canonical DAX measures (momentum, scores) and naming of key columns (e.g. `price_change_percentage_7d_in_currency`, `price_change_percentage_24h_in_currency`).
- `Raw_Data/api.txt`: contains API endpoints/source notes for reproducing raw pulls — treat it as the source of truth for data origins.

## Project conventions and patterns
- Folder intent:
  - `Raw_Data`: raw API responses and source notes.
  - `Clean_Data`: processed datasets and documentation of calculations (DAX snippets live here).
  - `REPORT`: Power BI report files, dashboards, and DAX documentation.
  - `RESULT`: final exported analysis and CSV/visual outputs.
- Naming: existing DAX and dataset column names are lowercase with underscores; preserve these names when adding scripts or tables to avoid breaking DAX measures.
- Calculations: momentum and scoring logic are implemented in DAX (see `Clean_Data/READme.md`). If adding derived columns, ensure their names match those referenced by the DAX measures.

## Developer workflows (what to run / tools required)
- Required: Power BI Desktop is expected for viewing and editing reports (mentioned in `README.md`).
- There are no repository-level build or test scripts visible — assume manual runs: update cleaned data, open Power BI desktop, refresh visuals, export to `RESULT`.

## Integration points & external dependencies
- Data sources: follow `Raw_Data/api.txt` for endpoints; scripts that re-ingest data should record or update that file.
- Power BI files in `REPORT` depend on the column names in `Clean_Data`; renaming columns will break measures.

## How an AI assistant should act here (practical rules)
- Read `Clean_Data/READme.md` before changing data columns or adding transformations — DAX formulas rely on exact column names.
- Do not modify `REPORT` Power BI files unless you can preserve existing field names and notify maintainers; prefer adding new datasets or fields rather than renaming.
- When adding scripts that fetch or clean data, commit the script under a clear path (e.g. `scripts/` or `ingest/`) and add an entry to `Raw_Data/api.txt` describing its source and schedule.
- Avoid placing credentials in `Raw_Data`; if a new credentials file is required, document secrets handling and add it to `.gitignore`.

## Examples (concrete snippets from this repo)
- Momentum rating logic lives in `Clean_Data/READme.md` (see `MOMENTUM RATING` DAX) — preserve its inputs when adding upstream transforms.
- Growth momentum uses `price_change_percentage_7d_in_currency` and `price_change_percentage_24h_in_currency`; keep these fields numeric and present for all rows used in DAX aggregation.

## When to ask the maintainer
- If you must rename a column referenced in `Clean_Data/READme.md` or `REPORT` assets.
- If you plan to add automated ingestion jobs or CI (no CI found in this repo yet).

## Next steps for contributors
- If adding reproducible scripts: include a short README in the same folder describing commands to run, required packages, and where outputs land (prefer `RESULT` for final exports).

---
If anything above is unclear or you'd like more detail (for example, suggested script templates or a CI plan), tell me which area to expand.
