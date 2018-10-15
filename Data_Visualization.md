# Introduction

Data Visualization is a vital tool for understanding data which, in turn, is important to derive performance. 
Below you will find scripts for commonly used plots to visualize datasets using **Matplotlib**, **Seaborn** and **Pandas** APIs.

# Sample Dataset

I am using 'Prima Indians dataset' for this task which can be found [here](https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv).

# Initialiazing
```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np
sns.set(color_codes=True)

url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv"
features = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
data = pd.read_csv(url, names=features)
```

*Note: For the purpose of illustration, I will just use first four features of dataset*

# Univariate Plots

## Line plot
To rapidly get an idea of the range of features, line plot is an ideal choice. This plot is generated using Maplotlib and Pandas 'plot' api.
```
fig, (ax) = plt.subplots(2, 2, sharex=True)
features = data.columns[:4]
ax = ax.ravel()

for i in range(len(features)):
    data[features[i]].plot(ax=ax[i])
    ax[i].legend(loc=4)
    plt.show()
```

## Box and Whisker plot

To understand features in a summarized fashion, boxplots can be used. It plots 5 values for a given feature. 
Box shows 25th and 75th percentile with a line in between giving an idea of median while the whiskers shows the min and max value. 
FYI, there is no API in any library to also show the exact values of these quantities, so I have added a patch for the same.

```
features = data.columns[:4]
fig, axes = plt.subplots()
data_viz = data[features]
bp_dict = plt.boxplot(data_viz.values)

def add_values_on_plot(bp, ax):
    for element in ['whiskers', 'medians', 'caps']:
        for line in bp[element]:
            (x_l, y),(x_r, _) = line.get_xydata()
            if not np.isnan(y): 
                x_line_center = x_l + (x_r - x_l)/2
                y_line_center = y
                ax.text(x_line_center, y_line_center, '%.3f' % y, verticalalignment='center', fontsize=6, 
                        backgroundcolor="white")
add_values_on_plot(bp_dict, axes)
labels = features
plt.xticks(range(1, len(labels) + 1), labels)
plt.show()
```

You can comment out `add_values_on_plot(bp_dict, axes)` if you dont want values to be shown on plot
## Distribution plot
To get a better and broader understanding of features, distribution plot is a necessity. It uses Seaborn.

```
fig, (ax) = plt.subplots(2, 2, sharex=True)
features = data.columns[:4]
ax = ax.ravel()

for i in range(len(features)):
    sns.distplot(data[features[i]], label=features[i], ax=ax[i])
    ax[i].legend(loc=2)

plt.show()
```



# Multivariate Plots

## Scatter plot
```
x='plas'
y='pres'
plt.scatter(data[x], data[y])
plt.xlabel(y)
plt.ylabel(y)
plt.show()
```

## Reg plot

```
x='plas'
y='pres'
data_viz = data[[x,y]]
sns.regplot(x=x, y=y, data=data)
plt.show()
```

You can also cap and floor your data like `data = data[[x,y]][data[x]<=data[x].quantile(0.95)]` to remove outliers.
# Acknowledgement
