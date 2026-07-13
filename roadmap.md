# Innalytix Product Roadmap

**Product:** Innalytix

**Owner:** Bennett Associates

**Current Version:** 0.1.0-alpha

**Status:** Active Development

**Last Updated:** 13 July 2026

---

# Product Vision

Build the leading hospitality operations, integration and business intelligence platform for independent accommodation providers.

Innalytix will integrate hospitality applications, automate operational workflows, preserve financial integrity and provide meaningful business intelligence through a single operational platform.

---

# Development Strategy

Development follows an incremental, release-based approach.

Each release delivers production-quality functionality that can be deployed, tested and expanded without architectural redesign.

The roadmap is organised around business capabilities rather than technology.

---

# Release 0.1 — Foundation

**Objective**

Establish the technical foundation for the platform.

### Deliverables

* Repository structure
* Product documentation
* FastAPI backend
* React frontend
* SQLite database
* SQLAlchemy integration
* Alembic migrations
* Logging framework
* Configuration framework
* Health API
* Version API
* Development environment
* Continuous Integration (GitHub Actions)

### Exit Criteria

* Repository can be cloned successfully.
* Backend starts without errors.
* Frontend connects to backend.
* Database initializes automatically.
* Health endpoint reports system status.
* Version endpoint reports product version.

---

# Release 0.2 — Platform Services

**Objective**

Build the reusable services required by all future modules.

### Deliverables

* Connector Framework
* Synchronisation Engine
* Event Logging
* Audit Framework
* Exception Management
* Configuration Management
* Diagnostics
* Operational Ledger
* Connector Health Monitoring

### Exit Criteria

* Connector framework operational.
* Audit events recorded.
* Synchronisation engine reusable.
* Diagnostic information available.

---

# Release 0.3 — Yoco Connector

**Objective**

Import payment information from Yoco.

### Deliverables

* Authentication
* Merchant configuration
* Payment download
* Settlement download
* Merchant fee retrieval
* Refund retrieval
* Raw payload storage
* Duplicate detection

### Exit Criteria

* New payments successfully downloaded.
* No duplicate imports.
* Complete audit trail maintained.
* All source payloads preserved.

---

# Release 0.4 — Xero Connector

**Objective**

Integrate with Xero Accounting.

### Deliverables

* OAuth authentication
* Organisation selection
* Invoice lookup
* Customer lookup
* Payment creation
* Journal creation
* Merchant fee posting

### Exit Criteria

* Invoices located successfully.
* Payments posted automatically.
* Merchant fees recorded correctly.
* Exceptions captured.

---

# Release 0.5 — Payment Reconciliation

**Objective**

Complete the first end-to-end business workflow.

### Workflow

Yoco Payment

↓

Invoice Matching

↓

Payment Allocation

↓

Merchant Fee Processing

↓

Settlement Processing

↓

Audit Logging

↓

Reporting

### Deliverables

* Invoice number extraction
* Business rule engine
* Exception handling
* Retry processing
* Synchronisation history
* Operational reports

### Exit Criteria

* Manual reconciliation eliminated for supported payment workflows.
* Complete accounting audit trail.
* Financial integrity verified.

---

# Release 1.0 — Hospitality Payment Platform

**Objective**

Deliver the first commercial release.

### Features

* Production deployment
* Web interface
* Configuration management
* Operational dashboard
* Payment reconciliation
* Reporting
* Diagnostics
* User documentation
* Installation guide

### Target Users

* Guesthouses
* Boutique hotels
* Lodges
* Bed & Breakfast establishments

---

# Future Releases

## Reservation Management

### Integrations

* NightsBridge
* Booking.com
* Expedia
* LekkeSlaap
* Additional reservation platforms

### Capabilities

* Reservation synchronisation
* Guest synchronisation
* Booking analytics
* Occupancy reporting

---

## Financial Intelligence

### Capabilities

* Revenue analysis
* Payment analysis
* Settlement tracking
* Merchant fee analysis
* Cash flow reporting
* VAT reporting
* Financial dashboards

---

## Hospitality Analytics

### Operational KPIs

* Occupancy
* ADR
* RevPAR
* Booking lead time
* Cancellation rates
* Average stay
* Guest return rate
* Revenue per booking source

---

## Operations Management

### Modules

* Housekeeping
* Maintenance
* Staff tasks
* Property inspections
* Asset management

---

## Guest Relationship Management

### Features

* Guest profiles
* Communication history
* Repeat guest analysis
* Loyalty management
* Marketing segmentation

---

## Artificial Intelligence

### Capabilities

* Revenue forecasting
* Occupancy forecasting
* Exception detection
* Operational recommendations
* Financial anomaly detection
* Natural language reporting
* AI-powered assistant

---

# Cloud Platform

Future production deployments will include:

* Microsoft Azure
* PostgreSQL
* Azure App Service
* Azure Storage
* Azure Monitor
* Secure authentication
* Multi-property support
* Multi-user support

---

# Product Principles

Every release must:

* Solve a real hospitality problem.
* Preserve accounting integrity.
* Maintain complete auditability.
* Be backward compatible where practical.
* Include automated tests.
* Include updated documentation.
* Be deployable.

---

# Success Measures

The success of Innalytix will be measured by:

* Administrative time saved.
* Reduction in manual reconciliation.
* Financial accuracy.
* Operational visibility.
* Customer satisfaction.
* Platform reliability.
* Ease of deployment.
* Extensibility.

---

# Out of Scope (Current Roadmap)

The following are intentionally excluded from the current roadmap:

* Property Management System (PMS)
* Accounting system replacement
* Booking engine
* Channel manager
* Payment gateway
* Point of Sale (POS)

Innalytix integrates with these systems rather than replacing them.

---

# Product Evolution

The long-term objective is to create a platform that quietly collects, validates, reconciles and analyses hospitality data, enabling operators to spend less time administering systems and more time running successful hospitality businesses.

Every release should move the product closer to that vision while remaining focused, maintainable and commercially valuable.

---

**Roadmap Status:** Active

**Next Milestone:** Release 0.1 – Foundation

**Next Sprint:** Sprint 1 – Platform Bootstrap
