# Accreditamento FSE 2.0 (DRAFT)
Questo repository raccoglie i risultati dei test effettuati per l'accreditamento dei software con il sistema FSE 2.0

- [Accreditamento FSE 2.0 (DRAFT)](#accreditamento-fse-20-draft)
	- [Procedura di caricamento dei risultati](#procedura-di-caricamento-dei-risultati)
		- [Struttura dei risultati (data.json)](#struttura-dei-risultati-datajson)
		- [File riassuntivo (report-checklist.xlsx)](#file-riassuntivo-report-checklistxlsx)
		- [Pull request](#pull-request)

## Procedura di caricamento dei risultati
Per sottomettere i risultati dei test effettuati è necessario esegure una pull request.  
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

I risultati delle verifiche verranno mandate per mail all'indirizzo immesso nel [modulo di richiesta accreditamento](https://ec.europa.eu/eusurvey/runner/FSE-raccolta-id-applicativo)

### Struttura dei risultati (data.json)
All'interno della directory bisognerà creare un file `data.json` con il seguente schema:

|ATTENZIONE|
|---|
|È stato rimosso il campo `email` dalla struttura dati|


```json
{
	"appVendor": "vendor",
	"appID": "id",
	"appVersion": "version"
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




[^1]: attenzione, questa non è la regular expression corretta, è necessario fare escape di `.`:`[a-zA-Z0-9\.-_]` 

[^2]: non è necessario che i certificati di firma siano "qualificati", verrà controllata solo la corretta apposizione della firma PADES