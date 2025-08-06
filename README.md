# YouTube Comments Sentiment ETL Pipeline

A **Databricks-based ETL pipeline** that ingests YouTube comment data, applies sentiment analysis, and generates curated tables for analytics. This project follows the **Medallion Architecture** (Bronze → Silver → Gold) and highlights modern data engineering practices.

---

## Summary

Gathering insights from YouTube comments can be messy: data comes in different formats, needs cleaning, and must be ready for analysis. This project:

- **Fetches** YouTube comment data via the Tellagence sentiment analysis API.
- **Stores** raw data in the Bronze layer (Delta tables and CSV files).
- **Cleans & merges** sources in the Silver layer using Delta Live Tables.
- **Builds** business-friendly Gold tables for ad-hoc reporting.

The result? A clear, maintainable pipeline that any data team can deploy and extend.

---

## Project Files

| File Name                                                                                | Description                                                                                    |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **bronze\_table\_ingestion\_fetching\_data\_from\_sentiment\_analysis\_api.ipynb**       | Notebook to ingest API data into a Delta table (Bronze)                                        |
| **bronze\_volume\_ingestion\_fetching\_data\_from\_sentiment\_analysis\_api.ipynb**      | Notebook to ingest API data into CSV files on a mounted volume (Bronze)                        |
| **silver\_transformation\_used\_for\_dlt\_pipeline.ipynb**                               | Delta Live Tables pipeline for cleaning and unifying Bronze sources into Silver                |
| **gold\_aggregates\_for\_ad\_hoc\_analysis.ipynb**                                       | SQL notebook to create Gold tables for comments by video, author details, and sentiment trends |
| **sentiments\_api\_data.csv**                                                            | Sample raw data CSV pulled from the API                                                        |
| **DLT\_Pipeline\_Graph.png**                                                             | Diagram of the Silver layer Delta Live Tables pipeline                                         |
| **Streaming\_DLT\_Pipeline\_Code\_For\_Silver\_Layer.png**                               | Screenshot of streaming DLT code                                                               |
| **Sentiment\_Analysis\_ETL\_Job(End\_to\_End\_Pipeline).png**                            | Overview of the Databricks Job orchestrating all pipeline tasks                                |
| **[task1]bronze\_table\_ingestion\_fetching\_data\_from\_sentiment\_analysis\_api.png**  | Screenshot of the first task output                                                            |
| **[task2]bronze\_volume\_ingestion\_fetching\_data\_from\_sentiment\_analysis\_api.png** | Screenshot of the second task output                                                           |
| **[task3\_dlt\_pipeline]silver\_transformation\_used\_for\_dlt\_pipeline.png**           | Screenshot of the third task (DLT Silver)                                                      |
| **[task4]gold\_aggregates\_for\_ad\_hoc\_analysis.png**                                  | Screenshot of the fourth task (Gold aggregates)                                                |

---

## Architecture

This project uses the **Medallion Architecture**:

1. **Bronze (Raw)**

   - API → Delta table
   - API → CSV files

2. **Silver (Clean & Enrich)**

   - Delta Live Tables unifies and cleans streams, enforces schema.

3. **Gold (Curated)**

   - SQL transforms to produce tables optimized for analytics.



And here’s the end-to-end job setup that ties everything together:



---

## How to Use

### 1. Clone the repo

```bash
git clone https://github.com/your-username/youtube-comments-sentiment-etl-pipeline.git
```

### 2. Set up Databricks

- Create a secret scope for your `QUERY_ID` and `API_TOKEN`.
- Mount a storage volume for CSV outputs (DBFS or external).

### 3. Import notebooks

- Upload all `.ipynb` files into your Databricks workspace under a folder of your choice.

### 4. Prepare Catalogs & Schemas

- Verify Unity Catalog is enabled.
- Create schemas: `bronze`, `silver`, `gold` under the `youtube2` catalog.

### 5. Configure & Run the Job

- Create a Databricks Job with four sequential tasks:
  1. Bronze Delta ingestion (`bronze_table_ingestion...`)
  2. Bronze CSV ingestion (`bronze_volume_ingestion...`)
  3. Silver DLT pipeline (`silver_transformation...`)
  4. Gold SQL transformations (`gold_aggregates...`)
- Kick off the job and watch each medallion layer complete in order.

### 6. Explore the Results

- **Bronze**: `youtube2.bronze.raw_api_data`
- **Silver**: `youtube2.silver.cleaned_api_data`
- **Gold**: `youtube2.gold.comments_by_video`, `author_details`, `sentiment_details`

---

## Visualizations & Insights

- **Comments by Video**: Track comment volume and sentiment per video.
- **Author Engagement**: Analyze top commenters and their activity.
- **Sentiment Trends**: See how sentiment shifts over time across videos.



---

## Results

- Achieved a **scalable pipeline** that processes thousands of comments with minimal latency.
- Demonstrated **schema enforcement** and **data quality** using DLT.
- Produced **actionable tables** for dashboarding tools like Power BI or Tableau.

---

## Future Enhancements

1. **Parameterize** notebooks for dynamic date ranges and credentials.
2. **Automate tests** and implement data quality checks.
3. **Integrate ML models** for predictive sentiment analysis.
4. **Publish dashboards** directly from Databricks to Power BI.

---

## Contact

If you have questions or suggestions, feel free to reach out:

- **Email**: [paidikalayesukrishna@gmail.com](mailto\:paidikalayesukrishna@gmail.com)
- **LinkedIn**: [paidikala-yesukrishna](https://www.linkedin.com/in/paidikala-yesukrishna-b00121202/)

Thanks for checking out my project! 🚀
