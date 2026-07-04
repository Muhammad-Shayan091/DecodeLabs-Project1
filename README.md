<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:1F3A8A,100:0D1117&height=200&section=header&text=DecodeLabs%20Project%201&fontSize=40&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=Data%20Cleaning%20and%20Preparation%20%7C%20Python%20Pipeline%20%7C%20Batch%202026&descAlignY=58&descSize=16" width="100%"/>

<br/>

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
![Status](https://img.shields.io/badge/Status-Completed-2ea44f?style=for-the-badge)
![Verification](https://img.shields.io/badge/Verification-PASSED-brightgreen?style=for-the-badge)
<<<<<<< HEAD
=======

</div>

---
>>>>>>> c52c3976806e88a18b8a25af7f867482078cd258

A fully reproducible **Python data cleaning and preparation pipeline** that transforms **1,200 raw e-commerce orders** into production-ready data with **zero duplicates**, **zero bad dates**, and **6 business insight charts**.

---

A fully reproducible **Python data cleaning and preparation pipeline** that transforms **1,200 raw e-commerce orders** into production-ready data with **zero duplicates**, **zero bad dates**, and **6 business insight charts**.

---

## Table of Contents

| # | Section |
|---|---------|
| 1 | [Dataset Overview](#-dataset-overview) |
| 2 | [Verification Gate Results](#-verification-gate-results) |
| 3 | [Tools Used](#-tools-used) |
| 4 | [Pipeline — Step by Step](#️-pipeline--step-by-step) |
| 5 | [Insight Charts](#-insight-charts) |
| 6 | [Key Insights & Findings](#-key-insights--findings) |
| 7 | [Project Structure](#-project-structure) |
| 8 | [How to Run](#-how-to-run) |

---

## Dataset Overview

This project uses a **single raw Excel file** containing **1,200 e-commerce orders** spanning January 2023 to June 2025.

### `Dataset_for_Data_Analytics.xlsx` — 1,200 rows × 14 columns

| Column | Type | Description |
|--------|------|-------------|
| `OrderID` | String | Unique order identifier |
| `Date` | Date | Order date (standardised to YYYY-MM-DD) |
| `CustomerID` | String | Unique customer identifier |
| `Product` | String | Product name (Laptop, Chair, Phone, etc.) |
| `Quantity` | Integer | Number of units ordered |
| `UnitPrice` | Float | Price per unit ($) |
| `ShippingAddress` | String | Delivery address |
| `PaymentMethod` | String | Online, Cash, Credit Card, Debit Card, Gift Card |
| `OrderStatus` | String | Delivered, Shipped, Pending, Cancelled, Returned |
| `TrackingNumber` | String | Shipment tracking ID |
| `ItemsInCart` | Integer | Total items in cart at time of order |
| `CouponCode` | String | Discount coupon applied (309 missing → imputed) |
| `ReferralSource` | String | Instagram, Email, Google, Facebook, Referral |
| `TotalPrice` | Float | Total order value ($) |

---

## Verification Gate Results

> Project requirement: **0% error rate on both unique identifiers and date formats.**

<div align="center">

| ✅ Metric | Target | Result | Status |
|:---|:---:|:---:|:---:|
| Duplicate Order IDs | 0 | 0 | ✅ PASSED |
| Invalid / Malformed Dates | 0 | 0 | ✅ PASSED |
| Missing Values Remaining | 0 | 0 | ✅ PASSED |
| Rows Lost During Cleaning | 0 | 0 | ✅ PASSED |
| Raw Rows → Clean Rows | — | 1200 → 1200 | ✅ ZERO DATA LOSS |

</div>

---

## Tools Used

<div align="center">

| Tool | Purpose | Badge |
|------|---------|-------|
| **Python 3.14** | Core scripting language | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) |
| **Pandas** | Data loading, cleaning, transformation | ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white) |
| **Matplotlib** | Insight chart generation | ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=flat-square&logo=python&logoColor=white) |
| **OpenPyXL** | Excel file read/write | ![OpenPyXL](https://img.shields.io/badge/OpenPyXL-217346?style=flat-square&logo=microsoft-excel&logoColor=white) |
| **ReportLab** | PDF change log & quality report generation | ![ReportLab](https://img.shields.io/badge/ReportLab-FF0000?style=flat-square&logo=python&logoColor=white) |
| **VS Code** | Development environment | ![VS Code](https://img.shields.io/badge/VS%20Code-007ACC?style=flat-square&logo=visual-studio-code&logoColor=white) |

</div>

---

## Pipeline — Step by Step

```
📥 Load Raw Data  ──►  🔍 Audit Duplicates  ──►  🩹 Impute Missing  ──►  📅 Standardise Formats  ──►  ✅ Validate  ──►  📊 Insights
```

| Step | Phase | Action | Result |
|------|-------|--------|--------|
| 1 | Ingestion | Load raw Excel file via `pd.read_excel()` | 1,200 rows × 14 columns loaded |
| 2 | Phase 2 — Integrity Audit | Check & remove fully duplicated rows | 0 exact duplicates found |
| 3 | Phase 2 — Integrity Audit | Check & remove duplicate OrderIDs | 0 duplicate IDs — Gate 1 ✅ |
| 4 | Phase 1 — Imputation | Fill 309 missing CouponCode with `"NoCoupon"` | 309 records preserved |
| 5 | Phase 3 — Formatting | Standardise Date to ISO 8601 `YYYY-MM-DD` | 0 invalid dates — Gate 2 ✅ |
| 6 | Phase 3 — Formatting | Trim whitespace + Title Case on text fields | 5 columns standardised |
| 7 | Phase 3 — Formatting | Trim whitespace + UPPER CASE on ID fields | 4 columns standardised |
| 8 | Phase 3 — Formatting | Round prices to 2 decimal places | UnitPrice, TotalPrice standardised |
| 9 | Phase 4 — Validation | Verify TotalPrice = Quantity × UnitPrice | 0 mismatches found |
| 10 | Verification Gate | Final check — 0 duplicate IDs, 0 bad dates | ✅ PASSED |

---

## Insight Charts

> 6 business intelligence charts auto-generated by the pipeline and saved in `/charts`

| # | Chart | Key Finding |
|---|-------|-------------|
| 01 | Monthly Revenue Trend | Revenue fluctuates between $28K–$68K monthly over 30 months |
| 02 | Revenue by Product | Chair & Printer lead total revenue at ~$195K each |
| 03 | Order Status Breakdown | ~20% orders in each status — high cancellation & return rate notable |
| 04 | Payment Method Distribution | Online payments lead (258 orders), all methods nearly equal |
| 05 | Revenue by Referral Source | Instagram drives highest revenue at $275K |
| 06 | Average Order Value by Product | Laptop has highest AOV at $1,111 per order |

---

## Key Insights & Findings

---

### Insight 1 — 309 Missing CouponCode Values

**Finding:** 25.75% of records had no CouponCode value.

**Why it matters:**
- A naive analyst would delete these 309 rows — losing 25% of the dataset permanently
- Listwise deletion reduces statistical power and biases every downstream analysis
- **Fix Applied:** Imputed with `"NoCoupon"` categorical placeholder — 100% records preserved

---

### Insight 2 — Instagram Is The #1 Revenue Driver

**Finding:** Instagram referrals generated $275.3K — highest across all 5 channels.

**Why it matters:**
- Instagram outperforms Google ($250.4K) and Facebook ($250.4K) despite similar order volumes
- Suggests Instagram customers have higher average order values, not just higher volume
- **Strategic Fix:** Increase Instagram marketing budget — it delivers the best revenue per customer acquired

---

### Insight 3 — High Cancellation & Return Rate

**Finding:** Cancelled (20.8%) + Returned (20.6%) = 41.4% of all orders never completed successfully.

**Why it matters:**
- Only 19.2% of orders are Delivered — meaning less than 1 in 5 orders reaches the customer
- Every cancelled/returned order has hidden costs: logistics, restocking, customer service
- **Strategic Fix:** Investigate root causes of cancellation — payment failures, stock issues, or delivery problems

---

### Insight 4 — Laptop Has Highest Average Order Value

**Finding:** Laptop AOV = $1,111 vs Phone AOV = $973 — a $138 gap per order.

**Why it matters:**
- Laptops generate more revenue per transaction despite not being the top product by volume
- Phone has the lowest AOV and lowest total revenue — suggesting low-margin, high-competition positioning
- **Strategic Fix:** Cross-sell laptop accessories (bags, mice, keyboards) to maximise revenue per laptop order

---

## Project Structure

```
📁 DecodeLab_P1/
│
├── 📁 charts/
│   ├── 📊 01_monthly_revenue_trend.png
│   ├── 📊 02_revenue_by_product.png
│   ├── 📊 03_order_status_breakdown.png
│   ├── 📊 04_payment_method_distribution.png
│   ├── 📊 05_revenue_by_referral_source.png
│   └── 📊 06_avg_order_value_by_product.png
│
├── 🐍 clean_data.py                     # Main cleaning & insight pipeline
├── 📄 Change_Log.pdf                    # Accountability record — every change documented
├── 📄 Data_Quality_Report.pdf           # Before/after quality proof with visuals
├── 📊 Cleaned_Dataset.xlsx              # Production-ready cleaned dataset
├── 📊 Cleaned_Dataset.csv              # Same dataset in CSV format
├── 📊 Dataset_for_Data_Analytics.xlsx   # Original raw dataset
└── 📄 README.md                         # You are here
```

---

## How to Run

### Prerequisites

- Python 3.10 or above
- The raw dataset file in the same folder as the script

### Install Dependencies

```bash
pip install pandas openpyxl matplotlib
```

### Run the Pipeline

```bash
python clean_data.py
```

### What Happens When You Run It

```
LOADED: 1200 rows × 14 columns
DUPLICATE ROWS REMOVED: 0
DUPLICATE ORDER IDs REMOVED: 0 — VERIFICATION GATE 1 PASSED
COUPONCODE MISSING VALUES IMPUTED: 309 records preserved
DATE FORMAT STANDARDISED — VERIFICATION GATE 2 PASSED
TEXT COLUMNS STANDARDISED TO TITLE CASE
IDENTIFIER COLUMNS STANDARDISED TO UPPER CASE
NUMERIC PRECISION ENFORCED
TOTALPRICE VALIDATION COMPLETE — MISMATCHES CORRECTED: 0

========== VERIFICATION GATE RESULTS ==========
DUPLICATE ORDER IDs REMAINING : 0  (TARGET = 0)
INVALID DATES REMAINING       : 0  (TARGET = 0)
VERIFICATION GATE PASSED      : True
ROWS IN → ROWS OUT            : 1200 → 1200 (ZERO DATA LOSS)
================================================

PIPELINE COMPLETE ✓
```

### Output Files Generated

| File | Description |
|------|-------------|
| `Cleaned_Dataset.xlsx` | Production-ready Excel file |
| `Cleaned_Dataset.csv` | Same data in CSV format |
| `charts/01_*.png` to `charts/06_*.png` | 6 insight charts |

---

<div align="center">

**Built with precision for DecodeLabs Industrial Training — Batch 2026**

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,14,30&height=100&section=footer" width="100%"/>

</div>
