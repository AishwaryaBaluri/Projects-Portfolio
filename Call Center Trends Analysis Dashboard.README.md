<h1 style="text-decoration: underline;">📞 Call Center Trends Analysis Dashboard</h1>

<div align="center">
    <img src="https://github.com/user-attachments/assets/a23738ff-f7dd-4326-a82b-045b907deec1" width="500" height="500">
</div>

## 📈 Goal 
The aim of this project is to create a dynamic Power BI dashboard for a leading telecom company to unveil what truly drives customer satisfaction and agent effectiveness. 
By integrating KPIs such as overall customer satisfaction, call response metrics, and agent performance analytics, the dashboard will serve as a decisive tool for understanding consumer demands and optimizing call center operations. This initiative directly supports strategic decision-making by providing clarity on key aspects like call handling efficiency and service quality across different customer segments.
## 🎢 Detailed Project Workflow
1. [Data Loading](#data-loading)
2. [Data Transformation](#data-transformation)
3. [DAX Measures](#dax-measures)
4. [KPI Integration](#kpi-integration)
5. [Slicers](#slicers)
6. [Gauge Visuals](#gauge-visuals)
7. [Chart Visuals](#chart-visuals)
### <ins>Data Loading
I imported the dataset from Excel into Power BI Desktop, setting the stage for a detailed analysis. This step involved loading comprehensive call center operation data to explore trends and performance metrics effectively.
### <ins>Data Transformation
#### *Data Type Adjustment:* 
I verified and adjusted the data types of all columns to ensure compatibility and accuracy in analysis.

| FIELD                 | DATA TYPE      |
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

#### *Quality Checks:* 
I conducted thorough quality checks across the dataset to ensure data integrity. This included identifying and correcting any discrepancies, removing blank rows, and validating data consistency, thus preparing a clean and reliable dataset for analysis.

### <ins>DAX Measures

I developed several DAX measures to quantify various aspects of call center performance, which are critical for the dashboard visualizations:

**Average Speed of Answer in Seconds**
```DAX
Avg_SpeedOfAnswer_Sec = DIVIDE(
    SUM('call center Dataset'[Speed of answer in seconds]),
    COUNT('call center Dataset'[Speed of answer in seconds]),
    0
) 
```
**Count of Calls Answered**
```DAX
Calls_Answered = CALCULATE(COUNT('call center Dataset'[Answered (Y/N)]), 'call center Dataset'[Answered (Y/N)] = 1)
```
**Count of Calls Unanswered**
  ```DAX
Calls_Unanswered = CALCULATE(COUNT('call center Dataset'[Answered (Y/N)]), 'call center Dataset'[Answered (Y/N)]=0)
```
**Count of Calls Resolved**
```DAX
Calls_Resolved = CALCULATE(COUNT('call center Dataset'[Resolved]),'call center Dataset'[Resolved]=1
```
**Count of Calls Unresolved**
```DAX
Calls_UnResolved = CALCULATE(COUNT('call center Dataset'[Resolved]),'call center Dataset'[Resolved]=0)
```
**Overall Customer Satisfaction**
```DAX
Overall_CustomerSatisfaction = DIVIDE(COUNTROWS(FILTER('call center Dataset','call center Dataset'[Satisfaction rating] >=4)), COUNTROWS('call center Dataset'),0)
```
### <ins>KPI Integration
I integrated these DAX measures as Key Performance Indicators (KPIs) within the dashboard. This allows for professional and organized reporting, giving stakeholders a clear view of operational metrics and their implications.

### <ins>Slicers
To enhance dashboard interactivity, I implemented slicers for **'Quarter'** and **'Agent'** These slicers enable users to dynamically filter the data, customizing the view according to specific time periods or agents, which facilitates targeted analysis.

### <ins>Gauge Visuals
Gauge visuals were incorporated to depict the progress of average customer satisfaction against predefined targets, offering a quick visual assessment of goal attainment.

### <ins>Chart Visuals
 incorporated a range of charts into the Power BI dashboard, each specifically designed to meet the unique analytical needs of the company. As depicted in the visual examples, these charts transform complex data sets into clear, intuitive formats. This approach not only enhances the accessibility of the data but also facilitates a deeper understanding, enabling users to quickly grasp key insights and make informed decisions based on comprehensive visual evidence.
 
## ✍️ Conclusion

The Call Center Trends Analysis Dashboard meticulously tracks performance metrics, revealing that of 5,000 total calls, 4,054 were successfully answered, while 946 went unanswered, indicating areas needing improvement. The resolution rate stood strong at approximately 73%, underscoring effective call handling. However, overall customer satisfaction was recorded at 40.46%, signaling opportunities for enhancing service strategies. Monthly trends showed consistent call volume and resolution rates, ensuring operational stability. Variations in agent performance suggest a need for focused training or procedural changes to improve consistency and service quality.

<div align="Center">
    <img src="https://github.com/user-attachments/assets/f12d1abc-fd9d-486a-90cc-6e0f25ae990c" width="100%" height=auto>
</div>

