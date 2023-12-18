# CAM_SSTSIC_forcing
make SST &amp; SIC forcing file for CESM F1850 compset (i.e. CAM), with the amplitude of them perturbed.  
the need for this can be seen in Sheng & Zwiers (1998) paper. 

# Dependences
## command line tool
- CDO

## python packages
- numpy
- scipy
- xarray
- netcdf4
- cftime
- matplotlib

python packages can be installed by conda
```bash
conda install numpy scipy xarray netcdf4 cftime matplotlib
```

# How to make forcing file
1. remap the SST (unit: degC) and SIC (unitless, range 0-1) files to the official file map. `cdo remapbil,./ref_nc/CAM_sst_grid.nc infile.nc outfile.nc` the MAP file "./ref_nc/CAM_sst_grid.nc" is included.
2. run ./_Pre_SSTSIC.ipynb

Sample of remaped SST &amp; SIC files are also included

# Key algorithm
The processes of perturbing the amplitude of the monthly SST &amp; SIC are included in the ./_Pre_SSTSIC.ipynb

As the amplitude of the annual cycle will be weakened when the model interp the monthly mean to daily data (Sheng & Zwiers, 1998), the origional monthly data need to be preturbed. In ./_Pre_SSTSIC.ipynb it is done by numerical method, thanks to the boost of computing power. The analytical method was shown in Sheng & Zwiers (1998) paper, but I don't really understand the detail of that 😅. The performace are similar. 


# Reference
Sheng, J., & Zwiers, F. (1998). An improved scheme for time-dependent boundary conditions in atmospheric general circulation models. Climate Dynamics, 14(7), 609–613. https://doi.org/10.1007/s003820050244
