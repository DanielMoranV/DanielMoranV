# Daniel Morán Vílchez

**Full Stack Developer · Data Engineer** — Piura, Peru

I build business software that ships: multi-tenant ERPs, electronic invoicing,
and the data pipelines that move companies off legacy systems. Most of my week
goes into the clinical systems I maintain at **Clínica Santa Rosa**; the rest into
eight products of my own that are live in production, four of them for paying clients.

📍 Piura, Peru · 📧 skaan.dmv@gmail.com · 💼 [LinkedIn](https://linkedin.com/in/danielmoranv)

---

## 🚀 In production

| Product | What it does | Stack | Live |
|---|---|---|---|
| **AlmaZen ERP** | Multi-tenant ERP: inventory, purchasing, sales, POS, electronic invoicing | Laravel · Livewire · PostgreSQL | [almazenapp.djasoft.net.pe](https://almazenapp.djasoft.net.pe/) |
| **MozaicoPro** | Restaurant and order management, with real-time order updates over WebSockets | Go · Gin · React 19 · PostgreSQL | [mozaicopro.djasoft.net.pe](https://mozaicopro.djasoft.net.pe/) |
| **EasyPay** | HR, attendance and payroll | TypeScript · NestJS | [easypay.djasoft.net.pe](https://easypay.djasoft.net.pe/) |
| **Otto Tonsmann** — *client* | Sales, cash desk and student registry for a technical institute | Vue 3 · Firebase | [otto-tonsmann.web.app](https://otto-tonsmann.web.app/) |
| **CONERI** — *client* | Corporate site, product catalog and admin panel for a solar energy company | Firebase · Cloud Functions · Cloudinary | [coneri.pe](https://coneri.pe/) |
| **Master Color** — *client* | E-commerce platform (in active development) | Laravel · Vue 3 · Flutter · AWS S3 | [mastercolor.net.pe](https://www.mastercolor.net.pe/) |
| **SURGIMED** — *client* | Corporate site for a surgical equipment importer | Static · Firebase Hosting · GitHub Actions | [surgimed-pe.web.app](https://surgimed-pe.web.app/) |
| **Agenda EH** | Eisenhower-matrix task manager with two-way Google Calendar sync | Vue 3 · Firestore · OAuth 2.0 | [agenda-eh.web.app](https://agenda-eh.web.app/) |

---

## 🏥 Healthcare systems — where most of my week goes

I build and maintain the systems below at **Clínica Santa Rosa** (Piura, Peru), where they
are in daily use across admissions, medical records, billing and support. **The code is
closed and stays that way** — clinical data. What follows is the engineering, not the data.

**Clinical intranet — API + SPA.** A Laravel 12 REST API behind a Vue 3 single-page
application, used across admissions, medical records, HR and internal IT support.
WebSockets (Laravel Reverb) push state between departments in real time instead of
polling. The backend stamps data and signatures onto existing PDF templates rather than
regenerating documents from scratch, and emits heavy analytical reports as Excel. The
front end scans barcodes through the browser's camera, runs drag-and-drop scheduling over
a live calendar, and builds PDF and Excel exports client-side so the server never touches
them. JWT throughout, with input sanitised at the edge.

**Medical insurance management — the full lifecycle.** Admissions, clinical histories,
billing, medical audits and settlements, as a Laravel 11 API plus a Vue 3 client. Stateless
JWT auth with role-based access control separating auditors, billing staff and
administrators; real-time notifications over Reverb and Echo; bulk Excel import/export for
invoices and audits; Chart.js dashboards. Containerised for production with Docker.

**A binary FoxPro engine, written from scratch.** The hard one. Rather than depend on ODBC
or Windows-only tooling, I built a cross-platform Python engine that reads *and writes*
`.dbf` files at the byte level — parsing FoxPro's binary headers, null flags and
end-of-file markers, reserving the legacy system's native auto-increment IDs to preserve
referential integrity, and using byte-range locking so records can be appended **while
staff are actively working in the 1990s FoxPro application**. No downtime, no corruption.
This is what made migrating 500,000+ historical records possible without stopping a clinic.

---

## 📊 By the numbers

- **3+ years** building and maintaining systems that run every day
- **500,000+** historical records migrated from FoxPro to PostgreSQL
- **2,000+** records processed daily through automated ETL pipelines
- **50+** administrative and healthcare users on systems I maintain
- **20+** business modules developed and in service

---

## 🛠 Stack

Ordered by how much I actually use it, not by what looks good.

**Core**
`PHP` · `Laravel` · `Livewire` — my backbone. AlmaZen ERP, electronic invoicing, inventory.
`Go` · `Gin` · `sqlx` — MozaicoPro's backend: hand-written SQL over an ORM, JWT, WebSockets.
`Vue 3` · `PrimeVue` · `Pinia` · `TailwindCSS` — the front end of most of what I ship.
`TypeScript` · `React 19` · `NestJS` · `Express` — SPAs and decoupled APIs.
`Python` — not for web: ETL, legacy data migration, analytics, OCR automation.

**Also shipping**
`C#` (Windows desktop) · `Dart` / `Flutter` (mobile, offline-first) · `Java` · `Blade`

**Data**
`PostgreSQL` · `MySQL` · `Redis` · `SQLite` / `Drift` · `Prisma` · `Eloquent` · `SQLAlchemy`
Legacy sources: `FoxPro` / `DBF`

**Infrastructure**
`Docker` · `Nginx` · `GitHub Actions` · `Cloudflare` (Pages, R2, Tunnels) · `Firebase`
(Firestore, Auth, Cloud Functions, Hosting) · `AWS` (EC2, S3) · `Linux`

---

## 🏗 Architecture I work with

- **Multi-tenancy** — company-level isolation in AlmaZen; one PostgreSQL schema per tenant
  in a school management system, with per-tenant backup and migration.
- **Decoupled API + SPA** — Laravel or NestJS behind a Vue 3 front end, JWT auth.
- **Serverless / BaaS** — Firestore with Cloud Functions callables and triggers, security
  rules as the real access-control layer.
- **Offline-first mobile** — Flutter over local SQLite (Drift), full transactional business
  logic with no network and no backend.
- **ETL and legacy modernization** — FoxPro/DBF to PostgreSQL and MySQL, with data quality
  checks and scheduled jobs.
- **Real-time** — WebSocket channels pushing order state to kitchen and floor as it changes.
- **Queues and scheduled jobs** — BullMQ over Redis, cron-driven processes.
- **Object storage** — product media on AWS S3, served straight from the bucket by absolute
  URL so the application server never handles image traffic.
- **Modular monolith** — Laravel + Livewire when a SPA would only add moving parts.
- **Packaged desktop apps** — C# and Python compiled to portable Windows executables.

---

## 🤖 AI in production

Not "I use AI to code" — AI features shipped inside products.

**AlmaZen — conversational assistant over the ERP.** A function-calling agent with
**29 read-only tools** (stock levels, sales summaries, margin analysis, expiring
batches, customer debt, cash position, inventory valuation), built behind a
provider-agnostic `LlmProvider` contract — currently Google Gemini, swappable
without touching the tools. Every tool requires its own RBAC permission and is
re-validated at execution time; the SQL tool is restricted to read-only `SELECT`
inside the caller's tenant schema, with a forced row limit. Usage is metered as a
monthly per-plan quota, and the API key never reaches the client.

**Master Color — public sales chatbot.** A storefront assistant answering product
availability and pricing questions, deliberately built the *opposite* way: no tools
at all. The product catalog is composed into the system prompt and the model can
see nothing else — for an unauthenticated endpoint, no tool surface means no tool
surface to abuse. Hardened with per-IP rate limiting, bounded message and history
size, and a capped conversation window. Provider-agnostic behind a single
interface, running a self-hosted **Ollama** model with **OpenRouter** as fallback.
Code: [`master_color_api`](https://github.com/GiancarloGO/master_color_api).

Two products, two deliberately different designs: tools plus per-user permissions
where the audience is authenticated and the data is sensitive; context-only where
the traffic is anonymous and the data is already public.

---

## 📦 Open source

| Package | What it is |
|---|---|
| **[sunat-comprobantes](https://github.com/DanielMoranV/sunat-comprobantes)** | Peruvian electronic invoicing (SUNAT) utilities. Published on Packagist as `djasoft/sunat-comprobantes` · MIT |
| **[nomenclador](https://github.com/DanielMoranV/nomenclador)** | Bulk PDF invoice renaming with OCR fallback (Tesseract), following each insurer's required naming scheme |
| **[almazen-api](https://github.com/DanielMoranV/almazen-api)** · **[almazen_frontend](https://github.com/DanielMoranV/almazen_frontend)** | The decoupled v2 of AlmaZen — Laravel API and Vue 3 client · PolyForm Noncommercial |
| **[almazen-lite](https://github.com/DanielMoranV/almazen-lite)** | Free desktop edition of AlmaZen, in C# · PolyForm Noncommercial |

---

## 🎯 What I'm good at

**Modernizing legacy systems.** Companies running on FoxPro and VFP that cannot simply
"migrate to the cloud" — because the old system is still open on every desk. I move their
data to PostgreSQL without stopping the operation, at 500,000-record scale, using a binary
engine I wrote for exactly that. Most backend developers have only ever met modern
databases; far fewer have written a driver that appends to a 1990s one while it is in use.

**Peruvian regulatory domain.** SUNAT electronic invoicing, SIAGIE and MINEDU for education,
SUSALUD for healthcare, RENIEC and ubigeo data. This is the knowledge that makes local
software actually usable — and it is the part a generic imported SaaS never gets right.

**The whole product cycle.** Requirements and technical specification, development,
deployment, and a client who pays for it. Not just the code in the middle.

---

## 📫 Let's connect

💼 [LinkedIn](https://linkedin.com/in/danielmoranv) · 📧 skaan.dmv@gmail.com

⭐ Open to remote roles in **Backend Engineering**, **Data Engineering** and
**Cloud Infrastructure** — and to building custom business software for Peruvian companies.
