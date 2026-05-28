# UI/UX Design Standards

> **Document Version**: v1.0.0  
> **Effective Date**: 2026-02-09  
> **Document Status**: Draft

---

## Document Purpose

This document defines the **UI/UX Design Standards** for the Ascend Verification System platform. It serves as a comprehensive design specification that enables:

1. **AI-Assisted Design**: AI systems can automatically generate UI/UX designs based on business requirements by following these standards, minimizing manual design effort.

2. **Design Consistency**: All modules across the platform maintain a unified visual language and interaction patterns.

3. **Development Efficiency**: Developers can implement UI components without extensive design documentation for each feature.

4. **Quality Assurance**: Provides clear criteria for reviewing and validating UI implementations.

## How to Use This Document

When designing a new UI page or component:

1. **AI Design Flow**: 
   - Input: Business Process description (from `*_business.md`)
   - Reference: This design standards document
   - Output: UI/UX design specification (in `*_tech_UiUx.md`)

2. **Manual Design Flow**:
   - Designers reference this document for patterns and guidelines
   - Deviations from standards must be documented with justification

---

## Table of Contents

- [1. Design Principles](#1-design-principles)
- [2. Layout Patterns](#2-layout-patterns)
- [3. Navigation Patterns](#3-navigation-patterns)
- [4. Data Display Patterns](#4-data-display-patterns)
- [5. Form Patterns](#5-form-patterns)
- [6. Action Patterns](#6-action-patterns)
- [7. Feedback Patterns](#7-feedback-patterns)
- [8. Common Page Templates](#8-common-page-templates)
- [9. Component Library Reference](#9-component-library-reference)
- [10. Accessibility Standards](#10-accessibility-standards)

---

## 1. Design Principles

### 1.1 Color Theme

- **Default Theme**: Dark theme for all platform pages
- **Tag Colors**: When displaying tags or badges, use visually appealing colored backgrounds to distinguish different states or categories

### 1.2 Business Object Centric Design

All UI pages are designed around **business objects**. For each business object:

- **List Page**: Default page for listing, searching, and sorting objects
- **Detail Page**: Default page for viewing and editing all attributes of a selected object
- **Create Page**: Uses empty Detail Page in edit mode (see Section 8.4)

This ensures consistent user experience across all modules.

### 1.3 Portal Module Scope

> **Note**: Login page, logout functionality, and feedback pages are defined in the **Unified Portal Module** requirements (`unified-web-portal_business.md`), not in this design standards document. This document focuses on product interaction page patterns.

---

## 2. Layout Patterns

### 2.1 Portal Framework (Global Layout)

The **Unified Portal Module** provides the base page framework after user login:

```
+-----------------------------------------------------------------+
|  [Logo]                              [User Avatar] [System Menu]|  <- Header Bar
+--------------+--------------------------------------------------+
|              |                                                  |
|   Product    |                                                  |
|   Menu       |              Main View Area                      |
|   (Multi-    |         (Product Interaction Pages)              |
|    level)    |                                                  |
|              |                                                  |
|   [Collapse] |                                                  |
+--------------+--------------------------------------------------+
```

#### Header Bar (Top Row)
| Position | Component | Description |
|----------|-----------|-------------|
| Left | Logo | Platform logo |
| Right | User Avatar | User profile icon with dropdown menu |
| Right | System Menu | User Profile, System Info, Logout, Feedback |

#### Left Sidebar (Multi-level Menu)
- **Collapsible**: Click to collapse/expand to the left
- **Product Level**: Outer layer, each product is a collapsible section (collapsed shows only product name)
- **Menu Tree**: Each product contains a 2-level menu tree maximum

#### Main View Area (Right)
- Displays actual product interaction pages
- Full width when sidebar is collapsed

### 2.2 Master-Detail Layout: Single Column List + Large List

> **Note**: This is a special layout pattern. Must be explicitly specified in module UI design document with left/right object types and their trigger relationship.

```
+----------------+-------------------------------------------------+
|  Single Column |                                                 |
|  List (Parent) |           Large List (Child Objects)            |
|                |                                                 |
|  [+ - EDIT VIEW]    |   [Filter] [Search]                             |
|  ------------- |   -----------------------------------------     |
|  Item A >      |   | Col1 | Col2 | Col3 | Col4 | Col5 |          |
|  Item B        |   |------|------|------|------|------|          |
|  Item C        |   | ...  | ...  | ...  | ...  | ...  |          |
|  Item D        |                                                 |
|                |   Page 1/10  Total: 500 records                 |
+----------------+-------------------------------------------------+
```

#### Left Single Column List
- Displays parent/upstream business objects
- **No filter functionality**
- Default sorted alphabetically by display text
- **Single-click only**: Click refreshes right large list
- Icon buttons: Create, Delete, Edit, View Detail
- Clicking button navigates to selected object's detail page

#### Right Large List
- Standard List Page style (see Section 8.1)
- Shows child objects of selected left item

### 2.3 Master-Detail Layout: Tree + Large List

Same display logic as "Single Column List + Large List", except:
- Left side is a **logical tree structure** instead of single column list
- Must be explicitly specified in module UI design document

---

## 3. Navigation Patterns

### 3.1 Product Menu Structure

The left sidebar menu follows this hierarchy:

```
v Product A (Section - Collapsible)
  +- Menu Level 1
  |  +- Menu Level 2
  |  +- Menu Level 2
  +- Menu Level 1
     +- Menu Level 2
     +- Menu Level 2

> Product B (Collapsed - Shows name only)

v Product C (Section - Collapsible)
  +- ...
```

### 3.2 Page Navigation

- **List -> Detail**: Double-click row OR select + click "View" button
- **Detail -> List**: Back button navigation
- **Cross-module**: Via left sidebar menu

> **Note**: Breadcrumb navigation is **not provided** in this platform. Use back button or sidebar menu for navigation.

---

## 4. Data Display Patterns

### 4.1 Table/List Display Rules

| Rule | Specification |
|------|---------------|
| Columns | Select most important attributes only, **max 5 columns** |
| Rows per page | Fixed at **50 rows** (user cannot adjust). Exception: embedded child lists use 30 rows/page |
| Pagination | Bottom of list: page navigation + total pages + total records |
| Selection | Windows-style: single-click select, Ctrl+click multi-select, Shift+click range select |
| Double-click | Navigate to read-only detail page |
| Sorting | Click column header to sort. First click: ascending (small to large). Second click: descending (large to small) |
| Empty State | Show table header with empty grid structure (visible row/column borders). Do not show blank area |
| Image Column | If object has image attribute, display as **2nd column** (max 400x400), 1st column is usually ID |

### 4.2 Tree List Page

A special variant of the list page where the first column has tree structure relationships.

```
+-----------------------------------------------------------------+
|  [Title: Tree List Name]                                        |
+-----------------------------------------------------------------+
|  [Create] [View] [Edit] [Delete]                                |
+----------------------+----------+----------+----------+---------+
|  Name (Tree)         |  Col 2   |  Col 3   |  Col 4   |  Col 5  |
+----------------------+----------+----------+----------+---------+
|  v Parent A          |  ...     |  ...     |  ...     |  ...    |
|    +- Child A1       |  ...     |  ...     |  ...     |  ...    |
|    +- Child A2       |  ...     |  ...     |  ...     |  ...    |
|  > Parent B          |  ...     |  ...     |  ...     |  ...    |
|  v Parent C          |  ...     |  ...     |  ...     |  ...    |
|    +- Child C1       |  ...     |  ...     |  ...     |  ...    |
+----------------------+----------+----------+----------+---------+
```

#### Tree List Rules
- **No pagination** by default (loads entire table)
- **No filter** by default
- **Empty State**: Display "Empty Tree" text at root node position
- If module UI requires search:
  - Tree is limited to **2 levels**
  - Search criteria applies to **first level objects only**
  - Expand shows child objects of first level

---

## 5. Form Patterns

### 5.1 Filter Form (List Page)

| Element | Specification |
|---------|---------------|
| Layout | Max **4 filters per row**, overflow to next row |
| ID Filter | Comma-separated ID list input |
| Enum Filter | Dropdown select |
| Date Filter | Date range picker (start - end) |
| Keyword Filter | Text input (for objects with description field) |
| Default Values | All filters empty (no filter applied) |
| Submit | Large "Search" button at the end |

### 5.2 Detail Form (Edit Mode)

| Rule | Specification |
|------|---------------|
| Display Order | Attributes ordered by priority (top to bottom) |
| Layout | Single column; use **dual column** if content exceeds one screen |
| Validation | Inline validation on blur, form validation on submit |
| Unsaved Changes | Prompt user when leaving page with unsaved edits |
| Read-only Fields | `id`, `created_at`, `updated_at` are always read-only even in edit mode |
| File Fields | Display file path (truncate middle with "..." if too long). Show upload button in edit mode |
| Image Fields | Display image max 600x600 on its own row. Show upload button in edit mode |

---

## 6. Action Patterns

### 6.1 List Page Action Buttons

Action buttons appear at the **top of the list**, above the table header:

```
[Create] [View] [Edit] [Delete]
-----------------------------------------
| Col1 | Col2 | Col3 | Col4 | Col5 |
```

| Button | Action | Selection Required |
|--------|--------|--------------------|
| Create | Open create form (new object) | No |
| View | Open read-only detail page | Yes (single) |
| Edit | Open editable detail page | Yes (single) |
| Delete | Confirmation dialog -> Delete selected | Yes (single/multi) |

### 6.2 Detail Page Action Buttons

| State | Buttons |
|-------|------|
| Read-only Mode | [Edit] |
| Edit Mode | [Save] [Cancel] |

### 6.3 Delete Confirmation

Always show confirmation dialog before delete:

```
+-------------------------------------+
|  Confirm Delete                     |
+-------------------------------------+
|  Are you sure you want to delete    |
|  the selected item(s)?              |
|                                     |
|  This action cannot be undone.      |
|                                     |
|         [Cancel]  [Delete]          |
+-------------------------------------+
```

---

## 7. Feedback Patterns

### 7.1 Page Loading

No special loading indicator. The page simply appears frozen until content loads.

### 7.2 Success Notification

Displayed when an operation completes successfully:

```
+-------------------------------------+
|   Light Green Background     |
|                                     |
|           OK                        |
|                                     |
|  [Success message text here]        |
|                                     |
+-------------------------------------+
      (Auto-dismiss after 2 seconds)
```

| Property | Value |
|----------|-------|
| Position | Center of screen |
| Style | Light green sticky note |
| Title | "OK" |
| Content | Specific success message |
| Dismiss | Auto-dismiss after **2 seconds** (no button) |

### 7.3 Error Notification

Displayed when an error or unexpected exception occurs:

```
+-------------------------------------+
|   Yellow Background           |
|                                     |
|       ERROR  (Red Bold)             |
|                                     |
|  [Error message content here]       |
|                                     |
|            [OK]                     |
+-------------------------------------+
```

| Property | Value |
|----------|-------|
| Position | Center of screen |
| Style | Yellow sticky note |
| Title | "ERROR" (red, bold) |
| Content | Error message details |
| Dismiss | User must click **[OK]** button to dismiss |

### 7.4 Empty State

| Context | Display |
|---------|---------||
| Empty List | Show table header with empty grid structure (visible borders) |
| Empty Tree | Show "Empty Tree" text at root node position |

---

## 8. Common Page Templates

### 8.1 List Page Template

```
+-----------------------------------------------------------------+
|  [Title: Business Object List Name]                             |
+-----------------------------------------------------------------+
|  Filter Section                                                 |
|  [ID List] [Enum Dropdown] [Date Range] [Keyword]  [SEARCH Search]  |
|  (max 4 per row, more filters on next row)                      |
+-----------------------------------------------------------------+
|  [Create] [View] [Edit] [Delete]                                |
+-----------------------------------------------------------------+
|  | Col1 | Col2 | Col3 | Col4 | Col5 |  (max 5 columns)          |
|  |------|------|------|------|------|                           |
|  | ...  | ...  | ...  | ...  | ...  |                           |
|  | ...  | ...  | ...  | ...  | ...  |                           |
|  | ...  | ...  | ...  | ...  | ...  |  (50 rows per page)       |
+-----------------------------------------------------------------+
|  [< Prev] Page 1/10 [Next >]    Total: 500 records              |
+-----------------------------------------------------------------+
```

#### List Page Specifications

| Element | Specification |
|---------|---------------|
| Title | Clearly indicates business object type |
| Filters | ID list, enum dropdowns, date range, keyword (if has description) |
| Filter Layout | Max 4 per row |
| Action Buttons | Create, View, Edit, Delete |
| Table Columns | Max 5 most important attributes |
| Rows per Page | 50 (fixed, user cannot change) |
| Selection | Windows-style (single-click, Ctrl/Shift for multi-select) |
| Double-click | Navigate to read-only detail page |
| Pagination | Page navigation + total pages + total records |

### 8.2 Detail Page Template

```
+-----------------------------------------------------------------+
|  [Title: Object Name/ID]                    [Edit] or [Save]    |
+-----------------------------------------------------------------+
|  Attribute Section (All attributes, ordered by priority)       |
|  +---------------------------------------------------------+    |
|  | Attribute 1: Value                                      |    |
|  | Attribute 2: Value                                      |    |
|  | Attribute 3: Value          Attribute 4: Value          |    |
|  | Attribute 5: Value          Attribute 6: Value          |    |
|  | ...                                                     |    |
|  +---------------------------------------------------------+    |
|                                                                 |
|  Child Object List (if specified in module UI doc)              |
|  +---------------------------------------------------------+    |
|  | [Create] [View] [Edit] [Delete]                         |    |
|  | | Col1 | Col2 | Col3 | Col4 | Col5 |                    |    |
|  | |------|------|------|------|------|                    |    |
|  | | ...  | ...  | ...  | ...  | ...  |  (30 rows/page)    |    |
|  | [< Prev] Page 1/5 [Next >]  Total: 150 records          |    |
|  +---------------------------------------------------------+    |
|                                                                 |
+-----------------------------------------------------------------+
      <-> Single vertical scrollbar for entire page
```

#### Detail Page Specifications

| Element | Specification |
|---------|---------------|
| Attributes | Display ALL attributes, ordered by priority |
| Layout | Single column; dual column if exceeds one screen |
| Default Mode | Read-only |
| Mode Switch | Edit button (read-only) / Save button (edit mode) |
| Unsaved Warning | Prompt when leaving page with unsaved changes |
| Child List | If specified: 30 rows/page, action buttons only, no filters |
| Scrolling | **Single vertical scrollbar** for entire page (not separate scroll areas) |

### 8.3 Page Mode Parameters

Detail pages can be opened with URL parameters:

| Parameter | Value | Description |
|-----------|-------|-------------|
| `mode` | `view` | Open in read-only mode (default) |
| `mode` | `edit` | Open in edit mode |

### 8.4 Create Page

Create page uses an **empty Detail Page in edit mode** with the following rules:

| Rule | Specification |
|------|---------------|
| Template | Same as Detail Page (Section 8.2) |
| Mode | Edit mode (fields editable) |
| Read-only Fields | `id`, `created_at`, `updated_at` are read-only (auto-generated by system) |
| File/Image Fields | Show upload button; file path populated after upload |
| Submit | Save button creates new object |

---

## 9. Component Library Reference

> **TODO**: Reference to Ant Design components with platform-specific usage guidelines

---

## 10. Accessibility Standards

> **TODO**: Define accessibility requirements (WCAG compliance, keyboard navigation, screen reader support)

---

## Appendix A: Design Pattern Examples

> **TODO**: Provide concrete examples mapping business processes to UI patterns

---

> **End of Document**  
> Last Updated: 2026-02-09
