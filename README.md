# Apple & Peach Sales Dashboard

### Dashboard Link : https://drive.google.com/file/d/15Jye4HyaLBzqlLJX0qxGHJYRPG-wA4q0/view?usp=sharing

## Problem Statement

This dashboard helps Apple & Peach Global better understand their sales performance from 2021 to 2023. It enables Apple & Peach Global to assess whether they are meeting their sales targets. By analyzing their sales data, they can identify areas needing improvement and recognize unique clients. The dashboard also provides insights into total sales, total profit, total cost, and unique clients. Having identified these issues using the dashboard, they can focus on factors affecting their weekly, monthly, and quarterly sales targets. Sunday has the lowest sales for the year. There were no sales on Tuesday and Wednesday, which affected their ability to achieve the sales target.

Given that they are 32.31% away from achieving their sales target, they can work on increasing their unique customers (currently 89) and improving their weekly sales.

### Steps followed

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.

- Step 2: Cleaned the data using the Power Query Editor. Renamed the column names, adjusted the date formats, and set the appropriate data types for each column before creating the report.

- Step 3:
  For data modeling, I joined three tables together—ordertb, employeetb, and datetb—using their respective IDs, utilizing the single-to-many relationship provided by Power BI.

- Step 4:
  Since the data profile was limited to only 1,000 rows, column profiling based on the entire dataset was selected to ensure accuracy.

- Step 5:
  It was observed that no errors or empty values were present in any of the columns except for the CustomersName and CustomerCompany columns.

- Step 6:
  In the report view, I created the canvas using PowerPoint to improve the performance and loading time.

- Step 7:
  Since the data contained various KPIs, a new visual was imported from Google Fonts, which provided images to identify each KPI.

- Step 8:
  Visual filters were added for the years 2021, 2022, and 2023. Additionally, filters were applied for different categories.

- Step 9:
  Three cards were added to the canvas, representing total profit, total cost, total sales, and unique clients.

- Step 10:
  A line chart was added to the report to represent total sales by quarter. It included a drill mode that allows drilling up and down by month, quarter, and year.

- Step 11:
  A line and clustered column chart was added, representing total sales, total cost, and total profit by month.

- Step 12:
  A stacked column chart was added to the report dashboard to classify customers into different groups: top customers (top 10), least customers, and average customers.

- Step 13:
  A clustered column chart was added, representing different sales made for each day.

- Step 14:
  A donut chart was added to the report dashboard to track the sales target for the year. It displays total sales and areas for improvement.

- Step 15:
  In the report view, under the Insert tab, a rectangle shape was inserted using the Shape option from the Elements group. Similarly, the company logo was added to the report design area using the Image option.

- Step 16 Sales Target was created using a DAX formula, which helps us determine our performance metric.

        %target sales = VAR targetdiff = [Total Sales] - [Target] RETURN DIVIDE(targetdiff , [Target])

This shows that we were 32.31% short of achieving our sales target for the year, out of a total target of 100%.

![sales_target](https://github.com/user-attachments/assets/764f3b5c-93c9-4ce4-bbba-091e89ec7c1c)
     

- Step 17 : New measure was created to classify the customers.

The following DAX expression was written for this:

          Classify Customers = CALCULATE([TotalSales],FILTER(VALUES(Ordertbl[CustomerCompany]),
                              COUNTROWS(FILTER(Customer_Classification,RANKX(ALL(Ordertbl[CustomerCompany]),
                              [Total Sales],,DESC) >= Customer_Classification[Min] && RANKX
                              (ALL(Ordertbl[CustomerCompany]),
                              [Total Sales],,DESC) <= Customer_Classification[Max])) >0 ))

- Step 18 : New measure was created to find total profit .

The following DAX expression was written for this:

        Total Profit = [Total Sales] - [Total Cost]

A card visual was used to represent this total Profit.

![total_profit](https://github.com/user-attachments/assets/15e83b7d-c959-457c-848e-0a2deb89c5e1)

- Step 19 : New measure was created to find total cost .

The following DAX expression was written for this:

        Total Cost = SUMX(Ordertbl, Ordertbl[Amount] * Ordertbl[PurchasingPrice])

A card visual was used to represent this total cost.

![total_cost](https://github.com/user-attachments/assets/af31a3f6-032d-4d97-b0aa-eb03affd52e7)

- Step 20 : New measure was created to find total sales .

The following DAX expression was written for this:

        Total Sales = SUMX(Ordertbl, Ordertbl[Amount] * Ordertbl[SellingPrice])

A card visual was used to represent this total sales.

![total_sale](https://github.com/user-attachments/assets/63d79a42-e428-46d7-862d-ab359ddbcf3b)

- Step 21 : New measure was created to find unique clients.

The following DAX expression was written for this:

        UniqueClients = DISTINCTCOUNT(Ordertbl[CustomerCompany])

A card visual was used to represent this unique clients.

![unique_clients](https://github.com/user-attachments/assets/1ccc53aa-4480-4ebe-b357-bf084800692c)

# Report Snapshot (Power BI DESKTOP)

![dashboard](https://github.com/user-attachments/assets/06105d1f-89d0-4cb7-807c-55c461d1c177)

# Insights

Following inferences can be drawn from the dashboard;

### [1] Classification of customers into three categories.

Top (28.05%) , Least(27.60%) and Average(44.35%) = 2021

Top (33.94%) , Least(35.78%) and Average(30.28%) = 2022

Top (36.27%) , Least(27.43%) and Average(36.30%) = 2023

The top customers contributed more in 2023, the least customers contributed more in 2022, and the average customers contributed more in 2021.

### [2] Sales by Days

    a) Monday - $0.28M
    b) Thursday - $0.27M
    c) Friday - $0.27M
    d) Saturday - $0.27M
    e) Sunday - $0.26M

The highest sales by day were on Monday.
There were no sales recorded on Tuesday and Wednesday. Therefore, they won't be displayed in the dashboard report since the value is zero.

### [3] Total Sales, total cost and Total profit by month

    a) The highest sale was in the month of April - $177,889
    b) The highest cost was in the month of January - $111,258
    c) The highest profit was in the month of April - $68,052

The value will change when it is filtered by each year.

### [4] Total Sales by Quarter

    a) Q1 total sales - $471,451
    b) Q2 total sales - $286,366
    c) Q3 total sales - $253,677
    d) Q4 total sales - $342,207

The highest total sales made by Apple & Peach were in Q1 (January, February, March)
