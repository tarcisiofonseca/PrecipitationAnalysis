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

![Rainfall image](https://cdn.discordapp.com/attachments/345357344978501642/1034642130485911562/z.jpg?ex=66c1f952&is=66c0a7d2&hm=964628c9d987b72dfc8fe7be7fb173ce10ae8a300a8f5193f2549bf94cb3d36d&) "Rainfall image")

###### Imagem de precipitação GeoTIFF obtida no ClimateSERV, do banco de dados UCSB CHIRPS. 

Coloque todas as imagens na mesma pasta.


### Parâmetros

**municipios_lista** = Escolha os municípios que deseja analisar, escrevendo seus nomes dentro de aspas e os separando com vírgulas. Também é possível deixar a lista vazia para selecionar todos os municípios do estado abaixo.

**estado** = Escolha o o estado que contém os municípios escolhidos acima. O script suporta apenas um estado por vez.

**raster** = Insira o caminho do diretório de suas imagens GeoTiff. No momento, apenas uma imagem é suportada por vez, então insira o nome da imagem também.

**dados** = O segundo argumento deve ser **0** ou **1**. Selecione 0 para exibir o nome das estações no diagrama Gantt ou 1 para exibir os seus códigos.


## Resultados atuais

No momento, é possível obter uma imagem raster que exibe as estações de coleta de cada um dos municípios selecionados sobre a imagem GeoTIFF.
<br>

![Estações de coleta da Bahia](https://media.discordapp.net/attachments/345357344978501642/1034643557128077423/bahia.png?ex=66c1faa6&is=66c0a926&hm=178f4fc2072508d79f2797cb4bdd63f691a76642a301760d4244459761480756&=&format=webp&quality=lossless&width=562&height=582)

###### Todas as estações da Bahia. A imagem GeoTIFF usada é a mesma presente na sessão "Uso".
<br>

![Disponibilidade de dados de Mucuri (códigos)](https://media.discordapp.net/attachments/345357344978501642/1034643536739582002/newplot_2.png?ex=66c1faa1&is=66c0a921&hm=45ae909b2fd4f455af64690213f37c2db7bafe6bf2d394aaba2f413bad27b4ae&=&format=webp&quality=lossless&width=1440&height=553) "Disponibilidade de dados de Mucuri (códigos)")

###### Disponibilidade de dados de cada estação de coleta de "Mucuri" (exibindo seus códigos).
<br>

![Disponibilidade de dados de Mucuri (nomes)](https://media.discordapp.net/attachments/345357344978501642/1034643536399847504/newplot.png?ex=66c1faa1&is=66c0a921&hm=ac79de0c70a1bf55e313eece7b2b93a20d593088fb00558cfad3df0787ad8e7a&=&format=webp&quality=lossless&width=1440&height=553) "Disponibilidade de dados de Mucuri (nomes)")

###### Disponibilidade de dados de cada estação de coleta de "Mucuri" (exibindo seus nomes).
