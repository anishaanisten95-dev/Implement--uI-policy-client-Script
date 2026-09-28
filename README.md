# Implementation of Client Scripts & UI Policies on Incident Management

![ServiceNow](https://img.shields.io/badge/Platform-ServiceNow-green.svg)
![Build](https://img.shields.io/badge/Status-Completed-brightgreen.svg)
![Phases](https://img.shields.io/badge/Phases-1%20to%208%20Complete-blue.svg)

## 📌 Project Overview
This project demonstrates client-side data enforcement within ServiceNow's Incident table. By combining UI Policies, UI Policy Actions, and Client Scripts (`onChange`, `onSubmit`, `onCellEdit`), this implementation guarantees clean data entry, reduces user error during incident triage, and protects critical workflows against unauthorized updates.

---

## ⚙️ Configuration & Logic Summary

### 1. UI Policy: High Impact Control
* **Table:** `Incident [incident]`
* **Condition:** `Impact is 1 - High`
* **Reverse if false:** `true`
* **Actions:**
  * `Assignment group` -> Mandatory: `true`
  * `Urgency` -> Read-only: `true`

---

### 2. Client Scripts Implementation

#### A. onChange Script — `Auto set urgency for high impact`
* **Table:** `Incident` | **Type:** `onChange` | **Field:** `Impact`
```javascript
function onChange(control, oldValue, newValue, isLoading) {
    if (isLoading || newValue == '') {
        return;
    }

    if (newValue == '1') {
        g_form.setValue('urgency', '1');
        g_form.addInfoMessage('Urgency set to High for High impact incident.');
    }
}
