---
layout: post
title:  "Digital questionnaires scripting pro tips"
date:   2018-12-17 09:58:19
categories: [XLSForms,ODK,SurveyToGo,SurveyCTO]
comments: false
---
When working on evaluations of development projects,Market Research data or any other form of data collection, it is extremely important to get high quality data from the point of collection, which is made possible by scripting the tools right.

**Start with a paper questionnaire**

It is always useful to start with a paper questionnaire. Once you have scripted (or programmed) a relatively final draft of your paper questionnaire, you can make modifications directly on the script and it is advisable to make changes in the paper questionnaire simultaneously, or make notes of your changes.

**Quick Scripting tips**

1. Create pre-coded options or a finite range of responses wherever possible.
2. If you plan to use *Stata/SPSS, keep your field names lowercase and 32 characters or shorter.
3. Create checks and balances—like prompts that help guard against illogical responses—in the questionnaire wherever possible.
4. Think through how you want your data to look (sometimes sketching it out can help) and then work backwards.
5. Avoid overlaping repeat groups. Make sure that the groups are completely encased within one another.
6. When writing long complicated code like constraint, relevance, it is easier to first write the code using a text editor (I like Notepad++), and then copy it to Excel, or scripting studio.
7. Script in ONE language first, once the tool has been tested, you can now go ahead and add the translations.
8. Write the questions in a way that is easily read and understood.
9. Break up the large repeat groups or questions with long choice lists into smaller ones.
10. Test smaller bits of your script as you keep building up.

**Test the questionnaire**

- Always test your questionnaire before training or roll out for data collection to make sure it works without errors. 
- Don’t rely only on the “Preview” function of your scripting system; also, try it out on the tablet/phone you will be using in the field-NOTE "USING IN FIELD" Some of the tablets/phones used by scripters for testing might be more advanced or have bigger screens than the actual ones.
- In addition to making sure that the questionnaire runs smoothly, export the data and look through it to make sure that your data is in the format you want it in.
- Enumerators are also good script testers.
- Finally use real world respondents to test the questionnaire.

*While this may seem like a lot of work, it is always beneficial when the same person who scripts the questionnaire also trains the enumerators and cleans the data. This way, the data is in a format you are comfortable working in, and if the data are a mess you only have yourself to blame!*

