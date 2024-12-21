<head>
    <title>Redfin ETL Data Analysis</title>
</head>
<body>

<h1>Redfin ETL Data Analysis</h1>

<p>This repository contains the ETL (Extract, Transform, Load) process for analyzing Redfin data using AWS, Apache Airflow, Python, and Snowflake.</p>

<h2>Architecture</h2>

<p>The following diagram illustrates the architecture of the Redfin ETL Data Analysis:</p>

<img src="Redfin_Data_Analytics\redfin_etl_architecture.drawio.png" alt="Redfin ETL Architecture">

<h3>Components:</h3>
<ol>
    <li><strong>Data Source: Redfin</strong>: The original source of real estate data.</li>
    <li><strong>Extraction</strong>:
        <ul>
            <li><strong>Python</strong>: Scripts to extract data from Redfin via web scraping or API calls.</li>
            <li><strong>Apache Airflow</strong>: Orchestrates the ETL workflow, scheduling and managing the extraction process.</li>
        </ul>
    </li>
    <li><strong>Raw Data Storage</strong>:
        <ul>
            <li><strong>AWS S3 (Raw Data Bucket)</strong>: Stores the extracted raw data.</li>
        </ul>
    </li>
    <li><strong>Transformation</strong>:
        <ul>
            <li><strong>AWS S3 (Transform Data Bucket)</strong>: Stores the transformed data after processing.</li>
        </ul>
    </li>
    <li><strong>Loading</strong>:
        <ul>
            <li><strong>Snowpipe</strong>: Automates data loading from S3 into Snowflake.</li>
        </ul>
    </li>
    <li><strong>Data Warehouse</strong>:
        <ul>
            <li><strong>Snowflake</strong>: Stores the transformed data for querying and analysis.</li>
        </ul>
    </li>
    <li><strong>Visualization</strong>:
        <ul>
            <li><strong>BI Tools</strong>: Used for data visualization and generating insights.</li>
        </ul>
    </li>
</ol>

<h2>Prerequisites</h2>
<ul>
    <li><strong>AWS Account</strong>: To use S3 and EC2 instances.</li>
    <li><strong>Snowflake Account</strong>: For data warehousing.</li>
    <li><strong>Apache Airflow</strong>: For workflow orchestration.</li>
    <li><strong>Python</strong>: For writing extraction and transformation scripts.</li>
</ul>

<h2>Setup</h2>

<h3>1. AWS Setup</h3>
<ul>
    <li><strong>S3 Buckets</strong>: Create two S3 buckets - one for raw data and one for transformed data.</li>
    <li><strong>EC2 Instance</strong>: Launch an EC2 instance to host Apache Airflow and run your scripts.</li>
</ul>

<h3>2. Snowflake Setup</h3>
<ul>
    <li>Create a Snowflake account and set up a data warehouse.</li>
    <li>Configure Snowpipe to monitor the S3 bucket and load data into Snowflake tables.</li>
</ul>

<h3>3. Airflow Setup</h3>
<ul>
    <li>Install Apache Airflow on the EC2 instance.</li>
    <li>Create DAGs (Directed Acyclic Graphs) to define the ETL workflow.</li>
</ul>

<h3>4. Python Scripts</h3>
<ul>
    <li><strong>Extraction Script</strong>: Write a Python script to extract data from Redfin.</li>
    <li><strong>Transformation Script</strong>: Write a Python script to clean and transform the extracted data.</li>
</ul>

<h2>Workflow</h2>
<ol>
    <li><strong>Extraction</strong>:
        <ul>
            <li>Schedule the extraction script using Apache Airflow.</li>
            <li>Extract data from Redfin and store it in the raw data S3 bucket.</li>
        </ul>
    </li>
    <li><strong>Transformation</strong>:
        <ul>
            <li>Trigger the transformation script using Airflow.</li>
            <li>Clean and transform the data, then store it in the transformed data S3 bucket.</li>
        </ul>
    </li>
    <li><strong>Loading</strong>:
        <ul>
            <li>Snowpipe detects new data in the transformed data S3 bucket and loads it into Snowflake.</li>
        </ul>
    </li>
    <li><strong>Analysis and Visualization</strong>:
        <ul>
            <li>Use BI tools to visualize and analyze the data stored in Snowflake.</li>
        </ul>
    </li>
</ol>

<h2>Directory Structure</h2>
