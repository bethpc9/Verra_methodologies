# Verra_methodologies
QGIS Py file mapping South African National Land Cover (SANLC) to Verra methodologies.

## Description:
This Python script processes land use classification and VM binning data within the QGIS Python environment. The script maps land use classes (LU_1, LU_2, etc.) from a land use CSV file to corresponding VM bins in a classification CSV, calculates the total hectares for each VM bin, and outputs the summarized data into a new CSV file.

The script is designed to be used in a QGIS Python environment, where it can directly interact with geospatial data, extract land use data, and perform classification and binning tasks efficiently.

## Workflow:
1. Input Files:
- Land Use CSV: Contains hectare data for different land use classes (LU_1_Hectares, LU_2_Hectares, etc.) for each project site. The data is initially extracted and processed using QGIS.
- Classification CSV: Contains a Code column representing land use class codes and VM bin columns with 'Y' indicating which bins the land use classes belong to.

2. Processing Steps:
- The script uses the QGIS Python environment to map each land use class (LU_1, LU_2, etc.) from the classification CSV to the corresponding VM bins.
- It then aggregates the hectares for each project site and assigns them to the relevant VM bins based on the mapping.
- The total hectares for each VM bin are calculated by summing the hectares from the land use classes assigned to each bin.

3. Output:
- The script generates a new CSV file containing the total hectares for each VM bin across all project sites, making the data ready for further analysis or reporting.

## Features:
- Land Use to VM Bin Mapping: Automates the process of assigning land use classes to VM bins based on the classification CSV.
- Hectare Summing: Aggregates hectares from multiple land use classes for each VM bin.
- CSV Output: Outputs the summarized data into a new CSV file, which contains the total hectares for each VM bin.

## Usage:
- This script is designed to be run within the QGIS Python environment, where it can interact with and process geospatial data directly.
- Simply load the land use and classification CSV files, run the script, and the total hectares for each VM bin will be output into a new CSV file.

## Dependencies:
- QGIS Python: The script is designed to be executed within the QGIS Python environment.
- pandas: For handling CSV files and data manipulation.
- Python 3.x: The script is compatible with Python 3.

## How to Use in QGIS:
1. Open QGIS and go to the Python Console.
2. Run the script within QGIS Python Console, ensuring the land use and classification CSV files are in the correct directories.
3. The output CSV file will be saved with the total hectares for each VM bin, which you can use for further analysis.

