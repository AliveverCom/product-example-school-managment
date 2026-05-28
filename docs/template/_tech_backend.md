# {Module Name} - Backend Technical Design

> **Document Version**: v1.0.0
> **Effective Date**: {YYYY-MM-DD}
> **Document Status**: Draft

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Class Definitions (Python)](#2-class-definitions-python)
  - [2.1 Enums](#21-enums)
  - [2.2 {Entity Class 1}](#22-entity-class-1)
  - [2.3 {Entity Class 2}](#23-entity-class-2)
  - [2.N {Entity Class N}](#2n-entity-class-n)
- [3. Database Design](#3-database-design)
  - [3.1 Table: {table_name_1}](#31-table-table_name_1)
  - [3.2 Table: {table_name_2}](#32-table-table_name_2)
  - [3.N Table: {table_name_n}](#3n-table-table_name_n)
  - [3.X Indexes](#3x-indexes)
- [4. API Definitions](#4-api-definitions)
  - [4.1 {Resource Group 1} APIs](#41-resource-group-1-apis)
  - [4.2 {Resource Group 2} APIs](#42-resource-group-2-apis)
  - [4.N {Resource Group N} APIs](#4n-resource-group-n-apis)
- [5. Business Logic Implementation](#5-business-logic-implementation)
  - [5.1 {Flow 1}](#51-flow-1)
  - [5.2 {Flow 2}](#52-flow-2)
  - [5.N {Flow N}](#5n-flow-n)
- [6. Integration with {External Service}](#6-integration-with-external-service)
- [7. Technology Stack](#7-technology-stack)

---

## 1. Overview

<!-- Describe what this backend module handles, which tables it owns, and what responsibilities belong to other services (if any). -->

The {Module Name} module backend handles **{list primary responsibilities}**. Standard CRUD operations for core business objects ({list objects}) are provided by the **{External Service}** service (if applicable).

This backend owns {N} tables:
- `{table_name_1}` - {description}
- `{table_name_2}` - {description}

---

## 2. Class Definitions (Python)

### 2.1 Enums

```python
class E{EnumName}(str, Enum):
    VALUE_1 = "Value1"
    VALUE_2 = "Value2"
    VALUE_3 = "Value3"

class E{EnumName2}(str, Enum):
    VALUE_A = "ValueA"
    VALUE_B = "ValueB"
```

### 2.2 {Entity Class 1}

<!-- Describe the entity's role and what it represents. -->

{Description of what this entity does.}

```python
class {EntityClass1}(Base):
    __tablename__ = "{table_name_1}"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    {field_name}: Mapped[{type}] = mapped_column({SQLAlchemyType}, nullable={True|False}, index={True|False})
    status: Mapped[E{StatusEnum}] = mapped_column(
        String(20), nullable=False, default=E{StatusEnum}.DEFAULT_VALUE
    )
    created_at: Mapped[datetime] = mapped_column(DateTime, nullable=False, server_default=func.now())

    # Relationships (if applicable)
    {related_items}: Mapped[list["{RelatedClass}"]] = relationship(
        "{RelatedClass}",
        primaryjoin="...",
        foreign_keys="...",
        order_by="...",
        lazy="joined",
    )
```

### 2.3 {Entity Class 2}

{Description of what this entity does.}

```python
class {EntityClass2}(Base):
    __tablename__ = "{table_name_2}"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    {field_name}: Mapped[{type}] = mapped_column({SQLAlchemyType}, nullable={True|False})
    created_at: Mapped[datetime] = mapped_column(DateTime, nullable=False, server_default=func.now())
```

### 2.N {Entity Class N}

<!-- Shared or auxiliary entity if applicable. -->

{Description of what this entity does.}

```python
class {EntityClassN}(Base):
    __tablename__ = "{table_name_n}"

    id: Mapped[int] = mapped_column(Integer, primary_key=True, autoincrement=True)
    {field_name}: Mapped[{type}] = mapped_column({SQLAlchemyType}, nullable={True|False})
```

---

## 3. Database Design

### 3.1 Table: {table_name_1}

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | INTEGER | PRIMARY KEY, AUTO INCREMENT | Unique identifier |
| {column_name} | {TYPE} | {constraints} | {description} |
| status | VARCHAR(20) | NOT NULL, DEFAULT '{default}' | {enum values description} |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | Creation timestamp |

### 3.2 Table: {table_name_2}

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | INTEGER | PRIMARY KEY, AUTO INCREMENT | Unique identifier |
| {column_name} | {TYPE} | {constraints} | {description} |
| created_at | TIMESTAMP | NOT NULL, DEFAULT NOW() | Creation timestamp |

### 3.N Table: {table_name_n}

| Column | Type | Constraints | Description |
|--------|------|-------------|-------------|
| id | INTEGER | PRIMARY KEY, AUTO INCREMENT | Unique identifier |
| {column_name} | {TYPE} | {constraints} | {description} |

### 3.X Indexes

```sql
CREATE INDEX idx_{table_name_1}_{column} ON {table_name_1}({column});
CREATE INDEX idx_{table_name_1}_{column2} ON {table_name_1}({column2});

CREATE INDEX idx_{table_name_2}_{column} ON {table_name_2}({column});

CREATE INDEX idx_{table_name_n}_{column} ON {table_name_n}({column1}, {column2});
```

---

## 4. API Definitions

> **Design Principle**: All APIs return **complete class objects**. No UI-specific aggregation or projection endpoints.

### 4.1 {Resource Group 1} APIs

#### GET /api/{module}/{resource-plural}

List {resources} with pagination. Each {resource} object includes its embedded {sub-objects} (if applicable).

**Query Parameters:**

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| page | integer | No | Page number (default: 1) |
| page_size | integer | No | Items per page (default: 20) |
| status | string | No | Filter by status |
| {filter_param} | {type} | No | {filter description} |
| date_from | string (ISO date) | No | Filter by created_at >= date_from |
| date_to | string (ISO date) | No | Filter by created_at <= date_to |

**Response Example:**

```json
{
  "items": [
    {
      "id": 1,
      "{field}": "{value}",
      "status": "Done",
      "created_at": "2026-01-01T00:00:00Z",
      "{nested_objects}": [
        {
          "id": 1,
          "{field}": "{value}",
          "status": "Done"
        }
      ]
    }
  ],
  "total": 100,
  "page": 1,
  "page_size": 20
}
```

#### GET /api/{module}/{resource-plural}/{id}

Get a single {resource} with embedded {sub-objects}.

**Response**: Same structure as one item in the list response above.

#### POST /api/{module}/{resource-plural}

Create a new {resource}.

**Request Example:**

```json
{
  "{field_1}": "{value_1}",
  "{field_2}": "{value_2}"
}
```

**Response**: The created {resource} object.

---

### 4.2 {Resource Group 2} APIs

<!-- Repeat API pattern for additional resource groups. Follow the same structure: -->
<!-- GET list with pagination + filters -->
<!-- GET single by ID -->
<!-- POST create -->
<!-- PUT update (if applicable) -->
<!-- DELETE (if applicable) -->

---

### 4.N {Resource Group N} APIs - Composite / Special Operations

#### POST /api/{module}/{operation}

<!-- For composite operations that span multiple entities or trigger workflows. -->

{Description of the composite operation and its steps.}

**Request Example:**

```json
{
  "{input_ids}": [1, 2, 3],
  "{target_id}": 50,
  "{optional_param}": "{value}"
}
```

> {Notes about conditional behavior, e.g., "When `{field}` is null but `{field2}` is provided, a new {object} is created first."}

**Response Example:**

```json
{
  "created_{object}_ids": [101, 102, 103],
  "{target_id}": 50
}
```

---

### 4.X Validation APIs (if applicable)

#### POST /api/{module}/validate/{resource}

Validate a {resource} against its specification.

**Request Example:**

```json
{
  "file_url": "/files/{path}/{filename}"
}
```

**Response Example:**

```json
{
  "valid": false,
  "errors": [
    {
      "line": 45,
      "message": "{error description}"
    }
  ],
  "warnings": [
    {
      "line": 12,
      "message": "{warning description}"
    }
  ]
}
```

---

### 4.Y Preview / Async APIs (if applicable)

#### POST /api/{module}/preview/{resource}

Request asynchronous generation of a {resource}. Returns immediately.

**Request Example:**

```json
{
  "{source_id}": 200,
  "{input_file_url}": "/files/{path}/{filename}"
}
```

**Response Example:**

```json
{
  "{source_id}": 200,
  "status": "Processing",
  "message": "{description} started"
}
```

#### GET /api/{module}/preview/{resource}/{id}

Check the status of an asynchronous generation request.

**Response Example:**

```json
{
  "{source_id}": 200,
  "status": "Done",
  "{output_url}": "/files/{path}/{filename}"
}
```

---

## 5. Business Logic Implementation

### 5.1 {Flow 1}

<!-- Use ASCII flow diagrams to illustrate multi-step business logic. -->

```
POST /api/{module}/{operation}
  |
  +- 1. Validate input ({describe validation})
  |
  +- 2. {Step 2 description}
  |
  +- 3. For each {item}:
  |     +- 3a. {Sub-step a}
  |     +- 3b. {Sub-step b}
  |     +- 3c. {Sub-step c}
  |
  +- 4. {Step 4 - e.g., submit to external service}
  |
  +- 5. Return {result description}
```

### 5.2 {Flow 2}

```
POST /api/{module}/{operation}
  |
  +- 1. Validate input ({describe validation})
  |
  +- 2. {Step 2}
  |
  +- 3. {Step 3 - e.g., update related entity via external service}
  |
  +- 4. {Step 4 - e.g., submit to workflow engine}
  |
  +- 5. Return {result}
```

### 5.3 {Callback / Event Flow} (if applicable)

<!-- Describe asynchronous callback flows. -->

```
{External Service} -> POST /api/{module}/{callback-endpoint}
  |
  +- 1. Parse callback payload ({describe fields})
  |
  +- 2. Update {record} status
  |
  +- 3. If {condition for completion}:
  |     +- Update {parent entity} status
  |     +- Update {related fields}
  |     +- Trigger notification
  |
  +- 4. If {condition for failure}:
        +- Update {parent entity} status
        +- {Cleanup actions}
        +- Trigger notification
```

#### Callback API

#### POST /api/{module}/{callback-endpoint}

Receives completion callbacks from {external service}.

**Request Example:**

```json
{
  "{entity_id}": 401,
  "{entity_type}": "{type}",
  "{step_identifier}": 2,
  "status": "Done",
  "output": {
    "{output_key}": "{output_value}"
  }
}
```

**Response**: `200 OK`

### 5.N {Validation Logic} (if applicable)

- **{Validation Type 1}**: {Description of validation approach}
- **{Validation Type 2}**: {Description of validation approach}

---

## 6. Integration with {External Service}

<!-- Describe how this backend interacts with external services. Separate frontend-direct calls from server-to-server calls. -->

The {Module Name} module backend delegates {operations} to {External Service}. The frontend calls {External Service} APIs **directly** (via BFF/Gateway) for:

| Operation | {External Service} API |
|-----------|------------------------|
| {Operation 1} | `GET/POST/PUT/DELETE /api/{service}/{resource}` |
| {Operation 2} | `GET /api/{service}/{resource}` |

The {Module Name} module backend calls {External Service} APIs **server-to-server** for:

| Operation | When |
|-----------|------|
| {Operation 1} | {Trigger condition} |
| {Operation 2} | {Trigger condition} |

---

## 7. Technology Stack

- **Framework**: FastAPI
- **ORM**: SQLAlchemy 2.x
- **Database**: PostgreSQL
- **Validation**: Pydantic v2
- **Async HTTP**: httpx (for inter-service calls)
- **{Additional}**: {description}
