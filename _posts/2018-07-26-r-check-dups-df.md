---
layout: post
title:  "How to check for duplicate values in a column in a dataframe in R"
date:   2018-07-26 18:45:19
categories: [R]
comments: false
---
The Problem;

> Assuming you have a variable that you collected unique `IDs` like `HHIDs` and would like to see if there are any duplicates;


~~~
#The required libraries
require(tidyverse)

#Load the libraries
library(tidyverse)  

hhIDs_Dups <- 
  DF %>% 
  group_by(hhID) %>% # the group of interest (hhIDs)
  mutate(duplicate = n()) %>% # count number in each group
  filter(duplicate > 1) %>% # select only duplicated records
  select(-duplicate) # remove group count column

~~~

If you now `View(hhIDs_Dups)`, you will only see the duplicate records.

Its advisable to add some metadata to your `DF` like location and other respondent info for easier identification of which record to update/change.


