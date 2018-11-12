# UtbetalingsOppdrag

## Ressurser
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
utbetalingsOppdragId | Number | id på UtbetalingsOppdrag, opprettes av helse-utbetaling 
forsystemRef| String | forsystems referanse/id
systemId | Number | id på forsystem
oppdragstype| String | UTBETALING, ORDRE eller AVSTEMMING
offisiellId | String | organisasjonsnummer eller fødslesnummer
belop | Number | beløp i i valutasort
valutasort| String |
data | String | krypterte og signerte data, eller json som skal krypteres og signeres
opprettetDato | Date | når ble oppdraget opprettet
avstemtDato | Date | når ble oppdraget avstemt


## Eksempel

```json
{
  "avstemtDato": "2018-11-12T13:15:20.321Z",
  "belop": 123.45,
  "data": "{\"offisiellId\":\"992316314\",\"praksisId\":\"1000047550\",\"mottakergruppe\":\"VIRKSOMHET\",\"navn\":\"Apoteket Trønk Test\",\"postnr\":\"0000\",\"landkode\":\"NO\",\"kontonummer\":\"61820537164\",\"oppdragstype\":\"UTBETALING\",\"tjenesteType\":\"NY\",\"systemId\":14,\"bilagsart\":\"TR\",\"forsystemRef\":\"U510000000016505\",\"forfallsdato\":\"2018-11-08\",\"belop\":80,\"valutasort\":\"NOK\",\"kidnummer\":\"01230000000000100000003\",\"konteringer\":[{\"linjenr\":0,\"artskonto\":\"872\",\"kapPost\":\"279070\",\"belop\":80,\"koststed\":\"2340\"}]}",
  "forsystemRef": "U510000000016505",
  "offisiellId": "992316314",
  "oppdragstype": "UTBETALING",
  "opprettetDato": "2018-11-11T13:14:21.123Z",
  "systemId": 14,
  "valutasort": "NOK"
}
```

