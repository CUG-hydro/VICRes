 ![Build](https://img.shields.io/badge/VIC--Res-developing-orange) ![Version](https://img.shields.io/badge/version-1.0-blue)

# VIC-Res: Representation of water reservoir storage and operations in the Variable Infiltration Capacity (VIC) model

The Variable Infiltration Capacity (VIC) model is a popular large-scale hydrological model developed and maintained by the University of Washington, US. VIC has been used extensively to study and model river basins around the world. The model simulates key hydrological processes occurring in a river basin (e.g., water and energy balances, streamflow routing), but does not account for the operations of artificial water reservoirs. Since the environmental impact of reservoirs comes under ever-increasing scrutiny, we developed a variant of VIC that allows to account for the presence of these infrastructures. More details about the development of this variant are presented in [Dang et al. (2019)](https://www.hydrol-earth-syst-sci-discuss.net/hess-2019-334/).

### Prerequisites

VIC-Res is based on VIC 4.2—the last release of the VIC Version 4 development track, which has a large number of active users. The key difference between VIC 4.2 and VIC-Res stands in the routing module (written in FORTRAN), which has been modified to account for the presence and operations of water reservoirs. The two models share the same rainfall-runoff module (written in C). Both VIC and VIC-Res have been developed for Linux and Unix platforms, and they require the GNU and G77 compilers. VIC-Res has been tested on Linux Ubuntu 16.04 (Xenial Xerus) operating system.

### How to run

This task can be carried out through the following steps:
1. Download/compile the source code (by using GNU and G77)
2. Prepare the input files:
* Climate forcings (e.g. precipitation, maximum/minimum temperature, wind, etc.)
* Land use
* Soil parameters
* Flow direction
* Location of basin outlet
* Location of reservoirs (new)
* Reservoir parameters (new)
3. Configure the output files

More information on how to run the original version of VIC can be found here:
```
https://vic.readthedocs.io/en/master/
```
The sequence of syntax to run VIC-Res is similar to the one adopted by VIC.

### How to customize

Representation of water reservoirs:
The reservoir location is stored in the file *reservoirlocation.txt*, which has the same number of rows and columns of the flow direction matrix. This file contains integer numbers:
* '1' - '9998' represent the ID of reservoirs/dams
* '9999' represents open water surface (reservoir cells)
* '0' refers to other land use

Operation of water reservoirs:
For each reservoir (e.g., ID = 1), there is a reservoir configuration file (e.g., *res1.txt*), containing specifications on the maximum water level (*m*), minimum water level (*m*), storage capacity (*1000 m3*), hydraulic head (*m*; optional for the calculation of hydropower production), design discharge (*m3/s*), year of commission, initial water volume (*1,000 m3*), reservoir name, seepage rate (*m3/s*), infiltration rate (*m3/s*), and characteristics of the rule curves. 

### Example 

VIC-Res is demonstrated on a ‘toy’ case study, that is, a small catchment with dimension of 5 x 5 (cell) (see *Rainfall-runoffSetup* and *RoutingSetup* folders). 

The representation of water reservoirs is exemplified in the file *reservoirlocation.txt*, which contains two reservoirs (Reservoir 1 and Reservoir 2, IDs 1 and 2). The files containing all specifications of these reservoirs are named *res1.txt* and *res2.txt*.

### Citation

If you use VIC-Res, please cite the following paper:

*T.D. Dang, A.K. Chowdhury, and  S. Galelli. On  the  representation  of  water reservoir storage and operations in large-scale hydrological models:  implications on model parameterization and climate change impact assessments. Hydrology and Earth System Sciences, 2019:24, 397–416.* ![DOI](https://img.shields.io/badge/DOI-doi.org%2F10.5194%2Fhess--2019--334-lightgrey)

## Acknowledgments

VIC-Res development is supported by Singapore's Ministry of Education (MoE) via the Tier 2 project "Linking water availability to hydropower supply-an engineering system approach" (Award No. MOE2017-T2-1-143).

### Contact

For questions and feedback related to VIC-Res—and requests to fix possible bugs—please send an email to thanhiwer@gmail.com (Thanh Dang), Resilient Water Systems Group, Singapore University of Technology and Design, Singapore.
