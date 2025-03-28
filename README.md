# Credit Card Weekly Status Report - Power BI Project

## Project Overview

This Power BI project is designed to analyze and visualize the weekly status of credit card transactions and customer data. The data includes credit card details and customer demographics, which are processed to generate insights on various performance metrics.

The data source consists of two tables:

1. **Credit Card Table**: Contains detailed credit card transaction and usage information.
2. **Customer Table**: Contains customer demographic and financial information.

### Tables and Columns

**Credit Card Table:**
- `Client_Num`: Unique identifier for the client
- `Card_Category`: The category of the credit card (e.g., Blue, Silver)
- `Annual_Fees`: The annual fee for the credit card
- `Activation_30_Days`: Whether the card was activated within 30 days
- `Customer_Acq_Cost`: The cost of acquiring the customer
- `Week_Start_Date`: The start date of the week
- `Week_Num`: The week number
- `Qtr`: The quarter number
- `Current_Year`: The year of the transaction
- `Credit_Limit`: The credit limit for the card
- `Total_Revolving_Bal`: The total revolving balance
- `Total_Trans_Amt`: The total transaction amount
- `Total_Trans_Vol`: The total transaction volume
- `Avg_Utilization_Ratio`: The average utilization ratio
- `Use Chip`: Whether the customer uses a chip on the card
- `Exp Type`: The type of card expense (e.g., purchase, cash advance)
- `Interest_Earned`: The interest earned from transactions
- `Delinquent_Acc`: Whether the account is delinquent

**Customer Table:**
- `Client_Num`: Unique identifier for the customer
- `Customer_Age`: Age of the customer
- `Gender`: Gender of the customer
- `Dependent_Count`: Number of dependents
- `Education_Level`: Education level of the customer
- `Marital_Status`: Marital status of the customer
- `State_cd`: State code of residence
- `Zipcode`: Customer’s zipcode
- `Car_Owner`: Whether the customer owns a car
- `House_Owner`: Whether the customer owns a house
- `Personal_loan`: Whether the customer has a personal loan
- `Contact`: Contact method
- `Customer_Job`: Job type
- `Income`: Income of the customer
- `Cust_Satisfaction_Score`: Customer satisfaction score

---

## Data Workflow

1. **Data Import**: The data is imported into MySQL from CSV files containing credit card and customer data.
2. **Power BI Connection**: Once the data is in MySQL, it is connected to Power BI Desktop for further analysis.
3. **Data Preparation**: The data is cleaned and transformed using DAX queries to create new columns and measures for efficient analysis.

---

## DAX Measures and Calculations

To facilitate in-depth analysis, several custom DAX queries and calculations have been created:

### 1. **Age Group**  
Categorizes customers into age groups.

```DAX
AgeGroup = SWITCH(
    TRUE(),
    'public cust_detail'[customer_age] < 30, "20-30",
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
    'public cust_detail'[customer_age] >= 60, "60+",
    "unknown"
)
