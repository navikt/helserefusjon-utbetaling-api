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
linjenr |Number | Starter på 1
belop | Number | 
fraDato | Date |
tilDato | Date |
artskonto | String| |
kapPost | String|
koststed | String  | **_2340_**
 


## Eksempel

```json
{
  "meldingId": "17406bf7-5e7e-42ea-8b11-dce99aa88f71",
  "systemId": 15,
  "mottakergruppe": "Virksomhet",
  "forsystemRef": "U100001775179825",
  "offisiellId": "964966109",
  "praksisId": "1001428150",
  "navn": "Evje Og Hornnes Kommune",
  "postnr": "0000",
  "landkode": "NO",
  "kontonummer": "17301883730",
  "eksternReferanse": "Fastlønnet",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "ny",
  "bilagsart": "TR",
  "valutasort": "NOK",
  "belop": 63.0,
  "forfallsdato": "2019-01-22",
  "melding": "Fastlønnet refusjon fra Helfo",
  "konteringer": [
    {
      "linjenummer": 1,
      "belop": 63.0,
      "artskonto": "870",
      "kapPost": "275570",
      "koststed": "2340",
      "fraDato": "2019-01-01",
      "tilDato": "2019-01-31"
    }
  ]
}

```

