# Commission Advance Platform: Real-Estate Broker Liquidity

## Public Report — Module 15 MVP Development

---

## Executive Summary

**Giroo** is a fintech platform that provides **liquidity to real estate brokers and agencies** by advancing sales commissions secured by **purchase-and-sale agreements (CCVs)** through structured **credit assignment (cessao)**. Module 15 delivered the **functional MVP**, progressing from architecture design and relational modeling through requirements specification, low-fidelity prototyping, and culminating in a working **modular monolith** with three services — **BFF**, **Frontend**, and **Integration Engine** — containerized via Docker Compose. The platform digitizes the full commission advance lifecycle: partner onboarding, CCV registration, credit analysis, contract formalization with e-signature, disbursement, and portfolio monitoring.

---

## Problem Statement

### Market Gap

Brazil's real estate value chain locks significant working capital inside commissions that are **hard for banks to underwrite**. Reasons include:

- **Limited/fragmented credit history** for brokers and small agencies
- **Rescission risk** in purchase-and-sale agreements (title/financing issues)
- **Short, variable tenors** with regional payment practices
- **Low ticket averages** with operational idiosyncrasies
- **Traceability gaps** on receivables flow that raise perceived default risk

Traditional lenders avoid the segment; as a result, **productive professionals remain illiquid** — unable to fund expenses or invest in growth, even when they hold financeable receivables.

### Operational Challenges

- Manual, WhatsApp-scattered workflows for commission tracking
- No governed credit analysis or underwriting framework
- Lack of auditable formalization (contracts, assignments, signatures)
- No centralized partner/broker lifecycle management

---

## Solution Overview

### Core Approach

**Fintech platform** operating as a **commission advance company**, purchasing/advancing real estate **commission receivables** via **credit assignment** backed by the underlying **purchase-and-sale contract**. The system digitizes onboarding, eligibility assessment, underwriting, contract formalization, and payment routing — replacing manual operations with a **governed, auditable web system**.

### Value Proposition

**For Brokers and Agencies:**
- Immediate, compliant liquidity against commission receivables
- No traditional collateral, minimal friction, transparent pricing
- End-to-end digital formalization

**For Investors (FIDC):**
- A governed, data-rich asset with clear eligibility
- Controlled concentrations and auditable payment flows
- Attractive risk-adjusted returns

### Customer Segments

- **Primary:** Independent real estate brokers and small-to-mid agencies with recurring sales yet limited access to working capital
- **Secondary:** Investors/allocators (FIDC managers) seeking short-duration, granular exposure to real estate commission receivables
- **Channel Partners:** Real estate agencies (as originators and payment routers), pay-out/split processors

---

## Technical Architecture

### System Design Principles

The architecture is designed as a **modular monolith** with clear service boundaries, optimized for:
- **Domain separation** — BFF handles CRUD, Integration Engine handles complex rules
- **Asynchronous processing** — long-running jobs decoupled via message queues
- **Auditability** — full event/operation logs on all critical entities
- **Scalability** — containerized services that can evolve independently

### Architecture Overview

```
┌─────────────────────────────────────────────────────────────────┐
│                    FRONTEND (React + TypeScript)                 │
│   Pages: Users │ Partners │ CCVs │ Assignments │ Credit Engine  │
│          Renegotiation │ Contracts │ Documents │ Dashboards     │
└────────────────────────────┬────────────────────────────────────┘
                             │ HTTP (REST)
┌────────────────────────────▼────────────────────────────────────┐
│                     BFF (Fastify + Drizzle ORM)                 │
│   Auth JWT/Redis │ CRUD APIs │ Aggregation │ RBAC │ Rate-limit  │
└───────┬──────────────────┬──────────────────────┬───────────────┘
        │ SQL              │ HTTP/BullMQ          │ Redis
┌───────▼───────┐  ┌───────▼──────────────┐  ┌───▼───────────────┐
│  PostgreSQL   │  │  Integration Engine  │  │      Redis        │
│  (Supabase)   │  │  Credit Engine       │  │  Sessions/Cache   │
│  System of    │  │  ZapSign/Serasa      │  │  BullMQ Queues    │
│  Record       │  │  BullMQ Jobs         │  │                   │
└───────────────┘  └───────┬──────────────┘  └───────────────────┘
                           │ AMQP
                   ┌───────▼──────────────┐
                   │     RabbitMQ         │
                   │  Domain Events       │
                   │  Async Processing    │
                   └──────────────────────┘
```

### Technology Stack

| **Component** | **Technology** | **Justification** |
|---|---|---|
| **Runtime** | Node.js 20 | Unified JavaScript/TypeScript runtime across all services |
| **Language** | TypeScript 5 (strict mode) | Type safety across full stack; shared types via monorepo |
| **BFF Framework** | Fastify 4 | High-performance HTTP server; plugin architecture; schema validation |
| **ORM** | Drizzle ORM | Type-safe SQL queries; lightweight; migration support |
| **Frontend** | React 18 + Vite + shadcn/ui + TanStack Query | Component library with accessible defaults; fast build; server-state management |
| **Database** | PostgreSQL 16 (Supabase) | System-of-record; transactional consistency; relational integrity |
| **Cache/Sessions/Queues** | Redis 7 + BullMQ | JWT session management; idempotency locks; job queue processing |
| **Message Broker** | RabbitMQ 4 | Reliable async processing; domain event transport; retry with backoff |
| **E-Signature** | ZapSign | Digital contract signing; webhook callbacks for status tracking |
| **Credit Bureau** | Serasa | PJ/PF credit scoring; protest/debt data for risk assessment |
| **Validation** | Zod | Runtime schema validation; shared between BFF and Integration Engine |
| **Testing** | Vitest + Supertest + Playwright | Unit, integration, and E2E testing across services |
| **Containers** | Docker + Docker Compose | Reproducible development environments; service orchestration |
| **Package Manager** | pnpm workspaces | Monorepo management; shared dependencies; workspace linking |
| **Observability** | Pino (structured logging) + Prometheus + Grafana | Structured JSON logs; metrics collection; dashboard visualization |

### Service Responsibilities

| **Service** | **What It Does** | **What It Does NOT Do** |
|---|---|---|
| **BFF** | Auth JWT/Redis, CRUD APIs, data aggregation, rate-limit, RBAC, gateway to Integration Engine | External integrations, complex jobs, long workflows |
| **Frontend** | React SPA, consumes exclusively the BFF | Direct HTTP to external services, business logic |
| **Integration Engine** | ZapSign/Serasa integrations, BullMQ jobs, credit analysis, contract generation, billing policies | User authentication, simple CRUD, browser-facing HTTP responses |

### Key Integrations

**ZapSign (E-Signature):**
- Envelope creation with dynamic contract variables
- Individual signer tracking via webhooks
- Status lifecycle: Created → Sent → Signed → Completed

**Serasa (Credit Bureau):**
- PJ/PF credit scoring for partner and broker risk assessment
- Protest and debt data collection
- Feeds into Gold/Silver/Bronze risk rating matrix

**WhatsApp (via Chatwoot + Meta Cloud API):**
- Inbound/outbound messaging for broker communication
- SDR automation and follow-up cadences via n8n
- Conversation history persisted in MongoDB

---

## Module 15 Deliverables by Sprint

### Sprint 1 (Feb 2–13, 2026)
**Deliverables:**
1. **Detailed Submission Plan** — Project document defining scope, objectives, customer segments, work schedule, and business context for the commission advance platform
2. **Relational Model** — Comprehensive data dictionary with 44+ entities across 8 bounded contexts (Identity & Access, Partners & CRM, Property & CCV, Assignment, Documents & Signature, Credit Engine, Contracts, Audit)
3. **Simplified Architecture** — System architecture document defining the modular monolith with BFF, Frontend, and Integration Engine; component responsibilities; integration contracts; ADR-lite decisions; and security/compliance framework

### Sprint 2 (Feb 16–27, 2026)
**Deliverables:**
1. **Requirements & Implementation Roadmap** — Full functional requirements specification covering 13 domains (Users, Partners, Franchises, CCVs, Assignments, Renegotiation, Contracts, Adhesion Terms, Credit Analysis, Credit Policies, Documents, Integrations, Infrastructure) with a 12-week phased implementation roadmap
2. **Infrastructure Setup** — Docker Compose configuration for local development with BFF, Frontend, Integration Engine, Redis, RabbitMQ, and test PostgreSQL

### Sprint 3 (Mar 2–13, 2026)
**Deliverables:**
1. **Low-Fidelity Prototype** — Interactive web prototype built with Lovable, simulating 16 pages covering all primary operational workflows: Dashboard, Task queues (Assignments, Billing, Partnership, Adhesion Terms), Partner CRM pipeline, User management, Assignment details, CCV management, Renegotiation wizard, Growth testing, Credit policy configuration, and Document management

### Sprint 4 (Mar 16–27, 2026)
**Deliverables:**
1. **Functional MVP** — Working modular monolith with three services (BFF on Fastify/Drizzle, Frontend on React/Vite/shadcn, Integration Engine on Fastify/BullMQ), containerized via Docker Compose, with PostgreSQL on Supabase, Redis for sessions/queues, and RabbitMQ for async domain events

### Sprint 5 (Mar 30–Apr 10, 2026)
**Deliverables:**
1. **User Feedback Report** — Feedback collection and analysis on MVP usability, conversion barriers, and feature priorities
2. **Product Benchmarking** — Competitive analysis against RLTY Capital, PipeImob, Imobitech, and other market players
3. **Compliance Analysis** — Regulatory and ethics review for commission advance operations
4. **Final Presentation** — Presentation summarizing MVP development outcomes and technical decisions
5. **Public Report** (this document) — Written, publicly accessible report detailing Module 15 outcomes

---

## Relational Model

### Bounded Contexts

The data model is organized into **8 bounded contexts** with **44+ entities**:

| **Context** | **Key Entities** | **Purpose** |
|---|---|---|
| **Identity & Access** | `person`, `contact_point`, `app_user`, `user_system_role`, `partner_user_role`, `broker_company` | User identity, authentication, role-based access control |
| **Partners & CRM** | `partner`, `partner_lead_qualification`, `partner_focus`, `partner_risk_profile`, `partner_crm`, `partner_crm_status_history` | Partner lifecycle management from lead to active |
| **Property & CCV** | `cartorio`, `imovel`, `ccv`, `ccv_party`, `ccv_cedente`, `ccv_commission_installment`, `ccv_installment_cedente_share` | Real estate property data and purchase-and-sale agreements |
| **Assignment (Advance)** | `cessao`, `cessao_ccv`, `cessao_ccv_cedente` | Commission advance operations — the core financial product |
| **Pix Keys** | `pix_key` | Payment routing for disbursements |
| **Documents & Signature** | `document_type`, `document`, `document_signer`, `zapsign_envelope`, `zapsign_signer`, `zapsign_event` | Document lifecycle with ZapSign e-signature integration |
| **Contracts & Terms** | `partner_parceria_contract`, `user_termo_adesao`, `adesao_parceiro` | Partnership contracts and broker adhesion terms |
| **Audit** | `event_log`, `operation_log` | Full audit trail for compliance and traceability |

### Design Decisions

- **PostgreSQL as system-of-record** — transactional consistency for decisions, contracts, and operational states
- **Financial values as `numeric(15,2)`** — never `float`; transported as `string` in JSON; computed via `decimal.js`
- **Full audit trail** — every create/update on core entities produces an `event_log` record; every financial/contractual event produces an `operation_log` record
- **Idempotency by design** — `request_id` propagated across all service boundaries to prevent duplicate operations

---

## Low-Fidelity Prototype

### Overview

The low-fidelity prototype was built using [Lovable](https://lovable.dev) to simulate core user flows and validate information architecture before full-stack development. It covers the **primary operational workflows** of the Giroo Internal Operator persona.

### Pages Implemented

| **Page** | **Route** | **Key Features** |
|---|---|---|
| **Dashboard** | `/` | KPI cards (face value, disbursed, active assignments, active partners); monthly volume chart; assignment status donut chart |
| **Tasks — Assignments** | `/tarefas/cessoes` | Pending assignment queue with payment order and signer notification actions |
| **Tasks — Billing** | `/tarefas/cobranca` | Installment billing queue with mark-paid and renegotiation triggers |
| **Tasks — Partnership** | `/tarefas/parceria` | Partnership contract lifecycle tracking |
| **Tasks — Adhesion** | `/tarefas/termo-de-adesao` | Broker adhesion term lifecycle tracking |
| **Partners / CRM** | `/parceiros` | Kanban pipeline board (Lead → Contacted → Meeting → Negotiation → Active) with temperature tags and risk ratings |
| **New Partner** | `/parceiros/novo` | 6-step creation wizard covering registration, CRM, qualification, risk, white-label, and review |
| **Users** | `/usuarios/:id` | Profile with tabs: Personal Data, Account, Mobile Qualification, Financial, Serasa, Tests, Documents, Logs |
| **Assignments** | `/cessoes/:id` | Financial summary + tabs: Data, CCVs, Installments, Documents, Renegotiations, Logs |
| **CCVs** | `/ccvs` | Purchase-and-sale agreement listing and detail views |
| **Renegotiations** | `/renegociacoes/nova` | 5-step wizard: Assignment → Values → Installments → Document Template → Review |
| **CRM** | `/crm` | Alternative CRM pipeline entry point |
| **Growth Tests** | `/testes` | Campaign tracking with investment, conversion, and CAC metrics |
| **Credit Policy** | `/politica-de-credito/*` | Rating-based parameter tables (A–E) for agencies and brokers |
| **Documents** | `/documentos` | Document management with ZapSign signature tracking |

### Design System

- **Persistent left sidebar** with collapsible sections
- **KPI summary cards** with trend indicators
- **Color-coded status badges** (green=active, yellow=pending, blue=upcoming, red=late)
- **Multi-step wizards** for complex creation flows
- **Kanban pipeline cards** for CRM management

---

## Functional MVP

### Architecture Implementation

The functional MVP implements the architecture as a **pnpm monorepo** with three services:

```
giroo/
├── services/
│   ├── bff/                  # Fastify 4 + Drizzle ORM — REST API + Auth
│   ├── frontend/             # React 18 + Vite + shadcn/ui — Admin Panel
│   └── integration-engine/   # Fastify + BullMQ — Jobs, External Integrations
├── packages/
│   └── shared/               # Zod schemas, types, financial utilities
├── infra/
│   └── rabbitmq/             # RabbitMQ configuration (definitions.json)
└── docker-compose.yml        # Full local development environment
```

### Infrastructure Stack

| **Service** | **Port** | **Purpose** |
|---|---|---|
| **BFF** | 3333 | REST API gateway, JWT auth, CRUD operations |
| **Frontend** | 5173 | React SPA admin panel |
| **Integration Engine** | 3334 | Credit analysis, ZapSign, Serasa, async jobs |
| **Redis** | 6379 | Sessions, BullMQ queues, idempotency locks |
| **RabbitMQ** | 5672 / 15672 | Domain events, async processing / Management UI |
| **PostgreSQL** | Supabase (remote) | System-of-record (test instance on port 5433) |

### Key Technical Decisions

1. **Fastify over Express** — higher throughput, built-in schema validation, plugin ecosystem
2. **Drizzle ORM over Prisma** — lighter weight, SQL-first approach, better TypeScript inference
3. **BullMQ over raw RabbitMQ consumers** — Redis-backed job queues with retry, backoff, and dashboard (Bull Board)
4. **Supabase for PostgreSQL** — managed database with built-in auth capabilities, row-level security, and real-time subscriptions
5. **shadcn/ui over Material UI** — accessible, customizable components; Tailwind-native; smaller bundle
6. **pnpm workspaces** — efficient disk usage, strict dependency resolution, workspace protocol for shared packages

### Development Workflow

- **Containerized development** via `docker-compose up` — all services start with hot-reload
- **Strict TypeScript** across all services (`noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`)
- **Structured logging** via Pino (never `console.log`)
- **Migration-based schema changes** — all DDL through versioned Drizzle migrations
- **Pre-merge checklist** — lint, typecheck, test, no `any`, migration reversibility

---

## Risk Management Strategy

### Technical Risks & Mitigation

**Rescission/Default Risk:**
- **Risk:** Purchase-and-sale agreements may be rescinded, invalidating the receivable
- **Mitigation:** Eligibility filters, payment split/escrow, concentration caps per partner/agency

**Data Gaps:**
- **Risk:** Incomplete broker/agency information affects credit decisions
- **Mitigation:** API-based data intake, document standards, Serasa integration, audit trails

**Integration Dependencies:**
- **Risk:** ZapSign or Serasa downtime affects critical flows
- **Mitigation:** Async processing via BullMQ with retry/backoff; webhook deduplication; graceful degradation

### Business Risks & Mitigation

**Concentration Risk:**
- **Risk:** Over-exposure to single partner or agency
- **Mitigation:** Gold/Silver/Bronze risk framework with per-partner and per-agency concentration caps (max 25%)

**Regulatory Compliance:**
- **Risk:** Commission advance operations may face regulatory scrutiny
- **Mitigation:** Compliance-first architecture; KYC/AML routines; full audit trail; document templates

**Scale Challenges:**
- **Risk:** Manual processes may not scale with volume growth
- **Mitigation:** Automation-first design; modular architecture; RabbitMQ for async processing; job scheduling

---

## Business Model Context

### Revenue Model
- **Discount rate** on advanced commission value (customer rate 5–6% per month)
- **Service fees** complementing the spread
- **Capital structure** via FIDC (investment fund) acquiring eligible receivables

### Unit Economics (from Module 14 Financial Model)
- **Gross spread per R$1,000 advanced:** ~R$43.30 (30-day tenor, 5.5% rate, CDI 10%)
- **Gross contribution margin:** 40–58% before fixed costs
- **Break-even funded volume:** ~R$2M/month
- **5-year Base Case:** R$16.1M revenue, R$4.0M net profit (~25% margin), R$2.1M NPV

### Credit Governance Framework

| **Rating** | **LTV Max** | **Max Assignment Value** | **Max Concentration** |
|---|---|---|---|
| **A** (Gold) | 85% | R$ 750,000 | 30% |
| **B** | 80% | R$ 500,000 | 25% |
| **C** | 70% | R$ 300,000 | 20% |
| **D** | 60% | R$ 150,000 | 15% |
| **E** (Bronze) | 50% | R$ 50,000 | 10% |

---

## Future Roadmap

### Completed (Module 13 — Product-Market Fit)
- Project plan and PMF hypotheses (H1–H4)
- Architecture design and API integration documentation
- Technology stack selection and justification

### Completed (Module 14 — Financial Model)
- Cost/revenue assumptions and pricing strategy
- 12-month P&L projection and 5-year DCF analysis
- Governance and credit policy framework (Gold/Silver/Bronze)

### Completed (Module 15 — MVP Development)
- Detailed submission plan with scope and schedule
- Relational model (44+ entities, 8 bounded contexts)
- System architecture (modular monolith, 3 services)
- Requirements specification (13 functional domains, 12-week roadmap)
- Low-fidelity prototype (16 pages, all core workflows)
- Functional MVP (BFF + Frontend + Integration Engine)
- User feedback collection and product benchmarking
- Compliance analysis (regulations & ethics)

### Upcoming (Module 16 — Go to Market)
- Launch plan and customer onboarding strategy
- PMF validation execution with real partners
- Post-launch business metrics collection
- Stability and security hardening
- Strategic logs establishment

---

## Key Project Insights

### Strategic Positioning

**"Build governed, scale automated"** — Technology choices prioritize:
1. **Operational governance** — every action is auditable, every decision is traceable
2. **Automation-first** — manual processes are exceptions, not defaults
3. **Institutional readiness** — the platform converts opaque receivables into investor-grade assets

### Architectural Strengths

1. **Modular Monolith:** Clear service boundaries (BFF / Integration Engine) enable independent evolution without microservice complexity
2. **Event-Driven Processing:** RabbitMQ + BullMQ decouple long-running credit analysis, document generation, and billing jobs from the synchronous API path
3. **Full Audit Trail:** `event_log` + `operation_log` on all critical entities provide compliance-grade traceability
4. **Type Safety End-to-End:** Shared Zod schemas + strict TypeScript eliminate runtime type errors across services
5. **Financial Precision:** `numeric(15,2)` in PostgreSQL + `decimal.js` in Node + `string` in JSON — no floating-point risk

### MVP Validation Insights

The low-fidelity prototype validated information architecture with key findings:
- CRM pipeline visualization is essential for partner lifecycle management
- Task-based queues (assignments, billing, partnership, adhesion) match operator mental models
- Multi-step wizards reduce cognitive load for complex operations (partner creation, renegotiation)
- Credit policy configuration requires rating-based parameter tables, not simple toggles

---

## Current Status & Next Steps

### Module 15 Status
- Detailed submission plan and relational model
- System architecture with integration contracts
- Full requirements specification (13 domains)
- Low-fidelity prototype (16 pages)
- Functional MVP with 3 containerized services
- User feedback and compliance analysis

### Immediate Next Steps (Module 16)
- Execute PMF validation with real partner agencies
- Onboard first broker cohort via WhatsApp + web system
- Collect live transaction data for financial model calibration
- Implement security hardening and penetration testing
- Deploy to production environment

---

## Conclusion

Module 15 delivered a comprehensive MVP development cycle for the Giroo commission advance platform:

1. **Designed a robust relational model** — 44+ entities across 8 bounded contexts, covering the full commission advance lifecycle from partner onboarding through disbursement and billing
2. **Specified complete functional requirements** — 13 domains with clear CRUD matrices, integration contracts, and a phased 12-week implementation roadmap
3. **Validated UX with a low-fidelity prototype** — 16 interactive pages covering Dashboard, CRM pipeline, task queues, assignment management, credit policy configuration, and document handling
4. **Built a working functional MVP** — modular monolith with BFF (Fastify/Drizzle), Frontend (React/shadcn), and Integration Engine (BullMQ), containerized via Docker Compose with PostgreSQL, Redis, and RabbitMQ
5. **Established engineering standards** — strict TypeScript, structured logging, migration-based schema changes, financial precision with decimal types, and full audit trails

The platform converts an opaque, manually-managed receivable into an **institutional-grade asset class** — providing liquidity for brokers while delivering governed, traceable performance for investors.

---

## Contact Information

**Project Lead:** Felipe Martins Moura
**Project Type:** Entrepreneurship
**Current Module:** 15 — MVP Development
**Current Status:** Functional MVP delivered; preparing for Go-to-Market validation

---

## Appendix: Premises and Constraints

### Premises
- Interested **FIDC** buyer(s) for receivable acquisition
- Signed **partnership agreements with agencies** as originators
- **Broker adhesion terms** for individual onboarding
- **Deal-level assignment terms** per purchase-and-sale contract
- **Agency health/validation** (operational confirmation)

### Constraints
- **Ticket ≥ R$250k** for underlying property transactions
- **≤ 25% concentration** per client or agency
- **No direct payments to brokers** — agency receipt or payment split required
- **Tenor ≤ 6 months** for advance operations
- Preference for **low rescission risk** profiles
- **Academic deadlines** for deliverables (2-week sprint cadence)

---
