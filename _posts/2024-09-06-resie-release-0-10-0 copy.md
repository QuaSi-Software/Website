---
layout: entry
title: "Release of new ReSiE version 0.10.0"
date: 2024-09-06 12:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 0.10.0 of our energy system simulation engine ReSiE. This release reworks how time is handled in the input of the simulation and how time is formatted in the profiles used by the engine. These changes both increase usability by allowing users to specify time in a more human-readable way as well as helping to clarify what the output means. Other changes since the last release include an improved implementation of geothermal probes and improvements of the mechanism to handle different temperatures of components processing heat.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available on [the documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io).

<!--more-->

### Key Features

* Datetime Indexes for Profiles and Simulations: Introduced datetime handling for profiles and internal processes. Simulation start and end times are now datetime-based, and time steps can be provided in seconds, minutes, or hours. Profiles must cover the full simulation period and can be defined with various formats (start date & timestep, start date & timestamp or custom date format). Multi-year weather data is now supported. Added extensive/intensive data types in profiles, replacing "is_power." Improved segmentation and aggregation algorithms with support for linear or stepwise interpolation.

* Temperature Layer Integration: Temperature layers are now handled in input/output interfaces for correct calculation of COP. Enhanced the heat pump component to manage temperature layers, and implemented a method to handle unknown energies during the potential step to avoid balance errors.

### Additional Improvements

* Improved Time Definition: Data is now defined as the mean/sum of the following time step. Weather data is converted accordingly were required. Internally, local standard time is used. Profiles with daylight saving time (DST) are converted. Leap days are omitted in both input and output.
* Coordinate Support: Added input for coordinates and automatic conversion for coordinates provided in weather data files.
* New Parameters: Introduced "time_shift_seconds" to manually shift profile data and "use_linear_segmentation" for linear interpolation. Simulation parameters are defined completely new. Added long-wave irradiation from weather files to be used by components.

### Other Changes

* Removed deprecated internal parameters like "is_first_timestep."
* Improved geothermal probe interpolation and added custom g-function import, temperature limits, and bypass functionality in the heat pump for temperature management.
* Enhanced tests to cover profile conversions and added default simulation parameters for tests.
* Introduced support for timezones beyond 2038.

### Code and Documentation

* Applied autoformat to non-formatted files, added YAS code style configuration using JuliaFormatter, and introduced pre-commit hooks for automatic formatting. Extended README to cover code style guidelines.

### Scenarios

* Added new scenarios: "transformer_chain" and "hp_temperature_layer," along with new scenario references due to heat pump bypass, correct COP calculation for multiple heat layers and for line plots using dates as x-axis.
