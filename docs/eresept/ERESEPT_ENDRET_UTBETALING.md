# ERESEPT Endret Utbetaling

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |-------------------
forsystemRef|String| _**U**_ + vedtak_id fra VEDTAK
meldingId | String | GUID for hver melding
systemId | Number | _**14**_ = ERESEPT
oppdragstype|String| _**UTBETALING**_
mottakergruppe|String| _**VIRKSOMHET**_
tjenesteType|String| _**ENDRET**_
offisiellId |String | orgnr fra SAR 
praksisId | String | samh_praksis_id fra SAR
kontonummer | String | konto fra SAR
kidnummer | String | kid fra SAR
bilagId | Number | bilagId fra VEDTAK
endretKid | Number | 0 eller 1
endretKontakt | Numver | 0 eller 1 

## Eksempel

```
{
    "forsystemRef": "U510000000018400",
    "meldingId": "997ec5f5-804d-11e9-898a-697e14200691",
    "systemId": 14,
    "oppdragstype": "ENDRET_UTBETALING",
    "mottakergruppe": "VIRKSOMHET",
    "tjenesteType": "ENDRET",
    "offisiellId": "973590413",
    "praksisId": "1000107700",
    "kontonummer": "60050609955",
    "kidnummer": "100000000111"
    "bilagId": 1527066,
    "endretKid": 1,
    "endretKontakt": 0
}

```

