# FRIKORT Utbetaling

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
systemId | Number | _**16**_ = FRIKORT
forsystemRef|String| _**FRIKU? **_ + utbetalingsid fra UTBETALING. Skal alltid være FRIK etterfulgt av en bokstav: U (Ubetaling), E (Endre), A (Annulering), S (Stopp).
oppdragstype|String| _**UTBETALING**_ (hentet fra eResept)
tjenesteType|String| _**NY**_ (hentet fra eResept)
mottakergruppe|String| _**PRIVATPERSON**_ (hentet fra dok)
valutasort|String| **_NOK_** (hentet fra eResept). Hvordan håndtere andre valutaer?
navn | String | navn fra Borger (i dok står det "navn på leverandør"?)
postnr | String| _avklar_ (fra eresept: _**0000**_). Hvordan håndtere utland?
landkode | String | _avklar_ (fra eresept: _**NO**_). Hvordan håndtere utland (hvilket kodeverk brukes for landkoder ISO 3166-1 alpha-2)?
kontonummer | String | gironummer fra Borger (_hva med utland)_
bilagsart | String | _**TR**_ (hentet fra eResept og dok)
forfallsdato | Date| Dagens dato 
belop | Number | Sum beløp på alle utbetalingslinjene
~~kidnummer~~ | String | ~~kid fra SAR~~ _Utgår_
melding | String | "Refusjon egenandel(er) frikort 2018" Velg år dynamisk.
konteringer | Array:Konteringslinje |

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | _874_ (en fast verdi?) (Hentet fra dok)
kapPost | String | _???_ 
belop | Number | beløp fra utbetaling
koststed | String | _**2340**_ (avklar om denne skal fylles inn)
fradato | Date | Antar at denne ikke skal fylles inn?
tildato | Date | Antar at denne ikke skal fylles inn?
 


## Eksempel

```
{
	"forsystemRef": "FRIKU510000000016844",
	"meldingId": "c61c646b-f87d-11e8-a217-ffa20916eaa5",
	"systemId": 14,
	"offisiellId": "973151401",
	"oppdragstype": "UTBETALING",
	"belop": 80.00,
	"valutasort": "NOK",
	"mottakergruppe": "VIRKSOMHET",
	"tjenesteType": "NY",
	"praksisId": "1000472046",
	"kontonummer": "15031769342",
	"navn": "Test 5.21 RC3",
	"postnr": "0000",
	"bilagsart": "TR",
	"forfallsdato": "2018-12-04",
	"landkode": "NO",
	"konteringer": [{
			"linjenr": 1,
			"artskonto": "872",
			"kapPost": "275170",
			"belop": 48.80,
			"koststed": "2340"
		}, {
			"linjenr": 0,
			"artskonto": "872",
			"kapPost": "275270",
			"belop": 31.20,
			"koststed": "2340"
		}
	]
}
```