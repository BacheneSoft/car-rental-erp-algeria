# Fleet & Car Rental Management SaaS

A multi-tenant SaaS platform for car rental agencies and fleet operators in Algeria — built end-to-end from architecture to production deployment.

> **Note:** This is a private commercial product currently in use by real clients. This repository showcases the project's scope and architecture for portfolio purposes; the source code remains private.

---

## Overview

Rental agencies in Algeria typically manage their fleets with spreadsheets and paper records — no automated alerts, no real financial visibility, no centralized data. This platform replaces that with a single system covering the full operational and financial lifecycle of a car rental business: from booking a vehicle to generating a legally compliant Algerian invoice.

Built solo, from initial architecture through a live production deployment currently serving real agencies.

🌐 Live platform: [app.bachenesoft.com](https://app.bachenesoft.com/)

## Screenshots

<!-- Drag and drop your screenshots directly into this README on GitHub's web editor —
     it will auto-upload them and insert the markdown for you. Replace the lines below
     with the generated image links, one per screenshot. -->

| Dashboard | Fleet Management | Rental Contracts |
|---|---|---|
| <img width="1266" height="668" alt="dashboard" src="https://github.com/user-attachments/assets/a3909c48-da20-4667-8c2f-d0abcb3f847c" /> | <img width="1266" height="668" alt="vehicles" src="https://github.com/user-attachments/assets/5f824abf-7015-434f-81ee-c0d7a2ece319" /> | <img width="1266" height="672" alt="dashboard2" src="https://github.com/user-attachments/assets/c6019bdd-743f-415d-87cc-b13749a0c009" /> |

| Invoicing | Client Ledger | Reports |
|---|---|---|
| <img width="1276" height="666" alt="payment" src="https://github.com/user-attachments/assets/3c60bade-a8d9-48ae-8531-96058ca87aa1" /> | <img width="1278" height="662" alt="clients" src="https://github.com/user-attachments/assets/21b7f541-5511-46e9-a3b9-94f557f54f44" /> | <img width="1278" height="668" alt="contrats" src="https://github.com/user-attachments/assets/5e05e96a-7c7d-4812-a872-7e0626a4e407" /> |

## Key Features

- **Multi-tenant architecture** — a single codebase serving many independent rental agencies, with strict data isolation enforced at the model layer (not just query filters)
- **Full rental lifecycle** — vehicle reservations with real date-range overlap detection, contract creation with/without a driver, automated km-overage billing, vehicle handover/return condition reports
- **Automated Algerian-compliant invoicing** — auto-generated on contract closure, with proper NIF/NIS/RC/TVA breakdown, plus credit notes (avoir) and proforma quotes
- **Financial tracking** — per-client running balance (ledger) across multiple contracts and partial payments, cash-basis vs. accrual revenue reporting
- **Fleet maintenance & compliance** — automatic alerts for insurance/inspection expiry and scheduled maintenance, enforced before a vehicle can be rented
- **Subscription management** — trial periods, plan-based usage limits, automated account suspension for non-payment
- **Role-based access** — platform admin, agency managers, and fleet staff each see only what's relevant to them

## Tech Stack

- **Backend:** Laravel, PostgreSQL
- **Admin/Web UI:** Filament (Livewire-based admin panel framework)
- **PDF generation:** DomPDF for contracts, invoices, and reports
- **Email:** Brevo (transactional SMTP)
- **Infrastructure:** Linux VPS, Nginx, PHP-FPM, Certbot/Let's Encrypt

## Architecture Highlights

- **Tenant isolation via Eloquent global scopes** — rather than manually filtering every query, tenant scoping is enforced at the model level so it can't be accidentally bypassed by a new feature
- **Event-driven state consistency** — vehicle availability, invoice generation, and client balances update automatically via model observers rather than being manually maintained across the UI
- **Business rules enforced server-side** — e.g. a vehicle cannot be booked with expired mandatory documents, a reservation requires a deposit, overlapping bookings are rejected at the data layer, not just the form

## Role

Solo-built: requirements, database design, backend logic, admin UI, PDF/document generation, deployment, and production troubleshooting.

---

Built using an AI-assisted development workflow (Claude) for accelerated delivery.
