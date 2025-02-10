---
layout: post
title: Data Cleaning Using Power BI
subtitle: Garbage In, Garbage Out!
cover-img: /assets/img/powerbi-logo.png
gh-repo: https://github.com/aptejada/aptejada.github.io
gh-badge: [star, fork, follow]
tags: [PowerBI,data,analytics,data cleaning]
comments: true
thumbnail-img: /assets/img/power-bi-logo.png
mathjax: false
author: Dats Aquamariene
---

<details> 
  <summary>Table of Contents</summary>
  <br>
  
> [Prerequisites](#prerequisites)
  
> [Data Background](#data-background)
> 
> [Import and transform dirty data](#import-and-transform-dirty-data)
> 
> [Clean the data](#clean-the-data)
>
> [Take Away](#take-away)
</details>

# **Prerequisites**
* Excel file with uncleaned data
* Power BI

# **Data Background**

A raw dataset with greenhouse gases emissions, economic, and industrial profiles for Southeast Asian region. The dataset is structured as an excel file with each row representing data/values for specific country or region obtained between 1889 to 2018. Each column representing parameters. Here's a general idea of what the structure could look like:

|location information | time period | carbon emission sources | carbon consumption | capita | total greenhouse gases | population | 
|:--------------------|:-----------:|:-----------------------:|:------------------:|:------:|:----------------------:|:----------:|
|        Philippines  |      2023   |          #              |          #         |   #    |            #           |     #      |        

This dataset was provided by Eskwelabs. Intentionally left uncleaned for training purposes.
  
# **Import and transform dirty data**

Once you load Power BI, this image will be prompted. 

![start](/assets/img/start.png)

Add the uncleaned data in .xlsx format by clicking the _Import data from Excel_. On the navigator ribbon, click the data of interest. <br> For this demo, we chose the _Expanded SEA dataset (dirty)_.
![navigator](/assets/img/navigator.png)

If you initially click the _load_, Power BI will prompt error messages. Instead, click _transform_ to check errors and validity status of data.
![load and transform](/assets/img/loadandtransform.png)

You will be redirected to the Power Query user interface to edit your uncleaned data.
![power-query](/assets/img/power-query.png)

Notice the encircled details. The current Power Query editor profile is based on 1000 samples only, click on that and choose an option covering the entire dataset.

# **Clean the Data**
You are now here! 
![data-preview](/assets/img/data-preview.png)
The data preview (encircled) provides insights into the percent validity, errors, and empty profile of the dataset (boxed). <br> 
Use this as a guide to clean data per column.

**Let's begin cleaning!**

### [1] **iso_code**

Observation
> With 98% valid and 2% empty data. 

Solution
> Sort data in ascending order <br>
> ![ascending](/assets/img/sort-ascending.png) <br>
<br>

> Check other columns before removing the _null_. Here, you see that there are 13 empty rows. Remove these empty rows but be careful not to include rows with contents <br> 
> Go to _Home_ &#8594; _Remove Rows_ &#8594; _Remove Blank Rows_ <br>

![empty-rows](/assets/img/empty-rows.png) <br>

> If you can retrieve info on missing contents per column, modify the dataset to include the info. (e.g. based on column 2, null values belong to Philippines. Replace _null_ with PHL <br>
Go to _Home_ &#8594; _Replace Values_

### [2] **country**
Observation
> With 98% valid and 2% empty data
> Country with iso code _THA_ is empty

Solution
> Follow the same steps done in Column 1. If values are null but data are retrievable elsewhere. Modify the data (e.g. _THA = Thailand_) <br>
Go to _Home_ &#8594; _Replace Values_

### [3] **year**
Observation 
> Data type is in _whole number_. Error is 100%
> ![year](/assets/img/year.png)

Solution
> Go to _Home_ &#8594; _Keep Errors_ &#8594; Click on Error within the column to see details <br>
> Report detail says ** DataFormat.Error: We couldn't convert to Number. Details: Year 1919 ** <br>
> Close the last step on the _Applied Steps_ section and change the Error into 1919 <br>
> Right-click on the column name &#8594; Click the _Replace Errors_ &#8594; Write 1919 as the replaced value &#8594; Close the _Kept Errors_ on the _Applied Steps_

### [4] flaring_co2_per_capita
Observation
> With 6% Error
> ![flaring](/assets/img/flaring.png)

Solution
> Sort in _ascending order_. ** DataFormat.Error: We couldn't convert to Number. Details: zero ** <br>
> Close the _sorted by Rows_ step. Then go to _Home_ &#8594; _Keep Errors_ &#8594; Right click column name &#8594; Replace Error "zero" with "0" <br>
> Close _Kept Errors_

### [5] population
Observation
> Arranged data in descending order. We observed that some data has string data type (e.g. 118 thousand) and <br>
> Has negative values

Solution
> Go to Transform &#8594; Replace Values; &#8594; Manually change strings into numerical equivalent <br>
> Sort data in descending order to check if strings are still present <br>
> Transform the negative values into absolute values <br>
> Right click on column name &#8594; Click _Absolute Value_ <br>
> Recheck if errors persist. Go to _Keep Rows_ &#8594; _Keep Errors_ &#8594; Close the _Kept Errors_ step

### [6] region
Observation
> Data column shows no % Error however, <br> 
> Presence of _Central Asia_ in the data. Recall the data background. This data should only report data from South East Asian regions. <br>
> If you look at the **iso_code** and **country**, almost all are located in South East Asia

Solution
> Replace string value _Central Asia_ as _South East Asia_ <br>
> Go to _Transform_ or right click then _Replace Value_

### [7] income_group
Observation
> Column categorized data into 3 groups: _High Income_, _Lower middle income_, _Upper middle income_ but a _null_ group was observed <br>
> _null_ group falls under Philippines which is considered as _Lower middle income_ group

Solution
> Replace _null_ with the correct categorization (Lower middle income) <br>
> Go to _Transform_ &#8594; Replace Values &#8594; Input the correct values/strings

We're almost done!

### [8] Watch out for duplicates
Observation
> Go back to the first column. Notice that _LAO_ is duplicated. Highlight all dataset by selecting all columns from **iso_code** to **income_group**
> ![duplicates](/assets/img/duplicates.png) <br>


Solution
> Then Right click on the dataset &#8594; Remove duplicates <br>
> Close the _Filtered Rows_ on the _Applied Steps_

### [9] Remove unnecessary data, outliers, or anomalies
Observation
> EU is a different region. Obviously, not in South East Asia

Solution
> Filter the data <br>
> Click the filter toggle button beside the column **iso_code**. Uncheck the box beside EU <br>
> Finally, Apply All steps by saving the Power Query
> ![fin](/assets/img/fin.png) <br>

### Save and Exit!

### Bonus
Here is the list of steps used to _dirtify_ the dataset
![guide](/assets/img/guide.jpg)

# Take Away

Cleaning data is time-intensive but pivotal step in data analytics. We had to be keen checking for anomalies, missing values, duplicates, data format and types. 

With Power BI, we prepared a clean, reliable, and format consistent data ready for analysis and visualization.

# Acknowledgment

Special thanks goes to the _Eskwelabs Team_, _Luigi (Instructor)_ and _JC (Mentor)_ who shared time and expertise during our Data Analytics - Data Cleaning Sprint

_ciao, I'm dozing off!_













