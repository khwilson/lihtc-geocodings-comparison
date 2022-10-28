# Exploring divergence between LIHTC official lat/lons and those from geocoders

Step one in every spatial analysis is to transform abstract "locations" (housing units,
addresses, theme parks) into a mathematical representation of that location. The most
common of these is a lat/lon pair.

To save researchers time, the LIHTC program at HUD has provided these for all the
housing projects it has sponsored. But how _good_ are those geocodings. This was
explored recently in [N.E. Wilson et al.](https://www.mhankinson.com/documents/lihtc_geocodes.pdf).

The real meat of that paper is doing a detailed analysis on some subset of the data,
but they also straight up compare Google geocodes to the ones provided by LIHTC. I was
curious if similar observations were present when using other geocoders, notably the
(free) Census geocoder.

In this repository, we examine those outcomes. The money comparisons are in the
`src/notebooks/300_comparisons.ipynb` notebook.

## Data

The data originally came from [this link](https://lihtc.huduser.gov/) on the HUD website.
For some reason, they have storedt he data in dBase format, aka, Microsoft Access.
So I have gone ahead and exported these in Access to Excel files (data/LIHTC*.xlsx) and
then again into a duckdb format (data/lihtc.duckdb) so that it's a lot faster to open.

This occurs in the notebook `src/notebooks/100_convert_to_duckdb.ipynb`.


We also need the list of all state plane CRSs so that we can make good comparisons of
lat/lons. (Note: we went into this expecting most discrepancies to be <100m so Euclidean
distance in a state plane should be a very accurate approximation of the actual
distances involved.) For those, we grabbed them from the always wonderful
[Neil Freeman](https://gist.github.com/fitnr/10795511).

## Geocoding

We geocode with the following services:
  * [Census Geocoder](https://geocoding.geo.census.gov/geocoder/): `201_geocode_census.ipynb`

More may be added later

## Comparisons

Comparisons occur in `src/notebooks/300_comparisons.ipynb`. Some simple observations:
* Observed distances depend on CRS (no surprise)
* 10-100m is very common
* The Census geocoder misses a lot of addresses (also no surprise)

## License

MIT. See `LICENSE` file.
