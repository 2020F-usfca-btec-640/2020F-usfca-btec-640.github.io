---
layout: post
title:  "Basic Coding Applications for Commercial Strategy"
date:   2020-11-08 12:54:04 -0700
categories: sales commercial strategy revenue cogs margins applications
---

Every department for every company can benefit from data analysis. Coding allows large data sets to be manipulated and presented in a helpful way. For all code, the goal is that you start with raw information and you end up with useful information derived from the raw form. In genetics, you may have genome sequences as your starting material that are used to determine the similarities and differences between the DNA for different samples. This analysis has many different applications, including the determination of mutations in cancer cells.

Benefits of programming can also be found outside of research and development such as in sales and marketing. Below are a few examples of how R  code can be used to create impactful tools for commercial departments.


# Data Cleaning
Before we dive into each code example, it is crucial to clean your raw data first. The most important items to check are that the column titles are in line with what your code references as well as to check that the data points are consistently and correctly formatted.
1. **Check raw data column titles:** The raw data column titles must match the code exactly including capitalization. With code that references `revenue`, a column title of `Revenue` will not work. If your general code references `territory`, but your raw data uses `states` as the territory descriptor, the column title for the states must be changed to `territory`.
2. **Check data format consistency:** If a data point doesn’t exist, it needs to say `NA`. Otherwise, the data should follow the same template throughout the data set and that aligns with the code. For example, the state of California should not be represented as `California`, `california`, `CA`, and `ca`. It doesn't matter which one is used as long as it is the same format used for all raw data points and the code input.

# Directory Set-Up
Create your project folder with your R project file saved into this folder. Also include the following folders: `data`, `code`, `output`. The `data` folder should be the location where all of your raw data files are kept. The `code` folder should contain your scripts. The `output` folder is where your output files should be saved to and should also include a subfolder titled `figures`.

# Applications
## Territory Analysis
It is essential to analyze revenue by territory for many different reasons. Each territory can have a slightly different client base that has different needs that should be understood in order to create a successful commercial strategy specific to that region. Additionally, if different territories are covered by different reps, a clear understanding of territory performance is essential for quota development and commission payout. Along the same lines, territory splits can be determined should certain territories show growth that warrants multiple account managers.
#### Starting Material:
A revenue report that has the following columns should be saved in your `data` folder in your directory -
* `revenue` - revenue dollar amount
* `date` - invoice date, shipping date, start date, purchase date, or whatever date is most relevant for your purposes
* `territory` - sales representative (i.e. Debbie Vo), state (i.e. WA), territory name (i.e. North West)

#### Code to Separate Data by Territory:
We start off by creating a general function to subset any territory out of the full data set. This code should not have to change when different files and territories are indicated. This should also create an output CSV file that is named based on the defined territory.
```ruby
subset_data_to_territory <- function(input_file_name, territory_to_subset) {

  # read in the complete csv files
  all_revenue_data <- readr::read_csv(input_file_name)

  # subset the data set to only include rows where the territory column has the
  # chosen territory name(s) in it
  territory_data <- all_revenue_data %>%
    dplyr::filter(`territory` %in% territory_to_subset)

  # check that the subsetted data actually has data in it
   if (nrow(territory_data) == 0) {
    stop("ERROR, no rows matching given territory name. Did you make a typo?")
   }

  # save the territory list as a string to use in the file name
  dat <- data.frame(Col2 = territory_to_subset)
  print(head(dat))
  territory_summary <- dat %>%
    dplyr::summarise(Col2 = paste(Col2, collapse = "_"))
  print(head(territory_summary))

  # save the territory data to a new csv file in your output directory
  readr::write_csv(territory_data, paste0("output/",
                                          tools::file_path_sans_ext(
                                            basename(input_file_name)),
                                          "_",
                                          territory_summary,
                                          ".csv"))
  return(territory_data)
}

```
It is important that the appropriate libraries be loaded in prior to running the function.
```ruby
library("dplyr")
library("readr")
```
Next you want to define your inputs. The below example is for the North West region that includes the states of WA, OR, NV, ID, MT, UT, WY, CO, ND, SD, NE, KS, OK, MN, and WI. The raw data file in this example is titled `name_of_invoices_report.csv`.
```ruby
input_file_name = paste0("data/name_of_invoices_report.csv")
territory_to_subset = c("WA", "OR", "NV", "ID", "MT", "UT", "WY", "CO",
                               "ND", "SD", "NE", "KS", "OK", "MN", "WI")
```
Finally, it's time to execute the function.
```ruby
subset_data_to_territory(input_file_name, territory_to_subset)

```
For this example, our result is a csv file with the name `name_of_invoices_report_WA_OR_NV_ID_MT_UT_WY_CO_ND_SD_NE_KS_OK_MN_WI.csv`. This file contains all of the revenue data from the original file for just the indicated states. With this subsetted data, you can dive deeper into territory analysis by looking at the revenue over time. This general function is a helpful tool in that it can allow you to define what `territory` is. This general variable can be defined as the city, manager, region, and more. To toggle between these different categories, simply change the chosen column name in the raw data set to `territory`.
