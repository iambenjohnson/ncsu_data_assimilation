Python
======

Anaconda
--------
Configure the Environment
^^^^^^^^^^^^^^^^^^^^^^^^^
We use a package manager known as Anaconda to install the necessary
python packages and configure them correctly (since the packages have
dependencies) .

.. parsed-literal::
    wget https://repo.anaconda.com/miniconda/Miniconda2-latest-Linux-x86_64.sh
    ./Miniconda2-latest-Linux-x86_64.sh

Once anaconda is installed we will use it to download the appropriate
python packages and configure an environment with them. The environment
is actually a directory with a particular configuration of packages.
Modifying one environment will not affect other environments.

.. parsed-literal::
    conda create -n renci_env -c conda-forge python numpy scipy matplotlib netcdf4 cartopy docutils sphinx sphinx-fortran h5py

The ``-n`` flag is used to indicate the name of the environment (in this
case ``renci_env``) and the ``-c`` flag is used to indicate which conda
channel the packages will be downloaded from (in this case
``conda-forge``).

Activate the Environment
^^^^^^^^^^^^^^^^^^^^^^^^
.. parsed-literal::
    source activate renci_env

Deactivate the Environment
^^^^^^^^^^^^^^^^^^^^^^^^^^
.. parsed-literal::
    source deactivate

Remove the Environment
^^^^^^^^^^^^^^^^^^^^^^
.. parsed-literal::
    conda env remove -n renci_env

Sphinx
------
We use a tool known as Sphinx to create this documentation. Sphinx
automates a lot of the documentation process by importing python modules
and converting their docstrings into output formats such as HTML or
LaTeX as long as the docstrings are in accordance with a markup syntax
known as reStructuredText.

Sphinx and its extensions also parse code snippets and automatically
employ syntax highlighting when outputting HTML documentation.

Once we have the environment created and activated we can use a utility,
``sphinx-quickstart``, to start the documentation.

.. parsed-literal::
     mkdir docs
     cd docs
     sphinx-quickstart

We use most of the ``sphinx-quickstart`` default settings for our 
documentation. However, two of the options that are not enabled by
default are useful for our case.

.. parsed-literal::
     autodoc: automatically insert docstrings from modules (y/n) [n]: y
     mathjax: include math, rendered in the browser by MathJax (y/n) [n]: y

Since our code is written in python and the docstrings from the modules
are written in reStructuredText, we want Sphinx to automatically insert
the docstrings into the documentation by enabling ``autodoc``.

Additionally, since there are various formulae that we describe from the
data assimilation literature and from the DART documentation, we want 
Sphinx to render them by enabling ``mathjax``.