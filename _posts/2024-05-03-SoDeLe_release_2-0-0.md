---
layout: entry
title: "Initial release of SoDeLe in version 2.0.0"
date: 2024-05-03 00:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

Open source launch of SoDeLe for simple photovoltaics simulation

SoDeLe (loosely translated as "Solar simulation as easy as can be") is an easy-to-use tool for calculating energy profiles of photovoltaic systems. It is based on the well-validated python-pvlib, but offers a user-friendly GUI based on Microsoft-Excel® (and a CLI with JSON input). SoDeLe can simulate PV systems with parameters from real PV modules and inverters with different orientations. Alternatively, preset standard modules and a constant DC-AC efficiency can be selected. The database of parameters contains more than 35,000 PV modules from various manufacturers.
The simulation is based on a weather file, which can be either an EWP file (EnergyPlus® Weather File) or a .dat file from the German Weather Service (DWD).

The latest release can be found [here](https://github.com/QuaSi-Software/SoDeLe/releases) and a short user manual is available within the [README of the repository](https://github.com/QuaSi-Software/SoDeLe).

<div class="row">
    <img class="col" src="{{'assets/sodele_logo.jpg' | absolute_url}}" style="max-width: 400px; padding: 0"/>
</div>

<!--more-->

With SoDeLe, the energy yield of planned or existing photovoltaic systems can be determined quickly and easily in high temporal resolution without much expert knowledge. The results can be used for dynamic energy system simulations, storage sizing or dynamic cost and greenhouse gas calculations. In addition, different orientations and different PV modules and inverters can be analyzed or the energy yield of existing systems can be checked if real historical weather data is used as input.

The results of SoDeLe were verified for different module-inverter configurations, orientations and locations using comparative simulations with the commercial software PV*SOL and with the annual totals calculated by [PVGIS](https://re.jrc.ec.europa.eu/pvg_tools/en/).
