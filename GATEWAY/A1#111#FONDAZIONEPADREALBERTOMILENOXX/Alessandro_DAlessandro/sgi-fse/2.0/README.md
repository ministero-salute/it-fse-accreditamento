# Sottomissione Accreditamento FSE 2.0 - LDO

Questa cartella prepara la sottomissione dell'applicativo SGI per la tipologia documentale `LDO`.

Percorso costruito secondo i dati applicativi e di certificato attualmente usati in SGI:
- `commonName auth`: `A1#111#FONDAZIONEPADREALBERTOMILENOXX`
- `subject_application_vendor`: `Alessandro D'Alessandro`
- `subject_application_id`: `sgi-fse`
- `subject_application_version`: `2.0`

Contenuto previsto:
- `data.json`: riferimenti di tracciatura dei test eseguiti
- `report-checklist.xlsx`: checklist compilata
- `FILES/`: PDF usati nei test

Note operative:
- il caso `45` e' un caso descrittivo di timeout applicativo e non ha una transazione Gateway associata; resta documentato nel file checklist e nell'appunto `docs/TIMEOUT_RIGA_45_APPUNTO.txt`, ma non e' incluso in `data.json`
- i nomi file elencati in `data.json` e nel manifest di `FILES/` sono quelli da usare nella raccolta finale dei PDF
