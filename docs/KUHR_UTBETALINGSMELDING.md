# KUHR Utbetalingsmelding

## Ressurser
**_(Hardkodede konstanter er markert med bold-kursiv)_**
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
meldingId | String | GUID for hver melding, brukes for å oppdage duplikater og spore en melding gjennom en kjede av systemer.
offisiellId |String | HPR-nummeret hvis samhandleren har ett, ellers behandler_identifikasjon fra ODB_VEDTAK 
praksisId | String | samh_praksis_id fra SAR
systemId | Number | _**15**_ = KUHR
forsystemRef|String| _**U**_ / _**MU**_ + vedtak_id fra ODB_VEDTAK / ODB_MAN_REG_VEDTAK
oppdragstype|String| **_utbetaling_**
tjenesteType|String| _**ny**_ _**endret**_ _**stoppet**_
mottakergruppe|String| **_Behandler_** **_Virksomhet_**
valutasort|String| **_NOK_**
navn | String | behandler_navn fra ODB_VEDTAK 
postnr | String| **_0000_** 
landkode | String | **_NO_**
kontonummer | String | konto fra SAMH_PRAKSIS_KONTO
bilagsart | String | **_TR_**
forfallsdato | Date| Settes til dagens dato for å kunne utbetale "så fort som mulig" 
belop | Number | sum_utbetalt_bel fra ODB_VEDTAK
kidnummer | String | KID fra SAMH_PRAKSIS_KONTO, for samleregning brukes KID fra innsendingen hvis det finnes, ellers fra samh. 
eksternReferanse | String| Praksisnavn hvis det finnes, ellers praksistype
melding | String | Teksten praksistype + " refusjon fra Helfo"
konteringer | Array:Konteringslinje |

### Konteringslinje
Hentes fra tabellene odb_vedtak_utbetalt_dfoe og odb_man_reg_vedtak_utbet_dfoe.

Felt | Type | Beskrivelse / Verdi
-----|------ |------------
linjenr |Number | Starter på 0
belop | Number | 
fraDato | Date |
tilDato | Date |
artskonto | String| |
kapPost | String|
koststed | String  | **_2340_**
 


## Eksempel

```json
{
  "meldingId": "11aac730-ca0f-4ca6-b54b-08c98ba93d5d",
  "systemId": 15,
  "mottakergruppe": "Virksomhet",
  "forsystemRef": "U100001775600523",
  "offisiellId": "964963738",
  "praksisId": "1000042996",
  "navn": "Seljord Kommune",
  "postnr": "0000",
  "landkode": "NO",
  "kontonummer": "27110710777",
  "eksternReferanse": "Seljord helsesenter",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "ny",
  "bilagsart": "TR",
  "valutasort": "NOK",
  "belop": 1298.0,
  "forfallsdato": "2019-01-25",
  "melding": "Fastlønnet refusjon fra Helfo",
  "konteringer": [
    {
      "linjenr": 0,
      "belop": 38.0,
      "artskonto": "870",
      "kapPost": "275171",
      "koststed": "2340",
      "fraDato": "2019-01-01",
      "tilDato": "2019-01-31"
    },
    {
      "linjenr": 1,
      "belop": 116.0,
      "artskonto": "870",
      "kapPost": "275171",
      "koststed": "2340",
      "fraDato": "2018-12-01",
      "tilDato": "2018-12-31"
    },
    {
      "linjenr": 2,
      "belop": 833.0,
      "artskonto": "870",
      "kapPost": "275570",
      "koststed": "2340",
      "fraDato": "2019-01-01",
      "tilDato": "2019-01-31"
    },
    {
      "linjenr": 3,
      "belop": 311.0,
      "artskonto": "870",
      "kapPost": "275570",
      "koststed": "2340",
      "fraDato": "2018-12-01",
      "tilDato": "2018-12-31"
    }
  ]
}


```

