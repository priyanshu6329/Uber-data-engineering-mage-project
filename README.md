# End-to-End Uber Data Engineering Project

![Project Banner](https://user-images.githubusercontent.com/81239436/226089993-8a82cf59-52e9-44ea-b9f9-3f1a5472859c.png)

This project demonstrates a complete end-to-end data engineering pipeline built using modern tools. The goal was to process a raw Uber dataset, model it, and create a BI dashboard for analysis. This repository contains all the necessary code, configurations, and documentation to reproduce the project.

---

## 🏛️ Project Architecture

The project follows a modern data stack architecture, leveraging the strengths of Google Cloud Platform and open-source tools.

1.  **Data Source**: Raw Uber trip data in CSV format.
2.  **Ingestion**: Data is uploaded to a **Google Cloud Storage (GCS)** bucket, which acts as our data lake.
3.  **Orchestration & Transformation**: A **Mage** pipeline, deployed on a **Google Compute Engine** virtual machine, is triggered. It extracts the data from GCS, performs transformations using **Python (Pandas)** to clean the data and model it into a fact-dimensional schema.
4.  **Data Warehouse**: The transformed, structured data is loaded into **Google BigQuery**.
5.  **Business Intelligence**: An analytical view is created in BigQuery by joining the fact and dimension tables. This view is then connected to **Looker Studio (formerly Google Data Studio)** to build an interactive dashboard for visualizing key business metrics.

Here is a diagram of the cloud architecture:
