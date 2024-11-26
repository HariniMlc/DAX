# DAX Tutorials and Basics

Welcome to the DAX (Data Analysis Expressions) repository! This repository contains tutorials and basic information to help you get started with DAX, a powerful formula language used in Microsoft Power BI, Excel, and SQL Server Analysis Services.

## Table of Contents
- Introduction to DAX
- Basic Functions
  - SUM
  - SUMX
  - AVERAGE
  - CALCULATE
- Measures
- Calculated Columns
- Variables
- Best Practices
- Resources

## Introduction to DAX
DAX (Data Analysis Expressions) is a formula language used for data modeling and analysis. It is designed to work with relational data and perform dynamic aggregation. DAX is used in various Microsoft products, including Power BI, Excel, and SQL Server Analysis Services.

## Basic Functions

### SUM
The `SUM` function adds up all the values in a single column.
```dax
SUM(Sales[Amount])
```

### SUMX
The `SUMX` function calculates the sum of an expression evaluated for each row in a table.
```dax
SUMX(Sales, Sales[Quantity] * Sales[Price])
```

### AVERAGE
The `AVERAGE` function calculates the average of a column.
```dax
AVERAGE(Sales[Amount])
```

### CALCULATE
The `CALCULATE` function evaluates an expression in a modified filter context.
```dax
CALCULATE(SUM(Sales[Amount]), Sales[Region] = "West")
```

## Measures
Measures are calculations used in data analysis that are evaluated based on the context of the data. They are dynamic and change according to the filters applied in your report.

### Example of a Measure
```dax
Total Sales = SUM(Sales[Amount])
```

## Calculated Columns
Calculated columns are computed during data load and stored in the table. They are static and do not change based on filters.

### Example of a Calculated Column
```dax
Sales[Total Price] = Sales[Quantity] * Sales[Price]
```

## Variables
Variables in DAX are used to store the result of an expression so that it can be reused multiple times in the same calculation. They help improve readability and performance.

### Example of Using Variables
```dax
Total Sales with Discount = 
VAR DiscountRate = 0.1
VAR TotalSales = SUM(Sales[Amount])
RETURN TotalSales * (1 - DiscountRate)
```

## Best Practices
- Use measures instead of calculated columns whenever possible.
- Keep your DAX code clean and well-documented.
- Test your DAX expressions thoroughly to ensure accuracy.

## Resources
- Microsoft DAX Documentation
- DAX Guide
- SQLBI DAX Patterns

Happy analyzing!

