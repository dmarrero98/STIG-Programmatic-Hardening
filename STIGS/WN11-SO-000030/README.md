# 🛡️ STIG Remediation: WN11-SO-000030

**Title:** Audit policy using subcategories must be enabled  
**STIG ID:** [WN11-SO-000030](https://stigaview.com/products/win11/v2r3/WN11-SO-000030/)
**Severity:** Medium  
**CCI:** CCI-000169  
**Status:** Remediated ✅  

---

## 📝 Description

Maintaining an audit trail of system activity logs can help identify configuration errors, troubleshoot service disruptions, and analyze compromises.  
This STIG ensures that **advanced audit policy subcategories** override legacy audit categories for more precise auditing.


---

## 💻 Remediation Steps

1. **Registry Method (Manual / Scripted):**

```powershell
#Print current "process creation" policy setting
$audit = auditpol.exe /get /subcategory:"Process Creation"
Write-Output "Current setting:" 
Write-Output $audit

#Enable auditing of failed process creation attempts
auditpol.exe /set /subcategory:"Process Creation" /failure:enable

#Recheck "process creation" policy setting again
$audit2 = auditpol.exe /get /subcategory:"Process Creation"
Write-Output "Second check :)"
Write-Output $audit2
```

<img alt="image" src="https://github.com/dmarrero98/STIG-Programmatic-Hardening/blob/main/STIGS/WN11-SO-000030/output.png">
