# MLE_lab2
Working with PySpark

##Project Overview

This repository contains a containerized data processing pipeline that implements a Medallion Architecture. It is designed to reliably ingest raw daily loan data, apply staged transformations, and output refined datasets in Parquet format. The containerized approach ensures a consistent runtime environment for all data operations.

##Repository Structure

The project relies on modular Python scripts, orchestrated environments, and isolated processing stages:

main.py: The primary entry point for executing the end-to-end data pipeline.

data_processing_main.ipynb: An interactive Jupyter Notebook designed for pipeline testing, step-by-step execution, and data exploration.

utils/: The core directory housing the transformation logic across three files: data_processing_bronze_table.py, data_processing_silver_table.py, and data_processing_gold_table.py.

bronze_label_store.py: A specialized script managing the label storage mechanism during the initial data ingestion phase.

data/: The local source directory containing raw input files, specifically lms_loan_daily.csv.

Dockerfile & docker-compose.yaml: Definitions for packaging the application into a Docker image and orchestrating the necessary container services.

requirements.txt: A manifest of all required Python libraries and dependencies.

##Data Pipeline Flow
The architecture processes information sequentially through three distinct maturity layers:

Bronze Layer: Ingests raw CSV loan data and writes it to Parquet format, creating an immutable historical record without altering the original values.

Silver Layer: Cleanses, filters, and standardizes the data from the Bronze layer, resolving missing values and establishing a conformed schema for analysis.

Gold Layer: Aggregates the cleansed Silver data into highly refined, business-level tables optimized for downstream analytics, reporting, and label generation.

##Getting Started
To initialize and run this pipeline on your local machine, follow these steps:

Navigate to the root directory of the project within your terminal.

Ensure Docker Desktop or the Docker daemon is actively running on your system.

Execute the environment build using Docker Compose to automatically install dependencies and run the pipeline inside an isolated container.

To run the project locally without Docker, install the packages listed in requirements.txt via pip and execute main.py using your standard Python interpreter.
