**Project Summary**

This personal project is designed to develop and apply ETL pipeline concepts by extracting personal training data from Strava, GymNotes and Garmin,
transforming and visualizing the data, identifying performance patterns and trends, and generating training recommendations tailored to specific
goals and race objectives.

**Overall Architecture**:
- _Data Extraction & Processing_: Training data is extracted from Strava, GymNotes and Garmin and processed through a Python-based ETL pipeline.
- _Data Storage_: Processed data is stored in a Supabase PostgreSQL database.
- _Analysis & Visualization_: Python is used to analyze training metrics, identify performance trends, and generate visualizations.
- _Recommendations Engine_: Insights derived from the data are leveraged to provide personalized recommendations for training goals and race preparation.

**Script Descriptors**
- _Strava_Database_Upload_: Handles the full ETL pipeline for syncing Strava activity data to a Supabase PostgreSQL database. Authenticates with the Strava API via OAuth2, retrieves all historical activities and per-kilometre split data (with built-in rate-limit handling), converts units and timestamps, and upserts the results into three tables: athletes, activities, and splits. Requires a .env file with Strava and Supabase credentials.
- _Strava_RunAnalytics_: Queries the Supabase database and produces interactive visualisations of general running performance over time. Covers distance progression, yearly volume totals, aerobic efficiency (heart rate vs. pace), heart-rate zone distribution, suffer score trends, and a country-level running map. Plots include interactive hover annotations for individual activities.
- _Strava_MarathonAnalytics_: Focuses specifically on marathon training blocks (Eindhoven 2024, Copenhagen 2026, Amsterdam 2026). Visualises peak daily run distance side-by-side across all three blocks with proportional panel widths, compares weekly long-run trajectories and monthly volumes on a shared training timeline, and tracks taper and cool-down windows. Also includes a volume forecast for the current block using Holt's damped exponential smoothing.
- _Strava_MLEngine_: A growing machine learning notebook for data-driven, personalised training intelligence. Currently implements the Acute:Chronic Workload Ratio (ACWR) — comparing the last 7 days of running load against a rolling 28-day baseline, with standard risk bands and personalised percentile thresholds derived from the athlete's full training history. Planned extensions include LSTM sequence modelling for performance forecasting, unsupervised anomaly detection for physiological outliers, and reinforcement learning for adaptive plan adjustment.
