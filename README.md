# Bike-sharing challenge 2026

For my colleagues, here's how to run the code on your machine.

## Requirements

- Python 3.12+
- `uv` installed and available on your PATH
- Git LFS installed (`git lfs version` should work)
- A local checkout of this repository

## Reproduce the workflow

1. Install Git LFS if needed, then initialize it:

   ```bash
   git lfs install
   ```

2. Clone the repository without automatically downloading every large data file, then fetch only the files used by the notebook:

   ```bash
   GIT_LFS_SKIP_SMUDGE=1 git clone https://github.com/haitam-l/Challenge-DASCI.git
   cd Challenge-DASCI
   git lfs pull --include="data/bike_types.csv,data/bikes.csv,data/cities.csv,data/city_areas.csv,data/stations.csv,data/trips_small.csv"
   ```

3. Install the project and development dependencies:

   ```bash
   uv sync --group dev
   ```

5. Open `notebooks/data_analysis.ipynb` in Jupyter and run all cells from top to bottom.

## Notes

- The notebook follows the preprocessing logic described in the paper cited in the notebook: it keeps bikes with trip records and known propulsion types, assigns a primary city per bike based on the longest cumulative trip duration, and keeps cities with at least 10 bikes.
- If you are using VS Code, open the folder and select the project environment created by `uv` as the Python interpreter before running the notebook cells.
