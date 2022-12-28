# TEST CASE

Questa directory contiene i Test Case da effettuare per l'accreditamento dei software al sistema FSE 2.0.

Il file `accreditamento-checklist.xlsx` contiene la lista di tutti i test case possibili tra i quali è necessario individuare quelli rilevanti per lo specifico accreditamento.  
Il file dovrà essere "*personalizzato*" mantenendo solo i casi attinenti a quanto dichiarato nel modulo di richiesta accreditamento.

I test sui documenti sono descritti, suddivisi per tipologia di documento, all'interno delle specifiche directory.
 
Ogni directory contiene:

* documento di descrizione dei test case.
* foglio contenente i test "OK" con la descrizione dei campi richiesti nei documenti per le diverse tipologie di test.
* foglio contenente i test "KO" con una guida dei campi da valorizzare per le diverse tipologie di test.

## Svolgimento dei test

Il fornitore che deve accreditare il software dovrà quindi:

* Compilare il [modulo di richiesta accreditamento](https://ec.europa.eu/eusurvey/runner/FSE-raccolta-id-applicativo) indicando la tipologia di documento e servizi desiderati
* Selezionare i test rilevanti nel file `accreditamento-checklist.xlsx` (fare riferimento al foglio `summary`)
* Eseguire i test appropiati seguendo anche quanto definito nella directory specifica del tipo di documento
* Collezionare i risultati nel file `report-checklist.xlsx`
* Seguire le [indicazioni](https://github.com/ministero-salute/it-fse-accreditamento/) per il caricamento dei risultati nel repoistory

**NB** Per i test "KO" è possibile autocertificare la *non applicabilità* dei casi che non possono darsi nell'utilizzo del software specifico.
