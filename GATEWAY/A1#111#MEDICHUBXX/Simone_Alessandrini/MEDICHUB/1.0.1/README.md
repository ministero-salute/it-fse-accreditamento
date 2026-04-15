# MedicHub FSE 2.0 — Accreditamento V9.0.0

## Dati fornitore

| Campo | Valore |
|-------|-------|
| `appVendor` | `Simone Alessandrini` |
| `appID` | `MEDICHUB` |
| `appVersion` | `1.0.0` |
| CN certificato | `A1#111#MEDICHUBXX` |
| Path PR | `GATEWAY/A1_111_MEDICHUBXX/Simone_Alessandrini/MEDICHUB/1.0.0/` |

## Stato test

| Test | Operazione | Timestamp | TraceID | WFI | Stato |
|------|-----------|-----------|---------|-----|-------|
| V-01 | VERIFICA CDA valido | PENDING | PENDING | — | ⬜ rieseguire |
| V-02 | INVIA (VALIDATION+PUBLICATION) | 2026-04-02T15:36:14 | `07842e03...` | | OK |
| V-03 | INVIA duplicato (KO atteso) | 2026-04-02T14:23:10 | `510f07fd...` | | KO atteso |
| V-04 | VERIFICA sintattico KO | PENDING | PENDING | — | ⬜ rieseguire |
| V-05 | VERIFICA semantico KO | PENDING | PENDING | — | ⬜ rieseguire |
| D-01 | ELIMINA documento | 2026-04-02T15:28:55 | `6625080f...` | | OK |
| R-01 | SOSTITUISCI documento | 2026-04-02T16:42:57 | `520b3d89...` | | OK |
| U-01 | AGGIORNA METADATI | 2026-04-02T17:14:57 | `908f9b0d...` | | OK |

## Cosa fare prima della PR

1. **Rieseguire V-01, V-04, V-05** con il comando accreditamento (ora che `verificaReferto()` esiste):
 ```
 php artisan fse:accreditamento 3 --test=V-01 --medico=1
 php artisan fse:accreditamento 3 --test=V-04 --medico=1
 php artisan fse:accreditamento 3 --test=V-05 --medico=1
 ```
 Poi aggiornare `data.json` con i traceID ottenuti (in `fse_trasmissioni_steps.gateway_response->traceID`).

2. **Scaricare il report-checklist.xlsx** vero da:
 https://github.com/ministero-salute/it-fse-accreditamento/tree/main/Test%20Case
 
 Compilarlo con i dati della colonna ID del tab TestCases (gli ID numerici ufficiali di Sogei).
 Aggiornare i campi `id` in `data.json` con quelli corrispondenti.

3. **Copiare i PDF firmati PADES** usati per V-02 e R-01 in `FILES/SIGNED/`:
 - `v02-invia-documento.pdf` (il PDF con CDA embedded usato per la trasmissione #10)
 - `r01-sostituisci-documento.pdf` (il PDF usato per la trasmissione #14)
 
 I PDF temporanei erano in `storage/app/private/fse-temp/` ma vengono cancellati dopo l'invio.
 **Per recuperarli**: rieseguire le operazioni salvando il PDF prima dell'invio, oppure rigenerare
 lo stesso PDF dal preventivo (stesso contenuto, firma diversa ma CDA identico).

4. **Aprire la PR** su https://github.com/ministero-salute/it-fse-accreditamento
 con la cartella `GATEWAY/A1_111_MEDICHUBXX/...` come descritto nel README del repo.

## Struttura cartella

```
GATEWAY/A1_111_MEDICHUBXX/Simone_Alessandrini/MEDICHUB/1.0.0/
├── README.md ← questo file
├── data.json ← ⬜ aggiornare traceID V-01/V-04/V-05
├── report-checklist.xlsx ← ⬜ da compilare con xlsx ufficiale Sogei
└── FILES/
 ├── SIGNED/
 │ ├── v02-invia-documento.pdf ← ⬜ da inserire
 │ └── r01-sostituisci-documento.pdf ← ⬜ da inserire
 └── (altri PDF non firmati se necessari)
```
