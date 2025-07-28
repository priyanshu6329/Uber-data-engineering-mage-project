# End-to-End Uber Data Engineering Project

This project is a complete, end-to-end data engineering pipeline built on the Google Cloud Platform (GCP). It processes raw NYC Yellow Taxi trip data from ingestion and transformation to storage in a data warehouse and final visualization on an interactive business intelligence dashboard.

The entire workflow is orchestrated using the open-source data pipeline tool, **Mage AI**.

---

## 🏛️ Cloud Architecture & Tech Stack

The project follows a modern, scalable, and cloud-native architecture, leveraging the strengths of the Google Cloud ecosystem. The data flows from raw storage to final insights as shown below.

![Architecture Diagram](https://github.com/priyanshu6329/Uber-data-engineering-mage-project/blob/main/architecture.jpg?raw=true)

The technology stack includes:
* **Cloud Provider**: Google Cloud Platform (GCP)
* **Data Ingestion/Data Lake**: Google Cloud Storage
* **Orchestration & Transformation**: Mage AI running on a Google Compute Engine VM
* **Programming Language**: Python (with Pandas)
* **Data Warehouse**: Google BigQuery
* **Business Intelligence**: Looker (formerly Looker Studio)

---

## 📊 Data Modeling

To optimize for analytical queries and performance, the data was modeled into a **Star Schema**. This schema consists of a central `fact_table` containing quantitative measures of each trip and foreign keys that link to multiple descriptive **dimension tables**.

This dimensional model simplifies complex queries and allows for efficient filtering and aggregation of the data.

![Data Model](https://github.com/priyanshu6329/Uber-data-engineering-mage-project/blob/main/data_model.jpeg?raw=true)

---
---

## 📊 Dataset Overview

This project utilizes a public dataset of Uber taxi trips. The data is in CSV format and contains detailed information for each trip, making it ideal for demonstrating ETL processes and business intelligence analysis.

Key fields in the raw dataset include:
* **VendorID**: A code indicating the TPEP provider that provided the record.
* **tpep\_pickup\_datetime**: The date and time when the meter was engaged.
* **tpep\_dropoff\_datetime**: The date and time when the meter was disengaged.
* **passenger\_count**: The number of passengers in the vehicle.
* **trip\_distance**: The elapsed trip distance in miles.
* **RatecodeID**: The final rate code in effect at the end of the trip. (e.g., Standard rate, JFK, Newark).
* **PULocationID** & **DOLocationID**: The pickup and drop-off location IDs.
* **payment\_type**: A numeric code signifying how the passenger paid for the trip. (e.g., Credit card, Cash).
* **fare\_amount**: The time-and-distance fare calculated by the meter.
* **tip\_amount**: The tip amount. This field is automatically populated for credit card tips.
* **total\_amount**: The total amount charged to passengers.

---
## ✨ Final Looker Dashboard

The project culminates in an interactive dashboard built in Looker that provides a multi-faceted view of the taxi trip data.

### Executive Summary
The main dashboard offers a high-level summary for stakeholders, tracking key performance indicators such as **$1.6M in Total Revenue** from **100K records**. It also features interactive filters for drilling down into the data by Vendor ID, Payment Type, and Rate Code.

<p align="center">
  <img src="https://github.com/priyanshu6329/Uber-data-engineering-mage-project/blob/main/Screenshots/Main%20Dashboard.png?raw=true" alt="Main Dashboard" width="800">
</p>

### Geographic Trip Analysis
A detailed map view allows for geographic analysis of trip density across New York City. Trips are color-coded by their rate code, making it easy to identify patterns in specific areas like JFK, Newark, and Manhattan.

<p align="center">
  <img src="https://github.com/priyanshu6329/Uber-data-engineering-mage-project/blob/main/Screenshots/Map%20View.png?raw=true" alt="Map View" width="800">
</p>

---

## ⚙️ How to Reproduce This Project

To run this project, you will need a GCP account and to follow these setup steps:

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)
    cd your-repo-name
    ```

2.  **GCP Setup**
    * Create a GCP Project and enable the APIs for **Compute Engine, Cloud Storage, and BigQuery**.
    * Create a Service Account with `Storage Admin` and `BigQuery Admin` roles.
    * Create and download the JSON key for this service account.

3.  **Handle Credentials Securely (IMPORTANT!)**
    * **DO NOT** commit your JSON key file to GitHub. Add the filename to your `.gitignore` file.
    * When configuring your Mage data loader, use Mage's secret management to securely store your credentials.

4.  **Run the Pipeline**
    * Deploy Mage on a Compute Engine VM.
    * Create a new Mage project and copy the transformation logic from the `/scripts` folder.
    * Configure the data loader and exporter blocks using your secure credentials.
    * Trigger the pipeline to run the full ETL process.
