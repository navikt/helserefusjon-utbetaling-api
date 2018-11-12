# Ekstern UtbetalingsOppdrag request

## Ressurser
### Request
Felt | Type | Beskrivelse / Verdi
-----|------ |------------
size | Number | maks antall oppdrag som skal hentes, valgfri default = 10 
start| Number | hvilken id det skal startes å, inklusive, valgfri default = 1
systemId | Number | id på forsystem, valgfri
type| String | UTBETALING, ORDRE eller AVSTEMMING, valgfri


## Eksempel

```json
{
  "size": 10,
  "start": 1109,
  "systemId": 14,
  "type": "UTBETALING"
}
```

