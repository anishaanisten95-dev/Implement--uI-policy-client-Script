# Phase 5: Project Development Phase

This phase contains the exact configurations and client-side source code implemented on the Incident (`incident`) table in ServiceNow.

---

## 1. UI Policy Configuration

### Policy Details
* **Name:** `High Impact Control`
* **Table:** `Incident [incident]`
* **Active:** `true`
* **Reverse if false:** `true`
* **Condition:** `Impact` `is` `1 - High`

### UI Policy Actions
| Field Name | Mandatory | Read Only | Visible |
| :--- | :--- | :--- | :--- |
| **Assignment group** | `True` | `Leave alone` | `Leave alone` |
| **Urgency** | `Leave alone` | `True` | `Leave alone` |

---

## 2. Client Scripts Implementation

### A. onChange Client Script
* **Name:** `Auto set urgency for high impact`
* **Table:** `Incident [incident]`
* **UI Type:** `All`
* **Type:** `onChange`
* **Field name:** `Impact`
* **Active:** `true`

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
