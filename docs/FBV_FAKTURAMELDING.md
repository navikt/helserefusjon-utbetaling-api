# FBV Fakturamelding

## Ressurser
**_(Hardkodede konstanter er markert med bold-kursiv)_**
### Faktura
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
offisiellId |String | Helseforetak orgnr. fra ODB_HELSEFORETAK 
systemId | Number | _**15**_ = KUHR
forsystemRef|String| faktura_id fra ODB_FAKTURA
oppdragstype|String| **_ordre_**
tjenesteType|String| _**ny**_
mottakergruppe|String| **_Virksomhet_**
valutasort|String| **_NOK_**
egenReferanse|String| referanse fra ODB_FAKTURA
fakturaType|String| **_Fritt behandlingsvalg_**
meldingFaktura|String| **_Refusjon for oppgjør til behandlingsvalgleverandør (FBV). Periode <dato fra>-<dato og år til>._**
ordreType|String| **_FF_**
navnKontakt|String| Helseforetak-navn fra ODB_HELSEFORETAK
adresseKontakt|String| Helseforetak-adresse fra ODB_HELSEFORETAK
postnrKontakt|String| Helseforetak-postnr fra ODB_HELSEFORETAK
poststedKontakt|String| Helseforetak-poststed fra ODB_POSTSTED
landkode|String| **_NO_**
belop|Number| Sum av beløpet på takster som inngår i fakturaen, unntatt takst 201b 
betalingsfrist|Number| _**20**_
artikkellinjer|Array:Artikkellinje|

### Artikkellinje 
Felt | Type | Beskrivelse
-----|------ |------------
linjenummer|Number|
belop|Number| Sum av beløpet på takstene for regningen, unntatt takst 201b
artskonto|String| _**827**_
kapittelPost|String| _**372030**_
utleveringsdato|Date| datotid fra ODB_ENKELTREGNING, omgjort til den første i måneden
artikkelnummer|String| **_FBV_**
antallEnheter|Number| **_100_**
tekstlinje|Array:Tekstlinje| 
     
### Tekstlinje 
Felt | Type | Beskrivelse
-----|------ |------------
tekstlinjenummer|Number|      
tekstlinjetekst|String|

#### Tekstlinjeverdier
tekstlinjenummer|tekstlinjetekst-prefix| Format | Beskrivelse
-----|------|---------|------------------
1|Orgnr| | Orgnr. for samhandleren/behandleren
2|Leverandørnavn| | Navn for samhandleren/behandleren
3|Beh.mnd|MM.yyyy| datotid fra ODB_ENKELTREGNING omgjort til måned-år
4|RESH-kode| | RESH-koden for samhandleren/behandleren
5|Avdelingsnavn| | Praksisnavnet for samhandleren/behandleren
6|Pas.id| | Pseudoid for pasienten. Hentes fra ODB_PASIENT_PSEUDOID
7|Komnr| | tknr fra ODB_ENKELTREGNING
8|RegningsId| | enkeltregning_id fra ODB_ENKELTREGNING
9|Vedtaksdato| dd.MM.yyyy
10|Funksjon| | Funksjonsgruppe for takstene på regningen
11|Status| | Status på regningen


## Eksempel

```json
{
    "offisiellId": "983975259",
    "systemId": 15,
    "forsystemRef": "100001139692294",
    "oppdragstype": "ordre",
    "tjenesteType": "ny",
    "mottakergruppe": "Virksomhet",
    "valutasort": "NOK",
    "egenReferanse": "FBV-SIV-2017-11-2-55",
    "fakturaType": "Fritt behandlingsvalg",
    "meldingFaktura": "Refusjon for oppgjør til behandlingsvalgleverandør (FBV). Periode 01.11-01.11.2017.",
    "ordreType": "FF",
    "navnKontakt": "Sykehuset i Vestfold HF",
    "adresseKontakt": "Postboks 2168",
    "postnrKontakt": "3103",
    "poststedKontakt": "TØNSBERG",
    "landkode": "NO",
    "belop": 1600,
    "betalingsfrist": 20,
    "artikkellinjer": [
        {
            "linjenummer": 1,
            "belop": 1600,
            "artskonto": "827",
            "kapittelPost": "372030",
            "utleveringsdato": "2016-04-01",
            "artikkelnummer": "FBV",
            "antallEnheter": 1,
            "tekstlinje": [
                {
                    "tekstlinjenummer": 1,
                    "tekstlinjetekst": "Orgnr;915378404"
                },
                {
                    "tekstlinjenummer": 2,
                    "tekstlinjetekst": "Leverandørnavn;KALBAKKENKLINIKKEN AS"
                },
                {
                    "tekstlinjenummer": 3,
                    "tekstlinjetekst": "Beh.mnd;04.2017"
                },
                {
                    "tekstlinjenummer": 4,
                    "tekstlinjetekst": "RESH-kode;4211435"
                },
                {
                    "tekstlinjenummer": 5,
                    "tekstlinjetekst": "Avdelingsnavn;Kalbakkenklinikken"
                },
                {
                    "tekstlinjenummer": 6,
                    "tekstlinjetekst": "Pas.id;1014433213"
                },
                {
                    "tekstlinjenummer": 7,
                    "tekstlinjetekst": "Komnr;0709"
                },
                {
                    "tekstlinjenummer": 8,
                    "tekstlinjetekst": "RegningsId;100001568690030"
                },
                {
                    "tekstlinjenummer": 9,
                    "tekstlinjetekst": "Vedtaksdato;09.12.2017"
                },
                {
                    "tekstlinjenummer": 10,
                    "tekstlinjetekst": "Funksjon;620"
                },
                {
                    "tekstlinjenummer": 11,
                    "tekstlinjetekst": "Status;Godkjent"
                }
            ]
        }
    ]
 }
```

