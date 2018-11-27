# KUHR Utbetalingsmelding

## Ressurser
**_(Hardkodede konstanter er markert med bold-kursiv)_**
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
meldingId | String | GUID for hver melding, brukes for å oppdage duplikater og spore en melding gjennom en kjede av systemer.
offisiellId |String | behandler_identifikasjon fra ODB_VEDTAK 
praksisId | String | samh_praksis_id fra SAR
systemId | Number | _**15**_ = KUHR
forsystemRef|String| vedtak_id fra ODB_VEDTAK
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
kidnummer | String | kid fra SAMH_PRAKSIS_KONTO, spesial greie for samleregning
eksternReferanse | String| brukes på samleregning
melding | String | Teksten praksistype + " refusjon fra Helfo"
konteringer | Array:Konteringslinje |

### Konteringslinje
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

```

