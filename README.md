# Systems Architect | End-to-End System Development

<div align="center">

**Give us a plan, we deliver a working system.**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-junebay-blue?style=flat&logo=linkedin)](https://linkedin.com/in/junebay)
[![GitHub](https://img.shields.io/badge/GitHub-JuneBay-black?style=flat&logo=github)](https://github.com/JuneBay)

*Seoul, South Korea | Remote Available*

</div>

---

## About

I design and build end-to-end systems across web, finance, AI, and IoT domains. Every project listed here is running in production — not a proof of concept, not a demo.

My approach: **cost-aware architecture** and **operational sustainability**. Systems that work reliably, cost as little as possible to run, and stay running without constant attention. This has led to outcomes like **$0 infrastructure costs** and **sub-5ms latency** through deliberate design choices.

I use AI as a design partner — not a replacement for engineering judgment.

---

## Tech Stack

**Languages:** Python, JavaScript, C++, C#, SQL
**Infrastructure:** Vercel, Docker, ZeroMQ, Flask, Serverless Architecture
**AI/ML:** GPT-4o, Gemini, ElevenLabs, Flux, Multi-Model Orchestration
**Domains:** Geospatial (VWorld, Leaflet.js, Turf.js), Finance (Kiwoom REST/WebSocket), IoT (ESP32, SMTP)
**Tools:** Git, FFmpeg, Streamlit, PySide6 (Qt), n8n

---

## Projects

### 🗺️ My Land Manager — Geospatial Decision Support System
**v6.0 | [landmanager.co.kr](https://landmanager.co.kr) | Patent Filed**

Serverless web application for land parcel analysis. Integrates VWorld public cadastral data with surrounding infrastructure to support pre-calculation and dispute risk assessment.

- $0 infrastructure (Vercel + VWorld OpenAPI, pure client-side)
- Patent-filed dispute risk management (virtual surveying, cost pre-calculation)
- 100MB+ geospatial data processed in-browser via chunk loading
- Stateful workflow: save/load/resume at any analysis stage
- Government portal integration (Toji-eum, Supreme Court Registry)

[Architecture Showcase →](https://github.com/JuneBay/My-Land-Manager-Showcase)

---

### 💹 Mini Citadel — Financial Data Systems (v3)
**5-Layer Architecture | Kiwoom REST/WebSocket | ZMQ**

Centralized trader decision support system. Aggregates multi-API signals into a unified real-time dashboard with sub-5ms data access.

- O(1) hashmap architecture: 50ms → <5ms lookup
- ZMQ-based multi-machine signal orchestration
- Direct memory reference for zero-copy UI updates (500ms → 100ms)
- Real-time API health monitoring across all connected services
- Automated data archiving pipeline for backtesting

[Architecture Showcase →](https://github.com/JuneBay/Mini-Citadel-Showcase)

---

### 🌾 FarmStudio — Remote IoT Monitoring System
**5 ESP32 Devices | SMTP-as-Backend | $0/month | 3+ Years Running**

Serverless IoT data collection for remote farm monitoring. Collects sensor and image data from devices 100km+ away using email as the data transport layer.

- $0 server costs (SMTP/IMAP data pipeline — no backend server)
- 5 ESP32 devices, >99% data delivery in unstable rural networks
- Self-healing data: regex normalization + time-series interpolation
- OTA firmware updates for zero-touch maintenance
- 3+ years continuous operation

[Architecture Showcase →](https://github.com/JuneBay/FarmStudio-Showcase)

---

### 🎬 WhatIF Factory — Multi-Model AI Orchestration System
**GPT-4o, Gemini, ElevenLabs, Flux | 2 YouTube Channels Operating**

Multi-model AI orchestration system that integrates external AI APIs into a single automated pipeline. Focus on architecture and cost control, not content volume.

- Stateful pipeline: save/load/rollback at any production stage
- Cost-aware logic: error classification prevents wasteful API retries
- Resilient design: exponential backoff-based automatic recovery
- HITL design: human intervention at critical decision points
- Currently operating across 2 YouTube channels

[Architecture Showcase →](https://github.com/JuneBay/WhatIF-Factory-Showcase)

---

## Design Philosophy

> **"Practical innovation over theoretical perfection. Stable deployment over rapid iteration. Cost-aware architecture over feature bloat."**

Every system I build is evaluated through one lens: **does it keep running in production without burning money or requiring constant attention?**

---

## Contact

Reach me through **[LinkedIn](https://linkedin.com/in/junebay)** only.

---

<div align="center">

*"Give us a plan, we deliver a working system."*

**Project commissions and technical partnerships welcome.**

</div>
