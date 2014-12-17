# Workflow

Start a new `virtualenv` session

    $ virtualenv jobname
    (jobname)  $_             # within the virtual environment 'jobname' now

Make a project directory and initialize `git` there 

    (jobname)  $ mkdir src
    (jobname)  $ git init

Create a package directory and create infastructure files (`__init__.py` and `setup.py`) 

    (jobname)  $ mkdir newpackage        # create a new package dir
    (jobname)  $ cd newpackage
    (jobname)  $ touch __init__.py       # signalize it is a package dir
    (jobname)  $ touch setup.py          # create a setup file
    (jobname)  $ vim setup.py            # see further

Make a local installation of the package with developer mode 

    (jobname)  $ python setup.py --help
    (jobname)  $ python setup.py sdist
    (jobname)  $ python setup.py develop 

within the `setup.py`:

	from setuptools import setup, find_packages

	VERSION = (0, 0, 1)
	# VERSION = "0.0.1"
	
	setup(name="name_to_call",
	    version=VERSION,
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



