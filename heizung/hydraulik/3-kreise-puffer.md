# Hydraulik – 3-Kreise-System mit Pufferspeicher

## Übersicht

Zentraler Pufferspeicher (300–500 L) mit drei getrennten Pumpenkreisen und Heizstab.

```
                    ┌─────────────────────┐
                    │   PUFFER 300-500 L  │
                    │                     │
   Kamin-VL  ──►   │ ████ OBEN (Kamin)   │
                    │                     │
   WP-VL     ──►   │ ████ MITTE (WP)     │   ──► HK-VL (35°C) → Mischer → FBH
                    │                     │
                    │ ████ UNTEN          │   ◄── HK-RL (28°C)
   Kamin-RL  ◄──   │                     │
   WP-RL     ◄──   └─────────────────────┘
                    │ Heizstab 3 kW (PV)  │
                    └─────────────────────┘
```

## Kreis 1: Wärmepumpe (nur Netzbetrieb)

```
LG Therma V R290 → integrierte Pumpe → Panzerschlauch DN25 1"
  → Alu-Verbundrohr 32x3 → Puffer MITTE → Rücklauf → zurück zur LG
```

- Die LG hat eine integrierte Umwälzpumpe – KEINE separate WP-Kreispumpe nötig
- Panzerschläuche am LG-Anschluss für akustische Entkopplung
- Fällt bei Stromausfall komplett aus

## Kreis 2: Kamin (Notstromkreis!)

```
Kratki MBM PW → Ladepumpe → Rücklaufanhebung (min. 55°C)
  → Alu-Verbundrohr 32x3 → Puffer OBEN → Rücklauf → zurück zum Kratki
```

- Eigene Ladepumpe am Notstromkreis (PV + Akku)
- Rücklaufanhebung PFLICHT (sonst Kondensation/Versottung)
- TAS (Thermische Ablaufsicherung) PFLICHT

## Kreis 3: Heizkreis FBH (Notstromkreis!)

```
Puffer → sep. Heizkreispumpe → Mischer (35°C VL-Begrenzung)
  → Alu-Verbundrohr 32x3 Steigleitung → 3x Verteiler UP (EG/1.OG/2.OG)
  → 16 FBH-Kreise → Rücklauf (28°C) → zurück zum Puffer UNTEN
```

- Separate Heizkreispumpe (Grundfos/Wilo) – unabhängig von LG-Pumpe!
- Mischer begrenzt VL auf 35 °C für FBH
- 3 Strangregulierventile (pro Etage) für hydraulischen Abgleich
- Am Notstromkreis → läuft auch bei Stromausfall mit Kamin-Wärme

## Heizstab (PV-Überschuss)

- 3 kW Einschraubheizkörper 1½" im Puffer (mitte/oben)
- Geschaltet via Shelly Pro 1 (gleicher wie Sensor-Host)
- Home Assistant steuert: PV-Überschuss vorhanden UND Puffer nicht voll → Heizstab EIN

## Verrohrung

- **Anbindeleitungen:** Alu-Verbundrohr 32x3 PE-RT/Al/PE-RT
- **Verbindungen:** Pressfitting TH (Akku-Presszange)
- **Isolierung:** Armaflex 25 mm Dämmung, Outdoor UV-beständig für Außenbereich
- **Entlüftung:** Schnellentlüfter am höchsten Punkt (2.OG), Mikroblasenabscheider am Puffer-VL

## Pufferspeicher Anforderungen

- Volumen: 300–500 L
- Min. 6 Muffen auf verschiedenen Höhen (oben, mitte, unten je VL+RL)
- 1½" Muffe für Heizstab
- Muffe für Schlammabscheider/Magnetitfilter am Rücklauf

## Temperaturfühler (7x DS18B20 via Shelly Pro Sensor Add-on)

| Position | Kanal | Funktion |
|----------|-------|----------|
| Puffer oben | 1-Wire Ch.1 | Kamin-Schichtung, Ladezustand |
| Puffer mitte | 1-Wire Ch.1 | WP-Einspeisung, Heizstab-Steuerung |
| Puffer unten | 1-Wire Ch.1 | Rücklauf-Temperatur, WP-Effizienz |
| VL Heizkreis | 1-Wire Ch.1 | Mischer-Kontrolle, FBH Vorlauf |
| RL Heizkreis | 1-Wire Ch.1 | Rücklauf FBH, Spreizung berechnen |
| VL Kaminkreis | 1-Wire Ch.2 | Kamin-Leistung überwachen |
| RL Kaminkreis | 1-Wire Ch.2 | Rücklaufanhebung kontrollieren |
