---
title : "Building a database"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

In the lab, once we have the input data with the above path as at the beginning of the lab, we will configure **AWS Glue** and **Crawler** so that it runs on a schedule **once a day* *. **Crawler** will scan the path containing the input **Parquet** file, save it on S3 and then create a database with accompanying tables. When a new version of **report** is available, the data sheet is automatically updated.

**Amazon Athena** helps us access and view parquet file contents through **SQL code**. **Amazon Athena** is a **serverless** solution that supports executing **SQL queries** on large amounts of data. **Athena** is charged only for scanned data, unlike a traditional database solution.

The detailed configuration steps for **Amazon Athena** to access data files through **AWS Glue** are as follows:


1. Go to [AWS Management Console](https://aws.amazon.com/en/console/)

   - Find **AWS Glue**
   - Select **AWS Glue**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0001-builddatabase.png?featherlight=false&width=90pc)

2. In the **AWS Glue** interface

   - Select **Crawlers**
   - Select **Create crawler**

![Prerequisite](/images/2/0001.png?featherlight=false&width=90pc)

3. Configure **Crawler**, enter **Name** as **```Cost_MasterCrawler```**. Then select **Next**

![Prerequisite](/images/2/0002.png?featherlight=false&width=90pc)

4. Select **Add a data source**

![Prerequisite](/images/2/0003.png?featherlight=false&width=90pc)

5. Configure data source

![Prerequisite](/images/2/0004.png?featherlight=false&width=90pc)

6. Select **S3 path**

![Prerequisite](/images/2/0005.png?featherlight=false&width=90pc)

7. Complete the data source configuration.

![Prerequisite](/images/2/0006.png?featherlight=false&width=90pc)

8. After configuring the data source, select **Next**

![Prerequisite](/images/2/0007.png?featherlight=false&width=90pc)

9. For security, select **Create new IAM role**

![Prerequisite](/images/2/0008.png?featherlight=false&width=90pc)

10. Enter the role name and select **Create**

![Prerequisite](/images/2/0009.png?featherlight=false&width=90pc)

11. After creating the role, select **Next**

![Prerequisite](/images/2/00010.png?featherlight=false&width=90pc)

12. Implement more database

- Select **Add database**

![Prerequisite](/images/2/00011.png?featherlight=false&width=90pc)

13. Enter the database name as **```costmaster```**. Select **Create database**

![Prerequisite](/images/2/00012.png?featherlight=false&width=90pc)

14. Complete database creation.

![Prerequisite](/images/2/00013.png?featherlight=false&width=90pc)

15. Add database successfully and select **Next**

![Prerequisite](/images/2/00014.png?featherlight=false&width=90pc)

14. Check and select **Create crawler**

![Prerequisite](/images/2/00015.png?featherlight=false&width=90pc)

15. Complete crawler creation.

![Prerequisite](/images/2/00016.png?featherlight=false&width=90pc)

16. Select **Run crawler**

![Prerequisite](/images/2/00017.png?featherlight=false&width=90pc)

17. It takes about 1 minute to initialize the run crawler.

![Prerequisite](/images/2/00018.png?featherlight=false&width=90pc)

18. Initialize **run crawler**

![Prerequisite](/images/2/00019.png?featherlight=false&width=90pc)

19. **Run crawler** successfully.

![Prerequisite](/images/2/00020.png?featherlight=false&width=90pc)

20. Check out the AWS Glue **Table**. We see a data table **monthly_report**

![Prerequisite](/images/2/00021.png?featherlight=false&width=90pc)

21. View detailed data sheet information.

![Prerequisite](/images/2/00022.png?featherlight=false&width=90pc)