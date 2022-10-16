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
[...]
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


## Updates to this README file
We will be updating this README file regularly as the project evolves. You may want to keep checking back.
