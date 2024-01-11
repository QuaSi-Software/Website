---
layout: entry
title: "Release of new ReSiE version 0.7.0"
date: 2024-11-01 12:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 0.7.0 of our energy system simulation engine ReSiE. This release was developed over some time and contains many internal changes to better support various energy systems and use cases we envision for the future. However we are not done with refactoring and continue to improve our engine to cover a wider range of use cases. Please note that ReSiE in general is still in an early stage and might not be suited for use in projects without consultation on the current capabilities and limitations.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available on [the documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io).

<!--more-->

### Changes

#### Input and output
* Rename parameters and output variables across several components:
  * Load --> Demand                     in output channel of FixedSink
  * static_load --> constant_demand     for parameters of sinks
  * static_* --> constant_*             for parameters where * in (power, temperature, demand, supply)
  * fixed_cop --> constant_cop          for HeatPump
  * draw sum --> output_sum             in output channel of GridConnection
  * load sum --> input_sum              in output channel of GridConnection
  * power --> power_*                   for parameters of all transformers, where * in (el, th)
  * medium --> consider_medium          for control strategy parameters of all transformers
* Add output channel "Losses" to all components and to Sankey output. "Losses" are total losses, while "Losses_XX" are medium-wise break downs
* Constant values for fixed sources and sinks are now given as power instead of work/energy to be consistent with bounded sources and sinks
* Add global logging functionalities with the following categories: Debug, Info, BalanceWarn, Warn, Error and redirected all println() to logger (console and/or logging files, separately for general logs and Balancewarn)
* Update configuration options for busses:
  * Rename "connection_matrix" to "connections"
  * Rename "storage_loading" to "energy_flow"
  * Make "connections" a required part of the config for a bus, including items "input_order" and "output_order", however "energy_flow" remains optional
  * Remove "output_refs" item as "output_order" contains the same information and is now required

#### Functionality
* Sankey diagrams now display the difference of requested and delivered energy in fixed sinks and sources
* Remove condition "would overfill thermal buffer" in storage_driven strategy as this is now handled implicitly
* Add profile aggregation and segmentation with testcases
* Add import of weather files in EPW format and .dat format (DWD)
* Add functionality to map profiles from weather file to component profiles, like ambient temperature from the weather file to a geothermal collector

#### Fixes
* Fix generic storage implementation not being available due to the module not being included
* Fix the profile scaling factor of some components being required despite profiles being optional
* Add missing output channels to Electrolyser

#### Refactorings
* Change the input and output interfaces of busses such that the order matches the input and output priorities
* Rename helper function highest_temperature to highest and add types to inputs
* Provide docstrings for some structs and functions that were missing them
* Rename internal variables to match changes in the input and output variables mentioned above
* Remove last potential() step of transformer chains as this is not needed
* Add required Julia packages: Colors, Interpolations, Dates, Logging
* Rename argument "parameters" for simulation parameters to "sim_params" and add them to all components and profiles
* Rework communication of balances, energy/storage potentials and temperatures via busses. This is an extensive rework that touches almost all components and how the `process` and `potential` simulation steps work. Please note that the rework is not finished with v0.7.0 and will continue to support more energy systems and component configurations that might be of interest to users. However no compatability is knowingly broken with examples that worked in previous versions.

