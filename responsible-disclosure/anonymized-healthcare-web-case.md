# Anonymisierte Fallstudie  
Webbasiertes Healthcare-Management-System (Deutschland)

## Deutsch

Art: Sicherheitsbeobachtung im Rahmen Responsible Disclosure  
Methode: Passiv (Browser, Entwickler-Tools)  
Status: Anonymisiert, nicht ausgenutzt

---

### 1. Hintergrund

Im normalen Arbeitsalltag fiel bei der Nutzung eines webbasierten
Healthcare- bzw. Sozial-Management-Systems auf,
dass sich bestimmte Abläufe im Browser ungewöhnlich verhalten.

Die Software wird unter anderem genutzt für:
- Dienst- und Einsatzplanung
- Verwaltung von Klienten- und Bewohnerdaten
- interne organisatorische Abläufe

Es wurde kein aktiver Angriff durchgeführt.

---

### 2. Beobachtungen

#### 2.1 Session-Handling und Logout

- Authentifizierungs-Cookies blieben nach dem Logout gültig
- Keine erkennbare Session-Invalidierung
- Tokens wirkten statisch
- Keine Mehrfaktor-Authentifizierung

Einschätzung:  
Fehlerhaftes Session-Handling / Broken Authentication

---

#### 2.2 Redirect-Verhalten

- Login-bezogene Redirect-Parameter akzeptierten externe Ziele
- Missbrauch für Phishing theoretisch möglich

Einschätzung:  
Open Redirect

---

#### 2.3 Versionsinformationen

- Framework-Versionen waren im HTML-Code sichtbar
- Unterschiedliche Versionen bei verschiedenen Mandanten

Einschätzung:  
Information Disclosure

---

#### 2.4 Sicherheits-Header

- Keine Content-Security-Policy erkennbar
- Cookies teilweise ohne HttpOnly- oder Secure-Flags
- Kein klar erkennbarer CSRF-Schutz aus Client-Sicht

Einschätzung:  
Security Misconfiguration

---

### 3. Gesamtrisiko

In Kombination könnten diese Punkte theoretisch zu
Session-Übernahmen, Kontoübernahmen und Zugriff auf sensible
personenbezogene Daten führen.

Bei einer Anbindung an nationale Gesundheitsinfrastrukturen
würde sich der potenzielle Schaden deutlich erhöhen.

---

### 4. Umgang mit den Beobachtungen

- Keine Ausnutzung
- Keine Veröffentlichung technischer Details
- Vorbereitung für koordinierte Responsible Disclosure

---

## English below

An anonymized case study describing passive security observations
in a web-based healthcare management system used in Germany.

The observations were made during regular usage using browser
developer tools only. No exploitation or active testing was performed.

The issues relate to session handling, redirect behavior,
information disclosure and missing security headers.

All details are anonymized and documented solely for responsible
disclosure and educational purposes.
