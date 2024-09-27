# Table of Contents
1. [Introduction](Introduction)
2. [How to use this tutorial](How-to-use-this-tutorial)
    1. [Tutorial workflow](Tutorial-workflow)
3. [Local instalation](#Local-instalation)
    1. [Using virtualenv](#Using-virtualenv)
    2. [Using conda](#Using-conda)
    3. [Adding the enviroment to your local notebook](#Adding-the-enviroment-to-your-local-notebook)
    4. [Clean-up](#Clean-up)

# Introduction
This tutorial will guide you throught the usage of the ATLAS open-data provided for machine learning in substructure provided at <https://opendata.cern.ch/record/80030>. This open data includes fully simulates ATLAS detector Monte Carlo samples with Run-2 conditions for the binary classification problem of seperating top from QCD jets (known as tagging). Further details are found in the open data link. A complementary set of instruction on how to utlize this data can be found at <https://gitlab.cern.ch/atlas/ATLAS-top-tagging-open-data>

This open-data is attached to the publication [JINST 19 (2024) P08018](https://iopscience.iop.org/article/10.1088/1748-0221/19/08/P08018) and should be cited in conjunction.

This tutorial would not be possible with the large effort from [Kevin Grief](https://gitlab.cern.ch/atlas/ATLAS-top-tagging-open-data), who really made these studies possible.

![Background uncert](https://atlas.web.cern.ch/Atlas/GROUPS/PHYSICS/PAPERS/JETM-2023-06/fig_09b.png)

# How to use this tutorial
This tutorial uses Jupyter for interactive notebooks.

If you do not wish to download any new packages/materials locally you can use Binder to build an enviroment from the GitHub page directly and host it on a webpage. Simply go to the Binder website:
[https://mybinder.org/](https://mybinder.org/), input the GitHub address <https://github.com/RobertLes/cometa-ML-tutorial> and hit launch! This may take several minutes to build, and will not be very fast for interactivity so we also provide instructions on how to run the notebooks on a local laptop.

## Tutorial workflow
There are 4 notebooks
1. [inspect_inputs.ipynb](https://github.com/RobertLes/cometa-ML-tutorial/blob/main/inspect_inputs.ipynb) - Will guide you on how to access the open data
2. [constituent_preprocessing.ipynb](https://github.com/RobertLes/cometa-ML-tutorial/blob/main/constituent_preprocessing.ipynb) - Will guide you on the recommended pre-processing of the open data file
3. [train.ipynb](https://github.com/RobertLes/cometa-ML-tutorial/blob/main/train.ipynb) - A very basic walkthrough on how to run some example neural network training on these inputs
4. [eval.ipynb](https://github.com/RobertLes/cometa-ML-tutorial/blob/main/eval.ipynb) - A basic walkthrough on usual and ATLAS metrics used to evaluete perfromance on this dataset

# Local instalation:
If you do not mind installing some new software temporarily we also provide instructions below for setuping the enviroment needed for this tutorial (mainly pytorch if you do not have it already). As to not interfere with your local installation we reccomend either using a virtualenv or conda to create isolated enviroments. We also provide instructions for removing these enviroments after the tutorial is finished.

If you do not have Jupyter installed already you can download it locally via `pip install jupyter`, or if you do not want to install it centrally on your laptop you can substitute `ipykernel` -> `jupyter` in the dependencies below

## Using virtualenv
Almost all python installtions have virtualenv and pip already installed. To setup the enviroment in the path `~/venv/CometaTutorial/`:
```
python -m venv ~/venv/CometaTutorial
source ~/venv/CometaTutorial/bin/activate
pip install torch==1.13.1 h5py torchinfo numpy matplotlib scikit-learn ipykernel
```

## Using conda
If you are more familiar with conda you can do the same with
```
conda create --name CometaTutorial python=3.9 pytorch=1.13.1 h5py conda-forge::torchinfo numpy matplotlib scikit-learn ipykernel
conda activate CometaTutorial
```

## Adding the enviroment to your local notebook

Now to have your central Jupyter runner see these enviroments, within the enviroment run:
```
python -m ipykernel install --user --name=CometaTutorial
```
After this when you deactivate the enviroment and open the notebook, you should see it in the drop-down menu for restarting the kernel.

If instead you downloaded `jupyter` directly in the enviroment you can skip this step.

## Clean-up
Once you are done with this tutorial you can deactivate the virtualenv/conda enviroment with the command `deactivate`. Then to remove the Jupyter kernel you can run
```
jupyter kernelspec list
jupyter kernelspec uninstall cometatutorial
```

For uninstalling the enviroment and cleaning your pip cache:
```
rm -r ~/venv/CometaTutorial
pip cache purge
```
Or similarly for conda:
```
conda env remove --name CometaTutorial
conda clean --all
```
