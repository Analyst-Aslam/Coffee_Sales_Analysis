# Coffee_Sales_Analysis

## Overview

This project involves accessing the required data about the sales from different sheets in Excel, formatting to create a dashboard to express the coffee sales.

---

## Dataset Information

- **Source**: CoffeeOrdersData is available in the repository.
  (Access the dataset from [GitHub Repository Link](https://github.com/Analyst-Aslam/Coffee_Sales_Analysis))

---

## How to Use the Dashboard

- **Excel Dashboard File**
  Download the Completed project Excel file [CoffeeOrdersProject](https://github.com/Analyst-Aslam/Coffee_Sales_Analysis/blob/main/CoffeeOrdersProject.xlsx)
  
---

##Steps 

1.Data Integration from Customers and Products Sheets into Orders Sheet:

Begin by pulling relevant data from the Customers and Products sheets into the Orders sheet, based on matching values, to populate the necessary columns.
To retrieve the Customer Name, Email, and Country from the Customers sheet, the following XLOOKUP formulas are used:

For Customer Name:
```excel
=XLOOKUP(C2,customers!$A$1:$A$1001,customers!$B$1:$B$1001,,0)
```

For Customer Email (with blank returned for missing values, using IF along with XLOOKUP):
```excel
=IF(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
```

For Customer Name Country:
```excel
=XLOOKUP(C2,customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)
```
2.Retrieving Product Data Using INDEX and MATCH:

To gather the required data for the products purchased by the customer, based on the product ID, use the following INDEX and MATCH formula:
```excel
=INDEX(products!$A$1:$G$49,MATCH(orders!$D2,products!$A$1:$A$49,0),MATCH(orders!I$1,products!$A$1:$G$1,0))
```
This approach efficiently retrieves the necessary product information.

3.Sales Calculation:

The Sales value is determined by multiplying the Quantity by the Unit Price, using the respective cell addresses.

4.Creation of New Columns for Coffee Type and Roast Type Names:

New columns for Coffee Type Name and Roast Type Name are created by constructing full names for the values in the Coffee Type and Roast Type columns. The formulas used are as follows:
```excel
=IF(I2="Rob","Robesta",IF(I2="Exc","Excelsa",IF(I2="Ara","Arabica",IF(I2="Lib","Liberica",""))))

=IF(J2="M","Medium",IF(J2="L","Light",IF(J2="D","Dark"," ")))
```
5.Formatting:

The Unit Price and Sales columns are formatted as Currency.
The Size column is custom formatted to include the kg unit indicator.
The entire dataset is then converted into a Table for enhanced data management and analysis.
