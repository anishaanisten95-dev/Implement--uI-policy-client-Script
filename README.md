# Implementation of Client Scripts & UI Policies on Incident Management

![ServiceNow](https://img.shields.io/badge/Platform-ServiceNow-green.svg)
![Build](https://img.shields.io/badge/Status-Completed-brightgreen.svg)
![Phases](https://img.shields.io/badge/Phases-1%20to%208%20Complete-blue.svg)

## 📌 Project Overview
This project demonstrates client-side data enforcement within ServiceNow's Incident table. By combining UI Policies, UI Policy Actions, and Client Scripts (`onChange`, `onSubmit`, `onCellEdit`), this implementation guarantees clean data entry, reduces user error during incident triage, and protects critical workflows against unauthorized updates.

---

## 📂 Repository Structure & Phase Documentation

- 📁 [Phase 1: Brainstorming & Ideation Phase](./01_Brainstorming_and_Ideation/Problem_Statement_and_Ideation.md)
- 📁 [Phase 2: Requirement Analysis Phase](./02_Requirement_Analysis/Requirements_Specification.md)
- 📁 [Phase 3: Project Design Phase](./03_Project_Design/Architecture_and_Workflow.md)
- 📁 [Phase 4: Project Planning Phase](./04_Project_Planning/Implementation_Plan_and_WBS.md)
- 📁 [Phase 5: Project Development Phase](./05_Project_Development/)
- 📁 [Phase 6: Project Testing Phase](./06_Project_Testing/Test_Cases_and_Matrix.md)
- 📁 [Phase 7: Project Documentation Phase](./07_Project_Documentation/User_and_Admin_Guide.md)
- 📁 [Phase 8: Project Demonstration Phase](./08_Project_Demonstration/Demo_Script_and_Drive_Link.md)

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
