# Conda Environment Starter

This repo is my current best practice for creating and managing `conda` development environments with a consistent and repeatable api controlled by `make`. The objective is to simply create a conda environment file to drive.

## Prerequisite

Before using this project you must have installed and configured `conda` on your local system.
It is a best practice to only install `miniconda` and use this pattern to manage a conda environment for each project.
You can find the latest installers [here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/) or use a package manager like Homebrew if you are using MacOS.

It is also recommended that you add the following to your `~/.condarc` to force conda-forge to be preferred over the default.

```yaml
channels:
  - conda-forge
  - defaults
```

## Usage

### Conda Environment

The ony requirement for usage is to update the 1.) `name` and 2.) the `python` version in `dev-env.yaml`. This starter pack also includes three basic stacks frequently used in a data driven project:

- numpy, pandas, pyspark, scikit-learn stack for analysis
- jupyter and streamlit for exploration
- the vega ecosystem for visualizations
- black, mypy, pylint, pytest for code quality

**The `blas=*=mkl` entry optimizes this envrinment for intel based chipsets. Change this to `blas=*=openblas` for non-chip specific numerical computing libraries**

Add or remove packages specific for your project as necessary.

### Makefile commands

The Makefile is used to (re)build the environment as well activate that environment before running specific tasks.

#### dev

Either creates or updates the development environment. This rebuild the entire environment when called so as to have the best possible dependency tree each time a package is installed

```bash
make dev
```

#### Jupyter

You can run `notebook` or `lab` with or without `pyspark`.

```bash
make pyspark    # jupyter lab with pyspark
make pyspark-nb # notebook with pyspark
make notebook
make lab
```

#### Streamlit

A streamlit app starter file is also included.

```bash
make streamlit
```
