# Introduction

This notebook shows you how to use the functions in the R file `exportBruker.R`. The first few sections (**Basic Usage** and **Setup**) are aimed at people who simply want to export a Bruker-format dataset to a .csv file. The steps described there should get you going quickly 90% of the time. The remaining sections describe the functions in more detail. 



# Basic Usage.

Assuming you've set up R or RStudio, the functions in the file `exportBruker.R` allow you to create csv files from Bruker data in just a few lines. You can run this code from any directory in the system as long as you know where your Bruker file is, for example: 


    source("exportBruker.R")
    exportDataSetCsv(loadBruker("~/Desktop/20140307_SH_Mammoth/"))


## What the code does

The code above does the following:

  - Loads the functions and packages needed (using `source(...)`)
  - Loads the Bruker dataset (using `loadBruker()`)
  - Exports the Bruker dataset to a subdirectory called `csv` (using `exportDataSetCsv(...)`). Note that the subdirectory will be created if it doesn't exist already. 

# Setting up

To set your system up for running this code, all you have to do (once you've installed RStudio or R) is install the `MALDIquantForeign` package. You can check if that's already been done and install it if necessary like this:

    require("MALDIquantForeign")


This will check whether the package is installed or not, and install it for you if it isn't. 

http://web.cs.ucla.edu/~gulzar/rstudio/ shows you how to use RStudio to install the package via the menu bar. 

# Details

## Paths to the Bruker folder - examples

The line:

    exportDataSetCsv(loadBruker("~/Desktop/20140307_SH_Mammoth/"))

gives an example of creating csv files from a Bruker directory. The only thing you need to change to run this on your code is the part within the quotes, which is the *path* to the directory where the Bruker data is held. Other example paths might be:

- `"C:\\Users/sjh/Desktop/BrukerData/20140307_SH_Mammoth"`: This is the *absolute path* to the folder on a windows machine
- `"~/../Desktop/BrukerData/20140307_SH_Mammoth"`: This is the path within a users directory space
- `"../../Desktop/BrukerData/20140307_SH_Mammoth"`: This is the *relative path*, i.e. the route to the Bruker folder from wherever you are running R from.

Note 

- the use of `/` in specifying the path, as opposed to the `\` symbol that windows normally uses!
- If you want to use `\`, then you must type `\\` because the backslash is an *escape character*




## Functions in exportBruker.R

The full list of functions is:

- `printUsage()`
- `loadBruker()`
- `exportDataSetCsv()`
- `exportDataSetTab()`
- `listData()`
- `indexFromPlatePos()`
- `exportPlateMapSpot()`

Below is a short description of what each function does

### printUsage()

This function simply prints out a message to tell you how to export the dataset, like this:

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

This function parses the Bruker directory and creates an R object to hold the data. For more information, browse the internet for the R package called `MALDIquant`. You might use this to create an object that you plan to do other things with, like this:

    mydata <- loadBruker("~/Desktop/20140307_SH_Mammoth/")

### exportDataSetCsv()

This function creates csv files from a R MALDIquant data object. You can call it like this:

    exportDataSetCsv(mydata)
    
..this assumes you've created `mydata` by using the `loadBruker` function. If all you want is csv files, you can put one function inside the other like this: 

    exportDataSetCsv(loadBruker("~/Desktop/20140307_SH_Mammoth/"))


### exportDataSetTab()

This function works exactly like `exportDataSetCsv()` except that it creates tab-delimited files instead of .csv files. 

### listData()

This function prints to the console a list of all the data in the bruker directory, like this: 

    listData(mydata)
    
..where `mydata` is the MALDIquant data object

### indexFromPlatePos()

Get the index of a spot's data within the MALDI data object, for example:

    pos <- indexFromPlatePos("L9") 
    
..will tell you which of the samples in the MALDI data object pertains to spot L9. This assumes that the spot position is after the '.' in the name of the sample, as in '20131016_Oxford_Samples.L9'.


### exportPlateMapSpot()

This allows a single spot to be exported to csv rather than a whole dataset. 

    exportPlateMapSpot(mydata,"L9","L9.csv")
    
will parse the `mydata` object for spot L9 and export the specrum to a file called "L9.csv".    


