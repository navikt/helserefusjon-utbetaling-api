# FRIKORT Endret Utbetaling

meldingsdefinisjon for utbetaling-endret meldinger for Frikort.

### Utbetaling-endret
Felt | Type | Påkrevet | Beskrivelse 
-----|------ |------ |-------------------
meldingId | String | Ja | 
offisiellId | String | Ja |
praksisId | String | Ja | (Frikort setter borgerId)
systemId | Number | Ja | 
forsystemRef| String | Ja | Skal denne være med?
oppdragstype| String | Ja | _**UTBETALING**_
tjenesteType| String | Ja | _**ENDRET**_
mottakergruppe| String | Ja |
kontonummer | String | Nei
mottakerNavn | String | Nei| Nytt felt
mottakerAdresse | Adresse | Nei | Nytt felt
banknavn | String | Nei | Nytt felt
bankAdresse | Adresse | Nei | Nytt felt
iban | String | Nei | Nytt felt
bban | String | Nei | Nytt felt
swift | String | Nei | Nytt felt
bankkode | String | Nei | Nytt felt
bilagId | Number | Nei |
endretKontakt | Number | Ja |  Nytt felt
endretKid  | Number | Ja |  Alltid false
valutasort | String | Ja  | _Skal denne være med ???_

### Adresse
Felt | Type | Påkrevet | Beskrivelse 
-----|----- |----- |--------------------
landkode | String | Nei | Ny
adresselinje1 | String | Nei |Ny
adresselinje2 | String | Nei |Ny
adresselinje3 | String | Nei |Ny

## Eksempel norsk utbetaling
Nedenfor er et eksempel på en endret utbetalingsmelding til en borger som har norsk kontonummer.

```
{
  "offisiellId": "1234561",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKU0001",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "ENDRET",
  "mottagergruppe": "PRIVATPERSON",
  "kontonummer": "15031769342",
  "valutasort": "NOK",
  "meldingId": "7a30b579-9318-4e88-adb9-d68c5671c4c3",
  "mottakerNavn": "Finn Dott No",
  "utenlandsbetaling": 0,
  "endretKontakt": 1,
  "endretKid": 0
}
```

## Eksempel IBAN utbetaling
Nedenfor er et eksempel på en endret utbetalingsmelding til en borger som har et IBAN nummer til en bank i Tyskland.

```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKU0002",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "ENDRET",
  "mottagergruppe": "PRIVATPERSON",
  "kontonummer": "15031769342",
  "valutasort": "EUR",
  "meldingId": "a54402e4-002f-4436-8349-149a92e9bb41",
  "utenlandsbetaling": 1,
  "endretKontakt": 1,
  "endretKid": 0,
  "iban": "DE123456789123",
  "swift": "SWCODE99",
  "bilagsart": "TR",
  "mottakerNavn": "Finn Dott No",
  "mottakerAdresse": {
      "landkode": "DE",
      "adresselinje1": "Heinzstrasse 11",
      "adresselinje2": "87789 Düsseldorf",
      "adresselinje3": "GERMANY"
    }
}
```

## Eksempel BBAN utbetaling
Nedenfor er et eksempel på en endret utbetalingsmelding til en borger som har et BBAN nummer til en bank i USA.

```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKU0002",
  "oppdragstype": "UTBETALING",
  "tjenesteType": "ENDRET",
  "mottagergruppe": "PRIVATPERSON",
  "kontonummer": "15031769342",
  "valutasort": "USD",
  "meldingId": "347d3b5b-0f35-4613-aa9b-9aacfa5b9826",
  "utenlandsbetaling": 1,
  "endretKontakt": 1,
  "endretKid": 0,
  "mottakerNavn": "Apple",
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
  "bilagsart": "TR",
  "bankAdresse": {
     "landkode": "US",
     "adresselinje1": "200 West St",
     "adresselinje2": "NY 10282",
     "adresselinje3": "USA"
    }
}
```