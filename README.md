# Bank Loan Dashboard

This project involves the design and implementation of a comprehensive dashboard using Power BI to analyze loan data for a bank. The primary objective of the dashboard is to provide a clear and insightful visualization of the ratio between good and bad loans, enabling stakeholders to make informed decisions

# Problem Statement

Here we are requested to create three dashboards, namely Summary, Overview, and Details based on the requirements stated below:

![Image](https://github.com/user-attachments/assets/5a3b1427-b119-4d1c-9a84-ceb630fd0850)

![Image](https://github.com/user-attachments/assets/ddfdeff5-5a4e-4739-b385-e557b6c7f3c6)

![Image](https://github.com/user-attachments/assets/7bb3e0eb-95d9-4869-84b4-5a7a8a73a7e2)

# Data cleaning

The data is stored in MS SQL Server, we had tested the data and data is of very good quality. We do not find any NULL or missing values, neither do we have any duplicates records, hence we are good to go ahead with data analysis 

# Data analysis

For this project, we are doing the analysis in MS SQL Server and then the same will be done in Power BI as well. This way we are sure that the values we are showing in the Power BI dashboard after calculating in Power BI actually match with those in MS SQL Server and they are correct

Here are some of the MS SQL queries used to find the required values

![Image](https://github.com/user-attachments/assets/83ae19ac-27d0-49f7-abe9-6712471fd960)

![Image](https://github.com/user-attachments/assets/a1a036d4-73d8-456f-b2fd-675caa8caf69)

![Image](https://github.com/user-attachments/assets/03c362d9-fbd6-4b1c-a4c0-9f0ccef67780)

![Image](https://github.com/user-attachments/assets/d79e4b2d-7908-46d9-874f-d3cea62d073e)

![Image](https://github.com/user-attachments/assets/a6c62236-8263-4b7b-b966-93e4d49b590b)

![Image](https://github.com/user-attachments/assets/8549defe-92de-41fd-af3f-135729dbb8a2)

![Image](https://github.com/user-attachments/assets/a5b0b0a9-44d6-434a-8ed4-84d224c504ea)

- Moving to Power BI
Once all the calcutions are completed in MS SQL Server and we have found out all the required values, we pull the data into Power BI to complete the dashboards

We create measures in Power BI to complete the calculations required, some of them are highlighted below:
- Total Amount Received = SUM(loan_data[total_payment])
- MTD Total Amount Received = CALCULATE([Total Amount Received], DATESMTD('Date Table'[Date]))
- PMTD Total Amount Received = CALCULATE([Total Amount Received], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))
- MoM Total Amount Received = ([MTD Total Amount Received] - [PMTD Total Amount Received])/[PMTD Total Amount Received]
- Total Funded Amount = SUM(loan_data[loan_amount])
- MTD Funded Amount = CALCULATE([Total Funded Amount], DATESMTD('Date Table'[Date]))
- PMTD Total Funded Amount = CALCULATE([Total Funded Amount], DATESMTD(DATEADD('Date Table'[Date], -1, MONTH)))
- MoM Total Funded Amount = ([MTD Funded Amount] - [PMTD Total Funded Amount])/[PMTD Total Funded Amount]
- Total Loan Applications = count(loan_data[id])
- Average Interest Rate = AVERAGE(loan_data[int_rate])
- Average DTI Ratio = Average(loan_data[dti])
- Area Chart Value = var selected_value = SELECTEDVALUE('Measures selected'[Measures])                                          Return SWITCH(selected_value, "Total Loan Applications", [Total Loan Applications], "Total Funded Amount", [Total Funded Amount], "Total Amount Received", [Total Amount Received])
- Area Chart Value Title = [What is selected] & " by Month"

Once we are done creating the required measures, we start designing the dashboards as required. We build Summary dashboard to show the summarized view of the bank loan data, next we create the Overview Dashboard which further analyzes the loan data based on different factors and finally we have the details dashboard which shows the bank loan data in details 

- SUMMARY PAGE
![Image](https://github.com/user-attachments/assets/32a8044f-ee97-4ca0-8d24-61ea41d9639c)
- OVERVIEW PAGE
![Image](https://github.com/user-attachments/assets/aaa63f13-8a2a-4102-8773-6fa04d2956c8)
- DETAILS PAGE
![Image](https://github.com/user-attachments/assets/f8421dc9-0eb2-45d6-abfa-045d9c1eddf0)

Once done, we apply the themes, allign the vizuals, add the required filters and slicers and finally complete the customizations of the dashboards

### Conclusion

The dashboards created help the customer/stakeholders understand how the bank is performing regarding loans, it will allow the customer/stakeholders take better decisions regarding whom to sanction loans and whom not to. 

The dashboards also help the customer analyze day by day how the loans are performing, what are the application count, amount received count, amount disbursed count, good loans and bad loans all under one single report 
