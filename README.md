# 🎬 Netflix Insights — Power BI Analytics Dashboard

A complete end-to-end data analysis project built with **Power BI**, focused on uncovering strategic insights from the Netflix Movies & TV Shows dataset.

---

# 📌 1. Project Overview

This project analyzes Netflix’s global content library to understand trends in production, ratings, genres, and geographic distribution.
The dashboard answers key business questions such as:

* How is Netflix expanding its content over time?
* Which countries contribute the most content?
* What genres dominate the platform?
* How do ratings and content types (Movie/TV Show) vary?
* What patterns exist in release years and audience categories?

This project demonstrates full-cycle **data cleaning → data modeling → DAX → visualization → insights**.

---

# 📁 2. Project Files

| File                                | Description                 |
| ----------------------------------- | --------------------------- |
| **Netflix_Insights_Dashboard.pbix** | Complete Power BI dashboard |
| **README.md**                       | Project documentation       |

---

# 🧰 3. Tools & Technologies Used

* **Power BI Desktop**
* **Power Query**
* **DAX (Data Analysis Expressions)**
* **Netflix Movies & TV Shows Dataset (CSV)**
* **Data Modelling Best Practices**

---

# 🧼 4. Data Cleaning (ETL) — Performed in Power Query

### ✔ Steps Applied

* Removed duplicates
* Replaced nulls and cleaned inconsistent values
* Standardized text fields (trim, lowercase, formatted)
* Converted `date_added` to proper Date type
* Extracted:

  * **Primary Genre** from `listed_in`
  * **Year**, **Month**, **Day** from `date_added`
* Split multi-valued fields: `cast`, `director`, `listed_in`
* Standardized country names
* Removed leading/trailing spaces
* Ensured correct data types for all columns

---

# 🧾 5. Data Dictionary (Important Columns)

| Column                        | Description                              |
| ----------------------------- | ---------------------------------------- |
| `type`                        | Movie or TV Show                         |
| `title`                       | Name of the content                      |
| `director`                    | Director(s) involved                     |
| `cast`                        | Actors involved                          |
| `country`                     | Country of production                    |
| `date_added`                  | Date content was added to Netflix        |
| `release_year`                | Year the content was released            |
| `rating`                      | Audience rating (TV-MA, PG, etc.)        |
| `duration`                    | Duration (minutes or number of seasons)  |
| `listed_in`                   | Genres                                   |
| `description`                 | Summary of the content                   |
| **Calculated: Primary Genre** | First genre extracted for classification |

---

# 🧱 6. Data Modeling

The data model follows Star Schema principles.

### ✔ Tables

* **Fact Table** — Netflix raw dataset
* **Supporting calculated columns**:

  * Primary Genre
  * Release Year hierarchy
  * Country normalized

### ✔ Slicers

* Type
* Genre
* Country
* Rating
* Year

This improves filtering performance and enables flexible exploration.

---

# 🧮 7. DAX Measures Used

### **Key KPIs**

```DAX
Total Titles = COUNTROWS('Netflix')

Total Movies = CALCULATE(
    COUNTROWS('Netflix'),
    'Netflix'[type] = "Movie"
)

Total TV Shows = CALCULATE(
    COUNTROWS('Netflix'),
    'Netflix'[type] = "TV Show"
)
```

### **Content by Year**

```DAX
Titles By Year = COUNTROWS('Netflix')
```

### **Percentage Contribution**

```DAX
Movie % = DIVIDE([Total Movies], [Total Titles])
TV Show % = DIVIDE([Total TV Shows], [Total Titles])
```

Additional measures built for YoY growth, category composition, and rating segmentation.

---

# 📊 8. Dashboard Walkthrough

### **📌 Page 1 — Overview**

* Total Titles
* Movie vs TV Show comparison
* Titles added per year
* Rating distribution
* Global content distribution
* Top contributing countries

### **📌 Page 2 — Genre Analysis**

* Popular genres
* Genre composition
* Heatmap for Genre × Type
* Genre-level filtering

### **📌 Page 3 — Country Insights**

* World Map visual
* Top 10 producing countries
* Year-wise country breakdown
* Country-level filters

### **📌 Page 4 — Detailed Explorer**

* Full dataset browser
* Slicers for:

  * Genre
  * Type
  * Rating
  * Year
  * Country

---

# 🔍 9. Key Insights & Findings

### ✔ Content Trends

* Huge surge in content released **after 2010**.
* Netflix added the highest number of titles between **2016–2020**.

### ✔ Content Type

* **Movies dominate** the platform compared to TV Shows.

### ✔ Ratings

* **TV-MA** is the most common rating → Netflix focuses on mature audiences.

### ✔ Geographic Pattern

* **USA**, **India**, and **UK** contribute the highest number of titles.
* Strong global distribution across 120+ countries.

### ✔ Genres

* Most common genres:

  * **Dramas**
  * **Comedies**
  * **Documentaries**
  * **International Movies**

---

# ❓ 10. Business Questions Answered

* Which genres are most popular?
* Which countries produce the most Netflix content?
* What is the distribution of Movies vs TV Shows?
* How has Netflix’s content catalog grown over time?
* What ratings dominate the platform?
* Which years had the most releases?
* What type of content do individual countries specialize in?

---

# 🚀 11. Future Improvements

* Add sentiment analysis using content description
* Build predictive model for future content growth
* Separate dataset for more detailed demographic insights
* Add cast/director network graph visual
* Integrate external data (IMDb ratings)

---

# ⚠️ 12. Limitations

* Country field sometimes contains multiple values
* Dataset does not include viewership numbers
* Dataset is static and not updated regularly
* No financial or revenue-related information

---

# 👨‍💻 13. Author

**Muhammad Mathin**
Power BI • SQL • Python • Analytics & Visualization

---

# ⭐ 14. Support

If you find this project useful, please star ⭐ the repository on GitHub and share your feedback!

---
