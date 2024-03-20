---
layout: entry
title: "Release of new ReSiE version 0.8.0"
date: 2024-03-20 09:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 0.8.0 of our energy system simulation engine ReSiE. This release builds on the changes of the previous release v0.7.0, which introduced a lot of new things in regards to how the energy flow and distribution works on busses. With v0.8.0 we finalise these changes and brought the simulation model of ReSiE more closely to a finished state as we envision it. There will be further changes and additional features down the line to address the current modelling challenges when working with district networks.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available on [the documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io).

<!--more-->

### Changes

* Standardise storage un-/loading control parameters for all components and make them customisable to the input/output media
* Remove operational strategy "extended_storage_loading_control"
* Update line plot & sankey outputs to better show missing demands
* Rework internal energy distribution calculations on busses:
    * If two or more busses are connected in a chain (necessarily of the same medium), a so-called proxy bus is created, which handles the calculations for any energy transfer from components on any of the principal/original busses
    * Remove the distinction of maximum potential energy utilisation (max_energy) and storage un-/loading potential, as the calculation on a bus considers storages according to the energy flow matrix as well as storage loading flags and thus does not require a distinction anymore. Direct 1-to-1 connections do not require this either, hence the removal.
    * Add automatically generated output channels for busses in a chain, where each bus tracks how much energy is transfered to other busses in the input->output direction
    * Some slight changes the generated order of operations, as this now makes use of the input and output order on proxy busses. This should not have an impact on results, but might change the order of operations compared to versions before v0.8.0.
