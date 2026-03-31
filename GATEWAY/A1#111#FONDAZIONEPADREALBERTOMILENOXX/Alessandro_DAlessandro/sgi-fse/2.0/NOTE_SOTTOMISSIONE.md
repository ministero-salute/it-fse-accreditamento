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

## Assunzioni fatte

- `450` associato alla validazione OK con `traceId=f9ab0f1c73487e305636d0b375500192`
- `451` associato alla validazione OK con `traceId=0db52134a1ced008c56e8eb7fa232362`

Questa associazione e' coerente con il lavoro fatto in progetto, ma va tenuta sotto controllo fino alla sottomissione finale.
