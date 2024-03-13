# UtbetalingsKvittering

## Ressurser
### Kvittering

#### versjon 1

| Felt                    | Type   | Beskrivelse / Verdi                                                           |
|-------------------------|--------|-------------------------------------------------------------------------------|
| utbetalingsKvitteringId | Number | id på UtbetalingsKvittering, opprettes av helse-utbetaling                    |
| utbetalingsOppdragId    | Number | id på UtbetalingsOppdrag kvittering gjelder for                               | 
| forsystemRef            | String | forsystems referanse/id                                                       |
| systemId                | Number | id på forsystem                                                               |
| oppdragstype            | String | _**UTBETALING**_, _**ENDRET_UTBETALING**_, _**ORDRE**_ eller _**AVSTEMMING**_ |
| betalingId              | Number |                                                                               |
| bilagId                 | Number |                                                                               |
| ordrenummer             | Number |                                                                               |
| valutasort              | String |                                                                               |
| belop                   | Number | beløp i valutasort                                                            |
| belopNok                | Number | beløp i NOK                                                                   |
| status                  | String |                                                                               |
| statusKode              | Number |                                                                               |
| statusDato              | Date   |                                                                               |
| feilmeldingTekst        | String |                                                                               |
| feilmeldingKode         | Number |                                                                               |
| utbetalingDato          | Date   |                                                                               |
| innbetalingDato         | Date   |                                                                               |
| mottattDato             | Date   |                                                                               |
| behandletDato           | Date   |                                                                               |
| apiVersion              | Number | 1                                                                             |

#### mellomfase mellom versjon 1 og versjon 2

| Felt                    | Type   | Beskrivelse / Verdi                                                           |
|-------------------------|--------|-------------------------------------------------------------------------------|
| utbetalingsKvitteringId | Number | id på UtbetalingsKvittering, opprettes av helse-utbetaling                    |
| utbetalingsOppdragId    | Number | id på UtbetalingsOppdrag kvittering gjelder for                               | 
| forsystemRef            | String | forsystems referanse/id                                                       |
| systemId                | Number | id på forsystem                                                               |
| oppdragstype            | String | _**UTBETALING**_, _**ENDRET_UTBETALING**_, _**ORDRE**_ eller _**AVSTEMMING**_ |
| betalingId              | Number |                                                                               |
| bilagId                 | Number |                                                                               |
| ordrenummer             | Number |                                                                               |
| valutasort              | String |                                                                               |
| belop                   | Number | beløp i valutasort                                                            |
| belopNok                | Number | beløp i NOK                                                                   |
| status                  | String |                                                                               |
| statusKode              | Number |                                                                               |
| statusDato              | Date   |                                                                               |
| feilmeldingTekst        | String |                                                                               |
| feilmeldingKode         | Number |                                                                               |
| feilmeldingTekster      | String |                                                                               |
| feilmeldingKoder        | String | kan være flere koder, i så fall er de kommaseparert                           |
| utbetalingDato          | Date   |                                                                               |
| innbetalingDato         | Date   |                                                                               |
| mottattDato             | Date   |                                                                               |
| behandletDato           | Date   |                                                                               |
| apiVersion              | Number | 1 eller 2, avhengig av om feilmeldingKoder er med eller ikke                  |

#### versjon 2

| Felt                    | Type   | Beskrivelse / Verdi                                                           |
|-------------------------|--------|-------------------------------------------------------------------------------|
| utbetalingsKvitteringId | Number | id på UtbetalingsKvittering, opprettes av helse-utbetaling                    |
| utbetalingsOppdragId    | Number | id på UtbetalingsOppdrag kvittering gjelder for                               | 
| forsystemRef            | String | forsystems referanse/id                                                       |
| systemId                | Number | id på forsystem                                                               |
| oppdragstype            | String | _**UTBETALING**_, _**ENDRET_UTBETALING**_, _**ORDRE**_ eller _**AVSTEMMING**_ |
| betalingId              | Number |                                                                               |
| bilagId                 | Number |                                                                               |
| ordrenummer             | Number |                                                                               |
| valutasort              | String |                                                                               |
| belop                   | Number | beløp i valutasort                                                            |
| belopNok                | Number | beløp i NOK                                                                   |
| status                  | String |                                                                               |
| statusKode              | Number |                                                                               |
| statusDato              | Date   |                                                                               |
| feilmeldingTekster      | String |                                                                               |
| feilmeldingKoder        | String | kan være flere koder, i så fall er de kommaseparert                           |
| utbetalingDato          | Date   |                                                                               |
| innbetalingDato         | Date   |                                                                               |
| mottattDato             | Date   |                                                                               |
| behandletDato           | Date   |                                                                               |
| apiVersion              | Number | 2                                                                             |

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

