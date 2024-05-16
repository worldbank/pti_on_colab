# PTI_on_Colab (PTI raw data prep on Google Colab)
Prepare the PTI raw data of the coutnry of interest solely on the Google Colab environment with a complete Pythonic approach.


## Structure of the pipeline:
•	/content/drive/MyDrive/Colab Notebooks/PTI/OLD config files
Just stored the country config file for the previous work. Just reference.
•	/content/drive/MyDrive/Colab Notebooks/PTI/OLDversion
Original codes from Grace. For debugging purposes.
•	/content/drive/MyDrive/Colab Notebooks/PTI/data
All raw data and products will be stored here.
•	/content/drive/MyDrive/Colab Notebooks/PTI/tools.py
Common Python tool. No need to open it.


## Quick start:
Put the PTI folder with all codes in your own Google Drive:
/content/drive/MyDrive/Colab Notebooks/PTI/


## Basic workflow:

### Common process
(1) 'config.ipynb' You can specify global parameters for all processes here by a target country. Renaming the config file, for example, 'config_SEN,' you can keep a config setting for the country (this case Senegal) next time you need to rework it (see inside the 'OLD config files' for example). For the actual process, the name of the config file must be 'config.ipynb.'

NOTE1: In Specify the name of ADM3 SHP, every time select a proper option for each target country.
NOTE2: In Specify the name of the Livelihood Zone SHP, every time select a proper option for each target country. 

(2) generate_dir.ipynb-> As Taka needs a specifically designed directory structure for his work, this tool automatically generates the specified directories under 'data' folder based on the target country list defined in the config file (ie., config.l_tar_ISO). 

PUT all available raw data in the generated directories( **/Source ). For example, a WorldPop raster of Senegal should be stored in
/content/drive/MyDrive/Colab Notebooks/PTI/data/SEN/WorldPop/Source

It would be nice to have a data check sheet like below to organize the process.
What you need to download beforehand are basically ADM-3 shapefile (or ADM-1 – ADM3 Shapefiles), WorldPop raster, FEWS Livelihood or Climate Zone layers. ACLED and MapSPAM data are already stored in the common folder.

Each country process:
(3) ADM_prep.ipynb-> This is a good tool for preparing a fine ADM-3 shapefile, which is the base of all zonal statistics for other steps. As the condition of ADM-3 Shapefile can vary across target countries, you may need to modify this tool if needed.

(4) Auxilliary_Prep.ipynb -> Process GRID3 Settlement layer V1 and WorldPop raster. Note that GRID3 now provides a version 2 (V2) settlement layer, but this does not work for the module. Be sure that you get the V1 layer.

(5) Conflict.ipynb -> Process the ACLED layer. The layer is stored in data > common. If you need to update the ACLED layer, replace the old one in this folder.

(6) LivelihoodZones_PopWeighted.ipynb -> Process FEWS Livelihood zone or Climate Zone layers. The FEWS is prefered but in case it is not available for your target country, use a Climate Zone layer. You can 

(7) MapSPAM_to_ADM.ipynb -> Process the MapSPAM layer. The layer is stored in data > common > MapSPAM_global_sum


##Technical notes:
TBA

##Contributors
- Eigo Tateishi (transplanting the original to the Colab ver)
- Grace Doherty (the original coder)
- Walker Kosmidou-Bradley (expert input)

The World Bank (2024)