---
title : "Building Database"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.2 </b> "
---

In the lab, once we have the input data with the path on S3 as at the beginning of the lab, we will configure **AWS Glue** and **Crawler** so that it runs on a schedule **once a day.**. **Crawler** will scan the path containing the input **Parquet** file, save it on S3 and then create a database with accompanying tables. When a new version of **report** is available, the data table is automatically updated.

**Amazon Athena** helps us access and view parquet file contents through **SQL code**. **Amazon Athena** is a **serverless** solution that supports executing **SQL queries** on large amounts of data. **Athena** is charged only for scanned data, unlike a traditional database solution.

The detailed configuration steps for **Amazon Athena** to access data files through **AWS Glue** are as follows:


1. Go to [AWS Management Console](https://aws.amazon.com/en/console/)

- Find **AWS Glue**
- Select **AWS Glue**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0001-builddatabase.png?featherlight=false&width=90pc)

1. In the **AWS Glue** interface

- Select **Crawlers**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0002-builddatabase.png?featherlight=false&width=90pc)

3. In the **Crawler** interface

- Select **Add crawler**


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0003-builddatabase.png?featherlight=false&width=90pc)

4. We perform the **crawler** configuration steps

- In the **Crawler info** section, enter **Crawler name** as ```Cost_MasterCrawler```


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0004-builddatabase.png?featherlight=false&width=90pc)

5. **Crawler source type** configuration step

- Select **Data stores**
- Select **Crawl new folders only**
- Select **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0005-builddatabase.png?featherlight=false&width=90pc)

6. In the **Data store** interface

- **Choose a data store**, enter **S3**
- **Crawl data in**, select **Specified path in my account**
- **Include path**, Select **path of S3**


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0006-builddatabase.png?featherlight=false&width=90pc)

7. Specify the file formats that will not be crawled in the **exclude patterns** section. Including file types **.json**, **.yml**, **.sql**, **.csv**, **.gz**, **.zip**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0007-builddatabase.png?featherlight=false&width=90pc)


8. Select **No** and select **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0008-builddatabase.png?featherlight=false&width=90pc)

9. In the **IAM Role** section

- Select **Create an IAM role**
- Enter ```cost_MasterCrawler```
- Select **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/0009-builddatabase.png?featherlight=false&width=90pc)

10. In the **Schedule** section

- **Frequency**, select **Run on demand**
- Select **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00010-builddatabase.png?featherlight=false&width=90pc)


11. **Output** configuration step

- Select **Add database**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00011-builddatabase.png?featherlight=false&width=90pc)

12. In the **Add database** interface

- **Database name**, enter ```costmaster```
- Select **Create**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00012-builddatabase.png?featherlight=false&width=90pc)

13. Select **Next**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00013-builddatabase.png?featherlight=false&width=90pc)

14. Double check and select **Finish**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00014-builddatabase.png?featherlight=false&width=90pc)

15. Finish creating **Crawler**

- Select **Cost_MasterCrawler** just created
- Select **Run crawler**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00015-builddatabase.png?featherlight=false&width=90pc)

16. Crawler runs for about 5 minutes, results appear as shown with **1 Table** added

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00016-builddatabase.png?featherlight=false&width=90pc)

17. In the **AWS Glue** interface

- Select **Databases**
- Select **costmaster** database
- Select **View tables**

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00017-builddatabase.png?featherlight=false&width=90pc)

18. Select **monthly_report** table


![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00018-builddatabase.png?featherlight=false&width=90pc)

19. It is easy to see that the **record count value is different from 0**, which proves that **parquet data on S3** has been successfully converted to tabular form by AWS Glue **Crawler tool**.

![Prerequisite](/images/2-Prerequiste/2.2-Builddatabase/00019-builddatabase.png?featherlight=false&width=90pc)