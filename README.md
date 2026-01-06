# crypto_analysis

Short project description
-------------------------
crypto_analysis is a data-analysis repository that processes cryptocurrency market data, produces cleaned datasets, and provides Power BI report artifacts (DAX measures and visuals) for momentum, growth and trend analysis.

Key features
------------
- Cleaned datasets and data lineage for crypto market metrics (price, market cap, % changes)
- Canonical DAX measures for momentum scoring and ratings (see `Clean_Data/READme.md`)
- Power BI report files for visual analysis and exports in `RESULT`

Tech stack / tools
------------------
- Power BI Desktop for report creation and visualization
- CSV / flat-file datasets stored under `Clean_Data` and `Raw_Data`
- DAX for calculated measures (documented in `Clean_Data/READme.md`)

Repository layout
-----------------
- `Raw_Data/`: raw API responses, export logs and `Raw_Data/api.txt` with endpoints/source notes
- `Clean_Data/`: processed datasets, cleaning notes and canonical DAX expressions ([Clean_Data/READme.md](Clean_Data/READme.md))
- `REPORT/`: Power BI report files and PBIX artifacts
- `RESULT/`: final exports (CSV, images, reports)

Getting started
---------------
1. Clone the repository:

	git clone <repository-url>

2. Install tools:

- Install Power BI Desktop to open and refresh PBIX files.
- Use your preferred data tools (Python/R/Excel) for any new data processing scripts you add.

3. Inspect the canonical measures:

- Open [Clean_Data/READme.md](Clean_Data/READme.md) to review DAX implementations used by the reports.

Data sources & ingestion
------------------------
- Data sources and API endpoints are recorded in `Raw_Data/api.txt`. If you add or update ingestion scripts, update this file with the source, cadence and any authentication requirements.
- Preserve column names used by DAX measures (e.g. `price_change_percentage_7d_in_currency`, `price_change_percentage_24h_in_currency`). Renaming these fields will break the Power BI measures.

Working with Power BI reports
----------------------------
- Open PBIX files in `REPORT/` with Power BI Desktop.
- After updating `Clean_Data` datasets, use Power BI Desktop to refresh data sources and verify visuals and measures.

Contributing guidelines (quick)
------------------------------
- Before changing column names or DAX measures, discuss changes with the maintainers.
- Put ingestion/processing scripts under a clear path such as `scripts/` or `ingest/` and update `Raw_Data/api.txt`.
- Do not commit secrets or credentials. If needed, document secret handling and add credential filenames to `.gitignore`.

Examples & notes
----------------
- Momentum rating and scoring logic are defined in `Clean_Data/READme.md` (search for `MOMENTUM RATING`, `MOMENTUM SCORE`, `GROWTH MOMENTUM`). Keep upstream transforms aligned to these inputs.

License
-------
See the project `LICENSE` file for license terms.

Need more detail?
-----------------
If you'd like, I can:
- Add a data-ingestion script template (Python) and a small README for `scripts/`.
- Draft a short CONTRIBUTING.md with PR and issue guidelines.

Please tell me which of the above you'd like next.

Contact
-------
For questions, collaboration, or issues, contact the project maintainer: shwetavishwakarma042@gmail.com
