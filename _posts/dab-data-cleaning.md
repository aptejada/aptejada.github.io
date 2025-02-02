---
layout: post
title: Data Cleaning Using PowerBI
subtitle: Garbage In, Garbage Out!
author: Dats Aquamariene
---
# **Table of Contents**

# **Prerequisites:**
* Excel file with uncleaned data
* PowerBI
  
# **Import and transform dirty data**

Once you load PowerBI, this image will be prompted. 

![start](https://github.com/aptejada/aptejada.github.io/tree/master/images/start.png)

Add the uncleaned data in .xlsx format by clicking the _Import data from Excel_. On the navigator ribbon, click the data of interest. For this demo, I chose the _Expanded SEA dataset (dirty)_.
![navigator](https://github.com/aptejada/aptejada.github.io/tree/master/images/navigator.png)

If you initially click the _load_, PowerBI will prompt error messages. Instead, click _transform_ to check errors and validity status of data.
![load and transform](https://github.com/aptejada/aptejada.github.io/tree/master/images/loadandtransform.png)

You will be redirected to the PowerQuery user interface to edit your uncleaned data.
![power-query](https://github.com/aptejada/aptejada.github.io/tree/master/images/power-query.png)

Notice the encircled details. The current Power Query editor profile is based on 1000 samples only, click on that and choose an option covering the entire dataset.
