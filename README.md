# Netflix EDA Analysis
> *Exploratroy data analysis of Netflix's content catalog - cleaning, analysing and visulaizing 8,807 Movies and TV shows to uncover trends in the content type, production countries, ratings and growth overtime.*

---

## ⚙️ Project Type Flags
> *Check what applies. This helps reviewers and collaborators understand the nature of the work at a glance. Delete this block before publishing.*

- [x] Exploratory Data Analysis (EDA)
- [ ] SQL Analysis / Querying
- [x] Dashboard / Data Visualization
- [ ] Data Pipeline / ETL
- [ ] Predictive Modelling / Machine Learning
- [x] Data Cleaning / Wrangling
- [ ] End-to-End (multiple of the above)
- [ ] Other: ___________

---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Repository Structure](#4-repository-structure)
5. [Data Workflow](#5-data-workflow)
6. [Analysis & Metrics](#6-analysis--metrics)
7. [Key Insights](#7-key-insights)
8. [Recommendations](#8-recommendations)
9. [Assumptions & Limitations](#9-assumptions--limitations)
10. [Future Enhancements](#10-future-enhancements)
11. [Deliverables](#11-deliverables)
12. [Author](#12-author)

---


## 1. Project Overview

**Context:** Netflix's catalog spans thousands of titles across countries, genres, and decades, but the raw dataset alone doesn't reveal patterns in how that catalog has grown or what it's made up of.

**Problem Statement:** What trends exist in Netflix's content library - by type, country of production, rating, and growth over time - and what do those trends suggest about the platform's content strategy?

**Approach:** Cleaned the raw dataset (handling missing values, duplicates, and formatting issues) in Python, then used pandas and visualizations to explore patterns in content type, production countries, ratings, and additions over time.

**Outcome:** A cleaned, analysis-ready dataset and a set of visual insights showing that movies (6,131) outnumber TV shows (2,666) by roughly 2-to-1, with content additions peaking in 2019 before declining slightly through 2021.

---


## 2. Objectives

- **Primary Objective:** Clean and explore the Netflix titles dataset to identify meaningful patterns in content type, country of origin, and audience ratings.

- **Secondary Objective 1:** Quantify the split between Movies and TV Shows in the catalog.
  
- **Secondary Objective 2:** Identify the leading content-producing countries.
  
- **Secondary Objective 3:**  Determine the most common content ratings and genres.

- **Secondary Objective 4:** Evaluate how the volume of titles added to Netflix has changed over time.
  
---

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|-----------|---------|
| **In Scope** | 8,807 Netflix titles covering show ID, title, type, director, cast, country, date added, release year, rating, duration, and genre |
| **Out of Scope** |Viewer engagement/streaming metrics, external ratings, or data on titles removed from the platform |
| **Time Period** | 2008 – 2020 |
| **Granularity** | Row-level data (one row per title) |

### Tools & Technologies

| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | Python (pandas) - handling missing values, duplicates, datetime conversion, text standardization
Data Analysis |
| Analysis | Python (pandas) - value_count, groupby, sorting |
| Visualization |Python (Matplotlib) |
| Documentation | Markdown, Github|

---

## 4. Repository Structure

```
Netflix-EDA-Analysis/
│
├── data/
│   └── raw/              # Original, unmodified Netflix dataset (netflix_titles.csv)
│
├── notebooks/            # Colab notebook with full cleaning, analysis, and visualizations
│
├── reports/              # Written summary report of findings
│
├── visuals/              # Exported charts and graphs
│
├── README.md             # You are here
└── project_metadata.yml  # Project metadata
```

---

## 5. Data Workflow

1. **Source:** Netflix titles dataset downloaded via kagglehub (source: shivamb/netflix-shows on Kaggle), containing 8,807 records with 12 columns.
2. **Ingestion:** Dataset read into a pandas DataFrame using pd.read_csv() with latin1 encoding to handle special characters in text fields.
3. **Cleaning:** - Filled missing values in director, cast, country, rating, and duration with "Unknown" to preserve as many records as possible.
   - Removed rows with missing date_added, since this field was essential for time-based analysis.
   - Checked for and confirmed no duplicate rows.
   - Converted date_added to datetime format and extracted year_added for trend analysis.
   - Standardized column names and text values to lowercase, removing unnecessary whitespace.
5. **Analysis:** Used pandas (value_counts, groupby, sort_index) to break down content by type, year added, release year, country, and rating.
6. **Output:** Built bar charts, pie charts, line charts, histograms, and box plots to illustrate the trends found in the analysis and summarized analysis report .


---

## 6. Analysis & Metrics

### Analytical Approach

This was primarily exploratory examining the cleaned dataset to uncover patterns in content type, growth over time, and audience ratings, rather than testing a specific hypothesis. Descriptive statistics and grouped counts were used to summarize the catalog's composition and trends.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|---------------------------|-----------------|
| `type distribution` | Count of titles by Movie vs. TV Show | Shows the overall composition of Netflix's catalog |
| `year_added counts` | Number of titles added to Netflix per calendar year | Reveals growth trends and peak content-acquisition periods |
| `country frequency` | Count of titles by producing country | Identifies which markets contribute most to the catalog |
| `rating distribution` | Count of titles by content rating (e.g., TV-MA, PG-13) | Indicates the intended audience maturity of the catalog |

### Methods Used

- Descriptive statistics - value counts, distribution, and central tendency (mean, min, max, standard deviation) for release year
- Trend analysis across year added (2008–2021)
- Segmentation / group  comparison by content type, country, and rating

---

## 7. Key Insights



**Insight 1: Movies dominate the catalog**
At 6,131 titles vs. 2,666 TV Shows, movies make up about 70% of Netflix's catalog in this dataset. This suggests Netflix's content strategy still leans heavily on film licensing/production even as TV Shows have grown as a category - useful context for anyone analyzing content investment priorities.

**Insight 2:  Content growth peaked in 2019, not the most recent year**
Additions rose sharply from 429 titles in 2016 to a peak of 2,016 in 2019, before declining to 1,879 (2020) and 1,498 (2021). This points to a slowdown in catalog expansion rather than continued acceleration - worth investigating whether this reflects licensing costs, a shift toward original content, or incomplete 2021 data in the source.

**Insight 3: Mature-audience content dominate the catalog**
TV-MA is the most common classification across titles and drama-related genres appears most frequently overall - together these suggest Netflix's catalog is weighted towards matures-audience rather than family-friendly or lighter content relevant for anyone assessing audience  targeting or content - acquisition strategy. 

**Insight 4: The United States is the leading content production country**
The U.S produces far more titles than any other count country, followed by India (972), and far ahead of the UK (419) nearly three times far than the U.S output. This  concentation suggests Netflix's  catalog, despite being a global platform, is still heavily anchored in America- product content with India standing out as the clearest secondary hub.

---

## 8. Recommendations

| Priority | Recommendation | Based On | Suggested Owner |
|----------|-----------------|----------|------------------|
| High | Investigate why content additions declined after the 2019 peak - determine if this reflects a strategic shift toward original productions, rising licensing costs, or incomplete data for 2021 | Insight 2 - growth peaked in 2019 | Content Strategy / Data team |
| Medium | Break down the movie-to-TV-show ratio by country to see if the 70/30 split holds globally or varies by region | Insight 1 - movie-heavy catalog | Content Acquisition team |
| Low | Extend the analysis to include genre-level trends over time for a fuller picture of catalog evolution | Insight 3 - concentration in recent years | Data Analytics team |
---

## 9. Assumptions & Limitations
### Assumptions
- The dataset was treated as a complete and accurate snapshot of Netflix's catalog at the time of extraction (via Kaggle), with no independent verification against Netflix's own records.
- Missing director, cast, country, and rating values were assumed to be genuinely missing/unlisted rather than data entry errors, and were filled with "Unknown" rather than dropped.

### Limitations
- The dataset only reflects titles available at one point in time - it does not capture titles that were removed from Netflix before or after this snapshot.
- No viewer engagement or streaming data is included, so popularity or performance of titles cannot be assessed — only catalog composition.
- The date_added field marks when a title was added to Netflix, not when it was actually produced or released, which limits precision when comparing production trends across countries.
---

## 10. Deliverables

| Deliverable | Description | Location |
|-------------|--------------|----------|
| Cleaned dataset | Netflix titles data with nulls handled, duplicates checked, and datetime fields formatted |  `data/raw/` |
| Analysis notebook | Full cleaning, analysis, and visualization code | notebooks/`Netflix_EDA_Analysis.ipynb` |
| Live notebook (Colab) | Interactive version, viewable/run directly in-browser | `https://colab.research.google.com/drive/1QX6vx8r_Wic1w4rT_OH2fMzlT4Nh90Sf`|
| Summary report | Written findings and insights | `reports/` |
| Visualizations | Charts illustrating key trends | `visuals/` |
---

## 11. Author

**Vivian Okwara | Lagos Nigeria**
Data Analyst

- 🔗 https://Linkedin.com/in/okwara-vivian
- 💼 https://Vivian-Portfolio.github.io
- 📧 okwaravivian26@gmail.com

---

*Last updated: July 2026*
