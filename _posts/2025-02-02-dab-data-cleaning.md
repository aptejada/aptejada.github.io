---
layout: post
title: Data Cleaning Using PowerBI
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

# **Table of Contents**
> [Prerequisites](https://github.com/aptejada/aptejada.github.io/edit/master/_posts/dab-data-cleaning.md#prerequisites)
> 
> [Data Background](https://github.com/aptejada/aptejada.github.io/edit/master/_posts/dab-data-cleaning.md#data-background)
> 
> [Import and transform dirty data](https://github.com/aptejada/aptejada.github.io/edit/master/_posts/dab-data-cleaning.md#import-and-transform-dirty-data)
> 
> [Clean the data](https://github.com/aptejada/aptejada.github.io/edit/master/_posts/dab-data-cleaning.md#cleaning-the-data)

# **Prerequisites:**
* Excel file with uncleaned data
* PowerBI

# **Data Background**
The dataset contains
Eskwelabs
Sprint 1
  
# **Import and transform dirty data**

Once you load PowerBI, this image will be prompted. 

![start](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/start.png)

Add the uncleaned data in .xlsx format by clicking the _Import data from Excel_. On the navigator ribbon, click the data of interest. For this demo, we chose the _Expanded SEA dataset (dirty)_.
![navigator](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/navigator.png)

If you initially click the _load_, PowerBI will prompt error messages. Instead, click _transform_ to check errors and validity status of data.
![load and transform](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/loadandtransform.png)

You will be redirected to the PowerQuery user interface to edit your uncleaned data.
![power-query](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/power-query.png)

Notice the encircled details. The current Power Query editor profile is based on 1000 samples only, click on that and choose an option covering the entire dataset.

# **Clean the Data**
You are now here! 
![data-preview](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/data-preview.png)
The data preview (encircled) provides insights into the percent validity, errors, and empty profile of the dataset (boxed). Use this as a guide to clean data per column.

**Let's begin cleaning!**

### Column 1

Observation
> Column 1 is for **iso_code** with 98% valid and 2% empty data. 

Solution
> Sort data in ascending order <br>
![sort-ascending](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/sort-ascending.png) <br>
<br>

> Check other columns before removing the _null_. Here, you see that there are 13 empty rows. Remove these empty rows but be careful not to include rows with contents <br> 
> Go to _Home_ &#8594; _Remove Rows_ &#8594; _Remove Blank Rows_ <br>

![empty-rows](https://github.com/aptejada/aptejada.github.io/tree/master/assets/img/empty-rows.png) <br>

> If you can retrieve info on missing contents per column, modify the dataset to include the info. (e.g. based on column 2, null values belong to Philippines. Replace _null_ with PHL <br>
Go to _Home_ &#8594 _Replace Values_

### Column 2
Observation
> Column 2 is for **country** with 98% valid and 2% empty data
> Country with iso code THA is empty

Solution
> Follow the same steps done in Column 1. If values are null but data are retrievable elsewhere. Modify the data (e.g THA = Thailand) <br>
Go to _Home_ &#8594 _Replace Values_

### Column 3
Observation 










