# TechCore Sales Analytics | Power BI & Data Modeling

End-to-end **Data Analytics** project for TechCore, a fictional technology retail chain operating across several Colombian cities. The project covers data cleaning, relational modeling, business intelligence, dashboard development, and row-level security.

## Project objective

Transform raw sales data into a reliable analytical model and an interactive Power BI dashboard that supports business decision-making.

The workflow combines **Power Query, Python, pandas, relational data modeling, DAX, Power BI, and Row-Level Security (RLS)**.

## Workflow

### 1. Data cleaning and transformation - Power Query

The original dataset contained **30,307 rows**. Cleaning and transformation included:

- Column standardization and data-type correction.
- Normalization of city and brand names.
- Treatment of null values for optional products.
- Removal of **307 exact duplicate rows**.

The resulting clean dataset contains **30,000 sales records**.

### 2. Relational model - Python & pandas

The cleaned data was transformed into seven related entities:

- Cities
- Branches
- Salespeople
- Customers
- Products
- Invoices
- Invoice details

The notebook converts the original wide product structure into a long-format invoice-detail table and validates referential integrity across all relationships.

Additional quality checks identified and corrected:

- A `Razer` / `Razor` brand inconsistency.
- Inflated unit prices for transactions with quantities of 10 or 20.
- An original sales-total field that did not reconcile with invoice detail. A validated `TotalVentaCalculado` field was therefore used for the analysis.

### 3. Power BI dashboard

The final dashboard includes:

- Total Sales
- Average Ticket
- Invoice Count
- Products Sold
- Sales by city
- Sales by brand
- Sales evolution over time
- Payment-method distribution
- Product analysis
- Interactive filters by city, branch, brand, and date

The model also includes a date dimension and DAX measures for the main KPIs.

### 4. Row-Level Security (RLS)

A hierarchical RLS model was designed with three access levels:

- National Manager - full access
- Regional Manager - city-level access
- Branch Manager - branch-level access

Dynamic filters use `USERPRINCIPALNAME()` and `LOOKUPVALUE()` to apply access rules according to the simulated user table.

## Main business findings

- Total sales: **$2.57 trillion** in the dataset's currency.
- Average ticket: **$85.74 million**.
- **30,000 invoices** and **495,597 products sold**.
- Lenovo was the leading brand by sales, followed by HP and Dell.
- Medellin generated the highest sales among the analyzed cities.
- Credit card represented **40.04%** of sales revenue by payment method.
- Annual sales remained relatively stable from 2015 to 2024; 2025 is incomplete and should not be interpreted as a full-year decline.

> The dataset does not include product costs, so the analysis covers gross sales revenue rather than profitability.

## Repository structure

```text
techcore-sales-analytics-powerbi/
|-- README.md
|-- requirements.txt
|-- data/
|   |-- ventas_raw.csv
|   |-- ventas_transformed.csv
|   `-- modelo_ventas.xlsx
|-- notebooks/
|   `-- relational_data_model.ipynb
|-- powerbi/
|   |-- 01_data_cleaning_power_query.pbix
|   `-- 02_sales_dashboard.pbix
`-- docs/
    |-- project_documentation.pdf
    `-- business_insights_recommendations.pdf
```

## Technologies

**Power BI · Power Query · DAX · Python · pandas · NumPy · Excel · Data Cleaning · Relational Data Modeling · Data Visualization · RLS · Business Analytics**

## How to explore the project

1. Review `notebooks/relational_data_model.ipynb` to see the relational-model construction and data-quality validation.
2. Open `powerbi/02_sales_dashboard.pbix` with Power BI Desktop to explore the interactive dashboard.
3. Read `docs/business_insights_recommendations.pdf` for the business findings and recommendations.

If Power BI requests a new source location when refreshing the PBIX file, point it to the corresponding files in the repository's `data/` folder.

## Context

Developed as the **Module 3 Integrative Project** of the Data Science program at Henry (2026).
