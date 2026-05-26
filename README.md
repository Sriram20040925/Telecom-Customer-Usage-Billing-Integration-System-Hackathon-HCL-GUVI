Telecom Customer Usage & Billing Integration System (IICS + Flat File Targets)
Project Overview

This project is an end-to-end Telecom Data Integration and Billing Analytics System developed using:

Oracle Database (Source System)
Informatica IICS (ETL Tool)
Flat Files (CSV) as Target Layer
Power BI (Reporting Layer)

The system processes:

Customer master data
Usage records (Call, SMS, Data)
Billing transactions
Usage alerts
Customer analytics (Top 5 customers)

It implements:

Incremental loading
Data validation rules
Reject handling
Lookup-based validations
Aggregation and ranking logic
Flat file based data delivery


Hour 1 - Project Setup and Database Design
Activities Completed
Created Oracle source tables:
SRC_CUSTOMER_MASTER
SRC_USAGE_RECORD
SRC_BILLING_TRANSACTION
SRC_SUBSCRIPTION_PLAN
Designed flat file target structures (CSV format):
TGT_CUSTOMER_MASTER.csv
TGT_USAGE_RECORD.csv
TGT_BILLING_TRANSACTION.csv
USAGE_ALERT.csv
INVALID_USAGE_REJECT.csv
INVALID_BILLING_REJECT.csv
Inserted sample datasets for testing ETL flows
Defined relationships and constraints in source database
Outcome

A structured telecom source system was created with flat file-based target design.



Hour 2 - Informatica IICS Setup and Connections
Activities Completed
Configured Oracle source connection in IICS
Configured Flat File connection (CSV target directory)
Created Secure Agent for execution
Imported source metadata into IICS
Defined flat file target definitions (CSV schema)
Outcome

ETL environment fully configured with Oracle-to-Flat File integration.




Hour 3 - Mapping 1 (Customer Master Load)
Objective

Load and validate customer master data into CSV.

Source

SRC_CUSTOMER_MASTER

Target

TGT_CUSTOMER_MASTER.csv

Transformations Used
Expression Transformation
Lookup Transformation
Router Transformation
Sequence Generator
Business Rules
Mobile number must not be null
Duplicate customers are rejected
Only active customers are processed
Flow

Source → Expression → Lookup → Router → CSV Output / Reject File



Hour 4 - Mapping 2 (Usage Record Processing)
Objective

Process telecom usage data and generate outputs.

Source

SRC_USAGE_RECORD

Targets

TGT_USAGE_RECORD.csv
INVALID_USAGE_REJECT.csv
USAGE_ALERT.csv

Transformations Used
Source Filter (Incremental Load)
Expression Transformation
Lookup Transformation
Router Transformation
Business Rules
Usage amount cannot be negative
Invalid customers are rejected
High usage generates alerts
Incremental loading implemented
Flow

Source → Filter → Expression → Lookup → Router → CSV Outputs



Hour 5 - Mapping 3 (Billing Transaction Processing)
Objective

Validate billing data and generate billing files.

Source

SRC_BILLING_TRANSACTION

Targets

TGT_BILLING_TRANSACTION.csv
INVALID_BILLING_REJECT.csv

Transformations Used
Source Filter
Expression Transformation
Lookup Transformation
Router Transformation
Business Rules
Billing amount must be greater than zero
Invalid customers rejected
Valid transactions stored in CSV
Flow

Source → Filter → Expression → Lookup → Router → CSV Output / Reject File



Hour 6 - Mapping 4 (Usage Alert Generation)
Objective

Generate alert CSV for abnormal usage behavior.

Source

SRC_USAGE_RECORD

Target

USAGE_ALERT.csv

Transformations Used
Expression Transformation
Filter Transformation
Sequence Generator
Business Rules
Data usage > 1000 → HIGH alert
Call usage > 100 → MEDIUM alert
SMS usage > 500 → LOW alert
Flow

Source → Expression → Filter → CSV Alert File



Hour 7 - Mapping 5 (Usage Summary and Top 5 Customers)
Objective

Generate aggregated usage report and Top 5 customers.

Source

TGT_USAGE_RECORD.csv (or staging output)

Target

TGT_CUSTOMER_USAGE_SUMMARY.csv

Transformations Used
Expression Transformation
Aggregator Transformation
Sorter Transformation
Rank Transformation
Business Rules
Aggregate usage per customer
Rank customers based on total usage
Extract top 5 customers
Flow

Source → Expression → Aggregator → Sorter → Rank → CSV Output



Hour 8 - Incremental Loading Implementation
Objective

Implement incremental loading using LOAD_DATE.

Source

SRC_CUSTOMER_MASTER

Target

TGT_CUSTOMER_MASTER.csv

Transformations Used
Source Filter (LOAD_DATE condition)
Expression Transformation
Lookup Transformation
Router Transformation
Business Rules
Only new records processed
Duplicate customers rejected
Incremental logic based on LOAD_DATE parameter
Flow

Source → Filter (LOAD_DATE) → Expression → Lookup → Router → CSV Output



Hour 9 - Testing and Validation
Activities Completed
Inserted valid and invalid datasets
Verified CSV outputs
Validated reject files
Checked alert generation files
Tested incremental loading logic
Outcome

All business rules successfully validated through flat file outputs.



Hour 10 - Reporting (Power BI)
Data Sources
CSV output files from Informatica IICS
Dashboards Created
Customer Usage Trends
Billing Analysis
Revenue Performance
Usage Alerts Dashboard
Top 5 Customers Report
Key Features Implemented
Incremental loading using LOAD_DATE
Parameterized mappings
Lookup-based validation
Router-based data separation
Reject file generation
Aggregation and ranking logic
Alert generation system
Flat file based data delivery
Output Files Generated
TGT_CUSTOMER_MASTER.csv
TGT_USAGE_RECORD.csv
TGT_BILLING_TRANSACTION.csv
USAGE_ALERT.csv
INVALID_USAGE_REJECT.csv
INVALID_BILLING_REJECT.csv
TGT_CUSTOMER_USAGE_SUMMARY.csv




Power BI Dashboard 1: Telecom Customer Analytics

<img width="494" height="284" alt="Telecom_Customers_Source" src="https://github.com/user-attachments/assets/f6a6e6c3-6f90-4ac2-a8e9-46148d1c230d" />

Power BI Dashboard 2: Customer Churn Analysis

<img width="514" height="285" alt="Screenshot 2026-05-26 064003" src="https://github.com/user-attachments/assets/5199f657-2dda-450a-9e46-4e545ce63987" />


