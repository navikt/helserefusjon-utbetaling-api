# ERESEPT Ordre Hresept faktura

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
forsystemRef | String | _**H**_ + hres_faktura_id fra HRES_FAKTURA
meldingId | String | GUID for hver melding
systemId | Number | _**14**_ = ERESEPT
oppdragstype | String| _**ORDRE**_
belop | Number | sum_belop fra HRES_FAKTURA
valutasort | String | _**NOK**_
mottakergruppe | String | _**VIRKSOMHET**_
tjenesteType | String | _**NY**_
offisiellId |String | orgnr fra HRES_HELSEFORETAK 
mottakernavn | String | navn fra HRES_HELSEFORETAK
mottakeradresse | Adresse | adresse fra HRES_HELSEFORETAK
ordreType | String | _**FH**_
meldingFaktura | String | _**Refusjon for H-reseptoppgjør til apotek. Periode dd.MM.yyyy - dd.MM.yyyy**_
fakturaType | String | _**H-resept**_
egenReferanse | String | referanse fra HRES_FAKTURA
fakturaReferanse | String | faktura referanse fra HRES_HELSEFORETAK
betalingsfrist | Number | _**15**_
artikkellinjer | Array:Artikkellinje |



### Artikkellinje
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
linjenummer | Number | Starter på 1
utleveringsdato | String | utleveringsdato fra UTLEVERING på format dd.MM.yyyy
artikkelnummer | String | varenr gfra UTLEVERT_VARE
antallEnheter | Number | antall pakninger fra UTLEVERT_VARE multiplisert med 100
belop | Number | godkjent beløp fra ENKELTREGNING
artskonto | String | _**827**_
kapittelpost | String | _**074071**_
tekstlinje | Array:Tekstlinje |

#### Tekstlinje
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
tekstlinjenummer | Number | Starter på 1
tekstlinjetekst | String | Kommunenummer;yyyy eller Regningsid;xyz eller Vedtaksdato;dd.MM.yyyy eller Krediteringsref;abc

#### Adresse
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
adresselinje1 | String  
postnr | String
poststed | String
landkode | String
 


## Eksempel
```
{
    "forsystemRef": "H120",
    "meldingId": "cc453bb6-8140-11e9-898a-a39190cf7f59",
    "systemId": 14,
    "oppdragstype": "ORDRE",
    "belop": 123.50,
    "valutasort": "NOK",
    "mottakergruppe": "VIRKSOMHET",
    "tjenesteType": "NY",
    "offisiellId": "983974929",
    "mottakernavn": "Sykehuset HF",
    "mottakeradresse": {
        "postnr": "1234",
        "poststed": "Postby",
        "landkode": "NO"
    },
    "ordreType": "FH",
    "meldingFaktura": "Refusjon for H-reseptoppgjør til apotek. Periode 01.05.2019 - 15.05.2019",
    "fakturaType": "H-resept",
    "egenReferanse": "HR-SYK-2019-05-2-120",
    "fakturaReferanse": "Ola Nordmann",
    "betalingsfrist": 15,
    "artikkellinjer": [{
        "linjenummer": 1,
        "utleveringsdato": "2019-04-01",
        "artikkelnummer": "464545",
        "antallEnheter": 100,
        "belop": 123.50,
        "artskonto": "827",
        "kapittelpost": "074071",
        "tekstlinje": [{
            "tekstlinjenummer": 1,
            "tekstlinjetekst": "Kommunenummer;1234"
        },
        {
            "tekstlinjenummer": 2,
            "tekstlinjetekst": "Regningsid;1234567"
        },
        {
            "tekstlinjenummer": 3,
            "tekstlinjetekst": "Vedtaksdato;01.04.2019"
        }]
    }]
}

```

