# H2Global meets Africa: Power-to-X Opportunities in Kenya

Branch: [PtX-Kenya](https://github.com/pypsa-meets-earth/pypsa-earth)

Input & Results: [![DOI](https://zenodo.org/badge/451538981.svg)](...)

## Respository structure
- `config`: contains configuration files for PyPSA-Earth (Kenya).
- `workflow/envs:` contains the environment used for PyPSA-Earth.
- `workflow/notebooks:` contains the Jupyter notebooks and Python files used for the evaluation of results
- `workflow/pypsa-earth:` contains the PyPSA-Earth branch used for this calculations.

## Installation and usage
1. Open your terminal at a location where you want to install the repository PtX-Opporunity-Kenya including it's subworkflows PyPSA-Earth. Type the following in your terminal to download the packages and the dependencies (pypsa-earth) from GitHub. Note that the tag `--recursive-submodules` is needed to automatically clone also the pypsa-eur and pypsa-earth dependencies.
   
   ```bash
   git clone --recurse-submodules https://github.com/AlexanderMeisinger/PtX-Opportunity-Kenya.git
   ```
   
2. Move the current directory to the head of the repository.
   
   ```bash
   .../some/path/without/spaces % cd PtX-Opportunity-Kenya
   ```
   
3. The PyPSA-Earth python package requirements are curated in the `workflow/pypsa-earth/envs/environment.yaml` of the PyPSA-Earth respository. The environment can be installed using conda or mamba:
   
   ```bash
   .../PtX-Opportunity-Kenya % conda env create -f workflow/pypsa-earth/envs/environment.yaml
   ```
   
4. For running the optimisation one has to install the solver. We can recommend the open source `HiGHs` solver, see more details on solvers in the documentation of [PyPSA-Earth](https://pypsa-earth.readthedocs.io/en/latest/index.html). The optimisation in this work was performed using the commercial `Gurobi` solver.

## Run scenarios
For starting the PyPSA-Earth model, run the following command:
```bash
.../PtX-Opportunity-Kenya/workflow/pypsa-earth % conda activate pypsa-earth-PtX-Kenya
```
```bash
% Quick check
% snakemake --cores all solve_all_networks --configfile .../PtX-Opportunity-Kenya/config/config.yaml -n
```
```bash
% Full run
% snakemake --cores all solve_all_networks --configfile .../PtX-Opportunity-Kenya/config/config.yaml
```

Please follow the documentation of [PyPSA-Earth](https://pypsa-earth.readthedocs.io/en/latest/index.html) for more details. The estimated time to run one single optimisation is 3o mins on a standard laptop.

## Reproducibility
The project results and analysis can be reproduced using the notebooks in `workflow/notebooks` after successfully running the scenarios in `config`.

## Result and input data
A dataset of the model results will be available on Zenodo under a CC-BY-4.0 license. Please refer to the documentation of [PyPSA-Earth](https://pypsa-earth.readthedocs.io/en/latest/index.html) for details on the input data.

## License
The code in this repo is MIT licensed, see ./LICENSE.md.
