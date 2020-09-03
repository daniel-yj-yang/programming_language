Use <a href="https://pip.pypa.io/en/stable/">pip</a> 

<hr>

To see the location of pip.conf on Mac:

```
pip config list -v
```

For example, a user lib parh in **/Users/\<username\>/.pip/pip.conf**
  
```
[global]
target = /Users/<username>/Python-library
```

<hr>

Install a package, for example, <a href="https://pytorch.org/">PyTorch</a>.

```
pip install torch torchvision
```

<hr>

Check package version.

Method#1: use Python IDE

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

