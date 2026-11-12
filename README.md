# Blinkit Grocery Sales Analysis Dashboard

An interactive Power BI dashboard exploring grocery sales performance
across product categories, outlet formats, outlet sizes, and location
tiers.

![Blinkit Sales Analysis
Dashboard](images/Blinkit_Dashboard_Screenshot.png)

## Project Overview

The objective of this project was to transform the BlinkIT Grocery Data
dataset into an interactive dashboard that makes it easier to explore
sales performance and product mix. The report combines high-level KPIs
with category and outlet-level visual analysis.

## Business Questions

-   What is the overall sales value and average sales per record?
-   Which item categories contribute the most to sales?
-   How does sales contribution differ by item fat content?
-   Which outlet sizes, location tiers, and outlet types contribute
    most?
-   How do sales values vary by outlet establishment year?
-   What is the average rating in the dataset?

## Dataset

-   **Source:** [BlinkIT Grocery Dataset ---
    Kaggle](https://www.kaggle.com/datasets/arunkumaroraon/blinkit-grocery-dataset)
-   **Format:** CSV
-   **Records:** 8,523
-   **Columns:** 12

The dataset contains item attributes, outlet attributes, sales,
visibility, weight, and rating information. It is used here as a
portfolio/practice dataset and should not be interpreted as a live
operational feed from Blinkit.

## Tools and Technologies

-   Microsoft Power BI Desktop
-   Power Query --- data cleaning and transformation
-   DAX --- measures and KPI calculations
-   GitHub --- project documentation and versioned portfolio
    presentation

## Data Cleaning and Preparation

The following steps were completed in Power Query:

1.  Standardized inconsistent `Item Fat Content` labels:
    -   `LF` and `low fat` → `Low Fat`
    -   `reg` → `Regular`
2.  Addressed missing `Item Weight` values using an `Item Identifier`
    lookup:
    -   Created a lookup query.
    -   Removed null and duplicate lookup keys.
    -   Merged the lookup into the main table.
    -   Used the original weight when present and the recovered weight
        when the original was missing.
3.  Retained 374 unresolved item-weight values as blank rather than
    inserting unsupported estimates.
4.  Retained 526 zero values in `Item Visibility`; zero was not
    automatically treated as an error.
5.  Preserved all 8,523 source records; no rows were removed.

## DAX Measures

The loaded model table is named `Blinkit_Sales`.

``` dax
TOTAL SALES =
SUM(Blinkit_Sales[Sales])
```

``` dax
Average Sales =
AVERAGE(Blinkit_Sales[Sales])
```

``` dax
Item Count =
COUNTROWS(Blinkit_Sales)
```

``` dax
Average Rating =
AVERAGE(Blinkit_Sales[Rating])
```

**Metric note:** The `Item Count` measure above counts rows/records, not
distinct product identifiers. The dashboard displays 8,523 for this
measure.

## Dashboard Features

### KPI Cards

-   Total Sales: approximately **1.20M**
-   Average Sales: **140.99**
-   Item Count / Records: **8,523**
-   Average Rating: **3.92**

### Interactive Slicers

-   Outlet Location Type
-   Outlet Size
-   Outlet Type
-   Item Type

### Visualizations

1.  Sales by Fat Content --- donut chart
2.  Sales by Item Type --- Top 5 horizontal bar chart
3.  Sales by Outlet Size --- donut chart
4.  Sales by Outlet Establishment Year --- line/area chart
5.  Sales by Outlet Location Type --- column chart
6.  Sales by Outlet Type --- horizontal bar chart

The slicers were tested to confirm that the KPI cards and charts respond
to filter selections and return to the overall view when selections are
cleared.

## Key Insights

-   Low Fat items account for approximately **64.6%** of sales (about
    **776.32K**); Regular items account for approximately **35.4%**
    (about **425.36K**).
-   Fruits & Vegetables and Snack Foods are the leading item categories,
    each contributing about **0.18M** in sales.
-   Medium outlets contribute approximately **42.27%** of sales, Small
    outlets **37.01%**, and High outlets **20.72%**.
-   Tier 3 outlets record the highest sales among location tiers, at
    approximately **0.47M**.
-   Supermarket Type 1 contributes the largest sales value,
    approximately **0.79M**.
-   The outlet establishment-year chart has a visible peak around
    **2018**.
-   The average rating is **3.92 out of 5**.

These are descriptive findings from this dataset. They do not establish
why customers behaved in a particular way or prove a causal
relationship.

## Business Recommendations

-   Review demand and stock availability for Low Fat products and
    leading item categories across outlet segments.
-   Compare performance across outlet sizes and location tiers before
    making inventory or expansion decisions.
-   Use Supermarket Type 1 as a benchmark for deeper analysis of
    outlet-format performance.
-   Examine ratings by item category and outlet type to identify
    possible customer-experience improvement areas.
-   Combine establishment-year sales with outlet counts and comparable
    operating-period information before drawing conclusions about outlet
    maturity.

## Limitations

-   The dataset does not include costs or margins; therefore, this
    project analyzes **sales, not profit**.
-   The data does not provide a verified order-date time series.
-   Sales grouped by outlet establishment year do not, by themselves,
    represent sales changing over calendar time.
-   Some item-weight values remain missing after lookup-based recovery.
-   Findings describe this dataset and may not represent Blinkit's
    current business performance.

## Repository Structure

``` text
Blinkit-Grocery-Sales-Analysis/
├── README.md
├── Blinkit_Grocery_Sales_Analysis.pbix
└── images/
    └── Blinkit_Dashboard_Screenshot.png
```

You may also add the PDF project report to the repository if its file
size and the repository's sharing/licensing requirements permit.

## How to Use

1.  Download or clone this repository.
2.  Open the `.pbix` file in Power BI Desktop.
3.  Use the slicers on the left to filter the report.
4.  Explore the KPI cards and six charts to compare sales across
    products and outlets.

## Author

**Aditya Dahibhate**

*Power BI \| Data Analytics \| Business Analytics*

------------------------------------------------------------------------

*This project was created for learning and portfolio demonstration using
a publicly available Kaggle dataset.*
