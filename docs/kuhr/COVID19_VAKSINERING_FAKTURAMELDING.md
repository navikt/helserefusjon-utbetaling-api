# Covid-19 vaksinering fakturamelding

## Ressurser
**_(Hardkodede konstanter er markert med bold-kursiv)_**
### Faktura
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
meldingId | String | GUID for hver melding, brukes for å oppdage duplikater og spore en melding gjennom en kjede av systemer.
offisiellId |String | Orgnr. fra ODB_KOMMUNE_FAKTURERING 
systemId | Number | _**15**_ = KUHR
forsystemRef|String| FAKTURA_C_VAKSINE_ID fra ODB_FAKTURA_C_VAKSINE
oppdragstype|String| **_ORDRE_**
tjenesteType|String| _**ny**_
mottakergruppe|String| **_Virksomhet_**
valutasort|String| **_NOK_**
egenReferanse|String| FAKTURA_C_VAKSINE_ID fra ODB_FAKTURA_C_VAKSINE
fakturaReferanse|String| **_Covid19-vaksinering <år>-<måned>_**
fakturaType|String| **_Covid19-vaksinering_**
meldingFaktura|String| **_Refusjon for covid19-vaksinering hos fastlege. Månedsfaktura <år>-<måned>._**
ordreType|String| FV | 
mottakerNavn|String| Navn fra ODB_KOMMUNE_FAKTURERING
mottakerAdresse| Mottakeradresse | Adresse fra ODB_KOMMUNE_FAKTURERING
belop|Number| Sum av beløpet på takster som inngår i fakturaen 
betalingsfrist|Number| _**20**_ 
artikkellinjer|Array:Artikkellinje|

### Mottakeradresse
Felt | Type | Beskrivelse
-----|------ |------------
adresselinje1|String| Adresse fra ODB_KOMMUNE_FAKTURERING
postnr|String| Postnr fra ODB_KOMMUNE_FAKTURERING
poststed|String| Poststed fra ODB_POSTSTED
landkode|String| **_NO_**


### Artikkellinje 
Det lages 1 artikkellinje per lege i en praksis som har vaksinert pasienter fra kommunen den måneden. 

Felt | Type | Beskrivelse 
-----|------ |------------
linjenummer|Number|
belop|Number| Sum av beløpet på takstene for legen i praksisen
artskonto|String| **8301** 
kapittelPost|String| **374006** 
utleveringsdato|Date| Settes til første i måneden fakturaen gjelder
artikkelnummer|String| V 
antallEnheter|Number| 100 
tekstlinje|Array:Tekstlinje| En linje per ekstra felt som skal med 
     
### Tekstlinje 
Felt | Type | Beskrivelse
-----|------ |------------
tekstlinjenummer|Number|      
tekstlinjetekst|String|

#### Tekstlinjeverdier
tekstlinjenummer|tekstlinjetekst-prefix| Format | Beskrivelse
-----|------|---------|------------------
1|Orgnr| | Legens org.nr. hentet fra avsender_orgnr. Kan være blank.
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
{
  "meldingId": "7006aace-4059-47cb-990c-e51eb3967eed",
  "offisiellId": "99998888",
  "systemId": 15,
  "forsystemRef": "F1",
  "oppdragstype": "ORDRE",
  "tjenesteType": "ny",
  "mottakergruppe": "Virksomhet",
  "valutasort": "NOK",
  "egenReferanse": "1",
  "fakturaReferanse": "OSL-VAK-1-FAK",
  "fakturaType": "Covid19-vaksinering",
  "meldingFaktura": "Refusjon for covid19-vaksinering hos fastlege. Månedsfaktura 2021-01.",
  "ordreType": "FV",
  "mottakerNavn": "Oslo",
  "mottakerAdresse": {
    "adresselinje1": "Rådhuset 1",
    "postnr": "0170",
    "poststed": "Oslo",
    "landkode": "NO"
  },
  "belop": 30000.0,
  "betalingsfrist": 20,
  "artikkellinjer": [
    {
      "linjenummer": 1,
      "belop": 15000.0,
      "artskonto": "8301",
      "kapittelPost": "374006",
      "artikkelnummer": "V",
      "antallEnheter": 100,
      "tekstlinje": [
        {
          "tekstlinjenummer": 1,
          "tekstlinjetekst": "Orgnr;88889999"
        },
        {
          "tekstlinjenummer": 2,
          "tekstlinjetekst": "HPRnr;99998888"
        },
        {
          "tekstlinjenummer": 3,
          "tekstlinjetekst": "Legensnavn;Test Person"
        },
        {
          "tekstlinjenummer": 4,
          "tekstlinjetekst": "Legekontor;Legekontor"
        },
        {
          "tekstlinjenummer": 5,
          "tekstlinjetekst": "Utbetalt refusjon;15000.0"
        },
        {
          "tekstlinjenummer": 6,
          "tekstlinjetekst": "Antall takst 61a;3"
        },
        {
          "tekstlinjenummer": 7,
          "tekstlinjetekst": "Refusjon takst 61a;660.0"
        },
        {
          "tekstlinjenummer": 8,
          "tekstlinjetekst": "Antall takst 61b;3"
        },
        {
          "tekstlinjenummer": 9,
          "tekstlinjetekst": "Refusjon takst 61b;660.0"
        },
        {
          "tekstlinjenummer": 10,
          "tekstlinjetekst": "Antall takst 62;1"
        },
        {
          "tekstlinjenummer": 11,
          "tekstlinjetekst": "Refusjon takst 62;6840.0"
        },
        {
          "tekstlinjenummer": 10,
          "tekstlinjetekst": "Antall takst 63;1"
        },
        {
          "tekstlinjenummer": 11,
          "tekstlinjetekst": "Refusjon takst 63;6840.0"
        }
      ]
    },
    {
      "linjenummer": 2,
      "belop": 15000.0,
      "artskonto": "827",
      "kapittelPost": "074072",
      "artikkelnummer": "V",
      "antallEnheter": 100,
      "tekstlinje": [
        {
          "tekstlinjenummer": 1,
          "tekstlinjetekst": "Orgnr;88889999"
        },
        {
          "tekstlinjenummer": 2,
          "tekstlinjetekst": "HPRnr;99998888"
        },
        {
          "tekstlinjenummer": 3,
          "tekstlinjetekst": "Legensnavn;Test Perso2n"
        },
        {
          "tekstlinjenummer": 4,
          "tekstlinjetekst": "Legekontor;Legekontor2"
        },
        {
          "tekstlinjenummer": 5,
          "tekstlinjetekst": "Utbetalt refusjon;15000.0"
        },
        {
          "tekstlinjenummer": 6,
          "tekstlinjetekst": "Antall takst 61a;3"
        },
        {
          "tekstlinjenummer": 7,
          "tekstlinjetekst": "Refusjon takst 61a;660.0"
        },
        {
          "tekstlinjenummer": 8,
          "tekstlinjetekst": "Antall takst 61b;3"
        },
        {
          "tekstlinjenummer": 9,
          "tekstlinjetekst": "Refusjon takst 61b;660.0"
        },
        {
          "tekstlinjenummer": 10,
          "tekstlinjetekst": "Antall takst 62;1"
        },
        {
          "tekstlinjenummer": 11,
          "tekstlinjetekst": "Refusjon takst 62;6840.0"
        },
        {
          "tekstlinjenummer": 10,
          "tekstlinjetekst": "Antall takst 63;1"
        },
        {
          "tekstlinjenummer": 11,
          "tekstlinjetekst": "Refusjon takst 63;6840.0"
        }
      ]
    }
  ]
}

```

