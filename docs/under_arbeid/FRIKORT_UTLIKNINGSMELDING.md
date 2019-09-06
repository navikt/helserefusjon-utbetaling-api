# FRIKORT Utlikningsmelding
Utlikningsmelding fra Frikort for å utlikne tidligere utbetalinger.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
**Følgende felter er nye/endret ift opprinnelig utbetalingsmelding:**
* forsystemRef: Når er det behov for å løpenr? Vil vi noen gang sende en utlikningsmelding på nytt? Altså at det faktisk opprettes en ny utlikningsmelding?
* Skal oppdragstype ha en annen verdi? Evnt tjenestetype
* bilagnummer: Denne er grei.
* bilagsart: Er UA ved foreldelse?
  * Fra meldingsbeskrivelsen: Skal være: UF - for utlingning på grunn av feil. UA - for avskrivning av utbetalinger som er mer enn tre år gamle. De nye bilagsartene må etableres i UBW.
* belop: Beløp med motsatt fortegn av beløpet på den opprinnelige utbetalingen.
* Status: Dette feltet finnes ikke og skal være blank ihht meldingsbeskrivelsen. Trenger vi å ta det med?
* Utbetalingstype: Denne står i meldingsbeskrivelsen, men jeg kan ikke se at har denne med på opprinnelig utbetalingsmelding. 
  * Fra meldingsbeskrivelsen: Som for den opprinnelige utbetalingen.
* Kontering.belop: Skal ha motsatt fortegn.
  
**Andre ting å avklare:**
* Tjenestetype: Hva skal denne være, NY eller ENDRET, dersom vi har sendt en endringsmelding?
* Kan vi forenkle meldingen ennå mer? Hvilke felter er det egentlig nødvendig å sende med?
  * Trenger vi konteringer?
  * Det vil være enklere å håndtere denne med mange færre felter.
* Betyr det noe om det har vært endringsmeldinger etter at vi sendte opprinngelig utbetalingsmelding? Disse har samme forsystemRef. 

### Utbetaling
Felt | Type | Obligatorisk | Beskrivelse / Verdi
-----|------|--------------| -------------------
offisiellId |String | Ja | fødselsnummer
praksisId | String | Ja | borgerId (en unik id for en borger, uavhengig av fødselsnummer)
systemId | Number | Ja | _**16**_
forsystemRef|String| Ja | Må være en annen id enn den opprinnelige utbetalingen da det opprettes en ny utbetaling og forsystemreferansen må være unik. Kan for eksempel være den opprinnelige forsystemreferansen + en bindestrek og et løpenummer. Det samme må tenkes på hvis man skal sende utbetalingen på nytt etter at den er utlignet.
oppdragstype|String| Ja | _**UTBETALING**_
tjenesteType|String| Ja | Kan være en av følgende: _**NY**_, _**ENDRET**_
mottakergruppe|String| Ja | _**PRIVATPERSON**_
valutasort|String| Ja | Kodeverk: ISO-4217. Settes til valutakoden som er knyttet til borgers konto. 
meldingId | String | Ja | CorrelationId for den nye utlikningsmeldingen.
mottakerNavn | String | Ja | navn på borger (fra Frikort-borger)
mottakerAdresse.landkode | String | Ja | _**KAN DENNE UTGÅ?????.**_
utenlandsbetaling | Number | Ja | Indikerer om det er norsk eller utenlands betaling.
bilagnummer | String | Ja | _**Bilagsnummeret til utbetalingen man skal utligne. Nytt felt**_.
bilagsart | String | Ja | _**Skal være: UF - for utlingning på grunn av feil. UA - for avskrivning av utbetalinger som er mer enn tre år gamle. De nye bilagsartene må etableres i UBW.**_
forfallsdato | Date| Ja | Dagens dato. Format er ISO8601: ``yyyy-MM-ddTHH:mm:ss.SSSZ``. _Todo: Avklare omkring neste virkedag._ 
belop | Number | Ja | _**Beløp med motsatt fortegn av beløpet på den opprinnelige utbetalingen.**_
konteringer | Array:Konteringslinje ||

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Samme som opprinngelig utbetaling.
artskonto | String | Samme som opprinngelig utbetaling. 
kapPost | String | Samme som opprinngelig utbetaling.
belop | Number | _**Beløp med motsatt fortegn av den opprinnelige utbetalingen.**_
 
 
# Eksempler på utfylling av utlikningsmelding
_**TODO Eksempelmeldingen er ikke ferdig ennå**_

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
