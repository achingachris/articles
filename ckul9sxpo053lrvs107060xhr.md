---
title: "Quick Data Exploration - Python"
datePublished: Sun Oct 10 2021 13:36:48 GMT+0000 (Coordinated Universal Time)
cuid: ckul9sxpo053lrvs107060xhr
slug: quick-data-exploration-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1633494038264/eaSLt__Z0.png
tags: python, data-science, 2articles1week, hacktoberfest-1

---


> 
Hi There! Welcome to Data 101.

NOTE:

I'll be using Google's Colab and Python in the article.

To learn how to read files, refer to the previous article in this  [series](https://chrisdevcode.hashnode.dev/series/data-101) :

%[https://chrisdevcode.hashnode.dev/reading-data-from-files-using-python]

# Data Exploration

In Data Exploration, we look into finding the number of instances of records, number of columns and rows, the columns and data types in each column...

I will be using  [pandas](https://pandas.pydata.org/)  library throughout.

I will be using  [airlines](https://docs.google.com/spreadsheets/d/1hipdEeKU6UBrCpzyLEF-Vj5F4nA8gCRLYJP50CKr-B0/edit?usp=sharing)  and  [airports](https://docs.google.com/spreadsheets/d/1fWIIVmxXSwahoB79rxRFRY2qQbaQpAED0fx_RKR1o20/edit?usp=sharing)  CSV files.

To import the data:

```python
import pandas as pd
airlines = pd.read_csv('airlines.csv')
airports = pd.read_csv('airports.csv')

```

### Viewing First and Last few rows

To view the first 5 rows on the data set, we use  `.head()` from pandas.

```python
airports.head()
```

![head.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633871741764/Z-4IDvsyG.png)

You can use `.head(x)` to get x number of rows from the top

To view the last 5 rows on the data set, we use  `.tail()` from pandas.

```python
airports.tail()
```

![tail.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633872092900/3qlS9DH25.png)

### Viewing Rows and Columns

To know the number of columns and rows in your data frame, use `.shape`. It returns the dimensions of your data set:

```python
airports.shape
```

![shape.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633872345871/mTW49VAbB.png)

To view the columns in the data frame, use `.columns()`

```python
airports.columns
```

![columns.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633872419220/ly8KEV0vX.png)

### Viewing Data Types

To view datatypes of each data in each column, use `.dtypes`:

```python
airports.dtypes
```

![dtype.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633872704929/f-fn1Ixjg.png)

<hr />

Other tricks you could use are:

```python
x.rows
x.info()
x.describe()
x.unique()
x.describe()
```
