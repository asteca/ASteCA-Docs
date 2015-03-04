
If the Best fit method function is set to run the theoretical
isochrones are read and the corresponding magnitudes and colors
created and stored, according to those defined in the input
photometric data file.

1- Use the first photometric system stored to obtain the 
metallicity and age values allowed according to those
present in the theoretical isochrones.
*WE ASUME ALL PHOTOMETRIC SYSTEMS CONTAIN THE SAME NUMBER OF
METALLICITY FILES*
Function: `get_met_age_values`.

2- For each photometric system used, we read all the magnitudes
defined by the input photometric data file. The initial and
present day masses are read only for the first photometric
system and assumed equal for the remaining (if any).
Function: `get_isochs`

3- All magnitudes (and masses) for each system are interpolated.
The resulting list `isoch_interp` contains one sublist per metallicity
value, each metallicity sub-list contains one sub-list per age value
and each age sub-list contains: initial masses, actual masses and
all magnitudes defined by the input photometric data file.
Function: `interp_isoch`

4- Magnitudes are ordered to match the input data file and colors
are created and equally ordered.
Function: `get_mc_order`