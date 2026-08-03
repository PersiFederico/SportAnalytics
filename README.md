**Project Summary**

This personal project is designed to develop and apply ETL pipeline concepts by extracting personal training data from Strava and Garmin, 
transforming and visualizing the data, identifying performance patterns and trends, and generating training recommendations tailored to specific 
goals and race objectives.

**Overall Architecture**:
-  _Data Extraction & Processing_: Training data is extracted from Strava and Garmin and processed through a Python-based ETL pipeline.
-  _Data Storage_: Processed data is stored in a Supabase PostgreSQL database.
-  _Analysis & Visualization_: Python is used to analyze training metrics, identify performance trends, and generate visualizations.
-  _Recommendations Engine_: Insights derived from the data are leveraged to provide personalized recommendations for training goals and race preparation.

**Script Descriptors**
- _Strava_Database_Upload_: Handles the full ETL pipeline for syncing Strava activity data to a Supabase PostgreSQL database. Authenticates with the Strava API via OAuth2, retrieves all historical activities and per-kilometre split data (with built-in rate-limit handling), converts units and timestamps, and upserts the results into three tables: athletes, activities, and splits. Requires a .env file with Strava and Supabase credentials.
- _Strava_Analytics_: Queries the Supabase database populated by the upload notebook and produces interactive visualisations of running performance over time. Covers Suffer Score trends, distance progression, and side-by-side training load comparisons across marathon training cycles. Plots include interactive hover annotations for individual activities.
