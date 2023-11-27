---
layout: entry
title: "Release of new GenSim version 2.15"
date: 2023-11-08 00:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 2.15 of our tool GenSim that is now fully open source, including a graphical user interface (GUI) based on Microsoft-Excel® (currently available in German only, however the English version will follow soon). GenSim calculates the energy demand for heating, cooling and electric loads of an individual building as yearly high-resolution profiles. The underlying generic building model makes it possible to model any building type. For all necessary parameters, standard data sets for common building types are available directly in the GUI (focus currently on german standards). The Geometry can be defined using a simple generic approach or by importing an own geometry model. An individual building can thus be modelled quickly, which is necessary when modelling entire districts. GenSim uses EnergyPlus® v9 as the simulation engine to perform physics-based thermal building simulation based on the framework that OpenStudio® provides.

The latest release can be found [here](https://github.com/QuaSi-Software/GenSim/releases) and a detailed user manual is available within the [documentation of the QuaSi-Projekt](https://quasi-software.readthedocs.io/en/latest/gensim_user_manual/).

<div class="row">
    <img class="col" src="{{'assets/gensim_logo.jpg' | absolute_url}}" style="max-width: 400px; padding: 0"/>
</div>

For citation of this release, use the following DOI: [https://doi.org/10.5281/zenodo.10200808](https://doi.org/10.5281/zenodo.10200808)

<!--more-->

What is GenSim? Find out more Datails in the [manual](https://quasi-software.readthedocs.io/en/latest/gensim_user_manual/#1-what-is-gensim).

A validation of the software is described in the recently published open-access [paper](https://doi.org/10.3390/en16176115).
