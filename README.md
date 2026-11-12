# High-Residual-Content Aluminum Automotive Body Sheet — MSEC2027

Supporting information, model inputs, and optimization scripts associated with:

**Impact of Using High-Residual-Content Recycle Friendly Alloys on the Recycled Content of Aluminum Automotive Body Sheets in the United States**

**Authors:** Alissa Tsai, Ala'aldin Alafaghani, Constantin Chiriac, Daniel Freiberg, George Luckey, and Daniel R. Cooper.  
**Conference:** ASME Manufacturing Science and Engineering Conference (MSEC2027), June 21–25, 2027, Corvallis, Oregon.

## Repository contents

| Location | Description |
| --- | --- |
| [`supplementary/SI1.pdf`](supplementary/SI1.pdf) | Supplementary methods, Table S1, Figures S1–S5, and references. |
| [`supplementary/SI2.xlsx`](supplementary/SI2.xlsx) | DMFA data, composition inputs, recycling metrics, 2050 optimization results, ranked composition constraints, and frozen/moderate/aggressive emissions-factor data. |
| [`domestic_Al.py`](domestic_Al.py) | Main Gurobi-based aluminum blending optimization and results-processing code. |
| [`iterate_Al.py`](iterate_Al.py) | Script to iterate over scenarios and years and export calculated results. |
| [`Input data/`](Input%20data/) | Excel inputs used by the scripts, including scenario definitions, demand, scrap flows, alloy chemistry, and emissions factors. |
| [`documentation/`](documentation/) | SI1 LaTeX source files; the original figure and bibliography dependencies are not all included in this archive. |

## Model overview

The Python model optimizes blends of primary materials, production scrap, and post-consumer scrap subject to scrap availability, alloy composition, melting-yield, and furnace-charge constraints. The scenario inputs include conventional ABS compositions and high-residual-content (HRC) variants. The scripts also read process-specific emissions intensities for frozen, moderate, and aggressive decarbonization pathways.

## Running the supplied scripts 

The scripts use **Python**, `numpy`, `pandas`, **Gurobi** (`gurobipy`, with a valid license), and Excel-reading/writing dependencies (including `openpyxl` and `xlsxwriter`). Exact software versions have not been established.

The script currently looks for `domesticABS_scenarios.xlsx` and the referenced Excel inputs **relative to the working directory**, while those inputs are stored under `Input data/`. From the repository root, a possible invocation is:

```bash
cd "Input data"
python ../domestic_Al.py
```

`domestic_Al.py` currently defaults to the **Baseline scenario in 2050** when executed directly. `iterate_Al.py` contains a larger hard-coded scenario list, processes 2020–2050, and writes outputs to `RESULTS/`. To run that script from the same input directory:

```bash
python ../iterate_Al.py
```

These are **source-inspection instructions, not verified successful execution commands**. Scenario names and all input references should be checked before running, and additional input corrections may be required. `iterate_Al.py` runs many scenarios and may be computationally expensive.


## Relationship to previous work

The existing model repository for the related study by Tsai and coauthors is [ReMaDe-Al-ABS-LP](https://github.com/alitsai6/ReMaDe-Al-ABS-LP). This repository is organized around the separate MSEC2027 HRC alloy study.

## Updates and feedback

Corrections to the supporting data, code, and documentation can be tracked through Git commits and GitHub Issues. Any model changes made after the initial conference submission should be described in commit messages and, where appropriate, noted in a release description.

## License

No reuse license has been assigned pending agreement among the authors and relevant data owners. Public visibility does not, by itself, grant reuse rights.
