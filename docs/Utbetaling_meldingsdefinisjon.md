# Utbetaling meldingsdefinisjon

Felles meldingsdefinisjon for utbetbalingsmeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

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
mottakerNavn | String | Ja | 
mottakeradresse | Adresse | Nei | 
kontonummer | String | Nei | 
utenlandsbetaling | Number | Ja | 
banknavn | String | Nei | 
bankadresse | Adresse | Nei | 
iban | String | Nei |
bban | String | Nei | 
swift | String | Nei | 
bankkode | String | Nei | 
bilagsart | String | Ja | Fast verdi: TR 
forfallsdato | Date| Ja | 
belop | Number | Ja | 
kidnummer | String | Nei | 
eksternReferanse | String | Nei |
melding | String | Nei |
trekkpliktig | Number | Nei | Brukes av Kuhr
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

### Adresse 
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | 
poststed | String | Nei | 
landkode | String | Nei | 
adresselinje1 | String | Nei |
adresselinje2 | String | Nei |
adresselinje3 | String | Nei |
