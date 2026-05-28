# {Module Name} Module - UI/UX Design Specification

> **Document Version**: v1.0.0  
> **Effective Date**: {YYYY-MM-DD}  
> **Document Status**: Draft  
> **Reference**: [UI/UX Design Standards](../UI_UX_Design_Standards.md)

---

## Table of Contents

- [1. Overview](#1-overview)
- [2. Page Navigation Flow](#2-page-navigation-flow)
- [3. Page Index](#3-page-index)
- [4. {XX}-P01: {Page 1 Name}](#4-xx-p01-page-1-name)
- [5. {XX}-P02: {Page 2 Name}](#5-xx-p02-page-2-name)
- [6. {XX}-P03: {Page 3 Name}](#6-xx-p03-page-3-name)
- [...Additional Pages...]
- [{N}. Custom Controls](#n-custom-controls)
- [{N+1}. Special Interactions](#n1-special-interactions)
- [{N+2}. Status Tags Color Scheme](#n2-status-tags-color-scheme)
- [{N+3}. Technology Stack](#n3-technology-stack)

---

## 1. Overview

The {Module Name} module provides a comprehensive user interface for managing {domain description}. From the user's perspective, this module offers capabilities for:

- **{Capability Category 1}**: {Brief description}
- **{Capability Category 2}**: {Brief description}
- **{Capability Category N}**: {Brief description}

### 1.1 Module Menu Structure

The {Module Name} module appears in the left sidebar under the "{Module Name}" product section:

```
v {Module Name}
  +- {Menu Item 1}
  +- {Menu Item 2}
  +- {Menu Item 3}
  +- {Sub Group}
     +- {Sub Menu 1}
     +- {Sub Menu 2}
```

#### Menu-to-Page Mapping

| Menu Name | Page ID | Page Title |
|-----------|---------|------------|
| {Menu Item 1} | {XX}-P01 | {Page Title 1} |
| {Menu Item 2} | {XX}-P02 | {Page Title 2} |
| {Menu Item 3} | {XX}-P03, {XX}-P04 | {Page Title 3}, {Page Title 4} |

### 1.2 Architecture Note

> **Important**: From the user's perspective, the {Module Name} module provides all {domain} management capabilities. However, from the backend architecture perspective, {describe architectural separation if applicable}.

---

## 2. Page Navigation Flow

The following diagram illustrates the navigation relationships between all pages in the {Module Name} module. Boxes represent pages, arrows represent navigation, and arrow labels describe the triggering actions.

![Page Navigation Flow]({module_name}_UiUx_PageNavigationFlow.png)

> Source: [{module_name}_UiUx_PageNavigationFlow.mmd]({module_name}_UiUx_PageNavigationFlow.mmd)

### 2.1 Navigation Summary

| Source Page | Target Page | Trigger Action |
|-------------|-------------|----------------|
| {XX}-P01 | {XX}-P02 | {Action description} |
| {XX}-P02 | {XX}-P01 | Click Back button |

---

## 3. Page Index

| Page ID | Page Title | Layout Pattern | Primary Business Object |
|---------|------------|----------------|-------------------------|
| {XX}-P01 | {Page Title} | {Tree Page / List Page / Master-Detail / Detail Page / Editor Page} | {Business Object} |
| {XX}-P02 | {Page Title} | {Layout Pattern} | {Business Object} |

---

## 4. {XX}-P01: {Page Name - Tree Page}

![{XX}-P01 {Page Name}](ui_page_design/{XX}-P01%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P01%20%20{Page%20Name}/code.html)

**Layout**: Tree Page with Toolbar

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### 4.1 Page Description

<!-- Describe what the page displays, what information each node/row shows. -->

This page displays a hierarchical tree structure representing {domain data}. Each node shows:
- {Field 1}
- {Field 2}
- {Field N}

> **Note**: {Any important note about data display or behavior.}

### 4.2 Toolbar Buttons

| Button | Action | Description |
|--------|--------|-------------|
| Add | {Action} | {Description} |
| Delete | {Action} | {Description} |
| Refresh | {Action} | {Description} |

### 4.3 Tree Behavior

| Behavior | Description |
|----------|-------------|
| Default Expansion | {e.g., First 3 levels expanded by default} |
| Expand/Collapse | {Click arrow icon to expand or collapse nodes} |
| Edit | {e.g., Double-click node to edit name inline} |
| Selection | {Selection behavior} |
| Search | {Search behavior, if any} |

### 4.4 Node Display Columns

| # | Column | Attribute | Notes |
|---|--------|-----------|-------|
| 1 | {Column Name} | `{attribute}` | {notes} |
| 2 | {Column Name} | `{attribute}` | {notes} |

### 4.5 Edit Rules

- {Rule 1}
- {Rule 2}
- {Rule N}

---

## 5. {XX}-P02: {Page Name - Standard List Page}

![{XX}-P02 {Page Name}](ui_page_design/{XX}-P02%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P02%20%20{Page%20Name}/code.html)

**Layout**: Standard List Page

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### 5.1 Page Description

<!-- Describe what the list page displays and any special behaviors. -->

This page lists all {objects}. Each {object} is defined by {description}.

> **{Special Note}**: {e.g., This data is read-only, auto-generated, etc.}

### 5.2 Filter Section

| Filter | Type | Description |
|--------|------|-------------|
| {Filter 1} | {Text / Dropdown / Tag Input / Date Picker} | {Description} |
| {Filter 2} | {Type} | {Description} |

### 5.3 Table Columns

| # | Column | Attribute | Notes |
|---|--------|-----------|-------|
| 1 | {Column Name} | `{attribute}` | {notes} |
| 2 | {Column Name} | `{attribute}` | {notes} |

### 5.4 Action Buttons

| Button | Action |
|--------|--------|
| {Button} | {Action} |

### 5.5 Row Behavior

| Action | Trigger | Description |
|--------|---------|-------------|
| {Action} | {Trigger} | {Description} |

### 5.6 {Enum/Status} Color Scheme (if applicable)

| {Value} | Color |
|---------|-------|
| {Value 1} | {Color} |
| {Value 2} | {Color} |

---

## 6. {XX}-P03: {Page Name - Master-Detail Page}

![{XX}-P03 {Page Name}](ui_page_design/{XX}-P03%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P03%20%20{Page%20Name}/code.html)

**Layout**: Master-Detail ({Left Panel Description} -> {Right Panel Description})

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### 6.1 Page Description

This page provides a two-panel layout for {task description}:
- **Left Panel**: {Left panel content description}
- **Right Panel**: {Right panel content description}

### 6.2 Left Panel: {Left Panel Name}

#### 6.2.1 {Selector / Search} (if applicable)

| Component | Type | Description |
|-----------|------|-------------|
| {Selector} | {Type} | {Description} |

#### 6.2.2 {Left List}

**Display**: Single column showing {fields}

**Columns**:

| # | Column | Attribute | Notes |
|---|--------|-----------|-------|
| 1 | {Column Name} | `{attribute}` | {notes} |

**Icon Buttons** (if applicable):

| Button | Action |
|--------|--------|
| Create | {Action} |
| Edit | {Action} |
| Delete | {Action} |

**Behavior**:
- Single-click: {Behavior, e.g., Refresh right panel with selected item's data}
- Double-click: {Behavior, e.g., Enter edit mode}
- Sorted by {sort criteria}

### 6.3 Right Panel: {Right Panel Name}

**Style**: Standard List Page

#### 6.3.1 Filter Section

| Filter | Type | Description |
|--------|------|-------------|
| {Filter} | {Type} | {Description} |

#### 6.3.2 Table Columns

| # | Column | Attribute | Notes |
|---|--------|-----------|-------|
| 1 | {Column Name} | `{attribute}` | {notes} |

#### 6.3.3 Action Buttons

| Button | Action | Description |
|--------|--------|-------------|
| {Button} | {Action} | {Description} |

#### 6.3.4 Row Actions

| Action | Trigger | Description |
|--------|---------|-------------|
| View Detail | Double-click row | Navigate to {XX}-P{nn} in **view mode** (read-only) |
| Edit Detail | Select row + Click Edit button | Navigate to {XX}-P{nn} in **edit mode** |
| Select | Checkbox | Select for batch operations |

### 6.4 {Dialog / Panel} (if applicable)

<!-- Describe any dialogs that can be triggered from this page. -->

When clicking "{Action}" button:

| Field | Type | Description |
|-------|------|-------------|
| {Field 1} | {Type} | {Description} |
| {Field 2} | {Type} | {Description} |

**Confirmation Message** (if applicable):
1. {Message 1}
2. {Message 2}

---

## {N}. {XX}-P{nn}: {Page Name - Detail Page}

![{XX}-P{nn} {Page Name}](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/code.html)

**Layout**: Standard Detail Page

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### {N}.1 Page Description

<!-- Describe the detail page, including view mode vs edit mode, and what conditional sections exist. -->

This is the main detail page for viewing and editing {Object}. It includes:
- {Content category 1}
- {Content category 2}
- {Content category N}

### {N}.2 Attribute Display Order

| # | Attribute | Display | Edit Mode | Notes |
|---|-----------|---------|-----------|-------|
| 1 | `{attribute}` | {Display type} | {Read-only / Editable / Required} | {Notes} |
| 2 | `{attribute}` | {Display type} | {Read-only / Editable} | {Notes} |

### {N}.3 {Conditional Section} (if applicable)

Visible only when `{condition}`:

| # | Attribute | Display | Edit Mode | Notes |
|---|-----------|---------|-----------|-------|
| 1 | `{attribute}` | {Display type} | {Read-only / Editable} | {Notes} |

### {N}.4 {Media / File Section} (if applicable)

| # | Attribute | Display | Notes |
|---|-----------|---------|-------|
| 1 | `{file_url}` | URL + Download | {Description} |
| 2 | `{video_url}` | URL + Video Player | {Description} |

### {N}.5 Action Buttons

| Button | Action | Condition |
|--------|--------|-----------|
| Save | Save changes | Edit mode |
| Cancel | Discard changes | Edit mode |
| Edit | Enter edit mode | View mode |
| Delete | Delete with confirmation | View mode |
| Back | Return to source page (dynamic) | Always |

#### {N}.5.1 Back Button Behavior (if applicable)

The Back button dynamically returns to the page from which the user navigated:

| Source Page | Source Page Name | Entry Action | Back Returns To |
|-------------|------------------|--------------|-----------------|
| {XX}-P{nn} | {Page Name} | {Entry action} | {XX}-P{nn} |

> **Implementation Note**: The frontend should track the navigation source (e.g., via URL query parameter `?from={XX}-P{nn}` or React Router state) to enable correct Back navigation.

### {N}.6 Save Behavior

**Create Mode**:
1. User fills in required fields
2. User clicks Save
3. System creates {object} record
4. {Automatic side effects, e.g., creates related objects}
5. System navigates back to {XX}-P{nn}

**Edit Mode**:
1. User modifies fields
2. User clicks Save
3. System updates {object} record
4. {Automatic side effects}
5. System returns to view mode or navigates back

### {N}.7 Delete Behavior

1. User clicks Delete button
2. System shows confirmation dialog: "{Deletion warning message}"
3. User confirms deletion
4. System deletes {object} {and cascade deletes if applicable}
5. System navigates back to {XX}-P{nn}

---

## {N+1}. {XX}-P{nn}: {Page Name - Pipeline / Monitoring List Page} (if applicable)

![{XX}-P{nn} {Page Name}](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/code.html)

**Layout**: List Page with Pipeline Visualization

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### {N+1}.1 Page Description

This page displays all {Pipeline/Task} instances.

### {N+1}.2 Filter Section

| Filter | Type | Description |
|--------|------|-------------|
| Status | Dropdown | {Status enum values} |
| Date Range | Date Picker | Filter by creation date |
| {ID Field} | Text | Search by {ID type} |

### {N+1}.3 Table Columns

| # | Column | Attribute | Notes |
|---|--------|-----------|-------|
| 1 | ID | `id` | {Object} ID |
| 2 | {Source/Target} | `{reference_id}` | Link to {related object} |
| 3 | Started | `started_at` | Start time |
| 4 | Duration | `duration_seconds` | Duration in seconds |
| 5 | Status | `status` | Overall status with color |

### {N+1}.4 {Step/Phase} Columns (if applicable)

Additional columns for each {step/phase}:

| Step # | Step Name | Shows |
|--------|-----------|-------|
| 1 | {Step Name} | Step status |
| 2 | {Step Name} | Step status |

### {N+1}.5 Visualization Options (if applicable)

| Option | Description |
|--------|-------------|
| Table View | Traditional table layout |
| {Visual View} | Visual representation of {pipeline steps / progress} |

### {N+1}.6 Row Actions

| Action | Trigger | Description |
|--------|---------|-------------|
| View Details | Click row | Open detail modal |
| View {Related} | Link click | Navigate to {XX}-P{nn} |

### {N+1}.7 Status Colors

| Status | Color |
|--------|-------|
| {Status 1} | {Color} |
| {Status 2} | {Color} |

---

## {N+2}. {XX}-P{nn}: {Page Name - Editor Page} (if applicable)

**Layout**: Visual Editor Page

**Purpose**: {Describe the purpose of this page.}

**Business Process**: BP-{XX}-{ref}

### {N+2}.1 Page Description

This is a specialized visual editor for {content type}. Due to its complexity, detailed UI/UX design will be provided in a later phase.

### {N+2}.2 UI Reference

![{XX}-P{nn} {Page Name}](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/screen.png)

> Document HTML Preview: [code.html](ui_page_design/{XX}-P{nn}%20%20{Page%20Name}/code.html)

### {N+2}.3 Implementation Note

> **Note**: {Description of complexity and deferred detailed specifications.}

---

## {Last-3}. Custom Controls

<!-- List any custom UI controls required beyond the standard design system. -->

This module primarily uses standard UI components from the design system. The following custom controls may be required:

### {Last-3}.1 {Custom Control 1}

**Purpose**: {Description}

**Behavior**:
- {Behavior 1}
- {Behavior 2}
- {Behavior N}

### {Last-3}.2 {Custom Control 2}

**Purpose**: {Description}

**Behavior**:
- {Behavior 1}
- {Behavior 2}

### {Last-3}.3 {Custom Control N}

**Purpose**: {Description}

**Components**:
- {Component 1}
- {Component 2}

---

## {Last-2}. Special Interactions

<!-- Describe complex multi-step interactions that span multiple pages or components. -->

### {Last-2}.1 {Interaction 1}

**Trigger**: "{Button/Action}" on {XX}-P{nn} with {precondition}

**Flow**:
1. User {action 1}
2. User {action 2}
3. System {action 3}
4. User {action 4}
5. System {result}

### {Last-2}.2 {Interaction 2}

**Trigger**: "{Button/Action}" on {XX}-P{nn}

**Flow**:
1. User {action 1}
2. System {action 2}
3. {Result description}

### {Last-2}.N {Auto-Refresh Behavior} (if applicable)

**Trigger**: Viewing {page type} pages ({XX}-P{nn}, {XX}-P{mm})

**Behavior**:
- Page auto-refreshes every {N} seconds when {condition}
- Refresh stops when {stop condition}
- Manual refresh always available via Refresh button

---

## {Last-1}. Status Tags Color Scheme

### {Last-1}.1 {Status Type 1}

| Tag | Color | Background |
|-----|-------|------------|
| {Status} | {Color} | {Background} |
| {Status} | {Color} | {Background} |

### {Last-1}.2 {Status Type 2}

| Tag | Color | Background |
|-----|-------|------------|
| {Tag} | {Color} | {Background} |
| {Tag} | {Color} | {Background} |

---

## {Last}. Technology Stack

- **Framework**: React 19.x
- **UI Library**: Ant Design 6.2
- **State Management**: TBD
- **Routing**: React Router
- **{Additional}**: {Description}

---

> **End of Document**  
> Last Updated: {YYYY-MM-DD}
