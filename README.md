# 🏅 Tokyo Olympic Data Analytics Project

## 📌 Project Overview

This comprehensive data engineering project demonstrates an end-to-end Azure-based data pipeline for analyzing Tokyo Olympic Games data. By leveraging cutting-edge cloud technologies and data processing tools, the project transforms raw Olympic data into meaningful insights that reveal the performance, diversity, and dynamics of the world's premier sporting event.

## 🎯 Project Objectives

- Develop a scalable and robust data engineering pipeline
- Process and analyze Tokyo Olympic Games dataset
- Generate actionable insights through advanced data analytics
- Showcase best practices in cloud-based data infrastructure

## 🔹 Architecture and Data Flow

```
Data Source 
    ↓ 
Azure Data Factory (Ingestion)
    ↓
Azure Data Lake Gen2 (Storage)
    ↓
Azure Databricks (Processing & Transformation)
    ↓
Azure Synapse Analytics (Data Warehousing)
    ↓
Power BI / Looker Studio / Tableau (Visualization)
```

## 🛠️ Technologies and Tools

### Cloud Platform
- **Microsoft Azure**
  - Azure Data Factory
  - Azure Data Lake Gen2
  - Azure Databricks
  - Azure Synapse Analytics

### Data Processing
- **Apache Spark**
- **PySpark**
- **Python**

### Visualization Tools
- Power BI
- Looker Studio
- Tableau

## 🔬 Key Data Processing Steps

### 1. Data Ingestion
- Source: Tokyo Olympic Games dataset
- Method: Azure Data Factory
- Storage: Azure Data Lake Gen2

### 2. Data Transformation (PySpark)
- Data cleaning
- Type casting
- Handling missing values
- Aggregation and enrichment

### 3. Data Analytics
- Advanced statistical analysis
- Performance metrics computation
- Cross-country comparisons

## 📊 Insights Generated

The project generates comprehensive insights such as:
- Detailed medal tallies by country
- Athlete performance metrics
- Gender distribution across sports
- Historical performance trends
- Coaching and team composition analysis

## 🚀 Getting Started

### Prerequisites
- Azure Account
- Azure CLI
- Databricks Workspace
- Power BI or Tableau (optional)

### Setup and Installation

1. **Azure Resource Provisioning**
   ```bash
   # Create resource group
   az group create --name TokyoOlympicDataProject --location eastus

   # Create Data Lake Storage
   az storage account create --name tokyoolympicdatalake --resource-group TokyoOlympicDataProject

   # Create Databricks workspace
   az databricks workspace create --resource-group TokyoOlympicDataProject --name TokyoOlympicDatabricks
   ```

2. **Data Ingestion**
   - Upload raw CSV files to Azure Data Lake Gen2
   - Configure Azure Data Factory pipelines

3. **Data Processing**
   - Open Databricks workspace
   - Import and run transformation notebooks
   - Execute PySpark scripts for data cleaning

4. **Analytics and Visualization**
   - Connect Azure Synapse Analytics
   - Create dashboards in Power BI or Tableau

## 📝 Sample PySpark Transformation

```python
from pyspark.sql.functions import col
from pyspark.sql.types import IntegerType, StringType

def transform_olympic_data(spark, input_path, output_path):
    # Read raw data
    athletes_df = spark.read.csv(input_path, header=True, inferSchema=True)
    
    # Data transformations
    transformed_df = (
        athletes_df
        .withColumn("Age", col("Age").cast(IntegerType()))
        .withColumn("Country", col("Country").cast(StringType()))
        .dropDuplicates()
        .na.drop()
    )
    
    # Write transformed data
    transformed_df.write.mode("overwrite").parquet(output_path)
```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request


Your Name - Sachin Loddiya Karthik

Project Link: https://github.com/SachinLoddiyaKarthik/tokyo-olympic-data-engineering-project.git

## 🙏 Acknowledgements

- Microsoft Azure
- Apache Spark
- Databricks
- Tokyo 2020 Olympic Committee

---

**Note**: Ensure you have necessary permissions and follow best practices for data privacy and security.
