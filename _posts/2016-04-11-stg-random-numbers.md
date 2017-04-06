---
layout: post
title: Generating Random Numbers in SurveyToGO
categories: [survey to go]
comments: false
image:
  feature: 
  credit: Jonathan Munene
  creditlink: 
---

You might want to generate a random number from an array, and use it later in the survey. To do this, we'll create a global var as follows;

    var steps = RandomizeArray([20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50]);

The above will return a number between 20 and 50, selected randomly.

