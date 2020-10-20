# Formato dei dati meteorologici

I dati debbono essere in formato **long**: 
- sotto il campo _station_code_ e _station_eu_code_ si susseguono i codici delle stazioni di monitoraggio
- sotto il campo _date_ si susseguono le date dei singoli giorni relativi al periodo dell'analisi dei dati

I file di output debbono essere in formato testo (estensione `.csv`) utilizzando la virgola (,) come separatore di campo.

I dati di ciascuna stazione di monitoraggio sono identificati dal campo:
- station_eu_code
- date

Il campo date deve essere nel formato: ANNO-MESE-GIORNO
- anno: 4 cifre
- mese: due cifre (0 per il padding)
- giorno: due cifre (0 per il padding)

**I dati devono essere riportati (a meno di eccezioni) con una cifra decimale**.

## Dati mancanti

I dati mancanti debbono essere identificati dalla stringa NA.

## Nomi dei campi

Per facilitare la lettura dei dati su R, le intestazioni dei file dati `.csv` devono rispettare le seguenti regole:
- NON devono contenere spazi
- NON devono iniziare con una cifra (0-9( 
- devono contenere SOLO lettere (A-Z) e cifre (0-9)
- devono essere nomi brevi di chiaro significato

Si suggerisce di utilizzare la seguente tabella per i nomi delle variabili climatiche:

| Nome esteso variabile | codice per intestazione file `.csv` | Unità di misura | Aggregazione giornaliera |
| ---| --- | --- | --- |
| Surface pressure | sp | hPa | media |
| Average temperate (2m) | t2m | °C | media |
| Maximum temperature (2m) | tmax2m | °C | media |
| Minimum temperature (2m) | tmin2m |  °C | media |
| Planet Boundary Layer ore 00 | pbl00 | km | media |
| Planet Boundary Layer ore 12 | pbl12 | km | media |
| Total precipitation | tp | mm | somma |
| Previous day total precipitation | ptp | mm | somma |
| Wind speed | wspeed | m/s | media |
| Wind direction | wdir | gradi | **moda** |
| Wind U component (10 meters) | u10m | numero | media |
| Wind V component (10 meters) | v10m | numero | media |
| Relative Humidity | rh | % | media |
| Wind gust | wgust | m/s | Valore massimo giornaliero  | media |
| Net irradiance | nirradiance | W/m^2 | media |
| Altre ? | ?? | ?? | ?? |

** NOTA: la tabella sopra ancora non è definitiva **

## Esempio di file dati prodototto dagli archivi netCDF

L'ordine delle colonne all'interno del file **NON** è importante.

|station_eu_code|date|t2m|tp|altre variabili|
|---|---|---|---|---|
|IT0966A|2013-01-01|49.7|---|---|
|IT0966A|2013-01-02|25.5|---|---|
|IT0966A|2013-01-03|NA|---|---|
|IT0966A|2013-01-04|45.0|---|---|
|IT0966A|2013-01-05|46.9|---|---|
|IT0966A|2013-01-06|64.0|---|---|
|IT0966A|2013-01-07|51.6|---|---|
|IT0966A|2013-01-08|46.6|---|---|
|IT0966A|2013-01-09|48.8|---|---|
|IT0966A|2013-01-10|61.5|---|---|
|---|---|---|---|---|
|IT0967A|2013-01-08|46.64223|---|---|
|IT0967A|2013-01-09|48.8916|---|---|
|IT0967A|2013-01-10|61.53846|---|---|
