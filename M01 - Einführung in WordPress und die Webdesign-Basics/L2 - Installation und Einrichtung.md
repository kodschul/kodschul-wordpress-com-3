
# Installation und Einrichtung

## Installation von WordPress auf einem Webserver: Schritt-für-Schritt-Anleitung

WordPress ist eine beliebte Plattform zur Erstellung von Websites und Blogs. Hier ist eine Schritt-für-Schritt-Anleitung zur Installation von WordPress auf einem Webserver:

### 1. Voraussetzungen
- Ein Webserver (Apache oder Nginx)
- PHP (Version 7.4 oder höher)
- MySQL oder MariaDB

### 2. WordPress herunterladen
Lade die neueste Version von WordPress von der offiziellen Website herunter:
```bash
wget https://wordpress.org/latest.tar.gz
tar -xzvf latest.tar.gz
```

### 3. Dateien auf den Webserver verschieben
Verschiebe die entpackten Dateien in das Webverzeichnis:
```bash
sudo mv wordpress/* /var/www/html/
```

### 4. Rechte und Berechtigungen setzen
Stelle sicher, dass die richtigen Berechtigungen gesetzt sind:
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

### 5. Datenbank erstellen
Melde dich bei deiner MySQL-Datenbank an und erstelle eine neue Datenbank für WordPress:
```sql
CREATE DATABASE wordpress;
GRANT ALL PRIVILEGES ON wordpress.* TO 'wp_user'@'localhost' IDENTIFIED BY 'password';
FLUSH PRIVILEGES;
```

### 6. WordPress einrichten
- Besuche die URL deines Servers (`http://dein-server`) und folge den Anweisungen zur Einrichtung der Datenbankverbindung.
- Schließe die Installation ab, indem du die notwendigen Einstellungen (Website-Name, Admin-Konto) eingibst.

## Konfiguration der Grundfunktionen: Datenbanken, Benutzer und Einstellungen

Nachdem WordPress installiert ist, sollten die Grundfunktionen konfiguriert werden, um eine stabile und sichere Umgebung zu gewährleisten.

### 1. Datenbankeinstellungen anpassen
Über die `wp-config.php` Datei können wichtige Datenbankeinstellungen vorgenommen werden:
- Sicherstellen, dass die Zugangsdaten korrekt sind (`DB_NAME`, `DB_USER`, `DB_PASSWORD`).
- Optional: Die Tabellenpräfixe ändern, um Sicherheit zu erhöhen.

### 2. Benutzerverwaltung
WordPress bietet ein integriertes System zur Verwaltung von Benutzern und deren Rollen:
- **Admin**: Vollzugriff auf alle Funktionen.
- **Editor**: Kann Inhalte veröffentlichen und verwalten.
- **Author**: Kann eigene Beiträge veröffentlichen.
- **Subscriber**: Nur Lesezugriff.

Sichere Passwörter und die richtige Zuweisung von Rollen sind entscheidend für die Sicherheit.

### 3. Grundeinstellungen im Backend konfigurieren
Im WordPress-Admin-Panel können weitere Grundeinstellungen vorgenommen werden:
- **Permalinks**: Suchmaschinenfreundliche URLs aktivieren (`/%postname%/`).
- **Zeitzone**: Richtig einstellen, um Zeitstempel für Beiträge korrekt anzuzeigen.
- **Medien**: Standardgrößen für hochgeladene Bilder definieren.

## Sicherheitstipps für eine stabile WordPress-Installation

Die Sicherheit ist ein wichtiger Faktor, um WordPress stabil und vor Angriffen geschützt zu halten.

### 1. Sicherheits-Plugins installieren
Verwende Plugins wie **Wordfence** oder **Sucuri**, um die Website vor Angriffen zu schützen. Diese Plugins bieten:
- Firewall-Schutz
- Malware-Scans
- Login-Schutz

### 2. Sichere Passwörter und Zwei-Faktor-Authentifizierung (2FA)
- Verwende komplexe und einzigartige Passwörter für das Admin-Konto.
- Aktiviere 2FA, um den Login weiter abzusichern.

### 3. Regelmäßige Updates durchführen
WordPress und seine Plugins sollten immer auf dem neuesten Stand gehalten werden:
- Aktiviere automatische Updates, um Sicherheitslücken schnell zu schließen.
- Überprüfe regelmäßig, ob Updates verfügbar sind, und installiere sie umgehend.

### 4. wp-config.php und .htaccess sichern
- Setze die richtigen Berechtigungen für die `wp-config.php` Datei, um den Zugriff einzuschränken:
  ```bash
  chmod 600 /var/www/html/wp-config.php
  ```
- Schütze die `.htaccess` Datei, um unbefugten Zugriff auf sensible Dateien zu verhindern.

## Fazit

Eine gut durchgeführte Installation und Konfiguration von WordPress ist die Basis für eine stabile und sichere Website. Durch die Beachtung der Sicherheitstipps und regelmäßige Wartung kann WordPress effektiv und sicher genutzt werden.
