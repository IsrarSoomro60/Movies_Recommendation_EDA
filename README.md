# 🎬 Movies Recommendation — Exploratory Data Analysis

A beginner-friendly EDA notebook that loads, cleans, and explores a movie dataset (`Movies Recommendation.csv`) using **Pandas** and **Matplotlib**.

## 📂 Dataset Overview

- **Rows:** 4,760 movies
- **Columns:** 21 (title, genre, language, budget, popularity, release date, revenue, runtime, vote, vote count, homepage, keywords, overview, production house/country, spoken language, tagline, cast, crew, director)

## 🛠️ What This Notebook Does

### 1. Load & Inspect
- Reads the CSV with `pd.read_csv()`
- Uses `df.head()`, `df.shape`, `df.columns`, and `df.info()` to understand structure, data types, and non-null counts

### 2. Statistical Summary
- `df.describe()` for numeric columns (budget, popularity, revenue, runtime, vote, vote count)
- `df.describe(include='str')` for categorical/text columns (most frequent title, genre, director, etc.)

### 3. Handle Missing Values
- Checked missing values with `df.isna().sum()`
- Filled missing values in bulk:
  | Column | Fill Value |
  |---|---|
  | Movie_Director | "Unknown" |
  | Movie_Tagline | "No Tagline Available" |
  | Movie_Cast | "Unknown" |
  | Movie_Keywords | "" |
  | Movie_Homepage | "" |
- Manually researched and filled the remaining `Movie_Overview` (3 rows) and `Movie_Runtime` (2 rows) missing values using `df.loc[]`
- Verified the fixes and re-ran `describe()` to confirm the stats stayed consistent

### 4. Exploration & Filtering
- `df['Movie_Genre'].unique()` — listed all unique genre combinations
- `df.sort_values('Movie_Revenue', ascending=False)` — found top-grossing movies
- `df[df['Movie_Director'] == 'James Cameron']` — filtered movies by a specific director
- `df.iloc[...]` — row/column slicing examples (by position, by range, and by sorted index)

### 5. Outlier / Top-N Identification
- Extracted the **top 5 highest-grossing movies**: *Avatar, Titanic, The Avengers, Jurassic World, Furious 7*

### 6. Visualization
- Plotted a **pie chart** of the top 5 movies by revenue using `matplotlib.pyplot.pie()`

## 📦 Requirements

```bash
pip install pandas matplotlib
```

## ▶️ How to Run

1. Place `Movies Recommendation.csv` in the same directory as the notebook
2. Run all cells top to bottom in Jupyter Notebook / JupyterLab / VS Code
3. Check the final pie chart output for the top 5 revenue-generating movies

## 📌 Key Takeaways

- Most missing values were non-critical (homepage, tagline, keywords) and safely filled with placeholders
- Only 5 rows needed manual research to fill (`Movie_Overview`, `Movie_Runtime`)
- **Avatar** is the highest-grossing movie in the dataset (~$2.79B)
- **James Cameron** directed 2 of the top 5 highest-grossing films (Avatar, Titanic)
