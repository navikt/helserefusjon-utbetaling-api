# ERESEPT Ordre Rabatt Avtale Faktura

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|-----|--------------------
forsystemRef | String | _**R**_ + rabatt_avtale_faktura_id fra RABATT_AVTALE_FAKTURA
meldingId | String | GUID for hver melding
systemId | Number | _**14**_ = ERESEPT
oppdragstype | String| _**ORDRE**_
belop | Number | sum_rabatt_belop fra RABATT_AVTALE_FAKTURA
valutasort | String | _**NOK**_
mottakergruppe | String | _**VIRKSOMHET**_
tjenesteType | String | _**NY**_
offisiellId |String | orgnr fra RABATT_AVTALE_FIRMA 
mottakernavn | String | navn fra RABATT_AVTALE_FIRMA
mottakeradresse | Adresse | adresse fra RABATT_AVTALE_FIRMA
ordreType | String | _**FR**_
meldingFaktura | String | _**Rabatt legemidler ihht. avtale. Periode. Periode dd.MM.yyyy - dd.MM.yyyy**_
fakturaType | String | _**H-resept**_
egenReferanse | String | referanse fra RABATT_AVTALE_FAKTURA
fakturaReferanse | String | faktura referanse fra RABATT_AVTALE_FAKTURA
betalingsfrist | Number | _**14**_
artikkellinjer | Array:Artikkellinje |

### Artikkellinje
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
linjenummer | Number | Starter på 1
utleveringsdato | String | utleveringsdato fra UTLEVERING på format dd.MM.yyyy
artikkelnummer | String | varenr fra RABATT_AVTALE
antallEnheter | Number | antall pakninger fra RABATT_AVTALE multiplisert med 100
belop | Number | rabatt_belop fra RABATT_AVTALE_ENKELTREGNING
artskonto | String | _**827**_
kapittelpost | String | _**275170**_
tekstlinje | Array:Tekstlinje |

#### Tekstlinje
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
tekstlinjenummer | Number | Starter på 1
tekstlinjetekst | String | Regningsid; + xxx eller Status; + xxx

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
    "forsystemRef": "R11",
    "meldingId": "4685ad37-81da-11e9-898a-6dcb06ab4fb9",
    "systemId": 14,
    "oppdragstype": "ORDRE",
    "belop": 123.45,
    "valutasort": "NOK",
    "mottakergruppe": "VIRKSOMHET",
    "tjenesteType": "NY",
    "offisiellId": "987654321",
    "mottakernavn": "Firma AS",
    "mottakeradresse": {
        "adresselinje1": "Postboks 123",
        "postnr": "0123",
        "poststed": "Oslo",
        "landkode": "NO"
    },
    "ordreType": "FR",
    "meldingFaktura": "Rabatt legemidler ihht. avtale. Periode 01.03.2019 - 31.03.2019",
    "fakturaType": "Rabatt legemidler",
    "egenReferanse": "FIMRMA-2019-03-5-11",
    "fakturaReferanse": "Referansetekst",
    "betalingsfrist": 14,
    "artikkellinjer": [{
        "linjenummer": 1,
        "utleveringsdato": "2019-02-28",
        "artikkelnummer": "123456",
        "antallEnheter": 100,
        "belop": 123.45,
        "artskonto": "872",
        "kapittelpost": "275170",
        "tekstlinje": [{
            "tekstlinjenummer": 1,
            "tekstlinjetekst": "Regningsid;1234567"
        },
        {
            "tekstlinjenummer": 2,
            "tekstlinjetekst": "Status;Godkjent"
        }]
    }]
}
```

