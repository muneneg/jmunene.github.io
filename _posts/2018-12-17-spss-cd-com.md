---
layout: post
title:  "How to filter rows in Excel that have count greater than 1"
date:   2018-12-14 13:58:19
categories: [Excel]
comments: false
---
The Problem;

> Assuming I have an excel workbook of some thousand rows, which has a unique ID column and would like to filter out rows where the ID has been duplicated and show how many times each ID is appearing.. To achieve this;

- At the end of my file, I'll a column named `count`.
- Assuming my ID column is column `B`, I'll add this formula to my `Count` column and drag down. ```=COUNTIF($B$2:$B$28,B2)```. Make sure you edit the size of you file, i.e. rows, mine is upto 28.
- Each row will now have a value of the number of times the ID value has been repeated, under the Count column.
- I can now use the normal filter and select all values greater than 1.


