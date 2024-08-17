# Precipitation data extractor

This is a prototype that I'm currently developing in my scientific initiation. Its purpose is to place data stations from multiple climate agencies (such as ANA, SUDENE etc) on a GeoTIFF image using RasterIO library, and then extract its precipitation data to a .csv file using their geographic coordinates.

### Current progress
1. Acquire GeoTIFF images. [:white_check_mark:]
2. Create a feature to allow the script to obtain data from multiple stations without having to run it again for each city (it's the standard behavior of _hydrobr_ library) [:white_check_mark:]
3. Create a Gantt chart to display the data availability for each selected station. [:white_check_mark:]
4. Display the selected stations together with the GeoTIFF image. [:white_check_mark:]
5. Iterate the last step over each .TIF image available. [ ]
6. Extract the rainfall data for each station from all images generated in the previous step to a .csv file. [ ]

## Installation

It's expected to use [Google Colab](https://colab.research.google.com/) to run the script, since

a) a local installation would require installing another package manager besides [pip](https://pip.pypa.io/en/stable/);

b) part of this code expects to access Google Drive to found the necessary files (but it's possible to change that to get those files from your local machine)

However, it's possible to run it locally by installing the libraries via pip by the following commands:

```bash
pip install hydrobr
pip install rasterio
pip install pandas
pip install matplotlib.pyplot
```
However, there is another library still needed ( _geopandas_ ) that is easily installed using [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) package manager. It's actually possible to install it via pip, but it'd require manually installing its dependencies.

Using Conda, run the following commands:

```bash
conda update --all
conda install geopandas
```

## Usage
Firstly, you need a GeoTIFF image so the data can be extracted. Images of that type may be obtained from [ClimateSERV](https://climateserv.servirglobal.net/map). 

![Rainfall image](https://cdn.discordapp.com/attachments/345357344978501642/1034642130485911562/z.jpg?ex=66c1f952&is=66c0a7d2&hm=964628c9d987b72dfc8fe7be7fb173ce10ae8a300a8f5193f2549bf94cb3d36d&? "Rainfall image")

###### Rainfall GeoTIFF image obtained via ClimateSERV, from UCSB CHIRPS database. 

Then, place all GeoTIFF images in the same folder.


### Parameters

**city_list** = Choose the cities to analyse, writing their names inside quotation marks and separating each one with commas. Leave the list empty to get all cities from the select state below.

**state** = Choose the state that contains the selected cities. The script supports only one state per time due to how much time would take to extract that amount of data.

**raster** = Type your images' path inside quotation marks. Currently, it's supporting just one image each time, so type one image's name too.

**data** = The second argument should be **0** or **1**. Select 0 for displaying the station names on the Gantt chart, or 1 for displaying their codes.


## Current results

By now, you can get a raster image displaying the data stations from the selected cities and the GeoTIFF image used.
<br>

![Data stations of Bahia](https://media.discordapp.net/attachments/345357344978501642/1034643557128077423/bahia.png?ex=66c1faa6&is=66c0a926&hm=178f4fc2072508d79f2797cb4bdd63f691a76642a301760d4244459761480756&=&format=webp&quality=lossless&width=562&height=582 "Data stations of Bahia")

###### All data stations from the state of Bahia. The GeoTIFF image used was the same shown on the "Usage" section.
<br>

![Mucuri data availability (codes)](https://media.discordapp.net/attachments/345357344978501642/1034643536739582002/newplot_2.png?ex=66c1faa1&is=66c0a921&hm=45ae909b2fd4f455af64690213f37c2db7bafe6bf2d394aaba2f413bad27b4ae&=&format=webp&quality=lossless&width=1440&height=553 "Mucuri data availability (codes)")

###### Availability of each data station from "Mucuri" (displaying their codes).
<br>

![Mucuri data availability (names)](https://media.discordapp.net/attachments/345357344978501642/1034643536399847504/newplot.png?ex=66c1faa1&is=66c0a921&hm=ac79de0c70a1bf55e313eece7b2b93a20d593088fb00558cfad3df0787ad8e7a&=&format=webp&quality=lossless&width=1440&height=553 "Mucuri data availability (names)")

###### Availability of each data station from "Mucuri" (displaying their names).
