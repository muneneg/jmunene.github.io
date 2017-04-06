---
layout: post
title: "Getting rid of the NaN in XLSForms calculations."
excerpt: "How to get rid of NaN in XLSForms Calculations. Sometimes its annoying when you want to display the value of calculation to the enumerator, 
but you get a NaN, this post will show you a workaround to this issue."
categories: [XLSForms]
comments: false
---

If we use this method `(${cost_sugar} + ${cost_flour} + ${cost_milk} + ${cost_oil})` to calculate how much the household spent on the products, 
the calculation will return a **Not a Number** (NaN) value if there is a product that was not used in that household.

> There is a workaround for this, and it involves using IF statement to assign the value “0” to any unanswered question. This works, because if an answer is skipped, then the “value” assigned to that skipped question is blank, and blank will always be considered “less” than any other numeric value. Because a calculation can’t be performed on a blank value (a blank value isn’t 0, it is simply nothing), we must assign a value 0 if we want the rest of the calculation to be performed.

For this case, these are the calculations that we will add to our survey sheet:

type | name | label | calculation 
--- | --- | --- | --- 
calculate | sugar_cost | add a 0 if sugar was skipped | if(${cost_sugar}>=0,${cost_sugar},0) 
calculate | flour_cost | add a 0 if flour was skipped | if(${cost_flour}>=0,${cost_flour},0) 
calculate | milk_cost | add a 0 if milk was skipped | if(${cost_milk}>=0,${cost_milk},0) 
calculate | oil_cost | add a 0 if oil was skipped | if(${cost_oil}>=0,${cost_oil},0) 
calculate | total_cost | sum all products | ${sugar_cost}+${flour_cost}+${milk_cost}+${oil_cost}

> You can see that we have introduced calculations with this syntax: `if(${cost_sugar}>=0, ${cost_sugar}, 0)`.
This means that if for instance cost_sugar is equal to or greater than 0, then the calculation will use the entered value, else, if cost_sugar is left blank/not answered, then 0 will be used as a value for sugar_cost in the total_cost calculation.

