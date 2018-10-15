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

url = "https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv"
names = ['preg', 'plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'class']
data = pandas.read_csv(url, names=names)
```

# Univariate Plots

## Line Plot
To rapidly get an idea of the range of features, line plot is an ideal choice. This plot is generated using Maplotlib and Pandas 'plot' api.
```
fig, ([ax1, ax2], [ax3, ax4]) = plt.subplots(2, 2, sharex=True)
data['plas'].plot(ax=ax1)
data['pres'].plot(ax=ax2)
data['skin'].plot(ax=ax3)
data['mass'].plot(ax=ax4)
ax1.legend(loc=4)
ax2.legend(loc=4)
ax3.legend(loc=4)
ax4.legend(loc=4)
plt.show()
```

## Distribution Plot
To get a better and broader understanding of features, distribution plot is a necessity. It uses Seaborn.

```
```

## Box and Whisker Plot

To understand features in a summarized fashion, boxplots can be used. It plots 5 values for a given feature. 
Box shows 25th and 75th percentile with a line in between giving an idea of median while the whiskers shows the min and max value. 
FYI, there is no API in any library to also show the exact values of these quantities, so I have added a patch for the same.

```
```

# Multivariate Plots

## Scatter plot

# Acknowledgement
