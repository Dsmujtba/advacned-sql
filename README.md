# Advanced SQL for DVD Rental Analytics: Extracting Business Insights

In this project, I applied a comprehensive suite of advanced SQL techniques to dissect the Sakila sample database (representing a DVD rental business called "Rentio"). My primary objective was to move beyond basic queries and leverage sophisticated SQL capabilities to answer practical business questions, thereby demonstrating proficiency in data manipulation, complex querying, and analytical problem-solving crucial for Data Analyst, Data Engineer, and Business Intelligence roles.

![Database Schema ERD](./images/star_schema_erd.png)

## Key Skills Applied & Achievements:

Through this project, I demonstrated mastery and practical application of advanced SQL features, including:

* **Complex Data Retrieval & Joins:** Expertly navigated a star schema, utilizing various `JOIN` types (primarily `INNER JOIN`) to synthesize information from multiple tables (e.g., `fact_rental`, `dim_film`, `dim_customer`).
* **Query Structuring & Readability:**
    * Employed **Common Table Expressions (CTEs)** extensively to break down complex problems into logical, readable, and maintainable steps.
    * Utilized **Subqueries** (scalar, row, and table) for multi-layered calculations and dynamic filtering.
* **Powerful Analytical Calculations with Window Functions:**
    * **Ranking & Ordering:** Applied `RANK()`, `DENSE_RANK()`, and `ROW_NUMBER()` to determine top N records within partitions (e.g., top-rented films per category, most active customers).
    * **Period-over-Period Analysis:** Leveraged `LAG()` and `LEAD()` to analyze trends, such as comparing month-over-month rental counts or revenue.
    * **Running Totals & Moving Averages:** Used aggregate window functions like `SUM() OVER(...)` and `AVG() OVER(...)` for cumulative calculations without collapsing rows.
* **Conditional Logic & Data Transformation:**
    * Implemented **`CASE` statements** for dynamic data categorization (e.g., customer segmentation based on rental frequency) and conditional aggregations.
    * Performed **data pivoting** using `CASE` within aggregate functions to transform row-level data into a columnar summary format.
* **Advanced Aggregation & Grouping:** Skillfully used aggregate functions (`SUM()`, `COUNT()`, `AVG()`, `MAX()`) with `GROUP BY` and `HAVING` clauses for insightful summarizations.
* **Date/Time & String Manipulation:**
    * Effectively used date/time functions (`EXTRACT`, `DATE_TRUNC`, `AGE`, date arithmetic) for time-based analysis and filtering.
    * Applied string functions (`CONCAT()`, `SUBSTRING()`, `LIKE`) for data cleaning and formatting.
* **Analytical Problem Solving:** Translated specific business questions into precise and efficient SQL queries, extracting actionable insights from the data.

## Dataset & Schema Overview:

The analysis was performed on a relational database modeled after the **Sakila Sample Database**, representing a fictional DVD rental company. This database predominantly follows a star schema, optimized for analytical queries. Key tables included:

* **Fact Table:** `fact_rental` (central transactional data)
* **Dimension Tables:** `dim_film`, `dim_customer`, `dim_store`, `dim_category`, `dim_actor`, `dim_staff`
* **Bridge Table:** `bridge_actor` (many-to-many relationship between films and actors)

## Approach: Solving Business Questions with SQL

The core of this project is captured within the **`Advanced SQL.ipynb`** Jupyter Notebook. My approach was to identify pertinent business questions relevant to a DVD rental operation and then craft advanced SQL queries to address them. Each query or set of queries in the notebook typically:

1.  Poses a **Business Question** (e.g., "Which film categories generate the most rental revenue?").
2.  Provides **Context** on its relevance.
3.  Details the **Advanced SQL Query** I developed, showcasing specific techniques.
4.  Presents the **Results/Insights** derived.

### Spotlight on Advanced Techniques (Examples):

While the notebook contains numerous examples, here's a glimpse into the types of problems I solved:

* **Identifying Top N Items per Group:** To find the top 3 most rented films within each film category, I utilized CTEs to first calculate rental counts per film and then applied the `RANK()` window function partitioned by category.
* **Month-over-Month Growth Analysis:** To understand growth trends, I calculated monthly rental revenue and then used the `LAG()` window function to compare each month's revenue with the previous month, deriving a growth percentage.
* **Customer Segmentation:** I employed `CASE` statements within aggregate queries to segment customers based on their rental frequency and monetary value (e.g., "High Value," "Medium Value," "Low Value").
* **Pivoting Data for Reporting:** For a summary report showing rental counts per film rating across different stores, I used `CASE` statements inside `SUM()` to pivot the data, transforming ratings into columns.

*(These are illustrative examples; the notebook provides the actual queries and detailed scenarios.)*

## Technologies & Tools Used:

* **Database:** MySQL (as per Sakila's origin, running on a local or cloud instance)
* **SQL Dialect:** MySQL SQL
* **Development Environment:** Jupyter Notebook / JupyterLab
* **Key Python Libraries:** `ipython-sql` (for embedding SQL in notebooks), `pymysql` (MySQL connector), `python-dotenv` (for environment management), `pandas` (for displaying results).
* **Version Control:** Git & GitHub

## Exploring the Analysis:

The detailed SQL queries, their explanations, and the resulting insights are available in the [Advanced SQL.ipynb](./Advanced%20SQL.ipynb) notebook within this repository. The setup instructions below guide you on how to replicate the environment if you wish to execute the queries yourself.

## Setup and Usage:

To run the analysis presented in the Jupyter Notebook:

1.  **Prerequisites:**
    * Python 3.x
    * Access to a MySQL database instance.
    * Jupyter Notebook or JupyterLab.
2.  **Database Setup:**
    * Load the Sakila sample database schema and data into your MySQL instance. (Ensure the database name matches your configuration, typically `sakila`).
3.  **Clone Repository & Navigate:**
    ```bash
    git clone <your-repository-url>
    cd <repository-directory-name>
    ```
4.  **Install Dependencies** (preferably in a virtual environment):
    ```bash
    pip install ipython-sql pymysql python-dotenv jupyterlab pandas # Add other specific dependencies if any
    ```
    *(Consider creating a `requirements.txt` file: `pip freeze > requirements.txt` and instructing `pip install -r requirements.txt`)*
5.  **Configure Environment Variables:**
    * Create a `.env` file in the project root. **Important:** Add `.env` to your `.gitignore`!
    * Populate `.env` with your MySQL connection details:
        ```
        DBHOST=your_database_host
        DBPORT=your_database_port
        DBNAME=sakila
        DBUSER=your_database_username
        DBPASSWORD=your_database_password
        ```
6.  **Run the Notebook:**
    * Start JupyterLab: `jupyter lab`
    * Open and execute the `Advanced SQL.ipynb` notebook.

---
