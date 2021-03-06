# FRIKORT Utbetaling
Utbetalingsmelding fra Frikort for nye utbetalinger.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
### Mapping av utbetalingslinjer i Frikort til Utbetalingsmelding
En utbetalingsmelding inneholder en aggregering av utbetalingslinjer fra Frikort.

Hver utbetalingslinje representerer helt eller delvis refusjon av **EN** egenandel.

Utbetalingsmelding blir først sendt når akkumulert beløp overstiger 200 NOK.

Hver utbetalingslinje holdes igjen i Frikort for å samle opp slik at man ikke lager unødvendig mange utbetalingsmeldinger. 


### Utbetaling
Felt | Type | Obligatorisk | Beskrivelse / Verdi
-----|------|--------------| -------------------
offisiellId |String | Ja | fødselsnummer
praksisId | String | Ja | borgerId (en unik id for en borger, uavhengig av fødselsnummer)
systemId | Number | Ja | _**16**_
forsystemRef|String| Ja | _**FRIKU **_ + utbetalingsid fra Frikort-utbetaling. _Denne må ikke være lenger enn maks 25 tegn_
oppdragstype|String| Ja | _**UTBETALING**_
tjenesteType|String| Ja | Kan være en av følgende: _**NY**_, _**ENDRET**_
mottakergruppe|String| Ja | _**PRIVATPERSON**_
valutasort|String| Ja | Kodeverk: ISO-4217. Settes til valutakoden som er knyttet til borgers konto. 
meldingId | String | Ja | GUID for hver melding. meldingId i [UTBETALINGSOPPDRAG](../UTBETALINGSOPPDRAG.md) skal settes til denne verdien Helseutbetaling.
mottakerNavn | String | Ja | navn på borger (fra Frikort-borger)
mottakerAdresse.landkode | String | Nei | Settes bare for utenlandsbetalinger. Kodeverdien hentes fra TPS for utenlandske adresser (feltet uland). Skal følger ISO-3166-1 alpha-2, mens TPS har ISO 3100-1 alpha-3.
mottakerAdresse.adresselinje1 | String | Nei | Settes bare for utenlandsbetalinger. Hentes fra TPS (uadresse1)
mottakerAdresse.adresselinje2 | String | Nei | Settes bare for utenlandsbetalinger. Hentes fra TPS (uadresse2)
mottakerAdresse.adresselinje3 | String | Nei | Settes bare for utenlandsbetalinger. Hentes fra TPS (uadresse3)
utenlandsbetaling | Number | Ja | Indikerer om det er norsk eller utenlands betaling.
kontonummer | String | Nei | Inneholder norsk bankkontonummer. Settes bare når det er innenlandsbetaling.
iban | String | Nei | For de landene som bruker IBAN. Settes bare for utenlandsbetalinger. 
bban | String | Nei | For de landene som bruker BBAN. Settes bare for utenlandsbetalinger. 
swift | String | Nei | Hvis mottaker har et IBAN kontonummer skal denne fylles ut. Ved BBAN kan den fylles ut om man har denne informasjonen. Settes bare for utenlandsbetalinger. 
bankkode | String | Nei | Bankcode/clearingcode som brukes for noen land. Settes bare for utenlandsbetalinger. 
banknavn | String | Nei | For de landene som bruker BBAN. Settes bare for utenlandsbetalinger. 
bankAdresse.landkode | String | Nei | Settes til _**NO**_ for norsk konto, ellers ISO-3166-1 alpha-2 for utenlandske konto. Settes bare for utenlandsbetalinger. 
bankAdresse.adresselinje1 | String | Nei | Hentes fra TPS (Adresse-linje1). Settes bare for utenlandsbetalinger. 
bankAdresse.adresselinje2 | String | Nei | Hentes fra TPS (Adresse-linje2). Settes bare for utenlandsbetalinger. 
bankAdresse.adresselinje3 | String | Nei | Hentes fra TPS (Adresse-linje3). Settes bare for utenlandsbetalinger.
bilagsart | String | Ja | _**TR**_
forfallsdato | Date| Ja | Dagens dato. Format er ISO8601: ``yyyy-MM-ddTHH:mm:ss.SSSZ``. _Todo: Avklare omkring neste virkedag._ 
belop | Number | Ja | Sum beløp på alle utbetalingslinjene
melding | String | Ja | Teksten "Refusjon egenandel(er) frikort 2018" (År blir generert dynamisk).
konteringer | Array:Konteringslinje ||

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | _*874*_ for betaling til norsk bank, _*874*_ for betaling til bank i utlandet. 
kapPost | String | _*275270*_ for tak 1. _*275271*_ for tak 2. **Todo** Det kan være at det skal være andre verdier også, dette skal avklares.
belop | Number | beløp fra utbetalingslinje
 
 
# Eksempler på utfylling av utbetalingsmelding
Det er satt opp tre eksempelmeldinger for de tre mulig scenarioene. 
* En typisk norsk utbetaling (de aller fleste meldingene vil av denne typen).
* IBAN: Eksempel på utbetaling til utlandet hvor kontoinformasjon er til et IBAN nummer.
* BBAN: Eksempel på utbetaling til utlandet hvor kontoinformasjon er til et BBAN nummer.

## Eksempel norsk utbetaling
Nedenfor er et eksempel på en ny utbetalingsmelding til en borger som har norsk kontonummer.
Mottakeradresse settes ikke. Ingen informasjon om utenlandsbetaling blir angitt.

```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKU0001",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "NY",
  "mottakergruppe": "PRIVATPERSON",
  "valutasort": "NOK",
  "meldingId": "7a30b579-9318-4e88-adb9-d68c5671c4c3",
  "mottakerNavn": "Finn Dott No",
  "utenlandsbetaling": 0,
  "kontonummer": "15031769342",
  "bilagsart": "TR",
  "forfallsdato": "2019-03-11T16:34:23.95+01:00",
  "belop": 40,
  "konteringer": [
    {
      "linjeNr": 0,
      "artskonto": "874",
      "kapPost": "275270",
      "belop": 20
    },
    {
      "linjeNr": 1,
      "artskonto": "874",
      "kapPost": "275270",
      "belop": 20
    }
  ]
}
```


## Eksempel IBAN utbetaling
Nedenfor er et eksempel på en ny utbetalingsmelding til en borger som har et IBAN nummer til en bank i Tyskland.
For IBAN så settes følgende felter spesielt:
* iban
* swift
* valutasort
* mottakerAdresse.landkode
* mottakerAdresse.adresselinje1
* mottakerAdresse.adresselinje2
* mottakerAdresse.adresselinje3
* artskonto i konteringene settes til "878"

_Merk at adresselinjene bare blir satt om Frikort (TPS) inneholder adresseinformasjon._


## Eksempel IBAN utbetaling

```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKUIBANIBANIBAN",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "NY",
  "mottakergruppe": "PRIVATPERSON",
  "valutasort": "EUR",
  "meldingId": "a54402e4-002f-4436-8349-149a92e9bb41",
  "mottakerNavn": "Finn Dott No",
  "utenlandsbetaling": 1,
  "mottakerAdresse": {
    "landkode": "DE",
    "adresselinje1": "Heinzstrasse 11",
    "adresselinje2": "87789 Düsseldorf",
    "adresselinje3": "GERMANY"
  },
  "iban": "DE123456789123",
  "swift": "SWCODE99",
  "bilagsart": "TR",
  "forfallsdato": "2019-03-11T18:32:23.474+01:00",
  "belop": 40,
  "konteringer": [
    {
      "linjeNr": 0,
      "artskonto": "878",
      "kapPost": "275270",
      "belop": 20
    },
    {
      "linjeNr": 1,
      "artskonto": "878",
      "kapPost": "275270",
      "belop": 20
    }
  ]
}
```

## Eksempel BBAN utbetaling
Nedenfor er et eksempel på en ny utbetalingsmelding til en borger som har et BBAN nummer til en bank i USA.
For BBAN så settes følgende felter spesielt:
* bban
* banknavn
* bankkode
* valutasort
* mottakerAdresse.landkode
* mottakerAdresse.adresselinje1
* mottakerAdresse.adresselinje2
* mottakerAdresse.adresselinje3
* bankAdresse.landkode
* bankAdresse.adresselinje1
* bankAdresse.adresselinje2
* bankAdresse.adresselinje3
* artskonto i konteringene settes til "878"

_Merk at adresselinjene bare blir satt om Frikort (TPS) inneholder adresseinformasjon._


## Eksempel BBAN utbetaling

```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKUBBANBBANBBAN",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "NY",
  "mottakergruppe": "PRIVATPERSON",
  "valutasort": "USD",
  "meldingId": "347d3b5b-0f35-4613-aa9b-9aacfa5b9826",
  "mottakerNavn": "Apple",
  "utenlandsbetaling": 1,
  "mottakerAdresse": {
    "landkode": "US",
    "adresselinje1": "767 5th Ave",
    "adresselinje2": "NY 10153",
    "adresselinje3": "USA"
  },
  "bban": "USA123456789123",
  "banknavn": "Goldman Sachs",
  "swift": "SWCODE88",
  "bankkode": "CLEARINGCODE_12",
  "bankAdresse": {
    "landkode": "US",
    "adresselinje1": "200 West St",
    "adresselinje2": "NY 10282",
    "adresselinje3": "USA"
  },
  "bilagsart": "TR",
  "forfallsdato": "2019-03-11T18:42:35.98+01:00",
  "belop": 40,
  "konteringer": [
    {
      "linjeNr": 0,
      "artskonto": "878",
      "kapPost": "275270",
      "belop": 20
    },
    {
      "linjeNr": 1,
      "artskonto": "878",
      "kapPost": "275270",
      "belop": 20
    }
  ]
}   
```