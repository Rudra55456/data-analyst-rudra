# Data-Analyst-rudra
In today's era of data-driven decision-making, efficiently extracting, processing, and analyzing data has become a critical skill for both organizations and individuals. This project centers on the development and implementation of a Data Analytics Platform (DAP) utilizing AWS cloud-based services, applied specifically to the ‘Parks, recreation and pets – Parks’ dataset from Vancouver's Open Data portal. The main goal is to unlock the potential of data to derive meaningful insights, such as analyzing the distribution of Facilities in Parks in Vancouver. By utilizing AWS tools like Amazon S3, AWS Glue DataBrew, and AWS Glue, this project establishes a systematic framework for data ingestion, profiling, cleansing, and transformation. The result is a robust pipeline that supports both descriptive and exploratory analysis, showcasing the value of cloud-based analytics in driving informed decisions and generating actionable insights.
# Data Selection
For my part, I chose the ‘Parks, recreation and pets – Parks’ dataset from https://opendata.vancouver.ca/explore/dataset/parks/analyze/?dataChart=eyJxdWVyaWVzIjpbeyJjaGFydHMiOlt7InR5cGUiOiJjb2x1bW4iLCJmdW5jIjoiQ09VTlQiLCJ5QXhpcyI6ImhlY3RhcmUiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjMDI3OUIxIn1dLCJ4QXhpcyI6Im5laWdoYm91cmhvb2RuYW1lIiwibWF4cG9pbnRzIjo1MCwic29ydCI6InNlcmllMS0xIiwic2VyaWVzQnJlYWtkb3duVGltZXNjYWxlIjoiIiwiY29uZmlnIjp7ImRhdGFzZXQiOiJwYXJrcyIsIm9wdGlvbnMiOnt9fX1dLCJ0aW1lc2NhbGUiOiIiLCJkaXNwbGF5TGVnZW5kIjp0cnVlLCJhbGlnbk1vbnRoIjp0cnVlfQ%3D%3D
<img width="452" alt="image" src="https://github.com/user-attachments/assets/c64d0edb-b1ca-42f8-a484-7e7ab919ab92" />
# Descriptiva Analysis
The main goal of performing Descriptive Analysis from the available data was to get information regarding the area that has the maximum number of Hectare in the city of Vancouver. Analyzing this on the opendata.vancouver website, we get the following column chart, where the maximum number of neighbourhood names are from West End (416), followed by Killarney(166). This graph should be the target of our Data Analytics process and the result after all the 4 steps should match this graph.
Column Chart showing the total number of Hectare from each neighbouring names.

<img width="414" alt="image" src="https://github.com/user-attachments/assets/5e444eff-9ce6-4f21-be1c-a6c6e827cd5c" />

# Data Storage
Based on my dataset, to store the data, three buckets were created:

1. prp-parks-raw-rudra
2. prp-parks-trf-rudra
3. prp-parks-cur-rudra
<img width="452" alt="image" src="https://github.com/user-attachments/assets/fba03d2f-cbd8-40cd-b67e-c41f7596c73d" />

# Draw io representation
<img width="452" alt="image" src="https://github.com/user-attachments/assets/f3620b53-435d-4659-b63f-78c02ee9bb1a" />

The development of this DAP utilized AWS services including Amazon S3, AWS Glue DataBrew, and AWS Glue. The implementation, as depicted in the accompanying figure, involves the use of various buckets and processes. Initially, data is ingested into a raw bucket on AWS. It is then processed using DataBrew, where tasks such as profiling and cleaning are performed. The processed data is subsequently stored in a transformed (trf) bucket. Following this, an ETL (Extract, Transform, Load) pipeline processes the transformed data to generate final outputs, which are saved in a curated bucket organized into two folders—system and user—catering to specific operational requirements.
# Step 1 Data Ingestion
The first step of designing any DAP is to fetch the structured dataset from the source. Data can be uploaded into the raw bucket either in an Excel, or CSV file, however, as per our requirements, excel is more suitable.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/f995192e-15cd-4fb5-86ea-d78d374739c2" />

# Step 2 Data Profiling
The next step after Data Ingestion is Data Profiling, that is done using the AWS ‘Glue Data Brew’ service. It is done to understand the quality of data ingested and make changes to the data as per it’s requirement.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/a619f319-9a61-4950-be5f-ffd0eed8c46c" />

Result of Data Profiling
To connect the two services, a dataset is first created to establish the integration. Following this, the profiling process is executed by setting up projects and running recipe jobs.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/1b6df0b4-bf79-4614-bbc8-8d26c6d2ffef" />

_Recipe Jobs_

# Step 3 Data Cleaning

In this process, data is prepared for analysis by undergoing a cleaning procedure. This involves several steps such as managing missing data(null values), eliminating duplicates, and addressing formatting issues. My specific dataset had ‘null’ values in the ‘EW Street’ and ‘NS Street’ columns, and a few extra columns that were unnecessary for achieving the desired results. The null values columns were removed. The clean data is then stored in the ‘data-cleaning’ folder within the ‘trf’ bucket.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/5bf7aa64-dcef-4116-8a7f-269b84aaed6f" />

# Step 4 Data Pipeline Design

The transformed data from Step 2 and Step 3. There is a pipeline used that can perform the ETL operations. The outcome of this process is called analytical data. For our case the first step is pulling out the cleaned data from the transform bucket and continue with the process of deleting particular columns that do not lead to outcomes. Following this, an aggregation operation called the count function to get the total parks. This information is kept in two folders developed on curated bucket, one for system and other for user. 

<img width="452" alt="image" src="https://github.com/user-attachments/assets/fb6c1d41-fd50-45c6-81cd-4ad25e699546" />

**_Final Result_**

<img width="452" alt="image" src="https://github.com/user-attachments/assets/bccc6509-e2c4-493f-b97c-f5ad005b0e5e" />

# Exploratory Analysis

For the Explanatory Analysis, I extracted the list of parks and it’s details. Due to the limitations in my dataset, I opted for ‘Special features’ and ‘Facilities’. This would give us information about special features and facilities. This form of analysis evaluates the quality of the dataset while also shedding light on broader implications regarding how special features and facilities are there in the parks.

**Data Analytics Platform (DAP) using draw.io for 2nd pipeline**

<img width="452" alt="image" src="https://github.com/user-attachments/assets/1c4cff2c-c1a4-48b4-932f-b8e202ac73eb" />

# Step 1 Data Ingestion

The first step of designing any DAP is to fetch the structured dataset from the source. Data can be uploaded into the raw bucket either in an Excel, or CSV file, however, as per our requirements, excel is more suitable.

**_Uploading Excel file into the raw bucket_**

<img width="452" alt="image" src="https://github.com/user-attachments/assets/b64c86a6-41ef-4517-90d6-90ee5ba94e7c" />

# Step 2 Data Profiling

The next step after Data Ingestion is Data Profiling, that is done using the AWS ‘Glue Data Brew’ service. It is done to understand the quality of data ingested and make changes to the data as per it’s requirement.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/a088661e-405f-4132-acdc-e7a2c6aa66ef" />

# Step 3 Data Cleaning

In this process, data is prepared for analysis by undergoing a cleaning procedure. This involves several steps such as managing missing data(null values), eliminating duplicates, and addressing formatting issues. My specific dataset had ‘null’ values in the ‘EW Street’ and ‘NS Street’ columns, and a few extra columns that were unnecessary for achieving the desired results. The null values columns were removed. The clean data is then stored in the ‘data-cleaning’ folder within the ‘trf’ bucket.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/d5fcf03c-1670-4147-a480-586f79136baa" />

# Step 4: Data Pipeline Design

For exploratory analysis, instead of using ‘Aggregate’ in the ETL pipeline, I used the ‘Filter’ option.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/4f262d73-87c8-4c01-90ce-6c38df1bd647" />

**_Final Result_**

<img width="366" alt="image" src="https://github.com/user-attachments/assets/b2b9b064-205c-46f1-a3cf-54e70150b1dd" />

<img width="378" alt="image" src="https://github.com/user-attachments/assets/86dd7622-0c02-4ed4-8b90-f7ddcdc6e38c" />

# Step 5: Data Enriching

Data is first transferred up from a web server to an S3 raw bucket as an additional set of data required for evaluation. This data is processed with DataBrew, selected non-relevant columns are excluded and cleaned before being stored in the transformed bucket. Further down the line, Glue services assist in formulating a pipeline using two datasets, before coming up with the last enriched report. Later on, it is possible to use SQL queries to obtain the required data from AWS Athena.
	Further, we use AWS Key Management Services to encrypt the data which is being held in S3. The details generated are checked against organizational and regulatory requirement before using AWS CloudWatch to develop a dashboard where the insights are reported.

**_S3 Endpoint_**

Data from the web server goes through an S3 endpoint before finally reaching the destination bucket.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/62cea36f-0fb2-4af2-a6d1-2745ecfb5d82" />

**_Ingestion Successful_**

After successful ingestion, we can see the ClickStream file getting stored in the S3 raw bucket automatically.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/f4b17872-6f86-42c1-a967-0a03c7358faf" />

**_Categorical Mapping_**

<img width="452" alt="image" src="https://github.com/user-attachments/assets/10ee76f8-ecc9-4e48-9a7c-2d46073bbdc5" />

**_ETL Pipeline_**

Two datasets were used as inputs to produce an enriched output. The ‘Parks’ dataset contains the original cleaned data, while the ‘Parks ClickStream’ provides categorical mapping information. As illustrated in the image below, we selected the Park ID from ‘Parks’ and after renaming the keys in the ‘Parks_ClickStream’, we joined them using the Park ID as the primary key. After merging them, we rearranged the columns and created two partitions for user accessibility. Once everything was set up in this pipeline, we simply clicked "run" to execute it.

 <img width="452" alt="image" src="https://github.com/user-attachments/assets/6993e689-6c0a-44ae-99fe-27f23ba2e596" />

**_SQL Query for Enriched Data_**

After selecting the file, I clicked on 'Action' to choose a query with SQL. Depending on the requirements, different SQL scripts can be executed. Below is an example of a query used to view data stored in the file.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/0808ab18-52f0-4b1b-8aa5-2838a8375405" />

**_Crawlers_**
Crawlers are used to put all the data stored in S3 Buckets in the form of tables. Since we had three buckets, we created 3 crawlers to extract metadata and update the catalog.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/ca9ab8bb-23f3-4482-9283-52fe428bf420" />

**_Athena_**

Another AWS Service named Athena is used to query and analyze data stored in S3 buckets. In the screenshot below, we selected the "cur-user" table, and the results are displayed.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/2fa93b0b-dd48-4afc-9fff-f84331eaa03b" />

# Step 6: Data Protection

The Key Management Service (KMS) is available to protect data within AWS. It encrypts information using symmetric or asymmetric keys. We can generate a new key and utilize it to secure any transmitted or received data. Below is the key we created to protect our data.

**_Key Creation_**

<img width="452" alt="image" src="https://github.com/user-attachments/assets/88846766-362b-4255-80a1-9a01f98084c9" />

**_Bucket Versioning_**

It helps to have multiple versions of objects within the bucket provided by this feature. Every time changes are made in any object then a new copy is generated, which will enable us to save other versions in case they can be used in the future.

**_Replication Rule_**

The replication rule is one that is designed to make copies of objects as soon as it from the original bucket to the backups. This is helpful for purposes of backing up data in the event that an event occurs that degrades objects in the original bucket. For this a ‘raw-backup’ bucket was created.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/2a2eb17a-3abf-450d-a200-116386159d81" />

<img width="452" alt="image" src="https://github.com/user-attachments/assets/7ffb3062-5dae-4474-9462-48e3800984a3" />

# Step 7: Data Governance

AWS data governance is a set of policies, practices, and norms to ensure that all data stored in AWS is secure, easily to manage, and used properly. This framework allows only the given users to access the system while making it secure to meet set laws and policies set by the company. It also protects information by hiding the private data from understanding by persons who are not authorized to do so.

**_ETL Pipeline_**

The following pipeline ensures that the data samples go through all the requisite steps to avoid compliance before being stored in the correct S3 bucket.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/5a82be02-7b3b-482c-8432-10d93e48b908" />

**_AWS Glue Folders_**

Listed below are the folders designed for the pipeline and linked to their respective targets. Based on the output (Passed/Failed), data will be automatically stored in them.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/696d349e-97a2-41c6-a6ed-f494b8ef68c8" />

# Step 8: Data Observatory

**_Dashboard_**

This feature allows the monitoring of some activities through creation of the widgets. Below figure presents the widgets for the total objects in each of the buckets, bucket size, the estimated cost, alarms and logs.

<img width="452" alt="image" src="https://github.com/user-attachments/assets/0e2a2f39-74f5-4e37-86df-3f4b4956e591" />

# Conclusion
