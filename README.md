**<h1>Coffee Sales Dashboard</h1>**

A sales dashboard for a coffee company built with PivotTables, PivotCharts, Slicers and a Timeline filter for interactive, self service reporting.

<hr>

**<h2>Demo</h2>**
*Open [Coffee_Sales_Dashboard.xlsx](Coffee_Sales_Dashboard.xlsx) in Excel, go to the DASHBOARD tab and interact with it*

https://github.com/user-attachments/assets/3045e59f-88be-4af4-922b-37a3bc797aeb

**<h3>What it does</h3>**
- Total Sales Over Time — a trend line broken out by coffee type (Arabica, Excelsa, Liberica, Robusta), filterable by a Timeline slicer
- Sales by Country — a bar chart comparing performance across the United States, United Kingdom and Ireland
- Top 5 Customers — a bar chart ranking customers by total sales

<hr>

**<h3>Process</h3>**

The workbook starts as three separate raw tables: orders, customers and products that don't share every field with each other. Before anything could be visualized, they needed to be joined into one clean, analysis ready table.

**1. Combining the tables**

- **XLOOKUP** pulls customer details (name, email, country) into the *orders* table by matching on Customer ID against the *customers* table.
- **INDEX/MATCH** pulls product details (coffee type, roast type, size, unit price) into *orders* by matching on Product ID against the *products* table. INDEX/MATCH was used here instead of XLOOKUP so the same formula could return any column from *products* just by changing which column header it matches against.
- **IFS** decodes shorthand codes into readable labels — e.g. turning **"Rob"** into **"Robusta"** for coffee type, and **"M"** into **"Medium"** for roast type.

**2. Calculating sales**

With unit price and quantity now sitting on the same row, **Sales = Unit Price × Quantity** is a straightforward multiplication per order line.

**3. Building the pivots**

Once **orders** was a fully self contained, joined table, PivotTables were built on top of it to aggregate sales by date, country and customer.

**4. Charting and dashboarding**

PivotCharts were built directly from those PivotTables, then arranged onto a single **DASHBOARD** sheet with a Slicer and Timeline layered on top for interactive filtering.

<hr>

**<h3>Key Insights</h3>**
- The US drives the business. Of $45.1K in total sales, the United States accounts for 79% (~$35.6K), with Ireland (15%) and the United Kingdom (6%) far behind.
- No single coffee type dominates. Arabica, Excelsa and Liberica each hold a similar 26-27% share of sales; Robusta trails a bit at 20%, suggesting a fairly balanced product mix rather than one hero product.
- Revenue is spread across customers, not concentrated. The top 5 customers each contribute a similar, modest share of total sales ($278-$317 each) — a healthy sign that the business isn't overly reliant on a handful of big accounts.

<hr>
  
**<h3>Skills Demonstrated</h3>**

Excel formulas **(XLOOKUP, INDEX/MATCH, IFS)**, PivotTables, PivotCharts, Slicers, Timeline filters.
