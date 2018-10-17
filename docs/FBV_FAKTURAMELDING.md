# Fakturamelding

## Ressurser

### Faktura
Felt | Type | Beskrivelse
-----|------ |------------
offisiellId|String|
systemId|Number| 
forsystemRef|String|
oppdragstype|String|
tjenesteType|String|
mottakergruppe|String|
valutasort|String|
egenReferanse|String|
fakturaType|String|
meldingFaktura|String|
ordreType|String|
navnKontakt|String|
adresseKontakt|String|
postnrKontakt|String|
poststedKontakt|String|
landkode|String|
belop|Number|
betalingsfrist|Number|
artikkellinjer|Array:Artikkellinje|

### Artikkellinje 
Felt | Type | Beskrivelse
-----|------ |------------
linjenummer|Number|
belop|Number|
artskonto|String|
kapittelPost|String|
utleveringsdato|Date|
artikkelnummer|String|
antallEnheter|Number|
tekstlinje|Array:Tekstlinje| 
     
### Tekstlinje 
Felt | Type | Beskrivelse
-----|------ |------------
tekstlinjenummer|Number|      
tekstlinjetekst|String|

#### Tekstlinjeverdier
tekstlinjenummer|tekstlinjetekst-prefix| Format | Beskrivelse
-----|------|---------|------------------
1|Orgnr
2|Leverandørnavn
3|Beh.mnd|MM.yyyy
4|RESH-kode
5|Avdelingsnavn
6|Pas.id
7|Komnr
8|RegningsId
9|Vedtaksdato| dd.MM.yyyy
10|Funksjon
11|Status


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

