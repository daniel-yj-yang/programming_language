Use <a href="https://pip.pypa.io/en/stable/">pip</a> to manage packages.

<hr>

To see the location of pip.conf on Mac:

```
pip config list -v
```

For example, to specify a userlib parh in **/Users/\<username\>/.pip/pip.conf**
  
```
[global]
target = /Users/<username>/Python-library
```

Notes:
- This userlib path needs to be added by $PYTHONPATH (e.g., ~/.zshrc) so python can load it by default
- This userlib path needs to be added by PYTHONPATH manager in Spyder

<hr>

Install a package, for example, <a href="https://pytorch.org/">PyTorch</a>.

```
pip install torch torchvision
```

<hr>

Check module version and module load path

Method#1: use Python

```
>>> import numpy

>>> numpy.__version__
'1.19.1'

>>> numpy.__file__
'/Users/daniel/Python-library/numpy/__init__.py'
```

Method#2: use pip

```
% pip freeze | grep numpy
numpy==1.19.1

% pip show numpy
Name: numpy
Version: 1.19.1
Summary: NumPy is the fundamental package for array computing with Python.
Home-page: https://www.numpy.org
Author: Travis E. Oliphant et al.
Author-email: None
License: BSD
Location: /Users/daniel/Python-library
Requires: 
Required-by: torchvision, torch, yellowbrick, umap-learn, tensorflow, tensorboard, tables, statsmodels, seaborn, scipy, scikit-learn, PyWavelets, patsy, pandas, opt-einsum, numexpr, numba, mkl-random, mkl-fft, matplotlib, Keras-Preprocessing, imageio, h5py, Bottleneck, bokeh, bkcharts, astropy, altair
```

<hr>

## <a href="https://packaging.python.org/tutorials/packaging-projects/">Create a Python package</a>

```
python3 setup.py sdist bdist_wheel
```

```
python3 -m twine upload dist/*
```
