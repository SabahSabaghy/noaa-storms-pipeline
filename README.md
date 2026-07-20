# noaa-storms-pipeline
A one-command pipeline that downloads a year of NOAA Storm Events data, converts it to GeoParquet, and lands it ready for analysis in DuckDB, GeoPandas, or QGIS.

## What it does

`pipeline.sh` takes a year (default: 2024), pulls the raw `details` file from NOAA's public archive, decompresses it, and converts it to a single GeoParquet file at `data/processed/storms_{YEAR}.parquet`.

Total runtime: about 90 seconds for a typical year on a home internet connection.

## The data

- **Source:** [NOAA Storm Events Database](https://www.ncei.noaa.gov/stormevents/)
- **License:** Public domain (US federal data)
- **What's in it:** every recorded storm event in the United States for the given year, including type, location, and damages

## How to run it

Requires GDAL (for `ogr2ogr`) and standard Unix utilities (`curl`, `gunzip`).

```bash
git clone https://github.com/SabahSabaghy/noaa-storms-pipeline.git
cd noaa-storms-pipeline
chmod +x pipeline.sh
./pipeline.sh
```

To run for a specific year:

```bash
./pipeline.sh 2023
```

## What I learned

This project strengthened my understanding of reproducible GIS/data engineering workflows using Git, Bash, and automated data pipelines. The most challenging aspect was debugging pipeline failures caused by unavailable data sources and learning how shell commands interact to download, process, and organise data. In future, I would implement more robust validation and error checking to identify issues earlier in the workflow and improve reliability.

## Stack

- bash
- curl
- GDAL / ogr2ogr
- GeoParquet
