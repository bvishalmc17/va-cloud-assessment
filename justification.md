## Vehicle Analytics Cloud Assessment – Justification

Use this file to briefly explain your design decisions. Bullet points are fine.

### 1. High-level architecture

- Summary of your overall cloud design:
  - The weather station collection system will comprise of an offboard weather station which measures temperature, humidity etc.
  - The weather station may often be in places with weak internet connection so having a live transmission of measurements will need     heavy internet usage. Hence the measurements will be sent once every few seconds (5-10 seconds) for less internet requirements.
  - This measurements will be collected by AWS IoT core and a Lambda function formats it and saves it in a S3 bucket.
  - Athena will be used to query both the vehicle analytics and the weather measurements based on the timestamps.

### 2. Weather station integration

- How the weather station connects to the cloud:
  - The weather station will be connected by AWS IoT core which helps the weather station to interact with the cloud infrastructure         securely. 
- How weather data flows into the Vehicle Analytics platform:
  - A lambda function will be created when a weather reading is received and the lambda function will add a timestamp and save it in     a S3 bucket for all weather measurements. 
### 3. Infrastructure as Code (IaC)

- Which IaC tool(s) you would use (e.g. Terraform, AWS CDK) and why:
  - Terraform is used for creating the AWS IoT core configuration, lambda function and the S3 weather measurements bucket. 
- How IaC fits into deployment / environments:

### 4. Security, reliability, observability

- Key security choices (network boundaries, authn/z, secrets, etc.):
  - Encryption of data and only allowing authorised engineers in the vehicle analytics department to be able to query the data using        Athena. 
- Reliability and failure modes:
  - Main issues are poor wifi in different track locations with poor internet infrastructure. In the case of no internet connection,     the weather station must contain some capacity to store data locally before reconnecting and transferring weather data.
- Monitoring/alerting and operational concerns:
  - An alert system if the no weather data is transferred from a weather station. Another alert can be for timestamp mismatches and checking the timezones and time settings of all devices and infrastructure in use. 

### 5. Cost and scalability considerations

- Expected cost drivers and how you would keep costs under control:
  - Cost includes AWS IoT costs which is around $0.26 USD and Lambda which is around $0.10 USD and S3 storage which is a few cents along with an Athena which is charged at $5.0 USD per TB. 
- How the design scales to more stations/events:
  - Having multiple weather stations read weather related data and storing it in different buckets and having Athena match it with          timestamps from vehicle analytics.
