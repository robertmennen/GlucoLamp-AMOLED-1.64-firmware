# GlucoLamp AMOLED 1.64: firmware

Deze repo bevat alleen de **firmwarebestanden** (onder *Releases*) voor het glucosescherm (GlucoLamp) op een Waveshare ESP32-S3-Touch-AMOLED-1.64. De broncode staat in een privé-repo.

Elke release bevat:

- `firmware.bin`: de firmware
- `firmware.bin.sha256`: het controlegetal (SHA-256) van de firmware

Het scherm kijkt **elk uur** of er een nieuwe release is. Op de instelpagina van het scherm kies je zelf of je hem installeert. Een release met **(belangrijk)** in de titel verschijnt op het scherm als oranje balk ("Belangrijke update"), in plaats van alleen een blauw pijltje.

## Mededelingen: `melding.json`

Het scherm leest ook elk uur het bestand `melding.json` in de hoofdmap van deze repo. Staat het er niet, dan is er geen mededeling. Voorbeeld:

```json
{
  "id": "2026-12-01-dexcom",
  "niveau": "dringend",
  "tekst": "Dexcom wijzigt zijn dienst",
  "uitleg": "Vanaf 1 maart werkt het inloggen anders. Installeer v1.3.0 via de instelpagina.",
  "vanVersie": "v1.0.0",
  "totVersie": "v1.2.9",
  "tot": "2027-03-31"
}
```

| Veld | Betekenis |
|---|---|
| `id` | unieke naam; een nieuw id is een nieuwe mededeling |
| `niveau` | `info` (blauwe balk) of `dringend` (oranje balk) |
| `tekst` | kort, voor de balk op het scherm |
| `uitleg` | langer, verschijnt na een tik op de balk (optioneel) |
| `vanVersie`, `totVersie` | alleen voor die firmwareversies, grenzen inbegrepen (optioneel) |
| `tot` | tot en met die dag, als JJJJ-MM-DD (optioneel) |

- Een **info**-mededeling komt na het wegtikken niet meer terug; een **dringende** komt na 24 uur terug, zolang ze geldt.
- Intrekken: verwijder het bestand (of maak het `id` leeg).
- Het kan tot een uur duren voor het scherm een wijziging ziet. De knop *Controleren op updates* op de instelpagina haalt ze meteen op (GitHub zelf kan nog enkele minuten de oude versie geven).
- Letters met accenten (é, ë, ï, ...) mogen. Gebruik geldige JSON (dubbele aanhalingstekens, geen komma na het laatste veld).
