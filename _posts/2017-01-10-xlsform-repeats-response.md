---
layout: post
title: Using text fields from a repeat group as choices in your XLSForm.
excerpt: "I want to know how many health facilities are within the respondents area/village and have a follow up question that asks of these facilities, which one is closer to the respondent."
categories: [XLSForm]
comments: false
image:
  feature: 
  credit: Jonathan Munene
  creditlink: 
---
For this guide, we'll use the following example;
- I want to know how many health facilities are within the respondents area/village. 
- I have a follow up question that asks of these facilities, which one is closer to the respondent.

I'll author an XLSForm with a repeat group, then pull out the names of the facilities and list them as a select one question.

Step 1.

#### The Repeats section of the XLSForm will look like this;

type | name | label | repeat_count | constraint |
--- | --- | --- | --- |
integer | number_facilities | How many health facilities are in this area? | | .<=4 |
begin_repeat | h_facility | Health Facilities Repeat | ${number_facilities} | |
text | hfname | What is the name of the health facility? | | |
end_repeat | h_facility| | | |

> I have used a constraint that checks of the number of facilities is less than or equal to 4. This helps in controlling the choice filter as you'll see below.

Step 2. 

#### Add calculations that will pull in the text[name of facility] captured on the repeat loop as follows;

type | name | label | repeat_count | constraint | calculation
--- | --- | --- | --- |
integer | number_facilities | How many health facilities are in this area? | | .<=4 | |
begin_repeat | h_facility | Health Facilities Repeat | ${number_facilities} | | |
text | hfname | What is the name of the health facility? | | | |
end_repeat | h_facility| | | | |
calculate | hfname1 | This pulls in the 1st facility name | | | indexed-repeat(${hfname}, ${h_facility}, 1) |
calculate | hfname2 | This pulls in the 2nd facility name | | | indexed-repeat(${hfname}, ${h_facility}, 2) |
calculate | hfname3 | This pulls in the 3rd facility name | | | indexed-repeat(${hfname}, ${h_facility}, 3) |
calculate | hfname4 | This pulls in the 4th facility name | | | indexed-repeat(${hfname}, ${h_facility}, 4) |

> I have used  `indexed-repeat()` function, that pulls the facility name from the facility repeat loop, for the specied index.

Step 3. 

#### Add a the facility names as choice labels on the choices sheet.

list_name | name | label |
--- | --- | --- | --- |
hfacility | hf1 | ${hfname1} |
hfacility | hf2 | ${hfname2} |
hfacility | hf3 | ${hfname3} |
hfacility | hf4 | ${hfname4} |

> I have referenced the `name` of the survey sheet to be the `label` in the choices sheet.

Step 4. 

#### Add a the select one follow up question that asks about the facility thats close to the respondent.

type | name | label | repeat_count | constraint | calculation | choice_filter |
--- | --- | --- | --- | --- | --- | --- | --- |
integer | number_facilities | How many health facilities are in this area? | | .<=4 | | |
begin_repeat | h_facility | Health Facilities Repeat | ${number_facilities} | | | |
text | hfname | What is the name of the health facility? | | | | |
end_repeat | h_facility| | | | | |
calculate | hfname1 | This pulls in the 1st facility name | | | indexed-repeat(${hfname}, ${h_facility}, 1) | |
calculate | hfname2 | This pulls in the 2nd facility name | | | indexed-repeat(${hfname}, ${h_facility}, 2) | |
calculate | hfname3 | This pulls in the 3rd facility name | | | indexed-repeat(${hfname}, ${h_facility}, 3) | |
calculate | hfname4 | This pulls in the 4th facility name | | | indexed-repeat(${hfname}, ${h_facility}, 4) | |
select_one h_facility | h_facility_near | Which health facility is the nearest to you? | | | | cf1 = ${hfnumber} or cf2 = ${hfnumber}  or cf3 = ${hfnumber}  or cf4 = ${hfnumber} |

> I have introduced a new column `choice_filter` that we'll use to filter out the facilities choice list based on number of facilities mentioned.

Step 5. 

#### Define the `cf` column in the choices sheet.

| list_name | name | label | cf1 | cf2 | cf3 | cf4 |
|--- |--- |--- |--- |--- |--- |--- |--- |
| hfacility | hf1 | ${hfname1} | 1 | 2 | 3 | 4 |
| hfacility | hf2 | ${hfname2} | 0 | 2 | 3 | 4 |
| hfacility | hf3 | ${hfname3} | 0 | 0 | 3 | 4 |
| hfacility | hf4 | ${hfname4} | 0 | 0 | 0 | 4 |


>I have used `cf` columns based on my maximum number of facilities, note the pattern on the `cf` columns.

Now your form is ready, upload it and test it out. You can use either [Ona](https://ona.io) or your prefered aggregate server.