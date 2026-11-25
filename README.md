# Quantitative Signal Detection in Post-Market Drug Surveillance
The final project for DEPI 5
# Quantitative Signal Detection in Post-Market Drug Surveillance

**Team:** The_Inner_Circle (Digital Egypt Pioneers Initiative - DEPI, Group `CAI5_DAT3_S1`, Round `773`)  
**Repository:** [Quantitative-Signal-Detection-in-Post-Market-Drug-Surveillance](https://github.com/Abdelrahman-Ezzat-A/Quantitative-Signal-Detection-in-Post-Market-Drug-Surveillance)  
**Project Status:** Ongoing (Data Collection, Cleaning, and Enrichment Completed; SQL Exploratory Analysis, Visualization, and Reporting In Progress)

---

## Project Name
**Quantitative Signal Detection in Post-Market Drug Surveillance**

## Project Idea
An end-to-end pharmacovigilance data engineering and analytics pipeline built on the FDA Adverse Event Reporting System (FAERS) spanning **2021Q1–2026Q2**. The project transforms over 132 million raw quarterly records across seven relational tables into a deduplicated, RxNorm-enriched analytical warehouse to support exploratory clinical safety analysis, disproportionality signal detection, and interactive post-market drug surveillance dashboards.

---

## Team Members
* **Abdelrahman Ezzat Abdelfattah Mohamed** — Team Leader
* **Ahmed Mohamed Yehia Soliman** — Member
* **Moaz Mohamed Kamel Essa** — Member
* **Youssef Sami Georges Naggar** — Member
* **Ahmed Nasser Ahmed Abdul Halim** — Member
* **Ziad Hazem Hussain Mahmoud** — Member *(Inactive)*

---

## Work Plan

| Phase | Scope & Deliverables | Status |
| :--- | :--- | :---: |
| **Phase 1: Data Acquisition** | Ingestion of 22 quarterly FAERS ASCII/XML releases (`2021Q1`–`2026Q2`) and FDA deleted case lists. | **Completed** |
| **Phase 2: Data Engineering & Cleaning** | Schema standardization, non-destructive duplicate archiving, orphan check validation, verbatim dose parsing, and RxNorm/formulation enrichment in Python & DuckDB. | **Completed** |
| **Phase 3: Exploratory Data Analysis (EDA) & SQL** | Relational querying, cohort profiling, and quantitative safety signal detection metrics across the 2021–2026 dataset. | **In Progress** |
| **Phase 4: Visualization & Final Reporting** | Building interactive dashboards, summarizing clinical safety findings, and preparing the final capstone presentation. | **Pending** |

---

## Roles & Responsibilities
* **Abdelrahman Ezzat Abdelfattah Mohamed (Team Leader):** Project coordination, data governance, data collection, Exploratory Data Analysis (EDA), and end-to-end SQL data analysis across the full 2021–2026 FAERS pipeline.
* **Ahmed Mohamed Yehia Soliman:** Python ETL pipeline development (combining quarterly releases into the 7 core FAERS tables, text standardization, duplicate archiving, quality audit checks, drug-name normalization, `DOSE_VBM` parsing, and RxNorm mapping integration).
* **Moaz Mohamed Kamel Essa:** Data exploration, data cleaning validation, and quality review support.
* **Youssef Sami Georges Naggar:** Data repository management, pipeline storage organization (`FAERS_Cleaned_2021_2026_pro`), and analytical support.
* **Ahmed Nasser Ahmed Abdul Halim:** Data preparation, quality verification, and ongoing analytical/reporting support.

---

## KPIs
### Data Engineering & Quality KPIs (Achieved)
* **Temporal Coverage:** 22 consecutive quarters (`2021Q1`–`2026Q2`) consolidated into 7 core relational tables.
* **Total Retained Records:** **131,886,244** unique records across `DEMO` (9.42M), `DRUG` (42.54M), `REAC` (31.65M), `INDI` (27.42M), `THER` (13.43M), `OUTC` (7.15M), and `RPSR` (269.8K).
* **Referential Integrity Rate:** **100%** (0 orphan records across all child tables linked to `DEMO`; 95,602 deleted case IDs isolated).
* **Data Audit Transparency:** **502,965** exact duplicate rows archived and **1,060,011** anomaly/review flags logged across `DEMO` and `DRUG` without destructive data loss.

### Analytical & Reporting KPIs (Target — Ongoing)
* Complete SQL-based EDA and disproportionality signal detection across top suspect drugs and serious adverse outcomes (`OUTC`).
* Deliver an interactive BI dashboard tracking adverse event trends, patient demographics, report sources (`RPSR`), and drug-event safety signals.

---

## Instructor
* **Amr Ayyad, MSc** — Data Analysis Instructor, Digital Egypt Pioneers Initiative (DEPI)

---

## Project Files
The cleaned dataset and audit artifacts are organized in the shared Drive repository ([`FAERS_Cleaned_2021_2026_pro`](https://drive.google.com/drive/folders/1PYbxzwRDdb9GBLag11gdP1YhdGUfA0Ym?usp=sharing)):

```text
FAERS_Cleaned_2021_2026_pro/
├── cleaned_parquet/                  # Primary analytical storage (columnar Parquet format)
│   ├── demo.parquet                  # Cleaned patient demographics (9,418,080 rows)
│   ├── drug.parquet                  # Cleaned drug exposure records (42,541,211 rows)
│   ├── reac.parquet                  # Cleaned adverse reaction terms (31,653,048 rows)
│   ├── outc.parquet                  # Cleaned patient outcomes (7,154,180 rows)
│   ├── ther.parquet                  # Cleaned therapy start/end dates (13,429,451 rows)
│   ├── indi.parquet                  # Cleaned drug indications (27,420,520 rows)
│   ├── rpsr.parquet                  # Cleaned report sources (269,754 rows)
│   ├── deleted_cases.parquet         # Isolated FDA deleted case IDs (95,602 IDs)
│   ├── drug_dose_extraction.parquet  # Parsed dose amount, unit, frequency, and route
│   ├── drug_enrichment.parquet       # Canonical drug names, RxCUIs, and formulation hints
│   └── rxnorm_row_links.parquet      # Row-level RxNorm concept mappings
├── cleaned_csv/                      # Annualized CSV partitions (2021/ through 2026/)
├── cleaned_latest_csv/               # Latest consolidated CSV exports (*_latest.csv)
└── reports/                          # Data governance, QA audit logs, and review queues
    ├── quality_summary.json          # Overall table row accounting and orphan check metrics
    ├── load_statistics.csv           # Quarter-by-quarter ingestion and deduplication counts
    ├── period_coverage.csv           # Status tracker for 2021Q1–2026Q4 quarters
    ├── all_table_flag_counts.csv     # Summary of data quality flags across DEMO and DRUG
    ├── drug_flag_counts.csv          # Breakdown of drug-specific anomaly flags
    ├── dose_parsing_summary.csv      # Summary counts of DOSE_VBM parsing outcomes
    ├── dose_parsing_review.csv       # Detailed records flagged for dose parsing review
    ├── formulation_review.csv        # Records flagged for dosage formulation verification
    └── rxnorm_mapping_review.csv     # Unmatched drug strings queued for RxNorm review
