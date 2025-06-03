---
title: "Reading Data From Files Using Python"
datePublished: Tue Oct 05 2021 19:14:00 GMT+0000 (Coordinated Universal Time)
cuid: ckuegnbpq03tdpxs12vtg4fq7
slug: reading-data-from-files-using-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1633375792676/HEBwBDQW-.png
tags: python, data-science, 2articles1week, hacktoberfest-1

---


> 
Hi There! Welcome to Data 101.

In this article, I will take you through reading files using Python as you prepare to analyze them.

I will be using  [Google's Colaboratory](https://research.google.com/colaboratory/) tool as my IDE. You don't have to install or set up anything on your laptop/computer to use it, simply go to https://research.google.com/colaboratory/ and create a new notebook.

# Reading CSV Files

You'll need to upload a data file. To do so, click on the folder icon on the far left of the Notebook:

![upload.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633372078972/e0xilNfH3.png)

I will be using [airlines](https://docs.google.com/spreadsheets/d/1hipdEeKU6UBrCpzyLEF-Vj5F4nA8gCRLYJP50CKr-B0/edit?usp=sharing) and  [airports](https://docs.google.com/spreadsheets/d/1fWIIVmxXSwahoB79rxRFRY2qQbaQpAED0fx_RKR1o20/edit?usp=sharing)  CSV files

On the new Notebook, import  [Pandas](https://pandas.pydata.org/). Pandas is a Python library that is used for data manipulation.

```python
import pandas as pd
```

Since we have two files, let's create two variables with the path to the files:

```python
airlines = pd.read_csv('airlines.csv')
airports = pd.read_csv('airports.csv')
```

The `.read_csv` from pandas library enables us to read the CSV files. (That simple!).

To view the contents of the files read, we'll use `.head()` from pandas that will return the first 5 rows of the data loaded.

```python
airlines.head()
```

![airlines.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633373312017/jmezcHP4h.png)

```python
airports.head()
```

![airports.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633373368025/4GYrU3cCq.png)


# Reading JSON Files

Get the file [airports.json](https://drive.google.com/file/d/1mYtu9mgykInL-FSQzugq9lIokbwShUAF/view?usp=sharing)

We'll create the path to the file:

```python
airports_json = pd.read_json('airports.json')
```

To view the first 5 data objects:

```python
airports_json.head()
```

![airportjson.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1633375000266/enC-lbCFG.png)

## Conclusion

This is probably the first-ever step into data analysis, and we nailed it!

Here is the whole demo file:


%[https://github.com/achingachris/datasciencelearninghub/blob/master/data_cleaning.ipynb]

