# ☁️ AVS Cloud – Sicherheits- & Architektur-Spezifikation

Willkommen im offiziellen Spezifikations-Repository der **AVS Cloud** (`aquav-cloud.de`), betrieben von AquaV Services. 

AVS Cloud ist eine zu 100% maßgeschneiderte (Custom Made), eigenentwickelte Cloud-Speicherlösung aus Deutschland. Um Entwicklern und Nutzern maximale Transparenz zu bieten, legen wir unsere angewendeten Sicherheitsstandards und die Systemarchitektur in diesem Whitepaper offen.

---

## 🛡️ Kryptografisches Konzept & Datensicherheit

Obwohl unser Kern-Quellcode proprietär (Closed Source) bleibt, setzen wir ausschließlich auf weltweit geprüfte Industriestandards der Kryptografie. Wir praktizieren keine "Sicherheit durch Geheimhaltung" (Security through Obscurity).

### 1. Datenverschlüsselung (AES-256-GCM)
- Jede hochgeladene Datei wird auf unseren Servern mittels **AES-256-GCM** (Advanced Encryption Standard mit Galois/Counter Mode) verschlüsselt gespeichert (Encryption at Rest).
- Dieser Standard bietet neben der reinen Vertraulichkeit auch eine integrierte Integritätsprüfung (Authentizität) der Daten.
- Die Schlüsselverwaltung läuft über ein **Envelope-Encryption-Verfahren** (KEK-DEK-Modell): Ein zentraler Key-Encryption-Key verschlüsselt pro Datei einen individuellen Data-Encryption-Key. Schlüsselverwaltung und Nutzdaten bleiben so strikt getrennt.

### 2. Transportwegsicherung (TLS 1.3 & HSTS)
- Die Datenübertragung erfolgt ausnahmslos über **TLS 1.3**. Veraltete Protokolle (TLS 1.0/1.1) sind serverseitig vollständig deaktiviert.
- Mittels **HSTS** (HTTP Strict Transport Security) mit Preload wird erzwungen, dass Client-Browser ausschließlich verschlüsselte Verbindungen aufbauen.
- Zusätzliche HTTP-Sicherheits-Header reduzieren gängige Angriffsvektoren im Browser: **X-Content-Type-Options**, **X-Frame-Options (DENY)**, **Referrer-Policy** und **Permissions-Policy**.

### 3. Server-Infrastruktur & Rechtssicherheit
- **Standort:** Der Serverbetrieb erfolgt vollständig auf EU-Infrastruktur in den **Niederlanden**.
- **Datenschutz:** Als deutsches Unternehmen (Sitz in Baden-Württemberg) garantieren wir einen zu 100% **DSGVO-konformen** Betrieb. Es erfolgt keine Datenanalyse oder Tracking zu Werbezwecken.

---

## 🛡️ Erweiterte Sicherheits-Features

### 🛡️ Multi-Engine Virenscan bei Upload
Um die Verbreitung von Schadsoftware über Freigabe-Links absolut auszuschließen, durchläuft jede hochgeladene Datei eine automatisierte Sicherheits-Pipeline:
1. Lokaler Echtzeit-Scan über **ClamAV** direkt auf dem Server.
2. API-gestützte Gegenprüfung über **VirusTotal** anhand des Datei-Hashes (SHA-256). Die Originaldatei verlässt dabei niemals unsere Infrastruktur – so bleiben maximale Erkennungsrate und Datenschutz miteinander vereinbar.

### 🔑 Sicheres Identity Management (Discord OAuth2 & E-Mail/Passwort)
- Neben der Anmeldung über den offiziellen **Discord OAuth2** Standard steht alternativ ein klassischer **E-Mail/Passwort-Login** zur Verfügung.
- Passwörter werden niemals im Klartext gespeichert. Die Speicherung erfolgt ausschließlich als **bcrypt-Hash** mit individuellem Salt pro Nutzer.
- Ein **Rate-Limiting-Mechanismus** schützt den Login-Endpunkt vor Brute-Force- und Credential-Stuffing-Angriffen.
- Das Session-Token wird nach der Anmeldung ausschließlich als **httpOnly-Cookie** ausgeliefert, niemals im Local Storage abgelegt. Das verhindert den Zugriff auf Session-Tokens durch clientseitige Skripte (Schutz vor XSS-Angriffen).

### 🔒 Infrastruktur-Schutz (Manuelle Freischaltung)
- Um Ressourcen-Missbrauch, DDoS-Strukturen und Spam effektiv zu unterbinden, nutzt AVS Cloud ein **Whitelisting-Verfahren**. Neue Registrierungen werden vom Administrator manuell geprüft und freigeschaltet, bevor Zugriff auf die Speicher-Infrastruktur gewährt wird.

### 🗑️ Datenminimierung & Löschkonzept
- Server-Logs (Nginx) werden automatisiert nach **7 Tagen** per Logrotate gelöscht, um die gespeicherte Datenmenge auf das notwendige Minimum zu beschränken.
- Bei Löschanfragen werden zugehörige Datensätze (z. B. Widerrufs- und Missbrauchsmeldungen) anonymisiert statt dauerhaft entfernt. So stehen gesetzliche Aufbewahrungspflichten und das Recht auf Löschung nicht im Widerspruch zueinander.

---

## 🐛 Verantwortungsvolle Offenlegung (Sicherheitslücken melden)

Solltest du als Entwickler oder Sicherheitsforscher eine potenzielle Schwachstelle im System finden, bitten wir um eine vertrauliche Meldung:

- 🌍 **Hauptwebseite:** [aquav-service.de](https://aquav-service.de)
- 💬 **Discord Support:** [Tritt unserem Server bei (Ticket erstellen)](https://discord.gg/2sbfVEtqyf)
- 📧 **E-Mail:** [aquavservices@gmail.com](mailto:aquavservices@gmail.com)

---
*Zuletzt aktualisiert basierend auf Live-Metriken: 07.09.2026 | © AquaV Services*
