## Vehicle Analytics Cloud Assessment – Justification

Use this file to briefly explain your design decisions. Bullet points are fine.

### 1. High-level architecture

- Summary of your overall cloud design:
- The weather station collection system will comprise of an offboard weather station which measures temperature, humidity etc.
- The weather station may often be in places with weak internet connection so having a live transmission of measurements will need heavy internet usage. Hence the measurements will be sent once every few seconds (5-10 seconds) for less internet requirements.
- This measurements will be collected by AWS IoT core and a Lambda function formats it and saves it in a S3 bucket.
- Athena will be used to query both the vehicle analytics and the weather measurements based on the timestamps.

### 2. Weather station integration

- How the weather station connects to the cloud:
- 
- How weather data flows into the Vehicle Analytics platform:

### 3. Infrastructure as Code (IaC)

- Which IaC tool(s) you would use (e.g. Terraform, AWS CDK) and why:
- How IaC fits into deployment / environments:

### 4. Security, reliability, observability

- Key security choices (network boundaries, authn/z, secrets, etc.):
- Reliability and failure modes:
- Monitoring/alerting and operational concerns:

### 5. Cost and scalability considerations

- Expected cost drivers and how you would keep costs under control:
- How the design scales to more stations/events:
