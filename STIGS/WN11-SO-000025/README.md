``` powershell
<#
.SYNOPSIS
    Renames the built-in Guest account to reduce the likelihood of unauthorized access via default accounts.

.NOTES
    Author          : Dillan Marrero
    LinkedIn        : linkedin.com/in/dmarrero98/
    GitHub          : github.com/dmarrero98
    Date Created    : 2025-11-04
    Last Modified   : 2025-11-04
    Version         : 1.0
    CVEs            : N/A
    Plugin IDs      : N/A
    STIG-ID         : WN11-SO-000025
.TESTED ON
    Date(s) Tested  : 2025-11-04
    Tested By       : Dillan Marrero
    Systems Tested  : 
    PowerShell Ver. : 5.1.26100.6899

.USAGE
    Put any usage instructions here.
    Example syntax:
    PS C:\> .\WN11-SO-000025.ps1 
#>


# Define a new name for the built-in Guest account
$newGuestName = "Guest_Obscured"

# Get the built-in Guest account object
$guest = Get-LocalUser -Name "Guest" -ErrorAction SilentlyContinue

# Check if the Guest account exists
If ($guest) {
    Write-Output "Found built-in Guest account. Renaming to '$newGuestName'."
    try {
        # Rename the Guest account
        Rename-LocalUser -Name "Guest" -NewName $newGuestName
        Write-Output "Rename successful."
    }
    catch {
        Write-Output "ERROR: Failed to rename Guest account. $_"
    }
}
else {
    Write-Output "No built-in Guest account found with name 'Guest'. It may already be renamed or disabled."
}

```
