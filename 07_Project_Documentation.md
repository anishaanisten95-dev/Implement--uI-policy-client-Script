# Phase 7: Project Documentation Phase

## Admin Deployment Guide
1. Log in to your ServiceNow instance with administrative privileges.
2. **Deploy UI Policy:**
   - Go to **System UI -> UI Policies**.
   - Create policy `High Impact Control` on table `Incident` with condition `Impact = 1`.
   - Add UI Policy Actions for `Assignment group` (Mandatory) and `Urgency` (Read-only).
3. **Deploy Client Scripts:**
   - Go to **System UI -> Client Scripts**.
   - Create `onChange` script on field `Impact`.
   - Create `onSubmit` script for `Assigned To` mandatory validation.
   - Create `onCellEdit` script on field `State`.
4. Verify that all rules are active.

## User Operational Guide
- **Incident Creation/Editing:** When creating or editing an incident with High Impact, the system will automatically boost the Urgency rating to High and lock it.
- **Required Fields:** Ensure `Assignment group` and `Assigned To` are populated prior to submitting a High Impact incident.
- **List View Restrictions:** Editing the `State` field must be done within the incident form view; inline updates in list views are disabled by administrative policy.
