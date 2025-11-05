```powershell
<#
.SYNOPSIS
    Disables indexing of encrypted files to prevent potential exposure of sensitive data through search indexes.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-05
    Last Modified   : 2025-11-05
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000305

.TESTED ON
    Date(s) Tested  : 2025-11-05
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-CC-000305.ps1 
#>

$regPath = "\SOFTWARE\Policies\Microsoft\Windows\Windows Search\"
# WN11-CC-000305 
# Ensure the registry key exists
if (-not (Test-Path $regPath)) {
    New-Item -Path $regPath -Force | Out-Null
    Write-Output "Created registry key: $regPath"
}

# Set the value to disable indexing of encrypted files
Set-ItemProperty -Path $regPath -Name "AllowIndexingEncryptedStoresOrItems" -Value 0 -Type DWord
Write-Output "Configured AllowIndexingEncryptedStoresOrItems = 0 under $regPath (encrypted file indexing disabled)."

```
