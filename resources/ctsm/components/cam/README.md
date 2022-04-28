# CAM: The Community Atmosphere Model

CAM code is stored in this repository on branches other than master.  The details are explained below.

Please see the [wiki](https://github.com/ESCOMP/CAM/wiki) for complete documentation on CAM, getting started with git and how to contribute to CAM's development.

This repository has three CAM branches:
* master - contains this readme and the Code of Conduct information
* cam_cesm2_1_release - contains the current CESM2.1 CAM code
* cam_development - contains the current CAM development code (see the important note below before using this branch)

# CAM-Nor: CAM version in the Norwegian Earth System Model

This repository has the following CAM-Nor branches:

* cam_cesm2_1_rel_05-Nor - contains the CAM6-Nor code, based on CESM2.1 CAM code. Contains aerotab and further changes as described by Seland et al. 2020, with tags

  - cam_cesm2_1_rel_05-Nor_v1.0.1 -- CAM6-Nor version, initial preliminary release of CMIP6 version, May 11 2020

  - cam_cesm2_1_rel_05-Nor_v1.0.2 -- CAM6-Nor version, CMIP6 bit-identical version (if used on fram, and as MM), June 2020

* cam_cesm2_1_rel_05-Nor-SpAer - based on cam_cesm2_1_rel_05-Nor, about to contain simple plume aerosol model code

### CAM-Nor and NorESM documentation https://noresm-docs.readthedocs.io/en/noresm2/

## How to checkout and use CAM:

The instructions below assume you have cloned this repository and are in the repository directory. For example:
```
git clone https://github.com/ESCOMP/CAM
cd CAM
```

### To run CAM compatible with the CESM2.1 release:
```
git checkout cam_cesm2_1_rel_33
./manage_externals/checkout_externals
```
### To view the release branch in github, go to the "Branch:master" pulldown menu and select cam_cesm2_1_rel

### To use unsupported CAM **development** code:

## NOTE: This is **unsupported** development code and is subject to the [CESM developer's agreement](http://www.cgd.ucar.edu/cseg/development-code.html).
```
git checkout cam6_2_000
./manage_externals/checkout_externals
```
### CAM Documentation - https://ncar.github.io/CAM/doc/build/html/index.html

### CAM6 namelist settings - http://www.cesm.ucar.edu/models/cesm2/settings/current/cam_nml.html
