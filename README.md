# Helserefusjon-utbetaling: API og meldingsdokumentasjon

## Meldinger
Meldinger |  Beskrivelse
-----|------------
[EKSTERN_UTBETALINGSOPPDRAG_REQUEST](docs/EKSTERN_UTBETALINGSOPPDRAG_REQUEST.md) | Ekstern request
[EKSTERN_UTBETALINGSOPPDRAG_RESPONSE](docs/EKSTERN_UTBETALINGSOPPDRAG_RESPONSE.md) | Ekstern response
[UTBETALINGSOPPDRAG](docs/UTBETALINGSOPPDRAG.md) | et UtbetalingsOppdrag fra et forsystem
[UTBETALINGSKVITTERING](docs/UTBETALINGSKVITTERING.md) | en UtbetalingsKvittering mottatt fra ekstern part, lagret i helse-utbetaling 

## Felles meldingsdefinisjoner
Meldinger |  Beskrivelse
-----|------------
[Ordre_meldingsdefinisjon](docs/Ordre_meldingsdefinisjon.md) | Ordremelding
[Utbetaling_meldingsdefinisjon](docs/Utbetaling_meldingsdefinisjon.md) | Utbetalingsmelding
[UtbetalingEndret_meldingsdefinisjon](docs/UtbetalingEndret_meldingsdefinisjon.md) | Endringsmelding

(Arbeidskatalog for meldingsendringer: [docs/under_arbeid](docs/under_arbeid))

### Meldinger fra e-resept
Meldinger |  Beskrivelse
-----|------------
[ERESEPT_UTBETALING](docs/eresept/ERESEPT_UTBETALING.md) | Utbetaling fra Eresept
[ERESEPT_ENDRET_UTBETALING](docs/eresept/ERESEPT_ENDRET_UTBETALING.md) | Endret utbetaling fra Eresept
[ERESEPT_ORDRE_HRESEPT_FAKTURA](docs/eresept/ERESEPT_ORDRE_HRESEPT_FAKTURA.md) | Hresept faktura fra Eresept
[ERESEPT_ORDRE_RABATT_AVTALE_FAKTURA](docs/eresept/ERESEPT_ORDRE_RABATT_AVTALE_FAKTURA.md) | Rabatt avtale faktura fra Eresept

### Meldinger fra kuhr
Meldinger |  Beskrivelse
-----|------------
[Fakturamelding FBV](docs/kuhr/FBV_FAKTURAMELDING.md) | Utsendelse av fakturaer for FBV
[KUHR_ENDRET_UTBETALING](docs/kuhr/KUHR_ENDRET_UTBETALING.md) | Endret utbetaling fra KUHR
[KUHR Utbetalingsmelding](docs/kuhr/KUHR_UTBETALINGSMELDING.md) | Utbetaling fra KUHR

### Meldinger fra frikort (under utvikling)
Meldinger |  Beskrivelse
-----|------------
[FRIKORT_UTBETALING](docs/frikort/FRIKORT_UTBETALING.md) | Utbetaling fra Frikort
