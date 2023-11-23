---
layout: entry
title: "Release of new GenSim version 2.15"
date: 2023-11-08 00:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released the new version 2.15 of our tool GenSim that is now fully open source, including a graphical user interface based on Microsoft-Excel (currently German only, but English will follow...). GenSim can be used to easily calculate the energy demand as yearly high-resolution profiles of a building. Although GenSim uses the rather compilicated simuation core "EnergyPlus" and a detailed, physics-based thermal building simulation, it's presets, the included database for typical parameters and the generic creation of buildings simplifies the usage significantly. 

The latest release can be found [here](https://github.com/QuaSi-Software/GenSim/releases) and a detailed manual is available within the [documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io/en/latest/gensim_user_manual/).

<div class="row">
    <img class="col" src="{{'assets/gensim_logo.jpg' | absolute_url}}" style="max-width: 400px; padding: 0"/>
</div>

For citation of this release, use the following DOI: [https://doi.org/10.5281/zenodo.10200808](https://doi.org/10.5281/zenodo.10200808)

<!--more-->

What is GenSim?

GenSim - for "generic building simulation" - is a building simulation software using the EnergyPlus® simulation engine to generate high-resolution heating and cooling demand profiles as well as electricity demand profiles for buildings with various types of use. "Generic" in this context refers to a "generally valid" building model. This means that the software is versatile enough to simulate any type of building in a very flexible and simplified way, enabling users to efficiently adapt the software for any building design.

GenSim was specifically devloped for the use during project pre-planning where detailed simulations of buildings are challenging due to typically constrained time budgets and limited availability of information. Traditional simulation tools like DesignBuilder®, IDA ICE® or TRNSYS® require extensive input data, making the process time-consuming. GenSim addresses this by providing a streamlined approach for quick, simple, yet accurate building simulations. This is particularly valuable in early planning stages when only rough data about the planned buildings is available. GenSim strikes an optimal balance between the model's detail level and the precision of input parameters, ensuring efficiency without compromising on accuracy. If more detailed information (wall structure, geometry, specific use, ...) is available about the building to be examined, this can be used for more precise results.

A validation is described in the recently published open-access [paper](https://doi.org/10.3390/en16176115).