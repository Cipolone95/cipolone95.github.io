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

<!-- Condition -->
{{< note title="S3 Buckets">}}

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

