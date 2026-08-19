# 📊 Power BI Sales Dashboard – Beginner Project

Welcome to the **Power BI Sales Dashboard Project**.

This project is designed for beginners to practice the complete Power BI workflow:

**Data → Power Query → Data Cleaning → Merge Queries → Data Model → DAX → Visualizations → Dashboard → Insights**

---

## 📥 Download the Project Files

### 📊 Dataset

Download the Excel dataset from the GitHub repository:

👉 **[Download Sales Dataset](./dataset/Sales-Dashboard-Data.xlsx)**

### 📈 Power BI Dashboard

👉 **[Download Power BI File](./powerbi/Sales-Dashboard.pbix)**

> If you are building the dashboard yourself, try to complete the project before opening the completed `.pbix` file.

---

# 🖼️ Dashboard Preview

![Sales Dashboard](./dashboard/sales-dashboard.png)

---

# 🎯 Learning Objectives

By completing this project, you will learn:

* How to import Excel data into Power BI
* How to use Power Query Editor
* How to clean and transform data
* How to check data types
* How to identify duplicates
* How to trim and format text
* How to merge two tables
* How to create a data model
* How to create calculated columns
* How to create DAX measures
* How to create KPI cards
* How to create charts
* How to use slicers
* How to analyze sales and profit
* How to build an interactive dashboard

---

# 📁 Dataset Structure

The dataset contains two main tables:

### 1. MasterData

Contains product-related information.

| Column        | Description                 |
| ------------- | --------------------------- |
| PRODUCT ID    | Unique product ID           |
| PRODUCT NAME  | Name of the product         |
| CATEGORY      | Product category            |
| UOM           | Unit of Measurement         |
| BUYING PRICE  | Product purchase/cost price |
| SELLING PRICE | Product selling price       |

### 2. InputData

Contains sales transaction information.

| Column       | Description       |
| ------------ | ----------------- |
| DATE         | Transaction date  |
| PRODUCT ID   | Product ID        |
| QUANTITY     | Quantity sold     |
| SALE TYPE    | Type of sale      |
| PAYMENT MODE | Payment method    |
| DISCOUNT %   | Discount provided |

---

# 📌 What is UOM?

**UOM = Unit of Measurement**

It tells us how a product is measured or sold.

| UOM | Meaning        | Example |
| --- | -------------- | ------- |
| Kg  | Kilogram       | Rice    |
| Lt  | Litre          | Milk    |
| Ft  | Feet           | Fabric  |
| No. | Number / Piece | Soap    |

---

# 🚀 Power BI Project Steps

## Step 1 – Download the Dataset

Download:

**`Sales-Dashboard-Data.xlsx`**

from the `dataset` folder.

Open **Power BI Desktop**.

---

# Step 2 – Import the Excel File

In Power BI:

**Home → Get Data → Excel**

Select:

`Sales-Dashboard-Data.xlsx`

Select both:

* `MasterData`
* `InputData`

Then click:

**Transform Data**

This will open the **Power Query Editor**.

---

# 🧹 Step 3 – Power Query Editor

Power Query is used to **clean and transform the data before creating the dashboard**.

You should perform the following checks.

---

## 3.1 Check Column Names

Make sure the column names are clear and consistent.

For example:

* PRODUCT ID
* PRODUCT NAME
* CATEGORY
* UOM
* BUYING PRICE
* SELLING PRICE
* DATE
* QUANTITY
* SALE TYPE
* PAYMENT MODE
* DISCOUNT %

---

## 3.2 Check Data Types

Correct data types are very important.

Recommended data types:

| Column        | Data Type                   |
| ------------- | --------------------------- |
| DATE          | Date                        |
| PRODUCT ID    | Text                        |
| PRODUCT NAME  | Text                        |
| CATEGORY      | Text                        |
| UOM           | Text                        |
| BUYING PRICE  | Decimal Number              |
| SELLING PRICE | Decimal Number              |
| QUANTITY      | Whole Number                |
| SALE TYPE     | Text                        |
| PAYMENT MODE  | Text                        |
| DISCOUNT %    | Decimal Number / Percentage |

### Why check data types?

Power BI needs to know whether a value is:

* Text
* Number
* Date
* Percentage

Incorrect data types can cause problems in calculations and visualizations.

---

# 3.3 Find Duplicates

To check duplicate records:

**Home → Remove Rows → Remove Duplicates**

⚠️ Do not remove duplicates blindly.

A repeated transaction may be a genuine sale.

First identify whether the duplicate is actually an error.

---

# 3.4 Trim Text

Sometimes text contains unwanted spaces.

Example:

```text
" Grocery "
```

Instead of:

```text
"Grocery"
```

Use:

**Transform → Format → Trim**

### Why Trim?

It removes unnecessary spaces before and after text.

This is important because:

```text
"Grocery"
```

and

```text
" Grocery"
```

may be treated as different values.

---

# 3.5 Format Text

You can also use:

**Transform → Format**

Options include:

* UPPERCASE
* lowercase
* Capitalize Each Word
* Trim
* Clean

Use these options to make text consistent.

---

# 3.6 Check Missing Values

Look for:

* Blank values
* Null values
* Missing product IDs
* Missing quantities
* Missing prices
* Missing categories

Do not automatically replace or delete missing values.

First understand why the value is missing.

---

# 🔗 Step 4 – Merge Queries

This is an important step in this project.

`InputData` contains the transaction information, while `MasterData` contains product information such as:

* Product Name
* Category
* UOM
* Buying Price
* Selling Price

We need to bring the product information into `InputData`.

### Steps:

Open **Power Query Editor**.

Select:

**Home → Merge Queries**

Choose:

**InputData**

as the first table.

Choose:

**MasterData**

as the second table.

Select:

**PRODUCT ID**

from both tables.

Use:

**Left Outer Join**

Then click:

**OK**

---

## Why do we use Merge?

`InputData` contains:

```text
PRODUCT ID
QUANTITY
SALE TYPE
PAYMENT MODE
DISCOUNT %
```

`MasterData` contains:

```text
PRODUCT ID
PRODUCT NAME
CATEGORY
UOM
BUYING PRICE
SELLING PRICE
```

Both tables have:

**PRODUCT ID**

So PRODUCT ID acts as the matching column.

After merging, expand the required columns from `MasterData`.

Select:

* BUYING PRICE
* SELLING PRICE
* PRODUCT NAME
* CATEGORY
* UOM

Your `InputData` will now contain the required product information.

---

# 🔄 Step 5 – Close & Apply

After completing the cleaning and merge:

Click:

**Home → Close & Apply**

Power BI will load the transformed data into the model.

---

# 🧩 Step 6 – Model View

Go to:

**Model View**

After merging, your main working table will contain the required information.

For this beginner project, understand the difference between:

### Power Query

Used for:

**Cleaning + Transformation + Merge**

### Model View

Used for:

**Relationships + Data Model**

### Report View

Used for:

**Charts + Slicers + Dashboard**

---

# 🧮 Step 7 – Create Calculated Columns

After the merge, create two calculated columns in `InputData`.

Go to:

**Data View → InputData → New Column**

---

## Column 1 – Total Buying Value

```DAX
Total Buying Value =
InputData[QUANTITY] * InputData[MasterData.BUYING PRIZE]
```

This calculates:

**Quantity × Buying Price**

---

## Column 2 – Total Selling Value

```DAX
Total Selling Value =
InputData[QUANTITY] *
InputData[MasterData.SELLING PRICE] *
(1 - InputData[DISCOUNT %])
```

This calculates the selling value after applying the discount.

### Formula

```text
Quantity × Selling Price × (1 − Discount %)
```

---

# 📊 Step 8 – Create Measures

Now create two measures.

Go to:

**Modeling → New Measure**

---

## Measure 1 – Profit

```DAX
Profit =
SUM(InputData[Total Selling Value])
-
SUM(InputData[Total Buying Value])
```

Profit is calculated as:

```text
Total Selling Value − Total Buying Value
```

---

## Measure 2 – Profit %

```DAX
Profit % =
[Profit] / SUM(InputData[Total Buying Value])
```

This calculates the profit percentage based on total buying value.

Format this measure as:

**Percentage**

---

# 📌 Columns vs Measures

In this project:

### Calculated Columns

Create:

1. `Total Buying Value`
2. `Total Selling Value`

These are calculated **row by row**.

### Measures

Create:

1. `Profit`
2. `Profit %`

Measures are calculated dynamically based on the selected filters and visuals.

---

# 📊 Step 9 – Create Dashboard

Create a new report page.

Your dashboard should contain the following.

---

## KPI Cards

Create four cards:

### Card 1

**Total Sales**

Use:

`SUM(Total Selling Value)`

### Card 2

**Quantity**

Use:

`SUM(QUANTITY)`

### Card 3

**Profit**

Use:

`Profit`

### Card 4

**Profit %**

Use:

`Profit %`

---

# 🎛️ Step 10 – Add Slicers

Add slicers for:

* Year
* Month Name
* Sale Type
* Payment Mode

These slicers allow users to interactively filter the dashboard.

---

# 📈 Step 11 – Create Visualizations

Create the following visuals.

### 1. Sales by Month

Use:

* Month Name
* Total Selling Value
* Profit

Recommended visual:

**Column Chart**

---

### 2. Sales by Sale Type

Use:

* Sale Type
* Total Selling Value

Recommended visual:

**Donut Chart**

---

### 3. Sales by Product

Use:

* Product Name
* Total Selling Value

Recommended visual:

**Bar Chart**

Sort from:

**Highest → Lowest**

---

### 4. Sales by Day

Use:

* Date
* Total Selling Value

Recommended visual:

**Line Chart**

---

### 5. Sales by Payment Mode

Use:

* Payment Mode
* Total Selling Value

Recommended visual:

**Donut Chart**

---

### 6. Sales by Category

Use:

* Category
* Total Selling Value

Recommended visual:

**Treemap**

---

# 🎨 Step 12 – Dashboard Design

Try to create a clean dashboard with:

* Dashboard title
* KPI cards
* Slicers
* Consistent fonts
* Proper alignment
* Appropriate chart sizes
* Clear labels
* Meaningful visual titles

Example dashboard title:

# **Sales Dashboard**

---

# 🔎 Step 13 – Analyze the Dashboard

After creating the dashboard, answer these questions:

### Sales

1. What is the total sales?
2. What is the total quantity sold?
3. Which year has higher sales?
4. Which month has the highest sales?
5. Which product has the highest sales?
6. Which category has the highest sales?

### Profit

7. What is the total profit?
8. What is the profit percentage?
9. Which product generates the highest profit?
10. Are any products generating negative profit?

### Sales Type

11. Which sale type generates the highest sales?
12. Which sale type generates the highest profit?

### Payment

13. Which payment mode has higher sales?
14. Compare Cash vs Online sales.

### Discount

15. How does discount affect profit?
16. Identify products where high discounts reduce profitability.


---

# 👨‍🏫 Project Instructions

**First try to build the dashboard yourself.**

Use the completed `.pbix` file only as a reference after attempting the project.

Focus on understanding:
