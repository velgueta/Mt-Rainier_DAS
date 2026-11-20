# Rainier — phase picker results

**20 November 2026. This is the small working folder: 15 CSV files.**

The earlier 228-file folder was an exhaustive archive. It included experiments,
threshold/radius variants, repository snapshots and intermediate outputs. Those
are not needed for the current comparison and remain in the separate full archive.

## Files to use

| Folder | CSVs | What is included |
| --- | ---: | --- |
| `01_DAS` | 5 | PhaseNet-DAS/GaMMA: 942 candidates and 478 reviewed records; PhaseNet-DAS/PyOcto: 778 candidates and 514 reviewed records; complete ELEP-DAS/PyOcto review: 99 candidates, 39 accepted, 60 rejected |
| `02_STATIONS` | 4 | GaMMA and PyOcto associations, each for five stations and all stations |
| `03_TEMPLATE_MATCHING` | 2 | Working DAS detections (85, CC > 0.07) and station detections (92) |
| `04_COMCAT` | 2 | Regional reference (942 earthquakes) and the saved expanded 1000-km source |
| `05_RESULTS` | 2 | Consolidated current results at ±7 s and the seven-event ELEP nonmatch audit |

For analysis, start with the **reviewed PhaseNet CSVs**. The candidate CSVs retain
the original association populations and are not additional catalogs to add to
the reviewed records. For ELEP, use `confirm == yes` or `review_status == confirmed`;
there is no need to keep separate accepted/rejected CSVs.

## Current comparison

Use **PyOcto for both DAS pickers** when comparing PhaseNet and ELEP:

- PhaseNet-DAS: **514 reviewed records**; ELEP-DAS: **39 accepted records**.
- PhaseNet–ELEP: **32** temporal matches.
- PhaseNet–ComCat regional: **208**; ELEP–ComCat regional: **26**.
- All three: **26**. The ELEP records split into **26 with both counterparts,
  6 with PhaseNet only, and 7 with neither**.

The GaMMA figures use the separate **478-record PhaseNet-DAS selection**.
Five-station GaMMA has **266 records**; all-station GaMMA has **1,384 raw rows**,
of which **1,383** fall in the common interval. PyOcto station sources have
**354** five-station and **1,495** full-network rows. Do not mix the associators.

## Settings and unresolved points

- Common UTC interval: **23 August 2023 21:00 inclusive to 22 November 2023
  00:00 exclusive**. Two rejected ELEP candidates fall before this interval.
- **±7 seconds**, one-to-one temporal matching. No DAS clock correction applied.
  The reported ~12-second clock problems still need a measured sign and date range.
- Regional ComCat: **45–48 N, 123–120 W**. The 25-km Rainier reference can be
  selected from this file using center **46.879967 N, 121.726906 W**; it contains
  **216** events in the common interval. No extra 25/30/100/200/300/500-km CSVs
  are necessary for the working set. The 1000-km file is kept for extended screening.
- **ELEP 88–89 may be the same earthquake.** They remain unconsolidated;
  39 is the number of accepted records, not a finalized distinct-earthquake count.
- The seven ELEP nonmatches are **21, 22, 24, 26, 45, 49, 89**. Zero match ComCat
  at ±7 s; five have nearby catalog times 12–30.2 s away. Do not call these seven
  new earthquakes before clock/phase/duplicate review.
- Station-TM production stations are unverified. The 92 detections cannot yet
  be described as a controlled five-station TM run.
- ELEP-DAS/GaMMA did not produce a completed catalog. There is no such result
  file in the working set.

## Resume

Open **`Reproduce_current_results.ipynb`** and choose **Run All**. It uses only
the CSVs in this folder, recalculates the current matches, and writes new outputs
to `generated/`. Install dependencies with `python -m pip install -r requirements.txt`.
The existing figures are in `FIGURES/`; no title paragraphs or notes are drawn
inside them.

`CURRENT_FILES.json` describes the 13 input catalogs. `CURATION_REVIEW.json`
records the review of all 228 CSVs, which 14 existing files were selected, and
why the other files remain archive-only. The fifteenth CSV is the consolidated
current-results table. Original files and the full archive were not deleted.
