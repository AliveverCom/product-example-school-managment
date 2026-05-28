# Directory Planning

> **Document Version**: v1.0.0  
> **Effective Date**: {YYYY-MM-DD}  
> **Document Status**: Template

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Root Directory Structure](#2-root-directory-structure)
- [3. Documentation Directory (`docs/`)](#3-documentation-directory-docs)
- [4. Source Code Directory (`src/`)](#4-source-code-directory-src)
  - [4.1 Contracts Layer](#41-contracts-layer)
  - [4.2 Backend Directory](#42-backend-directory)
  - [4.3 Frontend Directory](#43-frontend-directory)
  - [4.4 Deployment Configuration](#44-deployment-configuration)
- [5. Optional Prototype Directory (`src_prototype/`)](#5-optional-prototype-directory-src_prototype)
- [6. Module Documentation Standards](#6-module-documentation-standards)
- [7. Compliance Requirements](#7-compliance-requirements)

---

## 1. Overview

This document defines the **recommended directory structure** for a new forward-engineering project created from this template. All documentation, source code, and configuration files should follow this structure unless the project has a documented reason to diverge.

> **Recommended Standard**: Keep documentation predictable, keep ownership boundaries explicit, and keep module naming consistent across documentation, contracts, backend services, frontend apps, and deployment configuration.

---

## 2. Root Directory Structure

```text
{project-root}/
|
+-- docs/                           # Project documentation
+-- src/                            # Production source code root
+-- src_prototype/                  # Optional frozen prototype source tree
+-- README.md                       # Project entry guide
+-- .gitignore                      # Repository ignore rules
+-- package.json                    # Optional Node.js workspace config
```

Notes:

- `docs/` contains project-level and module-level documentation, including shared design standards.
- `src/` contains all implementation code for active development.
- `src_prototype/` is optional and should be used only when a frozen prototype must be preserved separately from production development.
- `README.md` should be the first document a new contributor reads.

---

## 3. Documentation Directory (`docs/`)

```text
docs/
+-- PRODUCT_OVERVIEW.md             # Product goals, workflows, users, and use cases
+-- TECHNICAL_OVERVIEW.md           # Architecture, engineering standards, and delivery rules
+-- architecture.md                 # System architecture and layer descriptions
+-- Documentation_Statistics.md     # Documentation metrics and statistics
+-- directory_planning.md           # This document
+-- platform_version_planning.md    # Platform-level version roadmap
+-- UI_UX_Design_Standards.md       # Shared UI/UX design standards
+-- backend_design_standard.md      # Shared backend design standards
+-- mermaid/                        # Mermaid source files and rendered diagram images
|   +-- Architecture.mmd
|   +-- Architecture.png
|   +-- business_process_flow.mmd
|   +-- business_process_flow.png
|   +-- platform_usecase.mmd
|   +-- platform_usecase.png
+-- templates/                      # Reusable document templates
|   +-- _business.md
|   +-- _tech_backend.md
|   +-- _tech_frontend.md
|   +-- _version_plan.md
|   +-- _dev_plan.md
|   +-- general_doc template.md
|   +-- prompt_history.md
+-- modules/                         # Module-specific documentation
    +-- {module-a}/
    +-- {module-b}/
    +-- common_libraries/
    +-- common_services/
```

Documentation rules:

- Keep all project-wide narrative documents in `docs/`.
- Keep all Mermaid source files and generated images in `docs/Mermaid/`.
- Keep reusable writing templates in `docs/templates/`.
- Keep each module's dedicated documentation under `docs/modules/{module-name}/`.

---

## 4. Source Code Directory (`src/`)

### 4.1 Contracts Layer

```text
src/contracts/
+-- openapi/                        # API and protocol contracts
```

Use this directory for:

- OpenAPI specifications
- Shared JSON schemas
- Generated contract sources when applicable

### 4.2 Backend Directory

```text
src/backend/
|
+-- common_backend_lib/             # Shared backend foundation library
|   +-- security/
|   +-- models/
|   +-- middleware/
|   +-- utils/
|
+-- gateway/                        # API gateway and BFF layer
|   +-- api_gateway/
|   +-- bff_portal/
|       +-- auth/
|       +-- aggregation/
|       +-- session/
|
+-- services/                       # Business and platform services
    +-- {module_a}_service/
    +-- {module_b}_service/
    +-- workflow_orchestration_service/
    +-- file_access_service/
    +-- reporting_service/
```

Backend rules:

- Place all backend services under `src/backend/services/`.
- Use `{module_name}_service` naming for service directories.
- Keep reusable backend logic in `common_backend_lib/` rather than duplicating code across services.
- Keep gateway and BFF logic separate from business services.

### 4.3 Frontend Directory

```text
src/frontend/
|
+-- libs/                           # Shared frontend libraries
|   +-- platform_common_frontend/
|   |   +-- auth/
|   |   +-- api/
|   |   +-- types/
|   |   +-- utils/
|   +-- ui_components/
|
+-- apps/                           # Frontend applications
    +-- portal/
    +-- {module_a}_app/
    +-- {module_b}_app/
    +-- {module_n}_app/
```

Frontend rules:

- Place all deployable frontend applications under `src/frontend/apps/`.
- Use `{module_name}_app` naming for module frontends.
- Keep shared UI and shared API logic in `src/frontend/libs/`.
- Avoid placing module-specific logic into shared libraries unless the ownership is truly cross-module.

### 4.4 Deployment Configuration

```text
src/deploy_config/
+-- environments/                   # Environment overlays such as dev/test/stage/prod
+-- platform/                       # Platform-level deployment configuration
+-- backend/                        # Backend deployment definitions
|   +-- gateway/
|   +-- services/
+-- frontend/                       # Frontend deployment definitions
|   +-- portal/
|   +-- apps/
+-- templates/                      # Shared deployment templates
```

Deployment rules:

- Keep deployment configuration separate from application source code.
- Separate platform-level configuration from backend and frontend configuration.
- Use shared deployment templates where repeated patterns exist.

---

## 5. Optional Prototype Directory (`src_prototype/`)

Use `src_prototype/` only when the project needs a permanently frozen prototype or demonstration build.

Recommended structure:

```text
src_prototype/
+-- contracts/
+-- backend/
+-- frontend/
+-- frontend_light/
+-- deploy_config/
```

Prototype rules:

- Treat `src_prototype/` as a snapshot, not as the primary development tree.
- Do not evolve the prototype beyond the version it is intended to preserve.
- All real feature development should happen in `src/`.

---

## 6. Module Documentation Standards

Each module should have a dedicated directory under `docs/modules/` using the same module name used in source code.

Recommended file naming pattern:

```text
docs/modules/{module-name}/
+-- {module-name}_business.md
+-- {module-name}_tech_backend.md
+-- {module-name}_tech_frontend.md
+-- {module-name}_version_plan.md
+-- prompt_history.md
+-- ai_dev/
+-- ui_page_design/
```

Document roles:

- **`_business.md`**: business goals, processes, objects, and use cases
- **`_tech_backend.md`**: backend models, database design, APIs, and business logic
- **`_tech_frontend.md`**: UI structure, page flows, interaction behavior, and frontend integration notes
- **`_version_plan.md`**: module version roadmap and progress tracking
- **`prompt_history.md`**: AI prompt history for the module

Optional additional files may include:

- development plans
- Mermaid diagrams
- review notes
- subcomponent design documents

### Special Module Types

#### common_libraries

Shared libraries used by multiple product modules. Each library has its own sub-directory:

```text
docs/modules/common_libraries/
+-- common_libraries_business.md
+-- common_libraries_tech_backend.md
+-- common_libraries_tech_frontend.md
+-- common_libraries_version_plan.md
+-- prompt_history.md
+-- {library_1}/
|   +-- {library_1}_business.md
|   +-- {library_1}_tech_backend.md
|   +-- {library_1}_tech_frontend.md
+-- {library_2}/
```

#### common_services

Shared platform services consumed by multiple product modules. Each service has its own sub-directory:

```text
docs/modules/common_services/
+-- common_services_business.md
+-- common_services_tech_backend.md
+-- common_services_tech_frontend.md
+-- common_services_version_plan.md
+-- prompt_history.md
+-- {service_1}/
|   +-- {service_1}_business.md
|   +-- {service_1}_tech_backend.md
|   +-- {service_1}_tech_frontend.md
+-- {service_2}/
```

---

## 7. Compliance Requirements

### 7.1 Enforcement

| Check Point | Action |
|-------------|--------|
| Code Review | Reviewers verify that files are placed in the correct directory |
| CI Validation | Automated checks validate naming and placement rules when available |
| Merge Gate | Non-compliant structural changes should be corrected before merge |

### 7.2 New Module Checklist

When adding a new module, ensure the following:

1. Create module documentation under `docs/modules/{module-name}/`.
2. Add API contracts under `src/contracts/openapi/` when applicable.
3. Create a backend service under `src/backend/services/{module_name}_service/` when backend ownership exists.
4. Create a frontend app under `src/frontend/apps/{module_name}_app/` when the module has its own UI.
5. Add deployment configuration under `src/deploy_config/`.
6. Keep naming aligned across docs, contracts, backend, frontend, and deployment assets.

---

## 8. Recommended Adaptation Notes

This template is a starting point. Before using it in a real project, replace placeholders such as:

- `{project-root}`
- `{module-name}`
- `{module_a}`
- `{module_b}`
- `{module_n}`

If the new project does not need a gateway, a prototype tree, or module-specific frontend apps, remove those sections explicitly rather than leaving ambiguous unused directories.