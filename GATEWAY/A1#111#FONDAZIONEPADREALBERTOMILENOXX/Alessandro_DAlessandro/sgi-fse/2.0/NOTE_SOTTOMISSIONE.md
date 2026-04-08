# Note operative

## Checklist

- usare il file `report-checklist.xlsx` come file riepilogativo finale
- nella checklist il campo `Esito` va valorizzato con `PASS` o `FAIL`

## Casi LDO coperti

- `29`, `37`
- `45` (descrittivo)
- `64`, `66`, `67`, `68`, `69`, `70`, `71`, `72`, `73`, `74`
- `450`, `451`
- `467`

## Casi non inseriti in data.json

- `45`: non ha una transazione Gateway associata con `traceId` tecnico; resta documentato nella checklist e nel file `docs/TIMEOUT_RIGA_45_APPUNTO.txt`

## File di supporto in questo repository

Per i dettagli di compilazione delle singole righe:
- `docs/CT10_RIGA_68_APPUNTO.txt`
- `docs/CT11_RIGA_69_APPUNTO.txt`
- `docs/CT12_RIGA_70_APPUNTO.txt`
- `docs/CT13_RIGA_71_APPUNTO.txt`
- `docs/CT14_RIGA_72_APPUNTO.txt`
- `docs/CT15_RIGA_73_APPUNTO.txt`
- `docs/CT16_RIGA_74_APPUNTO.txt`
- `docs/CT19_RIGA_467_APPUNTO.txt`
- `docs/TIMEOUT_RIGA_45_APPUNTO.txt`

## Evidenze eseguite direttamente

- `450` rieseguito il `08/04/2026` tramite pulsante dedicato `CT17 OK`
  - `traceId=a5072e1a94a0f5fe8af17188a6bae658`
  - `workflowInstanceId=2.16.840.1.113883.2.9.99.999.1.1.b5eb4a5fdbd67ac2506b34952bb0e02feaf8905c1dfe11270e110a6019c98b96.a854da9906^^^^urn:ihe:iti:xdw:2013:workflowInstanceId`
  - `idtransfse=40`
- `451` rieseguito il `08/04/2026` tramite pulsante dedicato `CT18 OK`
  - `traceId=4985640820b09596b123849b1ec5cb05`
  - `workflowInstanceId=2.16.840.1.113883.2.9.99.999.1.1.b5eb4a5fdbd67ac2506b34952bb0e02feaf8905c1dfe11270e110a6019c98b96.fde139a40a^^^^urn:ihe:iti:xdw:2013:workflowInstanceId`
  - `idtransfse=41`

Le precedenti associazioni provvisorie “in via ragionata” sono state superate da queste due esecuzioni dirette e tracciabili.
