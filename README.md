`# Data-Analyst-NavdeepSingh`
# AWS Portfolio Project – Academic Standing Policy (9023p)
# Project Part 1 Overview
This portfolio showcases a cloud-based data analytics solution developed using AWS to support the analysis and monitoring of academic performance under University Canada West’s Academic Standing Policy (9023p). The project was completed as part of the AWS Academy Cloud Foundations course and focuses on descriptive analysis and infrastructure monitoring. The policy defines how student performance is assessed based on GPA and CGPA to determine academic standing statuses such as Good Standing, Alert, Probation, Suspension, or Required to Withdraw. The solution utilizes Amazon S3 for data storage, AWS Glue and DataBrew for data wrangling, Amazon Athena for querying, and CloudWatch and CloudTrail for monitoring. Through this project, I gained hands-on experience in securely storing, transforming, analyzing, and monitoring academic datasets in a cloud environment while aligning with real-world institutional requirements.

# Academic Performance Analysis and Monitoring using AWS for Policy 9023p
# Objective 📌 
The primary goal of this project was to implement a cloud-based solution using AWS to support the analysis and monitoring of academic standing at University Canada West, in alignment with Academic Standing Policy 9023p. This policy outlines how student GPA and CGPA are evaluated to determine their academic status, such as Good Standing, Alert, Probation, Suspension, or Required to Withdraw. Using AWS services, I designed and deployed a data pipeline capable of storing, processing, analyzing, and monitoring student academic data. The project focuses on descriptive insights and system monitoring, while also incorporating data quality and transformation processes to ensure accuracy and consistency in reporting.

# Dataset 📁 
The dataset used in this project consisted of student academic records, which included student ID, name, enrollment year, academic program, GPA, CGPA, and the actions taken based on their performance. These datasets were stored in structured CSV and Parquet formats across three Amazon S3 buckets: registrar-raw-nav, registrar-trf-nav, and registrar-cur-nav. Each bucket was organized using logical prefixes such as year, quarter, and server, allowing efficient querying and partitioning. AWS Glue Crawlers were used to catalog the datasets into the Glue Data Catalog, enabling seamless SQL querying via Amazon Athena. This setup formed the foundation for reliable and reusable data pipelines and ensured that all academic records were accessible and query-ready in the cloud environment.

# Descriptive Analysis 📊 
Descriptive analysis played a key role in this project. Using Amazon Athena, I wrote and executed SQL queries to summarize key student performance metrics. One of the initial queries calculated the overall average CGPA across all students, which resulted in approximately 2.703. This provided a baseline understanding of academic performance. To explore how performance varied across different student cohorts, I grouped the average CGPA by enrollment year. The results showed that academic outcomes fluctuated across years, offering useful insights for faculty or administration. Another important query identified the minimum CGPA in the dataset — 1.53 — highlighting the academic risk zone for some students. These statistics helped frame how academic standing correlates with real student data, making the policy more transparent and actionable. While the core focus was descriptive, some queries also filtered students based on academic flags, such as “probation” or “suspension,” bringing in slight elements of diagnostic analysis to make the results more useful for decision-making.

# Data Wrangling (ETL) 🧹 
Data wrangling was performed using a combination of AWS Glue DataBrew and Visual ETL jobs. DataBrew recipes cleaned and transformed multiple datasets like student lists, course lists, and academic standing information. Recipe jobs were successfully executed and generated both system-level and user-level outputs. Additionally, an AWS Glue Visual ETL job (reg-ac-std-QC-nav) was designed to evaluate row-level data quality. A conditional router was applied to segregate passed and failed records, followed by schema transformations and loading into respective S3 buckets. This ETL process ensures clean, structured, and analysis-ready data.

# Monitoring and Security 🔐
Ensuring data security and system monitoring was a key part of this project. To secure student academic data, I enabled server-side encryption using AWS KMS with a custom key named reg-ac-std-key-nav. Each S3 bucket was encrypted, and versioning was turned on to protect against accidental deletions or overwrites. I also implemented cross-bucket replication rules to ensure backup and redundancy. Lifecycle policies were configured to manage storage efficiently by transitioning older files or automatically deleting temporary objects.

To monitor the data pipeline and user activity, I used Amazon CloudWatch and AWS CloudTrail. CloudWatch dashboards provided real-time visibility into resource usage and data movement, while CloudTrail tracked API calls and user actions across AWS services. This helped establish a clear audit trail and supported compliance with institutional data governance policies. The logs were stored in a centralized awslogs bucket for review and retention.

# Tools and Technologies 🛠️ 

Amazon S3 – for structured data storage and backup

AWS Glue / DataBrew – for data transformation and schema management

Amazon Athena – for serverless SQL queries on S3 data

AWS KMS – for encryption and data protection

Amazon CloudWatch & CloudTrail – for monitoring, logging, and operational insights

IAM Roles – for access control and permission boundaries

# Deliverables 📤
The key deliverables of this project include a secure and automated AWS-based data analytics pipeline, a cleaned and well-structured dataset stored in multiple formats, analytical insights generated using SQL queries in Athena, a quality-controlled ETL job, and a complete monitoring and logging system via CloudWatch and CloudTrail. All of these deliverables are backed by documentation and screenshots that reflect each step of the implementation process.

# Conclusion 🧾
This project offered hands-on experience with building a real-world data analytics and monitoring pipeline using AWS, fully aligned with academic policy requirements. Through descriptive analysis, security configuration, data wrangling, and monitoring implementation, I gained valuable skills in cloud-based data architecture. The Academic Standing Policy (9023p) was successfully mapped to AWS services, showing how institutions can make data-driven decisions while maintaining compliance, security, and operational transparency. This solution is scalable, secure, and ready for further expansion, such as predictive modeling or real-time student performance alerts.



