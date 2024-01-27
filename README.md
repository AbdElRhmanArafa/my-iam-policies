In AWS Identity and Access Management (IAM), when evaluating policies, the default behavior is to deny access unless an explicit allow is present. In other words, the most specific (explicit) deny always takes precedence over allow. If there is a conflict between a deny and an allow, the deny will be applied.

Let's consider an example:

Suppose you have a user named "John" and you attach two policies to this user:

1. Policy A (Deny):
   - Effect: Deny
   - Action: s3:*
   - Resource: arn:aws:s3:::example-bucket/*

2. Policy B (Allow):
   - Effect: Allow
   - Action: s3:GetObject
   - Resource: arn:aws:s3:::example-bucket/some-file.txt

In this example, Policy A denies all actions (`s3:*`) on objects within the "example-bucket" bucket, while Policy B allows only the `s3:GetObject` action on a specific object ("some-file.txt") within the same bucket.

The result will be that John is denied access to all objects in the "example-bucket" bucket except for the specific object "some-file.txt". The deny policy takes precedence over the allow policy.