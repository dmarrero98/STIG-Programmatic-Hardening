# 🛡️ STIG Compliance & Hardening

This repository contains examples of **STIG remediation** performed programmatically using PowerShell.  
The goal is to ensure systems are configured according to **Windows 11 security requirements** and maintain compliance.  

---

## ✅ Remediated STIGs

| STIG ID        | Title                                                | Status       | Notes / Remediation                                         |
|----------------|------------------------------------------------------|-------------|------------------------------------------------------------|
| [WN11-SO-000030](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-SO-000030) | Audit policy using subcategories must be enabled   | Remediated ✅ | `AuditPol.exe` set for Process Creation failures          |
| [WN11-AU-000585](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-AU-000585) | Legacy Audit Policy Disabled                         | Remediated ✅ | `SCENoApplyLegacyAuditPolicy` = 1                         |
| [WN11-CC-000100](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000100) | Prevent downloading print drivers over HTTP         | Remediated ✅ | `DisableWebPnPDownload` = 1 under `HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers` |
| [WN11-CC-000110](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000110) | Disable HTTP printing                                 | Remediated ✅ | `DisableHTTPPrinting` = 1 under `HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Printers` |
| [WN11-CC-000280](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000280) | Remote Desktop always prompt for password            | Remediated ✅ | `fPromptForPassword` = 1 under `HKLM\SOFTWARE\Policies\Microsoft\Windows NT\Terminal Services` |
| [WN11-CC-000305](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000305) | Disable indexing of encrypted files                  | Remediated ✅ | `AllowIndexingEncryptedStoresOrItems` = 0 under `HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Search` |
| [WN11-CC-000327](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000327) | Enable PowerShell transcription                      | Remediated ✅ | PowerShell transcription enabled, output directory set    |
| [WN11-CC-000360](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000360) | Disable WinRM Digest authentication                  | Remediated ✅ | `AllowDigest` = 0 under `HKLM\SOFTWARE\Policies\Microsoft\Windows\WinRM\Client` |
| [WN11-SO-000025](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-SO-000025) | Rename built-in Guest account                         | Remediated ✅ | Built-in Guest account renamed                              |
| [WN11-CC-000385](https://github.com/dmarrero98/STIG-Programmatic-Hardening/tree/main/STIGS/WN11-CC-000385) | Disable Windows Ink Workspace above the lock         | Remediated ✅ | `AllowWindowsInkWorkspace` = 0 under `HKLM\SOFTWARE\Policies\Microsoft\WindowsInkWorkspace` |

---

> ⚡ All remediations are applied **programmatically** via PowerShell scripts to enforce security controls and ensure STIG compliance.




