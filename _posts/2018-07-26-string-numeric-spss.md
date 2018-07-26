---
layout: post
title:  "How to check to convert a string variable to numeric/categorical in SPSS"
date:   2018-07-26 19:10:19
categories: [SPSS]
comments: false
---
The Problem;

> Assuming you have a variable that you collected data as string, or you imported CSV/Excel data into SPSS, categorical data is imported as `string`, and not numeric with values. This makes it hard to carry out a couple of analysis. To achieve this;

- Create a new numeric variable, and add the `value labels`.
- Create an `if statement`, that will assign the string statement to the correct value in the new numeric variable.

For my case, `QRC1`, which is a string variable and has days of the week.

~~~

* Create numeric QRC1 - RC1_Num.

NUMERIC QRC1_Num (f2.0).
Execute.
VARIABLE LABELS
QRC1_Num "Recoded QRC1".
EXECUTE.
VALUE LABELS 
QRC1_Num
1	"Monday"
2 "Tuesday"
3 "Wednesday"
4 "Thursday"
5 "Friday"
6 "Saturday"
7 "Sunday".
EXECUTE.

* Assign QRC1 string into QRC1_Num.
IF (QRC1 = "Monday") QRC1_Num=1.
IF (QRC1 = "Tuesday") QRC1_Num=2.
IF (QRC1 = "Wednesday") QRC1_Num=3.
IF (QRC1 = "Thursday") QRC1_Num=4.
IF (QRC1 = "Friday") QRC1_Num=5.
IF (QRC1 = "Saturday") QRC1_Num=6.
IF (QRC1 = "Sunday") QRC1_Num=7.
EXECUTE.

~~~



