# Jakarta Air Quality & Meteorology — Data Mining

A CRISP-DM data mining project exploring the relationship between air pollution (ISPU) and meteorological conditions across Jakarta monitoring stations for the 2024–2026 period.

## Datasets

| File | Records | Description |
| --- | --- | --- |
| `datasets/ISPU_2024-2025.csv` | ~3.5k | Daily Air Pollution Standard Index (ISPU) readings per station: PM10, PM2.5, SO₂, CO, O₃, NO₂, dominant pollutant, and category. |
| `datasets/Meteorologi_2024-2026.csv` | ~223k | Hourly/sub-daily meteorological observations per station: solar radiation (`grad`), air temperature, humidity, wind speed (`ff`), and rainfall. |

Both datasets share a common `stasiun` / `stasiun_pengamatan` key and a `periode_data` (YYYYMM) temporal field, enabling a station-and-time join.

## Prerequisites

- [Python 3.13+](https://www.python.org/)
- [uv](https://docs.astral.sh/uv/) for dependency management

## Getting started

Clone the repository and install dependencies into an isolated environment:

```bash
uv sync
```

This creates a `.venv` and installs `pandas`, `numpy`, and `missingno` along with the `ipykernel` dev dependency.

## Reproducing the analysis

Launch Jupyter and open the analysis notebook:

```bash
uv run jupyter notebook data_inspection.ipynb
```

Alternatively, run the notebook end-to-end from the command line:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace data_inspection.ipynb
```

> [!NOTE]
> All paths in the notebook are relative to the project root. Run the notebook from the repository root so `datasets/*.csv` resolves correctly.

## CRISP-DM progress

This project follows the [CRISP-DM](https://en.wikipedia.org/wiki/Cross-industry_standard_process_for_data_mining) lifecycle. Current status:

- [ ] **Business Understanding** — define objectives and success criteria
- [x] **Data Understanding** — data inspection in `data_inspection.ipynb`
  - [x] Temporal range of each dataset
  - [x] Recording locations (stations)
  - [x] Data collection method / granularity per dataset
  - [x] Missing & null value assessment (via `missingno`)
  - [ ] Value distribution analysis per dataset
- [ ] **Data Preparation** — cleaning, joining, and feature engineering
- [ ] **Modeling** — model selection and training
- [ ] **Evaluation** — validate results against objectives
- [ ] **Deployment** — package and share findings

## Project structure

```
.
├── data_inspection.ipynb        # CRISP-DM: Data Understanding
├── datasets/
│   ├── ISPU_2024-2025.csv        # Air quality index readings
│   └── Meteorologi_2024-2026.csv # Meteorological observations
├── main.py
├── pyproject.toml                # Project metadata & dependencies
└── uv.lock                       # Pinned dependency lockfile
```
