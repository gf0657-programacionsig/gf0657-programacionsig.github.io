# Creación y configuración del Jupyter Book de GF-0657 Programación en SIG

1. Creación de un ambiente Conda.
2. Creación del Jupyter Book principal: gf0657-programacionsig.github.io
3. Creación de un Jupyter Book para cada curso, por ejemplo: 2022-ii, accesible en https://gf0657-programacionsig.github.io/2022-ii/
4. Publicación de modificaciones.

## 1. Creación de un ambiente Conda

```shell
# Actualización de Conda
conda update conda

# Borrado del ambiente (si es que existe)
# conda remove -n gf0657 --all

# Creación del ambiente
conda create -n gf0657

# Activación del ambiente
conda activate gf0657

# Configuración del ambiente
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

# Instalación de mamba
conda install mamba

# Instalación de módulos requeridos
mamba install git python jupyter jupyterlab jupyter-book ghp-import numpy pandas matplotlib plotly gdal fiona shapely geopandas rasterio folium streamlit

# Desactivación del ambiente
conda deactivate
```

## 2. Creación del Jupyter Book principal y publicación inicial del sitio web en GitHub Pages

```shell
conda activate gf0657

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create gf0657-programacionsig.github.io

# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build gf0657-programacionsig.github.io

# En este punto, debe crearse en GitHub el repositorio gf0657-programacionsig.github.io

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd gf0657-programacionsig.github.io
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin git@github.com:gf0657-programacionsig/gf0657-programacionsig.github.io.git
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://gf0657-programacionsig.github.io/

conda deactivate
```

## 3. Creación de un Jupyter Book para cada curso y publicación inicial del sitio web en GitHub Pages

```shell
conda activate gf0657

# Creación del Jupyter Book con una plantilla inicial
jupyter-book create 2022-ii

# Generación de archivos HTML (en el subdirectorio _build/html)
jupyter-book build 2022-ii

# En este punto, se crea en GitHub el repositorio 2022-ii

# Configuración del repositorio local y su branch main (para manejar los archivos fuente)
cd 2022-ii
git init
git add .
git commit -m "Commit inicial"
git branch -M main
git remote add origin https://github.com/gf0657-programacionsig/2022-ii.git
git push -u origin main

# Creación del branch gh-pages (para manejar los archivos HTML publicados)
ghp-import -n -p -f _build/html

# En este punto, se configura el repositorio para buscar los archivos de GH Pages en la rama gh-pages
# El sitio debe estar disponible en https://gf0657-programacionsig.github.io/2022-ii/
```

## 4. Publicación de modificaciones

```shell
# Generación de archivos HTML (debe hacerse desde el directorio padre del Jupyter Book)
jupyter-book build gf0657-programacionsig.github.io

cd gf0657-programacionsig.github.io

# Aplicación de cambios en el branch main
git status
git add .
git commit -m "###Comentario###"
git push

# Aplicación de cambios en el branch gh-pages
ghp-import -n -p -f _build/html
```

