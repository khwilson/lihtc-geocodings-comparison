## Data

The data originally came from [this link](https://lihtc.huduser.gov/) on the HUD website.
For some reason, they have storedt he data in dBase format, aka, Microsoft Access.
So I have gone ahead and exported these in Access to Excel files (data/LIHTC*.xlsx) and
then again into a duckdb format (data/lihtc.duckdb) so that it's a lot faster to open.

This occurs in the notebook `src/notebooks/100_convert_to_duckdb.ipynb`.

List of EPSGs corresponding to state planes is from https://gist.github.com/fitnr/10795511

## Geocoding

We geocode with the following services:
  * [Census Geocoder](https://geocoding.geo.census.gov/geocoder/): `201_geocode_census.ipynb`


## Comparisons




## License

MIT. See `LICENSE` file.
