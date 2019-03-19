#Utbetaling meldingsdefinisjon

Felles meldingsdefinisjon for ubetbalingsmeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.

### Utbetaling
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
offisiellId |String | Ja | Orgnr/hpr-nummer 
praksisId | String | Ja | 
systemId | Number | Ja | Id for hvert forsystem
forsystemRef|String| Ja | Unik id fra forsystemet
oppdragstype|String| Ja | Fast verdi: UTBETALING
tjenesteType|String| Ja | Fast verdi: NY
mottakergruppe|String| Ja | Privatperson/behandler/virksomhet
valutasort|String| Ja | 
meldingId | String | Ja | GUID 
navn | String | Ja | 
postnr | String| Ja | 
landkode | String | Ja |
kontonummer | String | Ja | 
bilagsart | String | Ja | Fast verdi: TR 
forfallsdato | Date| Ja | 
belop | Number | Ja | 
kidnummer | String | Nei | 
eksternReferanse | String | Nei |
melding | String | Nei |
konteringer | Array:Konteringslinje |

### Konteringslinje
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
linjenr | Number | Ja |
artskonto | String | Ja |
kapPost | String | Ja |
belop | Number | Ja |
fraDato | Date | Nei |
tilDato | Date | Nei |
koststed | String | Nei | 
