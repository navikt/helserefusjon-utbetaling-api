# FRIKORT Utlikningsmelding
Utlikningsmelding fra Frikort for å utlikne tidligere utbetalinger.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
En utligningsmelding skal utligne en tidligere innsende utbetalingsmelding. Beløpene vil være de samme beløpene som i opprinnelig utbetalingsmelding bare med negativt fortegn.
Utligningsmeldingen til også referere til bilagsnr

### Utligningsmelding
Felt | Type | Obligatorisk | Beskrivelse / Verdi
-----|------|--------------| -------------------
offisiellId |String | Ja | fødselsnummer
praksisId | String | Ja | borgerId (en unik id for en borger, uavhengig av fødselsnummer)
systemId | Number | Ja | _**16**_
forsystemRef|String| Ja | **"FRIKU"** + id fra den opprinnelige utbetalingen + **"-UTL"**. Eks. **FRIKU94949-UTL**. 
oppdragstype|String| Ja | _Burde denne være noe annet enn _**UTBETALING**_? F.eks. UTLIGNING?_
tjenesteType|String| Ja | _**Hva skal denne være dersom det har vært en endringsmelding sendt? Skal den fremdeles være NY**_. En mulighet er f.eks. en ny verdi, f.eks. UTLIGNING?
mottakergruppe|String| Ja | _**PRIVATPERSON**_
valutasort|String| Ja | Kodeverk: ISO-4217. Settes til valutakoden som er knyttet til borgers konto. 
meldingId | String | Ja | CorrelationId for den nye utlikningsmeldingen.
mottakerNavn | String | Ja | navn på borger (fra Frikort-borger)
mottakerAdresse.landkode | String | Ja | _**KAN DENNE UTGÅ?????.**_
utenlandsbetaling | Number | Ja | _**KAN DENNE UTGÅ?????.**_
bilagId (merk annet navn enn bilagsnummer) | String | Ja | _**Bilagsnummeret til utbetalingen man skal utligne. Nytt felt**_. MERK! I meldingsbeskrivelse fra Hdir er det kalt bilagsnummer, men i kvitteringen heter det bilagsnummer.
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
```
{
  "offisiellId": "12345612345",
  "praksisId": 3333434,
  "systemId": 16,
  "forsystemRef": "FRIKU89891-UTL",
  "oppdragstype": "XXXXX",
  "tjenesteType": "XXXXX",
  "mottakergruppe": "PRIVATPERSON",
  "valutasort": "NOK",
  "meldingId": "7a30b579-9318-4e88-adb9-d68c5671c4c3",
  "mottakerNavn": "Finn Dott No",
  "bilagsart": "TR",
  "forfallsdato": "2019-03-11T16:34:23.95+01:00",
  "belop": -40,
  "konteringer": [
    {
      "linjeNr": 0,
      "artskonto": "874",
      "kapPost": "275270",
      "belop": -20
    },
    {
      "linjeNr": 1,
      "artskonto": "874",
      "kapPost": "275270",
      "belop": -20
    }
  ]
}
```
