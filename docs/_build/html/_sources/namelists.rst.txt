Namelists
=========
Properly configured namelists are essential for getting DART to work
suitably.

Tim Hoar mentioned that in order to get the nominal performance from
``obs_diag``, certain namelist options must be set properly. 

.. code-block:: fortran

    &filter_nml
        num_output_obs_members   = 31,
        num_output_state_members = 31,

        inf_flavor               = 5,
        inf_damping              = 0.9,
        inf_sd_lower_bound       = 0.6,
        inf_sd_max_change        = 1.05,
    /

``num_output_obs_members`` and ``num_output_state_members`` can be set
to zero and :code:`obs_diag` will still run but if we want the full
suite of diagnostic scripts to run these options should be set to the
correct number of ensemble members.

Since the Pressure Recording Inverted Echo Sounder (PIES) array is
moored at a fixed spot in our domain, ``inf_flavor`` should be set
to one of the adaptive inflation flavors. There are two such flavors:
option ``2`` is "Spatially-varying state space inflation" and option
``5`` is "Enhanced Spatially-varying state space inflation." Option
``5`` is the setting that Moha El Gharamti recommended. It employs a
different parametric distribution -- an Inverse Gamma rather than a
Gaussian. But the DAReS group suggested  that we might need to try both
``2`` and ``5``.

When using adaptive inflation ``inf_damping`` should be set to 0.9
initially (slow damping) and then possibly modified after examining the
priors. **Note well:** If inf_damping is set to 0, inflation will be
disabled.

Additionally, when using adaptive inflation, the ``inf_sd\*``
options are configurable and should be tuned. ``inf_sd_lower_bound``
should be set to 0.6 initially -- this option is only read when
``inf_flavor`` is set to 5. ``inf_sd_max_change`` should be set
to 1.05 initially.

.. code-block:: fortran

    &obs_diag_nml
        time_to_skip             = 0, 0, 7, 0, 0, 0
    /

``time_to_skip`` can be set to exclude spin up time from the diagnostic
period using ``YYYY, MM, DY, HR, MIN, SEC`` format.