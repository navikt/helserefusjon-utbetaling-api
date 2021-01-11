# Covid-19 vaksinering fakturamelding

## Ressurser
**_(Hardkodede konstanter er markert med bold-kursiv)_**
### Faktura
Felt | Type | Beskrivelse / Verdi | Avklart
-----|------ |------------|-----
meldingId | String | GUID for hver melding, brukes for � oppdage duplikater og spore en melding gjennom en kjede av systemer.
offisiellId |String | Orgnr. fra ODB_KOMMUNE_FAKTURERING 
systemId | Number | _**15**_ = KUHR
forsystemRef|String| FAKTURA_C_VAKSINE_ID fra ODB_FAKTURA_C_VAKSINE
oppdragstype|String| **_ORDRE_**
tjenesteType|String| _**ny**_
mottakergruppe|String| **_Virksomhet_**
valutasort|String| **_NOK_**
egenReferanse|String| FAKTURA_C_VAKSINE_ID fra ODB_FAKTURA_C_VAKSINE
fakturaReferanse|String| deres_referanse fra ODB_KOMMUNE_FAKTURERING
fakturaType|String| **_Covid19-vaksinering_**
meldingFaktura|String| **_Refusjon for covid19-vaksinering hos fastlege. Periode <dato fra>-<dato og �r til>._**
ordreType|String| FV | 
mottakerNavn|String| Navn fra ODB_KOMMUNE_FAKTURERING
mottakerAdresse| Mottakeradresse |
belop|Number| Sum av bel�pet p� takster som inng�r i fakturaen 
betalingsfrist|Number| _**20**_ | ?
artikkellinjer|Array:Artikkellinje|

### Mottakeradresse
Felt | Type | Beskrivelse
-----|------ |------------
adresselinje1|String| Adresse fra ODB_KOMMUNE_FAKTURERING
postnr|String| Postnr fra ODB_KOMMUNE_FAKTURERING
poststed|String| Poststed fra ODB_POSTSTED
landkode|String| **_NO_**


### Artikkellinje 
Det lages 1 artikkellinje per lege i en praksis som har vaksinert pasienter fra kommunen den m�neden. 

Felt | Type | Beskrivelse | Avklart
-----|------ |------------|------
linjenummer|Number|
belop|Number| Sum av bel�pet p� takstene for legen i praksisen
artskonto|String| | Trenger verdi
kapittelPost|String| | Trenger verdi
utleveringsdato|Date| | Sette til den f�rste i m�neden?
artikkelnummer|String| | Er hardkodet FBV for FBV
antallEnheter|Number| | Er hardkodet 100 for FBV
tekstlinje|Array:Tekstlinje| En linje per ekstra felt som skal med| 
     
### Tekstlinje 
Felt | Type | Beskrivelse
-----|------ |------------
tekstlinjenummer|Number|      
tekstlinjetekst|String|

#### Tekstlinjeverdier
tekstlinjenummer|tekstlinjetekst-prefix| Format | Beskrivelse
-----|------|---------|------------------
1|Orgnr| | Legens org.nr. hentet fra avsender_orgnr. Kan v�re blank.
2|HPRnr| | Legens HPRnr
3|Legensnavn| | Fornavn og etternavn
4|Legekontor| |  avsender_cn
5|Utbetalt refusjon| | 
6|Antall takst 61a | | 
7|Refusjon takst 61a| | 
8|Antall takst 61b| | 
9|Refusjon takst 61b| | 
10|Antall takst 62| 
11|Refusjon takst 62| | 
12|Antall takst 63| |
13|Refusjon takst 63| |  


## Eksempel

```json

```

