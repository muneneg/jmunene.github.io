---
layout: post
title:  "How to read all files in a folder and merge them into one file in R"
date:   2015-08-18 15:07:19
categories: [R]
comments: false
---
If you have a folder with individual files and would like to merge them into one master file, you can use the following script.

~~~
#The required libraries
require(data.table)
require(readxl)

#Load the libraries
library(data.table)  
library(readxl)  

> We are using the package `readxl` because our files are Excel workbooks.

#Read the files (note this should be point to the folder where the files are located)
files <- list.files(path = "D:/Jmunene@Ona/xlsforms/Tz Water Points/data/57 LGAs PBR (August Update)",pattern = ".xls")
temp <- lapply(files, read_excel)

#Merge the files by rows. (Note: If the files don't have the same columns, the columns that don't match will be appended)
data <- rbindlist(temp ,fill = TRUE)

#Save the file, as a csv file - but you can choose the format you want :)
write.csv(data,file = 'Merged 57 LGAs PbR.csv',row.names = FALSE)
~~~

