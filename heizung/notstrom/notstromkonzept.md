# Notstromkonzept

## Grundidee

Bei Stromausfall fällt die Wärmepumpe aus (9 kW Leistungsaufnahme = zu viel für Notstrom). Der Kamin übernimmt die Heizung, und die kritischen Pumpen laufen über PV + Akku weiter.

## Notstromkreis (~200 W)

Folgende Verbraucher laufen am Notstromkreis (PV + Akku-gespeist):

| Verbraucher | Leistung |
|------------|----------|
| Ladepumpe Kaminkreis (Kreis 2) | ~50 W |
| Heizkreispumpe FBH (Kreis 3) | ~50 W |
| Stellantriebe (16x NC, nur Halteenergie) | ~30 W |
| Shelly Wall Displays (12x) | ~24 W |
| Shelly Pro 1 + Sensor Add-on | ~5 W |
| PUSR DR302 Gateway | ~3 W |
| Home Assistant Server | ~30 W |
| **Gesamt** | **~200 W** |

## Betriebsmodi bei Stromausfall

### Stufe 1: PV + Akku verfügbar (Tag, Sonne)

- WP aus (zu viel Leistung)
- Kamin anfeuern → 7 kW Wasserleistung → Puffer → FBH im ganzen Haus
- Ladepumpe + Heizkreispumpe laufen über Notstrom
- HA steuert Stellantriebe und überwacht Temperaturen
- Heizstab ggf. an (wenn PV-Überschuss vorhanden)

### Stufe 2: Nur Akku (Nacht, kein PV)

- Wie Stufe 1, aber Akku-Kapazität begrenzt
- Bei 200 W Notstromlast: 5 kWh Akku = 25 Stunden Laufzeit
- Puffer (300-500 L) speichert Wärme für mehrere Stunden nach
- Kamin heizt abends/nachts, Puffer überbrückt die Zeit dazwischen

### Stufe 3: Worst Case (kein Strom, kein PV, kein Akku)

- Nur Kamin: **5 kW Strahlungswärme direkt ins Wohnzimmer**
- Kein Strom nötig – nur Holz und Streichholz
- Wasserseite (7 kW) funktioniert NICHT ohne Pumpe
- TAS schützt den Kamin vor Überhitzung (öffnet bei ~95°C, kaltes Wasser fließt nach)
- Wohnzimmer bleibt warm, Rest des Hauses kühlt langsam ab

## Elektrik

Der Elektriker muss folgende Kreise separat am Notstrom-Einspeisepunkt anschließen:

1. Steckdosen/Festanschluss Ladepumpe Kamin
2. Steckdose/Festanschluss Heizkreispumpe
3. Spannungsversorgung Stellantriebe (Verteilerebene, je Etage)
4. Shelly-Netzteile und Hutschienen-Geräte im HWR
5. HA-Server Steckdose

Die 400V-Versorgung der LG Therma V ist NICHT am Notstromkreis!
