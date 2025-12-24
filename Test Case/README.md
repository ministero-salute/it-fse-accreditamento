# TEST CASE

Questa directory contiene i Test Case da effettuare per l'accreditamento (convalida) dei software al sistema FSE 2.0.

Il file `accreditamento-checklist.xlsx` contiene la lista di tutti i test case possibili tra i quali è necessario individuare quelli rilevanti per la specifica sessione di verifica.  
Il file dovrà essere "*personalizzato*" mantenendo solo i casi attinenti a quanto dichiarato nel modulo di richiesta accreditamento.

All'interno della directory [Validazione](Validazione/) sono presenti i file di supporto, suddivisi per tipologia di documento.

Ogni directory contiene:

* documento di descrizione dei test case.
* foglio contenente i test "OK" con la descrizione dei campi richiesti nei documenti per le diverse tipologie di test.
* foglio contenente i test "KO" con una guida dei campi da valorizzare per le diverse tipologie di test.

**N.B.**
Per quanto riguarda il servizio di pubblicazione, in sostituzione al processo di accreditamento, middleware regionali e document repository locali hanno la possibilità di partecipare al [crash program](https://ministero-salute.github.io/it-fse-support/crashprogram/), un'iniziativa strategica volta a migliorare l'efficienza e l'affidabilità delle interazioni tra i servizi ICT regionali e i sistemi nazionali di gestione dei dati sanitari.

## Svolgimento dei test

Il fornitore che deve testare il software dovrà quindi:

* Compilare il [modulo di richiesta accreditamento](https://ec.europa.eu/eusurvey/runner/FSE-2-validazione) indicando la tipologia di documento e servizi desiderati
* Selezionare i test rilevanti nel file `accreditamento-checklist.xlsx` (fare riferimento al foglio `summary`)
* Eseguire i test appropiati seguendo anche quanto definito nella directory specifica del tipo di documento
* Collezionare i risultati nel file `report-checklist.xlsx`
* Seguire le [indicazioni](https://github.com/ministero-salute/it-fse-accreditamento/) per il caricamento dei risultati nel repository

**NB** Per i test "KO" è possibile autocertificare la *non applicabilità* dei casi che non possono darsi nell'utilizzo del software specifico.

## Come valorizzare la checklist (tab TestCases)
A partire dalla versione 8.2, per la compilazione della checklist occorre seguire le seguenti istruzioni. 
1. E' necessario compilare sempre le righe **2,3,4,5** con rispettivamente:
   * Nome fornitore dell'applicativo;
   * nome applicazione: `subject_application_id`;
   * Nome fornitore: `subject_application_vendor`;
   * versione applicazione: `subject_application_version`;

2) Per tutti i casi di test coerenti con la/e tipologia/e di documento utilizzata/e dal software è necessario compilare SEMPRE la colonna APPLICABILITA' con SI o NO
3) Nel caso in cui tra le tipologie documentali oggetto di accreditamento per l'applicativo figurino PSS,RAD,RAP i relativi casi di test con id 444,446,417,418,460 che recepiscono quanto previsto dal Decreto 07 settembre 2023, devono essere obbligatoriamente eseguiti e compilati (la colonna APPLICABILITA' deve essere valorizzata con SI)
4) Se il test è applicabile la colonna APPLICABILITA' deve essere compilata con SI e dovranno essere valorizzate:
   * `DATA ESECUZIONE`
   * `TIMESTAMP`
   * `TRACEID`
   * `WORKFLOWINSTANCEID` (ove ritornato in response, qualora non ritornato il WORKFLOWINSTANCEID puo' essere lasciato blank)
   * `ERRORE BLOCCANTE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO) e per i casi di test di TIMEOUT,
   * `ERRORE VISIBILE A UTENTE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO) e per i casi di test di TIMEOUT,
   * `MESSAGGIO DI ERRORE` da compilare con il messaggio di errore visualizzato dall’applicativo, solo per i casi KO (ovvero con colonna CASO OK / KO= KO) visibili all'utente (colonna ERRORE VISIBILE A UTENTE (SI/NO)=SI)
   * `GESTITO IN BACKOFFICE` (SI/NO) da compilare solo per i casi KO (ovvero con colonna CASO OK / KO= KO) e per i casi di test di TIMEOUT,
   * `GESTIONE ERRORE` da compilare con la procedura che viene adottata per la gestione dell'errore, solo per i casi KO (ovvero con CASO OK / KO= KO) e per i casi di test di TIMEOUT,  specificando le modalità di invio del documento clinico al FSE a seguito della correzione dell'errore e chiarendo se è possibile per l'utente (medico) proseguire con il processo e produrre il documento. Esclusivamente per i casi di test di TIMEOUT, qualora non fosse prevista una coda di retry e la gestione dell'errore non fossa gestita da un operatore di backoffice, indicare le modalità attraverso cui è reso esplicito all’utente (medico) di effettuare nuovi tentativi di invio verso il FSE fino al ripristino del servizio di validazione.
5) Se il test NON è applicabile la colonna APPLICABILITA' riporterà NO e dovrà essere compilata esclusivamente la colonna RAZIONALE DI APPLICABILITA' con le motivazioni per cui il test non è applicabile. Il campo è valorizzabile tramite selezione da menù a tendina (campo/sezione non gestito/a in modo strutturato dall’applicativo;campo obbligatorio; campo valorizzato di default; campo valorizzato in automatico tramite dati recuperati da servizi esterni; campo valorizzabile tramite selezione da un set di valori ammessi; l’applicativo effettua controlli preventivi sul dato inserito; altro (specificare)). Nel caso in cui si selezioni l'opzione "Altro (specificare)" è necessario compilare la colonna RAZIONALE DI "APPLICABILITA' - ALTRO" con le motivazioni per le quali il test non è applicabile
6) La colonna TEST AUTOCERTIFICATO non deve mai essere compilata dal fornitore


## Cambiamenti

Si riporta di seguito il changelog delle modifiche introdotte sul file report-checklist in ottemperanza a quanto espresso dal Decreto settembre 2023: 

| Versione checklist| Data rilascio      | CDA adeguato                                          | Test case obbligatorio da decreto                           |
|-------------------|------------------- |-------------------------------------------------------|-------------------------------------------------------------|
| 8.2.0		    | 12/06/2024         | PSS                                                   |		444		                               |
| 8.2.1		    | 19/07/2024         | RAP, RAD                                              |         417, 446                                            |
| 8.2.2             | 04/12/2024         | RAP                                                   |         417, 418, 460                                       |
| 8.2.3             | 14/02/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC                | 448, 450, 452, 454, 456, 457, 458                           |
| 8.2.4             | 05/03/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC, RAD, PSS, RAP | 448, 450, 452, 454, 456, 457, 458                           |
| 8.2.5             | 28/03/2025  	 | RSA, LDO, LAB, VPS, CERT_VAC, SING_VAC, RAD, PSS, RAP | 448, 450, 452, 454, 456, 457, 458, 471, 444, 417, 418, 460  |
| 8.2.6             | 14/05/2025  	 | RSA, LAB, RAD                                         | 448, 450, 452, 454, 456, 457, 458, 471, 444, 417, 418, 460  |
