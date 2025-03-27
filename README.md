`# Data-Analyst-NavdeepSingh`
# 📊 AWS Portfolio Project – Academic Standing Policy (9023p)

## 📘 Project Title  
**Academic Performance Analysis and Monitoring using AWS for Policy 9023p**

## 📄 Project Overview  

This portfolio showcases a cloud-based data analytics solution developed using AWS to support the analysis and monitoring of academic performance under University Canada West’s Academic Standing Policy (9023p). The project was completed as part of the AWS Academy Cloud Foundations course and focuses on descriptive analysis and infrastructure monitoring. The policy defines how student performance is assessed based on GPA and CGPA to determine academic standing statuses such as Good Standing, Alert, Probation, Suspension, or Required to Withdraw. The solution utilizes Amazon S3 for data storage, AWS Glue and DataBrew for data wrangling, Amazon Athena for querying, and CloudWatch and CloudTrail for monitoring. Through this project, I gained hands-on experience in securely storing, transforming, analyzing, and monitoring academic datasets in a cloud environment while aligning with real-world institutional requirements.

## 🎯 Objective  
![Screenshot (183)](https://github.com/user-attachments/assets/a8090f7b-9206-4d98-bc05-37e61dddda12)

The main objective of this project was to build a data-driven, cloud-native solution that could effectively analyze and monitor student performance in accordance with UCW’s Academic Standing Policy (9023p). This involved using AWS services to manage the full data lifecycle — from ingestion and wrangling to querying, analysis, and monitoring. The goal was to create meaningful insights that could support academic decisions such as issuing alerts, probation notices, or suspensions, while also ensuring the system followed best practices in security, automation, and monitoring.

## 🧾 Dataset  
![Screenshot (184)](https://github.com/user-attachments/assets/5a112d8d-de52-4206-a3c6-be9a62f5e621)

The primary dataset for this project was sourced from three essential files stored in the registrar-raw-nav Amazon S3 bucket. These files included the student list, course list, and standing list, each organized into separate folders. The student list contained comprehensive student details such as names, student IDs, dates of birth, academic programs, and CGPA. The course list provided information about all academic courses offered, including course codes, titles, and associated terms. Meanwhile, the standing list captured each student’s academic standing, indicating whether a student was in good standing, on probation, or facing suspension. These three datasets formed the backbone of the project, supporting further analysis related to the Academic Standing Policy (9023p). Their placement in S3 enabled seamless integration with AWS Glue and Athena for processing and querying.

![Screenshot (182)](https://github.com/user-attachments/assets/062754ba-a51f-45e4-a62c-6644d97305a1)
![Screenshot (181)](https://github.com/user-attachments/assets/be98a088-0839-4d44-9ee5-240e8cc53f60)


## 📊 Descriptive Analysis  

Descriptive analysis played a key role in this project. Using Amazon Athena, I wrote and executed SQL queries to summarize key student performance metrics. One of the initial queries calculated the overall average CGPA across all students, which resulted in approximately 2.703. This provided a baseline understanding of academic performance. To explore how performance varied across different student cohorts, I grouped the average CGPA by enrollment year. The results showed that academic outcomes fluctuated across years, offering useful insights for faculty or administration. Another important query identified the minimum CGPA in the dataset — 1.53 — highlighting the academic risk zone for some students. These statistics helped frame how academic standing correlates with real student data, making the policy more transparent and actionable. While the core focus was descriptive, some queries also filtered students based on academic flags, such as “probation” or “suspension,” bringing in slight elements of diagnostic analysis to make the results more useful for decision-making.
![Screenshot (96)](https://github.com/user-attachments/assets/a2c0e949-6d38-4923-a66a-a54be28f56b1)
![Screenshot (97)](https://github.com/user-attachments/assets/db23395c-7ce8-45c6-9ddb-be9d477de95a)
![Screenshot (98)](https://github.com/user-attachments/assets/794357ed-85ee-4af9-99e6-c9b652eff80b)


## 🧪 Data Wrangling (ETL) 

To make the raw data usable for analysis, an end-to-end data wrangling process was implemented using AWS Glue and AWS Glue DataBrew. The process began with uploading the raw datasets to the registrar-raw-nav S3 bucket under structured folders labeled as student-list, course-list, and standing-list. These datasets were then crawled using AWS Glue Crawlers, which scanned the contents and generated metadata tables automatically within the registrar-data-catalog-nav Glue Data Catalog. This catalog allowed us to centrally manage and structure the data schema for querying later in Amazon Athena.

Following the cataloging, AWS Glue DataBrew was employed to clean and prepare the data. DataBrew recipe jobs were created to perform transformations such as removing null values, eliminating duplicate entries, standardizing column headers, and formatting fields like cgpa (as a double) and enrollmentyear (as an integer). These transformations helped ensure consistency and readability across the datasets. After cleansing, the individual datasets were joined using shared identifiers to form a consolidated dataset that linked students with their courses and academic standings. This refined dataset was exported in Parquet format and saved into the registrar-trf-nav S3 bucket to enable efficient querying. This structured and clean dataset served as the basis for all further analysis in Athena, facilitating the project's descriptive analytics goals.

![Screenshot (67)](https://github.com/user-attachments/assets/66cc1ccc-a1c7-4dd7-b0fa-ff6bf5c26aad)
![Screenshot (93)](https://github.com/user-attachments/assets/6df57043-f82a-4c79-82cf-54db5a18b12f)
![Screenshot (94)](https://github.com/user-attachments/assets/bf354778-859a-4cad-9c61-cbad51b1fd83)
![Screenshot (95)](https://github.com/user-attachments/assets/4b005cb0-f180-43cf-b721-8531399a6927)


![Screenshot (66)](https://github.com/user-attachments/assets/86f295a1-31b2-46f8-9301-1cfa848010bc)
![Screenshot (77)](https://github.com/user-attachments/assets/4d6df9fd-eda3-48ee-ae81-99466329dc9b)

## 🔐 Monitoring and Security 

![Screenshot (188)](https://github.com/user-attachments/assets/f8f2fb0d-05ea-4cc7-9d90-d3e10f5a4700)

Ensuring data security and system monitoring was a key part of this project. To secure student academic data, I enabled server-side encryption using AWS KMS with a custom key named `reg-ac-std-key-nav`. Each S3 bucket was encrypted, and versioning was turned on to protect against accidental deletions or overwrites. I also implemented cross-bucket replication rules to ensure backup and redundancy. Lifecycle policies were configured to manage storage efficiently by transitioning older files or automatically deleting temporary objects.  

To monitor the data pipeline and user activity, I used Amazon CloudWatch and AWS CloudTrail. CloudWatch dashboards provided real-time visibility into resource usage and data movement, while CloudTrail tracked API calls and user actions across AWS services. This helped establish a clear audit trail and supported compliance with institutional data governance policies. The logs were stored in a centralized `awslogs` bucket for review and retention.

![Screenshot (140)](https://github.com/user-attachments/assets/1a0e9405-2d2d-4d05-ba16-aa6a8f3fba41)
![Screenshot (142)](https://github.com/user-attachments/assets/1e49c8d0-4ca9-430a-acca-56d9e088425c)
![Screenshot (138)](https://github.com/user-attachments/assets/77f91168-b3ac-4074-92b8-20ddb275c6f6)

![Screenshot (187)](https://github.com/user-attachments/assets/f6dec14a-113e-4830-ac24-4674bc733fd2)

![Screenshot (150)](https://github.com/user-attachments/assets/3a9f9abc-2961-4c52-a143-d853d4963b4c)
![Screenshot (151)](https://github.com/user-attachments/assets/3ccac5ec-2457-478e-aeaf-d2fd81bc8adf)

## 🛠️ Tools and Technologies  
 
 Amazon S3 – for structured data storage and backup
 
 AWS Glue / DataBrew – for data transformation and schema management
 
 Amazon Athena – for serverless SQL queries on S3 data
 
 AWS KMS – for encryption and data protection
 
 Amazon CloudWatch & CloudTrail – for monitoring, logging, and operational insights
 
 IAM Roles – for access control and permission boundaries

## 📤 Deliverables  

The key deliverables of this project include a secure and automated AWS-based data analytics pipeline, a cleaned and well-structured dataset stored in multiple formats, analytical insights generated using SQL queries in Athena, a quality-controlled ETL job, and a complete monitoring and logging system via CloudWatch and CloudTrail. All of these deliverables are backed by documentation and screenshots that reflect each step of the implementation process.

## ✅ Conclusion  

This project offered hands-on experience with building a real-world data analytics and monitoring pipeline using AWS, fully aligned with academic policy requirements. Through descriptive analysis, security configuration, data wrangling, and monitoring implementation, I gained valuable skills in cloud-based data architecture. The Academic Standing Policy (9023p) was successfully mapped to AWS services, showing how institutions can make data-driven decisions while maintaining compliance, security, and operational transparency. This solution is scalable, secure, and ready for further expansion, such as predictive modeling or real-time student performance alerts.

# Course Completion Badge

https://www.credly.com/badges/0a82d39b-fd4d-4a99-80e5-7fa13e2fdbe3/print

<img width="443" alt="image" src="https://github.com/user-attachments/assets/5624065e-fe1b-4df6-9de3-96ca5f640f2d" />

