---
layout: post
title:  "Pull most recent files in R"
date:   2020-11-09
categories: jekyll update
---
# Pulling most recent files in R
 ###### by Joel Christian Andrade

Many coding pipelines involve taking raw data files, formulating code and eventually working with a few, if not many, output files.

Take for example the list of files, in my directory `/raw_data` below from the publicly available Apple mobility database tracking movement.

```
applemobilitytrends_2020-08-29.csv
applemobilitytrends_2020-09-12.csv
applemobilitytrends_2020-09-18.csv
applemobilitytrends_2020-09-25.csv
applemobilitytrends_2020-09-30.csv
applemobilitytrends_2020-10-02.csv
applemobilitytrends_2020-11-08.csv
```

While retroactive data analysis is useful, the most recent file will include the data of the previous files.  Thus, to retrieve the most up to date information while using R, we must use some functions which are pre-loaded into R.

First, we must elucidate these functions
* `file.info` = provides some basic information about a file(s)
 * size
 * if the file is directory
 * if the file is an executable
 * editing times
   * `mtime` = modification time
   * `atime` = access time
   * `ctime` = creation time


* `list.files` = list of all files within a directory

* `which.min` or `which.max` = determine minimum or maximum with respect to a given set of variables

Let's take the directory `raw_data` and view various outputs using these functions

`file.info()`
```r
> file.info("/raw_data")

              size  isdir  mode              mtime                ctime                atime  exe  
data/raw_data    0   TRUE   777 2020-10-4 13:03:40  2020-09-19 17:14:40  2020-10-04 13:03:40  no
```

`list.files()`
```r
> list.files("/raw_data")
[1] "applemobilitytrends_2020-09-12.csv" "applemobilitytrends_2020-09-18.csv" "applemobilitytrends_2020-09-25.csv"
[4] "applemobilitytrends_2020-09-30.csv" "applemobilitytrends_2020-10-02.csv" "applemobilitytrends_2020-08-29.csv"
```


Now, we want to combine those functions to display a specific editing time `(atime, atime, ctime)`


Let's combine all the elements together using vectors and `rownames()` to pull the most recently created file via `ctime`.
```r
> raw_data_file_info <- file.info(
  list.files("/raw_data", full.names =T)
  )

> most_recent_file <- rownames(raw_data_file_info)[which.max(raw_data_file_info$ctime)]

> most_recent_file
> "raw_data/applemobilitytrends_2020-10-02.csv"
```

Notice that we used the `full.names = T` option because we want the entire path of the file to be placed in the vector.  Otherwise, you need to be in a specific project to utilize this code.
You can alter many things to cater to your own project.


Hope this tutorial helps!
