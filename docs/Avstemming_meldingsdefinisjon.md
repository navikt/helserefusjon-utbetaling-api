# Avstemming meldingsdefinisjon

Felles meldingsdefinisjon for avstemmingsmeldinger.

En avstemmingsmelding består av en array/liste av føgende ORDRE/UTBETALING som er endret siden sist en avstemming ble sendt. 

Felt | Type | Påkrevet | Beskrivelse 
-----|------|----------| --------------------
forsystemRef | String | Ja | Unik id fra forsystemet
betalingId | Number | Nei |
bilagId | Number | Nei |
ordrenummer | Number | Nei |
oppdragstype | String| Ja | ORDRE eller UTBETALING
systemId | Number | Ja | Id for hvert forsystem
valutasort | String | Ja | 
belop | Number | Ja |
belopNok | Number | Ja |
status | String | Ja |
statusKode | Number | Ja |
opprettetDato | Date | Ja |
sistEndret | Date | Ja |
utbetaltDato | Date | Nei | Kan være satt for UTBETALING 
innbetaltDato | Date | Nei | Kan være satt for ORDRE 
 
## Eksempel

```json
{
  "forsystemRef":"U510000000016238",
  "systemId":14,
  "oppdragstype":"UTBETALING",
  "betalingId":477202,
  "status":"Godkjent for overføring",
  "statusKode":3901,
  "opprettetDato":"2018-11-08T13:03:23.000Z",
  "sistEndret":"2018-11-08T13:16:18.695Z",
  "belop": 123.45,
  "belopNok": 123.45,
  "valutasort": "NOK"
}
```