Installation
============

The `DART Getting Started
<https://www.image.ucar.edu/DAReS/DART/DART2_Starting.html#installing>`_
guide uses the Lorenz (1963) [1]_ model as an example to demonstrate how
to build the source code. The Lorenz model is a simple example of an
unstable numerical system which is non-periodic in most cases.

The system of equations employed in the model are given by:

.. math::
    X'  = -\sigma X+\sigma Y \\
    Y' = -X Z+r X-Y \\
    Z' = X Y-b Z

where the coefficients are given default values in DART:

.. math::
    r = 28 \\
    \sigma = 10 \\
    b = 8/3

The Lorenz model is useful for developing an intuition of the behavior
of chaotic systems. DART also uses it as an example to demonstrate how
the namelists, makemakefile (mkmf) scripts and executables all work in
concert to make the testbed highly configurable.

In order to get DART working on Hatteras, load these modules in your
``.bashrc`` file.

.. code-block:: bash

    # /home/bkjohns2/.bashrc
    module load hdf5/1.10.1
    module load netcdf-C/4.5.0
    module load netcdf-Fortran/4.4.0

I was able to get the executables to compile using the default 
``mkmf.template`` file in ``/DART/build_templates``. There was no need
to change the NETCDF setting since:

.. parsed-literal::
    echo $NETCDF
    /usr/share/Modules/software/CentOS-7/netcdf-Fortran/4.4.0

As of March 2019 Jeff Willison found it necessary to use the intel set 
of modules to get DART running on Hatteras with larger models that use
MPI and by using ``mkmf.template.intel.linux``.

.. code-block:: bash

    # /home/rhe/loadall.csh
    module load hdf5/1.10.1_intel-18.0.0
    module load nco/4.7.3_intel-18.0.0
    module load intelc/18.0.0
    module load netcdf-C/4.5.0_intel-18.0.0
    module load intelfort/18.0.0
    module load netcdf-Fortran/4.4.0_intel-18.0.0

While running ``quickbuild.csh`` will delete the necessary files and
compile the necessary executables, it's important to know what each
executable actually does.

.. code-block:: fortran

    &hypothetical_nml
        obs_seq_in_file_name = "obs_seq.in"
    /

.. [1] Lorenz, Edward N. “Deterministic Nonperiodic Flow.” *Journal of the Atmospheric Sciences* 20, no. 2 (March 1, 1963): 130–41. https://doi.org/10.1175/1520-0469(1963)020<0130:DNF>2.0.CO;2.