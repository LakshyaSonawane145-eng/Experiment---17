# Experiment 17 — Basic Charts and Visual Encoding in Python

**Name:** Lakshya Sonawane &nbsp;|&nbsp; **PRN:** 25070123068

---

## Introduction

Data Visualization is the graphical representation of data that helps us understand patterns, trends, and relationships quickly. Before diving into complex charts, it is essential to master the **basic chart types** — as they form the foundation of all data storytelling.

This experiment focuses on creating and interpreting four fundamental chart types — **Line Chart, Bar Chart, Histogram, and Scatter Plot** — using both **Matplotlib** (the base Python plotting library) and **Seaborn** (a higher-level, statistically-oriented library built on top of Matplotlib). The experiment also demonstrates how adding visual elements like color-coding, value labels, and mean lines can significantly improve chart readability.

---

## Requirements

```python
pip install matplotlib seaborn pandas numpy
```

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np
```

---

## Dataset Used

```python
data = {
    'Days': ['Mon', 'Tue', 'Wed', 'Thu', 'Fri'],
    'Study_Hours': [2, 3, 2.5, 4, 3.5],
    'Marks': [50, 60, 55, 70, 65],
    'Attendance': [60, 70, 65, 80, 75],
    'Sleep_Hours': [8, 7, 8, 6, 7],
    'Assignments_Completed': [1, 2, 1, 3, 2]
}
df = pd.DataFrame(data)
```

| Days | Study_Hours | Marks | Attendance | Sleep_Hours | Assignments_Completed |
|------|-------------|-------|------------|-------------|----------------------|
| Mon  | 2.0         | 50    | 60         | 8           | 1                    |
| Tue  | 3.0         | 60    | 70         | 7           | 2                    |
| Wed  | 2.5         | 55    | 65         | 8           | 1                    |
| Thu  | 4.0         | 70    | 80         | 6           | 3                    |
| Fri  | 3.5         | 65    | 75         | 7           | 2                    |

---

## Theory & Commands

### 1. Line Chart

A line chart connects data points with a line. It is best used to show **trends over time** or continuous data. Multiple lines can be plotted on the same chart for comparison.

**Basic Line Chart:**

```python
plt.plot(df['Days'], df['Study_Hours'], marker='*')
plt.title('Study Hours Over Days')
plt.xlabel('Days')
plt.ylabel('Study Hours')
plt.show()
```

**Advanced — Multiple Lines (Matplotlib):**

```python
plt.figure(figsize=(7, 4))
plt.plot(df['Days'], df['Study_Hours'], marker='o', color='blue', label='Study Hours')
plt.plot(df['Days'], df['Marks'], marker='o', color='red', label='Marks')
plt.title('Line Graph')
plt.xlabel('Days')
plt.ylabel('Values')
plt.legend()
plt.show()
```

**Using Seaborn:**

```python
sns.lineplot(x='Day', y='Sales', data=df)
plt.title('Sales Over Days')
plt.show()
```

> **When to use:** Trends over time, comparing two variables across the same axis.

---

### 2. Bar Chart

A bar chart uses rectangular bars to compare values across **categories**. The height of each bar represents the value.

**Basic Bar Chart:**

```python
plt.bar(df['Days'], df['Marks'], color='green')
plt.title('Marks Over Days')
plt.xlabel('Days')
plt.ylabel('Marks')
plt.show()
```

**Advanced — Bar Chart with Value Labels and Grid:**

```python
bars = plt.bar(df['Days'], df['Marks'], color='red')
for bar in bars:
    yval = bar.get_height()
    plt.text(bar.get_x() + bar.get_width() / 2, yval,
             str(yval), ha='center', va='bottom')
plt.title('Marks Over Days')
plt.xlabel('Days')
plt.ylabel('Marks')
plt.grid(axis='y')   # horizontal gridlines for readability
plt.show()
```

**Using Seaborn:**

```python
sns.barplot(x='Day', y='Profit', data=df)
plt.title('Profit Over Days')
plt.show()
```

> **When to use:** Comparing distinct categories (e.g., sales by region, marks by subject).

---

### 3. Histogram

A histogram shows the **distribution (frequency) of a single numerical variable** by grouping values into intervals called **bins**. Unlike bar charts, histogram bars touch each other — there are no gaps.

**Basic Histogram:**

```python
plt.hist(df['Marks'], bins=3, edgecolor='black', alpha=0.3)
plt.title('Marks Distribution')
plt.xlabel('Marks')
plt.ylabel('Frequency')
plt.show()
```

**Advanced — Histogram with Mean Line:**

```python
import numpy as np

marks = [50, 60, 55, 70, 65, 75, 80, 85, 90, 45, 68, 72, 77, 82, 88]
mean_value = np.mean(marks)

plt.figure(figsize=(6, 4))
plt.hist(marks, bins=6, edgecolor='skyblue', alpha=0.7)
plt.axvline(mean_value, color='red', linestyle='dashed', linewidth=2)
plt.title('Marks Distribution with Mean')
plt.xlabel('Marks')
plt.ylabel('Frequency')
plt.grid(axis='y', linestyle='--', alpha=0.5)
plt.show()
```

**Using Seaborn:**

```python
sns.histplot(df['Sales'], bins=5)
plt.title('Sales Distribution')
plt.show()
```

> **When to use:** Understanding how data is distributed — symmetric, skewed, or spread out.

---

### 4. Scatter Plot

A scatter plot plots individual data points on a 2D plane to show the **relationship (correlation) between two numerical variables**. It helps identify positive correlation, negative correlation, or no correlation.

**Basic Scatter Plot:**

```python
plt.scatter(df['Study_Hours'], df['Marks'], color='orange')
plt.title('Study Hours vs Marks')
plt.xlabel('Study Hours')
plt.ylabel('Marks')
plt.show()
```

**Advanced — Conditional Color Scatter (Pass/Fail):**

```python
df['Result'] = ['Fail', 'Pass', 'Pass', 'Pass', 'Fail']
colors = {'Fail': 'red', 'Pass': 'green'}

plt.scatter(df['Study_Hours'], df['Marks'], c=df['Result'].map(colors))
plt.title('Study Hours vs Marks (Pass/Fail)')
plt.xlabel('Study Hours')
plt.ylabel('Marks')
plt.show()
```

**Using Seaborn:**

```python
sns.scatterplot(x='Sales', y='Profit', data=df)
plt.title('Sales vs Profit')
plt.show()
```

> **When to use:** Finding relationships or correlation between two variables; detecting outliers.

---

## Matplotlib vs Seaborn — Comparison

| Feature | Matplotlib | Seaborn |
|---|---|---|
| Type | Base library | Built on Matplotlib |
| Code length | More verbose | Shorter, cleaner |
| Default style | Basic | More attractive |
| Statistical features | Manual | Built-in |
| Best for | Full control over plots | Quick, beautiful statistical charts |

---

## Chart Selection Guide

| Chart Type | Best Used For | Function |
|---|---|---|
| Line Chart | Trends over time | `plt.plot()` / `sns.lineplot()` |
| Bar Chart | Comparing categories | `plt.bar()` / `sns.barplot()` |
| Histogram | Distribution of one variable | `plt.hist()` / `sns.histplot()` |
| Scatter Plot | Relationship between two variables | `plt.scatter()` / `sns.scatterplot()` |

---

## Conclusion

This experiment demonstrated the creation and interpretation of four fundamental chart types using Matplotlib and Seaborn:

- **Line Charts** effectively visualize trends over time and support multi-line comparison for different variables.
- **Bar Charts** enable clear comparison across categories; adding value labels and gridlines significantly improves readability.
- **Histograms** reveal the distribution of a single variable — adding a mean line further highlights the central tendency of the data.
- **Scatter Plots** show relationships between two numerical variables and can be enhanced with conditional coloring to encode a third categorical variable.

Seaborn consistently produces more visually appealing plots with less code, while Matplotlib provides greater flexibility and control over every chart element. Together, these basic charts form the foundation for all advanced data visualization techniques.

---

## Libraries Used

| Library | Purpose |
|---|---|
| `matplotlib.pyplot` | Core plotting — all basic charts |
| `seaborn` | Statistical, attractive chart variants |
| `pandas` | DataFrame creation and data handling |
| `numpy` | Numerical computations (mean, arrays) |
