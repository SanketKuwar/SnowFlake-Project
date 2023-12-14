## Step 1: Automated Data Ingestion with Scheduled Tasks and Snowpipe

**Objective:** Eliminate manual data loading and ensure timely analysis.

**Solution:**
- 🔄 Created a task named `GET_NEW_FILES` in Snowflake that automatically runs every 5 minutes using the `CREATE OR REPLACE TASK` statement.
- ☁️ Leveraged Snowpipe for automated data ingestion, continuously monitoring the stage for new files.
- 🚀 Upon arrival, Snowpipe seamlessly transfers files into the `ED_PIPELINE_LOGS` table, ensuring real-time data availability.

**Benefits:**
- 📉 Reduced operational overhead: No manual data loading, freeing up time for analysis and other tasks.
- 🚀 Scalability and performance: Snowpipe handles data ingestion efficiently, even with large datasets.
- 🔄 Real-time data availability: Always-fresh data ensures analysis reflects the latest player trends.

**Technical Skills Demonstrated:**
- 🗓️ Task scheduling in Snowflake.
- ☁️ Snowpipe integration for automated data ingestion.

## Step 2: Data Transformation and Enrichment for Deeper Insights

**Objective:** Transform and enrich raw data to unlock valuable player insights.

**Solution:**
- 🔍 Implemented a two-step approach for data transformation and enrichment:
  - 🔄 Normalization: Created a view named `PL_LOGS` that cleans and standardizes data within the `ED_PIPELINE_LOGS` table without physically moving it.
  - 🚀 Enrichment: Developed a task named `LOAD_LOGS_ENHANCED` that joins data, applies calculations, renames columns, and stores the final processed data in the `AGS_GAME_AUDIENCE.ENHANCED.LOGS_ENHANCED` table.

**Benefits:**
- 🌐 Improved data quality: Standardized data ensures consistent and reliable analysis.
- 📊 Richer insights: Joins and calculations unlock deeper player understanding based on location, time zone, and session duration.
- 📂 Organized structure: Clear column names facilitate intuitive analysis and reporting.

**Technical Skills Demonstrated:**
- 🔍 View creation and data normalization techniques.
- 🔄 Data joins and calculations using SQL functions.
- ⏲️ Window functions for session length analysis.

## Step 3: Streamlined Data Flow with CDC and MERGE for Real-time Consistency

**Objective:** Maintain data consistency and reflect changes in real-time.

**Solution:**
- 🔄 Transitioned from the `LOAD_LOGS_ENHANCED` task to a more efficient approach using Change Data Capture (CDC) and `MERGE` statements.
- 🔍 Created a CDC stream on the `ED_PIPELINE_LOGS` table, capturing updates or changes in the underlying data.
- 🚀 Developed a new task named `AGS_GAME_AUDIENCE.RAW.CDC_LOAD_LOGS_ENHANCED` that utilizes a `MERGE` statement for updating existing data and inserting new data.

**Benefits:**
- 🔄 Real-time data consistency: Reflects changes in player activity as they occur, providing up-to-date insights.
- 🔄 Automatic updates and insertions: No manual intervention needed, ensuring data accuracy and completeness.
- 🚀 Improved performance: Optimized processing avoids unnecessary workload.

**Technical Skills Demonstrated:**
- 🔍 CDC stream creation and utilization.
- 🔄 `MERGE` statement implementation for updates and insertions.
- 🚀 Task optimization techniques.

## Step 4: Data Visualization and Player Insights

**Objective:** Visually communicate findings and uncover player behavior patterns.

**Solution:**
- 📊 Leveraged the power of Snowflake dashboards to create interactive visualizations of enriched data.
- 🌍 Explored player location 
