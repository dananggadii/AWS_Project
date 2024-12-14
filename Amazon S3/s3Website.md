# Static Website Hosting with Custom Domain and TLS

### 1. Create S3 Bucket

1. Click Create bucket

2. Type Bucket name

3. Choose AWS region

> Note : accept the default value

4. Click create bucket

### 2. Uploud File

1. Click Bucket

2. On objects tab > Click Uploud

3. Choose website file

4. Click uploud

### 3. Config Bucket

1. On permissions tab

2. find block public access > click edit

3. Uncheck block all public access > click save

4. Find bucket policy > click edit

5. Click policy generator / type here :

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": "[Bucket ARN]"
    }
  ]
}
```

6. Click save changes

7. On properties tab > scroll down

8. Find static website hosting > click edit

9. Select enable for `static website hosting`

10. Choose Host a static website for `Hosting type`

11. Type specify home for `Index document` example `index.html`

12. Click save changes

13. And now click bucket website endpoint to show website

### 4. Set Custom Domain and TLS

1. Seacrh `Route 53` AWS Service.

2. Click `Hosted zones` on left panel.

3. Back to `S3` > Click `bucket hosting name` > select `properties tab`.

4. Copy `bucket website endpoint`.

5.
