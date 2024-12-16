# Static Website Hosting with Custom Domain and TLS

### 1. Create S3 Bucket

1. Search S3 > Choose buckets on left panel

2. Click Create bucket

![alt text](image-1.png)

3. Type Bucket name

4. Choose AWS region

![alt text](image-2.png)

> Note : accept the default value

5. Click create bucket

### 2. Uploud File

1. Click Bucket

2. On objects tab > Click Uploud

![alt text](image-3.png)

3. Choose website file

4. Click uploud

![alt text](image-4.png)

### 3. Config Bucket

1. On permissions tab

2. find block public access > click edit

![alt text](image-5.png)

3. Uncheck block all public access > click save

![alt text](image-6.png)

4. Find bucket policy > click edit

![alt text](image-7.png)

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

![alt text](image-8.png)

7. On properties tab > scroll down

8. Find static website hosting > click edit

![alt text](image-9.png)

9. Select enable for `static website hosting`

![alt text](image-10.png)

10. Choose Host a static website for `Hosting type`

11. Type specify home for `Index document` example `index.html`

![alt text](image-12.png)

12. Click save changes

13. And now click bucket website endpoint to show website

### 4. Set Custom Domain

1. Seacrh `Route 53` AWS Service.

2. Click `Hosted zones` on left panel.

![alt text](image-13.png)

3. Back to `S3` > Click `bucket hosting name` > select `properties tab`.

4. Copy `bucket website endpoint`.

![alt text](image-14.png)

5. Click domain on hosted zones

6. Click create record

![alt text](image-15.png)

7. On record type select CNAME

8. Type record name/subdomain

9. On value, paste `bucket endpoint website` > remove `http://`

10. Then create records

![alt text](image-16.png)

11. Test subdomain on web browser to show the website

### 5. Set TLS/SSL Certificate

1. Seacrh cloudfront

2. Create distribution

![alt text](image-17.png)

3. On origin domain > choose s3 domain bucket

4. Click use website endpoint on alert

![alt text](image-18.png)

5. Scroll down, on default cache behavior > viewer protocol policy, select `redirect HTTP to HTTPS`

![alt text](image-19.png)

6. Scroll down, on settings > price class, select `your contry/region (use all edge locations[best performance])`

![alt text](image-20.png)

7. On Alternate domain name(CNAME) > click add item > type subdomain website

![alt text](image-21.png)

8. On custom SSL certificate > click choose or request certificate

![alt text](image-22.png)

9. If you choose request certificate > direct to AWS certificate manager page

10. On request a public certificate for certificate type, click next

![alt text](image-23.png)

11. On domain names, type `subdomain bucket`

12. Accept the default config > Click request

![alt text](image-24.png)

13. Click `certificate name` > scroll down and find domains

14. Click create records in route 53

![alt text](image-25.png)

15. Click create records

![alt text](image.png)

16. Waiting certificate status success

![alt text](image-26.png)

17. Back to cloudfront config > select SSL certificate > scroll down, and click distribution

![alt text](image-27.png)

18. Copy `domain name` for static website

![alt text](image-28.png)

19. Back to route 53 > select static website domain

![alt text](image-29.png)

20. Select subdomain > click edit record

![alt text](image-30.png)

21. Paste domain name to value record > and click save

![alt text](image-31.png)

22. And now try to type subdomain on web browser : `https://subdomain`
