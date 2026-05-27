# ☁️ AquaV Cloud – Sicherheits- & Architektur-Spezifikation

AquaV Cloud (`aquav-cloud.de`) ist eine zu 100% maßgeschneiderte (Custom Made), eigenentwickelte Cloud-Speicherlösung. Um maximales Vertrauen zu gewährleisten, legen wir unsere Sicherheitsarchitektur, Datenflüsse und kryptografischen Standards in diesem Whitepaper offen.

---

## 🛡️ Kryptografisches Konzept & Transparenz

Obwohl der eigentliche Infrastruktur-Code aus Sicherheits- und Wettbewerbsgründen geschützt (Closed Source) bleibt, setzen wir bei der Sicherheit ausschließlich auf mathematisch bewiesene und öffentlich geprüfte Industriestandards. **Wir betreiben keine "Sicherheit durch Geheimhaltung des Verfahrens" (Security through Obscurity).**

### 1. Datenübertragung (Verschlüsselung auf dem Transportweg)
- Alle Verbindungen zu `aquav-cloud.de` sind zwingend über das moderne **TLS 1.3** Protokoll verschlüsselt.
- Ältere, unsichere Protokolle (TLS 1.0, 1.1) sowie unsichere Verschlüsselungsmethoden (Cipher-Suites) sind serverseitig komplett deaktiviert.
- **HSTS (HTTP Strict Transport Security):** Ist aktiv, um Man-in-the-Middle-Angriffe (erzwungene Herabstufungen auf unverschlüsseltes HTTP) unmöglich zu machen.

### 2. Datenspeicherung auf den Servern (Verschlüsselung der ruhenden Daten)
- Die physischen Speichermedien unserer Cloud-Infrastruktur sind vollständig mittels **AES-256** verschlüsselt.
- Selbst bei einem physischen Diebstahl der Festplatten aus dem Rechenzentrum sind die Daten für Dritte absolut unlesbar.

### 3. Benutzer-Authentifizierung
- Passwörter werden niemals im Klartext gespeichert.
- Wir nutzen moderne, rechenintensive Hashing-Verfahren mit individuellem Zusatzwert (Salt), um automatisierte Angriffe (Brute-Force) auf Benutzerkonten serverseitig effektiv zu blockieren.

---

## 🗺️ Datenfluss & Infrastruktur-Transparenz

### 📍 Serverstandort & Rechtssicherheit
- **Standort:** Unsere gesamte Cloud-Infrastruktur wird in zertifizierten Rechenzentren innerhalb der **Europäischen Union (Deutschland)** betrieben.
- **Rechtliches:** Es gilt zu 100% die strenge **DSGVO (Datenschutz-Grundverordnung)**. Deine Daten unterliegen nicht dem US-Cloud-Act und sind vor fremden Zugriffen geschützt.

### 🚫 Null-Datenanalyse (Kein Tracking)
Im Gegensatz zu großen kommerziellen Anbietern scannt AquaV Cloud deine Dateien *nicht* für Werbezwecke, erstellt keine Nutzerprofile und analysiert keine Metadaten. Deine Dateien sind und bleiben dein absolutes Eigentum.

---

## 🐛 Verantwortungsvolle Offenlegung (Sicherheitslücken melden)

Wir nehmen Sicherheit extrem ernst. Wenn du ein Entwickler oder Sicherheitsforscher bist und eine potenzielle Schwachstelle in unserer maßgeschneiderten Cloud-Infrastruktur gefunden hast, bitten wir dich, uns diese vertraulich mitzuteilen:

- 📧 **E-Mail:** [aquavservices@gmail.com](mailto:aquavservices@gmail.com)
- 💬 **Direkter Kontakt:** Über unser Ticket-System auf [Discord](https://discord.gg/2sbfVEtqyf)

Wir werden jeden validen Bericht schnellstmöglich prüfen, beheben und transparent aufarbeiten.
