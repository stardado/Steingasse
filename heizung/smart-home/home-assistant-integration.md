# Smart Home – Home Assistant Integration

## Hutschiene HWR-Verteilerschrank

| Gerät | Funktion | Anbindung |
|-------|----------|-----------|
| PUSR DR302 | Modbus RS-485 → Ethernet Gateway | LAN → HA Modbus TCP |
| Shelly Pro 1 | Host für Sensor Add-on + Relais Heizstab | WLAN/LAN → HA Shelly |
| Shelly Pro Sensor Add-on | 2x 1-Wire Bus, 7x DS18B20 | Intern via Shelly Pro 1 |
| DIN-Netzteil 12V | Versorgung Modbus Gateway | 230V → 12V DC |

## Wärmepumpe LG Therma V R290 → Modbus TCP

### Signalkette

```
LG Therma V (RS-485 Modbus RTU)
  → geschirmtes 2-Draht RS-485 Kabel (5-8 m, durch Hauswand)
  → PUSR DR302 (Hutschiene, konvertiert RTU → TCP)
  → Ethernet-Patchkabel → Switch/Router
  → Home Assistant: Modbus TCP Integration
```

### Konfiguration

- Baudrate: 9600
- Parity: N
- Modbus-Adresse: 1
- HA: `modbus:` Integration mit IP-Adresse des PUSR DR302

### Auslesbare Register (Auswahl)

- Vorlauf-/Rücklauf-Temperatur
- Außentemperatur
- Kompressor-Status, Betriebsmodus
- Leistungsaufnahme, COP
- Fehlercodes

### Steuerbare Register

- Solltemperatur VL
- Betriebsmodus (Heizen/Kühlen/Auto)
- Silent Mode ein/aus
- WP ein/aus

Fertige YAML-Configs: [HA Community](https://community.home-assistant.io/t/lg-therma-v-heat-pump-modbus-control/496233)

## Temperatursensorik → Shelly Pro Sensor Add-on

### 7x DS18B20 (1-Wire / OneWire)

Jeder DS18B20 hat eine eindeutige UUID → mehrere Sensoren auf einem Bus, automatisch erkannt.

**Kanal 1 (5 Sensoren):**
- Puffer oben, Puffer mitte, Puffer unten
- VL Heizkreis (nach Mischer), RL Heizkreis

**Kanal 2 (2 Sensoren):**
- VL Kaminkreis, RL Kaminkreis

### Kabellängen

| Sensor | Kabellänge |
|--------|-----------|
| Puffer (3x) | 1 m |
| VL/RL Heizkreis | 1–2 m |
| VL Kaminkreis | 3 m |
| RL Kaminkreis | 2 m |

## Raumregelung → Shelly Wall Display + BLU H&T

12 Räume mit jeweils:
- **Shelly Wall Display Black:** Touchscreen-Thermostat, 230V Relais (schaltet Stellantriebe direkt), WLAN → HA
- **Shelly BLU H&T Black:** Bluetooth Temperatur + Feuchte Sensor

### Regellogik

1. BLU H&T misst Raumtemperatur + Feuchte → Bluetooth → Wall Display
2. Wall Display vergleicht Ist vs. Soll → Relais auf/zu → Stellantrieb öffnet/schließt
3. HA übernimmt übergeordnete Steuerung: Zeitpläne, Abwesenheit, Nachtabsenkung

## Heizstab-Steuerung (PV-Überschuss)

```
Home Assistant: PV-Überschuss > 3 kW UND Puffer < 55 °C
  → Shelly Pro 1 Relais EIN → Heizstab 3 kW → Puffer laden
  
Home Assistant: PV-Überschuss < 1 kW ODER Puffer > 65 °C
  → Shelly Pro 1 Relais AUS → Heizstab aus
```

## HA Automatisierungen (Beispiele)

### Kamin-Erkennung
```yaml
# Wenn VL Kaminkreis > 60°C → Kamin brennt
# → WP-Solltemperatur reduzieren (Puffer wird vom Kamin geladen)
```

### Nacht-Modus
```yaml
# 22:00: LG Silent Mode aktivieren via Modbus
# 22:00: VL-Solltemperatur -2°C (Nachtabsenkung)
# 06:00: Normalmodus
```

### Notstrom-Modus
```yaml
# Wenn Netzstrom = 0 UND PV+Akku aktiv:
# → WP deaktivieren (zu viel Leistung)
# → Nur Kreis 2 (Kamin) + Kreis 3 (FBH) laufen
# → Benachrichtigung: "Kamin anzünden!"
```
