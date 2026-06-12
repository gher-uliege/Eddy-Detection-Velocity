# Eddy-Detection-Velocity

Try to detect eddies based on the velocity field created with `DIVAnd` using the `py-eddy-tracker`.

## Installation

That might be the trickiest part: installing the tool without conflict in the package versions.


### Install Python

We worked with python3.11.15, other versions may work, and other will fail.     

#### Download
The code is download from https://www.python.org/downloads/release/python-31115/ and extracted:
```bash
tar xvf Python-3.11.15.tar.xz
```

#### Compilation

```bash
cd Python-3.11.15
./configure
make
sudo make install
```

## Set virtual environment

It is often recommanded to create a virtual environment in Python to ensure compatilibity between the installed modules.      
We worked with the [https://virtualenvwrapper.readthedocs.io/en/latest/](virtualenvwrapper), which should be installed with:

```bash
pip install virtualenvwrapper
```
then we can create a new environment (here called `Eddy`) by specifying the Python version we just installed:
```bash
mkvirtualenv --python=/usr/local/bin/python3.11 Eddy
```

## Install module

We followed the official documentation: https://py-eddy-tracker.readthedocs.io/en/stable/installation.html.

First we install some requirements:

```bash
pip install "matplotlib<3.8" opencv-python pint polygon3 pyyaml requests scipy "zarr<3.0" netCDF4 numpy numba
```

then for the installation of `pyEddyTracker` there were some errors, so we ended up doing this:
```bash
pip install cython
pip install --no-build-isolation "netCDF4<1.6"  
pip install --no-build-isolation git+https://github.com/AntSimi/py-eddy-tracker.git
```
which solved the problem.

### Create a Jupyter kernel

If you want to use Jupyter notebooks with the same environment (`Eddy`):
```
pip install ipykernel
python -m ipykernel install --user --name Eddy --display-name "Eddy"
```
so when you open Jupyter, you can now select `Eddy` as the kernel.

## Running a detection

A full (and working) example is available in the notebook [detect_eddy_medsea](src/detect_eddy_medsea.ipynb).