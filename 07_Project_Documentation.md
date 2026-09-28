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
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/8f18585e-543e-441d-8d75-dc27aa153136" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/ca809266-61a4-4f6a-8460-4120521b0281" />

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/aeb2b1e2-e928-4f1f-a74e-ec86c12da7fd" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/487c8c3d-ecd9-4e7d-bb6d-2431545bc989" />
<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/74609a27-6ea1-49db-b6e8-56c3dcc6375f" />


