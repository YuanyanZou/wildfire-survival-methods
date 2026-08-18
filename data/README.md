# Data Access

The row-level WiDS Worldwide Global Datathon 2026 data are intentionally not included in this repository.

To run the code:

1. Obtain `train.csv` from the [official Kaggle competition data page](https://www.kaggle.com/competitions/WiDSWorldWide_GlobalDathon26/data) and follow the applicable competition terms.
2. Place it at `data/train.csv`, or set the environment variable `WILDFIRE_DATA_PATH` to its local path.
3. Do not commit the file. The repository `.gitignore` excludes common row-level data formats under `data/`.

Expected analytic dimensions in the course report are 221 rows and 37 columns, with 69 observed events and 152 right-censored observations. The code validates required columns and reports the dimensions it actually reads.

See [data_dictionary.md](data_dictionary.md) for the variables used in the public code.

