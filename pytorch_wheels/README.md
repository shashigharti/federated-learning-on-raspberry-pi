# PyTorch V1.0.0 Wheel file for Python 3.7 on Raspberry Pi with armv7l architecture

## What is a Wheel File
A Python Wheel (WHL) file is the standard Python package format for distributing Python libraries.  According to the Python Packaging Index’s 
description, a wheel is *designed to contain all the files for a PEP 376 compatible install in a way that is very close to the on-disk format*.

## Prerequisites for installing the given wheel file:
* Python version should be 3.7.  Use `python3 --version` to check this.
* Raspberry Pi architecture should be armv71.  Use `uname -a` to check this.

## Installation of the Pytorch Wheel
To install a wheel file, open the terminal in Raspberry Pi and type the following:

`pip3 install name_of_the_package.whl`  (for Python3) - In this project, we use Python3

`pip install name_of_the_package.whl`   (for Python2)

To make sure that the package has been successfully installed, launch Python and try to import that package. In this project, type: `import torch`.

If import is successful, you are good to go!

