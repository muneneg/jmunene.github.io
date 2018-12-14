---
layout: post
title:  "How to filter rows in Excel that have count greater than 1"
date:   2018-12-14 13:58:19
categories: [Excel]
comments: false
---
The Problem;

> Assuming I have an excel workbook of some thousand rows. Now I have to filter the rows that have count greater than 1 and then how many times each row is repeated.. To achieve this;

- At the end of your file, add a column named `count`.
- Assuming the column am checking for duplicates is column `B`, I'll add this formula to my count column and drag down. ```=COUNTIF($B$2:$B$28,B2)```. Make sure you edit the size of you file, i.e. rows, mine is upto 28.
- Each row will now have a value of the number of times the value in Column B appears, under the count Column.
- I can now use the normal filter and select all values greater than 1.


