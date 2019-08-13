# How to install a Python Wheel file
A Python Wheel (WHL) file is the standard Python package format for distributing Python libraries.  According to the Python Packaging Index’s 
description, a wheel is *designed to contain all the files for a PEP 376 compatible install in a way that is very close to the on-disk format*.

To install a wheel file, open the terminal in Raspberry Pi and type the following:

`pip3 install name_of_the_package.whl`  (for Python3)

`pip install name_of_the_package.whl`   (for Python2)

To make sure that the package has been successfully installed, launch Python and try to import that package.
If import is successful, you are good to go!
