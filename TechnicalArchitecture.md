# Technical Architecture

**Product:** Innalytix

**Version:** 1.0

**Status:** Approved

**Last Updated:** 13 July 2026

---

# 1. Purpose

This document defines the technical architecture for Innalytix.

Its purpose is to ensure that all development follows a consistent architectural approach while supporting future growth from a single-property deployment to a multi-property cloud platform.

This document intentionally focuses on architectural principles rather than implementation detail.

---

# 2. Architectural Principles

The architecture is based on the following principles:

* API First
* Cloud Native
* Modular
* Domain Driven
* Connector Based
* Canonical Data Model
* Audit First
* Security by Design
* Testable
* Observable

Every technical decision should support these principles.

---

# 3. High Level Architecture

```text
                        +----------------------+
                        |     React Web UI     |
                        +----------+-----------+
                                   |
                                   |
                             REST / HTTPS
                                   |
                                   |
                      +------------v-------------+
                      |     FastAPI Backend      |
                      +------------+-------------+
                                   |
      +----------------------------+----------------------------+
      |                            |                            |
      |                            |                            |
+-----v------+             +-------v-------+            +-------v-------+
| Connector  |             | Business      |            | Reporting &   |
| Framework  |             | Services      |            | Analytics     |
+-----+------+             +-------+-------+            +-------+-------+
      |                            |                            |
      +----------------------------+----------------------------+
                                   |
                           Canonical Domain Model
                                   |
                                   |
                      +------------v-------------+
                      |      Data Access Layer   |
                      +------------+-------------+
                                   |
                           SQLAlchemy ORM
                                   |
                                   |
                      +------------v-------------+
                      | SQLite / PostgreSQL DB   |
                      +--------------------------+
```

---

# 4. Architectural Layers

## Presentation Layer

Responsible for:

* User Interface
* User Experience
* Input validation
* Displaying information

Technology:

* React
* TypeScript
* Material UI

The Presentation Layer contains **no business logic**.

---

## API Layer

Responsible for:

* REST endpoints
* Request validation
* Authentication
* Authorization
* API versioning
* Response formatting

Technology:

* FastAPI

The API layer orchestrates services but contains minimal business logic.

---

## Business Services Layer

Responsible for implementing business processes.

Examples include:

* Payment Matching
* Invoice Matching
* Settlement Processing
* Merchant Fee Processing
* Synchronisation
* Exception Handling

Business Services operate only on canonical business objects.

---

## Connector Framework

Responsible for communicating with external systems.

Examples:

* Yoco
* Xero
* NightsBridge
* Booking.com
* Expedia

Connectors must never contain business rules.

Their sole responsibility is:

* Authenticate
* Read
* Write
* Transform
* Handle API communication

---

## Canonical Domain Model

The Canonical Domain Model represents the Innalytix business objects.

External systems are transformed into these objects.

Examples include:

* Property
* Guest
* Reservation
* Invoice
* Payment
* Settlement
* Connector
* SyncRun
* AuditEvent
* Exception

This model remains independent of any external application.

---

## Data Access Layer

Responsible for:

* Database access
* ORM mapping
* Transactions
* Repository pattern
* Persistence

Technology:

* SQLAlchemy

Business Services never access SQL directly.

---

# 5. Connector Architecture

Every connector implements the same interface.

```text
Connector

Connect()

Authenticate()

Download()

Upload()

Validate()

Disconnect()

HealthCheck()
```

Each connector remains independent.

Future connectors should be added without affecting existing functionality.

---

# 6. Canonical Data Flow

```
External System

↓

Connector

↓

Canonical Business Object

↓

Business Services

↓

Validation

↓

Database

↓

Analytics

↓

API

↓

User Interface
```

The connector is responsible only for translating external data.

Business logic begins after translation into the canonical model.

---

# 7. Synchronisation Architecture

Each synchronisation follows the same lifecycle.

```
User Initiates Sync

↓

Connector Authenticates

↓

Retrieve Source Data

↓

Store Raw Payload

↓

Transform

↓

Validate

↓

Business Rules

↓

Persist

↓

Generate Audit Events

↓

Update Sync Status

↓

Return Summary
```

No imported data is processed before the raw payload has been stored.

---

# 8. Data Storage Strategy

Development:

SQLite

Production:

PostgreSQL

Migration between database engines should require configuration changes only.

The application must not depend upon database-specific features.

---

# 9. Security

Authentication to external systems shall use industry-standard OAuth where supported.

Secrets shall never be stored in source code.

Credentials shall be encrypted.

All communication with cloud deployments shall use HTTPS.

Audit information shall never be deleted.

---

# 10. Logging

Three categories of logging are maintained.

## Application Log

Application lifecycle events.

Examples:

* Startup
* Shutdown
* Configuration
* Errors

---

## Synchronisation Log

Business operations.

Examples:

* Payments imported
* Invoices matched
* Synchronisations completed

---

## Audit Log

Permanent record of business events.

Examples:

* Payment created
* Journal posted
* Settlement reconciled

Audit information forms part of the product's permanent business record.

---

# 11. Error Handling

Every exception shall be classified.

Categories include:

* Validation
* Authentication
* Connectivity
* Business Rule
* External API
* Database
* Unknown

Errors must never silently fail.

---

# 12. Testing Strategy

Testing occurs at multiple levels.

Unit Tests

Business Services

Connector Tests

Integration Tests

End-to-End Tests

Business rules require automated testing.

---

# 13. Deployment Strategy

Development

Windows

Local SQLite

Local React

Local FastAPI

Production

Microsoft Azure

Azure App Service

Azure Database for PostgreSQL

Azure Storage

Azure Monitor

Future deployments should require minimal configuration changes.

---

# 14. Scalability

The architecture supports future expansion through:

* Multiple Properties
* Multiple Users
* Multiple Payment Providers
* Multiple Accounting Systems
* Multiple Reservation Systems
* AI Services
* Reporting Services

No architectural redesign should be required.

---

# 15. Architecture Decision Records

Significant technical decisions are documented separately within:

```
docs/ADR/
```

Each Architecture Decision Record includes:

* Context
* Decision
* Alternatives Considered
* Consequences

---

# 16. Non-Functional Requirements

Availability

The platform shall recover gracefully from failures.

Performance

Typical synchronisations should complete within one minute.

Reliability

Business transactions must never be lost.

Maintainability

Code shall remain modular and testable.

Observability

Operational behaviour must be visible through logs, diagnostics and audit records.

---

# 17. Guiding Principle

Innalytix is not a collection of integrations.

It is a hospitality operations platform.

Integrations exist only to provide trusted information to the platform.

The platform owns the business model.

External systems supply data.

Business services create value.

---

**End of Document**
