# FRIKORT Utbetaling
Utbetalingsmelding fra Frikort for nye utbetalinger.

Pt. gjelder denne meldingsbeskrivelse kun for utbetaling til norske kontoer.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
### Mapping av utbetalingslinjer i Frikort til Utbetalingsmelding
En utbetalingsmelding inneholder en aggregering av utbetalingslinjer fra Frikort.

Hver utbetalingslinje representerer helt eller delvis refusjon av **EN** egenandel.

Utbetalingsmelding blir først sendt når akkumulert beløp overstiger 200 NOK.

Hver utbetalingslinje holdes igjen i Frikort for å samle opp slik at man ikke lager unødvendig mange utbetalingsmeldinger. 


### Utbetaling
Felt | Type | Beskrivelse / Verdi
-----|------ |-------------------
meldingId | String | GUID for hver melding
offisiellId |String | borgerident
~~praksisId~~ | ~~String~~ | ~~ikke i bruk for Frikort~~
systemId | Number | _**16**_
forsystemRef|String| _**FRIKU **_ + utbetalingsid fra Frikort-utbetaling. _Er det ok?_
oppdragstype|String| _**UTBETALING**_
tjenesteType|String| _**NY**_
mottakergruppe|String| _**PRIVATPERSON**_
valutasort|String| **_NOK_**
navn | String | navn på borger (fra Frikort-borger)
~~adresse~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
postnr | ~~String~~| _**0000**_
~~poststed~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
landkode | String | _**NO**_
kontonummer | String | gironummer (fra Frikort-borger)
~~BBAN~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
~~IBAN~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
~~BIC~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
~~betalingsartkode~~ | ~~String~~ | ~~ikke i bruk for Frikort ved utbetalinger til norsk konto~~
bilagsart | String | _**TR**_
forfallsdato | Date| Dagens dato 
belop | Number | Sum beløp på alle utbetalingslinjene
~~kidnummer~~ | String | ~~ikke i bruker for Frikort~~
~~eksternReferanse~~ | ~~String~~ | ~~ikke i bruker for Frikort~~
melding | String | Teksten "Refusjon egenandel(er) frikort 2018" (År blir generert dynamisk).
konteringer | Array:Konteringslinje |

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | _*874*_ Forstår det slik at denne skal være 874?
kapPost | String | _???_  Hva skal denne være?
belop | Number | beløp fra utbetalingslinje
~~koststed~~ | ~~String~~ | ~~_**2340??**_ Skal denne fylles inn av Frikort?~~
~~fradato~~ | ~~Date~~ | Antar at denne ikke skal fylles inn for Frikort?
~~tildato~~ | ~~Date~~ | Antar at denne ikke skal fylles inn?
 


## Eksempel

```
{
	"forsystemRef": "FRIKU510000000016844",
	"meldingId": "c61c646b-f87d-11e8-a217-ffa20916eaa5",
	"systemId": 16,
	"offisiellId": "12345612345",
	"oppdragstype": "UTBETALING",
	"belop": 80.00,
	"valutasort": "NOK",
	"mottakergruppe": "PRIVATPERSON",
	"tjenesteType": "NY",
	"kontonummer": "15031769342",
	"navn": "Finn Dott No",
	"postnr": "0000",
	"bilagsart": "TR",
	"forfallsdato": "2019-12-24",
	"landkode": "NO",
	"konteringer": [{
			"linjenr": 1,
			"artskonto": "874",
			"kapPost": "???",
			"belop": 48.80,
		}, {
			"linjenr": 0,
			"artskonto": "874",
			"kapPost": "???",
			"belop": 31.20,
		}
	]
}
```