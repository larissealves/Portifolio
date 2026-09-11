# My Professional Engineering Experience
Full-Stack Development, Enterprise Systems, Integrations & Operations

## Stack

| Area | Technologies |
|---|---|
| Languages | JavaScript (ES6+), TypeScript, Python, SQL |
| Frontend | React, React Query, HTML5, CSS3, Tailwind CSS |
| Backend | Node.js, Express.js, REST API design |
| Data | PostgreSQL, SQL Server, relational modeling, ORM & raw SQL |
| Tooling | Git, Docker, CI/CD, Jest |

## Architecture

```
┌─────────────────────────────┐
│        React Frontend       │
│   UI / Components / State   │
└──────────────┬──────────────┘
               │ HTTP / REST
               ▼
┌─────────────────────────────┐
│       Node.js Backend       │
│  APIs / Business Logic      │
│  Data Processing            │
└──────────────┬──────────────┘
               │ Query / ORM
               ▼
┌─────────────────────────────┐
│     Relational Database     │
│   PostgreSQL / SQL Server   │
└──────────────┬──────────────┘
               │
               ▼
┌─────────────────────────────┐
│  External / Enterprise      │
│  Systems & Services         │
└─────────────────────────────┘
```

### Layers and responsibilities

**Frontend (React)**
- UI composed from reusable components (forms, tables, modals)
- Server state via React Query (fetching, caching, sync with the backend); Redux for cross-cutting client-side state (session/user context, global UI state)
- Client-side validation as a first check — never the only check; the backend re-validates everything
- No direct data-layer access: everything goes through the API boundary

**Backend (Node.js / Express)**
- Split between a route/controller layer (HTTP contract: parsing requests, shaping responses, status codes) and a service/business-logic layer (rules, calculations, orchestration)
- A data-access layer (ORM or raw queries) sits behind the service layer, so business logic doesn't depend on how data happens to be stored
- An adapter/integration layer for anything crossing a system boundary — third-party APIs, hardware event feeds, file-based imports — responsible for translating external formats into the application's internal model and back
- Consumes, rather than owns, the authentication/authorization context resolved earlier in the request pipeline

**Data (PostgreSQL / SQL Server)**
- Schema evolved incrementally as requirements changed, through migrations rather than ad-hoc edits
- ORM for straightforward CRUD; hand-written SQL when a query needed more control — multi-table joins, reporting aggregations, performance-sensitive paths
- Referential integrity enforced at the schema level (foreign keys), not only in application code

**External / enterprise systems**
- Third-party REST APIs, internal enterprise data sources, and in some cases physical hardware event feeds (e.g. access-control devices)
- Always accessed through an adapter, never directly from business logic — keeps the core application decoupled from any single integration's quirks

### Request lifecycle — read

```
1. Component requests data (React Query)
2. HTTP GET → REST endpoint
3. Controller parses the request, applies the auth/permission context
4. Service layer applies business rules (filtering, derived fields)
5. Data-access layer builds and runs the query
6. Database returns rows
7. Service layer shapes the response
8. Controller returns JSON + status code
9. React Query caches the response; component renders
```

### Request lifecycle — write

```
1. User submits a form (client-side validation first)
2. HTTP POST/PUT → REST endpoint
3. Controller re-validates on the server — the client is never trusted alone
4. Service layer applies business rules and orchestrates side effects
   (e.g. triggering an integration, recalculating a derived value)
5. Data-access layer persists the change (transaction if multiple writes are involved)
6. Any downstream sync (e.g. notifying another system) happens after persistence succeeds
7. Response returned; React Query invalidates/refetches affected queries
```

### Multi-tenant context

In multi-tenant setups, every request carries a tenant/institution context alongside the authenticated user:

```
Request
   │
   ▼
Authenticated User ──▶ Tenant / Institution Context
   │                              │
   └───────────────┬──────────────┘
                    ▼
        Business Logic (scoped to tenant)
                    │
                    ▼
        Database Query (tenant-scoped filter)
                    │
                    ▼
        Data belonging only to that tenant
```

Practical rule I follow: **no query that returns tenant-scoped data should be reachable without that context being applied.** If a feature genuinely needs a cross-tenant view (e.g. for admin/reporting), that's an explicit, separate path — never a side effect of forgetting the filter.

### Integration boundary pattern

For anything outside the core application — a third-party API, a legacy system, a hardware event feed, a file import — translation logic stays isolated in a boundary layer instead of letting external shapes leak into internal models:

```
External System / Hardware / File
              │
              ▼
     Adapter (parse + validate)
              │
              ▼
     Transform → Internal Model
              │
              ▼
     Core Business Logic
              │
              ▼
     Persistence
```

This keeps the core of the application unaware of *where* the data came from, which makes integration failures much easier to triage — "is the problem in the adapter, or after it?" is usually the first question.

## What I build

**Operational digitalization** — turning manual or spreadsheet-driven processes into structured web systems: monitoring, tracking, and approval workflows for physical/field operations.

**Workforce & productivity tracking** — badge/scanner-based identification, activity timing, and lead-time/productivity metrics derived from raw event data.

**Hardware & device integration** — backend services that consume events from physical access-control hardware and keep them in sync with core application data.

**System integration** — REST APIs connecting internal services, third-party systems, and enterprise data sources, including data transformation and validation across formats (JSON, XML, CSV).

**Multi-tenant platforms** — shared application codebases serving multiple organizations, with per-tenant configuration, permissions, and data isolation.

**Reporting & BI** — Power BI dashboards, including custom SVG-based interactive visualizations, and financial reporting features involving currency standardization for cross-region comparisons.

## How I approach a feature

```
Business Requirement
        │
        ▼
Understand Existing Flow
        │
        ▼
Design / Implement (Frontend + Backend + Data)
        │
        ▼
Integration
        │
        ▼
Functional Validation
        │
        ▼
QA
```

## How I approach a bug

I don't start by assuming which layer is at fault. I reproduce the issue, compare expected vs. actual behavior, and trace the data end-to-end until I find where it diverges:

```
React → HTTP Request → REST API → Business Logic → Query/ORM → Database → Response → React
```

Once the failing layer is isolated, I look for the root cause rather than patching the symptom, apply the smallest fix that addresses it, and re-check the original scenario plus related functionality before handing it off.

## Testing & quality

- Functional, API, and integration validation as part of feature development, before QA handoff
- Jest for targeted backend logic, not as a full test-ownership role
- Sanity and regression checks after fixes, focused on the affected flow and its neighbors

## Working with people

Most of what I build starts as a problem described by someone non-technical — an operations lead, an administrative team, an end user. Part of the job is translating that into a concrete technical requirement, and part of it is writing documentation clear enough that another engineer (or that same non-technical stakeholder) can understand what the system actually does.

---

`Full-Stack` · `React` · `Node.js` · `TypeScript` · `REST APIs` · `PostgreSQL` · `SQL Server` · `System Integration` · `Multi-Tenant Applications` · `Data Visualization` · `Debugging & Root-Cause Analysis`
