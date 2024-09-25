# How to use this tutorial
This tutorial uses Jupyter for interactive notebooks.

If you do not wish to download any new packages/materials locally you can use Binder to build an enviroment from the GitHub page directly and host it on a webpage. Simply go to the Binder website:
[https://mybinder.org/](https://mybinder.org/), input the GitHub address and hit launch! This may take several minutes to build, and will not be very fast for interactivity so we also provide instructions on how to run the notebooks on a local laptop.

# Local instalation:
If you do not mind installing some new software temporarily we also provide instructions below for setuping the enviroment needed for this tutorial (mainly pytorch if you do not have it already). As to not interfere with your local installation we reccomend either using a virtualenv or conda to create isolated enviroments. We also provide instructions for removing these enviroments after the tutorial is finished.

If you do not have Jupyter installed already you can download it locally via `pip install jupyter`, or if you do not want to install it centrally on your laptop you can substitute `ipykernel` -> `jupyter` in the dependencies below

## Using virtualenv
Almost all python installtions have virtualenv and pip already installed. To setup the enviroment in the path `~/venv/CometaTutorial/`:
```
python -m venv ~/venv/CometaTutorial
source ~/venv/CometaTutorial/bin/activate
pip install torch==1.13.1 h5py torchinfo numpy matplotlib ipykernel
```

## Using conda
If you are more familiar with conda you can do the same with
```
conda create --name CometaTutorial python=3.9 pytorch=1.13.1 h5py conda-forge::torchinfo numpy matplotlib ipykernel
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
jupyter kernelspec uninstall CometaTutorial
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
