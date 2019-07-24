Input data file
===============

The data file that contains the IDs  identifying each star, the star's
coordinates and their full photometric data must follow certain rules.

1. Data must be arranged into columns using points as decimal separators.
2. All lines which are not part of the data columns **must** be commented
   out using a `#` symbol at the beginning.
3. ID strings **must** be unique, ie: no two stars should have the same ID.
4. All photometric values (either magnitudes or colors) outside the range
   `[-50., 50.]` will be considered as *bad photometry* and any star showing
   such a value for *any* of its magnitudes/colors will be discarded.
5. All photometric columns **must** have an associated error column.
6. At least *one* magnitude column **must** be defined.
