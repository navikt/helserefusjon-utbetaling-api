# Utbetaling meldingsdefinisjon

Felles meldingsdefinisjon for ubetbalingsmeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.

### Utbetaling
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
offisiellId |String | Ja | 
praksisId | String | Ja | (Frikort setter borgerId)
systemId | Number | Ja| 
forsystemRef|String| Ja | 
oppdragstype|String| Ja | 
tjenesteType|String| Ja | 
mottakergruppe|String| Ja | 
valutasort|String| Ja | 
meldingId | String | Ja |  
~~navnKontakt~~ | ~~String~~ | ~~Ja~~ | Utgått
~~adresseKontakt~~ | ~~String~~ | ~~Ja~~ | Utgått
~~postnrKontakt~~ | ~~String~~ | ~~Nei~~ | Utgått
~~poststedKontakt~~ | ~~String~~ | ~~Nei~~ | Utgått
mottakerNavn | String | Ja | Nytt felt, erstatter navnKontakt
mottakeradresse | Adresse | Nei | Ny struktur
kontonummer | String | Nei | Ikke lenger påkrevet
utenlandsbetaling | Number | Ja | Nytt felt
banknavn | String | Nei | Nytt felt
bankadresse | Adresse | Nei | Nytt felt
iban | String | Nei | Nytt felt
bban | String | Nei | Nytt felt
swift | String | Nei | Nytt felt
bankkode | String | Nei | Nytt felt
~~betalingsartkode~~ | ~~String~~ | ~~Nei~~ | Utgår
bilagsart | String | Ja | 
forfallsdato | Date| Ja | 
belop | Number | Ja | 
kidnummer | String | Nei | 
eksternReferanse | String| Nei |
melding | String | Nei |
trekkpliktig | Number | Nei | Nytt felt. Brukes av Kuhr
konteringer | Array:Konteringslinje | Ja | 

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


### Adresse - Ny struktur
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | Ikke lenger påkrevet
poststed | String | Nei | 
landkode | String | Nei | Ikke lenger påkrevet
adresselinje1 | String | Nei |
adresselinje2 | String | Nei |
adresselinje3 | String | Nei |
