Use <a href="https://pip.pypa.io/en/stable/">pip</a> to manage packages.

<hr>

To see the location of <a href="https://pip.pypa.io/en/stable/user_guide/#config-file">pip.conf</a> on Mac:

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

Show detail about a installed package.

```
pip show --files twine
```

<hr>

Difficulty in finding commandline tool?

Try the following location:
```
/Users/<username>/Python-library/bin
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

Key commands to execute under the project directory:

1. Build
```
python3 setup.py sdist bdist_wheel
```

2a. (optional) Check readme rendering as HTML
```
python3 -m readme_renderer README.rst
```

2b. (optional) Check whether the distribution’s long description will render correctly on PyPI.
```
python3 -m twine check dist/*
```

3a. (optional) test upload to testpypi, via one of the following:
```
python3 -m twine upload --repository <repo_name> dist/*
python3 -m twine upload --repository testpypi dist/*
```
or
```
python3 -m twine upload --repository-url <repo_url> dist/*
python3 -m twine upload --repository-url https://test.pypi.org/legacy/ dist/* 
```

3b. officially test upload to pypi, via one of the following:
```
python3 -m twine upload --repository pypi dist/* 
python3 -m twine upload --repository-url https://upload.pypi.org/legacy/ dist/* 
```

<hr>

### Version number

https://packaging.python.org/guides/single-sourcing-package-version/

