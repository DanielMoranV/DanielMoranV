# Daniel Morán Vílchez

**Full Stack Developer · Data Engineer** — Piura, Peru

I build business software that ships: multi-tenant ERPs, electronic invoicing,
and the data pipelines that move companies off legacy systems. Eight products
of mine are live in production today; four of them for paying clients.

📍 Piura, Peru · 📧 skaan.dmv@gmail.com · 💼 [LinkedIn](https://linkedin.com/in/danielmoranv)

---

## 🚀 In production

| Product | What it does | Stack | Live |
|---|---|---|---|
| **AlmaZen ERP** | Multi-tenant ERP: inventory, purchasing, sales, POS, electronic invoicing | Laravel · Livewire · PostgreSQL | [almazenapp.djasoft.net.pe](https://almazenapp.djasoft.net.pe/) |
| **MozaicoPro** | Restaurant and order management | Java · Vue 3 | [mozaicopro.djasoft.net.pe](https://mozaicopro.djasoft.net.pe/) |
| **EasyPay** | HR, attendance and payroll | TypeScript · NestJS | [easypay.djasoft.net.pe](https://easypay.djasoft.net.pe/) |
| **Otto Tonsmann** — *client* | Sales, cash desk and student registry for a technical institute | Vue 3 · Firebase | [otto-tonsmann.web.app](https://otto-tonsmann.web.app/) |
| **CONERI** — *client* | Corporate site, product catalog and admin panel for a solar energy company | Firebase · Cloud Functions · Cloudinary | [coneri.pe](https://coneri.pe/) |
| **Master Color** — *client* | E-commerce platform (in active development) | Laravel · Vue 3 · Flutter | [mastercolor.net.pe](https://www.mastercolor.net.pe/) |
| **SURGIMED** — *client* | Corporate site for a surgical equipment importer | Static · Firebase Hosting · GitHub Actions | [surgimed-pe.web.app](https://surgimed-pe.web.app/) |
| **Agenda EH** | Eisenhower-matrix task manager with two-way Google Calendar sync | Vue 3 · Firestore · OAuth 2.0 | [agenda-eh.web.app](https://agenda-eh.web.app/) |

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
`Vue 3` · `PrimeVue` · `Pinia` · `TailwindCSS` — the front end of nearly everything I ship.
`Python` — not for web: ETL, legacy data migration, analytics, OCR automation.
`TypeScript` · `NestJS` · `Express` — decoupled APIs and services.

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
- **Queues and scheduled jobs** — BullMQ over Redis, cron-driven processes.
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
"migrate to the cloud". I move their data to PostgreSQL without stopping their operation,
and I have done it at 500,000-record scale.

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
