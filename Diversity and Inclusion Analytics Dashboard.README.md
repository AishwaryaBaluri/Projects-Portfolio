# 👩🏼‍🤝‍👨🏿 Diversity and Inclusion Analytics Dashboard
<div align="Center">
  <img src="https://github.com/user-attachments/assets/51a20caa-06e6-4d70-a539-77e399b306ac" width="100%" height="auto">
</div>

## 📈 Goal
Develop a Power BI dashboard to analyze and visualize Diversity and Inclusion data for a telecom client, focusing on gender balance and promoting strategic changes towards a more inclusive work environment.

## 🎢 Detailed Project Workflow
1. [Data Loading](#data-loading)
2. [Data Transformation](#data-transformation)
3. [DAX Measures](#dax-measures)
4. [Dashboard Design](#dashboard-design)
    - [Welcome Page](#welcome-page)
    - [Gender Analysis](#gender-analysis)
    - [Promotion Insights](#promotion-insights)
5. [Key Insights](key-insights)
### <ins>Data Loading
Loaded HR dataset into Power BI, encompassing demographics, employment histories, performance ratings, and promotion records.

### <ins>Data Transformation
- Adjusted data types for compatibility and accuracy (e.g., text to categorical conversions).
- Cleansed the data by removing duplicates and handling missing values to ensure data integrity.
- Created calculated columns to enhance data granularity, such as calculating tenure from hire dates.

### <ins>DAX Measures
Developed DAX measures to calculate critical diversity metrics:

**Employees_Promoted_FY21 for assessing promotion rates.**

```DAX
Employees_Promoted_FY21 =
DIVIDE(
    COUNTROWS(FILTER('Pharma Group AG', 'Pharma Group AG'[Promotion in FY21?]="Yes")),
    COUNTROWS('Pharma Group AG')
)
```

**Hires_Men and Hires_Women for analyzing hiring trends by gender.**

```DAX
Hires_Men =
Divide(
    COUNTROWS(
        FILTER('Pharma Group AG',
                'Pharma Group AG'[Gender]="Male" &&
                'Pharma Group AG'[New hire FY20?] = "Y"
        )
    ),
    COUNTROWS(
        filter('Pharma Group AG',
                'Pharma Group AG'[New hire FY20?] = "Y"
        )
    )
)
```

```DAX
Hires_Women =
Divide(
    COUNTROWS(
        FILTER('Pharma Group AG',
                'Pharma Group AG'[Gender]="Female" &&
                'Pharma Group AG'[New hire FY20?] = "Y"
        )
    ),
    COUNTROWS(
        filter('Pharma Group AG',
                'Pharma Group AG'[New hire FY20?] = "Y"
        )
    )
)
```

**Leavers for tracking employee turnover.**

```DAX
Leavers = COUNTROWS(FILTER('Pharma Group AG', 'Pharma Group AG'[FY20 leaver?]="Yes"))
```

**Male_Promoted and Women_Promoted for gender-specific promotion rates.**

```DAX
Male_Promoted =
    DIVIDE(
        COUNTROWS(filter(
            'Pharma Group AG',
            'Pharma Group AG'[Gender]= "Male" &&
            'Pharma Group AG'[Promotion in FY21?]="Yes"
            )
        ),
        COUNTROWS(FILTER('Pharma Group AG','Pharma Group AG'[Promotion in FY21?]="Yes")
    ), 0)
```

```DAX
Women_Promoted =
    DIVIDE(
        COUNTROWS(filter(
            'Pharma Group AG',
            'Pharma Group AG'[Gender]= "Female" &&
            'Pharma Group AG'[Promotion in FY21?]="Yes"
            )
        ),
        COUNTROWS(FILTER('Pharma Group AG','Pharma Group AG'[Promotion in FY21?]="Yes")
    ), 0)
```

**Womens Resigned.**

```DAX
Women_Resigned =
DIVIDE(
    COUNTROWS(filter
            ('Pharma Group AG',
             'Pharma Group AG'[Gender]="Female" &&
             'Pharma Group AG'[FY20 leaver?]="Yes")
),
COUNTROWS(FILTER('Pharma Group AG',
                'Pharma Group AG'[FY20 leaver?]="Yes")
), 0)
```

### <ins>Dashboard Design
Designed a comprehensive multi-page dashboard:

#### Welcome Page
  Introducing the diversity and inclusion initiative.
<div align="center">
  <img src="https://github.com/user-attachments/assets/30dfd039-deb1-4ddf-b3c2-c406d0a4898d">
</div>

#### Gender Analysis
Visualizations detailing gender distribution across departments, age groups, and job levels.
<div align="center">
  <img src="https://github.com/user-attachments/assets/5c42b80f-422a-4ec8-9181-3e2bb5522b78">
</div>

#### Promotion Insights
Analyzing promotion trends and highlighting gender equality progress or issues.
<div align="center">
  <img src="https://github.com/user-attachments/assets/9692bb9e-fc16-4486-a03d-28b6b2dd7f9e">
</div>

## 🔍 Key Insights 
Here are the key insights from the Diversity and Inclusion dashboard in concise points:
- Males received more promotions than females across multiple departments, suggesting the need for equitable promotion policies.
- Female employees generally had lower performance ratings, indicating possible bias in evaluation processes that need addressing.
- Hiring trends showed a gender skew with more males in technical roles and females in administrative positions, highlighting areas for promoting gender diversity in role allocation.
- Higher female turnover, especially in senior roles, suggests potential issues in career progression and workplace culture for women.
- Slow progress in achieving gender balance at executive levels points to the need for more effective diversity initiatives and leadership development programs.
