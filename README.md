# Formato dei dati meteorologici

I dati debbono essere in formato **long** rispetto al codice stazione e alla data: 
- sotto il campo _station_code_ e/o _station_eu_code_ si susseguono i codici delle stazioni di monitoraggio
- sotto il campo _date_ si susseguono le date dei singoli giorni relativi al periodo dell'analisi dei dati

I file di output debbono essere in formato testo (estensione `.csv`) utilizzando la virgola (,) come separatore di campo.

I dati di ciascuna stazione di monitoraggio sono identificati dal campo:
- station_eu_code (Raffaele ha utilizzato questo come codice identificativo delle stazioni per gli inquinanti)
- date

Il campo date deve essere nel formato: ANNO-MESE-GIORNO
- anno: 4 cifre
- mese: due cifre (0 per il padding nel caso dei mesi da 1 a 9)
- giorno: due cifre (0 per il padding nel caso dei giorni da 1 a 9)

Coordinate dei punti stazione:
- epsg 32632 (UTM32) in kilometri 


I dati devono essere riportati (a meno di eccezioni) con una cifra decimale. 
Separatore dicemale: "."

## Dati mancanti

- I dati mancanti debbono essere identificati dalla stringa NA (no -999 o altre stringhe tipo NULL).
- Il calendario (il campo date) deve essere completo anche laddove tutte le variabili siano mancanti (riga di NA).

## Nomi dei campi

Per facilitare la lettura dei dati su R, le intestazioni dei file dati `.csv` devono rispettare le seguenti regole:
- NON devono contenere spazi
- NON devono iniziare con una cifra (0-9) 
- NON devono contenere caratteri spaciali, SOLO lettere (A-Z) e cifre (0-9)
- devono essere nomi brevi di chiaro significato

Per i nomi delle variabili climatiche principali utilizzare la seguente tabella in cui sono riportati:
- il nome sintetico della variabile
- l'unità di misura da utilizzare 

| Nome esteso variabile | codice per intestazione file `.csv` | Unità di misura | Aggregazione giornaliera |
| ---| --- | --- | --- |
| Surface pressure | sp | hPa | media |
| Average temperate (2m) | t2m | °C | media |
| Maximum temperature (2m) | tmax2m | °C | **massimo giornaliero** |
| Minimum temperature (2m) | tmin2m |  °C | **minimo giornaliero** |
| Planet Boundary Layer ore 00 | pbl00 | km | media o **valore istantaneo** |
| Planet Boundary Layer ore 12 | pbl12 | km | media **valore istantaneo** |
| Total precipitation | tp | mm | somma |
| Previous day total precipitation | ptp | mm | somma |
| Wind speed | wspeed | m/s | media |
| Wind direction | wdir | gradi | **moda** |
| Wind U component (10 meters) | u10m | m/s  | media |
| Wind V component (10 meters) | v10m | m/s  | media |
| Relative Humidity | rh | % | media |
| Wind gust | wgust | m/s | **massimo giornaliero**  | media |
| Net irradiance | nirradiance | W/m^2 | media |


La tabella qui sotto riportata si riferisce ad altre variabili che potrebbero essere d'interesse per il progetto e che meritano comunque un approfondimento:


## Potenziali variabili meteorologiche aggiuntive emerse dall'analisi della letteratura scientifica:

| Nome esteso variabile | codice per intestazione file `.csv` | Unità di misura | Aggregazione giornaliera |
| ---| --- | --- | --- |
| Front | frontcat | numero o testo | categoriale |
| Number of days since front | dfront | numero | somma di giorni |
| Synoptic group | syngr | numero o testo | categoriale |
| Cloud cover | clcover |  okta | media |
| Cloud cover maxmin| clcovermaxmin |  okta | differenza massimo-minimo giornaliero (se disponibile) |
| Back trajectory | backtraj | numero o testo | categoriale |
| Altre da ERA5? | ?? | ?? | ?? |

**NOTA: la tabella sopra ancora non è definitiva**

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
