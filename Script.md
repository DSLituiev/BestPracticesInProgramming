# Best practices in Programming

## Motivation:
- Efficient programming
- Efficient debugging
- Maintainability and extendability

## Values:
- Simplicity
- Readability
	- Better to have a readable code than heavily commented code, as comments can get outdated.
- Consistency
- etc

# Excrecises and Practical Tips ( Python )

## Using `IPython`

- `%time` -- assess speed
- `%run`  -- debug

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
  	
## GUI design

Think of a GUI as a [state machine](http://en.wikipedia.org/wiki/Finite-state_machine). 
See also [Model-view-controller model](http://en.wikipedia.org/wiki/Model-view-controller)

- internal states 
	- **model**: does computations that change the internal state
	- **view** : GUI state
- external inputs (user input, via 'view')
- **controller**: a transition function (aka synchronisation):

The *model* should be implemented separately from other parts. This ensures testability.

The *controller* is usually integrated with the *view*. If very complex, can be represented by a hash table (dictionary). 

# Workflow

Start a new `virtualenv` session

    $ virtualenv jobname
    (jobname)  $_             # within the virtual environment 'jobname' now

Make a project directory and initialize `git` there 

    (jobname)  $ mkdir src
    (jobname)  $ git init

Create a package directory and create infastructure files (`__init__.py` and `setup.py`) 

    (jobname)  $ mkdir newpackage        # create a new package dir
    (jobname)  $ touch __init__.py       # signalize it is a package dir
    (jobname)  $ touch setup.py          # create a setup file
    (jobname)  $ vim setup.py            # see further

Make a local installation of the package with developer mode 

    (jobname)  $ python setup.py --help
    (jobname)  $ python setup.py sdist
    (jobname)  $ python setup.py develop 

within the `setup.py`:

	from setuptools import setup, find_packages
	
	version = "0.0.1"
	
	setup(name="name_to_call",
	    version=version,
	    maintainer="My Name",
	    maintainer_email="my@email.com",
	    license="http://opensource.org/licenses/BSD-3-Clause",
	    platforms=["any"],
	    long_description="""  """,
	
	    packages=find_packages(exclude=['examples', 'tests']),
	
	    include_package_data=True, # see MANIFEST.in
	    zip_safe=False,
	    entry_points={
		    'console_scripts':
		    [
		    'fm = name_to_call.module_name:function_name',
		    ]
	    },
	)

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

Exit the virtual environment

    (jobname)  $ virtualenv deactivate

Enter the desired virtual environment
 
    $ virtualenv activate jobname



