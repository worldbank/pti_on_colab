# PTI_on_Colab (PTI raw data prep on Google Colab)
Prepare the PTI raw data of the country of interest solely on the Google Colab environment with a complete Pythonic approach.


## Structure of the pipeline:


- `data` All raw data and products will be stored here.
- `data/common` You should store ACLED data and MapSPAM data here (not included in this package)
- `tools.py` Common Python tool. No need to open it.


## Quick start:
Put the PTI folder with all codes in your own Google Drive:
`/content/drive/MyDrive/Colab Notebooks/PTI/`

## Required raw data:
PUT all raw data in the generated directories( `**/Source` ). For example, a WorldPop raster of Senegal should be stored in
`/content/drive/MyDrive/Colab Notebooks/PTI/data/SEN/WorldPop/Source`

It would be nice to have a data check sheet like below to organize the process. The CSV file of this table is in `materials`.

![image](/materials/rawdata_summary_table.PNG)



<br>
What you need to download beforehand are:

For each country `**/Source`
- ADM-3 shapefile (or ADM-1 – ADM3 Shapefiles)
- [GRID3 Settlement layer Version 1](https://data.grid3.org/)
>[!WARNING]
>V2 Settlement layer does not work for this pipeline.
- [WorldPop raster](https://www.worldpop.org/)
- [FEWS Livelihood](https://fews.net/data/livelihood-zones) or any Climate Zone layers (as an alternative)

Common
- [ACLED](https://acleddata.com/) as an ESRI Shapefile format (this should be stored in `data/common`. In the code, default name is `ACLED_1997_202304_AFR.shp`)
- [MapSPAM](https://mapspam.info/) data as geotiff format (this should be stored in `data/common/MapSPAM_global_sum`)
The MapSPAM raster images should be a set of:
  - `HarvArea_2000_Irrigated.tif`
  - `HarvArea_2010_allTech.tif`
  - `HarvArea_2017_Irrigated.tif`
  - `PhysArea_2000_allTech.tif`
  - `PhysArea_2000_Irrigated.tif`
  - `PhysArea_2005_allTech.tif`
  - `PhysArea_2005_Irrigated.tif`
  - `PhysArea_2010_Irrigated.tif`
  - `PhysArea_2017_allTech.tif`
  - `PhysArea_2017_Irrigated.tif`
  - `Val_2017_allTech.tif`
  - `Val_2017_Irrigated.tif`


## Basic workflow:

## Common process
(1) `config.ipynb` You can specify global parameters for all processes here by a target country. Renaming the config file, for example, 'config_SEN,' you can keep a config setting for the country (this case Senegal) next time you need to rework it. For the actual process, the name of the config file must be `config.ipynb`.

>[!NOTE]
>- In `Specify the name of ADM3 SHP`, every time select a proper option for each target country.
>- In `Specify the name of the Livelihood Zone SHP`, every time select a proper option for each target country. 


(2) `generate_dir.ipynb` As the later PTI visualization process needs a specifically designed directory structure for the PTI team, this tool automatically generates the specified directories under `data`  based on the target country list defined in `config.ipynb` (ie., `config.l_tar_ISO`). 


## Each country process:
(3) `ADM_prep.ipynb` This is a good tool for preparing a fine ADM-3 shapefile, which is the base of all zonal statistics for other steps. As the condition of ADM-3 Shapefile can vary across target countries, you may need to modify this tool if needed.

(4) `Auxilliary_Prep.ipynb` Process GRID3 Settlement layer V1 and WorldPop raster. Note that GRID3 now provides a version 2 (V2) settlement layer, but this does not work for the module. Be sure that you get the V1 layer.

(5) `Conflict.ipynb` Process the ACLED layer (ESRI Shapefile format). The layer is stored in `data > common`. If you need to update the ACLED layer, replace the old one in this folder.

(6) `LivelihoodZones_PopWeighted.ipynb` Process FEWS Livelihood zone or Climate Zone layers. The FEWS is prefered but in case it is not available for your target country, use a Climate Zone layer. You can 

(7) `MapSPAM_to_ADM.ipynb` Process the MapSPAM geotiff images. The set of images should be stored in `data > common > MapSPAM_global_sum`. See the Required raw data section for details.


## Technical notes:
None.

## Contributors:
- `Eigo Tateishi` (transplanting the original to the Colab ver) / No longer working on this repo/project.
- `Grace Doherty` (the original coder) / No longer working on this repo/project.
- :star:`Walker Kosmidou-Bradley` (project leader, expert input) / Contact person

The World Bank (2024)
