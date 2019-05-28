# Utbetaling-endret meldingsdefinisjon

Felles meldingsdefinisjon for utbetaling-endret meldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.
### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | 
offisiellId |String | Ja |
praksisId | String | Ja | (Frikort setter borgerId)
systemId | Number | Ja |
forsystemRef|String| Ja |
oppdragstype|String| Ja |  Fast verdi: UTBETALING
tjenesteType|String| Ja | Fast verdi: ENDRET
mottakergruppe|String| Ja |
kontonummer | String | Nei
banknavn | String | Nei | 
bankadresse | Adresse | Nei | 
iban | String | Nei | 
bban | String | Nei | 
swift | String | Nei | 
bankkode | String | Nei | 
kidnummer | String | Nei |
bilagId | Number | Nei |
endretKontakt | Number | Ja |  
endretKid | Number | Ja |  

### Adresse
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | 
poststed | String | Nei | 
landkode | String | Nei | 
adresselinje1 | String | Nei |
adresselinje2 | String | Nei |
adresselinje3 | String | Nei |