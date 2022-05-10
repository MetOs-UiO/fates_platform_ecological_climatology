# NorESM land sites platform - lab instructions

You will be divided into three groups. Each group will be responsible for running CLM5.0-FATES single-point simulations corresponding to one of the grassland ecosystems (ALP, SUB, BOR; see below) from the Vestland climate grid. More specifically, each person will be assigned one site in the temperature/precipitation gradient in their respective ecosystem group (numbers 1-4 following the naming convention; see below).

Your tasks then are as follows (another section below gives the detailed protocol):

1. Use the NorESM land sites platform GUI (type "localhost:8080" into your browser search bar) to run **2 simulations over a 10 year period**:
    1. Standard FATES parameters (all PFTs), with non-default variable "NPATCH_BY_AGE" added to output
    2. Excluding tree and C4 grass PFTs, with non-default variable "NPATCH_BY_AGE" added to output
2. Open the `input_visualization.ipynb` notebook in this folder, run the code for your model input and discuss the questions with your group
3. Open the `analyze_output.ipynb` notebook in this folder, run the code for your model output and discuss the questions with your group
4. As a group, present your most interesting results and discussions to the class. Create a collaborative presentation that should touch upon the following aspects:
    1. Environmental conditions at the four sites in the input data. Is it coherent with the given observations (values in Fig. 1)?
    2. All PFTs enabled vs. only grass/shrubs - does the output make sense to you? Use available resources (user guide, OSF data repository, data paper, satellite images, ...) to check your assumptions. Note that this is constrained by the short simulation period while starting the model from bare ground.
    3. Using "fine-scale" ecological field data for land surface model parametrization and validation, e.g., with the soil temperature example

## The sites


<p style="text-align: center;">

![image](https://betweenthefjords.w.uib.no/files/2020/08/grid.png)

</p>

<p style="text-align: center;">
Fig. 1: The Vestland Climate Grid sites have four levels of annual precipitation (700-2700 mm/yr) and three levels of mean summer temperature corresponding to alpine (upward-facing triangles, ALP 1-4, 6.5 degrees C, above treeline), sub-alpine (circles, SUB 1-4, 9.5 degrees C, just below forest-/treeline), and boreal (downwards-facing triangles, BOR 1-4, 11.5 degrees C, in boreal forest areas). The vegetation is semi-natural, grazed and open in all the sites, and have been selected to be as similar as possible apart from the levels of precipitation and temperature.
</p>


## Groups

**ALP** - (1) Felix Bal (master), (2) Stian Leer-Salvesen Dammann (master), (3) Morgane Demeaux (PhD), (4) TEACHER 1

**SUB** - (1) Homa Esfandiari (PhD), (2) Jisca Schoonhoven (master), (3) Bendik Sivertsen (master), (4) TEACHER 2

**BOR** - (1) Josse Maria van den Berg (master), (2) Femke Jolanda Vianen (master), (3) Adele Zaini (master), (4) Robin Benjamin Zweigel (PhD)

## Simulation protocol

**ATTENTION!** It is crucial that you enter all the values carefully - double check your input before you create a case!

*For both simulations*:

CTSM:

| Parameter      | Value |
| ----------- | ----------- |
| CALENDAR      | No Leap       |
| DATM_CLMNCEP_YR_START   | 2000        |
| DATM_CLMNCEP_YR_ALIGN   | 2000        |
| DATM_CLMNCEP_YR_END   | 2010        |
| RUN_STARTDATE   | 2000-01-01        |
| STOP_N   | 10        |
| STOP_OPTION   | nyears        |
| STOP_DATE   | -999        |
| RUN_TYPE   | startup        |
| LND_TUNING_MODE   | clm5_0_GSWP3v1        |


NAMELIST - CLM:

| Parameter      | Value |
| ----------- | ----------- |
| co2_ppmv      | 367.0       |
| fates_spitfire_mode   | off      |
| use_bedrock   | TRUE (tick box)        |

NAMELIST-CLM-HISTORY (**Leave fields not mentioned empty here!**):

| Parameter      | Value |
| ----------- | ----------- |
| hist_fincl1      | Add: NPATCH_BY_AGE       |
| hist_dov2xy      | TRUE (tick box)       |
| hist_avgflag_pertape | Average |
| hist_nhtfrq      | 0       |
| hist_mfilt      | 1       |


#### Simulation 1:

FATES

| Parameter      | Value |
| ----------- | ----------- |
| Indices      | All (1-12)       |

#### Simulation 2:

FATES

| Parameter      | Value |
| ----------- | ----------- |
| Indices      | No trees, no C4 grass (only tick 7-11)       |

---

FATES default PFT indices and corresponding long names:

| Index | Long name |
| ----------- | ----------- |
|  1 | Broadleaf evergreen tropical tree |
|  2 | Needleleaf evergreen extratropical tree |
|  3 | Needleleaf cold-deciduous extratropical tree |
|  4 | Broadleaf evergreen extratropical tree |
|  5 | Broadleaf hydro-deciduous tropical tree |
|  6 | Broadleaf cold-deciduous extratropical tree |
|  7 | Broadleaf evergreen extratropical shrub |
|  8 | Broadleaf hydro-deciduous extratropical shrub |
|  9 | Broadleaf cold-deciduous extratropical shrub |
| 10 | Arctic C3 grass |
| 11 | Cool C3 grass |
| 12 | C4 grass |

---

## Optional exercises

If you finish early with executing and analyzing your simulations, here are some additional optional tasks:

1. **Programming in Python**: we added some minor programming tasks to the "analyze_output.ipynb" notebook, marked with a snake emoji ("🐍"). If you haven't worked with Python before, try to use your favorite search engine to find the answer first to get closer to the "real-life" experience of learning a new programming language, but the teachers will also be happy to help :)
2. **Increased ambient CO_2 levels**: set-up a third simulation. Adapt the "NAMELIST - CLM" parameter for `co2_ppmv` to use `600` ppmv instead while using the same remaining settings as in simulation 1.2 (only shrub/grass PFTs). Note that this *will not affect* the other environmental forcing variables such as input air temperature. Compare the two simulations. Which effect does elevated ambient CO_2 alone have on the model output? You may find the [FACE experiments](https://doi.org/10.1111/j.1469-8137.2004.01224.x) interesting when thinking about this model experiment.

---
