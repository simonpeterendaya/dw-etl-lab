# End-to-End ETL Lab

An ETL pipeline built using Docker, Apache Airflow, PostgreSQL, Python, and Parquet.

## Project Overview

This project processes sales data from sari-sari stores. It extracts CSV files, cleans invalid records, loads valid sales into PostgreSQL, and performs data quality checks.

## Technologies Used

- Docker and Docker Compose
- Apache Airflow 3.0.6
- PostgreSQL 16
- Python
- Pandas and PyArrow

## ETL Workflow

1. Extract - Reads sales CSV files and saves raw copies.
2. Transform - Removes duplicate and invalid records.
3. Load - Loads valid records into the PostgreSQL warehouse.
4. Quality Check - Verifies data accuracy and consistency.

## How to Run

Requirements:
- Docker Desktop with Docker Compose
- A Linux or WSL environment

Clone the repository:

git clone https://github.com/simonpeterendaya/dw-etl-lab.git

Enter the project:

cd dw-etl-lab

Create the required folders:

mkdir -p logs plugins datalake/raw datalake/staged

Configure the environment:

cp .env.example .env

For Linux or WSL, update AIRFLOW_UID in .env to match the output of `id -u`.

Initialize Airflow:

docker compose up airflow-init

Start the services:

docker compose up -d --build

Open Airflow:

http://localhost:8080

Find the DAG named `sarisari_sales_etl` and trigger it manually.

## Expected Results

After running the pipeline with the included sample data:

- 4 stores
- 22 valid sales records
- 0 sales records with unit prices of PHP 10,000 or higher

## Stop the Services

docker compose stop

## Author

Simon Peter Endaya
