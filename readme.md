A good `README.md` should explain the product to a new developer or stakeholder in under five minutes. This is a living document that we'll refine as Innalytix evolves.

# Innalytix

> **Hospitality Operations, Integration & Business Intelligence Platform**

Developed by **Bennett Associates**

---

## Overview

Innalytix is a cloud-ready, API-first hospitality platform that integrates operational and financial systems to provide a single source of truth for independent accommodation providers.

Rather than replacing existing hospitality applications, Innalytix connects them, automates business processes, maintains financial integrity, and provides meaningful operational intelligence.

The first implementation focuses on synchronising **Yoco** payment transactions with **Xero**, automatically allocating payments to invoices while maintaining a complete audit trail.

---

## Vision

To become the operational intelligence platform for guesthouses, lodges, boutique hotels and hospitality groups by integrating the systems they already use and transforming operational data into actionable business insight.

---

## Mission

Innalytix enables hospitality businesses to:

* Eliminate repetitive manual administration.
* Improve accounting accuracy.
* Integrate hospitality applications.
* Maintain complete auditability.
* Provide meaningful operational and financial analytics.

---

## Core Principles

### API First

All functionality is exposed through REST APIs.

### Cloud Ready

Develop locally.

Deploy to the cloud without redesign.

### Accounting Integrity

Financial data must always remain accurate, traceable and auditable.

### Audit First

Every imported transaction can be traced back to its source.

### Canonical Data Model

External systems never dictate the internal data model.

Connectors transform external data into Innalytix's own business model.

### Modular Design

Every integration is implemented as an independent connector.

### Hospitality Focus

Every feature must solve a real operational problem within the hospitality industry.

---

# Product Roadmap

## Version 0.1 — Foundation

* Backend framework
* Frontend framework
* Database
* Logging
* Configuration
* Health API
* Version API

---

## Version 1.0 — Payment Reconciliation

* Yoco Connector
* Xero Connector
* Invoice Matching
* Payment Posting
* Merchant Fee Processing
* Exception Management
* Audit Logging

---

## Future Releases

### Reservation Integration

* NightsBridge
* Booking.com
* Expedia
* LekkeSlaap

### Hospitality Analytics

* Occupancy
* ADR
* RevPAR
* Revenue Analysis
* Channel Performance
* Payment Costs

### Operational Management

* Housekeeping
* Maintenance
* Task Management

### Business Intelligence

* Executive Dashboards
* Financial Analytics
* Operational KPIs
* AI-powered Insights

---

# Architecture

```text
┌───────────────────────────────────────────┐
│              React Web UI                 │
└───────────────────────────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│             FastAPI REST API              │
└───────────────────────────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│         Business Services Layer           │
└───────────────────────────────────────────┘
                    │
        ┌───────────┴───────────┐
        ▼                       ▼
┌──────────────┐       ┌──────────────┐
│Yoco Connector│       │Xero Connector│
└──────────────┘       └──────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│      Canonical Business Data Model        │
└───────────────────────────────────────────┘
                    │
                    ▼
┌───────────────────────────────────────────┐
│      SQLite (Development)                 │
│      PostgreSQL (Production)              │
└───────────────────────────────────────────┘
```

---

# Technology Stack

## Backend

* Python 3.13
* FastAPI
* SQLAlchemy
* Alembic
* Pydantic

## Frontend

* React 19
* TypeScript
* Material UI

## Database

* SQLite (Development)
* PostgreSQL (Production)

## Development

* GitHub
* GitHub Actions
* Pytest
* Ruff
* Black

---

# Repository Structure

```text
innalytix/
│
├── backend/
├── frontend/
├── docs/
├── product/
├── database/
├── scripts/
├── tests/
├── installer/
└── .github/
```

---

# Current Status

**Release:** 0.1.0-alpha

**Sprint:** Sprint 1 – Foundation

Current objectives:

* Repository bootstrap
* Backend framework
* Frontend framework
* Database framework
* Logging
* Configuration
* Development environment

---

# Development Workflow

Every feature follows the same lifecycle:

1. Business Requirement
2. Functional Design
3. Technical Design
4. Implementation
5. Testing
6. Documentation
7. Release

---

# Product Ownership

**Product:** Innalytix

**Developed by:** Bennett Associates

**Pilot Deployment:** Maroela House, Bellville, Cape Town, South Africa

All intellectual property, source code and documentation are owned by Bennett Associates unless otherwise licensed.

---

# License

Copyright © Bennett Associates.

All Rights Reserved.

---

# Contact

**Bennett Associates**

For product information, licensing and commercial enquiries, contact Bennett Associates.

---

*"Connecting hospitality systems. Protecting financial integrity. Delivering operational intelligence."*


