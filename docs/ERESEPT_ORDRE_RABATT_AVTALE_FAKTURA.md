# ERESEPT Ordre Rabatt Avtale Faktura

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|-----|--------------------
meldingId | String | GUID for hver melding
offisiellId |String | orgnr fra RABATT_AVTALE_FIRMA 
systemId | Number | _**14**_ = ERESEPT
forsystemRef | String | _**R**_ + rabatt_avtale_faktura_id fra RABATT_AVTALE_FAKTURA
oppdragstype | String| _**ORDRE**_
tjenesteType | String | _**NY**_
mottakergruppe | String | _**VIRKSOMHET**_
valutasort | String | _**NOK**_
navnKontakt | String | navn fra RABATT_AVTALE_FIRMA
adresseKontakt | String | adresse fra RABATT_AVTALE_FIRMA
postnrKontakt | String | postnr fra RABATT_AVTALE_FIRMA
poststedKontakt | String | poststed fra RABATT_AVTALE_FIRMA
ordreType | String | _**FR**_
meldingFaktura | String | _**Rabatt legemidler ihht. avtale. Periode. Periode dd.MM.yyyy - dd.MM.yyyy**_
fakturaType | String | _**H-resept**_
belop | Number | sum_rabatt_belop fra RABATT_AVTALE_FAKTURA
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


 
 


## Eksempel

```
{
	"forsystemRef": "R1",
	"meldingId": "ea0ca08c-f89d-11e8-a443-9b00ec994fee",
	"systemId": 14,
	"offisiellId": "982725038",
	"oppdragstype": "ORDRE",
	"belop": 5272.26,
	"valutasort": "NOK",
	"mottakergruppe": "VIRKSOMHET",
	"tjenesteType": "NY",
	"navnKontakt": "Amgen AB Norge NUF",
	"adresseKontakt": "Postboks 1532 Vika",
	"postnrKontakt": "0117",
	"poststedKontakt": "Oslo",
	"ordreType": "FR",
	"meldingFaktura": "Rabatt legemidler ihht. avtale. Periode 01.07.2018 - 31.07.2018",
	"fakturaType": "Rabatt legemidler",
	"egenReferanse": "AMGEN-2018-07-1-1",
	"fakturaReferanse": "Hilde Gresslien",
	"betalingsfrist": 14,
	"artikkellinjer": [{
			"linjenummer": 1,
			"utleveringsdato": "2018-06-17",
			"artikkelnummer": "377249",
			"antallEnheter": 100,
			"belop": 5272.26,
			"artskonto": "872",
			"kapittelpost": "275170",
			"tekstlinje": [{
					"tekstlinjenummer": 1,
					"tekstlinjetekst": "Regningsid;4122710"
				}, {
					"tekstlinjenummer": 2,
					"tekstlinjetekst": "Status;Godkjent"
				}
			]
		}
	]
}
```

