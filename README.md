# Spotify End to End Data Engineering Project using Snowflake
 Project Overview
This project demonstrates a complete ETL (Extract, Transform, Load) pipeline built using AWS services, Snowflake, and the Spotify API. The pipeline is designed to extract the Top 50 Global songs from Spotify using the spotipy library, transform the raw JSON data, and load it into Snowflake using Snowpipe for scalable, near real-time analytics.

By leveraging AWS Lambda, S3, and CloudWatch, we ensure a fully automated and serverless solution for fetching, processing, and storing music data. The data pipeline enables organizations to analyze global music trends and derive actionable insights with ease.

 **Architecture**
![spotify-etl-using-snowflake-architecture-diagram](https://github.com/user-attachments/assets/5faf2a5f-9b70-43fb-a763-26e9669c96cd)

**Data Source**
We use the Spotify Web API to fetch data from the Top 50 Global Playlist, which includes:

Track Name
Artist Name
Album Name

Popularity
Track Duration

External Links

Data is retrieved in JSON format using the Python spotipy client, then transformed into structured tabular data for storage and querying in Snowflake.

**🔧 Technologies & Services Used**
🎵 Spotify API (Spotipy) – Fetches Top 50 Global playlist data in JSON format.

🐍 Python Libraries:
spotipy – API wrapper for Spotify
pandas – Data manipulation

**☁️ AWS Services:**

S3 – Stores raw and transformed data
Lambda – Serverless compute for ETL automation
CloudWatch – Logs and scheduled Lambda triggers

**❄️ Snowflake:**

Data Warehouse – Stores structured music data
Snowpipe – Automatically ingests transformed data from S3 for querying

🛠️ Installed Python Packages
pip install spotipy
pip install pandas
🔁 ETL Workflow
Scheduler Trigger: AWS Lambda is triggered weekly via CloudWatch.

Extraction:

Lambda runs spotify_api_data_extract.py.
Fetches Top 50 Global Playlist via spotipy.
Stores raw JSON data in an S3 bucket.

Transformation:

S3 event triggers another Lambda.
Runs spotify_transformation_load_function.py.
Cleans and structures the data (songs, artists, albums).
Saves the transformed data to a different S3 bucket.

Loading:

Snowpipe is auto-triggered via S3 event notification.
Transformed data is ingested into Snowflake tables.

Analysis:

Data is now queryable via Snowflake for dashboards, reports, or analytics tools.

📈 Use Case
This solution allows music platforms, analysts, and enthusiasts to:
Track global music trends
Perform artist and genre analysis
Build dashboards with live or weekly refreshed Spotify data
Generate reports for marketing, A&R, or streaming insights

Add batch historical ingestion for longer-term trend analysis
Add retry logic and error alerts in Lambda functions
