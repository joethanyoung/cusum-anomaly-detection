# CUSUM Anomaly Detection - Monthly Time Series

## Executive Summary

- Uses CUSUM control charts to detect unusual shifts in monthly time-series data.
- Converts tabular monthly data into a monitoring workflow that can flag units or periods for follow-up review.
- Applies normalization, baseline calculation, and statistical process control to make monitoring more systematic.
- Supports data quality review, operational monitoring, and exception-based reporting.

## Business Question

How can monthly operational metrics be monitored consistently so unusual shifts are identified early and review effort is focused on the units or periods that need attention?

## Data and Context

The original analysis uses monthly premium data across organizational units, but the method is transferable to other operational monitoring problems where the goal is to flag unusual changes over time.

Raw data is not included because the original source was private. The repository focuses on the monitoring logic and reproducible analytical workflow.

## What This Project Demonstrates

- Converting tabular monthly data into time-series form
- Normalizing values before comparing patterns across units
- Computing baseline mean and standard deviation for each series
- Applying CUSUM control charts to detect process shifts
- Extracting violations that exceed control limits
- Using statistical monitoring to prioritize follow-up review

## Method

| Step | Purpose |
|---|---|
| Data normalization | Put monthly series on a comparable scale |
| Time-series construction | Convert monthly columns into sequential observations |
| Baseline calculation | Estimate mean and standard deviation for each unit |
| CUSUM charting | Detect sustained shifts from the baseline process |
| Violation extraction | Identify units and periods that exceed control limits |

## Workflow

```text
Monthly tabular data
  -> Min-Max normalization
  -> matrix and time-series conversion
  -> baseline mean and standard deviation
  -> CUSUM control chart
  -> violation list for follow-up
```

## Key Findings

- CUSUM monitoring can turn many monthly series into a focused exception list for review.
- Normalization allows units with different scales to be compared through the same monitoring logic.
- A control-chart approach is more transparent for stakeholder review than ad-hoc visual inspection of many time series.

## Business Implication

The workflow supports exception-based reporting: instead of reviewing every unit manually, analysts can focus on units or periods that breach statistical control limits and then investigate business or data-quality explanations.

## Relevance

This project shows how statistical monitoring can support KPI review, operational reporting, data quality checks, and risk-oriented analytics.

## Current Repository Notes

- Raw Excel data is not included.
- The script expects a local Excel file path from the original analysis environment.
- The current code is a compact analysis script, not a packaged command-line tool.

To reproduce with a new dataset, update the `read_excel()` path and sheet name in `cusum_revised_v2.R`.

## How to Run

Install the required R packages:

```r
install.packages(c("qcc", "readxl"))
```

Then update the local data path and run:

```bash
Rscript cusum_revised_v2.R
```

## Next Improvements

- Replace the hardcoded Excel path with a configurable input parameter
- Save CUSUM violation results to `outputs/violations.csv`
- Add plots to an `outputs/figures/` folder
- Add a synthetic sample dataset for reproducible demonstration
- Wrap the CUSUM workflow into a reusable function

## Tech Stack

`R` · `qcc` · `readxl`
