# SQL Data Analysis & Exploration Assessment

## Project Overview
This project demonstrates proficiency in SQL querying, relational database management, and data visualization using Python (Pandas, Matplotlib, Seaborn). The assessment is divided into two main parts:
1. **Guided SQL Queries:** Analyzing a wholesale miniature model company's database to address specific business inquiries regarding customer segmentation, product performance, and remote work logistics.
2. **Exploratory Data Analysis:** Conducting an open-ended investigation into an Internet Movie Database (IMDb) dataset (2010–2019) to formulate business questions and assess data cleaning requirements.

## Part 1: Guided SQL Queries & Reflections

This section utilizes the `data.sqlite` database to extract insights for various departments. 

### Key Visualizations Produced
* **Customer Credit Limits:** Bar chart displaying the average credit limit of US-based customers grouped by state.
* **Top Customers:** Horizontal bar chart identifying the top 10 customers based on lifetime total payments.
* **Product Analysis:** Scatter plot comparing the total number of unique products in a product line against the total quantity ordered to evaluate inventory mix.

### Reflection Questions & Answers

**Reflection 1: Describing the `WHERE` clause for the International Collectable Campaign (Step 3)**
> The `WHERE` clause filters the dataset using two specific conditions linked by the `AND` operator, meaning both must be true for a customer to be selected. First, the operator `country != 'USA'` safely excludes any domestic customers. Second, the conditional expression `customerName LIKE '%Collect%'` uses wildcard characters (`%`) to scan the entire customer name string, isolating only the businesses that contain the exact word "Collect" anywhere within their name.

**Reflection 2: Visual Choice for Product Analysis (Step 7)**
> A scatter plot was selected because it is the most effective visualization for analyzing the correlation between two independent numeric variables—in this case, the number of unique products in a line versus the total quantity ordered. By plotting each product line on these two axes, the visual immediately and intuitively conveys to stakeholders whether a higher variety of products linearly translates into higher overall sales volume, or if certain product lines are outlier over-performers.

**Reflection 3: Subquery Design for Remote Offices (Step 8)**
> The subquery `(SELECT officeCode FROM employees GROUP BY officeCode HAVING COUNT(employeeNumber) < 5)` is executed first to isolate the specific list of office codes that qualify as "small" (under 5 employees). The main query then extracts the detailed employee and supervisor names, utilizing the `WHERE ... IN` clause to filter the final dataset exclusively to the targeted office codes returned by the subquery.

## Part 2: IMDb Exploratory Analysis

This section utilizes the `im.db` database (extracted from `im.db.zip`) to perform open-ended EDA on the film industry.

### 1. Initial Data Exploration Findings
* The database contains movies released from 2010 to 2019, but multiple text fields (like genres) are compressed into single, comma-separated strings.
* There is high variance in review volume; many niche titles possess high average ratings but extremely low vote counts (`numvotes`), which heavily skews perceived popularity.
* Documentaries and specific blended genres (e.g., Biography/Documentary) consistently yield the highest average ratings when filtering for sample sizes over 50 movies.

### 2. Business Question for Further Analysis
* **Question:** *Which specific genres and optimal runtimes yielded the highest average viewer ratings and largest audience engagement (numvotes) between 2010 and 2019?*
* **Relevance:** Answering this identifies safe, high-engagement content targets for a new indie studio or streaming platform looking to acquire or produce distribution rights for highly-rated modern catalogs.

### 3. Data Cleaning Tasks Identified
* **Null Handling:** `movie_ratings` often lacks entries for less popular movies found in `movie_basics`. Analysis requires `INNER JOIN` operations to drop unrated null records.
* **String Standardization:** The `genres` column in `movie_basics` contains comma-separated values (e.g., "Action,Adventure,Sci-Fi"). A cleaning task is required to split/explode this string to analyze single genres independently.
* **Data Type Integrity:** Filtering out invalid release years (`start_year > 2019` or `NULL`) is necessary. Runtime values must be validated and converted to numeric integers, as extreme outliers (0 minutes or 500+ minutes) exist in the raw data.

## Repository Structure
* `sql_assessment.ipynb`: The primary Jupyter Notebook containing all SQL queries, Pandas dataframe manipulations, and visualization code for Parts 1 and 2.
* `data.sqlite`: Wholesale company database for Part 1.
* `im.db.zip` / `im.db`: Compressed and extracted IMDb database for Part 2.
* `presentation.pdf`: The 3-5 slide presentation detailing the IMDb exploratory analysis.

## Execution Instructions
1. Ensure `im.db.zip` is located in the root repository folder alongside the `.ipynb` notebook.
2. Run the notebook sequentially. The built-in `zipfile` module will automatically extract `im.db`.
3. Required Python libraries: `sqlite3`, `pandas`, `matplotlib`, `seaborn`, `zipfile`.