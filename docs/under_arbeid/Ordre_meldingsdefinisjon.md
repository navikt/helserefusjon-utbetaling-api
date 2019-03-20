#Ordre meldingsdefinisjon

Felles meldingsdefinisjon for ubetbalingsmeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.

Felt | Type | Påkrevet | Beskrivelse 
-----|------|----------| --------------------
meldingId | String | Ja |
offisiellId |String | Ja |
systemId | Number | Ja |
forsystemRef | String | Ja |
oppdragstype | String| Ja | 
tjenesteType | String | Ja |
mottakergruppe | String | Ja |
valutasort | String | Ja | 
~~navnKontakt~~ | ~~String~~ | ~~Ja~~ | Utgått
~~adresseKontakt~~ | ~~String~~ | ~~Ja~~ | Utgått
~~postnrKontakt~~ | ~~String~~ | ~~Nei~~ | Utgått
~~poststedKontakt~~ | ~~String~~ | ~~Nei~~ | Utgått
mottakernavn | String | Ja | Nytt felt, erstatter navnKontakt
mottakeradresse | Adresse | Ja | Ny struktur
ordreType | String | Ja | 
meldingFaktura | String | Ja |
fakturaType | String | Ja | 
belop | Number | Ja |
egenReferanse | String | Ja | 
fakturaReferanse | String | Nei |
betalingsfrist | Number | Ja | 
artikkellinjer | Array:Artikkellinje | Ja |

### Artikkellinje
Felt | Type | Påkrevet | Beskrivelse 
-----|------|----------| --------------------
linjenummer | Number | Ja | 
utleveringsdato | String | Ja |
artikkelnummer | String | Ja | 
antallEnheter | Number | Ja |
belop | Number | Ja | 
artskonto | String | Ja |
kapittelpost | String | Ja | 
tekstlinje | Array:Tekstlinje | Nei | 

#### Tekstlinje
Felt | Type | Påkrevet | Beskrivelse
-----|------|----------| --------------------
tekstlinjenummer | Number | Ja | 
tekstlinjetekst | String | Ja | 

### Adresse - Ny struktur
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
adresselinje1 | String | Ja |
adresselinje2 | String | Nei |
adresselinje3 | String | Nei |
landkode | String | Ja | 
postnr | String | Nei | Ikke lenger påkrevet
poststed | String | Nei | 
