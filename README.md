# End-to-End Data Engineering Project: NYC Taxi Data Analytics

![Project Banner](https://i.imgur.com/7b2zV5V.png)

This project is a complete, end-to-end data engineering pipeline built on the Google Cloud Platform (GCP). It processes raw NYC Yellow Taxi trip data from ingestion and transformation to storage in a data warehouse and final visualization on a business intelligence dashboard.

The entire workflow is orchestrated using the open-source data pipeline tool, **Mage AI**.

---

## 🏛️ Cloud Architecture & Tech Stack

The architecture for this project was designed to be scalable, cost-effective, and entirely cloud-based, using a modern data stack.

* **Cloud Provider**: Google Cloud Platform (GCP)
* **Data Ingestion/Data Lake**: Google Cloud Storage (GCS)
* **Orchestration & Transformation**: Mage AI running on a Google Compute Engine VM
* **Programming Language**: Python (with Pandas)
* **Data Warehouse**: Google BigQuery
* **Business Intelligence**: Google Looker Studio

![Architecture Diagram](<![architecture](https://github.com/user-attachments/assets/d5a6187a-be50-4714-af56-49165ed7d6bf)
>)

---

## 📊 Dataset Overview

This project utilizes the **Yellow Taxi Trip Records** dataset, which is publicly available from the [NYC Taxi and Limousine Commission (TLC)](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page). The data is in CSV format and contains detailed information for each trip, making it ideal for demonstrating ETL processes and business intelligence analysis.

Key fields in the raw dataset include:
* **VendorID**: A code indicating the TPEP provider that provided the record.
* **tpep_pickup_datetime**: The date and time when the meter was engaged.
* **tpep_dropoff_datetime**: The date and time when the meter was disengaged.
* **passenger_count**: The number of passengers in the vehicle.
* **trip_distance**: The elapsed trip distance in miles.
* **RatecodeID**: The final rate code in effect at the end of the trip. (e.g., Standard rate, JFK, Newark).
* **PULocationID** & **DOLocationID**: The pickup and drop-off location IDs.
* **payment_type**: A numeric code signifying how the passenger paid for the trip. (e.g., Credit card, Cash).
* **fare_amount**: The time-and-distance fare calculated by the meter.
* **tip_amount**: The tip amount. This field is automatically populated for credit card tips.
* **total_amount**: The total amount charged to passengers.

---

## ✨ Final Looker Studio Dashboard

The project culminates in an interactive dashboard that provides key insights into the NYC Taxi dataset.

#### **Geographic Analysis of Trip Pickups**
<img src="YOUR_MAP_IMAGE_LINK_HERE" alt="Map View of NYC Taxi Trips" width="700"/>

#### **Revenue and Payment Analysis**
<img src="YOUR_BAR_CHART_IMAGE_LINK_HERE" alt="Bar chart of total amount by rate code" width="400"/> <img src="YOUR_PIE_CHART_IMAGE_LINK_HERE" alt="Pie chart of total amount by payment type" width="400"/>

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
