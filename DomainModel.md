# Domain Model

**Product:** Innalytix

**Version:** 1.0

**Status:** Approved

**Last Updated:** 13 July 2026

---

# 1. Purpose

The Domain Model defines the core business entities that make up Innalytix.

These entities represent the hospitality business itself—not the databases, APIs or third-party systems.

Every connector, service, API and user interface within Innalytix must operate using this shared business model.

The Domain Model is the heart of the platform.

---

# 2. Design Principles

The model is based on the following principles.

* Business objects represent real-world concepts.
* Objects are independent of external systems.
* Objects have globally unique identifiers (GUIDs).
* Every object maintains an audit trail.
* External system identifiers are stored separately.
* Relationships are explicit.
* Objects evolve without breaking integrations.

---

# 3. Core Business Domains

The platform consists of six primary domains.

```text
Hospitality
│
├── Properties
├── Guests
├── Reservations
├── Rooms
│
Finance
│
├── Invoices
├── Payments
├── Settlements
│
Integration
│
├── Connectors
├── Synchronisations
├── External Systems
│
Operations
│
├── Tasks
├── Housekeeping
├── Maintenance
│
Reporting
│
├── Dashboards
├── KPIs
├── Metrics
│
Platform
    ├── Users
    ├── Configuration
    ├── Audit
    └── Exceptions
```

---

# 4. Core Entities

## Property

Represents a hospitality business.

Examples

* Maroela House
* Future guesthouses
* Boutique hotels

Attributes

* PropertyId (GUID)
* Name
* Trading Name
* Registration Number
* Address
* Time Zone
* Currency
* Status

Relationships

* Owns Rooms
* Owns Reservations
* Owns Payments
* Owns Connectors

---

## Room

Represents an individual accommodation unit.

Attributes

* RoomId
* PropertyId
* Room Number
* Room Name
* Capacity
* Room Type
* Active

Relationships

* Belongs to Property
* Used by Reservations

---

## Guest

Represents an individual or organisation making a reservation.

Attributes

* GuestId
* Name
* Company
* Email
* Telephone
* Country
* Preferred Language

Relationships

* Creates Reservations
* Receives Invoices
* Makes Payments

---

## Reservation

Represents a confirmed booking.

Attributes

* ReservationId
* PropertyId
* GuestId
* Arrival Date
* Departure Date
* Status
* Booking Source

Relationships

* Occupies Rooms
* Generates Invoices

---

## Invoice

Represents an amount owed.

Attributes

* InvoiceId
* PropertyId
* Invoice Number
* GuestId
* Date
* Total
* Outstanding Balance
* Status

Relationships

* Receives Payments
* Linked to Reservation

---

## Payment

Represents money received.

Attributes

* PaymentId
* PropertyId
* InvoiceId
* Gross Amount
* Merchant Fee
* Net Amount
* Payment Date
* Payment Method
* Currency
* Status

Relationships

* Allocated to Invoice
* Included in Settlement

---

## Settlement

Represents funds transferred from a payment provider.

Attributes

* SettlementId
* Provider
* Date
* Gross Amount
* Fees
* Net Amount

Relationships

* Contains Payments

---

# 5. Integration Domain

## Connector

Represents an external software integration.

Examples

* Yoco
* Xero
* NightsBridge
* Booking.com

Attributes

* ConnectorId
* Name
* Version
* Enabled
* Status
* Last Synchronisation

Relationships

* Produces Transactions
* Generates Synchronisations

---

## Synchronisation

Represents a single synchronisation run.

Attributes

* SyncRunId
* ConnectorId
* Started
* Completed
* Status
* Duration
* Records Processed
* Exceptions

Relationships

* Generates Audit Events

---

## External Reference

Stores identifiers used by external systems.

Attributes

* ExternalReferenceId
* Entity Type
* Internal GUID
* External System
* External Identifier

Examples

Payment

```text
Internal Payment

↓

GUID

↓

Yoco Payment ID
```

Invoice

```text
Internal Invoice

↓

GUID

↓

Xero Invoice ID
```

This allows Innalytix to support multiple external systems without changing its own identity model.

---

# 6. Platform Domain

## User

Represents an authenticated user.

Version 1

Single administrator.

Future

Multiple users.

Role-based security.

---

## Configuration

Represents configurable application settings.

Examples

* Property defaults
* Connector settings
* Reporting options
* Synchronisation preferences

---

## Audit Event

Represents a permanent business event.

Examples

* Payment imported
* Invoice matched
* Journal created
* Synchronisation completed

Audit events are immutable.

---

## Exception

Represents an operational problem requiring attention.

Examples

* Invoice not found
* Authentication failed
* Duplicate payment
* Validation failure

Exceptions remain until resolved.

---

# 7. Entity Relationships

```text
Property
│
├── Rooms
├── Reservations
│     │
│     ▼
│   Guest
│
├── Invoices
│     │
│     ▼
│  Payments
│     │
│     ▼
│ Settlements
│
└── Connectors
      │
      ▼
Synchronisations
      │
      ▼
Audit Events
```

---

# 8. Business Rules

The Domain Model follows these rules.

A Reservation belongs to one Property.

A Payment belongs to one Invoice.

A Payment may belong to one Settlement.

An Invoice belongs to one Guest.

Every Connector produces Synchronisations.

Every Synchronisation creates Audit Events.

Every Exception references the affected business object.

Every business object has a GUID.

External identifiers never replace internal identifiers.

---

# 9. Future Expansion

The model has been designed to support future domains including:

* Multi-property management
* Revenue management
* Loyalty programmes
* AI recommendations
* Predictive analytics
* Procurement
* Asset management
* Staff scheduling
* Mobile applications

These additions should extend the model rather than replace it.

---

# 10. Guiding Principle

The Domain Model represents the business.

Databases persist it.

APIs expose it.

Connectors translate to it.

User interfaces present it.

Analytics interpret it.

The Domain Model remains the single source of truth for Innalytix.

---

**End of Document**
