# Xianyu-Sneaker-Grader-Bot
Python automation tool: scrapes Xianyu (IdleFish) for basketball shoes (Li-Ning, Peak, Anta, 361°, Xtep) → displays desktop GUI popups for manual grading (Excellent/Good/Poor) → sends differentiated negotiation messages based on the grade. Cookie-free, extensible, and community-friendly
# 👟 Xianyu-Sneaker-Grader-Bot

> A semi‑automated tool for sneaker flippers and bargain hunters on Xianyu (Chinese IdleFish). Focused on basketball shoes from Li‑Ning, Peak, Anta, 361°, and Xtep. **Stably running for over 6 months**, processing hundreds of listings daily.

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Selenium](https://img.shields.io/badge/Selenium-4.x-green)](https://www.selenium.dev/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 📌 Project Overview

This tool automates three main steps:

1. **Scraping** – Uses Selenium + BeautifulSoup to collect listing titles, prices, condition descriptions, image URLs, and more for the target brands.
2. **Human‑in‑the‑loop Grading** – Displays each shoe in a desktop popup window; you rate it with keyboard shortcuts:  
   `1` = Excellent, `2` = Good, `3` = Poor, `Space` = Skip (damaged / not resellable).
3. **Automated Messaging** – Sends different pre‑written negotiation messages to sellers based on the grade (enthusiastic for excellent, aggressive for poor). You manually log in to Xianyu once, then the bot takes over.

---

## 🧱 Architecture

```text
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│  Scraper    │ ──> │  CSV Store  │ ──> │ GUI Grader  │
│ (Selenium)  │      │  (pandas)   │      │  (Tkinter)  │
└─────────────┘      └─────────────┘      └──────┬──────┘
                                                   │ (key: 1/2/3)
                                                   ▼
┌─────────────┐      ┌─────────────┐      ┌─────────────┐
│   Output    │ <── │   Message   │ <── │   Sender    │
│  (CSV)      │      │   Matcher   │      │ (same browser)
└─────────────┘      └─────────────┘      └─────────────┘
