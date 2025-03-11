# Call Center Trends Analysis Dashboard
## Goal
The aim of this project is to create a dynamic Power BI dashboard for a leading telecom company to unveil what truly drives customer satisfaction and agent effectiveness. 
By integrating KPIs such as overall customer satisfaction, call response metrics, and agent performance analytics, the dashboard will serve as a decisive tool for understanding consumer demands and optimizing call center operations. This initiative directly supports strategic decision-making by providing clarity on key aspects like call handling efficiency and service quality across different customer segments.
## Detailed Project Workflow
### 1. Data Loading:
I imported the Excel dataset into Power BI Desktop, preparing it for analysis.
### 2. Data Transformation:
**Data Type Adjustment:** I verified and adjusted the data types of all columns to ensure compatibility and accuracy in analysis.

| Field                 | Data Type      |
|-----------------------|----------------|
| Call Id               | Text           |
| Agent                 | Text           |
| Date                  | Date           |
| Time                  | Time           |
| Topic                 | Text           |
| Answered (Y/N)        | Text           |
| Resolved              | Text           |
| Speed of Answer in Seconds | Whole Number |
| Avg Talk Duration     | Time Duration  |
| Satisfaction Rating   | Whole Number   |

**Quality Checks:** I conducted quality checks to identify and rectify any errors, removing unnecessary blank rows to clean the dataset.

**Measures:** I crafted dynamic measures to facilitate user-driven data aggregation and enhance the interactivity of the report's KPIs and visualizations.

### DAX Measures

Below are some of the key DAX measures used in the Power BI dashboard, along with explanations of their functions:

```DAX
// Calculate Average Speed of Answer in Seconds
Avg_SpeedOfAnswer_Sec = DIVIDE(
    SUM('call center Dataset'[Speed of answer in seconds]),
    COUNT('call center Dataset'[Speed of answer in seconds]),
    0
) 

// Count of Calls Answered
Calls_Answered = CALCULATE(COUNT('call center Dataset'[Answered (Y/N)]), 'call center Dataset'[Answered (Y/N)] = 1)

// Count of Calls Unanswered
Calls_Unanswered = CALCULATE(COUNT('call center Dataset'[Answered (Y/N)]), 'call center Dataset'[Answered (Y/N)]=0)

// Count of Calls Resolved
Calls_Resolved = CALCULATE(COUNT('call center Dataset'[Resolved]),'call center Dataset'[Resolved]=1

// Count of Calls Unresolved
Calls_UnResolved = CALCULATE(COUNT('call center Dataset'[Resolved]),'call center Dataset'[Resolved]=0)

// Overall Customer Satisfaction
Overall_CustomerSatisfaction = DIVIDE(COUNTROWS(FILTER('call center Dataset','call center Dataset'[Satisfaction rating] >=4)), COUNTROWS('call center Dataset'),0)

```
**KPI Integration:** I integrated key performance indicators into the dashboard based on the calculated measures, organizing them to support professional reporting needs.

**Slicers:** Implemented slicers for 'Select Quarter' and 'Select Agent' to allow users to filter and retrieve data dynamically.

**Gauge Visuals:** Incorporated gauge visuals to illustrate the progress of average satisfaction relative to the target goal.

**Chart Visuals:** Added various charts tailored to the company's specific analytical requirements.

Below is the final snapshot of the dashboard I developed.
