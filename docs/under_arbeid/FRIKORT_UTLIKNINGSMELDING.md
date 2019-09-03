# FRIKORT Utlikningsmelding
Utlikningsmelding fra Frikort for å utlikne tidligere utbetalinger.

## Ressurser
_**(Hardkodede konstanter er markert med bold-kursiv)**_

## Teknisk beskrivelse
**Følgende felter er nye/endret ift opprinnelig utbetalingsmelding:**
* forsystemRef: Når er det behov for å løpenr? Vil vi noen gang sende en utlikningsmelding på nytt? Altså at det faktisk opprettes en ny utlikningsmelding? 
* bilagnummer: Denne er grei.
* bilagsart: Er UA ved foreldelse?
  * Fra meldingsbeskrivelsen: Skal være: UF - for utlingning på grunn av feil. UA - for avskrivning av utbetalinger som er mer enn tre år gamle. De nye bilagsartene må etableres i UBW.
* belop: Beløp med motsatt fortegn av beløpet på den opprinnelige utbetalingen.
* Status: Dette feltet finnes ikke og skal være blank ihht meldingsbeskrivelsen. Trenger vi å ta det med?
* Utbetalingstype: Denne står i meldingsbeskrivelsen, men jeg kan ikke se at har denne med på opprinnelig utbetalingsmelding. 
  * Fra meldingsbeskrivelsen: Som for den opprinnelige utbetalingen.
* Kontering.belop: Skal ha motsatt fortegn.
  
**Andre ting å avklare:**
* Kan vi forenkle meldingen betraktelig? Hvilke felter er det egentlig nødvendig å sende med?
  * Trenger vi alle feltene fra oppdraget?
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
bilagnummer | String | Ja | _**Bilagsnummeret til utbetalingen man skal utligne. Nytt felt**_.
bilagsart | String | Ja | _**Skal være: UF - for utlingning på grunn av feil. UA - for avskrivning av utbetalinger som er mer enn tre år gamle. De nye bilagsartene må etableres i UBW.**_
forfallsdato | Date| Ja | Dagens dato. Format er ISO8601: ``yyyy-MM-ddTHH:mm:ss.SSSZ``. _Todo: Avklare omkring neste virkedag._ 
belop | Number | Ja | _**Beløp med motsatt fortegn av beløpet på den opprinnelige utbetalingen.**_
melding | String | Ja | Teksten "Refusjon egenandel(er) frikort 2018" (År blir generert dynamisk).
konteringer | Array:Konteringslinje ||

### Konteringslinje
Felt | Type | Beskrivelse / Verdi
-----|----- |--------------------
linjenr | Number | Starter på 0
artskonto | String | _*874*_ for betaling til norsk bank, _*874*_ for betaling til bank i utlandet. 
kapPost | String | _*275270*_ for tak 1. _*275271*_ for tak 2. **Todo** Det kan være at det skal være andre verdier også, dette skal avklares.
belop | Number | _**Beløp med motsatt fortegn av den opprinnelige utbetalingen.**_
 
 
# Eksempler på utfylling av utlikningsmelding
_**TODO**_