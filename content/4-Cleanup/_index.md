---
title : "Clean up resources"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

#### Clean up resources

#### Remove AWS Glue Crawler

1. Access the **AWS Glue** interface
2. Select **Crawlers**
3. Choose the crawler related to the lab
4. Select **Actions** and select **Delete crawler**
5. Select **Delete**

![Clean up](/images/4-Cleanup/0001-cleanup.png?featherlight=false&width=90pc)

#### Delete database in AWS Glue

1. Access the **AWS Glue** interface
2. Select **Databases**
3. Select the database related to the lab
4. Select **Delete**

![Clean up](/images/4-Cleanup/0002-cleanup.png?featherlight=false&width=90pc)

#### Delete S3 bucket

1. Access **S3** interface
2. Select **Bucket**
3. Select the bucket related to the lab
4. Select **Empty**

![Clean up](/images/4-Cleanup/0003-cleanup.png?featherlight=false&width=90pc)

5. Enter **permanently delete** and select **Empty**

![Clean up](/images/4-Cleanup/0004-cleanup.png?featherlight=false&width=90pc)

6. Select the bucket related to the lab and select **Delete**

![Clean up](/images/4-Cleanup/0005-cleanup.png?featherlight=false&width=90pc)

7. Verify the bucket name and select **Delete bucket**

![Clean up](/images/4-Cleanup/0006-cleanup.png?featherlight=false&width=90pc)