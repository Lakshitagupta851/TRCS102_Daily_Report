DAY 14 OF TRAINING
## Python Data Visualization — Matplotlib & Seaborn

Welcome to this session of **Industrial Training for AI & Machine Learning**!

In this session, we explored **Data Visualization** using **Matplotlib** and **Seaborn**. Data visualization helps us represent data graphically, making it easier to understand patterns, trends, comparisons, and relationships. It plays a vital role in Data Analysis, Data Science, and Machine Learning.

---

# Learning Objectives

By the end of this session, you will be able to:

- Understand the importance of Data Visualization.
- Create different types of plots using Matplotlib.
- Learn basic visualization using Seaborn.
- Interpret graphical data effectively.
- Apply visualization techniques in Machine Learning projects.

---

# What is Data Visualization?

**Data Visualization** is the graphical representation of data using charts and graphs. It helps us identify trends, patterns, and relationships that are difficult to observe from raw data.

### Installing Required Libraries

```python
pip install matplotlib
pip install seaborn
```

### Importing Libraries

```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np
```

---

# 1. Line Plot

A **Line Plot** is used to display data that changes over time. The data points are connected using straight lines.

```python
import matplotlib.pyplot as plt

days = [1,2,3,4,5]
speed = [10,25,45,70,95]

plt.plot(days, speed, marker='o')
plt.title("Speed Over Days")
plt.xlabel("Days")
plt.ylabel("Speed")
plt.grid(True)

plt.show()
```

### Output

A line graph showing the increase in speed over five days.

---

# 2. Bar Plot

A **Bar Plot** compares different categories using rectangular bars.

```python
import matplotlib.pyplot as plt

treats = ["Chocolate","Cookies","Ice Cream","Candy"]
count = [15,22,12,18]

plt.bar(treats, count, color="skyblue")
plt.title("Favorite Treats")

plt.show()
```

### Output

A bar chart comparing the number of treats.

---

# 3. Scatter Plot

A **Scatter Plot** represents individual data points and helps identify relationships between two variables.

```python
import matplotlib.pyplot as plt

x = [2,4,1,5,3]
y = [3,1,4,2,5]

plt.scatter(x, y, color="red")

plt.title("Scatter Plot")

plt.show()
```

### Output

A scatter plot displaying individual data points.

---

# 4. Histogram

A **Histogram** shows the frequency distribution of numerical data by dividing it into intervals called bins.

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [55,60,65,70,75,80,85,90,95]

sns.histplot(marks, bins=5)

plt.title("Marks Distribution")

plt.show()
```

### Output

A histogram showing the distribution of students' marks.

---

# 5. KDE Plot

A **Kernel Density Estimation (KDE)** plot displays the probability density of continuous data using a smooth curve.

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [55,60,65,70,75,80,85,90,95]

sns.kdeplot(marks, fill=True)

plt.title("KDE Plot")

plt.show()
```

### Output

A smooth density curve representing the distribution of marks.

---

# 6. Box Plot

A **Box Plot** summarizes data using the minimum, maximum, median, and quartiles. It is also useful for detecting outliers.

```python
import seaborn as sns
import matplotlib.pyplot as plt

marks = [55,60,65,70,75,80,85,90,95]

sns.boxplot(x=marks)

plt.title("Box Plot")

plt.show()
```

### Output

A box plot showing the spread of marks and any outliers.

---

# 7. Heatmap

A **Heatmap** represents numerical values using different colors. It is commonly used to visualize correlation matrices.

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np

data = np.array([[1,2,3],
                 [4,5,6],
                 [7,8,9]])

sns.heatmap(data, annot=True, cmap="Blues")

plt.show()
```

### Output

A heatmap displaying values using color intensity.

---

# Difference Between Matplotlib and Seaborn

| Matplotlib | Seaborn |
|------------|----------|
| Basic plotting library | Built on Matplotlib |
| More customization | Better default styles |
| Requires more code | Simpler syntax |
| Suitable for all plots | Best for statistical plots |

---

# Applications of Data Visualization

- Understanding datasets quickly.
- Comparing different categories.
- Detecting trends and patterns.
- Identifying outliers.
- Visualizing Machine Learning results.

---

# Exercises

## Exercise 1: Draw a Line Plot

### Solution

```python
import matplotlib.pyplot as plt

x = [1,2,3,4]
y = [10,20,30,40]

plt.plot(x, y, marker="o")
plt.show()
```

### Output

A line graph connecting four points.

---

## Exercise 2: Create a Bar Chart

### Solution

```python
import matplotlib.pyplot as plt

subjects = ["Python","Java","C++"]
students = [45,30,25]

plt.bar(subjects, students)

plt.show()
```

### Output

A bar chart comparing the number of students.

---

## Exercise 3: Plot a Histogram

### Solution

```python
import seaborn as sns
import matplotlib.pyplot as plt

data = [12,15,17,18,20,20,21,22,24,25]

sns.histplot(data)

plt.show()
```

### Output

A histogram showing the frequency distribution of the data.

---

## Exercise 4: Create a Heatmap

### Solution

```python
import seaborn as sns
import matplotlib.pyplot as plt
import numpy as np

matrix = np.array([[2,4],[6,8]])

sns.heatmap(matrix, annot=True)

plt.show()
```

### Output

A heatmap displaying the values using color intensity.

---

# Key Takeaways

- Data visualization helps represent data graphically for better understanding.
- Matplotlib is used to create a variety of charts such as line, bar, and scatter plots.
- Seaborn simplifies statistical visualization with attractive default styles.
- Histograms, Box Plots, and Heatmaps are useful for data analysis.
- Data visualization is an essential step in Data Science and Machine Learning.
