# FRIKORT Utlikningsmelding
Utlikningsmelding fra Frikort for å utlikne tidligere utbetalinger.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
En utligningsmelding skal utligne en tidligere innsende utbetalingsmelding. Beløpene vil være de samme beløpene som i opprinnelig utbetalingsmelding bare med negativt fortegn.
Utligningsmeldingen refererer også til bilagId fra mottatt kvittering.

### Utligningsmelding
Felt | Type | Obligatorisk | Beskrivelse / Verdi
-----|------|--------------| -------------------
offisiellId |String | Ja | Samme som opprinnelig utbetaling
praksisId | String | Ja | Samme som opprinnelig utbetaling
systemId | Number | Ja | _**16**_
forsystemRef|String| Ja | **"FRIKU"** + id fra den opprinnelige utbetalingen + **"-UTL"**. Eks. **FRIKU94949-UTL**.
oppdragstype|String| Ja | Vil alltid være **UTBETALING**
tjenesteType|String| Ja | Vil alltid være **NY**
mottakergruppe|String| Ja | Samme som opprinnelig utbetaling
valutasort|String| Ja | Samme som opprinnelig utbetaling 
meldingId | String | Ja | GUID for hver melding. 
mottakerNavn | String | Ja | Samme som opprinnelig utbetaling
mottakerAdresse.landkode | String | Nei | Samme som opprinnelig utbetaling
mottakerAdresse.adresselinje1 | String | Nei | Samme som opprinnelig utbetaling
mottakerAdresse.adresselinje2 | String | Nei | Samme som opprinnelig utbetaling
mottakerAdresse.adresselinje3 | String | Nei | Samme som opprinnelig utbetaling
utenlandsbetaling | Number | Ja | Samme som opprinnelig utbetaling
bilagId | String | Ja | _**Nytt felt. Bilagsnummeret til utbetalingen man skal utligne. Hentes fra kvittering mottatt fra Hdir.**_. 
kontonummer | String | Nei | Samme som opprinnelig utbetaling
iban | String | Nei | Samme som opprinnelig utbetaling 
bban | String | Nei | Samme som opprinnelig utbetaling 
swift | String | Nei | Samme som opprinnelig utbetaling 
bankkode | String | Nei | Samme som opprinnelig utbetaling 
banknavn | String | Nei | Samme som opprinnelig utbetaling 
bankAdresse.landkode | String | Nei | Samme som opprinnelig utbetaling 
bankAdresse.adresselinje1 | String | Nei | Samme som opprinnelig utbetaling 
bankAdresse.adresselinje2 | String | Nei | Samme som opprinnelig utbetaling 
bankAdresse.adresselinje3 | String | Nei | Samme som opprinnelig utbetaling
bilagsart | String | Ja | _**Skal være: UF - for utlingning på grunn av feil. UA - for avskrivning av utbetalinger som er mer enn tre år gamle.**_
forfallsdato | Date| Ja | Samme som opprinnelig utbetaling 
belop | Number | Ja | _**Samme som opprinnelig utbetaling men med negativt fortegn**_
melding | String | Ja | Samme som opprinnelig utbetaling

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Samme som opprinngelig utbetaling.
artskonto | String | Samme som opprinngelig utbetaling. 
kapPost | String | Samme som opprinngelig utbetaling.
belop | Number | _**Samme som opprinnelig utbetaling men med negativt fortegn**_
 
