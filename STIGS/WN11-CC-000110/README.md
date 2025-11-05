```powershell
<#
.SYNOPSIS
    Disables printing over HTTP to enforce secure print driver downloads and mitigate exposure to network threats.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-04
    Last Modified   : 2025-11-04
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-CC-000110

.TESTED ON
    Date(s) Tested  : 2025-11-04
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-CC-000110.ps1 
#>


$RegPath = "HKLM:\SOFTWARE\Policies\Microsoft\Windows NT\Printers"

If (!(Test-Path $RegPath)) {
    Write-Output 'The registry key (Printers) does not exist, creating now...'
    New-Item -Path "HKLM:\SOFTWARE\Policies\Microsoft\Windows NT" -Name "Printers" -Force | Out-Null
    New-ItemProperty -Path $RegPath -Name "DisableHTTPPrinting" -PropertyType DWord -Value 1 -Force | Out-Null
} else {
    # If the path already exists, just ensure the value is set
    New-ItemProperty -Path $RegPath -Name "DisableHTTPPrinting" -PropertyType DWord -Value 1 -Force | Out-Null
}

# Verify the change
$CheckValue = Get-ItemProperty -Path $RegPath | Select-Object DisableHTTPPrinting
Write-Output "Verification - Current DisableHTTPPrinting value:"
Write-Output $CheckValue.DisableHTTPPrinting
```
