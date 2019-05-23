# FRIKORT Endret Utbetaling

meldingsdefinisjon for utbetaling-endret meldinger for Frikort.

### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | 
offisiellId | String | Ja |
praksisId | String | Ja | (Frikort setter borgerId)
systemId | Number | Ja | 
forsystemRef| String | Ja | Skal denne være med?
oppdragstype| String | Ja | _**UTBETALING**_
tjenesteType| String | Ja | _**ENDRET**_
mottakergruppe| String | Ja | 
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