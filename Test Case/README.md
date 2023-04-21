# TEST CASE

Questa directory contiene i Test Case da effettuare per l'accreditamento (convalida) dei software al sistema FSE 2.0.

*I file di supporto ai test sono divisi per servizio all'interno delle directory [Validazione](Validazione/) e [Pubblicazione](Pubblicazione/)*

Il file `accreditamento-checklist.xlsx` contiene la lista di tutti i test case possibili tra i quali è necessario individuare quelli rilevanti per la specifica sessione di verifica.  
Il file dovrà essere "*personalizzato*" mantenendo solo i casi attinenti a quanto dichiarato nel modulo di richiesta accreditamento.

## Validazione

All'interno della directory [Validazione](Validazione/) sono presenti i file di supporto per il servizio di **validazione**.

I file di supporto sono all'interno delle specifiche directory, suddivisi per tipologia di documento.

Ogni directory contiene:

* documento di descrizione dei test case.
* foglio contenente i test "OK" con la descrizione dei campi richiesti nei documenti per le diverse tipologie di test.
* foglio contenente i test "KO" con una guida dei campi da valorizzare per le diverse tipologie di test.

## Pubblicazione

**N.B**

**Il processo di accreditamento (convalida) dei software per il servizio di pubblicazione è posticipato, al momento la priorità è data al processo di accreditamento legato all’adeguamento dei CDA2 alle nuove specifiche.  
Si ricorda che sono comunque disponibili i test case di pubblicazione ed è sempre possibile utilizzare i servizi dell’istanza del gateway in pre-produzione per test interni in ottica accreditamento.  
L’avvio dell’accreditamento (convalida) dei software per il servizio di pubblicazione sarà comunicato in seguito.**



All'interno della directory [Pubblicazione](Pubblicazione/) sono presenti i file di supporto per il servizio di **pubblicazione**.

Se il fornitore non ha a disposizione un documento *validato* da usare nei test, può utilizzare i file (già firmati) presenti nella directory 
[PDF_PER_PUBBLICAZIONE](Pubblicazione/PDF_PER_PUBBLICAZIONE/) e i metadati presenti nella directory [REQUEST_BODY_PUBBLICAZIONE](Pubblicazione/REQUEST_BODY_PUBBLICAZIONE).

All'interno di [REQUEST_BODY_PUBBLICAZIONE](Pubblicazione/REQUEST_BODY_PUBBLICAZIONE) ci sono directory, suddivise per tipologia di documento, contenenti:

* file `xml` del CDA2
* file `xml` del CDA2 per operazione di *replace*
* file `json` contenenti i diversi `requestBody` da utilizzare per le diverse operazioni


## Svolgimento dei test

Il fornitore che deve testare il software dovrà quindi:

* Compilare il [modulo di richiesta accreditamento](https://ec.europa.eu/eusurvey/runner/FSE-raccolta-id-applicativo) indicando la tipologia di documento e servizi desiderati
* Selezionare i test rilevanti nel file `accreditamento-checklist.xlsx` (fare riferimento al foglio `summary`)
* Eseguire i test appropiati seguendo anche quanto definito nella directory specifica del tipo di documento
* Collezionare i risultati nel file `report-checklist.xlsx`
* Seguire le [indicazioni](https://github.com/ministero-salute/it-fse-accreditamento/) per il caricamento dei risultati nel repository

**NB** Per i test "KO" è possibile autocertificare la *non applicabilità* dei casi che non possono darsi nell'utilizzo del software specifico.

## Come valorizzare la checklist (tab TestCases)
1. E' necessario compilare sempre le righe **2,3,4,5** con rispettivamente:
   * Nome fornitore dell'applicativo;
   * nome applicazione: `subject_application_id`;
   * Nome fornitore: `subject_application_vendor`;
   * versione applicazione: `subject_application_version`;
2. Per tutti i casi di test coerenti con la/e tipologia/e di documento; utilizzata/e dal software è necessario compilare **SEMPRE** la colonna APPLICABILITA' con SI o NO.
3. Se il test è applicabile la colonna APPLICABILITA' deve essere compilata con SI e dovranno essere valorizzate:
   * `DATA ESECUZIONE`
   * `TIMESTAMP`
   * `TRACEID`
   * `WORKFLOWINSTANCEID` (ove ritornato in response, qualora non ritornato il WORKFLOWINSTANCEID puo' essere lasciato blank)
   * `ERRORE BLOCCANTE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO)
   * `ERRORE VISIBILE A UTENTE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO)
   * `MESSAGGIO DI ERRORE` da compilare con il messaggio di errore visualizzato dall’applicativo, solo per i casi KO (ovvero con colonna CASO OK / KO= KO) visibili all'utente (colonna ERRORE VISIBILE A UTENTE (SI/NO)=SI)
   * `GESTITO IN BACKOFFICE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO)
   * `GESTIONE ERRORE` da compilare con la procedura che viene adottata per la gestione dell'errore, solo per i casi KO (ovvero con CASO OK / KO= KO)
4. Se il test NON è applicabile la colonna APPLICABILITA' riporterà NO e dovrà essere compilata esclusivamente la colonna RAZIONALE DI APPLICABILITA' con le motivazioni per cui il test non è applicabile.
5. Esclusivamente per i casi di test di TIMEOUT, così come riportato in DESCRIZIONE CASO TEST, è necessario valorizzare solo la cella GESTIONE ERRORE con il messaggio di errore visualizzato dall’applicativo e la procedura che viene adottata per la sua gestione.
6. **La colonna TEST AUTOCERTIFICATO non deve mai essere compilata dal fornitore**

 




