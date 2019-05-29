# ERESEPT Utbetaling

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |-------------------
forsystemRef|String| _**U**_ + vedtak_id fra VEDTAK
meldingId | String | GUID for hver melding
systemId | Number | _**14**_ = ERESEPT
oppdragstype|String| _**UTBETALING**_
belop | Number | sum_utbetalt_bel fra VEDTAK
valutasort|String| **_NOK_**
mottakergruppe|String| _**VIRKSOMHET**_
tjenesteType|String| _**NY**_
offisiellId |String | orgnr fra SAR 
praksisId | String | samh_praksis_id fra SAR
kontonummer | String | konto fra SAR
kidnummer | String | kid fra SAR
mottakerNavn | String | navn fra UTLEVERER 
bilagsart | String | _**TR**_
forfallsdato | Date| Dagens dato eller 30 dager frem i tid for HRESEPT 
utenlandsbetaling | Number | 0 eller 1
konteringer | Array:Konteringslinje |

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | Artskonto fra UTBETALING
kapPost | String | KapittelPost fra UTBETALING
belop | Number | UtbetaltBelop fra UTBETALING
koststed | String | 
 


## Eksempel

```json
{
                "forsystemRef": "U510000000018377",
                "meldingId": "bf4d1c0e-7c6a-11e9-ac9d-8bb0bd9c0db2",
                "systemId": 14,
                "oppdragstype": "UTBETALING",
                "belop": 129.50,
                "valutasort": "NOK",
                "mottakergruppe": "VIRKSOMHET",
                "tjenesteType": "NY",
                "offisiellId": "915692443",
                "praksisId": "1000048212",
                "kontonummer": "60050609955",
                "kidnummer": "01881000000000100000001",
                "mottakerNavn": "Testapotek Apotek1 Østre Bydel",
                "bilagsart": "TR",
                "forfallsdato": "2019-05-21T22:00:00.000Z",
                "utenlandsbetaling": 0,
                "konteringer": [{
                               "linjenr": 0,
                               "artskonto": "872",
                               "kapPost": "275170",
                               "belop": 129.50,
                               "koststed": "2340"
                }]
}

```

