MATLAB
======

When running diagnostics on DART output we should use the
MATLAB scripts that come with the source code as much as possible. When
I met with the `Data Assimilation Research Section (DAReS) 
<http://www.image.ucar.edu/DAReS/DAReS>`_, Jeff Anderson pointed out
that my ensemble rank histograms were produced incorrectly and would
never flatten out because I did not add random samples from the
observation error distribution [1]_. These types of subtle problems are
already accounted for in the MATLAB scripts.

.. [1] Anderson, Jeffrey L. “A Method for Producing and Evaluating Probabilistic Forecasts from Ensemble Model Integrations.” *Journal of Climate* 9, no. 7 (July 1, 1996): 1518–30. https://doi.org/10.1175/1520-0442(1996)009<1518:AMFPAE>2.0.CO;2.
