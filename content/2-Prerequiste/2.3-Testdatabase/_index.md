---
title : "Database Check"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

We create **S3 bucket** to store query results.

1. Access to **S3**

- Select **Bucket**
- Select **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0001-testdatabase.png?featherlight=false&width=90pc)

2. In the **Create bucket** interface

- **Bucket name**, enter ```cost-and-usage-query-results```

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0002-testdatabase.png?featherlight=false&width=90pc)

3. Select **Create bucket**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0003-testdatabase.png?featherlight=false&width=90pc)

4. Select **cost-and-usage-query-results** the newly created bucket

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0004-testdatabase.png?featherlight=false&width=90pc)

5. Create a folder to store query data

- Select **Create folder**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0005-testdatabase.png?featherlight=false&width=90pc)

6. Create a folder

- **Folder name**, enter ```Athena-Query-Results```
- Select **Create folder**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0006-testdatabase.png?featherlight=false&width=90pc)

7. Finish creating the folder

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0007-testdatabase.png?featherlight=false&width=90pc)

8. Access **AWS Console Management**

- Find **Athena**
- Select **Athena**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0008-testdatabase.png?featherlight=false&width=90pc)

9. To manipulate the data table, we need to configure where to save the query results on S3.

- Select **Settings**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/0009-testdatabase.png?featherlight=false&width=90pc)

10. Select **Manage**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00010-testdatabase.png?featherlight=false&width=90pc)

11. Choose the S3 path to store

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00011-testdatabase.png?featherlight=false&width=90pc)

12. Then select **Edit**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00012-testdatabase.png?featherlight=false&width=90pc)

13. Check and execute the query

- **Data Source**, select **AwsDataCatalog**
- **Database**, select **costmaster**
- **Table**, select **monthly_report**
- Execute the query with the following command: the table data is saved to **Amazon Athena's metastore**.

```
MSCK REPAIR TABLE monthly_report;
```
- Select **Run**
- Complete the query **Query successful**

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00013-testdatabase.png?featherlight=false&width=90pc)

14. Perform a system preview to test the ability to query data tables on AWS Glue

- Select **monthly_report** table
- Select **Preview Table**

```
SELECT * FROM "costmaster"."monthly_report"
LIMIT 10;
```

![Prerequisite](/images/2-Prerequiste/2.3-Testdatabase/00014-testdatabase.png?featherlight=false&width=90pc)