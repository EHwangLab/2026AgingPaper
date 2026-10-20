# Aging PPC figure reproduction

This repository contains the standalone notebook used to reproduce the main and supplementary figures for the Hwang Lab aging/PPC study. It generates 88 SVG figures and 147 CSV source/statistics tables in `outputs/` while preserving the plotting procedures used for the paper.

## Quick start

Python 3.12 is recommended. From a terminal:

```bash
git clone https://github.com/EHwangLab/2026AgingPaper.git
cd 2026AgingPaper

python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements-modern.txt
python -m ipykernel install --user --name aging312 \
  --display-name "Python 3.12 (2026 Aging)"

python -m jupyter lab HwangLab_Aging_PPC_Figures.ipynb
```

On Windows, activate the environment with `.venv\Scripts\activate` instead of `source .venv/bin/activate`.

In JupyterLab, select **Python 3.12 (2026 Aging)** and choose **Run → Run All Cells**. If `HwangLab_Aging_Data/` is not already beside the notebook, the first code cell downloads and extracts [HwangLab_Aging_Data.zip](https://zenodo.org/records/22131935/files/HwangLab_Aging_Data.zip?download=1) from Zenodo.

A complete run takes approximately three minutes on the validation workstation and generates about 75 MB of output. Download and extraction time depends on the network and storage system.

## Data

The publication dataset will be available from [Zenodo (DOI: 10.5281/zenodo.22131935)](https://doi.org/10.5281/zenodo.22131935). The notebook uses a local `HwangLab_Aging_Data/` directory when present and otherwise downloads the archive from Zenodo. Input data are not modified.

## Reproducibility environments

Python 3.12 with `requirements-modern.txt` is the recommended environment for readers. It reproduces the same figures, tables, and scientific conclusions as the paper environment. Minor text placement, layout, raster sampling, and tied heatmap row ordering can differ because of changes in Matplotlib and NumPy.

The notebook retains stored output from the paper-exact Python 3.8 run. To regenerate that output, create a separate archival environment using `requirements.txt`:

```bash
python3.8 -m venv .venv-paper-exact
source .venv-paper-exact/bin/activate
python -m pip install --upgrade "pip<25"
python -m pip install -r requirements.txt
python -m ipykernel install --user --name aging38 \
  --display-name "Python 3.8 (2026 Aging)"
python -m jupyter lab HwangLab_Aging_PPC_Figures.ipynb
```

Select **Python 3.8 (2026 Aging)** in JupyterLab for this archival run. Python 3.8 is end-of-life and is provided only for exact reproduction of the stored paper output.

Figure S7g has one version-dependent reporting difference: SciPy 1.6.2 uses a normal approximation for three Wilcoxon tests, whereas SciPy 1.12.0 uses the exact distribution. The reported p-values differ, but the Wilcoxon statistics and significance conclusions are unchanged.

## Repository contents

- `HwangLab_Aging_PPC_Figures.ipynb` — figure-reproduction notebook with paper-exact stored output.
- `requirements-modern.txt` — recommended Python 3.12 environment.
- `requirements.txt` — archival Python 3.8 paper-exact environment.

## License

Source code in this repository is licensed under the [BSD 3-Clause License](LICENSE). The Zenodo dataset is licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). The manuscript and published figures follow the journal's publication terms.

Please cite the associated manuscript and Zenodo dataset when using these materials.
