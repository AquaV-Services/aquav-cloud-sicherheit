# ☁️ AVS Cloud – Sicherheits- & Architektur-Spezifikation

Willkommen im offiziellen Spezifikations-Repository der **AVS Cloud** (`aquav-cloud.de`), betrieben von AquaV Services. 

AVS Cloud ist eine zu 100% maßgeschneiderte (Custom Made), eigenentwickelte Cloud-Speicherlösung aus Deutschland. Um Entwicklern und Nutzern maximale Transparenz zu bieten, legen wir unsere angewendeten Sicherheitsstandards und die Systemarchitektur in diesem Whitepaper offen.

---

## 🛡️ Kryptografisches Konzept & Datensicherheit

Obwohl unser Kern-Quellcode proprietär (Closed Source) bleibt, setzen wir ausschließlich auf weltweit geprüfte Industriestandards der Kryptografie. Wir praktizieren keine "Sicherheit durch Geheimhaltung" (Security through Obscurity).

### 1. Datenverschlüsselung (AES-256-GCM)
- Jede hochgeladene Datei wird auf unseren Servern mittels **AES-256-GCM** (Advanced Encryption Standard mit Galois/Counter Mode) verschlüsselt gespeichert (Encryption at Rest).
- Dieser Standard bietet neben der reinen Vertraulichkeit auch eine integrierte Integritätsprüfung (Authentizität) der Daten.

### 2. Transportwegsicherung (TLS 1.3 & HSTS)
- Die Datenübertragung erfolgt ausnahmslos über **TLS 1.3**.
- Mittels **HSTS** (HTTP Strict Transport Security) wird erzwungen, dass Client-Browser ausschließlich verschlüsselte Verbindungen aufbauen.

### 3. Server-Infrastruktur & Rechtssicherheit
- **Standort:** Der Serverbetrieb erfolgt vollständig auf EU-Infrastruktur in den **Niederlanden**.
- **Datenschutz:** Als deutsches Unternehmen (Sitz in Baden-Württemberg) garantieren wir einen zu 100% **DSGVO-konformen** Betrieb. Es erfolgt keine Datenanalyse oder Tracking zu Werbezwecken.

---

## 🛡️ Erweiterte Sicherheits-Features

### 🛡️ Multi-Engine Virenscan bei Upload
Um die Verbreitung von Schadsoftware über Freigabe-Links absolut auszuschließen, durchläuft jede hochgeladene Datei eine automatisierte Sicherheits-Pipeline:
1. Lokaler Echtzeit-Scan über **ClamAV** direkt auf dem Server.
2. API-gestützte Gegenprüfung über **VirusTotal**, um eine maximale Erkennungsrate von Bedrohungen zu garantieren.

### 🔑 Sicheres Identity Management (Discord OAuth2)
- Wir speichern keine Passwörter für den Login. Die Authentifizierung erfolgt sicher und direkt über den offiziellen **Discord OAuth2** Standard.

### 🔒 Infrastruktur-Schutz (Manuelle Freischaltung)
- Um Ressourcen-Missbrauch, DDoS-Strukturen und Spam effektiv zu unterbinden, nutzt AVS Cloud ein **Whitelisting-Verfahren**. Neue Registrierungen werden vom Administrator manuell geprüft und freigeschaltet, bevor Zugriff auf die Speicher-Infrastruktur gewährt wird.

---

## 🐛 Verantwortungsvolle Offenlegung (Sicherheitslücken melden)

Solltest du als Entwickler oder Sicherheitsforscher eine potenzielle Schwachstelle im System finden, bitten wir um eine vertrauliche Meldung:

- 🌍 **Hauptwebseite:** [aquav-service.de](https://aquav-service.de)
- 💬 **Discord Support:** [Tritt unserem Server bei (Ticket erstellen)](https://discord.gg/2sbfVEtqyf)
- 📧 **E-Mail:** [aquavservices@gmail.com](mailto:aquavservices@gmail.com)

---
*Zuletzt aktualisiert basierend auf Live-Metriken: 07.04.2026 | © AquaV Services*
