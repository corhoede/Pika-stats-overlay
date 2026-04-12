# 📊 Pika Stats Overlay (Minecraft 1.8)

A client-side overlay for Minecraft 1.8 that detects players in the current world and TAB list and displays real-time statistics using a cache-first system.

---

## 🚀 What this project does

The Pika Stats Overlay reads active players from Minecraft (world + TAB list) and displays a live overlay with per-player statistics.

The system is **cache-first**, meaning data appears instantly and is later updated asynchronously via API requests.

---

## ✨ Features

### 👥 Player detection

* Detects players from the world (entity list)
* Detects players from the TAB list
* Automatic name deduplication

---

### 📊 Player statistics

Per player:

* Level
* Rank
* Wins
* WLR (Win/Loss Ratio)
* FKDR
* Win Streak (WS)
* Guild
* UUID copy functionality

*(optionally extendable per gamemode / server type)*

---

### ⚡ Performance system

* Cache-first rendering (instant UI results)
* Incremental per-player updates (no full refresh cycles)
* Guard system against stale world data
* Asynchronous API updates without blocking the UI

---

### 💾 Caching & storage

* Local SQLite cache
* Fast reload on rejoin / server switch
* TTL-based refresh system
* Fallback to cache during API timeouts

---

### 🌐 API integration

* Pika Network API / custom endpoint support
* Rate-limit safe request queue
* Retry + backoff handling on errors
* Priority-based loading for visible players

---

## 🧠 Architecture overview

* TAB/world reader → player queue
* Cache lookup → instant UI render
* Cache miss → async API fetch
* Result update → per-player UI patch
* Guard system prevents:

  * duplicate entries
  * world switch race conditions
  * stale async updates

---

## ⚠️ Important notes

* Designed with the Minecraft 1.8 in mind (including Lunar Client and similar 1.8-based clients)
* Behavior may slightly vary depending on client implementation within the 1.8
* TAB list is the primary source for player detection
* Cache may temporarily show stale data (intentional for performance)
* API updates are fully asynchronous


