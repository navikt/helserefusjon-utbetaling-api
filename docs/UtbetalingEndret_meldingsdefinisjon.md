#Utbetaling-endret meldingsdefinisjon

Felles meldingsdefinisjon for utbetaling-endret meldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.
### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | 
offisiellId |String | 
praksisId | String | 
systemId | Number | 
forsystemRef|String| 
oppdragstype|String| Ja |  Fast verdi: UTBETALING
tjenesteType|String| Ja | Fast verdi: ENDRET
mottakergruppe|String| Ja |
kontonummer | String | Nei
kidnummer | String | Nei |
bilagId | Number | Nei |
