# Wärmepumpe – LG Therma V R290 Monobloc 9 kW

**Entscheidung: FINAL – R290 (kein R32, kein AVARMA)**

## Gewähltes Modell

- **Modell:** LG Therma V R290 Monobloc HM093HF.UB60
- **Kontrollbox:** PHCS0.ENCXLEU (KEINE Hydrobox – eigene Hydraulik mit Puffer)
- **Leistung:** 9 kW (bivalent mit Kamin + Heizstab ausreichend)
- **Spannung:** 400V 3-phasig
- **Kältemittel:** R290 (Propan), GWP 3, 1,2 kg Füllmenge

## Technische Daten

| Parameter | Wert |
|-----------|------|
| Heizleistung A7/W35 | 9 kW |
| SCOP bei 35 °C | >5,0 |
| SCOP bei 55 °C | 3,86 |
| Energieeffizienzklasse | A+++ (bei 35 °C und 55 °C) |
| Max. Vorlauftemperatur | 75 °C |
| Min. Außentemperatur | -28 °C |
| Schallleistungspegel | 49 dB(A) |
| Schalldruckpegel bei 3 m | 31 dB(A) |
| Höhe | ca. 1.000 mm (1 Ventilator) |
| Integrierte Komponenten | Umwälzpumpe, Plattenwärmetauscher, MAG, Sicherheitsventile |
| Schnittstellen | Modbus RS-485 (integriert), WiFi (Modul optional) |
| SG-Ready | Ja |

## Warum R290 und nicht R32

| Kriterium | R290 (gewählt) | R32 (verworfen) |
|-----------|---------------|----------------|
| GWP | 3 | 675 |
| Effizienzbonus BEG | +5 % (55 % statt 50 %) | Kein Bonus |
| Schallleistung | 49 dB(A) | 57 dB(A) |
| COP A7/W35 | >5,0 | ~4,6 |
| Max. Vorlauf | 75 °C | 65 °C |
| F-Gas-Verordnung | Nicht betroffen | Wird eingeschränkt |
| Konkret: Fördervorteil | ca. 615 EUR mehr Zuschuss | – |

## Warum 9 kW statt 12 kW

- Heizlast nach Dämmung Std. B: 10,5–12,5 kW
- 9 kW WP deckt ca. 95 % der Heiztage allein ab
- An den kältesten 5 % der Tage: Kamin (7 kW Wasser) als Backup
- Zusätzlich: Heizstab (3 kW) nutzt PV-Überschuss
- Leicht unterdimensionierte WP = weniger Takten, besserer COP, längere Lebensdauer
- Günstiger als 12 kW → passt ins Budget unter 5.000 EUR

## Verworfene Alternativen

| Modell | Grund für Ablehnung |
|--------|-------------------|
| Hofman AVARMA 290 | 65 dB(A) zu laut, Service nur per E-Mail |
| LG Therma V R32 Monobloc S2 | R32 = kein Effizienzbonus, lauter, niedrigerer COP |
| Panasonic Aquarea L R290 | Gute Alternative (SCOP 4,84, 44 dB(A) Silent), aber LG hat bessere Modbus-Integration |
| Midea M-Thermal Arctic R290 | Günstig, aber lauter (55–58 dB), Service unklar |

## Modbus-Integration in Home Assistant

Die LG hat eine integrierte RS-485 Modbus-Schnittstelle. Anbindung über:

1. RS-485 Kabel (geschirmt, 2-Draht) von LG Außeneinheit → HWR
2. PUSR DR302 Modbus Gateway (Hutschiene) → RS-485 zu Ethernet (Modbus TCP)
3. Home Assistant Modbus TCP Integration → IP des Gateways + LG Register

Fertige YAML-Configs sind in der HA Community verfügbar. Auslesbar: Temperaturen, COP, Leistung, Status, Betriebsmodus. Steuerbar: Solltemperatur, Modus, Silent Mode.

## Stiftung Warentest

- Note: **Gut (2,4)** – Stand 2024
- Positiv: Bedienung, Verarbeitung, Heizleistung bei Kälte
- Negativ: Service/Kundendienst in DE kleiner als Viessmann/Buderus
- AHR Innovationspreis 2025

## Links

- [LG Therma V R290 Monobloc](https://lgthermav.de/produkte-losungen/warmepumpen/r290-monobloc/)
- [Datenblatt HM093HF.UB60](https://www.heizungsdiscount24.de/waermepumpen/lg-therma-v-r290-monobloc-luft-wasser-waermepumpe-hm123hfub60-400v-12-kw.html)
- [HA Community: LG Therma V Modbus](https://community.home-assistant.io/t/lg-therma-v-heat-pump-modbus-control/496233)
