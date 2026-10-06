# 🏍️ BikeWale Bike Analytics | Web Scraping, Python EDA & Power BI

**Analysis on finding the best bikes in India based on their features.**

An end-to-end data analytics project that collects bike/model data from **BikeWale**, cleans it with **Python (Pandas)**, explores it through **EDA and visualizations**, ranks bikes with a transparent **Best Bike Score**, and presents the results in an interactive **Power BI** dashboard.

<img width="1532" height="862" alt="Screenshot 2026-10-06 185954" src="https://github.com/user-attachments/assets/af6d6298-8ec2-4526-a67f-aba354729125" />

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives & Business Questions](#-objectives--business-questions)
- [Tools & Technologies](#-tools--technologies)
- [Data Collection](#-data-collection)
- [Dataset & Data Dictionary](#-dataset--data-dictionary)
- [Data Cleaning & Preparation](#-data-cleaning--preparation)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Best Bike Scoring Model](#-best-bike-scoring-model)
- [Power BI Dashboard](#-power-bi-dashboard)
- [Key Results](#-key-results)
- [Business Recommendations](#-business-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Run](#-how-to-run)
- [Future Scope](#-future-scope)
- [Author](#-author)

---

## 📖 Project Overview

A bike marketplace holds a lot of product information that can be turned into useful insight. This project organizes bike data into a structured table and compares models on **price, mileage, engine capacity, power, torque, weight, user rating and ratings count**.

**Workflow:** Website Selection → Data Collection → Data Understanding → Data Cleaning → EDA → Visualization → Insights & Recommendations → Power BI Dashboard

> **Scope:** Conclusions apply only to the bikes and fields in the collected dataset. The Best Bike Score is a project-specific model, not a universal definition of the "best" motorcycle.

---

## 🎯 Objectives & Business Questions

- Which brands have the largest representation?
- How does average price vary by brand?
- How are bikes distributed across price categories?
- How does price relate to mileage and power?
- How does engine CC relate to power?
- Which bikes have the highest power, the most ratings and the best ratings?
- Which bikes score highest under the project scoring model?

---

## 🧰 Tools & Technologies

| Tool | Purpose |
|---|---|
| **Python** (Requests, BeautifulSoup) | Web scraping of BikeWale model pages |
| **Pandas, NumPy** | Data cleaning and analysis |
| **Matplotlib, Seaborn** | EDA visualizations |
| **Google Colab** | Notebook environment |
| **Power BI Desktop** | Interactive dashboard |

---

## 🌐 Data Collection

BikeWale was used as the data source. The collection workflow targeted **individual bike/model pages**, so each record represents a specific model rather than a brand or category page. Requests retrieved the web content, BeautifulSoup parsed it, and Pandas organized it into a table that was saved as a **raw CSV** before cleaning. Keeping the raw and cleaned datasets separate makes the cleaning process traceable.

---

## 🗂 Dataset & Data Dictionary

| Column | Type | Description |
|---|---|---|
| Bike Name | Text | Bike / model name |
| Brand | Categorical | Brand of the model (extracted from the model URL) |
| Price | Numeric | Bike price (₹) |
| Rating | Numeric | User rating (0–5) |
| Ratings Count | Numeric | Number of ratings |
| Mileage | Numeric | Mileage value |
| Engine CC | Numeric | Engine displacement |
| Power BHP | Numeric | Power |
| Torque Nm | Numeric | Torque |
| Weight KG | Numeric | Weight |
| Price Category | Categorical | Budget, Mid-Range, Premium or Luxury |
| Engine CC Category | Categorical | Engine displacement grouping |
| URL | Text | Source / model URL |

**Derived categories**

| Price Category | Range |
|---|---|
| Budget | Below ₹1,00,000 |
| Mid-Range | ₹1,00,000 to below ₹2,00,000 |
| Premium | ₹2,00,000 to below ₹3,00,000 |
| Luxury | ₹3,00,000 and above |

**Engine CC Category:** Below 125 CC · 125–199 CC · 200–299 CC · 300–499 CC · 500+ CC

---

## 🧹 Data Cleaning & Preparation

- Removed completely empty rows, duplicate Bike Name records and records without a Bike Name
- Cleaned Price and Ratings Count
- Converted Rating, Engine CC, Mileage, Power BHP, Torque Nm and Weight KG to numeric
- Invalidated ratings outside the 0–5 range and handled non-positive numeric values
- Extracted **Brand** from the model URL
- Created **Price Category** and **Engine CC Category**
- Re-checked missing values, duplicates and dataset shape, then reordered the final columns

---

## 📈 Exploratory Data Analysis

The notebook (`Bike Wale Web Scrapping.ipynb`) covers:

| Analysis | Chart |
|---|---|
| Bikes by Brand | Bar |
| Average Price by Brand | Bar |
| Price vs Mileage | Scatter |
| Price vs Power | Scatter |
| Engine CC vs Power | Scatter |
| Engine CC Distribution | Bar |
| Price Category Distribution | Pie |
| Average Mileage by Brand | Bar |
| Top 10 Bikes by Power | Horizontal bar |
| Top 10 Most Reviewed Bikes | Horizontal bar |
| Top 10 Rated Bikes | Horizontal bar |
| Correlation Matrix (Price, Rating, Ratings Count, Engine CC, Mileage, Power, Torque, Weight) | Heatmap |

> Correlation shows linear relationships within this sample and does not establish causation.

---

## 🏆 Best Bike Scoring Model

A weighted score combines four normalized factors:

| Factor | Weight | Normalization |
|---|:---:|---|
| Rating | 30% | Value ÷ max (higher is better) |
| Mileage | 25% | Value ÷ max (higher is better) |
| Power | 20% | Value ÷ max (higher is better) |
| Price | 25% | Inverse min-max (lower price scores higher) |

```
Best Bike Score = 0.30 × Rating Score + 0.25 × Mileage Score
                + 0.20 × Power Score  + 0.25 × Price Score
```

Changing the weights changes the ranking, so the score is best treated as a transparent analytical framework that can be adjusted to different priorities.

---

## 📊 Power BI Dashboard

The Power BI report (`Bike Wale power BI desktop.pbix`) has two pages.

### Page 1: Executive Overview
KPI cards (Total Bikes, Average Price, Average Mileage, Average Engine CC, Average Rating), Price vs Mileage, Price vs Power, Bikes by Brand, Average Price by Brand, and slicers for **Brand**, **Price Range** and **Engine CC Range**.

📷 Screenshot file: `images/Screenshot 2026-10-06 185954.png`

<img width="1532" height="862" alt="Screenshot 2026-10-06 185954" src="https://github.com/user-attachments/assets/02797275-666d-4940-ade5-35db51163c92" />

### Page 2: Bike Analysis
Engine CC Distribution, Price Category Analysis, Average Mileage by Brand, Top 10 Bikes by Power, Top 10 Most Reviewed Bikes and Top 10 Rated Bikes.

📷 Screenshot file: `images/Screenshot 2026-10-06 190014.png`


---

## 🔑 Key Results

Figures below are taken from the Power BI dashboard with no filters applied.

| KPI | Value |
|---|---|
| Total Bikes | 50 |
| Average Price | ₹248.39K |
| Average Mileage | 50.13 |
| Average Engine CC | 278.15 |
| Average Rating | 3.78 |

**Highlights**

- **Brand representation:** TVS (10), Royal Enfield (7), Honda (6), Bajaj (5) and Hero (5) have the most models.
- **Price positioning:** Norton has the highest average price (~₹4.0M), followed by BMW and Royal Enfield (~₹1.7M each).
- **Price segments:** Budget 38% (19), Mid-Range 36% (18), Premium 14% (7), Luxury 12% (6).
- **Engine size:** 20 bikes are below 125 CC, the largest group; only 2 fall in 200–299 CC.
- **Efficiency:** Hero has the highest average mileage (~71), followed by Bajaj (~61) and TVS (~55).
- **Power:** Norton Manx and Manx R lead at 206 BHP, followed by BMW R nineT Racer (107 BHP).
- **Feedback volume:** Honda SP 125 (~4.5K) and Honda Activa (~4.3K) have the most ratings.
- **Top rated:** Ather Konarc leads with a rating of 4.8.

---

## 💡 Business Recommendations

- Use **price categories** for budget-oriented exploration and **engine categories** for displacement-based filtering.
- Read **rating together with ratings count**, since a high rating from few reviews is less reliable.
- Compare **power vs. mileage** to understand the performance-versus-efficiency trade-off.
- Use the Power BI filters to explore a specific brand, price range or engine range.
- Adjust the scoring weights when business priorities change.

> These recommendations come from the analytical structure of the project and do not replace current market verification.

---

## 📁 Repository Structure

```
├── Bike Wale Web Scrapping.ipynb          # Python notebook: cleaning checks, EDA, scoring
├── Bike Wale power BI desktop.pbix        # Power BI dashboard
├── BikeWale_Vehicle_Dataset.csv           # Raw dataset
├── BikeWale_Cleaned_Data_.csv             # Cleaned dataset
├── BikeWale_Project_Documentation.docx    # Full project documentation
├── README.md
└── images/
    ├── Screenshot 2026-10-06 185954.png   # Power BI: Executive Overview
    └── Screenshot 2026-10-06 190014.png   # Power BI: Bike Analysis
```

---

## ▶️ How to Run

**Python notebook**
1. Open `Bike Wale Web Scrapping.ipynb` in [Google Colab](https://colab.research.google.com/).
2. Upload the raw and cleaned CSV files to the Colab session (`/content/`) and update the file names in the notebook's first cells if they differ.
3. Run all cells to reproduce the EDA, correlation matrix, Best Bike Score and final dataset export.

**Power BI**
1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
2. Open `Bike Wale power BI desktop.pbix` and explore using the Brand, Price Range and Engine CC Range slicers.

```bash
pip install pandas numpy matplotlib seaborn
```

---

## 🚀 Future Scope

- Automate periodic data collection and refresh
- Add historical price tracking and more models and brands
- Power BI drill-through pages and a direct bike comparison feature
- Experiment with alternative scoring weights
- Machine learning for price or rating prediction when enough data is available

---

## 👤 Author

**Abhinav Yadav**

Skills demonstrated: Python · Web Scraping · Pandas · EDA · Data Visualization · Power BI · Business Insights

⭐ If you found this project useful, consider giving the repository a star!
