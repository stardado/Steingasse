# Heizungsprojekt – Steingasse, 55430 Oberwesel

**Stand: Mai 2026 – Version 8**

Komplettsanierung der Heizungsanlage: Nachtspeicheröfen raus, Fußbodenheizung + Wärmepumpe + wassergeführter Kamin rein. Vollständige Smart-Home-Integration mit Home Assistant.

## Systemkonzept

Bivalentes Heizsystem mit drei Wärmequellen und drei Energieträgern:

| Wärmequelle | Leistung | Energieträger | Notstrom |
|------------|----------|--------------|----------|
| LG Therma V R290 Monobloc 9 kW | 9 kW | Netzstrom | ❌ |
| Kratki MBM PW Kamin wassergeführt | 7+5 kW | Holz | ✅ |
| Heizstab im Puffer | 3-6 kW | PV-Solarstrom | ✅ |

**Maximale Bivalenzleistung:** 22 kW (9+7+6)

## Hydraulik: 3 Pumpenkreise

1. **Kreis WP:** LG → int. Pumpe → Panzerschlauch → Verbundrohr 32x3 → Puffer mitte → zurück (nur Netzbetrieb)
2. **Kreis Kamin:** Kratki → Ladepumpe → Rücklaufanhebung → Verbundrohr 32x3 → Puffer oben → zurück (**Notstromkreis!**)
3. **Kreis Heizung:** Puffer → sep. Heizkreispumpe → Mischer 35°C → Verbundrohr 32x3 → 3x Verteiler UP → zurück (**Notstromkreis!**)

## Dokumentation

| Dokument | Beschreibung |
|----------|-------------|
| [Kostenplan v8](kostenplan/kostenplan-v8.md) | Detaillierte Kostenschätzung aller Positionen |
| [Wärmepumpe](waermepumpe/lg-therma-v-r290.md) | LG Therma V R290 Monobloc – Spezifikationen & Entscheidung |
| [Kamin](kamin/kratki-mbm-pw.md) | Kratki MBM PW wassergeführt – Details & Hydraulik |
| [Fußbodenheizung](fussboden-heizung/nordic-fos-xps.md) | Nordic FOS XPS Trockenbausystem – Planung & Verlegung |
| [Hydraulik](hydraulik/3-kreise-puffer.md) | 3-Kreise-Hydraulik mit Pufferspeicher |
| [Smart Home](smart-home/home-assistant-integration.md) | HA Integration: Modbus, Shelly, Sensorik |
| [Wasseraufbereitung](wasseraufbereitung/vdi-2035.md) | VDI 2035 bei 17 °dH Wasserhärte |
| [Förderung](foerderung/kfw-458-beg.md) | KfW 458 BEG Heizungstausch – 55 % Zuschuss |
| [Notstrom](notstrom/notstromkonzept.md) | Notstromkonzept mit PV + Akku |
| [Umsetzung](umsetzung/schritt-fuer-schritt.md) | 20 Schritte zur Umsetzung |

## Offene Punkte

- [ ] Typenschild Wille-NSP → HEA Chromat-Check (030 300199-0)
- [ ] Schornsteinfeger-Termin (Schächte prüfen, Kaminstandort klären)
- [ ] Heizlastberechnung DIN EN 12831 → bestätigt 9 kW bivalent ausreichend

## Erledigte Punkte

- [x] Wasserhärte Oberwesel: 17 °dH bestätigt, Aufbereitung eingeplant
- [x] WP-Entscheidung: LG Therma V R290 final (kein R32, kein AVARMA)
- [x] Verrohrung: Alu-Verbundrohr 32x3 (kein Sani-Flex)
- [x] Sensorik: Shelly Pro Sensor Add-on + 7x DS18B20 via OneWire
- [x] Modbus: PUSR DR302 Hutschiene RS-485/Ethernet Gateway
- [x] Förderquote: 55 % (30 % Grund + 20 % Klima + 5 % R290-Effizienz)

## Kosten (Kurzübersicht)

| Position | EUR |
|----------|-----|
| Gesamt vor Förderung | 16.051 – 17.401 |
| abzgl. KfW 55 % | -6.958 |
| **Eigenanteil** | **ca. 9.093 – 10.443** |
