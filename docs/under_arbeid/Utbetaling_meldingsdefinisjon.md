#Utbetaling meldingsdefinisjon

Felles meldingsdefinisjon for ubetbalingsmeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.

### Utbetaling
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
offisiellId |String | Ja | 
praksisId | String | Ja | 
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
mottakeradresse | Array:Mottakeradresse | Nei | Ny struktur
kontonummer | String | Ja | 
utenlandsbetaling | Number | Ja | Nytt felt
banknavn | String | Nei | Nytt felt
bankadresse | Array:Bankadresse | Nei | Nytt felt
iban | String | Nei | Nytt felt
bban | String | Nei | Nytt felt
swift | String | Nei | Nytt felt
bankkode | String | Nei | Nytt felt
betalingsartkode | String | Nei | Nytt felt
bilagsart | String | Ja | 
forfallsdato | Date| Ja | 
belop | Number | Ja | 
kidnummer | String | Nei | 
eksternReferanse | String| Nei |
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


### Mottakeradresse - Ny struktur
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | Ikke lenger påkrevet
poststed | String | Nei | 
landkode | String | Nei | Ikke lenger påkrevet
adresselinje1 | String | Nei |
adresselinje2 | String | Nei |
adresselinje3 | String | Nei |

### Bankadresse - Ny struktur
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
postnr | String | Nei | Nytt felt
poststed | String | Nei | Nytt felt
landkode | String | Nei | Nytt felt
adresselinje1 | String | Nei | Nytt felt
adresselinje2 | String | Nei | Nytt felt
adresselinje3 | String | Nei | Nytt felt

