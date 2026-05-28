# {Module Name} - {Version} {Scope} Development Plan

> **Version**: {version} - {Version Title}  
> **Created**: {YYYY-MM-DD}  
> **Author**: {Author}  
> **Theme**: {One-sentence description of the version's main theme / deliverables}  
> **Prerequisite**: {Previous version or "None"} must be completed  
> **WARNING Constraint**: After development is completed, the progress status of **ALL** tasks in this plan must be updated to reflect the actual outcome (reference to Progress Legend below). The Task Summary table in the final section must also be updated accordingly.

---

## Table of Contents

1. [Version Scope & Goals](#1-version-scope--goals)
2. [Required Reading Before Development](#2-required-reading-before-development)
3. [Infrastructure / Cross-Cutting Tasks](#3-infrastructure--cross-cutting-tasks)
4. [Entity A - {Operation Type}](#4-entity-a--operation-type)
5. [Entity B - {Operation Type}](#5-entity-b--operation-type)
6. [Deferred / Unchanged Items](#6-deferred--unchanged-items)
7. [Out of Scope](#7-out-of-scope)
8. [Task Summary](#8-task-summary)

<!-- 
  Instructions:
  - Add or remove Entity sections (4, 5, ...) as needed for the module.
  - Keep the Table of Contents in sync with actual sections.
  - Each entity section follows the same internal structure (Model -> Repository -> Service -> Handler for BE; Component -> State -> API Integration for FE).
-->

---

> **Progress Legend**:
> - [doing] `planned` - Not yet started
> - [partial] `doing` - Work in progress
> - [done] `done` - Completed
> - [pending] `partial` - Partially done, minor gaps remain
> - [failed] `failed` - Blocked or failed

---

## 1. Version Scope & Goals

**{Version} Goal**: {Clear statement of what this version achieves - what changes from the previous version.}

**What {version} delivers**:
- {Deliverable 1}
- {Deliverable 2}
- {Deliverable 3}
- ...

**What {version} is NOT** (deferred to later versions):
- {Deferred item 1} ({target version})
- {Deferred item 2} ({target version})
- ...

---

## 2. Required Reading Before Development

Developers **must** read and understand the following documents before starting development:

| # | Document | Path | Purpose |
|---|----------|------|---------|
| 1 | **Backend/Frontend Technical Design** | `docs/Module/{module}/...` | {Purpose description} |
| 2 | **Version Plan** | `docs/Module/{module}/{module}_version_plan.md` | Version scope boundaries |
| 3 | **Previous Version Dev Plan** | `docs/Module/{module}/ai_dev/dev_plan_{prev_version}_...md` | Understand prior completion status and existing code |
| 4 | **Technical Overview** | `docs/TECHNICAL_OVERVIEW.md` | Platform-level tech stack, coding conventions, and architecture |
| 5 | **OpenAPI Specification** | `src/contracts/openapi/{module}.openapi.yaml` | Authoritative API contract |
| 6 | **Business Overview** | `docs/Module/{module}/{module}_business.md` | Domain context |

<!-- Add or remove rows as needed. Always include the tech doc, version plan, and OpenAPI spec. -->

---

## 3. Infrastructure / Cross-Cutting Tasks

> {Brief description of shared infrastructure work required for this version.}

<!-- 
  For Backend versions: database setup, dependency installation, shared utilities, middleware, etc.
  For Frontend versions: state management setup, shared components, API client configuration, etc.
-->

> **Existing Code Assets** (already present - reuse, don't recreate):
> - {Existing asset 1 with path}
> - {Existing asset 2 with path}
>
> **What is missing** (must be created in this version):
> - {Missing item 1}
> - {Missing item 2}

### 3.1 {Infrastructure Sub-topic 1}

| ID | Task | Details | Progress |
|----|------|---------|----------|
| INF-01 | {Task title} | {Task details - what to do, where to put it, what to reference} | [doing] |
| INF-02 | {Task title} | {Task details} | [doing] |

### 3.2 {Infrastructure Sub-topic 2}

| ID | Task | Details | Progress |
|----|------|---------|----------|
| INF-03 | {Task title} | {Task details} | [doing] |
| INF-04 | {Task title} | {Task details} | [doing] |

<!-- Add more sub-sections (3.3, 3.4, ...) as needed. -->

---

## 4. Entity A - {Operation Type}

<!-- 
  Copy this entire section for each entity in the module.
  {Operation Type} examples: "Real CRUD", "UI Implementation", "API Integration", "Mock Data"
-->

> **Entity**: `{table_name}`  
> **API Base Path**: `/api/{module}/{entity-plural}`  
> **Reference**: Tech Doc Section {section numbers}  
> **Existing Model/Component**: `{path to existing code}`  
> **Existing Handlers/Pages**: `{path to existing code}`  
> **Special**: {Any special notes - computed fields, nested resources, associations, etc.}

### 4.1 Model / Data Layer

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {XX}-01 | {Task title} | {Task details} | [doing] |
| {XX}-02 | {Task title} | {Task details} | [doing] |

### 4.2 Repository / Data Access Layer

<!-- For Frontend dev plans, replace with "State Management" or "Store" -->

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {XX}-03 | {Task title - e.g., `List(page, pageSize, filters...)`} | {Query details, filter support, pagination} | [doing] |
| {XX}-04 | {Task title - e.g., `GetByID(id)`} | {Single record fetch, associations to preload} | [doing] |
| {XX}-05 | {Task title - e.g., `Create(entity)`} | {Insert details, return value} | [doing] |
| {XX}-06 | {Task title - e.g., `Update(id, fields)`} | {Partial update details} | [doing] |
| {XX}-07 | {Task title - e.g., `SoftDelete(id)`} | {Soft delete details} | [doing] |

### 4.3 Service / Business Logic Layer

<!-- For Frontend dev plans, replace with "API Integration" -->

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {XX}-08 | {Task title} | {Business logic, validation, error mapping} | [doing] |
| {XX}-09 | {Task title} | {Additional business rules} | [doing] |

### 4.4 Handler / Controller Layer

<!-- For Frontend dev plans, replace with "UI Components" -->

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {XX}-10 | `{HTTP_METHOD} /{endpoint}` - {description} | {Query params, request body, response format} | [doing] |
| {XX}-11 | `{HTTP_METHOD} /{endpoint}/{id}` - {description} | {Path params, response format} | [doing] |
| {XX}-12 | `{HTTP_METHOD} /{endpoint}` - {description} | {Request body validation, response format} | [doing] |
| {XX}-13 | `{HTTP_METHOD} /{endpoint}/{id}` - {description} | {Path params, body, response format} | [doing] |
| {XX}-14 | `{HTTP_METHOD} /{endpoint}/{id}` - {description} | {Path params, response format} | [doing] |

---

## 5. Entity B - {Operation Type}

<!-- Repeat the same structure as Section 4 for each additional entity. -->

> **Entity**: `{table_name}`  
> **API Base Path**: `/api/{module}/{entity-plural}`  
> **Reference**: Tech Doc Section {section numbers}  
> **Existing Model/Component**: `{path}`  
> **Existing Handlers/Pages**: `{path}`

### 5.1 Model / Data Layer

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {YY}-01 | {Task title} | {Task details} | [doing] |

### 5.2 Repository / Data Access Layer

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {YY}-02 | {Task title} | {Task details} | [doing] |

### 5.3 Service / Business Logic Layer

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {YY}-03 | {Task title} | {Task details} | [doing] |

### 5.4 Handler / Controller Layer

| ID | Task | Details | Progress |
|----|------|---------|----------|
| {YY}-04 | {Task title} | {Task details} | [doing] |

---

## 6. Deferred / Unchanged Items

> **Note**: {Explain why these items are deferred - e.g., dependency on external service, out of scope for this version, etc.}

| ID | Task | Details | Progress |
|----|------|---------|----------|
| DF-01 | {Keep/Defer item} | {Explanation - what stays unchanged and why} | [doing] |
| DF-02 | {Keep/Defer item} | {Explanation} | [doing] |

---

## 7. Out of Scope

The following features are explicitly **NOT** part of {version} and will be implemented in later versions:

| Feature | Target Version | Notes |
|---------|---------------|-------|
| {Feature 1} | {vX.Y} | {Brief explanation} |
| {Feature 2} | {vX.Y} | {Brief explanation} |
| {Feature 3} | {vX.Y} | {Brief explanation} |

---

## 8. Task Summary

| Section | Tasks | [doing] Planned | [partial] Doing | [done] Done | [pending] Partial | [failed] Failed |
|---------|-------|-----------|---------|---------|-----------|----------|
| **3. Infrastructure** | {n} | {n} | 0 | 0 | 0 | 0 |
| **4. Entity A** | {n} | {n} | 0 | 0 | 0 | 0 |
| **5. Entity B** | {n} | {n} | 0 | 0 | 0 | 0 |
| **6. Deferred** | {n} | {n} | 0 | 0 | 0 | 0 |
| **Total** | **{N}** | **{N}** | **0** | **0** | **0** | **0** |

<!-- 
  Naming Convention for dev plan files:
    dev_plan_{version}_{scope}_{YYYYMMDD}.md
  Examples:
    dev_plan_v0.4_BE_20260326.md
    dev_plan_v0.3_FE_BE_20260326.md
    dev_plan_v1.0_FE_20260401.md
  
  {scope} values: BE (Backend), FE (Frontend), FE_BE (Full-stack)
-->
