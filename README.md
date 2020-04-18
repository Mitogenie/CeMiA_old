# CeMiA
[![N|Solid](https://raw.githubusercontent.com/Mitogenie/CeMiA/master/misc/KLab.png)](https://mic.med.virginia.edu/kashatus/)

### Cellular Mitochondrial Analyzer 

![Build Status](https://raw.githubusercontent.com/Mitogenie/CeMiA/master/misc/ver.png)
##### CeMiA is a set of tools to enable high-throughput analysis of mitochondrial network morphology.

  - ##### Cell Catcher
  - ##### Mito Miner
  - ##### MiA

###### User Interface
All the tools in CeMiA toolkit offer interactive, semi graphical user interface through Jupyter notebooks.
###### Processing
All the tools analyze one cell at a time. However, Cell Catcher and Mito Miner, benefit from Multi-Threading, where applicable, to enhance the performance.
###### Requirements
  - CeMiA toolkit is developed in Jupyter notebooks using Python 3. Since it benefits from a wide range of Python libraries, along with Jupyter notebooks, we suggest installing Anaconda distribution of Python (V 3.7). --> [Download Anaconda](https://www.anaconda.com/distribution/)
  - While Anaconda installation takes care of most of the library requirements for CeMiA, there is only one more library (OpenCV) that needs to be installed, which can be done through command line.
    - Windows: Use Anaconda Prompt.
    - MacOS, Linux: Use Terminal.
```sh
$ pip install opencv-python==3.4.2.17
```
### CeMiA Toolkit

#### Cell Catcher
Cell Catcher is a tool designed to automatically detect, separate, and isolate individual cells from 2d multi-cell images. This tool uses the statistical distribution of mitochondria and nuclei across the image to separate individual cells from the images and export them as single-cell images.

###### What to know before use
- Input: Standard RGB Tiff images
    - Multi-cell fluorescence images
        - Number of stains: 2 
            - Nuclei should be stained with DAPI
- Output: Single-cell fluorescence images (Standard RGB Tiff)
    - Output images can used as input for Mito Tracker to extract their mitochondrial network, or they can be independently used to train the desired ML or NN models where appropriate. 

###### Instructions
- Run Cell Catcher.ipynb using Jupyter notebook.
    - You may find this video on Jupyter notebooks very helpful: [Watch Here](https://youtu.be/HW29067qVWk)
        - Note: We are not affiliated with the owner of the above video. We just found this video on Jupyter notebooks very helpful, There are plenty of great tutorials about this subject, and you may use any source your prefer.
- The Jupyter notebook file provides the users with step-by-step instructions to analyze their data.

###### Development
- 500+ images were used to develop and test Cell Catcher.
#### Mito Miner
Mito Miner is a tool to segment mitochondrial netwrok in the cells. It uses the statistical distribution of pixel intensities across the mitochondrial network to detect and remove background noise from the cell and segment the mitochondrial network. Additionally, this tool can further improve the accuracy of the mitochondrial network segmentation through an optional adaptive correction, which takes the variation in the efficiency of fluorescence staining across each cell into account to enhance mitochondrial segmentation. 
###### What to know before use
- Input: Standard RGB Tiff images
    - Single-cell fluorescence images
        - Number of stains: 2 
            - Nuclei should be stained with DAPI
- Output: Single-cell binary images of mitochondrial network
    - Output images can used as input for MiA to quantify their mitochondrial network, or they can be independently used to train the desired ML or NN models where appropriate. 
###### Instructions:
- Run Mito Miner.ipynb using Jupyter notebook.
    - You may find this video on Jupyter notebooks very helpful: [Watch Here](https://youtu.be/HW29067qVWk)
        - Note: We are not affiliated with the owner of the above video. We just found this video on Jupyter notebooks very helpful, There are plenty of great tutorials about this subject, and you may use any source your prefer.
- The Jupyter notebook file provides the users with step-by-step instructions to analyze their data.
###### Development
- 7500+ images were used to develop and test Mito Miner.
#### MiA (Mitochondrial Analyzer)
MiA uses the binarized mitochondrial network to perform greater than 100 mitochondria-level and cell-level morphometric measurements. 
###### What to know before use
- Input: Single-cell binary images of mitochondrial network
- Output: Tabular data (TSV format), including aggregate(per cell, and per mitochondrion where applicable) and raw (per mitochondrion) measurements. 
    - Why raw data along with aggregate measurements?
        - Flexibility! By providing raw data, users can limit or aggregate their data using their own criteria on each mitochondrial, or sub mitochondrial measurements, which can provide additional insight based on their specific applications.
###### Instructions:
- Run Mito Miner.ipynb using Jupyter notebook.
    - You may find this video on Jupyter notebooks very helpful: [Watch Here](https://youtu.be/HW29067qVWk)
        - Note: We are not affiliated with the owner of the above video. We just found this video on Jupyter notebooks very helpful, There are plenty of great tutorials about this subject, and you may use any source your prefer.
- The Jupyter notebook file provides the users with step-by-step instructions to analyze their data.
###### Development
- 4500+ images were used to develop and test MiA.

#### Nomenclature of Features
##### Mitochondria Level Measurements
- These features have the following format: mito_<feature name> and are raw measurements.
    - Examples:
        - area of individual mitochondrion in the cell: mito_area
##### Cell Level Measurements
###### Mitochondrial aggregate measurements
- These are cell-level measurements that are aggregates of raw mitochondrial-level measurements.
    - cell_mean_mito_<feature>: Average of the feature among all the mitochondria in the cell.
        - Example: 
            - cell_mean_mito_area: Average of the area among all the mitochondria in the cell.
            
    - cell_median_mito_<feature>: Median of the feature among all the mitochondria in the cell.
        - Example: 
            - cell_median_mito_area: Median of the area among all the mitochondria in the cell.
    - cell_std_mito_<feature>: Standard Deviation of the feature among all the mitochondria in the cell. 
        - Example: 
            - cell_std_mito_area: Standard deviation of the area among all the mitochondria in the cell.

###### Cell level measurements based on mitochondria distribution
- These features have the following format: cell_<feature name> and are aggregate measurements.
    - Examples:
        - Fractal dimension of the mitochondrial network of the cell: cell_network_fractal_dimension

Details of all the features measured by MiA can be found here: [Features Dictionary.txt](https://github.com/Mitogenie/CeMiA/blob/master/Features%20Dictionary.txt)

#### Libraries used for development (A/Z)
- copy
- cv2
- datetime
- math
- matplotlib.pyplot
- numpy
- os
- pandas
- random
- scipy
- skimage
