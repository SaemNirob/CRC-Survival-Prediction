# Reproducibility checklist

- [ ] Obtain the authorized SEER*Stat export for the study's 2018–2020 diagnosis years.
- [ ] Save it as `data/NEW_CRC_2018-2020.txt`, or set `SEER_DATA_FILE` to its location.
- [ ] Use Python 3.10.x and install dependencies from `requirements.txt` or `environment.yml`.
- [ ] Launch Jupyter from either the repository root or `notebooks/`; the notebook resolves the default data and results paths from either location.
- [ ] Run every notebook cell from top to bottom without skipping cells.
- [ ] Confirm cohort counts, exclusion counts and split checks against the final manuscript.
- [ ] Confirm the 2018–2019 development cohort and 2020 temporal test cohort do not overlap at patient level.
- [ ] Confirm outcome coding and the 36-month prediction horizon.
- [ ] Review all generated tables and 600-dpi figures.
- [ ] Confirm the final reproducibility assertions pass.
- [ ] Record operating system, Python and package versions, SEER release/version, and notebook revision for the manuscript/supplement.
- [ ] Inspect the Git history and final archive to ensure no restricted data, identifiers, credentials, or temporary files are included.

The notebook's final assertions check model refitting and calibration consistency. They do not constitute independent external validation or establish clinical utility.
