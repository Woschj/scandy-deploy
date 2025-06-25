# Scandy Deployment Repository

Dieses Repository enthält die Deployment-Dateien für die Scandy-Anwendung.

## 🚀 Ein-Klick-Installation

### Empfohlene Methode (funktioniert garantiert):
```bash
curl -sSL https://raw.githubusercontent.com/Woschj/scandy-deploy/main/install.sh -o install.sh && chmod +x install.sh && ./install.sh
```

### Alternative Methode (falls die erste nicht funktioniert):
```bash
# Sichere Installation mit Cache-Umgehung
curl -sSL -H "Cache-Control: no-cache" https://raw.githubusercontent.com/Woschj/scandy-deploy/main/install.sh -o install.sh && chmod +x install.sh && ./install.sh
```

## 📋 Voraussetzungen

- **Docker** muss installiert und gestartet sein
- **Docker Compose** muss installiert sein
- Mindestens **2GB freier Speicherplatz**

## 🔧 Was wird installiert?

Die Installation erstellt automatisch:

- **MongoDB 7.0** Container (Port 27017)
- **Mongo Express** Web-UI (Port 8081)
- **Scandy App** Container (Port 5000)
- **Verwaltungsskripte** (start.sh, stop.sh, update.sh, backup.sh)

## 🌐 Zugriff nach der Installation

Nach erfolgreicher Installation ist Scandy verfügbar unter:

- **Hauptanwendung:** http://localhost:5000
- **MongoDB Web-UI:** http://localhost:8081
- **MongoDB direkt:** localhost:27017

## 🛠️ Verwaltung

Im Projektverzeichnis stehen folgende Skripte zur Verfügung:

```bash
./start.sh    # Container starten
./stop.sh     # Container stoppen
./update.sh   # Container aktualisieren
./backup.sh   # Backup erstellen
```

## 🔐 Standard-Zugangsdaten

- **MongoDB Admin:** admin / scandy123
- **Mongo Express:** admin / scandy123

## 📁 Projektstruktur

```
scandy_project/
├── docker-compose.yml    # Container-Konfiguration
├── mongo-init/           # MongoDB Initialisierung
├── start.sh             # Start-Skript
├── stop.sh              # Stop-Skript
├── update.sh            # Update-Skript
└── backup.sh            # Backup-Skript
```

## 🐛 Fehlerbehebung

### Syntax-Fehler bei der Installation
Falls Sie einen Syntax-Fehler erhalten, verwenden Sie die **empfohlene Methode** oben. Die Pipe-Methode (`curl | bash`) kann zu Problemen führen.

### Port-Konflikte
Falls Ports bereits belegt sind, können Sie die Container-Ports in der `docker-compose.yml` anpassen.

### Docker-Probleme
Stellen Sie sicher, dass Docker läuft:
```bash
docker info
```

## 🔒 Sicherheitsverbesserungen

Die Installation wurde mit folgenden Sicherheitsmaßnahmen erweitert:

### ✅ Port-Konflikt-Prüfung
- Automatische Prüfung auf bereits belegte Ports
- Benutzer wird aufgefordert, alternative Ports zu wählen
- Verhindert Konflikte mit bestehenden Services

### ✅ Container-Konflikt-Prüfung
- Prüfung auf bereits existierende Container mit gleichen Namen
- Option zum sicheren Löschen bestehender Container
- Verhindert unbeabsichtigte Überschreibungen

### ✅ Dynamische Port-Konfiguration
- Benutzer kann alle Ports individuell anpassen
- Konfiguration wird in `.env`-Datei gespeichert
- Verwaltungsskripte verwenden korrekte Ports

### ⚠️ Empfohlene Sicherheitsmaßnahmen
- Ändern Sie die Standard-Passwörter nach der Installation
- Verwenden Sie HTTPS in Produktionsumgebungen
- Regelmäßige Backups mit `./backup.sh`
- Überwachen Sie die Container-Logs

## 📞 Support

Bei Problemen:
1. Prüfen Sie die Docker-Logs: `docker-compose logs`
2. Stellen Sie sicher, dass alle Voraussetzungen erfüllt sind
3. Verwenden Sie die empfohlene Installationsmethode

## 🔄 Updates

Für Updates verwenden Sie:
```bash
./update.sh
```

## 💾 Backups

Für Backups verwenden Sie:
```bash
./backup.sh
```

---

**Scandy** - Ein modernes Werkzeug- und Verbrauchsgüter-Management-System 