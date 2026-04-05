# Chrono24 Price Tracker

[![Bright Data](https://img.shields.io/badge/Powered%20by-Bright%20Data-blue?style=flat-square)](https://brightdata.de)
[![Chrono24 Price Tracker](https://img.shields.io/badge/Chrono24%20Price%20Tracker-Managed%20Solution-orange?style=flat-square)](https://brightdata.de/products/insights/price-tracker/chrono24)
[![Python](https://img.shields.io/badge/Python-3.9%2B-yellow?style=flat-square)](https://python.org)

[![Bright Insights Price Tracker](https://raw.githubusercontent.com/danielshashko/bright-insights-assets/main/price-tracker-hero-v2.png)](https://brightdata.de/products/insights/price-tracker/chrono24)

Chrono24-Preisverfolgung in Echtzeit – der weltweit größte Online-Marktplatz für Luxusuhren. Zwei Möglichkeiten für den Einstieg: eine **vollständig verwaltete** Intelligence-Plattform oder ein **benutzerdefinierter Scraper**, erstellt mit dem AI Scraper Builder von Bright Data.

---

## Option 1: Bright Insights - KI-gestützte Preisverfolgung (Empfohlen)

**[Bright Insights](https://brightdata.de/products/insights/price-tracker/chrono24)** ist die vollständig verwaltete Retail-Intelligence-Plattform von Bright Data. Keine Scraper zu erstellen, keine Infrastruktur zu warten – nur strukturierte, analysebereite Preisdaten, geliefert an Dashboards, Data Feeds oder Ihre BI-Tools.

**Warum Teams Bright Insights wählen:**
- 🚀 **Kein Setup** – In wenigen Minuten live mit sofort einsatzbereiten Dashboards und Data Feeds
- 🤖 **KI-gestützte Empfehlungen** – Ein konversationeller KI-Assistent verwandelt Millionen von Datenpunkten sofort in umsetzbare Erkenntnisse
- ⚡ **Echtzeit-Monitoring** – Aktualisierungsraten von stündlich bis täglich mit sofortigen Benachrichtigungen (E-Mail, Slack, webhook)
- 🌍 **Unbegrenzte Skalierung** – Jede Website, jede Geografie, jede Aktualisierungsfrequenz
- 🔗 **Plug-and-play-Integrationen** – AWS, GCP, Databricks, Snowflake und mehr
- 🛡️ **Vollständig verwaltet** – Bright Data übernimmt Schemaänderungen, Website-Updates und Datenqualität automatisch

**Wichtige Anwendungsfälle:**
- ✅ **Überwachen Sie die Preise seltener und limitierter Editionen** auf Chrono24
- ✅ **Verfolgen Sie die Verfügbarkeit** über Größen und Farben hinweg in Echtzeit
- ✅ **Überprüfen Sie Wiederverkaufsaufschläge** im Vergleich zu Einzelhandelspreisen
- ✅ Überwachen Sie die Einhaltung von MAP-Richtlinien und erkennen Sie Preisverstöße
- ✅ Verfolgen Sie Wettbewerberaktionen und die Dynamik von Werbeaktionen
- ✅ Speisen Sie saubere, harmonisierte Daten direkt in dynamische Preisalgorithmen oder KI-Modelle ein

> **Ab $250/Monat – [Erhalten Sie ein individuelles Angebot →](https://brightdata.de/products/insights/price-tracker/chrono24)**

---

## Option 2: Erstellen Sie Ihren eigenen Chrono24-Scraper

Keine vorgefertigte Chrono24-Scraper-API? Kein Problem. Der **AI Scraper Builder** von Bright Data generiert mit nur wenigen Klicks einen benutzerdefinierten Chrono24-Scraper — ganz ohne Programmierung.

### Erstellen Sie Ihren Chrono24-Scraper in wenigen Minuten

**[Öffnen Sie den Chrono24 AI Scraper Builder →](https://brightdata.de/products/web-scraper/chrono24)**

Wählen Sie die Domain, beschreiben Sie Ihre Datenanforderungen, und lassen Sie unseren AI Scraper Builder die API automatisch erstellen.

1. **Beschreiben Sie den Datenbedarf in einfachem Englisch**
2. **Die KI generiert sofort die Scraper-API**
3. **Führen Sie API-Anfragen für sofortige Ergebnisse aus**
4. **Bearbeiten Sie den Code in der integrierten IDE**, falls erforderlich

Sobald Ihr Scraper erstellt ist, erhält er eine **Web Scraper ID** (`gd_xxxxxxxxxxxx`) — kopieren Sie sie für den Setup-Schritt unten.

### Voraussetzungen

- Python 3.9 oder höher
- Ein [Bright Data-Konto](https://brightdata.de) (kostenlose Testversion verfügbar)
- Ein Bright Data-**API-Token** ([so erhalten Sie eines](https://docs.brightdata.de/general/account/account-settings#api-token))
- Eine **Web Scraper ID** für Chrono24 (aus dem obigen Erstellungsschritt)

### Setup

1. **Klonen Sie dieses repository**

   ```bash
   git clone https://github.com/bright-data-de/chrono24-price-tracker.git
   cd chrono24-price-tracker
   ```

2. **Installieren Sie die Abhängigkeiten**

   ```bash
   pip install -r requirements.txt
   ```

3. **Konfigurieren Sie die Zugangsdaten**

   Kopieren Sie `.env.example` nach `.env` und tragen Sie Ihre Werte ein:

   ```bash
   cp .env.example .env
   ```

   ```env
   BRIGHTDATA_API_TOKEN=your_api_token_here
   BRIGHTDATA_DATASET_ID=your_dataset_id_here
   ```

   > **Ihre Web Scraper ID**
   > Fügen Sie die Web Scraper ID aus Ihrem [AI Scraper Builder-Dashboard](https://brightdata.de/products/web-scraper/chrono24)
   > in `BRIGHTDATA_DATASET_ID` ein (Format: `gd_xxxxxxxxxxxx`).

---

## Verwendung

Sobald Ihr Chrono24-Scraper erstellt wurde und Ihre Web Scraper ID in `.env` konfiguriert ist, funktioniert die Python-Schnittstelle auf die gleiche Weise:

### 1. Bestimmte Produkte per URL verfolgen

Übergeben Sie eine Liste von Chrono24-Produkt-URLs, um strukturierte Preisdaten abzurufen:

```python
from price_tracker import track_prices

urls = [
    "https://www.chrono24.com/en/products/sample-product-123456",
    # Add more product URLs here
]

results = track_prices(urls)
for item in results:
    print(f"{item.get('title')} - {item.get('final_price', item.get('price'))} {item.get('currency', '')}")
```

Oder direkt ausführen:

```bash
python price_tracker.py
```

### 2. Produkte per Keyword entdecken

Finden Sie Produkte, die einer Keyword-Suche entsprechen:

```python
from price_tracker import discover_by_keyword

results = discover_by_keyword("laptop", limit=50)
```

### 3. Produkte per Kategorie-URL durchsuchen

Sammeln Sie alle Produkte von einer Chrono24-Kategorieseite:

```python
from price_tracker import discover_by_category

results = discover_by_category(
    "https://chrono24.com/category/example",
    limit=100,
)
```

---

## Ausgabefelder

Jeder Ergebnisdatensatz enthält die folgenden Felder:

| Field | Description |
|-------|-------------|
| `url` | Produktseiten-URL |
| `title` | Produktname |
| `brand` | Marke/Hersteller |
| `price` | Einzelhandelspreis |
| `currency` | Währungscode |
| `in_stock` | Verfügbarkeit |
| `color` | Farbe |
| `size` | Verfügbare Größen |
| `material` | Verwendete Materialien |
| `sku` | SKU / Referenznummer |
| `images` | Produktbilder |
| `description` | Produktbeschreibung |
| `timestamp` | Zeitstempel der Erfassung |

### Beispielausgabe

```json
[
  {
    "url": "https://www.chrono24.com/en/products/sample-product-123456",
    "title": "Example Product Name",
    "brand": "Example Brand",
    "initial_price": 59.99,
    "final_price": 44.99,
    "currency": "USD",
    "discount": "25%",
    "in_stock": true,
    "rating": 4.5,
    "reviews_count": 1234,
    "images": ["https://chrono24.com/images/product1.jpg"],
    "description": "Product description text...",
    "timestamp": "2025-01-15T10:30:00Z"
  }
]
```

---

## Erweiterte Optionen

Die Funktion `trigger_collection()` akzeptiert optionale Parameter zur Steuerung der Datenerfassung:

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `limit` | integer | - | Maximale Anzahl zurückzugebender Datensätze |
| `include_errors` | boolean | `true` | Fehlerberichte in die Ergebnisse einschließen |
| `notify` | string (URL) | - | Webhook-URL, die aufgerufen wird, wenn der Snapshot bereit ist |
| `format` | string | `json` | Ausgabeformat: `json`, `csv` oder `ndjson` |

Beispiel mit Optionen:

```python
from price_tracker import trigger_collection, get_results

inputs = [{"url": "https://www.chrono24.com/en/products/sample-product-123456"}]
snapshot_id = trigger_collection(inputs, limit=200, notify="https://your-webhook.com/hook")
results = get_results(snapshot_id)
```

---

## Ressourcen

- 🌟 [Chrono24 Price Tracker - Bright Insights (Managed)](https://brightdata.de/products/insights/price-tracker/chrono24)
- 🏗️ [Build a Chrono24 Scraper](https://brightdata.de/products/web-scraper/chrono24)
- 📖 [Bright Data Web Scraper API Documentation](https://docs.brightdata.de/scraping-automation/web-scraper-api/overview)
- 🗄️ [Web Scrapers Control Panel](https://brightdata.de/cp/scrapers)
- 🔑 [How to get an API token](https://docs.brightdata.de/general/account/account-settings#api-token)
- 🌐 [Bright Data Homepage](https://brightdata.de)

---

*Erstellt mit [Bright Data](https://brightdata.de) – der branchenführenden Webdatenplattform.*