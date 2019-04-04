# Milestone 1


### Identify the question that your team in interested in answering with the survey:

> "Does a person's choice of study location (home/academic setting/other public or private spaces) affect the time you take to finish your assignments (exclusion of optional questions)?"


### Identify the other questions you plan to ask in your survey to identify confounding variables and justify/explain why you plan to include them.

#### Confounding Variable 1 : Procrastination

**Definition:** "The action of delaying or postponing something."

**Explanation:** We identified "procrastination" as one of the confounding variables.  This personality trait affects how much time an individual spends on working on their assignments, and how much they have to review their assignments. For example, a procrastinator may start an assignment early of the week but may not have time left to review the questions or even to do optional questions.

**Questions to identify the confounding variable:**

* How much time do you have to review your assignments before submission?
* Do you do optional questions?
* If so, how much extra time do you have to do optional questions?
* Do you consider yourself as a procrastinator? Scale 1-7

#### Confounding Variable 2 : Household Responsibilities

**Definition:** Any type of responsibilities you have outside of school

**Explanation:** This is a confounding variable because having responsibilities outside of school take away an individual's time from working on assignments, which can be confusing with procrastination based on the time you spent on working on the assignments.

**Questions to identify the confounding variable:**  

* Do you have household responsibilities?
* How much time do you spend on your household responsibilities?

####  Confounding Variable 3:  Block Number

**Explanation:** Block number determines the level of difficulty, hence, it affects how much an individual spends on working on the assignments and the study location they choose.


**Questions to identify the confounding variable:**      

* How much time in total did you spend on all labs in Block 1?    
* How much time in total did you spend on all labs in Block 2?    
* How much time in total did you spend on all labs in Block 3?    
* How much time in total did you spend on all labs in Block 4?   
* How much time in total did you spend on all labs in Block 5?   
* How much time in total did you spend on all labs in Block 6?   

#### Confounding Variable 4 : Commute Time to Study Location

**Explanation:** This is a confounding variable because an individual's commute can affect where he/she will study and it can be a contributing factor to the amount of time one is capable to spend doing lab work.  

**Questions to identify the confounding variable:**   

* What is the average round trip commute time to study location?  (0 units for home)

#### Describe how you plan to analyze the survey results (e.g., what statistical test(s) do you plan to employ?).

**Independent Variable:** Study locations
*Categorical Nominal**
Home
Academic Settings (study rooms, classrooms,libraries)
Other public settings (cafe)
Other private settings (friend's home)

**Dependent Variable:** Time spent on assignment    
*Continuous (assuming normal distribution)*
Outside of class and lab hours, how long on average do you spent on completing mandatory lab questions per week?

**Confounding Variable:**
Household responsibility - *Continuous*  
Procrastination - *Dummy (binary)*  
Block difficulty - *Categorical*  
Commute time - *Continuous*  


**Analysis Method:**

Regression Method - To be determined with/without interaction variables   
Null Hypothesis - The choice of study location does not affect the amount of time spent on lab assignments   
Alternate Hypothesis - The choice of study location does affect the amount of time spent on lab assignments  

*Procedure: (Subject to change after data is collected)*  

1. EDA    
* Adjust distribution assumption if needed  
* Decide whether GLM is required  
2.  Develop regression model  
*  Inquire the effect of confounding variables (regression)  
* Decide on interaction terms -> Additive vs. multiplicative model  
* Perform tests and analyse results  


#### Discuss the aspects of the UBC Office of Research Ethics document on Using Online Surveys that are relevant to your proposed survey.

We will be ensuring that all personal information collected by the survey is in custody and under control solely store in Canada and only accessed in Canada.
We do not anticipate collecting any directly identifiable information from any of the participants such as SIN numbers, student numbers, IP addresses or names. In addition, the collection of indirectly identifying information is not foreseen in this survey.  Since our question revolves around the notion of Personal opinions, we do not anticipate collecting anything of which FIPPA constitutes "personal information".  That being said, we will be using the UBC-hosted version of Qualtrics as a precaution and to ensure that the data is secure, stored and backed up within Canada.  
Our data collection will be conducted solely in the form of an online survey and this we plan to use a cover letter in place of a fully signed consent form. The cover letter will include enough information about the purpose and requirement of the survey that enables the potential participant to make a valid and informed decision to contribute to the study.  
To comply with the UBC Office of Research Ethics we will include the following on the cover letter:

* The sentence "By completing the questionnaire, you are consenting to participate in this research."
* Study title
* The contact information of all 4 team members, and our Lab instructors (Vincenzo Coia)
* A description of the study
* Any Risks and benefits we anticipate from the results
* Whom benefits from the study
* Limits to confidentiality
* A statement indicating that participation is voluntary and not obligatory in any way.
* The UBC Research Participant Complaint Line text
* The UBC letterhead (if we can obtain it)

Amendments to the cover letter contents could occur depending on if changes or adjustments to the survey questions materialize in Milestone2.
