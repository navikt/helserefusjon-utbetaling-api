#Utbetaling-endret meldingsdefinisjon

Felles meldingsdefinisjon for utbetaling-endret meldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.
### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | 
offisiellId | String | Ja |
praksisId | String | Nei | Ikke lenger påkrevet
systemId | Number | Ja | 
forsystemRef| String | Ja | Skal denne være med?
oppdragstype| String | Ja | _**UTBETALING**_
tjenesteType| String | Ja | _**ENDRET**_
mottakergruppe| String | Ja | Trenger vi denne?
kontonummer | String | Nei
banknavn | String | Nei | Nytt felt
bankadresse | Adresse | Nei | Nytt felt
iban | String | Nei | Nytt felt
bban | String | Nei | Nytt felt
swift | String | Nei | Nytt felt
bankkode | String | Nei | Nytt felt
kidnummer | String | Nei |
bilagId | Number | Nei |
endretKontakt | Number | Ja |  Nytt felt
endretKid | Number | Ja |  Nytt felt

### Adresse - Ny struktur
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | Ny
poststed | String | Nei | Ny
landkode | String | Nei | Ny
adresselinje1 | String | Nei |Ny
adresselinje2 | String | Nei |Ny
adresselinje3 | String | Nei |Ny