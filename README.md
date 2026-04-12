# 📊 Pika Stats Overlay (Minecraft 1.8 ecosystem)

Een client-side geïnjecteerde overlay voor Minecraft 1.8 die spelers in de huidige wereld en TAB-lijst detecteert en realtime statistieken toont via een cache-first systeem.

---

## 🚀 Wat dit project doet

De Pika Stats Overlay leest actieve spelers uit Minecraft (wereld + TAB) en toont een live overlay met statistieken per speler.

Het systeem werkt **cache-first**, waardoor data direct zichtbaar is en daarna wordt aangevuld met API-updates op de achtergrond.

---

## ✨ Features

### 👥 Spelerdetectie

* Detectie van spelers uit de wereld (entity list)
* Detectie van TAB-lijst spelers
* Automatische deduplicatie van namen
* Optionele nickname resolutie / unnick support

---

### 📊 Overlay statistieken

Per speler:

* Level
* Rank
* Wins
* WLR (Win/Loss Ratio)
* FKDR
* Win Streak (WS)
* Guild
* UUID kopiëren

*(optioneel uitbreidbaar per gamemode / server type)*

---

### ⚡ Performance systeem

* Cache-first rendering (direct UI resultaat)
* Incremental per-speler updates (geen full refresh cycles)
* Guard system tegen stale world data
* Asynchrone API updates zonder UI blocking

---

### 💾 Caching & opslag

* Lokale SQLite cache
* Snelle reload bij rejoin / server switch
* TTL-based refresh systeem
* Fallback naar cache bij API timeouts

---

### 🌐 API integratie

* Pika Network API / custom endpoint support
* Rate-limit safe request queue
* Retry + backoff bij errors
* Prioriteit voor zichtbare spelers

---

## 🧠 Architectuur overzicht

* TAB/world reader → player queue
* Cache lookup → directe UI render
* Miss → async API fetch
* Result update → per-player UI patch
* Guard system voorkomt:

  * duplicate entries
  * world switch race conditions
  * stale async updates

---

## ⚠️ Belangrijke notes

* Ontworpen met Minecraft 1.8 ecosystem in gedachten (o.a. Lunar Client en vergelijkbare 1.8 builds)
* Gedrag kan licht variëren per client implementatie binnen 1.8
* TAB-lijst is leidend voor spelerdetectie
* Cache kan tijdelijk oude data tonen (bewust design voor snelheid)
* API updates gebeuren volledig async

---

## 📌 Aanbevolen verbeteringen

* UUID-first indexing i.p.v. naam-based tracking
* World/session ID tracking voor betere stabiliteit
* Prioriteitssysteem voor zichtbare spelers
* Atomic cache writes voor crash safety
* Strakkere scheiding tussen UI en data-layer
