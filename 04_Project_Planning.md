# Phase 4: Project Planning Phase

## Overview
The project planning phase outlines the structured roadmap, Work Breakdown Structure (WBS), and key milestones for implementing client-side validation and automated field controls on the ServiceNow Incident table.

---

## 🛠️ Work Breakdown Structure (WBS)

### 1. Project Initialization & Instance Readiness
* **1.1 Platform Access Verification:** Log in to the ServiceNow instance with administrative or configuration access.
* **1.2 Schema & Field Verification:** Confirm field names on `Incident [incident]` table (`impact`, `urgency`, `assignment_group`, `assigned_to`, `state`).

### 2. UI Policy & Actions Implementation
* **2.1 UI Policy Creation:** Create `High Impact Control` UI Policy triggered when `Impact` is `1 - High` with `Reverse if false = true`.
* **2.2 Policy Action 1:** Configure `Assignment group` field action to set `Mandatory = true`.
* **2.3 Policy Action 2:** Configure `Urgency` field action to set `Read-only = true`.

### 3. Client Scripts Development
* **3.1 onChange Client Script:** Implement `Auto set urgency for high impact` on the `Impact` field to auto-populate `Urgency = 1` and display an info banner.
* **3.2 onSubmit Client Script:** Implement `Prevent save if Assigned To missing` to validate that `Assigned To` is populated when `Impact` is High.
* **3.3 onCellEdit Client Script:** Implement `Prevent state change via list edit` on the `State` field to restrict direct updates in list view.

### 4. Quality Assurance & Validation
* **4.1 Form Level Testing:** Execute positive and negative scenarios for High Impact condition triggers and `onSubmit` validation blocks.
* **4.2 Reverse Logic Testing:** Confirm UI Policy rules revert when `Impact` is set back to Medium/Low.
* **4.3 List View Testing:** Verify `onCellEdit` script intercepts inline edits on the `State` column.

### 5. Documentation & Artifact Handover
* **5.1 Repository Setup:** Structure files across 8 phases in GitHub.
* **5.2 Video Demonstration:** Record screen-share demo covering all implemented controls and upload to Google Drive.

---

## 📅 Task Sequence & Milestone Schedule

```text
[Task 1: Setup] ──► [Task 2: UI Policy & Actions] ──► [Task 3: Client Scripts] ──► [Task 4: Testing Matrix] ──► [Task 5: Submission]
