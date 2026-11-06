---
layout: entry
title: "Release of new ReSiE version 1.1.0"
date: 2026-11-06 11:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 1.1.0 of our energy system simulation engine ReSiE.

This release introduces several new features and improvements. A new user-facing simulate() function simplifies the use of ReSiE as a Julia package by handling logging and simulation run management. Integer parameters are now supported in optimisation, parameter variation and sensitivity analysis.

Further improvements include Claesson–Javed load aggregation for geothermal probes, significantly improving computational efficiency, and automatic plot downsampling to reduce output file sizes. In addition, GLMakie has been replaced with PlotlyJS to reduce dependencies and compilation times and enable interactive HTML plots. Additionally, multiple bugs have been fixed.

Version 1.1.0 also introduces full compatibility with Julia 1.13, including tests and example scenarios.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available in [the documentation of the QuaSi project](https://quasi-software.readthedocs.io).

<!--more-->

Listed below are the changes since the last release v1.0.0:

## Major features
* New user-facing `simulate()` function to handle logging and run management if used as a package. More details in the documentiation.
* Add support for integer parameters in optimisation, parameter variation and sensitivity analysis
  * Apply integer rounding and discrete sampling, reuse identical simulation results and adapt global and local sensitivity calculations
* Add Claesson–Javed load aggregation to `GeothermalProbes` for improved computational efficiency
  * Enabled by default and configurable through `use_load_aggregation` and `load_aggregation_cells_per_level` (default: 200)
* Add plot downsampling to reduce file sizes to a workable level. Add new IO settings `enable_plot_downsampling` and `plot_downsampling_max_number_values` to enable downsampling and configure the amount of data above which downsampling is applied
* Replaced GLMakie with PlotlyJS to reduce dependencies, compile time and ability to save certain plots as html.
* Make ReSiE fully compatible with Julia 1.13 including tests and scenarios

## Breaking changes
* Replace the following string-valued weather-file parameters with Boolean flags:
  * `temperature_from_global_file` → `use_ambient_temperature_from_weather_file`
  * `ambient_temperature_from_global_file` → `use_ambient_temperature_from_weather_file`
  * `global_solar_radiation_from_global_file` → `use_global_solar_radiation_from_weather_file`
  * `beam_solar_radiation_from_global_file` → `use_beam_solar_radiation_from_weather_file`
  * `diffuse_solar_radiation_from_global_file` → `use_diffuse_solar_radiation_from_weather_file`
  * `infrared_sky_radiation_from_global_file` → `use_infrared_sky_radiation_from_weather_file`
  * `wind_speed_from_global_file` → `use_wind_speed_from_weather_file`
* Rename IO settings:
  * `auxiliary_info_file` → `auxiliary_info_file_path`
  * `auxiliary_plots_path` → `auxiliary_plots_directory`
  * `parameter_study_csv_path` → `parameter_study_csv_path_prefix`
  * `parameter_study_plots_path` → `parameter_study_plots_path_prefix`
* Rename geothermal-probe output `new_fluid_temperature` → `mean_fluid_temperature`
* Rename simulation parameter `start_end_unit` → `start_date_format`

## Minor changes & fixes
* Make component ordering and the order of operations deterministic by using `OrderedDict` instead of `Dict`. This affects the OOO and output ordering.
* Add parameter `auto_log_level` to `load_and_run` to be able to either set a specific log level independent of the single or multi run simulation or let resie handle the log level setting
* Generate line plots using `x0` and `dx` instead of an explicit x-axis array to reduce plot file sizes. This makes lines non-continuous around leap days.
* Fix wrong geothermal-probe temperature communication during loading and unloading; fix probe ignoring `min_probe_temperature_unloading` in some cases; add the output `current_mean_output_temperature` for better debugging
* Add objective aggregation functions `last`, `min` and `max` for parameter studies to use the last, minimum or maximum value of an output parameter in the objective function
* Add IO setting parameters `general_logfile_file_path` and `balance_warn_logfile_file_path` so that users can configure them; log files are now temporarily stored in the `./output` directory and moved after the simulation
* Improve SSOT parameter validation for strings; add error messages and SSOT validations for simulation dates
* Improve error messages in parsing of functions
* Improve output file handling: automatically create missing directories; enable thread-safe plot generation to allow plots to be generated during multi-threaded parameter variations
* Fix aggregated CSV path; add parameter-specific prefixes to auxiliary plots; correct `FixedSink` parameter metadata
* Add Python-based helper function to calculate a g-function of a geothermal probe field from a shape file using pygfunction
* Add subtitle to Sankey plots showing the simulation duration
* Place storages consistently on the right side of the bus in Sankey plots to improve readability of complex systems
* Adapt example input files so they can be imported by SUSI without errors
* Update tests, examples and scenario reference results where needed
* Fix bug of parameter `output_parameter_study_csv` beeing ignored in some cases
* Improve error handling in `run_simulation_sample` that depended on the existence of the CSV results file
* Add a lock for `current_runs` to avoid rare freezings during multi-thread simulations
* Add support for a `maxlog` parameter in the CustomLogger used in ReSiE to allow warnings to be shown only once
* Replaced GLMakie with PlotlyJS to reduce dependencies, compile time and ability to save certain plots as html.
* Fix a bug in the battery that caused it to charge more than the set SOC_max at higher time steps
* Added `JuliaFormat.toml` file to enable formatting in VSCode with newest version of the julia extension
* Fix a bug where the energy and temperature flow dynamic output channels of Bus would not show up in certain cases


