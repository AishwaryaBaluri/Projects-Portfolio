# 🛒 Customer Retention Analysis Dashboard
<div align="Center">
  <img src="https://github.com/user-attachments/assets/330b3e2e-d746-4089-aed5-2e4fa97dafaa" width="800" height="auto">
</div>

## 📈 Goal
To develop a detailed and interactive Power BI dashboard to conduct an in-depth analysis of customer churn for a telecom company. This dashboard will leverage advanced DAX measures to analyze demographic data, account specifics, and service subscriptions to pinpoint critical churn indicators. Simultaneously, it will proactively identify customer segments at high risk of churn. The ultimate aim is to empower the retention team with actionable insights from the visual data, enabling them to devise and deploy effective strategies that minimize churn and boost customer loyalty.

## 🎢 Detailed Project Workflow
1. [Data Loading](#data-loading)
2. [Data Transformation](#data-transformation)
3. [DAX Measures](#dax-measures)
   - [CHURN METRICS](#churn-metrics)
   - [RISK METRICS](#risk-metrics)
5. [Dashboard Design](#dashboard-design)
   - [Welcome Page](#welcome-page)
   - [Customer Churn Analysis Page:](#customer-churn-analysis-page)
   - [Risk Analysis Page](#risk-analysis-page)
6. [Analysis and Insights](#analysis-and-insights)

### <ins>Data Loading
The project started by importing the telecom company's customer data into Power BI Desktop. The data set included detailed customer demographics, their service subscriptions, account details, and history of support interactions. Ensuring data integrity and accuracy at this stage was crucial for the reliability of the subsequent analysis.

### <ins>Data Transformation
Once loaded, the data underwent a rigorous transformation process:
- **Data Type Standardization:** 
Ensuring all data fields were in correct formats (e.g., dates, categorical and continuous variables) to allow accurate calculations and comparisons.
- **Data Cleaning:**
Removing duplicates, filling or removing missing values, and correcting inconsistencies to purify the dataset for analysis.

*Below is the snip of the data transformed

![image](https://github.com/user-attachments/assets/ef29e8fa-6319-4b8b-be86-80522b81c60d)


### <ins>DAX Measures
Critical DAX measures were developed to perform dynamic and complex calculations directly within the Power BI environment, which include:

#### CHURN METRICS
These measures calculate the total number of churned and retained customers, segmented by various factors such as service type and contract length.

**Total Churned Customers:**
```DAX
  Total_Churned = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[Churn]="Yes")
```
**Total Retained Customers:**
```DAX
Total_Retained = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[Churn]="No")
```

**Churn by Service Type:**
```DAX
Churn_By_Service = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[Service]="ServiceName", '01 Churn-Dataset'[Churn]="Yes")
```

**Churn by Contract Length:**
```DAX
Churn_By_Contract = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[ContractLength]="ContractType", '01 Churn-Dataset'[Churn]="Yes")
```

**Churn Admin Tickets:**
```DAX
  Churn_Admintickets = CALCULATE(SUM('01 Churn-Dataset'[numAdminTickets]), '01 Churn-Dataset'[Churn]="Yes")
```

**Churn Tech Tickets:**
```DAX
Churn_Techtickets = CALCULATE(SUM('01 Churn-Dataset'[numTechTickets]), '01 Churn-Dataset'[Churn]="Yes")
```

**Customers at Risk:**
```DAX
Customers at risk = COUNTX(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn]="Yes"), '01 Churn-Dataset'[Churn])
```

**Customers Retained:**
```DAX
CustomersRetained = COUNTX(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn]="No"), '01 Churn-Dataset'[Churn])
```


#### RISK METRICS
These measures focus on identifying risk factors for churn based on demographic traits, service usage patterns, and customer service interactions.

**Risk by Demographics:**
```DAX
  Demographic_Risk = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[Demographic]="DemographicType", '01 Churn-Dataset'[Churn]="Yes")
```

**Risk by Service Usage:**
```DAX
Service_Usage_Risk = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[ServiceUsed]="ServiceType", '01 Churn-Dataset'[Churn]="Yes")
```

**Risk by Support Tickets:**
```DAX
Support_Ticket_Risk = CALCULATE(COUNTROWS('01 Churn-Dataset'), '01 Churn-Dataset'[TicketType]="TechSupport", '01 Churn-Dataset'[Churn]="Yes")
```

**Dependents Percentage Churned:**
```DAX
Dependents_Percentage_Churned = DIVIDE(
      COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Dependents] = "Yes" && '01 Churn-Dataset'[Churn] = "Yes")),
      COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"))
```

**Device Protection Percentage:**
```DAX
DeviceProtection_Per = DIVIDE(
    COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[DeviceProtection] = "Yes")),
    COUNTROWS('01 Churn-Dataset')
)
```

**Gender-Based Churn Percentage:**
```DAX
Female_Percentage_Churned = DIVIDE(
    COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[gender] = "Female" && '01 Churn-Dataset'[Churn] = "Yes")),
    COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"))
) * 100

Male_Percentage_Churned = DIVIDE(
    COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[gender] = "Male" && '01 Churn-Dataset'[Churn] = "Yes")),
    COUNTROWS(FILTER('01 Churn-Dataset', '01 Churn-Dataset'[Churn] = "Yes"))
) * 100
```

**Monthly Charges for Churned Customers:**
```DAX
Monthly_Charge = CALCULATE(SUM('01 Churn-Dataset'[MonthlyCharges]),'01 Churn-Dataset'[Churn]="Yes")
```

**Yearly Charges for Churned Customers:**
```DAX
Yearly_charges = CALCULATE(SUM('01 Churn-Dataset'[TotalCharges]), '01 Churn-Dataset'[Churn]="Yes")
```
### <ins>Dashboard Design

The dashboard was designed with a user-centric approach to ensure ease of navigation and interaction:

#### Welcome Page
An introductory page with general information on how to navigate the dashboard effectively.

<Div align="Center">
  <img src="https://github.com/user-attachments/assets/7d5812c1-ac3f-4ad0-b129-351f134c0260" width="100%">
</Div>



#### Customer Churn Analysis Page 
Visual representations of churn statistics, depicting trends over time, churn by service type, and impact of customer service interactions on churn.

<Div align="Center">
  <img src="https://github.com/user-attachments/assets/dcd27b6b-adf5-40a6-ba11-adee4a0fe194" width="100%">
</Div>

#### Risk Analysis Page
Detailed analyses focusing on identifying segments at high risk of churn, with visual filters for users to explore different customer segments and risk factors.

<Div align="Center">
  <img src="https://github.com/user-attachments/assets/633f59f3-f3de-4b8b-96ac-e5d87181d7c3"  width="100%">
</Div>

### Analysis and Insights
This dashboard section delves deep into the patterns and trends identified through the visualizations, offering strategic insights:

- **Proactive Interventions:** Based on the identified high-risk segments, suggesting targeted interventions that the retention team can initiate to reduce churn.

- **Customer Segmentation:** Highlighting specific demographic and service-related attributes that contribute to higher churn rates, allowing for customized retention strategies.


## ✍️ Conclusion

- **Churn Analysis Page:** Highlights the overall churn rates and breaks them down by demographic segments, showcasing how different factors such as age, gender, and service types impact customer retention.

- **Risk Analysis Page:** Focuses on predicting future churn by analyzing current customer behaviors and service usage patterns, allowing preemptive actions to be taken.

- **Interactive Features:** Users can interact with various slicers and controls to delve into specific datasets, making the dashboard not only a tool for viewing data but also a powerful analysis tool for predictive insights.
