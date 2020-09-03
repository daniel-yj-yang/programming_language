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
- This userlib path needs to be added by $PYTHONPATH so python can load it by default
- This userlib path needs to be added by PYTHONPATH manager in Spyder

<hr>

Install a package, for example, <a href="https://pytorch.org/">PyTorch</a>.

```
pip install torch torchvision
```

<hr>

Check package version.

Method#1: use Python

```
>>> import numpy
>>> numpy.__version__
'1.19.1'
```

Method#2: use pip

```
% pip freeze | grep numpy
numpy==1.19.1
```

