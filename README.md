# Training Module:  R Programming

The figure below provides a reasonable visual representation of the data analyst's workflow.  The first step is **Importing** the data into the data analyst's preferred software package.  The second step is **Tidying** the data.  This step is sometimes referred to as "munging" or "wrangling" but they all generally mean the same thing:  preparing the data for analysis.  The remaining time is spent **Exploring** the data, often through summary statistics, regressions, or more advanced techniques like Machine Learning and Artificial Intelligence.  The final step is to **Communicate** insights through figures, charts, tables, and other visuals.

The true workflow is not as linear as the figure implies.  Nevertheless, it provides a useful framework for how to approach a project and for learning a new software package.  

#### **Data Analyst Workflow**

![Data](https://d33wubrfki0l68.cloudfront.net/795c039ba2520455d833b4034befc8cf360a70ba/558a5/diagrams/data-science-explore.png)

##### Notes:  Wickham, Hadley, and Garrett Grolemund. R for data science: import, tidy, transform, visualize, and model data. " O'Reilly Media, Inc.", 2016. (available at https://r4ds.had.co.nz/). #####

Programming often follow the Pareto Principle:  80% of the work can be done by 20% (or less) of the available features.  This module is designed to introduce the fewest number of concepts necessary to be proficient on the vast majority of tasks.

## Import Data
There are lots of ways to import data into R.  For example, the base version of R has several data import functions like read.table, read.csv, and read.delim (note the "." after "read").  However, other packages provide slightly better functionality and speed than what is available in base R.  

The readR package includes functions like read_csv, read_tsv, and read_fwf (note the "\_" after "read").  The readXL package includes functions like read_excel (again, note the "\_" after "read").  Both readR and readXL are part of the Tidyverse.  The Tidyverse is a collection of R packages that share underlying design philosophy, grammer and datas structures.  Haven is another Tidyverse package that imports datasets from other statistical packages (SAS, Stata, and SPSS) into R.

Learn these three packages before branching out into other packages.  

> **BEST PRACTICE NOTE:**  
> Import data using code saved to a program **NOT** through drop-down menus included in the software.

### Videos

* [Introduction to readR (5:04)](https://www.youtube.com/watch?v=URJNKVBMCAY) - This video provides a very quick and high-level overview of the **readR** package.  It covers Hierarchical data types that are commonly found in social science research.  More detail on the readR package or other data types can be found in the optional videos below.

  * _(Optional)_ [The readr Package for Importing Delimited Data (25:02)](https://www.youtube.com/watch?v=qxbfVEDfi0o)
  * _(Optional)_ [Importing Excel Data, SAS Data, and More (14:44)](https://www.youtube.com/watch?v=qxbfVEDfi0o)
  * _(Optional)_ [Importing Data Into R (45:00)](https://www.rstudio.com/resources/webinars/importing-data-into-r/)

* [Importing/Reading Excel data into R using RStudio (8:11)](https://www.youtube.com/watch?v=JYVWufSQ4OI) - A brief introduction to the **readXL** package.  It begins by introducing how to import data using the drop-down menus in RStudio.  This is a great way to learn the syntax of readXL **however**, it is best practice to save the code into the program you are writing.  That way work can be replicated by others.
  * _(Optional)_ There are a lot of other packages that can read in Excel files. An overview of these packages and their pros and cons can be found here:  https://lgreski.github.io/dsdepot/2020/06/13/reading-Excel-files.html

### Sample Code
```r
# Import from Text using readR
library(readr)
csv <- read_csv("data/Water_Right_Applications.csv")

# Import from Excel using readXL
library(readxl)
excel <- read_excel("data/Water_Right_Applications.xlsx")

# Import from SPSS using haven
library(haven)
sav <- read_sav("data/Child_Data.sav")

# Import from SAS using haven
sas <- read_sas("data/iris.sas7bdat")

# Import from Stata using haven
stata <- read_dta("data/Milk_Production.dta")
```
readR can also save objects to different formats.  This is done via the functions write_csv, write_delim, and write_rds.

> **BEST PRACTICE NOTE:**  
> .RData (sometimes abbreviated as .Rda) is a valid data type.  .RData files can store multiple objects under the same name.  It is preferred to use .Rds rather than .Rda.

```r
# Save excel to an R dataset
write_rds(excel, "imported_from_excel.rds")

# Save excel to a csv file
write_csv(excel, "imported_from_excel.csv")

# Save excel to a bar delimited txt
write_delim(excel, "imported_from_excel.txt", delim = "|")
```

> **BEST PRACTICE NOTE:**  
> Large datasets should be imported once and then saved to a permanent R dataset. This saves you from having to wait to re-import data multiple times.


## Tidy Data
To be useful, data must be structured to facilitate analysis.  Unfortunately, data are rarely, if ever, provided in a form that is analysis ready.  By [some estimates](https://www.nytimes.com/2014/08/18/technology/for-big-data-scientists-hurdle-to-insights-is-janitor-work.html), data analysts spend between 50% and 80% of their time in the Import and Tidying phases.  Often, one dataset will need to be combined with multiple other datasets before an analysis can begin.  Moreover, new variables will need to be created or formats will need to be changed prior to performing analyses.  Data may also be missing or wrong.  These all have severe implications for the results of an analysis.  As the old addage goes --  _Garbage In, Garbage Out_.  

The term "Tidy Data" comes from a [paper by Hadley Wickham](https://vita.had.co.nz/papers/tidy-data.pdf) (author of multiple R packages and creator of the [Tidyverse](https://www.tidyverse.org/packages/)).  According to Wickham, there are generally four types of transformations needed to convert messy data to Tidy data:
* Filter:  subsetting or removing observations based on some condition.
* Transform:  adding or modifying variables
* Aggregate:  collapsing multiple values into a single value (e.g., by summing or taking means).
* Sort:  changing the order of observations.

The Tidyverse is a collection of R packages intended to make the task of Tidying simple.  The main packages used are tidyr, dplyr, stringr, lubridate, and magrittr.  Base R also includes functions for data transformation.  These are typically part of data.table.

### Videos

* [Missing Data in R (12:51)](https://youtu.be/hLYAno2r9O4)
* tidyr video
* dplyr video
* stringr video
* lubridate video
* data.table video

### Sample Code

### Exercises


## Explore Data

### Videos
* [Summary Statistics with One Variable](https://www.youtube.com/watch?v=l1lVtEyxnMs&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=8)
* [Summary Statistics with Two Variables](https://www.youtube.com/watch?v=L5WV8KiD8-A&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=10)
* [Simple Plots and Graphs](https://www.youtube.com/watch?v=pLh2gdHDUZc&list=PLcTBLulJV_AIuXCxr__V8XAzWZosMQIfW&index=11)

## Communicate Insights

## Important Functions
* head()
* str() - Get a summary of an object's structure.
* class() - Find the class an object belongs to.
* getwd() - Find the current working directory.
* setwd() - Change the current working direcotry.
* subset()
* mean() - Average of a variable.
* sd() - Standard Deviation of a variable.
* median() - Median of a variable.
* summary() - Descriptive information of a variable.  By default, the function reports the minimum, 25th Percentile, Median, Mean, 75th Percentile, and maximum.
* table() - Listing of all the values contained in a variable.  Often useful for categorical variables (for example, years of education).  When used with multiple variables it will yield a cross-tab.  To add labels to the cross-tab, use "dnn=c()" option.
* cor() - Calculates a correlation between two variables.  Alt version can be done with cor.test().  The alternative will yield statistical tests.
* aggregate() - Calculates summary statistics by group [[Tutorial](https://www.datasciencemadesimple.com/aggregate-function-in-r/)]
* sapply() -
* lapply() -
* mapply() -
* tapply() -
* plot() - A simple (unformatted) scatterplot of data.  Can also be used to plot a density plot ("plot(density(dataset$variablename))").
* hist() - A simple (unformatted) histogram of data.
* barplot() - A simple (unformatted) bar chart.

## Important Packages
* Import
  * readr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf))
  * readxl ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-import.pdf)) This package can read .xlsx files and legacy .xls files.
  * [haven](https://haven.tidyverse.org/) - Enables R to read and write various data formats ued by other statistical packages (SAS, SPSS, Stata).  Part of the tidyverse.  Output is a tibble.

* Tidy Data
  * tidyr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/tidyr.pdf))
  * dplyr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-transformation.pdf))
  * lubridate ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/lubridate.pdf))
  * stringr ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/strings.pdf))
  * data.table()

* Explore Data
  * stargazer ([]()) - Summary statistics (N, Mean, Std Dev., Min, Max by default) for a data frame.

* Communicate Insights
  * [ggplot2]() ([Cheat Sheet](https://raw.githubusercontent.com/rstudio/cheatsheets/main/data-visualization.pdf))
  * [plotly]()

To be Added:  
library(boot)
library(purrr)
library(furrr)
library(zoo)
library(scales)
library(modelr)
library(strucchange)
library(glue)
library(RQuantLib)
library(rvest)
library(broom)
