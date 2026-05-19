# Yoga Retreat Market Analysis in Spain

## Data-Driven Business Proposal for Sadhanalaya Ashram

A data science project analyzing the Spanish yoga retreat market to identify which retreat features influence popularity and to provide strategic business recommendations for **Sadhanalaya Ashram**.

---

# Project Overview

This project investigates the relationship between retreat characteristics and retreat popularity using data collected from yoga retreat listings on:

[BookRetreats.com]

The project was developed as part of a Data Science & Machine Learning portfolio project using Python, statistical analysis, and business analytics techniques.

The analysis focuses on three primary business questions:

1. **Pricing Strategy**

   * How does price influence retreat popularity?
   * Is Sadhanalaya Ashram currently underpriced?

2. **Accommodation Strategy**

   * Does offering private rooms significantly increase popularity?
   * Is investing in private accommodation worthwhile?

3. **Retreat Duration**

   * Are shorter retreats more popular than long retreats?
   * Should Sadhanalaya introduce shorter retreat formats?

The objective was to combine:

* exploratory data analysis,
* hypothesis testing,
* statistical reasoning,
* and business interpretation

to generate actionable recommendations for a real retreat center.

---

# Dataset

### Source

* Platform: [BookRetreats.com]
* Country analyzed: **Spain**

### Dataset Scope

* Total yoga retreats available in Spain on platform: **522**
* Sample manually collected and analyzed: **50 retreats**

### Features Included

| Feature             | Description                         |
| ------------------- | ----------------------------------- |
| retreat_name        | Name of retreat                     |
| location            | Nature / Island / City              |
| min_price_usd       | Lowest advertised retreat price     |
| max_price_usd       | Highest advertised retreat price    |
| duration_days       | Retreat duration                    |
| class_count         | Number of class/activity categories |
| meals_included      | Meals included (0–3)                |
| accommodation_score | Accommodation category              |
| interested          | Number of users interested          |
| review_score        | Average review rating               |
| number_of_reviews   | Total reviews                       |

---

# Accommodation Encoding

Accommodation types were transformed into numerical scores:

| Score | Accommodation Type                           |
| ----- | -------------------------------------------- |
| 1     | Shared dorm only                             |
| 2     | Private rooms only                           |
| 3     | Shared + private rooms                       |
| 4     | Shared + private + alternative accommodation |

---

# Research Questions

## Price vs Popularity

* Does lower pricing increase retreat popularity?
* What is the average minimum daily price in the Spanish market?
* What pricing strategy should Sadhanalaya Ashram adopt?

## Accommodation Impact

* Does accommodation type significantly affect popularity?
* Is dorm-only accommodation a disadvantage?

## Retreat Length

* Are short retreats (2–4 days) more popular?
* Should Sadhanalaya introduce shorter retreats?

---

# 🛠 Technologies Used

## Programming & Analysis

* Python
* Pandas
* NumPy
* SciPy
* Matplotlib

## Data Science Techniques

* Exploratory Data Analysis (EDA)
* Correlation Analysis
* Feature Engineering
* Hypothesis Testing
* ANOVA Testing
* Independent T-Tests
* Confidence Interval Interpretation
* Statistical Visualization

## Visualization & Presentation

* Jupyter Notebook
* Google Colab
* Tableau Public
* PowerPoint

---

# 📈 Data Preparation & Feature Engineering

Several custom variables were created to improve analysis quality.

## Price Per Day

A new feature was engineered:

```python
df["price_per_day_usd"] = df["min_price_usd"] / df["duration_days"]
```

This normalized retreat prices by duration and allowed fair comparisons between retreats of different lengths.

---

## Log Popularity

Because the popularity variable (`interested`) was highly skewed, a logarithmic transformation was explored:

```python
df["log_interested"] = np.log(df["interested"] + 1)
```

This reduced the impact of extreme outliers and improved interpretability for some analyses.

---

## Retreat Length Groups

Retreats were grouped into categories for hypothesis testing:

```python
df["retreat_length_group"] = df["duration_days"].apply(
    lambda x: "Short (2-4 days)" if x <= 4 else "Long (5+ days)"
)
```

Additional 3-category grouping:

```python
def categorize_length(days):
    if days <= 4:
        return "Short (2-4)"
    elif days <= 6:
        return "Medium (5-6)"
    else:
        return "Long (7+)"

df["length_category"] = df["duration_days"].apply(categorize_length)
```

---

# Exploratory Data Analysis (EDA)

The project explored relationships between retreat features and popularity using:

* histograms,
* scatter plots,
* boxplots,
* grouped averages,
* and correlation matrices.

---

# Correlation Analysis

Correlation analysis revealed:

| Feature             | Correlation with Popularity |
| ------------------- | --------------------------- |
| price_per_day_usd   | Negative correlation        |
| meals_included      | Slight positive correlation |
| review_score        | Weak positive correlation   |
| class_count         | Weak positive correlation   |
| accommodation_score | Very weak correlation       |

### Main Insight

Price showed the strongest relationship with popularity.

Higher daily prices generally corresponded with lower interest levels.

---

# Pricing Analysis

## Market Positioning

The analysis compared:

* Sadhanalaya Ashram’s current daily price (€45/day),
* the market average,
* and the market median.

### Visualizations Created

* Price distribution histogram
* Demand curve scatter plot
* Regression trendline

---

## Key Finding

Sadhanalaya Ashram’s current price is significantly below market norms.

### Recommendation

Suggested positioning:

* **€75–€100 per day**

This keeps the retreat competitively affordable while improving sustainability and perceived value.

---

# 🛏 Accommodation Analysis

## Research Question

Does offering private accommodation significantly increase popularity?

---

## Statistical Method

ANOVA (Analysis of Variance)

```python
from scipy.stats import f_oneway
```

---

## Result

```python
p-value ≈ 0.85
```

This indicates:

* No statistically significant difference between accommodation types.

---

## Business Conclusion

Dormitory-style accommodation alone does **not significantly reduce popularity**.

### Recommendation

Private rooms may improve comfort and premium branding, but are not essential for initial market success.

---

# Retreat Length Analysis

## Research Question

Are short retreats more popular than long retreats?

---

## Statistical Method

Independent T-Test

```python
from scipy.stats import ttest_ind
```

---

## Grouping

| Category | Duration |
| -------- | -------- |
| Short    | 2–4 days |
| Long     | 5+ days  |

---

## Result

```python
p-value ≈ 0.59
```

No statistically significant difference was found between short and long retreats.

---

## Visualization

The project used:

* grouped bar charts,
* boxplots,
* and popularity distributions.

---

## Business Interpretation

Short retreats showed slightly higher median popularity, while long retreats showed larger variability with some very successful outliers.

### Recommendation

Sadhanalaya Ashram can confidently maintain its 7-day retreat format while optionally experimenting with shorter retreats.

---

# Statistical Concepts Applied

This project incorporated concepts from statistics and data science coursework:

## Samples vs Population

* Population: 522 retreats in Spain
* Sample: 50 manually collected retreats

## Central Limit Theorem (CLT)

Used to justify statistical inference on sample means.

## Confidence Intervals

Used to interpret likely ranges for market pricing.

## Hypothesis Testing

Applied through:

* ANOVA
* Independent T-tests

## Goodness of Fit & Distribution Analysis

Used through:

* histograms,
* skew analysis,
* and boxplots.

---

# Example Visualizations

The project includes:

* Price distribution histograms
* Demand curve analysis
* Popularity scatter plots
* Accommodation comparison charts
* Retreat duration boxplots
* Market positioning visuals

---

# Final Business Recommendations

| Business Question | Recommendation                                        |
| ----------------- | ----------------------------------------------------- |
| Pricing           | Increase daily pricing toward €75–€100                |
| Accommodation     | Dormitory model is acceptable                         |
| Retreat Length    | Maintain 7-day retreats while testing shorter formats |

---

# Project Structure

```bash
├── notebooks/
│   └── Retreat_Project_Data_Science.ipynb
│
├── presentation/
│   └── Sadhanalaya Data Driven Business proposal.pptx
│
├── requirements/
│   └── requirements.txt
│
├── data/
│   └── spain_retreats.csv
│
└── README.md
```

---

# Future Improvements

Potential future extensions:

* Web scraping automation
* Larger dataset collection
* Predictive machine learning models
* Sentiment analysis of retreat reviews
* Interactive Tableau dashboard
* Regression modeling
* Time-series market analysis


---

# Author

Adair Guijt
Data Science & Machine Learning Student
Business Analytics & Wellness Industry Research

---

# Acknowledgements

Special thanks to:

* Ironhack Data Science Bootcamp
* [BookRetreats.com]
* Sadhanalaya Ashram

for providing inspiration and data context for this project.
