# Copernicus ETL Pipeline

This repository contains a script for extracting, transforming, and loading Sentinel-2 data from the Copernicus Data Space Ecosystem. The pipeline involves downloading Sentinel-2 raster data using Copernicus' API, processing them by applying filters on the downloaded products, calculating the NDVI using bands 04 and 08, and performing mosaicing and clipping of the images using the polygons from the `vertici_final.csv` file. The clipped raster is finally ingested.

The scope of this repository is to prepare Sentinel-2 data for a future project of downscaling Sentinel-3 data using an ATA CoKriging involving Sentinel-2 images in selected areas of Italy's Veneto region.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Functions](#functions)
- [Examples](#examples)
- [Contributing](#contributing)
- [Contact](#contact)

## Usage
The script can be run as a Databricks notebook or a standalone Python script. The main functionalities include obtaining an access token for API calls, downloading data, processing it, and performing various data transformations.

### Running the Script
Set up your environment: Ensure that you have all the required packages installed. Make sure to have a [Copernicus Browser]([url](https://browser.dataspace.copernicus.eu/)) account to complete the API call.

### Script Overview
The script performs the following main tasks:

**Obtain Access Token**: The get_keycloak function is used to obtain an access token for future API calls.

**Download Data**: The fetch_copernicus_data function fetches data from the Copernicus Data Space Ecosystem based on specified parameters.

**Process Data**: Several functions are used for data processing and transformation, including:
- Applying filters on the downloaded products
- Calculating the NDVI using bands 04 and 08
- Mosaicing and clipping the images using polygons from the vertici_final.csv file

## Functions
**get_keycloak(username: str, password: str) -> str**

This function obtains an access token for API calls.

**fetch_copernicus_data(data_collection, ft, date_start_string, date_end_string)**

This function fetches data from the Copernicus Data Space Ecosystem based on the specified parameters.

**diagnoseRequest(response)**

This function is used for debugging API requests by printing the status and details of downloaded items.

**process_copernicus_data(json_data, tiles, copernicus_user, copernicus_pwd, diagnostic=False)**

Processes the data from the Copernicus API response, filters the products by tile names, and downloads the relevant files.

**resize_image(image, shape)**

Resizes the given image to the specified shape using scikit-image.

**mask_raster_with_geometry(raster_path, geometry)**

Applies a mask to the raster image using the given geometry.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.

## Contact
For any questions or issues, please contact ealb94@gmail.com
