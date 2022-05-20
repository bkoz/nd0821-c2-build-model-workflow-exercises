# Build a Reproducible Model Workflow - Exercises

This repo contains the code for demos, exercises, and exercise solutions.

This repository organizes the code by the lessons that they are used in. Each set of code is located in their respective lessons.

Please note that certain instructions for each exercise, as well as any relevant environment setup, are only provided within the Udacity classroom.

## Example:
All lesson 2 files are in `/lesson-2-data-exploration-and-preparation/`.

This directory contains: `demo`, `exercises`, with the `exercises` directory organized by the exercise number, and therein containing an exercise `README.md` file and `starter` and `solution` directories.

### Conda installation

[Download and install miniforge](https://github.com/conda-forge/miniforge)

Create a conda environment.
```
```bash
conda create --name=mlops
```
```bash
conda activate mlops
```
```bash
conda install mlflow=1.14.1 ipython=7.21.0 notebook=6.2.0 jupyterlab=3.0.10 cookiecutter=1.7.2 hydra-core=1.0.6 matplotlib=3.3.4 pandas=1.2.3 git=2.30.2 pip=20.3.3 wandb=0.10.31
```

### Get API key for Weights and Biases
Let's make sure we are logged in to Weights & Biases. Get your API key from W&B by going to 
[https://wandb.ai/authorize](https://wandb.ai/authorize) and click on the + icon (copy to clipboard), 
then paste your key into this command:

```bash
wandb login [your API key]
```

You should see a message similar to:
```
wandb: Appending key for api.wandb.ai to your netrc file: /home/[your username]/.netrc
