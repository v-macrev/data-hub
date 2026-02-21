# Data Hub - A repo focused on the Databricks Enviroment

A modular analytics and machine learning platform built on Databricks, designed to host scalable data pipelines, forecasting systems, and production-grade time-series workflows.

This repository serves as a centralized **Data Hub** for structured, reproducible, and extensible data projects.

The first implemented pipeline focuses on **forecasting reconciliation**, but the architecture is intentionally designed to expand into multiple machine learning and time-series domains.

---

## Purpose

The Data Hub aims to provide:

* Structured machine learning pipelines
* Time-series forecasting frameworks
* Model validation and selection systems
* Macro–micro reconciliation logic
* Parameterized notebook workflows
* Production-ready Databricks Job orchestration
* Strong input validation and safe SQL handling

---

## Architecture Philosophy

The Data Hub follows a modular and production-oriented design:

* Fully parameterized workflows (via `dbutils.widgets`)
* Safe SQL generation and identifier validation
* Reproducible forecasting pipelines
* Clear separation of concerns (micro / macro / reconciliation)
* Databricks Asset Bundle orchestration
* Designed for future ML expansion
* Explicit validation windows and backtesting logic

Each project under `src/` represents a self-contained data workflow.

---

## Current Projects

### 1️ Forecast Reconciliation Pipeline

A full macro–micro forecasting system including:

* Micro-level baseline forecasting (Linear Regression)
* Macro-level multi-model evaluation
* Cross-validation and recent holdout validation
* MAPE-based winner selection
* Allocation reconciliation using:

  * Reliability caps (launch vs mature)
  * Bayesian smoothing priors
  * Beta constraints
  * Optional sqrt-weight reliability scaling
* Delta Lake outputs
* Databricks Job orchestration

Execution flow:

```
Micro → Macro → Reconciliation
```

---

## Planned Expansions

The Data Hub is structured to support future pipelines such as:

* Advanced ML forecasting models (Boosting, Ensemble, Hybrid)
* Feature-engineered regression pipelines
* Hierarchical time-series modeling
* Demand sensing pipelines
* Classification / anomaly detection systems
* Model monitoring workflows
* Automated retraining jobs
* MLOps-oriented experiment tracking

---

## Technology Stack

* Databricks
* PySpark
* Delta Lake
* Pandas / NumPy
* Time-series & ML libraries
* Databricks Jobs (Asset Bundles)
* Widget-driven configuration
* YAML-based workflow orchestration

---

## Repository Structure

```
.
├── src/
│   └── forecast-reconciliation/
│       ├── 01-linear-regression-products
│       ├── 02-best-models-categories
│       └── 03-macro-micro-union
│
├── resources/
│   └── job_forecast_reconciliation.yml
│
├── .github/
│   └── pull_request_template.md
│
└── README.md
```

---

## Running Workflows

### Option 1 — Manual Execution

Run notebooks sequentially:

1. `01-linear-regression-products`
2. `02-best-models-categories`
3. `03-macro-micro-union`

### Option 2 — Databricks Job (Recommended)

Defined in:

```
resources/job_forecast_reconciliation.yml
```

Workflow tasks:

* `micro_forecast_linear_regression`
* `macro_forecast_best_model`
* `macro-micro-reconciliation`

Queueing enabled
Performance target: `PERFORMANCE_OPTIMIZED`

---

## Configuration

All notebooks are fully widget-driven and support job-level overrides.

Example:

```python
dbutils.widgets.text("ORIGIN_TABLE", "samples.bakehouse.sales_transactions")
dbutils.widgets.text("RANGE_PREDICTION", "5")
```

Supported configuration categories:

* Source tables & columns
* Key composition & delimiters
* Forecast horizons
* Validation windows
* Cross-validation folds
* Reliability caps & smoothing controls
* Allocation constraints

---

## Production Safety

The platform includes:

* Regex-based identifier validation
* Safe SQL literal construction
* Typed parameter parsing (int, float, bool, JSON)
* Input integrity checks
* Allocation constraint validation
* Explicit window definitions for backtesting

---

## Output Tables (Current Implementation)

* `workspace.forecasting.linear_regression_forecast`
* `workspace.forecasting.macro_forecast`
* `workspace.forecasting.bakehouse_forecasting`

---

## Design Goals

* Reproducibility
* Safety in dynamic SQL
* Modular scalability
* Clear governance
* Structured review workflows
* Production-readiness
* Expandability toward ML platform architecture

---

## License

AGPL-3.0

---

## Maintainer

Victor Rodrigues<br>
Sr. Data Analytics Engineer