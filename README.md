# ChileAyuda.cl - Web Scraper

[![Build Status](https://travis-ci.org/davidlaym/chileayuda_newsscraper.svg?branch=master)](https://travis-ci.org/davidlaym/chileayuda_newsscraper)

Este scraper tiene como objetivo centralizar noticias de varias fuentes en un solo
origen para luego poder procesar y difundir a distintos sistemas.

## Stack de tecnologías

 - NodeJs

## Como instalar / ejecutar

``` bash
# Instalar dependencias
npm install

# Correr tests
npm run test

# Ejecutar (prod)
node scraper.js --source <source-name>

```

## Uso
``` bash 
# Una ejecución por fuente de datos

node scraper.js --source <source-name>

# El resultado es que genera un archivo en disco con el contenido
# parseado en JSON

```

## Cómo funciona

Este scraper consta de un controller, un fetcher, un writer y un conjunto de parsers.

El controller se encarga de delegar entre los componentes y realizar el control
de errores.

El fetcher se encarga de realizar el request http y generar un DOM mediante
cheerio.

Los parsers declaran que fuentes soporta este scraper. Cada parser soporta a una
fuente en particular, declarando su nombre, url y lo más importante, una función
que convierte el DOM en un JSON según lo que interese de cada sitio  en particular

El writer se encarga de escribir los resultados a un JSON probando que no haya
duplicados y que se mantengan/eliminen registros históricos deacuerdo a los parametros 
configurados.