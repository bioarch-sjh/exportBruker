---
title: "Guide to using the 'exportBruker.R' file"
output:
  html_document:
    df_print: paged
  pdf_document: default
---

# Introduction

This notebook shows you how to use the functions in the R file `exportBruker.R`. The first few sections (**Basic Usage** and **Setup**) are aimed at people who simply want to export a Bruker-format dataset to a .csv file. The steps described there should get you going quickly 90% of the time. The remaining sections describe the functions in more detail. 



# Basic Usage.

Assuming you've set up R or RStudio, the functions in the file `exportBruker.R` allow you to create csv files from Bruker data in just a few lines. You can run this code from any directory in the system as long as you know where your Bruker file is, for example: 

```{r eval=FALSE}
source("exportBruker.R")
exportDataSetCsv(loadBruker("~/Desktop/20140307_SH_Womble/"))
```

## What the code does

The code above does the following:

  - Loads the functions and packages needed (using `source(...)`)
  - Loads the Bruker dataset (using `loadBruker()`)
  - Exports the Bruker dataset to a subdirectory called `csv` (using `exportDataSetCsv(...)`). Note that the subdirectory will be created if it doesn't exist already. 

# Setting up

To set your system up for running this code, all you have to do (once you've installed RStudio or R) is install the `MALDIquantForeign` package. You can check if that's already been done and install it if necessary like this:

```{r eval=FALSE, message=FALSE, warning=FALSE}
require("MALDIquantForeign")
```

This will check whether the package is installed or not, and install it for you if it isn't. 

http://web.cs.ucla.edu/~gulzar/rstudio/ shows you how to use RStudio to install the package via the menu bar. 

# Details

## Functions in exportBruker.R

The full list of functions is:

- `printUsage()`
- `loadBruker()`
- `exportDataSetCsv()`
- `exportDataSetTab()`
- `listData()`
- `indexFromPlatePos()`
- `exportPlateMapSpot()`

### **`printUsage()`**

### printUsage()

This function simply prints out a message to tell you how to export the dataset, like this:

```{r eval=FALSE, include=TRUE}
source("exportBruker.R")
printUsage()
```

..which gives the output 

```
=============================================================
This file is part of exportBruker version 1.0.2
Typical usage is:

  > exportDataSetCsv(loadBruker(PATH))

..where PATH is the file path to the Bruker source directory

This program has created a subdirectory called 'csv',
where the exported text files will be placed
=============================================================
```

### loadBruker()






## Paths to the Bruker folder

If all you want to do is make a csv, then you needn't worry about that - the only thing you need to change to run this on your code is the part within the quotes, which is the *path* to the directory where the Bruker data is held. Other example paths might be:

- `"C:\\Users/sjh/Desktop/BrukerData/20140307_SH_Womble"`: This is the *absolute path* to the folder on a windows machine
- `"~/../Desktop/BrukerData/20140307_SH_Womble"`: This is the path within a users directory space
- `"../../Desktop/BrukerData/20140307_SH_Womble"`: This is the *relative path*, i.e. the route to the Bruker folder from wherever you are running R from.

Note 

- the use of `/` in specifying the path, as opposed to the `\` symbol that windows normally uses!
- If you want to use `\`, then you must type `\\` because the backslash is an *escape character*

# More Details

Since this is an R notebook, the R code you see is runnable from within R Studio! See https://bookdown.org/yihui/rmarkdown/notebook.html for more details. 

```{r eval=FALSE, include=FALSE}
source("exportBruker.R")
exportDataSetCsv(loadBruker("20140307_SF_UPenn164-181/"))
```


