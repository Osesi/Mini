# Data Exploration & Analysis

## Project Overview

This project contains an Exploratory Data Analysis (EDA) of the **Classic Models** database, a commercial dataset representing a company that sells miniature scale models (classic cars, vintage cars, motorcycles, planes, ships, and trains).

The goal of this analysis is to evaluate database integrity, uncover initial commercial trends, formulate a strategic business question for further investigation, and identify necessary data cleaning tasks.

## Key Deliverables

This project satisfies the following core deliverables:

1. **Initial Data Exploration Findings:** Highlights key commercial trends, customer segmentation by credit limit, product performance metrics, and fulfillment status patterns.

2. **Strategic Business Question:** Identifies a data-driven question regarding order fulfillment gaps (cancellations/delays) and their impact on revenue realization across different geographic regions and product lines, supported by data visualizations.

3. **Data Cleaning Tasks:** Outlines necessary SQL/Python preprocessing steps, including handling `NULL` values (e.g., customer states, order comments), standardizing geographical text strings, and normalizing date formats.

## Repository Contents

* **`Jupyter_Notebook.ipynb`**: The primary execution notebook containing SQL queries, data analysis logic, and chart generation steps.

* **`data.sqlite`**: The SQLite database containing all relational tables (`customers`, `orders`, `products`, `orderdetails`, etc.).

* **Visualizations (`.png`)**: Data charts generated during the EDA process to support the presentation slides.

* **Slide Presentation**: The 3–5 slide presentation highlighting the three primary deliverables.

## Getting Started & Execution

1. Clone or download this repository to your local machine.
2. Ensure the `data.sqlite` file is placed in the same working directory as `Jupyter_Notebook.ipynb`.
3. Open the notebook in your preferred environment (Jupyter Notebook, VS Code, or JupyterLab).
4. Run the notebook cells sequentially to execute the SQL queries and generate the analytical charts.

## Technologies Used

* **SQL (SQLite3):** Relational database querying and data extraction.
* **Python (Pandas):** Data cleaning, manipulation, and aggregation.
* **Matplotlib / Seaborn:** Data visual rendering.