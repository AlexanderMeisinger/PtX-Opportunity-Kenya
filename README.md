# More electricity, less dependency: Renewable Power-to-X Opportunities for Kenya

Energy Model: [PtX-Kenya](https://github.com/AlexanderMeisinger/pypsa-earth/tree/pypsa-kenya)

Zenodo: [![DOI](https://zenodo.org/badge/21497408.svg)](https://zenodo.org/badge/latestdoi/21497408)

Project: [H2Global meets Africa](https://fenes.oth-regensburg.de/en/forschung/projekte/h2-global-africa)

## Abstract
Kenya has one of the cleanest electricity systems in Africa. Almost 90% of its electricity is already generated from renewable sources, while 76% of the population has access to electricity. At the same time, the country has set ambitious targets under its Vision 2030 strategy: to achieve universal electricity access; to establish a fully renewable electricity system; and to increase energy independence by producing key Power-to-X (PtX) products, such as ammonia and methanol, domestically. Together with the country's exceptional geothermal resources along the Great Rift Valley, these ambitions could position Kenya as a promising case for renewable Power-to-X development.

This research develops and applies the open-source energy system model PyPSA-Earth, including a detailed representation of Kenya's geothermal resources along the Great Rift Valley, to assess future electricity system development and PtX opportunities. Three scenarios are analysed: (i) a Base Scenario achieving 100% renewable electricity and universal electricity access, (ii) a Low Independence Scenario additionally covering domestic production of 100 kt ammonia (20% of domestic demand) and 5 kt methanol (100% of domestic demand), and (iii) a High Independence Scenario with 350 kt ammonia production (50% of domestic demand) and 5 kt methanol production. To evaluate the strategic role of geothermal energy, a sensitivity analysis is conducted using various geothermal capacity limits.

Geothermal energy emerges as the least-cost expansion option for Kenya, followed by solar photovoltaics. Providing universal electricity access by 2030 while increasing domestic ammonia and methanol production requires up to 3.4 GW of installed geothermal capacity, representing an increase of 2.5 GW compared to 2023. If geothermal deployment is limited to 2 GW, up to 8 GW of additional solar photovoltaic capacity is required, increasing total system costs by €600 million. Additional storage requirements for balancing variable solar generation are a key driver of the cost increase, highlighting the economic value of baseload geothermal generation. Overall, the findings underline the strategic importance of Kenya's geothermal resources for cost-effective renewable electricity expansion and the development of a domestic green Power-to-X industry.

Further information and detailed results are available here: [PtX-Opportunities-Kenya](https://github.com/user-attachments/files/30275570/2026_Meisinger_H2G-A_PtX-Kenya.pdf)


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
A dataset of the model results available on [Zenodo](https://zenodo.org/badge/latestdoi/21497408) under a CC-BY-4.0 license. Please refer to the documentation of [PyPSA-Earth](https://pypsa-earth.readthedocs.io/en/latest/index.html) for details on the input data.

## Acknowledgement
We gratefully acknowledge funding from the H2Global meets Africa project (03SF0703A) by the German Federal Ministry
of Research, Technology and Space.

## License
The code in this repo is MIT licensed, see ./LICENSE.md.
