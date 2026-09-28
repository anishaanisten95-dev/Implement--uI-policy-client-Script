# Phase 1: Brainstorming & Ideation Phase

## Problem Statement
Incident management processes frequently face data consistency issues due to missing fields, incomplete triage, or incorrect entries during incident submission. Relying solely on user manual inputs leads to incomplete records, delayed routing, and SLA compliance issues. Enforcing validation rules directly on the client interface prevents data entry mistakes before records hit the database.

## Proposed Solution
Implement client-side controls on the Incident table using ServiceNow UI Policies and Client Scripts (`onChange`, `onSubmit`, and `onCellEdit`). This solution dynamically sets field attributes, automates updates, prevents invalid form submissions, and restricts improper inline edits.

## Key Capabilities & Scope
1. **Dynamic Visibility & Mandatory Constraints:** Auto-set `Assignment group` as mandatory when `Impact` is High (`1`).
2. **Automated Field Updates:** Auto-set `Urgency` to High (`1`) whenever `Impact` changes to High.
3. **Form-Level Read-Only Control:** Set `Urgency` to read-only when `Impact` is High.
4. **Save Validation:** Prevent form submission if `Assigned To` is blank for high-impact incidents.
5. **List View Editing Control:** Restrict direct updates to the `State` field from the list view via inline editing.
