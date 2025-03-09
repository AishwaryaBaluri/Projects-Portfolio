# Top Categories Contributing to the Success of an IPO
## Goal
The goal of this project is to identify and analyze the top content categories that significantly contribute to the success of an Initial Public Offering (IPO). By utilizing data analysis techniques in Excel, this project aims to generate insights that will inform strategic decision-making for Social Buzz, ensuring the company is well-prepared to execute a successful IPO.
## Detailed Project Workflow
### 1. Understanding the Business Requirement
The initial step involves a deep analysis of the project requirements. Social Buzz is preparing for an IPO and needs expertise to analyze their content categories based on user engagement to optimize their offerings. Clear objectives are set to focus on data that impacts user interactions and company growth.
### 2. Requirement Gathering
There are total seven distinct datasets, encompassing various aspects of user interaction and content dynamics. However, upon analyzing the project requirements, it became apparent that not all datasets were necessary for analysis on content category popularity. To streamline our efforts and ensure the precision of the insights, I selected only three datasets that are directly relevant to user interactions and content engagement metrics: **Reaction**, **Reaction Type**, **Content**.
  
  *Below is a snapshot of the data model used to integrate and analyze these three datasets effectively:*
![image](https://github.com/user-attachments/assets/8f6fc40f-7c00-40a7-8fe6-da2bb5c49b81)

### 3. Data Cleaning and Preparation
Key steps in data cleaning included:

- Eliminating records with missing or incomplete data.
- Standardizing data formats across columns to ensure uniformity.
- Removing unnecessary columns to focus exclusively on those that contribute to content engagement analysis, such as **Unique_ID, Content ID, Reaction Type, Datetime, Sentiment, Score, and Content Type.**

### 4. Integrative Data Modeling
To facilitate comprehensive analysis, I merged the selected datasets into a unified 'Reaction File'. This integration was achieved using Excel’s VLOOKUP() function for precise data alignment:

- Mapped Reaction Types: Connected Reaction[Type] with ReactionTypes[Type] to standardize reaction categories across the datasets.
- Linked Content IDs: Associated Content[Content ID] with Reaction[Content ID] to accurately match reactions to their respective content.
* Below is the final 'Reaction File' showcasing the integrated data model ready for analysis *

![image](https://github.com/user-attachments/assets/ccc01f37-2033-4372-8404-6df7674bd6e9)


### 5. Analytical Processing
- **Category Analysis:** Used the UNIQUE() function to determine unique content categories, followed by SUMIF() to quantify their popularity based on user scores.

  ![image](https://github.com/user-attachments/assets/1fdab5ad-5180-484d-bd66-b572d1cfa6b4)

- **Top Category Identification:** Analysis highlighted the most engaged-with categories: Healthy Eating, Technology, Food, and Cooking, pinpointing areas with the highest user interest

  ![image](https://github.com/user-attachments/assets/81964cbf-c96e-4155-88ac-2821177c002c)

- **Content Type Reaction Metrics:** A pivot table was used to analyze reactions across different content types, revealing insights into user preferences and content interaction.

  <img width="564" alt="image" src="https://github.com/user-attachments/assets/7cc370b9-c6b7-4941-8f83-398e220d751c" />

- **Sentiment Impact Evaluation:** Employed another pivot table to assess how different sentiments affect content popularity, crucial for understanding emotional engagement with the content.

  <img width="390" alt="image" src="https://github.com/user-attachments/assets/8a05599e-1665-4b06-b804-524f3fbe02b5" />

### Conclusion:

My analysis successfully identified the key content categories driving engagement and contributing to IPO readiness. I discovered that categories such as **Healthy Eating, Technology, Food, and Cooking** were the most popular among users, indicating strong preferences for content that either provides practical information or enhances lifestyle quality.

Additionally, the analysis highlighted that Visual Content Types like **GIFs** and **Photos** are particularly effective in engaging users, with a significant majority of reactions being positive. This suggests that incorporating more visually appealing content could further enhance user interaction and support successful content strategies.

Overall, my Excel-based data analysis project has provided crucial insights into content preferences and user engagement, offering valuable guidance for strategic content planning in preparation for an IPO.






