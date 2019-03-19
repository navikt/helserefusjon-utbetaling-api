#Utbetaling-endret meldingsdefinisjon

Felles meldingsdefinisjon for utbetaling-endret meldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.
### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | GUID
offisiellId |String | 
praksisId | String | 
systemId | Number | 
forsystemRef|String| 
oppdragstype|String| Ja | _**UTBETALING**_
tjenesteType|String| Ja | _**ENDRET**_
mottakergruppe|String| Ja |
kontonummer | String | Nei
kidnummer | String | Nei |
bilagId | Number | Nei |
endretKontakt | Number | Ja |  Nytt felt
endretKid | Number | Ja |  Nytt felt