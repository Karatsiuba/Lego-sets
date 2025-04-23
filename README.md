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

•Identifying trends in set size, complexity, and pricing

•Recognizing which themes and categories gained popularity over time

•Supporting data-driven decisions for inventory, marketing, and collection planning

## Approach & Insights
🧼 Data Preparation:
The dataset — covering over 18,000 LEGO sets from 1970 to 2022 — was cleaned and structured to ensure reliable analysis. Missing values were handled, columns were standardized, and data types were adjusted where necessary.

🔎 Exploratory Analysis:
I explored core metrics such as average piece count per set, theme popularity over time, pricing patterns, and the relationship between set size and cost. This phase helped shape the visuals and guide the story behind the data.

📊 Dashboard Design:
Using Power BI, I built an interactive dashboard with slicers, custom tooltips, navigation features, and decomposition trees. Each visual was designed to support intuitive exploration and highlight meaningful trends.

🧠 Key Insights:
Over the years, LEGO sets have become larger and more intricate, with standout themes like Star Wars and Technic continuing to shine — and when it comes to pricing, it’s not just about size, but also age range, branding, and theme.
![image](https://github.com/user-attachments/assets/6745830a-9e93-40bb-bf49-28207854d54c)





Created a new conditional column called `Age Range`, which grouped sets into age-based categories:
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

Created another conditional column named `Price Range`, to classify sets by cost using dollar signs:
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




![dash](https://github.com/user-attachments/assets/62a10471-8fd5-4087-989a-9d3d138e804c)

