NCSU Data Assimilation
======================
These pages document our use of the `Data Assimilation Research
Testbed (DART) <https://www.image.ucar.edu/DAReS/DART/>`_ with the
`Regional Ocean Modeling System (ROMS) <https://www.myroms.org/>`_.
While DART is designed to work on various flavors of UNIX/Linux, much of
this documentation will focus specifically on our configuration of it on
the `Hatteras Cluster <https://renci.org/resources/>`_ at the
`Renaissance Computing Institute <https://renci.org/>`_.

Our suite of python scripts prepare super-observations (superobs) for
assimilation and compare the ensemble assimilation algorithm with the
`4-Dimensional Variational (4D-Var)
<https://www.myroms.org/wiki/4DVar_Tutorial_Introduction>`_ assimilation
algorithm included with ROMS. 

**Note well:** When running diagnostics on DART output we should use the
MATLAB scripts that come with the source code as much as possible. When
I met with the `Data Assimilation Research Section (DAReS) 
<http://www.image.ucar.edu/DAReS/DAReS>`_, Jeff Anderson pointed out
that my ensemble rank histograms were produced incorrectly and would
never flatten out because I did not add random samples from the
observation error distribution [1]_. These types of subtle problems are
already accounted for in the MATLAB scripts.

.. toctree::
   :maxdepth: 2

   installation
   namelists
   python
   localization
   matlab
   license

   



Index Capabilities
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

.. [1] Anderson, Jeffrey L. “An Ensemble Adjustment Kalman Filter for Data Assimilation.” *Monthly Weather Review* 129, no. 12 (December 1, 2001): 2884–2903. https://doi.org/10.1175/1520-0493(2001)129<2884:AEAKFF>2.0.CO;2.
