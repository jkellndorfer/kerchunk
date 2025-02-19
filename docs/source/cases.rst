Case studies
============

Here we list completed datasets, with the reproducible code that made them, link to the
created references and possibly notebook/benchmark examples. This page is a work in progress.
All datasets available here will also be listed in the repo Intake catalogue.

.. note::

   This page needs to be cleaned up and the cases standardized.

Sentinel Global coherence
-------------------------

Native data format: GeoTIFF.

Effective in-memory size: 400TB.

Documentation: http://sentinel-1-global-coherence-earthbigdata.s3-website-us-west-2.amazonaws.com

Discussion: https://github.com/fsspec/kerchunk/issues/78

Generator script: https://github.com/cgohlke/tifffile/blob/v2021.10.10/examples/earthbigdata.py

Notebook: https://github.com/fsspec/kerchunk/raw/main/examples/earthbigdata.ipynb

Solar Dynamics Observatory
--------------------------

Native data format: FITS. 

Effective in-memory data size: 400GB

Notes: each wavelength filter is presented as a separate variable. The DATE-OBS of the nearest preceding 94A image
is used for other filters to maintain a single time axis for all variables.

Notebook: https://github.com/fsspec/kerchunk/raw/main/examples/SDO.ipynb

National Water Model
--------------------

Native data format: NetCDF4/HDF5. 

Effective in-memory size: 80TB

Notes: there are so many files, that dask and a tee reduction were required to aggregate the
metadata.

Notebook: https://nbviewer.org/gist/rsignell-usgs/02da7d9257b4b26d84d053be1af2ceeb

Generator notebook: https://gist.github.com/rsignell-usgs/ef435a53ac530a2843ce7e1d59f96e22

MUR SST
-------

Native data format: NetCDF4/HDF5. Effective in-memory size: 66TB. On disk size: 16TB

Documentation: https://podaac.jpl.nasa.gov/dataset/MUR-JPL-L4-GLOB-v4.1

Notebook: https://nbviewer.org/github/cgentemann/cloud_science/blob/master/zarr_meta/cloud_mur_v41_benchmark.ipynb

Notes: Global sea surface temperature data.  The notebook includes benchmarks.
See the notebook for how to establish NASA Earthdata credentials necessary for data access.

HRRR
----

Native format: GRIB2. 

Effective in-memory size: 7.5GB (200-file subset)

Documentation: https://rapidrefresh.noaa.gov/hrrr/

Notebook (generation and use): https://nbviewer.org/gist/rsignell-usgs/ae7bfb16e8a4049bb1ca0379805c4dc2

Notes: High-Resolution Rapid Refresh, real-time 3-km resolution, hourly updated, cloud-resolving,
convection-allowing atmospheric model from NOAA.  Notebook extracts only sections matching the filter "heightAboveGround=2". Requires importing ``kerchunk.grib2``
to register the codec.
