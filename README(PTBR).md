# Extrator de dados de precipitação

Esse é um protótipo que desenvolvi durante meu projeto de de iniciação científico. Seu propósito é dispor as estações de dados de diversas agências climáticas (tais como ANA, SUDENE etc) em uma imagem GeoTIFF usando a biblioteca RasterIO e, após isso, extrair os seus dados de precipitação para um arquivo .csv usando suas cordenadas geográficas.

### Progresso atual
1. Adquirir imagens GeoTIFF. [:white_check_mark:]
2. Implementar a obtenção dos dados de múltiplas estações em uma única execução (esse é o padrão da biblioteca _hydrobr_). [:white_check_mark:]
3. Criar um diagrama Gantt para mostrar a disponibilidade de dados de cada estação selecionada. [:white_check_mark:]
4. Mostrar as estações selecionadas junto com o mapa Raster. [:white_check_mark:]
5. Iterar o passo anteior para cada imagem GeoTIFF disponível. [ ]
6. Exportar os dados de precipitação de cada estação selecionada para uma planilha .csv. [ ]

## Instalação

É esperado que seja usado o [Google Colab](https://colab.research.google.com/) para executar o script, já que

a) uma instalação local requer um outro gerenciador de pacotes além do [pip](https://pip.pypa.io/en/stable/);

b) parte do código foi construída para acessar o Google Drive em busca dos arquivos necessários (mas é possível alterá-las para buscar esses arquivos na máquina local)

No entanto, é possível rodar o script localmente ao instalar as bibliotecas via pip com os seguintes comandos:

```bash
pip install hydrobr
pip install rasterio
pip install pandas
pip install matplotlib.pyplot
```
Porém, há uma outra biblioteca chamada ( _geopandas_ ) que é instalada mais facilmente usando o gerenciador de pacotes [Conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html). É possível instalá-la via pip, mas será necessário instalar sua dependências manualmente (há um tutorial para isso no próprio site).

Usando o Conda, execute os seguintes comandos:

```bash
conda update --all
conda install geopandas
```

## Uso
Inicialmente, você precisa de uma imagem GeoTIFF para que seja feita a extração dos dados. Esse tipo de imagem pode ser obtida pelo [ClimateSERV](https://climateserv.servirglobal.net/map). 

![Rainfall image](https://media.discordapp.net/attachments/345357344978501642/1034642130485911562/z.jpg "Rainfall image")

###### Imagem de precipitação GeoTIFF obtida no ClimateSERV, do banco de dados UCSB CHIRPS. 

Coloque todas as imagens na mesma pasta.


### Parâmetros

**city_list** = Choose the cities to analyse, writing their names inside quotation marks and separating each one with commas. Leave the list empty to get all cities from the select state below.

**state** = Choose the state that contains the selected cities. The script supports only one state per time due to how much time would take to extract that amount of data.

**raster** = Type your images' path inside quotation marks. Currently, it's supporting just one image each time, so type one image's name too.

**data** = The second argument should be **0** or **1**. Select 0 for displaying the station names on the Gantt chart, or 1 for displaying their codes.


## Current results

By now, you can get a raster image displaying the data stations from the selected cities and the GeoTIFF image used.
<br>

![Data stations of Bahia](https://media.discordapp.net/attachments/345357344978501642/1034643557128077423/bahia.png?width=412&height=427 "Data stations of Bahia")

###### All data stations from the state of Bahia. The GeoTIFF image used was the same shown on the "Usage" section.
<br>

![Mucuri data availability (codes)](https://media.discordapp.net/attachments/345357344978501642/1034643536739582002/newplot_2.png?width=1025&height=394 "Mucuri data availability (codes)")

###### Availability of each data station from "Mucuri" (displaying their codes).
<br>

![Mucuri data availability (names)](https://media.discordapp.net/attachments/345357344978501642/1034643536399847504/newplot.png?width=1025&height=394 "Mucuri data availability (names)")

###### Availability of each data station from "Mucuri" (displaying their names).
