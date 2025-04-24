# LEGO-sets
This is an interactive Power BI dashboard for exploring the evolution of LEGO sets over the past 50 years 📊

## About My Project
This project is my personal take on the story behind LEGO — not just as a toy, but as a cultural phenomenon. I wanted to explore how LEGO sets have changed over the past 50 years: the themes we loved, the complexity we faced, and how prices evolved. My goal was to build something interactive and insightful — not just for data nerds, but for collectors, casual fans, and curious minds alike.

### 🎯 Project Goals
- Visualize how LEGO themes have shifted over time  
- Track changes in set sizes and pricing  
- Explore the relationship between piece count and price  
- Create an intuitive, interactive dashboard that makes data exploration fun and simple

### 💼 Business Needs
LEGO has grown into one of the most iconic toy brands in the world. By analyzing trends in themes, pricing, and build complexity, this project uncovers valuable insights for nostalgic collectors and modern-day enthusiasts.

### Approach & Insights
#### 🧼 Data Preparation
The dataset — covering over 18,000 LEGO sets from 1970 to 2022 — was cleaned and structured in Power Query. Null values were removed, unnecessary columns were dropped, and types were corrected.

#### 🔎 Exploratory Analysis
Key metrics explored: average piece count, price distribution, theme popularity, and relationships between age recommendation and cost.

#### 📊 Dashboard Design
Power BI was used to build an interactive dashboard with:
- Slicers for filtering by age range, theme, and price  
- KPI cards displaying total sets, average price and pieces  
- A detailed table of LEGO sets  
- Custom tooltips showing thumbnails on hover  
- A dedicated product detail section for each selected set

#### 🧠 Key Insights
LEGO sets have become more detailed and expensive. Themes like Star Wars and Technic remain dominant, and price is driven by more than just piece count.

---

## 📥 Steps to Complete the LEGO Sets Project

### 1. Data Acquisition
- Dataset downloaded from [Maven Analytics]
- Over 18,000 LEGO sets
- Structure reviewed before loading into Power BI

### 2. Importing into Power BI
- Used “Get Data” to load dataset  
- Opened Power Query for cleaning and transformation

### 3. Data Transformation in Power Query
- Removed nulls and empty rows  
- Renamed columns for readability  
- Changed data types for `age` and `price`  
- Created conditional columns:

<details>
<summary>📘 Age Range</summary>

- **Over** – 18+  
- **10 to 17** – older children & teens  
- **5 to 9** – younger builders  
- **1 to 4** – toddlers  

</details>

<details>
<summary>💲 Price Range</summary>

- **$$$$$** – over $500  
- **$$$$** – $100 to $500  
- **$$$** – $50 to $100  
- **$$** – $5 to $50  
- **$** – under $5  

</details>

---

## 🧮 DAX Measures & Calculations

All DAX measures were stored in a dedicated `Measure Table` using the "Enter Data" feature.

### Core Measures

<details>
<summary>Total Sets</summary>

```DAX
Total Sets = DISTINCTCOUNT(lego_sets[set_id])
```
</details>

<details>
<summary>Total Theme Groups</summary>

```DAX
Total Groups = DISTINCTCOUNT(lego_sets[themeGroup])
```
</details>

<details>
<summary>Average Age</summary>

```DAX
Avg. Age = AVERAGE(lego_sets[age])
```
</details>

<details>
<summary>Average Pieces</summary>

```DAX
Avg. Pieces = AVERAGE(lego_sets[pieces])
```
</details>

<details>
<summary>Average Price</summary>

```DAX
Avg. Price = AVERAGE(lego_sets[price])
```
</details>

<details>
<summary>Max Price Filter</summary>

```DAX
Max Price Filter = IF([Avg. Price] <= 'Max Price'[Max Price Value], 1, 0)
```
</details>

### 🧠 Dynamic Selection Measures

<details>
<summary>Selected Set</summary>

```DAX
Selected Set = IF(HASONEVALUE(lego_sets[name]), MAX(lego_sets[name]), "Select a Set")
```
</details>

<details>
<summary>Selected Price</summary>

```DAX
Selected Price = IF(HASONEVALUE(lego_sets[price]), MAX(lego_sets[price]), "-")
```
</details>

<details>
<summary>Selected Pieces</summary>

```DAX
Selected Pieces = IF(HASONEVALUE(lego_sets[pieces]), MAX(lego_sets[pieces]), "-")
```
</details>

<details>
<summary>Selected Year</summary>

```DAX
Selected Year = IF(HASONEVALUE(lego_sets[year]), MAX(lego_sets[year]), "-")
```
</details>

<details>
<summary>Selected Age</summary>

```DAX
Selected Age = IF(HASONEVALUE(lego_sets[age]), MAX(lego_sets[age]), "-")
```
</details>

---

## 🧮 Parameter Controls

<details>
<summary>Max Price Parameter</summary>

- **Type:** Numeric Range  
- **Min:** 0  
- **Max:** 850  
- **Step:** 5  
- **Default:** 850  

Used to dynamically filter the table by max retail price.
</details>

---

## ✨ Visual Enhancements

### Custom Image Tooltips

When hovering over a table row, users see a preview of the LEGO set.

- Implemented with a separate report page (`Thumbnail`)  
- Tooltip type set to report page  
- Displays image from URL

### Product Detail View

- A dynamic card updates when a set is selected  
- Shows: image, name, price, year, pieces, age  
- Uses `HASONEVALUE()` DAX logic to avoid incorrect aggregation when multiple sets are selected

---

## 📈 Set Explorer (Decomposition Tree)

To provide deeper insights into set distributions, I added a `Set Explorer` page.

- Uses the **Decomposition Tree** visual  
- Explains `Total Sets` by:
  - Category → Theme Group → Theme → Name
- Allows drill-down exploration to find patterns and theme popularity

This page adds a powerful and intuitive breakdown tool for interactive storytelling.

---

## 🔁 Navigation Features

- Buttons allow seamless navigation between pages (`Main`, `Set Explorer`)  
- “Reset Filters” uses bookmarks to clear slicers and reset parameters  
- Interactive cards and slicers give full control over analysis

---

### Final Thoughts

This dashboard is more than a data viz — it’s a playful and powerful way to explore decades of creativity. Whether you're a LEGO fan or a BI pro, it’s proof that even bricks can tell stories.
