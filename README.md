# Music Data ETL Pipeline Using Spotify API and AWS

### Overview:
This pipeline automates the extraction, transformation, and storage of music data from Spotify, leveraging AWS services like Lambda, S3, Glue, Athena, and CloudWatch. It provides the music industry with valuable insights through automated, scalable data processing.

### Data Flow Overview
The pipeline begins with Spotify's API, continues through AWS Lambda functions for data extraction and transformation, and stores the final data in Amazon S3. It then uses AWS Glue for cataloging and Amazon Athena for querying the processed data.

![Architecture](https://github.com/vandithavb/Spotify-end-to-end-ETL-data-Pipeline--AWS/blob/main/Spotify%20end%20to%20end%20DE.png)

### Pipeline Architecture
#### Extract: Data is extracted from the Spotify API via AWS Lambda, triggered daily by CloudWatch.
#### Transform: Data is cleansed and formatted by another Lambda function after being uploaded to S3.
#### Load: The transformed data is stored in S3, and Glue Crawlers catalog the data schema for easy querying via Athena.

### Components Based on the Diagram
#### Spotify API: The starting point where the raw data about tracks, artists, albums, etc., is fetched using a Python script.

#### Amazon CloudWatch (Daily Trigger):
CloudWatch schedules and triggers the AWS Lambda function responsible for data extraction. The trigger runs on a daily basis, ensuring fresh data is collected regularly.

#### AWS Lambda (Data Extraction):
A Lambda function is used to extract raw data from the Spotify API. This function is executed based on the CloudWatch schedule.

#### Amazon S3 (Raw Data):
The raw data extracted from the Spotify API is stored in an Amazon S3 bucket. This bucket provides secure and scalable storage for unprocessed data.

#### Trigger (Object Put):
An S3 event trigger initiates the next Lambda function as soon as new raw data is uploaded to the bucket. This trigger ensures that data processing starts automatically.

#### AWS Lambda (Data Transformation):
Another Lambda function is used for transforming the raw data. It cleanses, formats, and aggregates the data before sending it to the next stage.

#### Amazon S3 (Transformed Data):
The transformed data is stored in a separate S3 bucket. This ensures the raw and processed data are managed independently for easy access and scalability.

#### AWS Glue Crawler (Infer Schema):
AWS Glue Crawler automatically identifies and catalogs the schema of the transformed data stored in S3. It creates a centralized Data Catalog, making the data easy to query.

#### AWS Glue Data Catalog:
The Data Catalog stores metadata of the transformed data, allowing efficient data discovery and simplifying SQL-based queries.

#### Amazon Athena (Analytics):
Athena enables querying the data stored in S3 using standard SQL queries. It provides a flexible and powerful way to analyze the processed music data and generate insights.

### Key Benefits
Automated Workflow: Daily triggers via CloudWatch, Lambda functions, and S3 event triggers ensure that the entire ETL process is fully automated with minimal manual intervention.

Scalable Data Storage: Amazon S3 offers scalable storage for both raw and transformed data, ensuring that large volumes of data can be stored securely.

Efficient Data Processing: AWS Lambda functions handle both data extraction and transformation, ensuring that the pipeline remains serverless and cost-efficient.

Comprehensive Data Cataloging: AWS Glue provides an automated way to manage metadata, simplifying data access for analysis.

Real-Time Insights: Amazon Athena allows real-time querying of the transformed data, enabling music industry professionals to gain actionable insights quickly.

-- This project was part of the Python for Data Engineering course by Data Vidya, showcasing a practical application of AWS services to build an efficient, scalable ETL pipeline for real-world data analysis.
