<p align="center">
  <img src="https://i.ibb.co/HTfd2SPz/Chat-GPT-Image-Sep-3-2026-04-46-44-AM.png" width="100%" alt="NORA Research Lab banner">
</p>

<p align="center">
  <a href="https://github.com/Nora-Research-Lab"><img src="https://img.shields.io/badge/GitHub-Nora--Research--Lab-181717?logo=github" alt="GitHub"></a>
  <a href="https://huggingface.co/NoraResearchLab"><img src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-NoraResearchLab-yellow" alt="Hugging Face"></a>
  <a href="https://www.linkedin.com/company/nora-research-lab"><img src="https://img.shields.io/badge/LinkedIn-NORA%20Research%20Lab-0A66C2?logo=linkedin" alt="LinkedIn"></a>
  <a href="https://x.com/noraresearchlab"><img src="https://img.shields.io/badge/X-@noraresearchlab-000000?logo=x" alt="X"></a>
</p>

## Quick Links
- [GitHub](https://github.com/Nora-Research-Lab)
- [Hugging Face](https://huggingface.co/NoraResearchLab)
- [LinkedIn](https://www.linkedin.com/company/nora-research-lab)
- [X](https://x.com/noraresearchlab)

# NGDOD — National Geochemical Database on Ore Deposits: Legacy Data

1,558,396 samples, 5,398,750 measurements. Nearly 30,000 historic
ore and ore-related rock samples from U.S. mineral deposits and mining
districts, covering 15 mineral system types and
42 mineral deposit types. Modernized from the USGS
ScienceBase data release into two linked GeoParquet tables for AI, API, and
GIS use.

## Scope
No geological reinterpretation or machine-learning modelling was performed —
this is a structural modernization only, preserving the original geochemical
measurements, spatial information, and provenance.

## Contents
- `geoparquet/samples.parquet` — one row per sample: identifying/metadata columns (including mineral system/deposit type where present), latitude, longitude, point geometry (EPSG:4326)
- `geoparquet/measurements.parquet` — long format: one row per (sample, analyte), join back to samples on `row_uid`
- `metadata.json` — provenance, citation, counts, standardization notes, known caveats

## Why two tables instead of one wide table
The legacy database mixes many analytical methods with inconsistent
per-method columns across historic submissions. Splitting sample metadata
from analyte measurements (long format) avoids hundreds of mostly-empty
columns and is the standard structure for programmatic geochemistry access.

## Caveats
Analyte vs. identifying/metadata columns were split per source table using keyword heuristics on column names (see ID_COLUMN_HINTS in the build notebook), not a hand-verified data dictionary — cross-check analyte column meanings against USGS documentation files bundled in the raw download before treating this as authoritative for a specific element or deposit type.

## Source & Citation
Granitto, M., Hofstra, A.H., Schmidt, D.E., and Khoury, R.M., 2021, National Geochemical Database on Ore Deposits: Legacy data: U.S. Geological Survey data release, https://doi.org/10.5066/P944U7S5

## License
CC0 1.0 Universal
