# Housing for All: PMAY-G Performance & Social Convergence Dashboard

[![Microsoft Elevate](https://shields.io)](https://github.com)
[![Power BI](https://shields.io)](https://microsoft.com)
[![Python](https://shields.io)](https://python.org)

An enterprise-grade hybrid analytics application combining **Microsoft Power BI Desktop (Developer Mode)** and an automated **Python Data Science Pipeline** to monitor, evaluate, and cross-validate the execution velocity and multi-scheme social convergence metrics of the **Pradhan Mantri Awaas Yojana-Gramin (PMAY-G)** scheme.

---

## 👤 Capstone Project Metadata
*   **Student Name:** Swaranjali Baburao Harkare
*   **College Name:** Dr. J. J. Magdum College Of Engineering, Jaysingpur
*   **Department / Program:** Master of Computer Applications (MCA)
*   **Internship Framework:** Microsoft Elevate AICTE Power BI & Python Analytics Internship

---

## 🚀 Project Overview & Problem Statement
The PMAY-G scheme is implemented across rural India to provide affordable housing alongside integrated welfare utilities (such as clean energy via Pradhan Mantri Ujjwala Yojana and sanitation via the Swachh Bharat Mission). However, monitoring execution speeds, identifying structural delays, and tracking data integration across **3.9 million+ multi-sector records** presents a major visual analysis challenge.

This hybrid project solves this challenge by engineering:
1.  **A Power BI Visual Analytics Portal** mapping delivery funnels, macro performance, and state-level administrative and construction lead-time bottlenecks.
2.  **A Programmatic Python Engine** that automates raw ETL processing on a decade of daily government datasets (2014–2026), cleans structural string and year anomalies, and cross-validates data aggregates to ensure model accuracy.

---

## 📂 Repository Structure

This repository utilizes Power BI's modern developer mode (`.pbip`) to break down the traditional binary model into itemized, version-controlled JSON schemas alongside the automated Python scripting directory.

```text
├── .gitignore                        # Filters local cache files, pycaches, and user config logs
├── README.md                         # Main repository landing page & documentation
│
├── PMAY_G_Dashboard.pbip             # Power BI Project metadata anchor file tracking structural paths
├── PMAY_G_Dashboard.Report/          # Visual layouts, canvas sizing, formatting JSON, and page bookmarks
└── PMAY_G_Dashboard.Dataset/         # Data model definitions, column mappings, and custom DAX measures
    └── model.bim                     # Complete relational Star Schema structural rules database
│
└── Python_Analysis/                  # Programmatic Data Pipeline & Analytics Engine
    ├── requirements.txt              # Dependency file managing local execution runtimes
    ├── analysis_workflow.ipynb       # Main notebook automating data extraction, ETL, and plot generation
    ├── clean_housing_fact.csv        # Output dataset: Cleaned, structured housing fact table
    ├── top_10_sanctioned_states.png  # Exported statistical graphic asset (Volumetric Leader Check)
    └── completion_time_distribution.png # Exported statistical graphic asset (Delay Skewness Check)
```

---

## 🛠️ Hybrid System Implementation & Features

### 🖥️ 1. Power BI Portal Dashboards

*   **Overview Analytics:** Tracks the national target scale. Out of **29.72 million houses sanctioned**, **19.46 million** units have been completed. It identifies **Bihar** as the absolute completion volume leader and **West Bengal** as the baseline minimum volume state, with national completion volumes peaking in **2022 at over 5.67 million finished units**.
*   **Efficiency Audit Module:** Establishes an overall housing **Completion Rate of 65.49%**. By evaluating administrative approval, physical construction, and transaction processing durations by state, it programmatically proves that **physical construction time**—rather than paperwork or financial transaction lag—is the primary driver of project delays in slow-turnaround zones like Goa and Chhattisgarh.
*   **Social Convergence Module:** Evaluates holistic village utility distribution. It maps an excellent clean energy funnel (**3.96M Ujjwala registrations** yielding a **97.4% sanction rate**), but exposes a severe policy delivery drop-off in sanitation, where **Swachh Bharat Mission (SBM) sealing integration lags significantly at just a 1.7% saturation rate**.

### 🐍 2. Python Automated Analytics Engine
The Python workflow (`Python_Analysis/analysis_workflow.ipynb`) acts as an automated data-engineering loop that replaces manual Power Query manipulations. 

*   **Robust ETL Cleansing:** Strips whitespace from geographical string entries, adjusts mixed-case syntax, and uses lambda functions to clamp negative timeline phase errors to `0` to prevent analytical skewness.
*   **Feature Engineering:** Uses regex parsing routines to reliably extract standard integer year identifiers from complex text blocks (e.g., parsing `2024` from `"Financial Year (Apr - Mar), 2024"`).
*   **Programmatic Cross-Validation:** Computes global sums, averages, and group rankings directly from flat-file records using `pandas`. This verifies that the underlying arithmetic matches your Power BI custom DAX calculations down to the exact whole number.
*   **Advanced Visual Output:** Leverages `seaborn` and `matplotlib` to export high-definition statistical charts (bar plots and distribution skews) directly into the file index directory.

---

## 📐 Enterprise Core Data Architecture

### Data Modeling (Star Schema)
To prevent circular data paths, many-to-many lookup complexities, and performance lag, the application decouples multi-sectoral data into an optimized Star Schema. Disparate operational records (Housing Performance, Phase-Based Delays, and Sanitation/LPG Seeding Status) are arranged as independent fact layers and mapped via single-direction filters through unified dimension tables:
*   `Dim_State` (Centralized Geographical Lookup for 31 States and UTs)
*   `Dim_Calendar` / `Year` (Centralized Date Table)

### Custom DAX Calculation Engine Examples
*   **Housing Completion Rate % Measure:**
    ```dax
    Completion Rate % = 
    DIVIDE(
        SUM('Fact_Housing'[Total Houses Completed]), 
        SUM('Fact_Housing'[Total Houses Sanctioned]), 
        0
    )
    ```
*   **LPG Convergence Saturation Funnel Rate % Measure:**
    ```dax
    LPG Saturation Rate % = 
    DIVIDE(
        SUM('Fact_Convergence'[Total Houses With Lpg Connection]), 
        SUM('Fact_Convergence'[Total Registration For Ujjwala Connection]), 
        0
    )
    ```

---

## 🔧 Local Installation & Version Control Setup

1. **Clone the repository onto your local system:**
   ```bash
   git clone https://github.com.git
   cd week_4/Final\ Project
   ```

2. **Environment Synchronization (Python):**
   Install the necessary programmatic data science libraries through pip:
   ```bash
   pip install -r Python_Analysis/requirements.txt
   ```

3. **Repository Cleanliness Management:**
   This project contains a root-level `.gitignore` file that automatically excludes Power BI background caches (`.pbi/`), local layout configurations (`*.user.config`), and runtime byte-codes (`__pycache__/`) from entering tracking logs. This guarantees a clean, lightweight version history optimized for multi-developer collaboration.

---

## 🔮 Future Development Scope
*   **Live Database Pipeline:** Scale the Python analytics stack from raw flat-files into an optimized database environment using an **SQLite or PostgreSQL** engine mapped via `SQLAlchemy`.
*   **Automated Sync Scripts:** Wire the current extraction architecture directly to NITI Aayog's open REST API endpoints using Python's `requests` library to fetch updates automatically.
*   **Machine Learning Modeling:** Build a predictive regression model within the notebook layer using `scikit-learn` to forecast project completion dates based on historical state-level execution speeds and social category distributions.

---

## 🔗 Technical References & Workspace Data Sourcing
*   **Primary Government Repository Sourced:** [NITI Aayog National Data and Analytics Platform (NDAP)](https://niti.gov.in)
*   **Production Deployment Space:** [GitHub Capstone Project Repository Link](https://github.com/tree/main/week_4/Final%20Project)

***

## 📜 License
Distributed under the MIT License. See `LICENSE` for more information.
