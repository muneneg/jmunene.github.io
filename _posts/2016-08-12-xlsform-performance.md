---
layout: post
title: "Improving performance of your XLSForm"
excerpt: "Expert advice on how to improve performance on your XLSForms. You might be able to improve the performance of your form by altering some 
aspects of its design. To begin with, it's helpful to understand the two key reasons why users might encounter sluggishness when filling out a form."
categories: [XLSForms]
link: 
share: true
---
How to improve performance of your XLSForm.
----
You might be able to improve the performance of your form by altering some aspects of its design. To begin with, it's helpful to understand the two key reasons why users might encounter sluggishness when filling out a form:
Memory. 

All form fields, choices on the choices sheet, and translations are stored in memory while a form is being filled out. This includes repeated fields, so if you have a 100-field repeat group that's repeated 20 times, then that's 2,000 fields in memory (even if the fields are not currently relevant and so aren't visible). To protect the OS and other apps, Android only gives a limited amount of memory to each app – and when memory gets low things start getting very sluggish because of how Android tries to conserve remaining memory.

Expression dependencies. 
----
Every reference to another field or group within a relevance, calculation, or constraint expression creates a dependency that is watched for potential changes, so that the appropriate expressions can be re-evaluated whenever something on which they depend might have changed. If you have 3,000 fields in memory (including all instances of repeated fields), then there will be up to 3,000 relevance, constraint, and calculation expressions that are always being considered for re-evaluation (including the relevance expressions for all of those fields not currently visible). So when you swipe from one field to the next and there is a delay, ask yourself: what can it be doing just then? Think about the field that you're swiping away from and what might depend on that field's value. Sometimes, with a long, complex form, one field can trigger several other fields to recalculate, and those can trigger several more, and the dependencies run so deep that hundreds or even thousands of expressions will be re-evaluated. Thus, in this way, performance will depend on the logic of your survey.
Understanding these causes of sluggishness, there are a few things that you can do to improve performance:

Move choices to pre-loaded .csv files. 
----
If you have a large number of choices on your choices worksheet (e.g., over 1,000), you should consider moving longer lists to pre-loaded .csv files. That will move those lists out of memory and will, in general, perform much better. 
Reduce the number of repeats. 

Some form designs involve a large number of repeated groups, most of which are never visible. For example, say that you want to ask a long series of questions about certain assets that might be found in a household; if there are 175 different types of asset, you might create a repeat group that's repeated 175 times, with only the relevant assets visible for any given household. In principle, this is a fine design – but the 175x fields in memory can cause the form to perform poorly. Generally, in these cases, there is an alternative design that achieves the same result without so many fields in memory. (In this example case, you could have a multiple-choice question with 175 choices, then repeat the list of questions just once for each selection made by the user. That way, there are only as many fields as necessary to cover the assets in any given household.)

Reduce the number of dependencies. 
----
If you've designed your form such that long, complex expressions create such intricate dependencies between fields that any change to one field results in re-evaluation of dozens or hundreds of complex down-stream expressions, the solution may be to simplify your form. However, you should be able to take full advantage of the electronic medium to constrain user entries, catch potential errors, etc. – so in some cases the solution may be to deploy your survey on more powerful devices that can handle whatever logic your survey requires.


