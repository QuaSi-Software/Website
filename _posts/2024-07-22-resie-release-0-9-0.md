---
layout: entry
title: "Release of new ReSiE version 0.9.0"
date: 2024-07-22 09:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 0.9.0 of our energy system simulation engine ReSiE. This release reworks how operational strategies, which are control mechanisms that extend beyond those covered by bus component, are implemented. In the new implementation components can be assigned control modules, that each control the operation of the component via defined callbacks. Multiple control modules can be combined in different ways to cover various use cases. Further improvements to this new implementation will likely follow in the future and will be based on the foundation laid with this update.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available on [the documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io).

<!--more-->

### Changes

* Implement functionality of control modules, that can be added to components and that control the operation of the components via defined callback functions. This replaces the previous implementation of "strategies", as this was too limiting. The currently implemented control module types are:
  * economical_discharge: Handles the discharging of a battery to only be allowed if sufficient charge is available and a linked PV plant has available power below a given threshold. Mostly used for examplatory purposes.
  * profile_limited: Sets the maximum PLR of a component to values from a profile. Used to set the operation of a component to a fixed schedule while allowing circumstances to override the schedule in favour of lower values (e.g. the produced energy could not be used up completely).
  * storage_driven: Controls a component to only operate when the charge of a linked storage component falls below a certain threshold and keep operation until a certain higher threshold is reached. This is often used to avoid components switching on and off rapdily to keep a storage topped up, as realised systems often operate with this kind of hysteresis behaviour.
* Restructure how the operational strategy is defined in the input file. In particular:
  * Remove entry "strategy"
  * Remove entry "control_refs"
  * Add entry "control_modules" that holds the definitions of control modules active for this component
  * Add entry "control_parameters" as container for miscellaneous parameters of the control behaviour as well as parameters to configure the storage un-/loading flags and special flags to modify the potential step of transformers to not consider given interfaces in during calculation.
* Add scenario "chpp_two_hyst" to highlight the operation of a transformer with two storage_driven control modules
