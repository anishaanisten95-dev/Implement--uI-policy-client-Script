# Phase 3: Project Design Phase

## Overview
The project design phase defines the logical control flow, client-side script architecture, and field behavior rules implemented on the ServiceNow Incident form and list view.

---

## 📐 Client-Side Execution Architecture

```text
                          ┌─────────────────────────────┐
                          │   Incident Form/List View   │
                          └──────────────┬──────────────┘
                                         │
                 ┌───────────────────────┼───────────────────────┐
                 │                       │                       │
                 ▼                       ▼                       ▼
       ┌───────────────────┐   ┌───────────────────┐   ┌───────────────────┐
       │   UI Policy &     │   │ onChange Client   │   │  onSubmit Client  │
       │   Policy Action   │   │      Script       │   │      Script       │
       └─────────┬─────────┘   └─────────┬─────────┘   └─────────┬─────────┘
                 │                       │                       │
                 ▼                       ▼                       ▼
          Impact = High            Impact = High            Impact = High
       └─► Urgency: Read-only   └─► Sets Urgency to High └─► Blocks save if
       └─► Assignment Group     └─► Info message shown      Assigned To is empty
           Mandatory
                                                                 │ (List View)
                                                                 ▼
                                                       ┌───────────────────┐
                                                       │ onCellEdit Client │
                                                       │      Script       │
                                                       └─────────┬─────────┘
                                                                 │
                                                                 ▼
                                                          Edits on State
                                                          blocked with alert
