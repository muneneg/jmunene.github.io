---
layout: post
title: "XLSForms Authoring Tips and Tricks"
excerpt: "Expert advice on how to author XLSForms.Have you ever wondered how what a good XLSForm looks like, then this should help you author one of them"
categories: [XLSForms]
link: 
share: true
---
Be consistent with your variables.
----
A neat form is an easy form to troubleshoot as well as the data is easily understood.
When naming the variables under the name column, please be consistent with the text and symbols used for instance, you can decide to use the question number(underscore)(concat of question text).
If this was my question 1, “What products are you aware of?” I can have this as my variable name “q1_products_aware_of”.

Start small and grow as the form becomes complex.
----
It’s always good to start with the basic structure, i.e. the two sheets (survey and choices) and the basic columns (type, name, label in survey sheet and list_name, name, label in choices sheet).
The next column you will need after this on the survey sheet is mostly relevance, then constraint, calculation, choice_filter…. This arrangement of columns will save you time since you won’t have to keep scrolling left and right to supply arguments to the relevant columns.

Breakdown your form into small sections.
----
When you breakdown your form into small sections, you will be able to test, troubleshoot and fix errors easily rather than having a big form full of errors

Add explanations/descriptions to calculations.
----
Calculations don’t require a label for them to work, but its good practice to add an explanation of what the calculation does on the label column. This will make it easier for your to remember what you did and also if you happen to share your form with someone else, they can easily understand what you did.

Add group name on the begin and end group constructs
----
Mostly you will find that you have a name on begin_group construct, but when you close the group using end_group construct, you leave it blank. It’s good to have name of the group you are closing for easier troubleshooting or reference.

Use different font or background colors.
----
When using different constructs in your form, it’s good to use different font colors or background colors, for instance, red fonts = calculations, yellow background = groups, green fonts = choice filter...etc.
This will help you to know navigate your form easily if you need to update something.

