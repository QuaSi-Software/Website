---
layout: entry
title: "Release of new ReSiE version 1.0.0"
date: 2026-08-07 11:00:00 +0200
categories: release
excerpt_separator: <!--more-->
---

We have released version 1.0.0 of our energy system simulation engine ReSiE.

Reaching version 1.0.0 marks an important milestone for the project. After the preceding beta releases, ReSiE now provides a stable basis for modelling and simulating energy systems, including component-based system modelling, control strategies, economic and emissions evaluation, parameter studies, optimisation and sensitivity analysis.

Version 1.0.0 also marks the transition towards a more stable public interface. While ReSiE will continue to be developed and extended, future changes will place greater emphasis on maintaining compatibility of established project-file structures, component interfaces and workflows.

With this release, ReSiE is also prepared for publication in the Julia General registry. As part of this process, the Julia package has been renamed and dependency compatibility has been specified more explicitly.

The latest release can be found [here](https://github.com/QuaSi-Software/resie/releases) and details are available in [the documentation of the QuaSi project](https://quasi-software.readthedocs.io).

<!--more-->

Listed below are the changes since the last beta release, v0.15.1. A full overview of the features available in ReSiE v1.0.0 can be found in the documentation.

#### Package renaming

* Rename the Julia package from `Resie` to `ResieQuasi`
  * This avoids naming conflicts with existing packages in the Julia General registry
  * The preferred name and spelling of the software remains **ReSiE**, as part of the QuaSi project
  * An explanation of the distinction between the software name ReSiE and the Julia package name `ResieQuasi` is available in the online documentation
  * If the package name is used extensively in code, it can conveniently be imported using `import ResieQuasi as Resie`

#### Grid connections

* Rename the component models `GridInput` and `GridOutput` to `GridSupply` and `GridSink`
  * The new names are consistent with other supply and sink components in ReSiE
  * They also avoid the ambiguity of "input" and "output", which referred to the complete energy system rather than the individual component
  * The component behaviour remains unchanged; only the names have been updated

#### Minor changes

* Update scenario reference files
* Add compatibility entries to `Project.toml`
  * This is required for registration in the Julia General registry
  * The compatibility entries define a known working set of dependency versions and reduce the risk of issues caused by incompatible future dependency updates

