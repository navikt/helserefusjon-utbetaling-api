# UtbetalingsKvittering

## Ressurser
### Kvittering
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
utbetalingsKvitteringId | Number | id på UtbetalingsKvittering, opprettes av helse-utbetaling
utbetalingsOppdragId | Number | id på UtbetalingsOppdrag kvittering gjelder for 
forsystemRef| String | forsystems referanse/id
systemId | Number | id på forsystem
oppdragstype| String| UTBETALING, ORDRE eller AVSTEMMING
betalingId | Number |
bilagId | Number | 
ordrenummer | Number |
valutasort| String | 
belop | Number | beløp i valutasort
belopNok | Number | beløp i NOK
status | String |
statusKode | Number |
statusDato | Date | 
feilmeldingTekst | String | 
feilmeldingKode | Number |
utbetalingDato | Date | 
innbetalingDato | Date |
mottattDato | Date |
behandletDato | Date | 

## Eksempel

```json
{
  "utbetalingsKvitteringId":21463,
  "utbetalingsOppdragId":1109,
  "forsystemRef":"U510000000016238",
  "systemId":14,
  "oppdragstype":"UTBETALING",
  "betalingId":477202,
  "status":"Godkjent for overføring",
  "statusKode":3901,
  "statusDato":"2018-11-08T13:03:23.000Z",
  "mottattDato":"2018-11-08T13:16:18.695Z"
}
```

