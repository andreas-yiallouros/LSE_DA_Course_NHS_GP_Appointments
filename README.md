# LSE_DA_Course_NHS_GP_Appointments
## Purpose
Analyse data to get closer to understanding the problem of the NHS incurring significant, potentially avoidable costs when patients miss general practitioner (GP) appointments.
### Motivation
We are motivated to help decision-makers at the NHS and in government understand this problem better because it matters.\
Healthcare is important for our society, and for each of us and our loved ones individually. Helping the NHS be more cost effective can free resources that can be invested in services that improve and save lives.
## Initial questions
The key initial question is about the reasons why people may miss their appointments.\
\
Relating to this key overarching question are the following two questions:
1. What is the NHS staff capacity?
2. What is the NHS staff utilisation?


These two questions are important because if NHS staff is operating at the limit of their capacity / they are fully utilised reducing the number of missed appointments becomes more important and urgent.
## Technology
We will use Python including
* pandas
* seaborn
* Beautiful Soup
## Limitations and challenges
See Jupyter Notebook.
## References
[NHS Digital, 2022, Appointments in general practice: supporting information, digital.nhs.uk, reviewed on 5 September 2022](https://digital.nhs.uk/data-and-information/publications/statistical/appointments-in-general-practice/appointments-in-general-practice-supporting-information#guide-to-data-files)

[GP Practice News, 2022, Prime Minister candidate wants to charge no show patients, practiceindex.co.uk, reviewed on 5 September 2022](https://practiceindex.co.uk/gp/blog/news-prime-minister-candidate-wants-to-charge-no-show-patients)

## Insights from initial exploration (end of week 2)

### Number of locations and period
The number of sub-ICB (sub-‘Integrated Care Board’) level locations, based on the ‘sub_icb_location_name’ in ‘df_national_categories’ and ‘df_actual_duration’ is the same – 106, showing the data in the two DataFrames is consistent. 

At the ICB level, based on the ‘icb_ons_code’ data in each of the three DataFrames, the number of locations is 42. This seems to be the number of ICBs per [NHS England](https://www.england.nhs.uk/integratedcare/integrated-care-in-your-area/), providing evidence that our data may be complete.

Looking at the ‘appointment_month’ data, our data seems to cover the 30 months from January 2020 to June 2022.

### Purpose of each DataFrame
By looking at the first ten rows of each DataFrame we can infer the purpose of each:

###### ‘df_actual_duration’
Shows the number of appointments grouped by: (1) ‘Sub-ICB location’; (2) appointment date; and (3) actual duration in minutes:
* 1-5
* 6-10
* 11-15
* 16-20
* 21-30
* 31-60
* Unknown / Data Quality   

###### ‘df_appointments_regional’
Shows the number of appointments grouped by: (1) appointment month; (2) ICB location; (3) appointment status; (4) type of healthcare professional; (5) appointment mode; and (6) time between booking and the appointment in days:
* Same
* 1
* 2-7
* 8-14
* 15-21
* 22-28
* greater than 28
* Unknown / Data Quality

###### ‘df_national_categories’ 
Shows the number of appointments grouped by: (1) appointment date; (2) sub-ICB location; (3) service setting; and (4) national_category.

A key open question for understanding the data is why is the sum of appointments different across the three DataFrames?
* df_actual_duration: 167,980,692
* df_appointments_regional: 742,804,525
* df_national_categories: 296,046,770 


## Data Analysis - summary of approach (end of week 3)
**Question 1 - dates between which appointments are in our data**\
I started by reviewing my notes from Activity 2 to see which DataFrames have ‘appointment_date’ in their columns. I changed the data type of the ‘appointment_date’ column in both relevant DataFrames from object to datetime. Then I used the min() and max() methods to find the earliest and latest dates.\
\
In case it becomes relevant later, I also changed the data type from ‘object’ to ‘datetime’ for the ‘appointment_month’ column in df_appointments_regional and df_national_categories.\
\
Having realised that the periods in the three DataFrames are different I went back and updated my notes for Activity 2 in my Notebook about the number of appointments being different across the three DataFrames.\
\
**Question 2 - service setting with the most appointments in North West London from 1 January to 1 June 2022**\
I started by creating a subset of df_national_categories using the == logic operator. Then I created a second subset based on the first filtering for the period in question, using the ‘>’, ‘<’, and ‘&’ logic operators. Then I used groupby(), sum() and sort_values() to calculate the total number of appointments by service setting and get to the answer.\
\
**Questions 3 and 4 – month with the highest number of appointment and number of records per month**\
I used the groupby(), sum(), sort_values(), and value_counts() functions to get to the answers to questions 3 and 4.

## Further questions
How does the analysis so far get us closer to informing decisions that may reduce the number of missed appointments?

## Visualise and identify initial trendes (end of week 4)
### Monthly visualisations
#### Service settings
The General Practice service setting has by far and consistently the highest number of appointments compared to the other three plus the unmapped.

#### Context type
The Care Related Encounter context type has by far and consistently the highest number of appointments compared to the Inconsistent Mapping and Unmapped categories.

#### National categories
The General Consultation Routine category has by far and consistently the highest number of appointments compared to all the other categories.\
\
Looking across the three visualisations, the lines for appointments in the General Practice, Care Related Encounter, and General Consultation Routine are similar indicating they likely represent approximately the same population of appointments. These three lines show variation from month to month. The lines for most other categories are relatively flat, except for six of the lines in national categories, five of which seem to follow a similar pattern as the General Consultation line.

### Seasonal visualisations
The four plots with appointments per day and service setting for each season from summer 2021 to Spring 2022show a consistent pattern of General Practice appointment at much higher numbers compared to the other service settings, especially during weekdays from Monday to Friday. The also show consistently GP appointment numbers are highest at the start of the week and reduce as the week progresses.

## Insights and questions from analysing the Twitter data (end of week 5)

### Number of tweets and topics
1,174 tweets is a relatively small number\
The hashtags seem to be clustered around health / medicine and technology

Whilst hashtags can provide insights, they can often be too generic or high level for them to be insightful on their own. Other analysis such as sentiment or search for specific key words may help.\
\
What precisely were the questions that the team who prepared the ‘tweets.csv; file had in mind?

How was the data in ‘tweets.csv’ obtained? For example,\
what period does it cover?\
what was it filtered on?



### Focusing on the hashtags with the highest counts
There are 47 hashtags with a count of more than 10.
Focusing on the hashtags with the highest counts can be a reasonable strategy on the basis that it may allow us to identify topics that are popular and therefore important.\ 
However, we might be more effective in understanding why appointments may be missed if we supplemented our analysis with questions such as ones around what Twitter data can tell us specifically about missing appointments.\
\
We will return to improve the visualisations to have productive discussions with the team and the NHS.

## Updates to this README file
We will be updating this README file regularly as the project evolves. You may want to keep checking back.
