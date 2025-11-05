``` powershell
<#
.SYNOPSIS
    This script alters a setting which prevents the computer from downloading print driver packages over HTTP.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000100

.TESTED ON
    Date(s) Tested  : 2025-11-05
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-CC-000100.ps1 
#>


#WN11-CC-000100 
# Registry path for preventing HTTP print driver downloads
$regPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows NT\Printers"

# Ensure the registry key exists
if (-not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force | Out-Null
    Write-Output "Created registry path: $regPath"
}

# Set the key value to disable download of print drivers over HTTP
Set-ItemProperty -Path $regPath -Name "DisableWebPnPDownload" -Value 1 -Type DWord

Write-Output "Configured DisableWebPnPDownload = 1 under $regPath (HTTP print driver download disabled)."
```
