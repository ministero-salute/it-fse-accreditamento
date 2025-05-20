# Accreditamento FSE 2.0
Questo repository raccoglie i risultati dei test effettuati per l'accreditamento dei software con il sistema FSE 2.0

- [Accreditamento FSE 2.0](#accreditamento-fse-20)
	- [Procedura di caricamento dei risultati](#procedura-di-caricamento-dei-risultati)
		- [Struttura dei risultati (data.json)](#struttura-dei-risultati-datajson)
		- [File riassuntivo (report-checklist.xlsx)](#file-riassuntivo-report-checklistxlsx)
		- [Pull request](#pull-request)
	- [Gestione equivalenza versione software](#gestione-equivalenza-versione-software)
		- [Procedura di caricamento delle informazioni di equivalenza applicativa](#procedura-di-caricamento-delle-informazioni-di-equivalenza-applicativa)
		- [Struttura file json di equivalenza](#struttura-file-json-di-equivalenza)
	- [Nuova tipologia documentale per applicativo già presente nella Lista dei software convalidati](#nuova-tipologia-documentale-per-applicativo-già-presente-nella-lista-dei-software-convalidati)

## Procedura di caricamento dei risultati
Per inviare i risultati dei test effettuati è necessario esegure una pull request.  
La struttura del repository è la seguente:
    
        GATEWAY/{commonName auth}/{subject_application_vendor}/{subject_application_id}/{subject_application_version}

per ogni software quindi, bisognerà creare la rispettiva *directory di sottomissione* rispettando lo schema.

---

L'insieme dei caratteri che compongono il path della directory è `[a-zA-Z0-9.-_]`[^1] gli *spazi* vanno trasformati in *underscore* `' ' -> _` eventuali altri caratteri non compresi nell'insieme saranno *omessi*.

---

Ad esempio:  
`GATEWAY/A1#111FORNITORE1/FOO_SPA/BARMED/V.4.2.0`

I dati da inviare comprendono:
* file `data.json` contenenti i riferimenti di tracciatura dei risultati dei test
* file pdf usati nelle invocazioni dei servizi (all'interno della directory `FILES`)
  * In caso di validazione, se pertinente (il software ha la funzionalità di firma e la firma è oggetto di adeguamento), i file file pdf utilizzati nell'invocazione dei servizi firmati PADES (all'interno della directory `FILES/SIGNED`)
* file riassuntivo (foglio di calcolo) `report-checklist.xlsx` di tutti i test case eseguiti

I risultati delle verifiche verranno mandate per mail all'indirizzo immesso nel [modulo di richiesta accreditamento](https://ec.europa.eu/eusurvey/runner/FSE-2-validazione)

### Struttura dei risultati (data.json)
All'interno della directory bisognerà creare un file `data.json` con il seguente schema:

|ATTENZIONE|
|---|
|È stato rimosso il campo `email` dalla struttura dati|


```json
{
	"appVendor": "vendor",
	"appID": "id",
	"appVersion": "version",
	"results": [
		{
			"id": 1,
            "ts":"2022-12-23T11:42:00Z",
			"traceId": "b5e75a93-e517-480b-9eaa-6cb8b81d03d8",
			"workflowInstanceId": "2.16.840.1.113883.2.9.2.120.4.4.97bb3fc5bee3032679f4f07419e04af6375baafa17024527a98ede920c6812ed.7ea73d015c^^^^urn:ihe:iti:xdw:2013:workflowInstanceId",
			"files": [
                "T1_VALIDATION.PDF"
                ]
		}
	]
}
```

le chiavi contrassegnate da `*` sono obbligatori

|chiave|descrizione|
|---|---|
|*appVendor|subject_application_vendor|
|*appID|subject_application_id|
|*appVersion|subject_application_version|
|*results|vedi [Results](#results)|

**Results** <a id="results"></a>

contiene la lista dei risultati, uno per ogni caso testato
|chiave|descrizione|
|---|---|
|*id|identificativo del test case nel piano di test|
|*ts|timestamp del test in formato ISO_8601 semplificato `YYYY-MM-DDThh:mm:ssZ` |
|*traceId|traceId restituito dal sistema|
|workflowInstanceId|workflowInstanceId restituito dal sistema|
|files|contiene la lista dei file (nome file) usati durante il test (e caricati nella directory FILES)|

I file dovranno essere posti all'interno della directory `FILES` dentro a quella creata per l'applicativo.

Ad esempio:

`GATEWAY/A1#111FORNITORE1/FOO_SPA/BARMED/V.4.2.0/FILES`

In caso di validazione e se pertinente (il software ha la funzionalità di firma e la firma è oggetto di adeguamento)) i file pdf firmati[^2] PADES andranno posti all'interno della directory `FILES/SIGNED`

Ad esempio:

`GATEWAY/A1#111FORNITORE1/FOO_SPA/BARMED/V.4.2.0/FILES/SIGNED`

### File riassuntivo (report-checklist.xlsx)

Il file riassuntivo deve essere composto a partire dalla [check list](Test%20Case) che individua tutti i possibili test case.


Il file modificato dovrà contenere solo i test individuati da *tipo documento* e *servizio* oggetto dell'accreditamento.

Il file `report-checklist.xlsx` andrà caricato nella *directory di sottomissione*.

Si riporta di seguito il changelog delle modifiche introdotte sul file report-checklist in ottemperanza a quanto espresso dal Decreto settembre 2023: 

| Versione checklist| Data rilascio      | CDA adeguato                                          | Test case obbligatorio da decreto                           |
|-------------------|------------------- |-------------------------------------------------------|-------------------------------------------------------------|
| 8.2.0		    | 12/06/2024         | PSS                                                   |		444		                               |
| 8.2.1		    | 19/07/2024         | RAP, RAD                                              |         417, 446                                            |
| 8.2.2             | 04/12/2024         | RAP                                                   |         417, 418, 460                                       |
| 8.2.3             | 14/02/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC                | 448, 450, 452, 454, 456, 457, 458                           |
| 8.2.4             | 05/03/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC, RAD, PSS, RAP | 448, 450, 452, 454, 456, 457, 458                           |
| 8.2.5             | 28/03/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC, RAD, PSS, RAP | 448, 450, 452, 454, 456, 457, 458, 471, 444, 417, 418, 460  |
| 8.2.6             | 14/05/2025  	 | RSA, LAB, RAD 					 | 448, 450, 452, 454, 456, 457, 458, 471, 444, 417, 418, 460  |

### Pull request
Per inviare i risultati sarà quindi necessario fare un pull request.  
I passi sono sostanzialmente:
* fork del repository
* creazione nel repository forkato della *directory di sottomissione*
* creazione del file `data.json`
* inserimento pdf utilizzati per i test nella directory `FILES`
  * eventuale inserimento dei pdf firmati nella directory `FILES/SIGNED`
* apertura della pull request

La descrizione della pull request dovrà contenere i dati che compongono la *directory di sottomissione*:
* `commonName auth`
* `subject_application_vendor`
* `subject_application_id`
* `subject_application_version`


## Gestione equivalenza versione software 
 
Il fornitore ha la possibilità di autodichiarare l’equivalenza tra una versione di software **già validata** ed una sua release successiva **se questa non ha subito modifiche al codice nei moduli relativi alla gestione dei CDA2 e al colloquio col gateway**.


L’equivalenza è pertanto da intendersi come:
* stesse tipologie documentali trattate
* stessi servizi invocati
* stessa gestione degli errori e casi di applicabilità


Dati questi presupposti le versioni del software contenute nell’autodichiarazione **non è necessario che siano sottoposte al processo di convalida**.

 
### Procedura di caricamento delle informazioni di equivalenza applicativa

Per dichiarare l’equivalenza tra le versioni di un applicativo è necessario eseguire una pull request che riporti come  titolo **”Dichiarazione di versioni equivalenti”**, e contenente il solo file json `versions.json` con le informazioni di equivalenza, la cui struttura è di seguito riportata.

Per eseguire la pull request, seguire le indicazioni sopra riportate.

 
### Struttura file json di equivalenza

All’interno della *directory di sottomissione* creare un file `versions.json` con il seguente schema:

```json
{
    	"appVendor": "vendor",
    	"appID": "id",
    	"appVersion": "version3.0",
    	"ts":"2023-06-08T15:30:29Z",
		"equiv_releases": [
			"version3.1",
			"version3.2",
			"version3.2.1"
		]
  }
```

Di seguito la descrizione delle chiavi del file `versions.json`:

|chiave|descrizione|
|---|---|
|**appVendor**|`subject_application_vendor`|
|**appID**|`subject_application_id`|
|**appVersion**|`subject_application_version` dell'applicativo validato|
|**ts**|timestamp di produzione del file versions.json in formato ISO_8601 semplificato `YYYY-MM-DDThh:mm:ssZ` |
|**equiv_releases**|array di versioni equivalenti a quella validata|


## Nuova tipologia documentale per applicativo già presente nella Lista dei software convalidati

Nel caso un applicativo abbia superato la Fase 1 per una particolare tipologia documentale (per es. LDO) e il fornitore sottometta una nuova richiesta di accreditamento per un’altra tipologia documentale (per es. RSA), l’applicativo ripeterà l’intera Fase 1 per le due tipologie documentali.


I fornitori dovranno sottomettere una nuova pull request contenente tutti i casi di test (e relativo data.json) eseguiti per le due tipologie documentali ( LDO+RSA ).


All’interno della Lista dei software convalidati la soluzione applicativa sarà riportata due volte: nella prima riga si riporterà l’esito relativo al LDO, nella seconda l’esito relativo a LDO, RSA.


Ai fini del conteggio dei documenti trasmessi dalle Regioni/PA si terrà presente la data di conclusione della Fase 1 di ciascuna tipologia documentale.




[^1]: attenzione, questa non è la regular expression corretta, è necessario fare escape di `.`:`[a-zA-Z0-9\.-_]` 

[^2]: non è necessario che i certificati di firma siano "qualificati", verrà controllata solo la corretta apposizione della firma PADES
