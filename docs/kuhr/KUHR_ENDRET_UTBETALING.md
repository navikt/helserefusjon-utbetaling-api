# KUHR Endret Utbetaling

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |-------------------
meldingId | String | GUID for hver melding
offisiellId |String | HPR-nummeret hvis samhandleren har ett, ellers behandler_identifikasjon fra ODB_VEDTAK 
praksisId | String | samh_praksis_id fra SAR
systemId | Number | _**15**_ = KUHR
forsystemRef|String| _**U**_ / _**MU**_ + vedtak_id fra ODB_VEDTAK / ODB_MAN_REG_VEDTAK
oppdragstype|String| _**ENDRET_UTBETALING**_
tjenesteType|String| _**endret**_
mottakergruppe|String| _**Virksomhet**_ eller _**Behandler**_
kontonummer | String | konto fra SAR
endretKontakt | Number | 0 eller 1 flagg for om kontakt/kontonummer er endret
kidnummer | String | KID fra SAMH_PRAKSIS_KONTO, for samleregning brukes KID fra innsendingen hvis det finnes, ellers fra samh.
endretKid | Number | 0 eller 1 flagg for om kidnummer er endret
bilagId | Number | bilagId hentet fra kvittering fra DFØ

## Eksempel

```
{
  "meldingId": "3905d5e0-c2f6-4bd6-8479-1e89053eb661",
  "forsystemRef": "U100001775176949",
  "systemId": 15,
  "bilagId": 5100305,
  "mottakergruppe": "Virksomhet",
  "offisiellId": "973850679",
  "praksisId": "1000404978",
  "kontonummer": "31230840205",
  "endretKontakt": 0,
  "kidnummer": "05192861623148",
  "endretKid": 1,
  "oppdragstype": "ENDRET_UTBETALING",
  "tjenesteType": "endret"
}
```

