# <div align="center">

# 🎵 Spotify End-to-End Data Engineering Project

### 🚀 Building a Scalable Cloud Data Pipeline with Azure & Databricks

<p>
  <img src="https://img.shields.io/badge/Azure-Data%20Engineering-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white"/>
  <img src="https://img.shields.io/badge/Azure%20Data%20Factory-ETL-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white"/>
  <img src="https://img.shields.io/badge/Databricks-PySpark-FF3621?style=for-the-badge&logo=databricks&logoColor=white"/>
  <img src="https://img.shields.io/badge/Apache%20Spark-Big%20Data-E25A1C?style=for-the-badge&logo=apachespark&logoColor=white"/>
  <img src="https://img.shields.io/badge/SQL-Database-4479A1?style=for-the-badge&logo=postgresql&logoColor=white"/>
</p>

<p>
  <strong>Azure Data Factory → Azure Data Lake → Databricks → PySpark → Delta → SQL</strong>
</p>

</div>

---

## 📌 Project Overview

This project demonstrates an **end-to-end cloud data engineering pipeline** for processing Spotify-style music streaming data using Microsoft Azure and Azure Databricks.

The solution extracts data from **Azure SQL Database**, performs **incremental data ingestion using Azure Data Factory**, stores the data in **Azure Data Lake Storage**, and processes the data using **Databricks and PySpark**.

The project also demonstrates **CDC-based incremental processing, SCD Type 2, data-quality validation, dynamic pipelines, dimensional modeling, and pipeline monitoring/alerting**.

### 🔄 End-to-End Data Flow

```text
Azure SQL Database
        │
        ▼
Azure Data Factory
        │
        │ Incremental / CDC Load
        ▼
Azure Data Lake Storage
        │
        │ Bronze
        ▼
Azure Databricks
        │
        │ PySpark / DLT
        ▼
Silver Layer
        │
        │ CDC + SCD Type 2
        ▼
Gold Layer
        │
        ▼
Analytics-Ready Data
```

---

## 🎯 Project Objective

The main objective of this project is to design a **scalable and maintainable data pipeline** that can:

- Ingest data from Azure SQL Database
- Perform incremental data extraction
- Store raw data in Azure Data Lake
- Process data using Azure Databricks
- Transform data using PySpark
- Implement CDC processing
- Maintain historical changes using SCD Type 2
- Apply data-quality rules
- Handle empty or unavailable data
- Monitor pipeline execution
- Trigger alerts when pipeline processing requires attention
- Produce analytics-ready dimensional data

---

# 💼 Business Problem

Modern music streaming platforms generate large volumes of data from users, artists, tracks, and streaming activities.

As the volume of data increases, repeatedly processing the complete dataset becomes inefficient.

This project addresses the challenge by implementing an **incremental data engineering architecture** where only newly inserted or updated records are processed during subsequent pipeline executions.

### The solution focuses on:

- ⚡ Incremental data ingestion
- 🔄 Change Data Capture (CDC)
- 🏗️ Scalable data processing
- 🧹 Data-quality validation
- 📚 Historical data tracking
- 📊 Dimensional data modeling
- 🚨 Pipeline monitoring and alerting
- ☁️ Cloud-based data engineering

### Business Flow

```text
Raw Source Data
      ↓
Incremental Extraction
      ↓
Cloud Data Lake
      ↓
Data Transformation
      ↓
Historical Data Management
      ↓
Analytics-Ready Dataset
```

The architecture is designed to demonstrate how a data engineering team can move data from operational systems into a structured analytical environment while minimizing unnecessary data movement and processing.


---

# 🏗️ Solution Architecture

The project follows a layered cloud data engineering architecture using **Azure Data Factory, Azure Data Lake Storage, Azure Databricks, PySpark, and SQL**.

```text
                         ┌──────────────────────┐
                         │      Azure SQL       │
                         │                      │
                         │  DimUser             │
                         │  DimArtist           │
                         │  DimTrack            │
                         │  DimDate             │
                         │  FactStream          │
                         └──────────┬───────────┘
                                    │
                                    │ Incremental Load
                                    │ CDC / Watermark
                                    ▼
                    ┌──────────────────────────────┐
                    │      Azure Data Factory      │
                    │                              │
                    │  Lookup                      │
                    │  ForEach                     │
                    │  Copy Activity               │
                    │  If Condition                │
                    │  Script Activity             │
                    │  Dynamic Datasets            │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                    ┌──────────────────────────────┐
                    │     Azure Data Lake Storage  │
                    │                              │
                    │          BRONZE              │
                    │                              │
                    │       Parquet Files          │
                    │       CDC Checkpoints        │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                    ┌──────────────────────────────┐
                    │       Azure Databricks       │
                    │                              │
                    │          PySpark             │
                    │          DLT                 │
                    │       Streaming              │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                    ┌──────────────────────────────┐
                    │           SILVER             │
                    │                              │
                    │   Cleaned & Transformed      │
                    │           Data               │
                    └──────────────┬───────────────┘
                                   │
                                   │ CDC
                                   │ SCD Type 2
                                   ▼
                    ┌──────────────────────────────┐
                    │            GOLD              │
                    │                              │
                    │       DimUser                │
                    │       DimArtist              │
                    │       DimTrack               │
                    │       DimDate                │
                    └──────────────┬───────────────┘
                                   │
                                   ▼
                          📊 Analytics Layer
```

### Architecture Layers

| Layer | Technology | Purpose |
|---|---|---|
| Source | Azure SQL | Operational source data |
| Ingestion | Azure Data Factory | Data extraction and orchestration |
| Storage | Azure Data Lake | Raw/landing data storage |
| Processing | Azure Databricks | Distributed data processing |
| Transformation | PySpark / DLT | Data transformation |
| Silver | Databricks | Cleaned and processed data |
| Gold | Databricks | Analytics-ready dimensional data |
| Analytics | SQL / BI | Downstream analytical workloads |


---

# 🛠️ Technologies Used

<div align="center">

| Technology | Purpose |
|---|---|
| ☁️ **Microsoft Azure** | Cloud platform |
| 🔄 **Azure Data Factory** | Data ingestion and orchestration |
| 🗄️ **Azure SQL Database** | Source and relational data |
| 💾 **Azure Data Lake Storage** | Cloud data storage |
| 🔥 **Azure Databricks** | Big data processing |
| ⚡ **Apache Spark** | Distributed data processing |
| 🐍 **PySpark** | Data transformation |
| 🧱 **Delta Lake** | Lakehouse data management |
| 🗃️ **SQL** | Data modeling and querying |
| 🔁 **CDC** | Incremental data processing |
| 📚 **SCD Type 2** | Historical dimension tracking |
| 🧩 **DLT / Lakeflow** | Declarative data pipelines |
| 📦 **Databricks Asset Bundles** | Project deployment structure |
| 🌐 **Git / GitHub** | Version control |

</div>

---

# 🗄️ Source Data Model

The source system is implemented using **Azure SQL Database** and contains dimensional and fact data representing a music streaming platform.

## 📐 Data Model

### Dimension Tables

| Table | Description |
|---|---|
| `DimUser` | User information |
| `DimArtist` | Artist information |
| `DimTrack` | Track information |
| `DimDate` | Date dimension |

### Fact Table

| Table | Description |
|---|---|
| `FactStream` | Music streaming / playback events |

### Logical Relationship

```text
                    DimUser
                       │
                       │
                       ▼
DimArtist ───────► FactStream ◄─────── DimTrack
                       │
                       │
                       ▼
                    DimDate
```

This dimensional structure separates descriptive attributes from streaming events and provides a foundation for analytical workloads.


---

# ✅ Data Quality

Data-quality validation is incorporated into the Databricks transformation layer.

For example, the `DimUser` pipeline contains a validation rule requiring:

```text
user_id IS NOT NULL
```

### Validation Flow

```text
Incoming Data
      │
      ▼
Data Quality Rules
      │
      ├───────────────┐
      ▼               ▼
Valid Records     Invalid Records
      │               │
      ▼               ▼
Continue          Excluded
Processing
```

The data-quality framework can be extended with additional rules as the pipeline evolves.

### Example Validation

```text
Rule:
user_id IS NOT NULL
```

This helps prevent records with missing business keys from entering the downstream dimensional layer.

---

# 🚨 Error Handling & Pipeline Monitoring

The Azure Data Factory pipeline includes an alerting mechanism using a **Web Activity** connected to an Azure Logic Apps HTTP endpoint.

The alerting mechanism can provide pipeline execution information such as:

- Pipeline name
- Pipeline Run ID
- Execution status

### Monitoring Flow

```text
ADF Pipeline
      │
      ▼
ForEach Processing
      │
      ▼
Pipeline Execution
      │
      ├───────────────┐
      ▼               ▼
   Success          Failure
      │               │
      └───────┬───────┘
              ▼
        Alert Activity
              │
              ▼
       Azure Logic Apps
              │
              ▼
       Notification
```

This provides a mechanism for identifying pipeline execution issues without manually checking every pipeline run.

---

# 📚 Key Learnings

Through this project, I gained practical experience with:

### Azure Data Factory

- Designing parameterized pipelines
- Dynamic datasets
- Lookup activities
- ForEach processing
- Copy Data activity
- Conditional execution
- Incremental loading
- Pipeline monitoring

### Azure Data Lake

- Data lake folder organization
- Bronze-layer ingestion
- Parquet storage
- CDC checkpoint management

### Azure Databricks

- Databricks project structure
- PySpark transformations
- Streaming data processing
- DLT-based transformations
- CDC processing
- SCD Type 2

### Data Engineering Concepts

- ETL / ELT
- Incremental processing
- Change Data Capture
- Medallion Architecture
- Dimensional Modeling
- Data Quality
- Historical Data Management
- Pipeline Monitoring

- ---

# 👨‍💻 About the Developer

I am a **Data Engineering professional focused on building cloud-based data pipelines using Microsoft Azure, Databricks, PySpark and SQL**.

This project represents my hands-on experience with designing data ingestion workflows, implementing incremental processing, transforming data using distributed processing technologies, and creating analytics-ready datasets.

### Core Areas

```text
Azure
  ├── Azure Data Factory
  ├── Azure Data Lake
  ├── Azure SQL
  └── Azure Synapse

Databricks
  ├── PySpark
  ├── Spark
  ├── Delta Lake
  ├── DLT
  └── CDC / SCD Type 2

Data Engineering
  ├── ETL / ELT
  ├── Incremental Loading
  ├── Data Quality
  ├── Dimensional Modeling
  └── Lakehouse Architecture
```

---

# 🤝 Connect With Me

<div align="center">

If you are interested in **Data Engineering, Azure, Databricks, PySpark or Cloud Data Platforms**, feel free to explore my repositories.

### ⭐ If you find this project useful, consider giving the repository a star!

</div>
