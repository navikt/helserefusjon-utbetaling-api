# Ordre meldingsdefinisjon

Felles meldingsdefinisjon for ordremeldinger. Skal innholde alle feltene som kan komme fra eresept og kuhr.

Beskrivelse av hvordan meldingen brukes av hvert system ligger i egen katalog for hvert system.

Felt | Type | Påkrevet | Beskrivelse 
-----|------|----------| --------------------
meldingId | String | Ja | GUID
offisiellId |String | Ja | 
systemId | Number | Ja | Id for hvert forsystem
forsystemRef | String | Ja | Unik id fra forsystemet
oppdragstype | String| Ja | Fast verdi: ORDRE
tjenesteType | String | Ja | Fast verdi: NY
mottakergruppe | String | Ja | Privatperson/Behandler/Virksomhet
valutasort | String | Ja | 
navnKontakt | String | Ja |
adresseKontakt | String | Ja | 
postnrKontakt | String | Nei |
poststedKontakt | String | Nei |
ordreType | String | Ja | FH/FR/FF
meldingFaktura | String | Ja
fakturaType | String | Ja | H-resept/Rabatt legemidler/Fritt behandlingsvalg
belop | Number | Ja |
egenReferanse | String | Ja | Kommer som "Vår referanse" på fakturaen
fakturaReferanse | String | Nei | Kommer som "Deres referanse" på fakturaen
betalingsfrist | Number | Ja | 
artikkellinjer | Array:Artikkellinje | Ja |

### Artikkellinje
Felt | Type | Påkrevet | Beskrivelse 
-----|------|----------| --------------------
linjenummer | Number | Ja | 
utleveringsdato | String | Ja |
artikkelnummer | String | Ja | Varenummer i h-resept
antallEnheter | Number | Ja | Tall med to desimaler, men uten desimalskilletegn (tall * 100)
belop | Number | Ja | 
artskonto | String | Ja |
kapittelpost | String | Ja | 
tekstlinje | Array:Tekstlinje | Nei | 

#### Tekstlinje
Felt | Type | Påkrevet | Beskrivelse
-----|------|----------| --------------------
tekstlinjenummer | Number | Ja | 
tekstlinjetekst | String | Ja | kolonnenavn;verdi
