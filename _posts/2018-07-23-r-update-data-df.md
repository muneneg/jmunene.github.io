---
layout: post
title:  "How to update fields in a DF"
date:   2018-07-23 18:33:19
categories: [R]
comments: false
---
The Problem;

> Assuming you have a data frame that has data collected as baseline, or have already started data collection and you change your data collection too - by adding new variables, for instance `var100`,`var202` & `var347`, the following will happen;

The already collected data, lets call it `dfA` will have blanks on the newly added variables once merged with the newly collected data. When running you analysis, the outputs for `var100`,`var202` & `var347`, variables will be `NULL`, thus give out the wrong numbers :(.

The Solution;

> Based on the method you are using to collect your data, you can either;
- Create a spreadsheet file with the variables that are missing data from `dfA`, or
- Create a short survey that the team will use to go back to the field and fill in.

Whichever option you use, make sure that you extract all relevant `metadata` from `dfA` that will be used as the `key` identifier and put it in the above created survey, lets call it `dfB`.

Once `dfB` has been filled in, you can now use the power of R to fill in the blanks in `dfA` using the data collected in `dfB`.

~~~
#The required libraries
require(data.table)

#Load the libraries
library(data.table)  


> We can using `join` from `data.table`. Convert the `data.frame` to `data.table` (setDT(df1), `join` on with `df1` using "key" and assign `(:=)`, the values in `var100`,`var202` and `var347 with `i.var100`, `i.var202` and `i.var347`.

Just run the following code

setDT(dfA)[dfB, c('var100', 'var202','var347') := .(i.var100, i.var202,i.var347), on = "key"]

If you now 'View(dfA)`, the data will be updated.
~~~

