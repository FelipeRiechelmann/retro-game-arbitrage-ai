# 🚀 AI-Powered Game Arbitrage & Data Pipeline

An automated end-to-end data engineering and computer vision pipeline designed to identify, evaluate, and capitalize on retro game arbitrage opportunities in real time.

---

## 📌 Business Overview

Finding undervalued retro video games on C2C marketplaces (e.g., OLX) usually requires hours of manual screening. This project automates the entire process:

1. **24/7 Scraping:** Continuously monitors targeted game listings.
2. **AI Inspection:** Leverages **Gemini 1.5 Flash Vision** to detect bootleg/pirated media, damaged items, or incorrect regional formats.
3. **Margin Calculation:** Approves listings only when the resale profit margin exceeds **80%**.
4. **Data Engineering:** Stores raw, sanitized, and business-ready data in a **Supabase (PostgreSQL)** database for analytics.
5. **Instant Alerts:** Sends push notifications to **Telegram** with pre-drafted negotiation messages and logs markdown cards in **Obsidian**.

---

## 📐 System Architecture

```text
Scraper (OLX) ➔ n8n Orchestrator ➔ Gemini 1.5 Flash (Vision + Pricing)
                                         │
                   ┌─────────────────────┴─────────────────────┐
                   ▼                                           ▼
             [Discarded]                              [Approved > 80%]
        Pirated / Low Margin                                   │
                                            ┌──────────────────┼──────────────────┐
                                            ▼                  ▼                  ▼
                                     Supabase (SQL)      Telegram Bot        Obsidian MD
                                  (BI / Gold Layer)    (Instant Alert)      (Action Card)
