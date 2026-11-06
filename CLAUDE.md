# Marine time series analysis (BioTIME)

Goal: time series analysis of marine assemblages using BioTIME v2 (2025),
https://biotime.st-andrews.ac.uk/

## Layout

- `data/biotime/` – raw downloads (do not modify)
  - `biotime_v2_metadata_2025(1).csv` – 708 studies, one row per `STUDY_ID`
  - `biotime_v2_rawdata_2025.rds` – ~12M rows, species × sample, joined by `STUDY_ID`
  - `biotime_marine_metadata.rds`, `biotime_marine_rawdata.rds` – marine subset (made by `01_import_marine.qmd`)
- `R/` – RStudio project (`biotime_marine.Rproj`) and numbered Quarto notebooks
- `eDNA cores/` – separate, not yet used

## Conventions

- Notebooks are numbered `NN_description.qmd` in `R/`; paths are relative to `R/` (`../data/biotime`).
- Use tidyverse (`dplyr`, `ggplot2`).
- Later notebooks load the saved marine `.rds` files rather than the full raw data.
- Quarto isn't on the shell PATH; render with
  `/Applications/RStudio.app/Contents/Resources/app/quarto/bin/quarto render <file>.qmd`
- Git repo at `time_series/` (branch `main`, remote `origin` = github.com/ngeraldi/Marine-timeseries, public). `data/`, rendered HTML and RStudio files are gitignored.
- BioTIMEr (CRAN, not installed yet) – use for gridding, rarefaction, alpha/beta metrics.

## Log

Claude: at the end of each working session, add a dated entry recording what was done,
key results and decisions made, and update "Next steps".

### 2026-11-06
- Created R project and `01_import_marine.qmd`: import full BioTIME, filter `REALM == "Marine"`.
- Result: 229 marine studies, ~5.2M rows. Taxa: 118 invertebrates, 67 fish, 18 multiple,
  12 plants, 11 birds, 3 mammals. Study duration median 10 yr (range 2–130).
- Added CLAUDE.md and set up git.

## Next steps / open questions

- Choose minimum time series length (e.g. ≥5 or ≥10 sampled years).
- Decide whether to grid/rarefy with BioTIMEr.
