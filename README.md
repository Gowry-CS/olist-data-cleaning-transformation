<div align="center">
<h2> Olist Data Cleaning & Transformation (Raw to Analysis Ready Data) </h2>

##### Bronze → Silver → Gold (Medallion Architecture)
</div>

### 📌 Project Overview
This project focuses on cleaning, standardising, and transforming messy raw e-commerce data from the Olist dataset into analysis-ready, high-integrity datasets.
Using the Medallion Architecture (Bronze → Silver → Gold), the project demonstrates how raw, user-generated data can be systematically validated, reconciled, and modelled into a Galaxy Schema optimised for OLAP and downstream analytics.
The goal of this project is to establish a reliable analytical foundation that supports accurate reporting, business insights, and scalable analytics.

### 🏗 Architecture Overview
| **Layer** | **Purpose** |
|--------|-------------|
| Bronze (raw) | Ingest raw CSV data with minimal transformation |
| Silver (cleaned) | Clean, validated, standardised, and normalised datasets |
| Gold (Analytics) | Star/Galaxy schema optimised for analytical queries |

### 🥉 Bronze Layer – Raw Data Ingestion
- Ingested raw Olist CSV files as-is via Kaggle API
- Preserved original schema and user-generated fields
- No assumptions made about data correctness at this stage
- Used as a single source of truth for raw data

### 🥈 Silver Layer – Data Cleaning & Transformation
The Silver layer focuses on **data quality, consistency, and integrity**. 

#### Key Cleaning & Transformation Strategies
###### 1. Geolocation Standardisation
- Resolved inconsistent city name spellings caused by:
  - Accents, casing, spacing, punctuation, and hyphenation
- Avoided unreliable string-based matching for analysis
- Standardised location data using:
  - Zip code–based joins
  - Official Brazilian municipality reference data (br-city-codes.csv)
- Applied:
  - Unicode normalisation (unidecode)
  - String regularisation
  - Fuzzy matching (Levenshtein distance) for plausible corrections
- Conservatively handled ambiguous cases to avoid over-cleaning
