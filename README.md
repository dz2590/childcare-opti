# Eliminating Child Care Deserts in New York State through Optimization

## Overview
This project develops two mixed-integer optimization models to estimate the minimum public funding required to eliminate child care deserts across New York State.

The workflow combines demographic, employment, income, child care capacity, and geographic data to:

1. identify ZIP codes that qualify as child care deserts,
2. estimate child care demand for children from two weeks through age 12,
3. enforce additional capacity requirements for children under age five,
4. choose between constructing new facilities and expanding existing facilities, and
5. compare a baseline budgeting model with a more realistic model that includes piecewise expansion costs and geographic spacing constraints.

Both optimization models achieved a reported **100% desert-elimination rate** for the ZIP codes included in the final model.

> **Course environment note:** This project was developed for Columbia University's IEOR 4004 Optimization Models and Methods course. The notebooks were originally run in Google Colab and use Gurobi. Reproducing the full workflow requires a valid Gurobi license and the included source datasets.

## Repository Structure
```text
├── README.md
├── code/
│   ├── Data Cleaning Part 1.ipynb
│   ├── Optimization_Budgeting_Problem1.ipynb
│   └── Optimization_Budgeting_Problem2.ipynb
├── data/
│   ├── raw/
│   │   ├── Public Data - Population By Age Group.xls
│   │   ├── Commercial Zipcodes.csv
│   │   ├── child_care_regulated.csv
│   │   ├── NYC Public Database - Child_Care_Regulated_Programs_20251005.csv
│   │   ├── avg_individual_income.csv
│   │   ├── employment_rate.csv
│   │   ├── population.csv
│   │   └── potential_locations.csv
│   └── processed/
│       └── Childcare Deserts FINAL.csv
├── results/
│   ├── optimization_result_problem1_final.csv
│   └── optimization_result_problem2_fin.csv
├── 4004_FinalReport.pdf
└── 
```

This organization separates the workflow into:

- `code/` for the data-cleaning and optimization notebooks
- `data/raw/` for original source files
- `data/processed/` for the cleaned modeling dataset
- `results/` for optimization outputs

## File Descriptions

### `code/Data Cleaning Part 1.ipynb`

Builds the final analysis-ready child care desert dataset by cleaning, merging, imputing, and transforming the source data.

### `code/Optimization_Budgeting_Problem1.ipynb`

Implements the baseline mixed-integer budgeting model for facility construction and expansion.

### `code/Optimization_Budgeting_Problem2.ipynb`

Implements the realistic model with:

- a 20% expansion cap,
- piecewise-linear expansion costs,
- geographic conflict detection, and
- ZIP-code-level limits on feasible new facilities.

### `results/optimization_result_problem1_final.csv`

Contains ZIP-code-level decisions and cost results from Model 1.

### `results/optimization_result_problem2_fin.csv`

Contains ZIP-code-level decisions and cost results from Model 2.

### `4004_FinalReport.pdf`

Contains the complete project motivation, model formulations, assumptions, results, comparative analysis, and ZIP-code case studies.

## Technologies and Methods

- Python
- Pandas
- NumPy
- Gurobi
- Geopy
- Google Colab
- Data Cleaning
- Missing-Value Imputation
- Geospatial Analysis
- Integer Programming
- Mixed-Integer Programming
- Piecewise-Linear Optimization
- Facility Location
- Budget Optimization

## Environment Requirements

The notebooks use the following packages:

```text
pandas
numpy
gurobipy
geopy
```

They also use standard-library utilities such as:

```text
pathlib
collections
os
```

The original notebooks contain Google Colab-specific imports:

```python
from google.colab import drive
```

A typical Colab setup is:

```python
!pip install gurobipy geopy
```

Pandas and NumPy are normally already installed in Colab.

Note that a valid Gurobi license is required. 

## Running the Project

Because the notebooks were created in Google Colab, file paths may reference mounted Google Drive folders.

To run the project outside the original environment:

1. Place all source files in a single project directory.
2. Update file paths in each notebook.
3. Run `Data Cleaning Part 1.ipynb`.
4. Confirm that `Childcare Deserts FINAL.csv` is generated.
5. Run `Optimization_Budgeting_Problem1.ipynb`.
6. Run `Optimization_Budgeting_Problem2.ipynb`.
7. Review the generated optimization result CSV files.

Exact reproduction may require adjusting filenames because some uploaded files contain spaces or parenthetical suffixes.

## Data Notes

The repository contains a combination of project-provided and public datasets. 

Public data sources described in the report include:
- U.S. Census population-by-age data
- New York State regulated child care program data
- employment and income data supplied for the course project
