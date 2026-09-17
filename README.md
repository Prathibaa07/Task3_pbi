# Power BI Sales Dashboard

## Project Overview

This project is a **Sales Dashboard created using Microsoft Power BI
Desktop**.\
The dashboard is designed to provide a simple and interactive view of
sales performance using KPIs, charts, and slicers.

## Tools and Technologies

-   **Microsoft Power BI Desktop**
-   **Power Query** for data preparation
-   **DAX** for calculated measures
-   **Data Modeling** for relationships
-   **Charts and Slicers** for visualization

## Dataset

The dashboard uses sales data containing fields such as:

-   Order Date
-   Region
-   Category
-   Sub-Category
-   Segment
-   Sales
-   Profit
-   Quantity
-   Customer information

The project also includes a separate **Date table** for time-based
analysis.

------------------------------------------------------------------------

# Steps to Create the Dashboard

## Step 1: Import the Dataset

1.  Open **Power BI Desktop**.
2.  Select **Home → Get Data**.
3.  Choose the required data source, such as Excel or CSV.
4.  Select the sales dataset.
5.  Click **Load**.

------------------------------------------------------------------------

## Step 2: Check the Data

Open **Data View** and verify that the required columns are available.

Important fields include:

-   Sales
-   Profit
-   Quantity
-   Order Date
-   Region
-   Category
-   Sub-Category
-   Segment

Make sure numeric columns have the correct data type.

------------------------------------------------------------------------

## Step 3: Create a Date Table

Create a separate Date table using DAX:

``` dax
Date =
CALENDAR(
    MIN(shopify_stock[date]),
    MAX(shopify_stock[date])
)
```

Add useful date columns:

``` dax
Year = YEAR('Date'[Date])
```

``` dax
Month = MONTH('Date'[Date])
```

``` dax
MonthName = FORMAT('Date'[Date], "MMMM")
```

``` dax
Day of week = FORMAT('Date'[Date], "dddd")
```

------------------------------------------------------------------------

## Step 4: Create the Relationship

Go to **Model View**.

Create a relationship between:

``` text
Date[Date]
      ↓
shopify_stock[date]
```

The Date table is used for time-based calculations such as Last Year and
YTD.

------------------------------------------------------------------------

# Step 5: Create Measures

Create a separate **Measure** table if required.

## Average Close

``` dax
Avg Close =
AVERAGE(shopify_stock[close])
```

This calculates the average closing value.

## Close Last Year

``` dax
Close LY =
CALCULATE(
    AVERAGE(shopify_stock[close]),
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

This calculates the average Close value for the previous year.

## Close YTD

``` dax
Close YTD =
TOTALYTD(
    AVERAGE(shopify_stock[close]),
    'Date'[Date]
)
```

This calculates the year-to-date average Close value.

------------------------------------------------------------------------

# Step 6: Create KPI Cards

Add Card visuals to display important metrics.

Recommended KPI cards:

1.  Total Sales
2.  Total Profit
3.  Total Orders
4.  Total Quantity

Arrange the cards horizontally at the top of the dashboard.

Example layout:

``` text
┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ Total Sales │ │Total Profit │ │Total Orders │ │Total Quantity│
└─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
```

------------------------------------------------------------------------

# Step 7: Create Sales by Region

1.  Select a **Clustered Bar Chart**.
2.  Add **Region** to the Y-axis.
3.  Add **Total Sales** to the X-axis/Values.
4.  Open **Format visual → General → Title**.
5.  Change the title to:

**Sales by Region**

This chart compares sales across different regions.

------------------------------------------------------------------------

# Step 8: Create Sales by Segment

1.  Select a **Donut Chart**.
2.  Add **Segment** to the Legend.
3.  Add **Total Sales** to Values.
4.  Change the title to:

**Sales by Segment**

This shows the contribution of each customer segment to total sales.

------------------------------------------------------------------------

# Step 9: Create Sales by Category

1.  Select a **Clustered Column Chart**.
2.  Add **Category** to the X-axis.
3.  Add **Total Sales** to the Y-axis/Values.
4.  Change the title to:

**Sales by Category**

The chart should show separate columns for the available categories.

------------------------------------------------------------------------

# Step 10: Add Slicers

Add slicers to make the dashboard interactive.

Recommended slicers:

-   Year
-   Region
-   Category
-   Sub-Category

For example:

``` text
Year
[ 2014 ───────── 2017 ]

Region
☐ Central
☐ East
☐ South
☐ West

Category
☐ Furniture
☐ Office Supplies
☐ Technology
```

Selecting a slicer value filters the dashboard visuals.

------------------------------------------------------------------------

# Step 11: Format the Dashboard

To create a clean dashboard:

1.  Select an empty area of the report page.
2.  Open **Format**.
3.  Set the page size to **16:9**.
4.  Use **View → Page view → Fit to page**.
5.  Give all KPI cards the same size.
6.  Align charts evenly.
7.  Keep consistent spacing between visuals.
8.  Use a clear dashboard title.

Recommended title:

**Sales Dashboard**

------------------------------------------------------------------------

# Step 12: Arrange the Dashboard

A simple final layout can be:

``` text
┌──────────────────────────────────────────────────────────────┐
│                         SALES DASHBOARD                      │
├──────────────┬──────────────┬──────────────┬────────────────┤
│ Total Sales  │ Total Profit │ Total Orders │ Total Quantity │
├──────────────┴──────────────┴──────────────┴────────────────┤
│                                                              │
│ Sales by Region                 Sales by Segment             │
│ ┌──────────────────────┐       ┌─────────────────────────┐  │
│ │      Bar Chart       │       │       Donut Chart        │  │
│ └──────────────────────┘       └─────────────────────────┘  │
│                                                              │
│ Sales by Category                 Filters                    │
│ ┌──────────────────────┐       ┌─────────────────────────┐  │
│ │    Column Chart      │       │ Year / Region / Category │  │
│ └──────────────────────┘       │ / Sub-Category           │  │
│                                └─────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

------------------------------------------------------------------------

# Step 13: Test Interactivity

After creating the dashboard:

1.  Select a **Year** from the Year slicer.
2.  Check whether the KPI cards change.
3.  Select a Region.
4.  Check whether the charts update.
5.  Select a Category.
6.  Verify that the other visuals respond to the selection.

This confirms that the report is interactive.

------------------------------------------------------------------------

# Step 14: Save the Power BI File

1.  Go to **File → Save As**.
2.  Give the file a meaningful name, for example:

``` text
Sales_Dashboard.pbix
```

3.  Save the file.

------------------------------------------------------------------------

## Dashboard Features

The completed dashboard contains:

-   Sales KPI
-   Profit KPI
-   Orders KPI
-   Quantity KPI
-   Sales by Region
-   Sales by Segment
-   Sales by Category
-   Year filter
-   Region filter
-   Category filter
-   Sub-Category filter
-   Date-based DAX calculations
-   Interactive visual filtering
-   16:9 dashboard layout

## DAX Measures Used

``` dax
Avg Close =
AVERAGE(shopify_stock[close])
```

``` dax
Close LY =
CALCULATE(
    AVERAGE(shopify_stock[close]),
    SAMEPERIODLASTYEAR('Date'[Date])
)
```

``` dax
Close YTD =
TOTALYTD(
    AVERAGE(shopify_stock[close]),
    'Date'[Date]
)
```

## Conclusion

The Power BI Sales Dashboard provides an interactive way to analyze
sales performance by region, segment, and category. KPI cards give a
quick overview of important business metrics, while slicers allow users
to filter the report dynamically. The Date table and DAX measures
support time-based analysis such as Last Year and Year-to-Date values.

## Project Structure

``` text
Sales Dashboard/
│
├── Sales_Dashboard.pbix
├── README.md
└── Dataset/
    └── sales_data.csv
```
