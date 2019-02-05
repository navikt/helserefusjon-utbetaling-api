# UtbetalingsOppdrag
_**(Hardkodede konstanter er markert med bold-kursiv)**_
## Ressurser
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
meldingId | String | GUID for hver melding
utbetalingsOppdragId | Number | id på UtbetalingsOppdrag, opprettes av helse-utbetaling 
forsystemRef| String | forsystems referanse/id
systemId | Number | id på forsystem, _**14**_, _**15**_ eller _**16**_
oppdragstype| String | _**UTBETALING**_, _**ENDRET_UTBETALING**_, _**ORDRE**_ eller _**AVSTEMMING**_
belop | Number | beløp i i valutasort, 0 for _**AVSTEMMING**_
valutasort| String | _**NOK**_, ikke satt for _**AVSTEMMING**_
data | String | krypterte og signerte data, eller json som skal krypteres og signeres
opprettetDato | Date | når ble oppdraget opprettet. Format er: ``yyyy-MM-ddTHH:mm:ss.SSSZ``. 
avstemtDato | Date | når ble oppdraget avstemt. Format er: ``yyyy-MM-ddTHH:mm:ss.SSSZ``. 


## Eksempel

```json
{
  "meldingId": "c61c646b-f87d-11e8-a217-ffa20916eaa5",
  "avstemtDato": "2018-11-12T13:15:20.321Z",
  "belop": 123.45,
  "data": "{\"offisiellId\":\"992316314\",\"praksisId\":\"1000047550\",\"mottakergruppe\":\"VIRKSOMHET\",\"navn\":\"Apoteket Trønk Test\",\"postnr\":\"0000\",\"landkode\":\"NO\",\"kontonummer\":\"61820537164\",\"oppdragstype\":\"UTBETALING\",\"tjenesteType\":\"NY\",\"systemId\":14,\"bilagsart\":\"TR\",\"forsystemRef\":\"U510000000016505\",\"forfallsdato\":\"2018-11-08\",\"belop\":80,\"valutasort\":\"NOK\",\"kidnummer\":\"01230000000000100000003\",\"konteringer\":[{\"linjenr\":0,\"artskonto\":\"872\",\"kapPost\":\"279070\",\"belop\":80,\"koststed\":\"2340\"}]}",
  "forsystemRef": "U510000000016505",
  "oppdragstype": "UTBETALING",
  "opprettetDato": "2018-11-11T13:14:21.123Z",
  "systemId": 14,
  "valutasort": "NOK"
}
```

