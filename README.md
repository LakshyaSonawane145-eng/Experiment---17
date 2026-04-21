# Experiment 17 — Basic Charts and Visual Encoding

**Name:** Lakshya Sonawane &nbsp;|&nbsp; **PRN:** 25070123068

---

## 📌 Introduction

Data visualization is the graphical representation of data to identify trends, patterns, and outliers. This experiment covers the four fundamental chart types — **Line, Bar, Histogram, and Scatter** — using **Matplotlib** and **Seaborn** on a student academic performance dataset and a regional sales dataset.

---

## 📖 Theory

### 1. Line Chart — Trend Visualization
- Displays data as points connected by lines; best for trends over ordered/time-based categories
- Multiple lines plotted using `plt.plot()` with `marker`, `color`, and `label` parameters
- `plt.legend()` distinguishes each line; `plt.show()` renders the final output

### 2. Bar Chart — Categorical Comparison
- Rectangular bars represent discrete category values; height is proportional to the value
- Drawn using `plt.bar()`; value labels added above each bar using `plt.text()` with `bar.get_height()`
- `plt.grid(axis='y')` adds horizontal gridlines for easier reading

### 3. Histogram — Frequency Distribution
- Shows the distribution of a continuous variable by grouping values into bins
- Created with `plt.hist()` using `bins`, `edgecolor`, and `alpha` for shape and transparency
- A mean line overlaid using `plt.axvline(np.mean(marks), color='red', linestyle='dashed')` marks central tendency

### 4. Scatter Plot — Relationship Between Variables
- Each point represents one observation plotted across two numerical axes
- Drawn with `plt.scatter()`; a third categorical dimension (e.g., Pass/Fail) added via `df['Result'].map(colors)` passed to the `c` parameter

### 5. Seaborn Equivalents
- Seaborn offers cleaner syntax and better default aesthetics built on top of Matplotlib
- `sns.lineplot()`, `sns.barplot()`, `sns.histplot()`, `sns.scatterplot()` accept DataFrame columns directly via `x`, `y`, and `data` parameters

---

## ✅ Conclusion

- The four core chart types were successfully implemented in both Matplotlib and Seaborn
- Matplotlib provides granular control; Seaborn offers concise, statistically enriched output
- Selecting the correct chart type based on data structure is foundational to exploratory data analysis
