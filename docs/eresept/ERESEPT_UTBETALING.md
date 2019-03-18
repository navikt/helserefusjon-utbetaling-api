# ERESEPT Utbetaling

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
tjenesteType|String| _**NY**_
mottakergruppe|String| _**VIRKSOMHET**_
valutasort|String| **_NOK_**
navn | String | navn fra UTLEVERER 
postnr | String| _**0000**_
landkode | String | _**NO**_
kontonummer | String | konto fra SAR
bilagsart | String | _**TR**_
forfallsdato | Date| Dagens dato eller 30 dager frem i tid for HRESEPT 
belop | Number | sum_utbetalt_bel fra VEDTAK
kidnummer | String | kid fra SAR
konteringer | Array:Konteringslinje |

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | Artskonto fra UTBETALING
kapPost | String | KapittelPost fra UTBETALING
belop | Number | UtbetaltBelop fra UTBETALING
 


## Eksempel

```json
{
	"forsystemRef": "U510000000016844",
	"meldingId": "c61c646b-f87d-11e8-a217-ffa20916eaa5",
	"systemId": 14,
	"offisiellId": "973151401",
	"oppdragstype": "UTBETALING",
	"belop": 80.00,
	"valutasort": "NOK",
	"mottakergruppe": "VIRKSOMHET",
	"tjenesteType": "NY",
	"praksisId": "1000472046",
	"kontonummer": "15031769342",
	"navn": "Test 5.21 RC3",
	"postnr": "0000",
	"bilagsart": "TR",
	"forfallsdato": "2018-12-04",
	"landkode": "NO",
	"konteringer": [{
			"linjenr": 1,
			"artskonto": "872",
			"kapPost": "275170",
			"belop": 48.80
		}, {
			"linjenr": 0,
			"artskonto": "872",
			"kapPost": "275270",
			"belop": 31.20
		}
	]
}
```

