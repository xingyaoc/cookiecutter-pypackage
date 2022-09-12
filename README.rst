======================
cookiecutter-pypackage
======================

.. image:: https://api.travis-ci.org/ardydedase/cookiecutter-pypackage.svg?branch=master
   :target: https://travis-ci.org/ardydedase/cookiecutter-pypackage


This was forked from: https://github.com/ardydedase/cookiecutter-pypackage. Here are the differences of this forked version:

* includes a virtual environment where python packages get installed
* target for make requirements

Cookiecutter template for a Python package. See https://github.com/audreyr/cookiecutter.

* Free software: BSD license
* Vanilla testing setup with `unittest` and `python setup.py test`
* Travis-CI_: Ready for Travis Continuous Integration testing
* Tox_ testing: Setup to easily test for Python 2.6, 2.7, 3.3, 3.4
* Sphinx_ docs: Documentation ready for generation with, for example, ReadTheDocs_
* Bumpversion: Pre-configured version bumping with a single command


Usage
-----

Generate a Python package project::

    cookiecutter git@github.com:eitm-org/cookiecutter-pypackage.git

To activate your virtual environment automatically on ``cd``, put this into your ``.bashrc``::


	function cd() {
		builtin cd "$@"

		if [[ -z "$VIRTUAL_ENV" ]] ; then
		## If env folder is found then activate the vitualenv
		   if [[ -d ./venv ]] ; then
			  source ./venv/bin/activate
		   fi
		else
		## check the current folder belong to earlier VIRTUAL_ENV folder
		# if yes then do nothing
		# else deactivate
		parentdir="$(dirname "$VIRTUAL_ENV")"
		   if [[ "$PWD"/ != "$parentdir"/* ]] ; then
			  deactivate
		   fi
		fi
	}
	
	function activate() {
	  if [[ -z "$VIRTUAL_ENV" ]] ; then
	    ## If env folder is found then activate the vitualenv
	      if [[ -d ./venv ]] ; then
		source ./venv/bin/activate
	      fi
	  fi
	}

To build the package, first set up and activate your virtual environment by running::

	make venv && activate

or just run ``make venv`` and ``cd`` out and back into you repo.


About the package ``requirements``:

* Install the requirements in your local machine by running::
    
    make requirements

* Install the requirements for Dev in your local machine by running::
    
    make requirements-dev

* Requirements for Prod build can be found in ``requirements/prod.txt``

* Requirements for Dev build can be found in ``requirements/dev.txt``

* Prod requirements are reused in Dev requirements.

Then create a new repo and put it there.

Not Exactly What You Want?
--------------------------

Don't worry, you have options:

Similar Cookiecutter Templates
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

* `Nekroze/cookiecutter-pypackage`_: A fork of this with a PyTest test runner,
  strict flake8 checking with Travis/Tox, and some docs and `setup.py` differences.
  
* `tony/cookiecutter-pypackage-pythonic`_: Fork with py2.7+3.3 optimizations. 
  Flask/Werkzeug-style test runner, ``_compat`` module and module/doc conventions.
  See ``README.rst`` or the `github comparison view`_ for exhaustive list of 
  additions and modifications.

* Also see the `network`_ and `family tree`_ for this repo. (If you find
  anything that should be listed here, please add it and send a pull request!)

Fork This / Create Your Own
~~~~~~~~~~~~~~~~~~~~~~~~~~~

If you have differences in your preferred setup, I encourage you to fork this
to create your own version. Or create your own; it doesn't strictly have to
be a fork.

* Once you have your own version working, add it to the Similar Cookiecutter
  Templates list above with a brief description. 

* It's up to you whether or not to rename your fork/own version. Do whatever
  you think sounds good.

Or Submit a Pull Request
~~~~~~~~~~~~~~~~~~~~~~~~

.. _Travis-CI: http://travis-ci.org/
.. _Tox: http://testrun.org/tox/
.. _Sphinx: http://sphinx-doc.org/
.. _ReadTheDocs: https://readthedocs.org/
.. _`Nekroze/cookiecutter-pypackage`: https://github.com/Nekroze/cookiecutter-pypackage
.. _`tony/cookiecutter-pypackage-pythonic`: https://github.com/tony/cookiecutter-pypackage-pythonic
.. _github comparison view: https://github.com/tony/cookiecutter-pypackage-pythonic/compare/audreyr:master...master
.. _`network`: https://github.com/audreyr/cookiecutter-pypackage/network
.. _`family tree`: https://github.com/audreyr/cookiecutter-pypackage/network/members
