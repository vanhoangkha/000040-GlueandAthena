---
title : "Preparing the database"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

In this lab, we use available data about **AWS Cost & Usage Report.**

The first step, to build a database for query purposes from **Amazon Athena** through **AWS Glue**, we need to have data based on **AWS Cost & Usage Report**. However, getting this report will **take at least 24h**, so we have prepared the report files.

{{% notice note %}}
You can download the data at [Cost and Usage Analysis](https://github.com/First-Cloud-Journey/000040-CUR). ![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00012-preparedatabase.png?featherlight=false&width=90pc)

{{% /notice %}}

1. Go to [AWS Management Console](https://aws.amazon.com/en/console/)

- Find **S3**
- Select **S3**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0001-preparedatabase.png?featherlight=false&width=90pc)

2. In the **S3** interface

- Select **Buckets**
- Select **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0002-preparedatabase.png?featherlight=false&width=90pc)

1. In the **Create bucket** interface

- **Bucket name**, enter ```cost-and-usage-analysis```

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0003-preparedatabase.png?featherlight=false&width=90pc)

4. Select **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0004-preparedatabase.png?featherlight=false&width=90pc)

5. Finish creating **S3 bucket**

- Select **cost-and-usage-analysis** bucket

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0005-preparedatabase.png?featherlight=false&width=90pc)

6. In **cost-and-usage-analysis** bucket

- Create a folder to store data by selecting **Create folder**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0006-preparedatabase.png?featherlight=false&width=90pc)

7. In the **Create folder** interface

- **Folder name**, enter ```Monthly-Report```
- Select **Create folder**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0007-preparedatabase.png?featherlight=false&width=90pc)

8. We perform **Upload** of data files

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0008-preparedatabase.png?featherlight=false&width=90pc)

9. Select downloaded data files

- Select **Add files**
- Select data files

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/0009-preparedatabase.png?featherlight=false&width=90pc)

10. Select **Upload**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00010-preparedatabase.png?featherlight=false&width=90pc)

11. When uploading status changes to **Succeeded**

![Prerequisite](/images/2-Prerequiste/2.1-Preparedatabase/00011-preparedatabase.png?featherlight=false&width=90pc)