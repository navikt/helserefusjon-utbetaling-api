# FRIKORT Håndtering av koder i kvitteringer

Dokumentasjon av hvilke kombinasjoner av statuskoder og feilkoder i kvitteringer som støttes/håndteres av Frikortløsningen. Manuell håndtering av andre status-/feilkoder beskrives ikke her.

Oppdragets status i Frikort | Statuskode | Feilkode | Betyr alltid ugyldig kontonummer? | Betyr alltid manglende kontonummer? | Ny status i Frikort? | Frikort sender Mangler gyldig kontonummer-brev? 
----------------------------|------------|----------|-----------------------------------|-------------------------------------|----------------------|------------------------------------------------
UTBETALES | 3905 | * | Nei | Nei | PARKERT | Nei
_UTBETALES | 3906 | 103 | Nei | Nei | PARKERT | Nei_
UTBETALES | 3906 | 19 | Ja | Nei | PARKERT | Ja
UTBETALES | 3906 | 201 | Ja | Nei | PARKERT | Ja
UTBETALES | 3912 | 19 | Ja | Nei | PARKERT | Ja
UTLIGNES | 3921 | * | N/A | N/A | UTLIGNET | Nei
* | 3913 | * | N/A | N/A | UTBETALT | Nei
