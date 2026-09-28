# Phase 2: Requirement Analysis Phase

## Overview
This phase details the functional and non-functional requirements necessary to enforce client-side data validation and dynamic field controls on the Incident table in ServiceNow.

---

## 📋 Functional Requirements

* **FR-01 (UI Policy Condition):** The system must execute a UI Policy when the `Impact` field value is set to `1 - High`.
* **FR-02 (Mandatory Assignment Group):** When `Impact` is `1 - High`, the `Assignment group` field must dynamically become mandatory.
* **FR-03 (Read-Only Urgency):** When `Impact` is `1 - High`, the `Urgency` field must dynamically become read-only to prevent user tampering.
* **FR-04 (Reverse Behavior):** When `Impact` is set to any value other than `1 - High`, field rules applied by the UI Policy must automatically revert (`Reverse if false = true`).
* **FR-05 (Auto-Populate Urgency):** Upon changing `Impact` to `1 - High`, an `onChange` Client Script must automatically populate `Urgency` to `1 - High` and display an informational banner message.
* **FR-06 (Save Validation):** An `onSubmit` Client Script must prevent saving or submitting an Incident if `Impact` is `1 - High` and the `Assigned To` field is left blank.
* **FR-07 (List Edit Restriction):** An `onCellEdit` Client Script must block attempts to edit the `State` field directly from the list view, displaying an alert dialog directing users to open the form.

---

## ⚙️ Technical & Non-Functional Requirements

| ID | Category | Requirement Description |
| :--- | :--- | :--- |
| **NFR-01** | Performance | Client Scripts must execute within `< 200ms` without degrading form rendering performance. |
| **NFR-02** | User Experience | Error messages and info banners must clearly explain why submission is blocked or why field values changed. |
| **NFR-03** | Data Integrity | Field constraints must enforce data completeness before database submission. |
| **NFR-04** | Compatibility | UI Policies and Client Scripts must be configured for Desktop and Mobile UI compatibility (`UI Type = All`). |

---

## 🔍 Data Mapping Table

| System Field Name | Display Name | Field Type | Target Table | Validation Rules Applied |
| :--- | :--- | :--- | :--- | :--- |
| `impact` | Impact | Choice | `incident` | Trigger field (`1 = High`) |
| `urgency` | Urgency | Choice | `incident` | Read-only via UI Policy Action; Auto-set via `onChange` |
| `assignment_group` | Assignment group | Reference | `incident` | Mandatory via UI Policy Action |
| `assigned_to` | Assigned To | Reference | `incident` | Save validation via `onSubmit` |
| `state` | State | Choice | `incident` | Restricted from inline list edit via `onCellEdit` |
