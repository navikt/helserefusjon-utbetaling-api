# ERESEPT Endret Utbetaling

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |-------------------
meldingId | String | GUID for hver melding
offisiellId |String | orgnr fra SAR 
praksisId | String | samh_praksis_id fra SAR
systemId | Number | _**14**_ = ERESEPT
forsystemRef|String| _**U**_ + vedtak_id fra VEDTAK
oppdragstype|String| _**UTBETALING**_
tjenesteType|String| _**ENDRET**_
mottakergruppe|String| _**VIRKSOMHET**_
kontonummer | String | konto fra SAR
kidnummer | String | kid fra SAR
bilagId | Number | bilagId fra VEDTAK

## Eksempel

```
{
	"forsystemRef": "U540000000000841",
	"meldingId": "02b68596-f931-11e8-8b07-0b28d018fdf3",
	"systemId": 14,
	"offisiellId": "971033541",
	"oppdragstype": "ENDRET_UTBETALING",
	"mottakergruppe": "VIRKSOMHET",
	"tjenesteType": "ENDRET",
	"praksisId": "1000399230",
	"kontonummer": "60030688247",
	"kidnummer": "1234567890"
	"bilagId": 5099623
}
```

