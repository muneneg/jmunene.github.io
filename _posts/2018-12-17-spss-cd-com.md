---
layout: post
title:  "SPSS working directory"
date:   2018-12-17 09:41:19
categories: [SPSS]
comments: false
---
The Problem;

> When working with SPSS syntax, the `GET FILE`, `GET DATA`, `WRITE OUTFILE` or `SAVE OUTFILE`, generally any command to open or save needs to have the full path where you want the file saved or retrieved from. For instance, if I want to save vars1 to Vars8 of my SPSS file, in my documents folder, I'd type:
`SAVE OUTFILE="C:\Users\User\Documents\Vars1_Vars8.sav"/COMPRESSED KEEP= Vars1 to Vars8.` If my path is long or I have to keep saving and getting files, I can just change my working directory in SPSS using the `cd` command and from there on I just have to worry about the file names only. 
To achieve this;

- At the begining of your syntax file, type: `cd "C:\Users\User\Documents".`. 
- If am to save the same Vars1 to Vars8, the syntax now would be: `SAVE OUTFILE="Vars1_Vars8.sav"/COMPRESSED KEEP= Vars1 to Vars8.`.

This has saved me a ton of key strokes and worry of if I have the right path over the couple of years.


