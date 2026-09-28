# Phase 6: Project Testing Phase

## Overview
The testing phase validates that all client-side configurations (UI Policies, UI Policy Actions, and Client Scripts) function as expected under various user interactions on the Incident form and list view.

---

## 🧪 Test Execution Matrix

| Test ID | Test Scenario | Steps / Action | Expected Outcome | Status |
| :--- | :--- | :--- | :--- | :--- |
| **TC-01** | High Impact UI Policy Trigger | Open a new/existing Incident form and change `Impact` to `1 - High`. | • `Urgency` auto-sets to `1 - High`<br>• Info message banner displays<br>• `Urgency` field becomes read-only<br>• `Assignment group` becomes mandatory | **PASS** |
| **TC-02** | onSubmit Save Prevention | Leave `Assigned To` empty while `Impact` is set to `1 - High` and click **Submit**. | • Record submission is cancelled<br>• Error box appears under the `Assigned To` field | **PASS** |
| **TC-03** | Successful Form Submission | Populate `Assigned To` field while `Impact` is `1 - High` and click **Submit**. | Incident record updates and saves successfully without validation errors | **PASS** |
| **TC-04** | Reverse Condition Test | Change `Impact` from `1 - High` to `2 - Medium` on an open Incident. | • `Urgency` field becomes editable again<br>• Mandatory constraint on `Assignment group` is removed | **PASS** |
| **TC-05** | List Edit Block (`State`) | Navigate to Incident list view (`Incident -> All`) and double-click the `State` field to inline edit. | • Alert pop-up window appears<br>• Edit is blocked and cancelled (`callback(false)`) | **PASS** |
| **TC-06** | Form-Based State Update | Open an Incident form, change the `State` field value, and click **Update**. | State updates and saves successfully through the form layout | **PASS** |

---

## 📊 Summary of Verification

- **UI Policy & Policy Actions:** Validated mandatory status on `Assignment group` and read-only behavior on `Urgency`.
- **onChange Client Script:** Confirmed auto-setting of `Urgency` to `1` and banner message output when `Impact` becomes `1`.
- **onSubmit Client Script:** Verified block on save when `Assigned To` is blank under high impact conditions.
- **onCellEdit Client Script:** Verified list view state modifications are properly intercepted and blocked via pop-up alert.

  <img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/a5c7c526-84dc-4967-b07a-dfa630f67388" />
  <img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/80e22495-060e-4b7f-8e0a-44635bc86d63" />
  


