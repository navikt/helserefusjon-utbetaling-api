# ERESEPT Ordre Hresept faktura

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_
### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------|--------------------
meldingId | String | GUID for hver melding
offisiellId |String | orgnr fra HRES_HELSEFORETAK 
systemId | Number | _**14**_ = ERESEPT
forsystemRef | String | _**H**_ + hres_faktura_id fra HRES_FAKTURA
oppdragstype | String| _**ORDRE**_
tjenesteType | String | _**NY**_
mottakergruppe | String | _**VIRKSOMHET**_
valutasort | String | _**NOK**_
navnKontakt | String | navn fra HRES_HELSEFORETAK
adresseKontakt | String | adresse fra HRES_HELSEFORETAK
postnrKontakt | String | postnr fra HRES_HELSEFORETAK
poststedKontakt | String | poststed fra HRES_HELSEFORETAK
ordreType | String | _**FH**_
meldingFaktura | String | _**Refusjon for H-reseptoppgjør til apotek. Periode dd.MM.yyyy - dd.MM.yyyy**_
fakturaType | String | _**H-resept**_
belop | Number | sum_belop fra HRES_FAKTURA
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

 
 


## Eksempel
```
{
	"forsystemRef": "H82",
	"meldingId": "ea17eb2d-f89d-11e8-a443-49cd4e4490d6",
	"systemId": 14,
	"offisiellId": "983975267",
	"oppdragstype": "ORDRE",
	"belop": 4091.20,
	"valutasort": "NOK",
	"mottakergruppe": "VIRKSOMHET",
	"tjenesteType": "NY",
	"navnKontakt": "Sykehuset Telemark HF",
	"ordreType": "FH",
	"meldingFaktura": "Refusjon for H-reseptoppgjør til apotek. Periode 16.10.2018 - 31.10.2018",
	"fakturaType": "H-resept",
	"egenReferanse": "HR-TEL-2018-10-4-82",
	"fakturaReferanse": "H-resept",
	"betalingsfrist": 15,
	"artikkellinjer": [{
			"linjenummer": 1,
			"utleveringsdato": "2018-10-15",
			"artikkelnummer": "023968",
			"antallEnheter": 400,
			"belop": 4091.20,
			"artskonto": "827",
			"kapittelpost": "074071",
			"tekstlinje": [{
					"tekstlinjenummer": 1,
					"tekstlinjetekst": "Kommunenummer;0815"
				}, {
					"tekstlinjenummer": 2,
					"tekstlinjetekst": "Regningsid;4123205"
				}, {
					"tekstlinjenummer": 3,
					"tekstlinjetekst": "Vedtaksdato;22.10.2018"
				}
			]
		}
	]
}
```

