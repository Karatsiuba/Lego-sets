# LEGO-sets
This is an interactive Power BI dashboard for exploring the evolution of LEGO sets over the past 50 years 📊
## About My Project
This project is my personal take on the story behind LEGO — not just as a toy, but as a cultural phenomenon. I wanted to explore how LEGO sets have changed over the past 50 years: the themes we loved, the complexity we faced, and how prices evolved. My goal was to build something interactive and insightful — not just for data nerds, but for collectors, casual fans, and curious minds alike.
#### 🎯 Project Goals
The main goal was to turn a raw dataset into something that tells a story. I wanted to:

• Visualize how LEGO themes have shifted over time

• Track changes in set sizes and pricing

• Explore the relationship between piece count and price

• Create an intuitive, interactive dashboard that makes data exploration fun and simple

#### 💼 Business Needs
LEGO has grown into one of the most iconic toy brands in the world, with a massive catalog of sets spanning decades. By analyzing trends in themes, pricing, and build complexity, we can uncover valuable insights that speak to both nostalgic collectors and modern-day enthusiasts. This project aims to dive into LEGO’s rich history and uncover the key patterns that have shaped its evolution.

The specific goals of this analysis include:

• Identifying trends in set size, complexity, and pricing

• Recognizing which themes and categories gained popularity over time

• Supporting data-driven decisions for inventory, marketing, and collection planning

### Approach & Insights
🧼 Data Preparation:
The dataset — covering over 18,000 LEGO sets from 1970 to 2022 — was cleaned and structured to ensure reliable analysis. Missing values were handled, columns were standardized, and data types were adjusted where necessary.

🔎 Exploratory Analysis:
I explored core metrics such as average piece count per set, theme popularity over time, pricing patterns, and the relationship between set size and cost. This phase helped shape the visuals and guide the story behind the data.

📊 Dashboard Design:
Using Power BI, I built an interactive dashboard with slicers, custom tooltips, navigation features, and decomposition trees. Each visual was designed to support intuitive exploration and highlight meaningful trends.

🧠 Key Insights:
Over the years, LEGO sets have become larger and more intricate, with standout themes like Star Wars and Technic continuing to shine — and when it comes to pricing, it’s not just about size, but also age range, branding, and theme.

## Steps to Complete the LEGO Sets Project
#### Data Acquisition
I started by downloading the LEGO dataset from [Maven Analytics], which included information on over 18,000 sets. Before jumping into analysis, I reviewed the structure to make sure everything was clean, relevant, and ready for Power BI.

#### Importing into Power BI
Once the data was ready, I opened Power BI Desktop and used the “Get Data” feature to load the dataset. From there, I began shaping and transforming the data using Power Query — setting the stage for analysis and visualization.

![image](https://github.com/user-attachments/assets/6745830a-9e93-40bb-bf49-28207854d54c)

#### Data Transformation in Power Query
After importing the dataset into Power BI, I clicked "Transform Data" to open the Power Query Editor.

Here’s what I did during this stage:

• Removed null values and unnecessary rows

• Renamed columns for better readability

• Adjusted data types for accurate analysis
•Created a new conditional column called `Age Range`, which grouped sets into age-based categories:
<details>
<summary>Age Range</summary>

- **Over** – for sets recommended for ages 18+  
- **10 to 17** – for older children and teens  
- **5 to 9** – for younger builders  
- **1 to 4** – for toddler-friendly sets

This made it easier to segment the data by age group in slicers and visuals.
</details>

---
![Age_range](https://github.com/user-attachments/assets/d0a25fdd-92b8-4beb-9460-5bd14fe6c809)

• Created another conditional column named `Price Range`, to classify sets by cost using dollar signs:
<details>
<summary>Price Range</summary>

- **$$$$$** – sets over $500  
- **$$$$** – $100 to $500  
- **$$$** – $50 to $100  
- **$$** – $5 to $50  
- **$** – under $5

This allowed for quick filtering and intuitive comparison of set prices.
</details>

![Price_range](https://github.com/user-attachments/assets/58698606-cc5d-4570-9c76-99938a113e1d)

## DAX Measures & Calculations
To keep everything organized, I created a dedicated Measure Table using the Enter Data option in Power BI and added all my DAX measures there. Below are the key calculations used across the dashboard:

<details>
<summary>Total Sets</summary>

```DAX
Total Sets = DISTINCTCOUNT(lego_sets[set_id])
```

Counts all unique LEGO sets, ensuring duplicates do not affect the result.
</details>

<details>
<summary>Total Theme Groups</summary>

```DAX
Total Groups = DISTINCTCOUNT(lego_sets[themeGroup])
```

Calculates the number of distinct theme groups in the dataset.
</details>

<details>
<summary>Average Age</summary>

```DAX
Avg. Age = AVERAGE(lego_sets[age])
```

Returns the average recommended age across all LEGO sets.
</details>

<details>
<summary>Average Pieces</summary>

```DAX
Avg. Pieces = AVERAGE(lego_sets[pieces])
```

Calculates the average number of pieces per LEGO set.
</details>

<details>
<summary>Average Price</summary>

```DAX
Avg. Price = AVERAGE(lego_sets[price])
```

Returns the average price of LEGO sets.
</details>

<details>
<summary>Max Price Filter</summary>

```DAX
Max Price Filter = MAX('Max Price'[Max Price])
```

Returns the selected value from the Max Price table for filtering visuals.
</details>

### Dynamic Selection Measures

<details>
<summary>Selected Age</summary>

```DAX
Selected Age = 
IF(
  HASONEVALUE(lego_sets[age]),
  MAX(lego_sets[age]),
  "-"
)
```

Displays the selected age, or "-" if multiple or none selected.
</details>

<details>
<summary>Selected Pieces</summary>

```DAX
Selected Pieces = 
IF(
  HASONEVALUE(lego_sets[pieces]),
  MAX(lego_sets[pieces]),
  "-"
)
```

Displays the selected piece count, or "-" if multiple or no values are selected.
</details>

<details>
<summary>Selected Price</summary>

```DAX
Selected Price = 
IF(
  HASONEVALUE(lego_sets[price]),
  MAX(lego_sets[price]),
  "-"
)
```

Displays the selected set’s price, or a placeholder.
</details>

<details>
<summary>Selected Set</summary>

```DAX
Selected Set = 
IF(
  HASONEVALUE(lego_sets[name]),
  MAX(lego_sets[name]),
  "Select a Set"
)
```

Returns the name of the selected LEGO set, or a default prompt.
</details>

<details>
<summary>Selected Year</summary>

```DAX
Selected Year = 
IF(
  HASONEVALUE(lego_sets[year]),
  MAX(lego_sets[year]),
  "-"
)
```

Displays the release year of the selected LEGO set.
</details>

---


![dash1](https://github.com/user-attachments/assets/6e950e6d-0b71-46d8-bb3a-1645b6f1f907)

Parameter Controls
<details> <summary>Max Price Parameter</summary>
To enhance the flexibility of my analysis, I created a Max Price parameter in Power BI.
This allows users to dynamically filter LEGO sets by maximum price, making it easier to explore products within a specific budget.

## Parameter Controls

To enhance the flexibility of my analysis, I created a Max Price parameter in Power BI.
This allows users to dynamically filter LEGO sets by maximum price, making it easier to explore products within a specific budget.

<details>
<summary>Max Price Parameter</summary>

**Steps to create the Max Price parameter:**

1. Go to the **Modeling** tab in Power BI  
2. Click on **New Parameter → Numeric Range**

**Parameter Configuration:**

- **Name:** Max Price  
- **Data Type:** Whole Number  
- **Minimum Value:** 0  
- **Maximum Value:** 850  
- **Increment:** 5  
- **Default Value:** 850  

Once created, this parameter was linked to the price field in the dataset, allowing real-time updates to charts and tables based on the selected maximum price. It also connects seamlessly with card KPIs and visuals for dynamic filtering.
</details>


![dash2](https://github.com/user-attachments/assets/d4e100ca-aed9-4293-aa16-729e2d63938d)



