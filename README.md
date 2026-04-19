# 📡 Web-Tracking & Analytics Portfolio

Dokumentation praxiserprobter Implementierungen im Bereich **Web-Tracking, Tag Management und Marketing Analytics**.  
Alle aufgeführten Umsetzungen wurden eigenständig konzipiert, implementiert und validiert — vom initialen Setup bis zur laufenden Fehlerbehebung in Produktionsumgebungen.

> 💼 Kompetenzen erworben in der Praxis als **Junior Tracking & Analytics Specialist**

---

## 🧰 Tech-Stack

| Tag Management | Analytics | Ads-Plattformen | Technisch |
|---|---|---|---|
| Google Tag Manager | Google Analytics 4 | Google Ads | JavaScript |
| GTM Server-Side* | DataLayer-Architektur | Microsoft Ads (UET) | HTML / CSS |
| Consent Mode v2 | GA4 DebugView | Spotify Ads Pixel | Chrome DevTools |
| Custom Pixel (JS) | Custom Dimensions | Offline Conversions | Google Sheets |
| CMP-Integration | Conversion-Mapping | Calendly-Tracking | Apps Script |

*GTM Server-Side: Grundkenntnisse vorhanden

---

## 📂 Kompetenzbereiche

### 01 — Google Tag Manager: Container-Setup & Tag-Architektur

Vollständiger Aufbau von GTM-Containern von Grund auf — strukturiert, skalierbar und auditierbar.

**Implementierungsumfang:**
- Neuaufbau von GTM-Containern inkl. Workspace-Struktur, Versionierung und Zugriffsmanagement
- Integration von Google Analytics 4 — Konfiguration aller Standard- und Custom-Events
- Integration von Google Ads — vollständiger Purchase-Funnel inkl. Remarketing-Tags
- Lead-Events: Formular-Submissions, E-Mail-Klicks, Telefon-Klicks, Button-Events
- Konfiguration von Triggern, Ausnahmen und Filterregeln für saubere Datenqualität
- Verwaltung von Variablen: JS-Variablen, DOM-Elemente, DataLayer-Variablen, Konstanten

---

### 02 — Google Analytics 4: Konfiguration & Event-Architektur

Aufbau einer validen GA4-Property mit sauberer Event-Taxonomie, korrekter Datenerfassung und zuverlässiger Nutzeridentifikation.

**Implementierungsumfang:**
- Konfiguration der GA4-Property: Datenstreams, erweiterte Einstellungen, interne Datenfilter
- Ausschluss interner IP-Adressen zur Sicherstellung sauberer Produktionsdaten
- Mapping und Implementierung benutzerdefinierter Events entlang des gesamten Nutzer-Funnels
- Einrichtung von Custom Dimensions und Custom Metrics für erweiterte Segmentierbarkeit
- Konfiguration von Conversions und Zieldefinitionen in GA4
- Debugging mit GA4 DebugView und Browser-Erweiterung Tag Assistant

---

### 03 — E-Commerce Tracking: Vollständiger Purchase-Funnel

End-to-End-Implementierung des E-Commerce-Trackings in Google Ads und Microsoft Ads.

| Google Ads (GAds) | Microsoft Ads (UET) |
|---|---|
| `view_item_list` / `view_item` | Produktkatalog-Events |
| `add_to_cart` / `remove_from_cart` | Checkout-Funnel vollständig gemappt |
| `begin_checkout` / `add_payment_info` | Purchase-Event mit dynamischem Wert |
| `purchase` + Revenue + Transaction-ID | Lead-Conversion-Ziele konfiguriert |
| Lead-Conversions: Formular, Anruf, Chat | Audience-Segmentierung via UET |
| Remarketing-Audience-Tags | Cross-Plattform-Konsistenz sichergestellt |

---

### 04 — Custom Pixel: Eigenentwicklung & Shopify-Integration

Entwicklung und Integration eigener Tracking-Pixel in Shopify-Umgebungen — unabhängig von nativen Shopify-Integrationen, vollständig kontrollierbar und erweiterbar.

**Implementierungsschritte:**
- Konzeption und Entwicklung eines Custom Pixels in JavaScript für Shopify-Storefronts
- Integration in GTM via Custom HTML-Tag und DataLayer-Bridge
- Mapping von Shopify-spezifischen Events (`checkout_started`, `purchase`, `page_viewed`) auf GTM-Trigger
- Nutzung der Shopify Pixel API (Web Pixels Manager) für datenschutzkonforme Datenerfassung
- Testing und Validierung via Network-Tab, Payload-Analyse und GTM-Preview-Modus
- Sicherstellung der korrekten Reihenfolge von Pixel-Fires im Checkout-Prozess

---

### 05 — Consent Mode v2: Vollständige CMP-Integration

Implementierung des Google Consent Mode v2 in Verbindung mit einer Consent Management Platform (CMP) — DSGVO-konform, vollständig und korrekt signalisiert.

**Implementierungsumfang:**
- Konfiguration aller sechs Consent-Typen: `analytics_storage`, `ad_storage`, `ad_user_data`, `ad_personalization`, `functionality_storage`, `security_storage`
- Integration der CMP-Signale in GTM via `dataLayer.push()` und `gtag()`-Aufrufen
- Implementierung von Default-State (denied) und Update-State (granted) nach Nutzerinteraktion
- Konfiguration von Consent-aware Tags in GTM: Warten auf Consent vor Tag-Aktivierung
- Validierung der korrekten Consent-Signalisierung via Network-Requests und GTM Preview
- Sicherstellung der Kompatibilität mit Google Ads Enhanced Conversions und GA4

---

### 06 — Plattform-Integrationen: Spotify Ads, Calendly & weitere

Tracking-Implementierungen jenseits des Google-Ökosystems — Integration von Drittanbieter-Pixeln.

| Spotify Ads | Calendly-Tracking |
|---|---|
| Konfiguration des Spotify Custom Event Pixels | Verfolgung von Calendly-Buchungs-Events |
| Integration in GTM via Custom HTML-Tag | Nutzung des Calendly postMessage-APIs |
| Event-Mapping: `page_view`, `conversion`, `lead` | GTM-Trigger auf Basis von Custom Events |
| Validierung der Pixel-Fires via Network-Inspector | Weiterleitung als Conversion an GA4 & GAds |

---

### 07 — Offline-Conversion-Tracking & Datenpipeline

Erfassung und Weiterverarbeitung von Lead-Daten über den digitalen Touchpoint hinaus — für vollständige Conversion-Attribution auch außerhalb des Browsers.

**Pipeline-Architektur:**
```
Kontaktformular
       ↓
Automatische Erfassung der Lead-Daten (Telefon, E-Mail, GCLID)
       ↓
Google Sheets via Apps Script / Webhook
       ↓
Upload als Offline Conversions → Google Ads
```

**Implementierungsumfang:**
- Automatische Erfassung von Lead-Daten bei Formular-Submissions
- Speicherung und Weiterleitung der Rohdaten in Google Sheets
- Verknüpfung von GCLID (Google Click ID) mit Lead-Datensätzen für saubere Attribution
- Qualitätssicherung: Validierung, Deduplizierung, Formatprüfung

---

### 08 — JavaScript-Variablen, Custom HTML & DataLayer

Technische Implementierungstiefe jenseits von Standard-GTM-Konfigurationen.

**Implementierungen:**
- Erstellung eigener JavaScript-Variablen in GTM für dynamische Wertextraktion aus dem DOM
- Entwicklung von Custom HTML-Tags für plattformspezifische Anforderungen
- Extraktion von Variablen aus dem DataLayer: strukturierte und verschachtelte Objekte
- Implementierung von DataLayer-Pushes direkt im Quellcode (in Abstimmung mit Entwicklern)
- Nutzung von CSS-Selektoren und DOM-Traversal für zuverlässige Element-Identifikation
- Erstellung von Lookup-Tables und Regex-Variablen für flexibles Event-Matching
- Einsatz von First-Party-Cookies via GTM für persistente Nutzeridentifikation

---

### 09 — Tracking-Debugging & Fehleranalyse

Systematische Erkennung, Analyse und Behebung von Tracking-Fehlern in Produktionsumgebungen.

**Debugging-Methoden:**
- Analyse von Network-Requests im Browser DevTools: Filterung nach Tracking-Endpunkten (`collect`, `gtag`, `bat.bing`, `tr.snapchat`)
- Inspektion von Request-Payloads: Validierung von Event-Parametern, Werten und Formaten
- GTM Preview & Debug-Modus zur Trigger- und Tag-Sequenzanalyse
- GA4 DebugView für Echtzeit-Event-Validierung in der GA4-Property
- Erkennung von Doppel-Fires, fehlenden Events und falschen Parameterwerten
- Behebung von Race-Conditions zwischen DataLayer-Push und Tag-Aktivierung
- Dokumentation von Fehlern und Korrekturen für reproduzierbare Audit-Trails

---

### 10 — Tracking-Audits: Analyse bestehender Implementierungen

Strukturierte Überprüfung bestehender Tracking-Setups auf Vollständigkeit, Korrektheit und Datenschutzkonformität.

**Audit-Umfang:**
- Vollständige Bestandsaufnahme aller aktiven Tags, Trigger und Variablen im GTM-Container
- Überprüfung der Datenqualität in GA4: Duplikate, fehlende Parameter, falsche Event-Namen
- Validierung der Consent Mode Signalisierung: korrekte Default- und Update-States
- Prüfung auf veraltete UA-Tags und Migration auf GA4-Standards
- Analyse der DataLayer-Implementierung: Vollständigkeit, Timing, Struktur
- Identifikation von ungenutzten oder konfliktierenden Tags und Triggern
- Erstellung strukturierter Audit-Berichte mit priorisierten Handlungsempfehlungen

---

## 📌 Hinweis

Alle in diesem Portfolio aufgeführten Implementierungen basieren auf **realen Projekten in Produktionsumgebungen**.  
Die Umsetzungen wurden eigenständig geplant, implementiert und validiert.  
Auf Wunsch stehe ich für ein technisches Gespräch oder eine Live-Demo einzelner Setups zur Verfügung.

---

## 👩‍💻 Autorin

**Katarzyna Brzeski**  
Junior Tracking & Analytics Specialist
