# Excrecises and Practical Tips ( Python )

## Using `IPython`

- `%time` -- assess speed
- `%run`  -- debug
- `%autoreload 2`  -- keep autoreloading packages

        %load_ext autoreload            # load the package
        %autoreload 2

## Keeping the system clean and tidy: 

### `virtualenv`

Allows to have a separate Python installation with a separate set of packages. 

- Create a virtual environment

        $ virtualenv jobname
        (jobname)  $_             # within the virtual environment 'jobname' now
        (jobname)  $ ls
        Include  Lib  Scripts
    
- Exit

         (jobname)  $ virtualenv deactivate

- Re-enter

        $ source Scripts/activate 
        (jobname)  $_             # within the virtual environment 'jobname' now

- configure for scientific computing
 - on [Windows](http://texploring.com/installing-scikit-learn-in-python-virtualenv-to-do-general-purpose-machine-learning/)

### `docker`

A light-weight virtual machine. Often used on server machines for security reasons. Can be tuned to communicate to other virtual machines.

## Packaging

### `easy_install`

Advantages: good when the package has binary files

e.g. `$ easy_install-3.4.exe virtualenv`

### [`PyPi`](http://PyPi.python.org)

Advantages: manages well dependencies on other Python packages

## Unit testing

Install `pytest` unit testing framework

    pip install pytest

Make testing directory and files

    ~/src       $ mkdir test
    ~/src/test/ $ touch test_algorithm.py


    python setup.py develop
    py.test test/
    test/test_algorithm.py
    py.test test/
    vim test/test_algorithm.py 
    py.test --help
    py.test test/
    py.test --pdb test/ # run test with Python debugger
    py.test

## [Integration testing](http://en.wikipedia.org/wiki/Integration_testing)

Individual software modules are combined and tested as a group. 
It occurs after unit testing and before validation testing. 

## Compilation of Python packages and modules

- [`cx_Freeze` ](http://cx-freeze.readthedocs.org/en/latest/)
- [`PyInstaller`](http://www.pyinstaller.org/)

## Exception (error) handling

Do not mix up errors with output values (e.g. old style `-1` for invalid input)

    try:
		f = open(input_)
  		return 2/x
	except ValueError, e:
		print( e.message )
		raise ValueError
	finally:
		f.close()
 

