# Umsetzung – 20 Schritte

## Phase 1: Vorbereitung

### 1. Typenschild Wille-NSP → Chromat-Check
- Typenschild der vorhandenen Wille-Nachtspeicheröfen fotografieren
- HEA anrufen: 030 300199-0
- Ergebnis: chromatfrei → Steine als Speichermasse im Kamin verwenden
- Ergebnis: chromathaltig → Steine entsorgen, frische Schamotte kaufen

### 2. Schornsteinfeger-Termin
- Bezirksschornsteinfeger kontaktieren
- Beide Schornsteinschächte begutachten lassen
- Kaminstandort im Wohnzimmer besprechen
- Ggf. Schornsteinsanierung klären (Edelstahlrohr)

### 3. BEG-Förderantrag KfW 458 – VOR Kauf!
> ⚠️ Ohne Förderzusage vor Bestellung/Beauftragung kein Zuschuss!
- Antrag online bei „Meine KfW" stellen
- Unterlagen: iSFP, Heizlastberechnung, Angebote
- Förderzusage abwarten → DANN erst bestellen

### 4. Heizlastberechnung DIN EN 12831
- Nach Dämmplanung (Std. B) berechnen lassen
- Bestätigt: 9 kW WP + 7 kW Kamin + 3 kW Heizstab = ausreichend
- Ggf. Energieberater im Rahmen des iSFP

## Phase 2: Rückbau & Rohbau

### 5. Nachtspeicher demontieren
- Strom abstellen, Nachtspeicheröfen abbauen
- Steine aufheben (falls chromatfrei → Kamin-Speichermasse)
- Asbest/PCB: kein Risiko bei Bj. ~1995

### 6. Dämmung Standard B
- Fassade, Dach, Kellerdecke dämmen
- Zielwert: 50–60 W/m² Heizlast
- Separater BAFA-Antrag: BEG Einzelmaßnahmen, 15 % + 5 % iSFP = 20 %

### 7. Elektrik komplett neu
- 400V Zuleitung für LG Therma V (Außenbereich → HWR)
- Notstromkreis definieren (Pumpen, Shellys, HA-Server)
- Kabel für Shelly Wall Displays in jeden Raum (230V + neutral)
- RS-485 Kabel (geschirmt, 2-Draht) von LG-Standort → HWR Hutschiene

### 8. Wandnischen stemmen für UP-Verteilerschränke
- 3 Nischen (EG, 1.OG, 2.OG) für Unterputz-Verteilerschränke
- Ausreichend dimensionieren (5-fach bzw. 6-fach Verteiler + Stellantriebe)

## Phase 3: Fußbodenheizung

### 9. XPS-Platten + Heizrohre eindrücken
- Nordic FOS XPS 500 Rillenplatten verlegen (230 m²)
- PE-RT 16x2 Heizrohre eindrücken (1.400 m)
- Max. 100 m pro Kreis, Verlegeabstand 15 cm
- Randdämmstreifen nicht vergessen

### 10. Verteiler UP + Verbundrohr 32x3
- 3 Verteiler in UP-Schränke montieren
- Heizrohre an Verteiler anschließen (Eurokonus-Klemmverschraubungen)
- Steigleitung Alu-Verbundrohr 32x3 verlegen, pressen, isolieren (Armaflex)
- Rohrschellen mit Gummieinlage (Körperschall-Entkopplung)

## Phase 4: Technikraum

### 11. Puffer + Hydraulik + Heizstab im HWR
- Pufferspeicher 300–500 L aufstellen
- MAG 25 L, Sicherheitsgruppe montieren
- Heizkreispumpe (Grundfos/Wilo) installieren → Notstromkreis!
- Mischer/Stellventil (VL 35 °C) einbauen
- Strangregulierventile (3x, pro Etage)
- Heizstab 3 kW einschrauben (1½" Muffe)
- Schlammabscheider/Magnetitfilter am Rücklauf
- Schnellentlüfter am Steigrohr 2.OG
- Mikroblasenabscheider am Puffer-Vorlauf

### 12. LG Therma V aufstellen
- Betonfundament gießen (Eigenleistung)
- Vibrationsdämpfer/Bodenständer montieren
- LG Therma V R290 auf Fundament setzen
- Panzerschläuche DN25 1" anschließen (akustische Entkopplung)
- Alu-Verbundrohr 32x3 durch Hauswand → Puffer

### 13. Elektriker: 400V + Notstrom + RS-485
- 400V-Anschluss LG Therma V
- Notstromkreis verdrahten (Pumpen, Shellys, HA-Server)
- RS-485 Kabel von LG-Außeneinheit → PUSR DR302 auf Hutschiene

## Phase 5: Inbetriebnahme Heizung

### 14. System befüllen, entlüften, Druckprobe
- Leitungswasser durch **Enthärtungspatrone** leiten (17 °dH!)
- **Korrosionsschutzmittel** (Fernox F1) zugeben
- System komplett entlüften (alle Verteiler, alle Kreise)
- Druckprobe: min. 3 bar, 24 Stunden halten
- Auf Leckagen prüfen an allen Pressfittings

### 15. Kratki MBM PW einbauen
- Kaminverkleidung / Bausatz aufbauen
- Speichermasse einsetzen (Schamotte oder NSP-Steine)
- Rauchrohr 200 mm anschließen
- TAS (Thermische Ablaufsicherung) montieren – PFLICHT!
- Rücklaufanhebungsgruppe (min. 55–60 °C)
- Ladepumpe → Notstromkreis anschließen
- Externe Verbrennungsluft 125 mm anschließen

### 16. Schornsteinfeger Abnahme
- Termin vereinbaren
- Abnahme Kamin + Schornstein
- Freigabe zum Betrieb

## Phase 6: Smart Home

### 17. Shelly Wall Displays + Stellantriebe
- 12 Shelly Wall Displays Black in den Räumen montieren
- 12 Shelly BLU H&T Black koppeln
- 16 Stellantriebe (230V NC) an Verteiler anschließen
- Relais-Verdrahtung: Wall Display → Stellantrieb

### 18. Hutschiene bestücken
- PUSR DR302 Modbus Gateway aufschnappen
- Shelly Pro 1 aufschnappen
- Shelly Pro Sensor Add-on anstecken
- 7x DS18B20 verdrahten (1-Wire, 2 Kanäle)
- DIN-Netzteil 12V für Gateway
- Ethernet-Patchkabel → Switch

### 19. Home Assistant konfigurieren
- Modbus TCP Integration: LG Therma V Register
- Shelly Integration: Wall Displays, Sensoren, Pro 1
- Dashboard bauen: Puffer-Schichtung, WP-Status, Kamin-Status
- Energiemonitoring: COP, Stromverbrauch WP, PV-Eigenverbrauch

### 20. Hydraulischer Abgleich + Automatisierungen
- Topmeter an jedem Verteiler einstellen (Durchfluss pro Kreis)
- HA Automatisierungen:
  - Nachtabsenkung (22:00 → -2 °C, Silent Mode)
  - PV-Heizstab-Steuerung
  - Kamin-Erkennung (VL Kamin > 60 °C → WP runterfahren)
  - Notstrom-Modus (Netz weg → WP aus, Kamin-Meldung)
  - Abwesenheitserkennung
