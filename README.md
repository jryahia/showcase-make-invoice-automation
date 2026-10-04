# Make Invoice Automation

**Receives invoice emails through a webhook, extracts structured data with AI (regex fallback) and exports it for accounting. The Google Sheets export is mocked in this version.**

> **This is a proprietary project. Source code is private. This page showcases the system's architecture and results.**

**Case study page:** [https://jryahia.github.io/showcase-make-invoice-automation/](https://jryahia.github.io/showcase-make-invoice-automation/)

![Make Invoice Automation](assets/00-dashboard.png)

## Problem it solves

Retyping supplier invoices into a spreadsheet or accounting tool is error-prone busywork. This service parses incoming invoices into structured records and pushes them onward automatically. It is built as the webhook backend for a Make.com scenario: the automation platform handles triggers, and this service holds the logic and data.

## Architecture

![Architecture](assets/architecture.svg)

1. Make.com forwards an invoice email to the webhook.
2. Invoice fields are extracted with AI, with a rule-based fallback.
3. The structured invoice is stored.
4. It is exported to the accounting destination, and the export is logged.

## Key features

- Webhook receiver for Make.com
- AI extraction with a deterministic fallback
- Vendor, totals and dates captured
- Export log
- Built-in test parser

## Tech stack

![Python](https://img.shields.io/badge/Python-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![FastAPI](https://img.shields.io/badge/FastAPI-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![Webhooks](https://img.shields.io/badge/Webhooks-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![OpenAI](https://img.shields.io/badge/OpenAI-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-161b22?style=for-the-badge&labelColor=161b22&color=161b22) ![Jinja2](https://img.shields.io/badge/Jinja2-161b22?style=for-the-badge&labelColor=161b22&color=161b22)

## What it does in practice

- Extraction runs on real invoice text; the accounting export currently writes to a local file standing in for Google Sheets.

## Screenshots

**Parsed invoice and totals**

![Parsed invoice and totals](assets/00-dashboard.png)

**API surface: invoice webhook, parsing, export**

![API surface: invoice webhook, parsing, export](assets/10-api.png)

---

Built by [Yahya Jarray](https://github.com/jryahia). Interested in a similar system? [Get in touch](mailto:yahiajarray43@gmail.com).
