# Data access and handling

The analysis requires an authorized SEER*Stat case-listing text export covering diagnosis years 2018–2020, named `NEW_CRC_2018-2020.txt` by default.

Place the file in this `data/` directory. The notebook checks both `data/NEW_CRC_2018-2020.txt` (when launched from the repository root) and `../data/NEW_CRC_2018-2020.txt` (when launched from `notebooks/`). To use another path, set the `SEER_DATA_FILE` environment variable before starting Jupyter.

The source patient-level file is not included in this repository. Obtain it through the applicable SEER access process and comply with all data-use conditions. The analysis reads the export as text and expects the SEER field names documented in the notebook's data-loading section. If the export uses different field labels, inspect and adapt that section carefully.

Never commit patient identifiers, restricted patient-level data, or other records that you are not authorized to redistribute. The `.gitignore` file excludes common local data formats, but authors must still inspect every commit before publishing.
