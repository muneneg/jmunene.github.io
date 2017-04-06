---
layout: post
title: Generating Random Directional Steps in SurveyToGO
excerpt: "How to randomly select direction and steps to be followed during data collection. Incase you want to specify the direction and number of steps to be 
followed by your enumerators, the following guide will help you out."
categories: [survey to go]
comments: false
image:
  feature: 
  credit: Jonathan Munene
  creditlink: 
---

### How to randomly select direction and steps to be followed during data collection

We would like to set up 2 random number counters; one that random selects an integer in the range `1 to 3` and the other that randomly selects a number in the range `20 to 50`. The `1, 2 and 3` would then be used to inform the interviewer to walk to their `left (1)`, `straight on (2)` or to their `right (3)`. The `20 to 50` random number selected would then tell them how many paces to walk in the chosen direction.

-   Step 1:

Add the following code in the `end script` of any question in your survey, before the question that shows the direction.

    //This will create an arry of 3 numbers (1,2,3), then select one randomly.
    var direction = RandomizeArray([1,2,3]); 

    // Checks if the randomly selected number is 1
    if ((direction[0]==1)) 
    {
    //Returns the text "to your Right" if the randomly selected number is 1.
        dblSetSpecificTopic(QRef(indexfordummyquestion),1,"to your Right"); 
    }
    // Checks if the randomly selected number is 2
    if ((direction[0]==2)) 
    {
    //Returns the text "to your Left" if the randomly selected number is 2.
        dblSetSpecificTopic(QRef(indexfordummyquestion),1,"to your Left"); 
    }
    // Checks if the randomly selected number is 3
    if ((direction[0]==3)) 
    {
    //Returns the text "straight on" if the randomly selected number is 3.
        dblSetSpecificTopic(QRef(indexfordummyquestion),1," straight on"); 
    }

-   Step 2:

Create an **Open ended grid** question that will store the texts we have created above, and replace `indexfordummyquestion` with the actual `index`. Under the topics, just enter `1`. Make sure to make the question `dummy/hidden`.

-   Step 3:

On the question that shows direction to the interviewer, add 2 place holders like this; `INTERVIEWER:  Walk {0}, Then {1} steps in the chosen direction:` then under scripts, enter this;

    //Returns a number between 20 and 50, that is being used as the number of paces/steps
    var steps = RandomizeArray([20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50]);
    //Returns the direction and number of paces/steps on the questions text.
    SetTextFormat(CurrQues,AnswerChoice(QRef(2),1),steps[0]);

