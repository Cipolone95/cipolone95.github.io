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
```

Azure Subdomain Enumeration
```
#github https://github.com/yuyudhn/AzSubEnum
python3 azsubenum.py -b domain -p permutations.txt -v
```

Username Enumeration
```
Github: https://github.com/0xZDH/Omnispray
python3 omnispray.py -m o365_enum_office -d example.com -uf ~/Documents/userList.txt
```



{{< /note >}}


