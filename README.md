## A Semi-Structural Model of the Danish Economy

This repository contains the source code for estimating a semi-structural model of the Danish economy based on the paper [Hasenzagl, T., Pellegrino, F., Reichlin, L., & Ricco, G. (2020). A Model of the Fed's View on Inflation.](https://arxiv.org/abs/2006.14110)

## Code structure
The main directory is organized as follows:

* *annex_global_data*: Contains a directory with the data files, `tc_mwg.jl`, and `iis_charts.ipynb` for the model with global variables. To estimate this model use these files instead of the files with the same names in the *data* and *code* directories. The dataset for the global model includes the Baltic Dry Index (BDI) which is available here: https://www.balticexchange.com/en/index.html. 
* *code_main*: Contains all of the Julia code necessary for estimating the model
    + The *Metropolis-Within-Gibbs* subdirectory contains the code for the Metropolis-Within-Gibbs algorithm
* *csv_output*: Used for storing the .csv output files.   
* *data*: Contains the data used in the estimation. The data is saved in .csv and .xlsx files.
* *docs*: Contains the original paper and online appendix by Hasenzagl et. al (2020).
* *img*: Used for storing the output figures.

The code is written in Julia 1.7 (https://julialang.org/).

The code uses a number of Julia packages. All necessary packages can be installed using the `import_packages.jl` script. To do so, start Julia and use the following command at the Julia REPL prompt:

`julia> include("import_packages.jl")`

## Running the code

The main file is `user_main.jl`. This script runs the following exercises:

* The in-sample estimation is run by setting `run_type=1` in `user_main.jl`.
    + Two different data sources are available: `inflation_DK_MONAshort` and `inflation_DK_MONAlong`.
* The conditional forecasting exercise is run by setting `run_type=2` and specifying the start date of the forecasting exercise, and the conditioning variables and time periods. Note that the paper does not include a conditional forecasting exercise.
* The out-of-sample forecasting exercise is run by setting `run_type=3` and specifying the start date of the forecasting exercise.

After choosing the `run_type` run the script by starting Julia and using the following command at the Julia REPL prompt:

`julia> include("user_main.jl")`

## Figures and Tables

The figures and tables are created in two Jupyter (https://jupyter.org/) notebooks:

* `iis_charts_noBConEP.ipynb`: creates all figures relating to the in-sample estimation.
* `oos_charts.ipynb`: creates all figures relating to the out-of-sample forecasting exercise and the RMSE of the trend-cycle model relative to the RMSE of a random walk with drift.
```
