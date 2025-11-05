```powershell
<#
.SYNOPSIS
    Disables Windows Ink Workspace above the lock screen to prevent access to ink features without user authentication.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000385

.TESTED ON
    Date(s) Tested  : 2025-11-05
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Example syntax:
    PS C:\> .\WN11-CC-000385.ps1 
#>

# WN11-CC-000385: Disable Windows Ink Workspace above the lock

# Registry path for Windows Ink Workspace policy
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\WindowsInkWorkspace"

# Ensure the registry key exists
if (-not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force | Out-Null
    Write-Output "Created registry key: $regPath"
}

# Set the policy value to disable Windows Ink Workspace above the lock
# 0 = Disabled
Set-ItemProperty -Path $regPath -Name "AllowWindowsInkWorkspace" -Value 0 -Type DWord

Write-Output "Configured AllowWindowsInkWorkspace = 0 under $regPath (Windows Ink Workspace above lock disabled)."
```
