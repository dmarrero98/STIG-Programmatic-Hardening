# 🛡️ STIG Remediation: WN11-AU-000585

**Title:** Process Creation Auditing Enabled  
**STIG ID:** [WN11-AU-000585](https://stigaview.com/products/win11/v2r3/WN11-AU-000585/)  
**Severity:** Medium  
**Status:** Remediated ✅  

---

## 📝 Description

Enabling process creation auditing allows administrators to track which processes are launched on a system.  
This is critical for **forensic investigations**, detecting suspicious activity, and maintaining a secure audit trail.

---

## 💻 Remediation Steps

1. **PowerShell / Registry Method:**

```powershell
#first check
$audit = Get-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Lsa" -Name "SCENoApplyLegacyAuditPolicy"
Write-Output "This is the initial check:"
Write-Output "$audit"

#Remediate the "SCENoApplyLegacyAuditPolicy does not exist" error
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Lsa" `
                 -Name "SCENoApplyLegacyAuditPolicy" `
                 -PropertyType DWord `
                 -Value 1 -Force

#second check
$audit2 = Get-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Lsa" -Name "SCENoApplyLegacyAuditPolicy"
Write-Output "This is the post remediation check:"
Write-Output "$audit2"
```

