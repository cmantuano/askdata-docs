---
title: The Survey Dataset
keywords: documentation
last_updated: October 15th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: mydoc_about.html
---

**Guide the Askdata Survey**

A survey dataset can manage an Askbase interactive flow of questions that can be used to collect data from an end-users.

You can just create a survey dataset clicking on the Survey dataset in the dataset selection like any other datasets.

We suggest to use an Excel compatible tool to quickly configure the survey. You can download the template using the "download" button in the top right corner of the "Advanced Configuration" section.

The template is composed of two sheet.

**‍**  
**Survey (Sheet 1)**

**‍**  
QUESTION NUMBER: Specify the question number.  
ALIAS (not mandatory): Specify the "Name" of the JSON Object that will be generated at the end of the survey for sending the data.  
‍

**QUESTION:** Specify the question.

‍  
**MANDATORY:** Specify the mandatory nature of the application. It can take 2 values:  
 true: if the question is mandatory  
 false: if the application is not mandatory  
‍

**ANSWER TYPE:** Specify the type of question. It can take 3 values:  
 *Simple Text*: the user can enter free text  
 *Quick Reply*: the user is obliged to choose one of the specified answers  
 *Regex*: the user is obliged to enter the text that respects the rules  
specified in the regex  
**‍**

**ANSWER VALUE**: It is linked to the type of question previously chosen:  
 In Simple Text always specify the value "<any>"  
 In Quick Reply specify the text of the quick reply. Just in case insert 2 or more quick replies you have to replicate the question line changing only the answer value and the next question. In Regex, specify a valid regex by entering at the beginning: <regex. ^ And at the end  
$>. Example: <regex. ^\ Insert your regex$>

‍  
**WRONG VALIDATION** (not mandatory): Specify the error response.  
Valid only in the case of regex.  
**‍**

**NEXT QUESTION** (not mandatory): Specify the number of the next question. To end the survey, this cell must not be completed.  
**‍**

**IMAGE URL** (not mandatory): Specify the URL of the image to be attached to the application.  
END QUESTION NUMBER (not mandatory): Specify the end of the survey question number. It only works if the application has false "mandatory"  
SURVEY\_SETTINGS (Sheet 2)  
‍

**ENDPOINT**: Specify the endpoint to be called upon completion of a survey.  
‍

**SKIP TEXT** *: Specify the trigger to skip a question. Multiple values ​​can be entered in the same cell separated by a semicolon (;).  
**‍**

**END TEXT** *: Specify the trigger to end the survey. Multiple values ​​can be entered in the same cell separated by a semicolon (;).  
‍

**TRIGGERS**: Specify the triggers for activating the survey.  
‍

Template Survey to be filled out: Download  
‍

* If the question is not mandatory, the quick reply will automatically appear to go to the next question, enhanced with the first trigger specified in the "SKIP TEXT". If the end of the survey question number (END QUESTION NUMBER) has also been specified, a second quick reply will appear with the first value specified in the "END TEXT".  




    {% include links.html %}

    