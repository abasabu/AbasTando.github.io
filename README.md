
# OPD Satisfaction-Dashboard

## Problem Statement

The quality of healthcare services is a critical determinant of patient satisfaction and overall health outcomes. In the Outpatient Department (OPD) of healthcare facilities, long wait times, staff attitudes, and inefficiencies in service delivery often result in dissatisfaction among clients. However, without actionable insights derived from data, it becomes challenging to identify specific problem areas and implement targeted improvements. The findings from this analysis will help healthcare administrators prioritize areas of improvement and enhance the patient experience at the OPD.

### Steps followed 
- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : It was observed that in none of the columns errors & empty values were present.
- Step 4 :Age variable was dragged into the field & change from sum to average
- Step 5 : Visual filters (Slicers) were added for four fields named "gender", and calender to switch between dates
           
- Step 6 : A bar chart was added to the report design area to visualize the number of satisfied respondents by year (2021 and 2024). The "Insured Status" field was included in the Legends bucket, segmenting the respondents based on their insurance status.

- Step 7: A tooltip was added to enhance interactivity by providing a drilldown view of dissatisfaction levels. The tooltip displays the number of dissatisfied respondents who are still willing to return for services despite their dissatisfaction.


   #Availability of seating space
  
clients who indicated no seating available are unwilling to return for services.     
![Snap](https://github.com/user-attachments/assets/60963ce5-301c-487d-b1dd-d4483f10100d)
            
A doughnut was used to represent count of respondents by satisfaction and dissatisfaction levels. as well as overall satisfaction perecntage
![Overal satisfaction](https://github.com/user-attachments/assets/0b9e5c5c-ff36-407d-86e9-6637ae809e60)
       
 - Step 8 : New measure was created to find  % of male and female respondents, 0 was add to ensure when one gender was selected the other wont display blank but 0 
 
 Following DAX expression was written to find % of customers,
 
         %male = CALCULATE(OPDSURVEY_NEW2024[Total Male]/OPDSURVEY_NEW2024[Satisfaction_All]*100)+0
 
 A card visual was used to represent this perecntage.

 Snap of % of repondents Male & Female
![Gender](https://github.com/user-attachments/assets/33125a65-c3e9-409c-b514-839adda5a97c)

 - Step 9 : New measure was created to calculate total respondents satisfied or not
 
 Following DAX expression was written to find total distance,
 Satisfaction_All = COUNTROWS(OPDSURVEY_NEW2024)         

 # Report Snapshot (Power BI DESKTOP)
![Dashboard](https://github.com/user-attachments/assets/3b7c32e2-2309-4eec-9511-a7e10f0e86ef)

# Insights

A single page report was created on Power BI Desktop

Following inferences can be drawn from the dashboard;

### [1] Total Number of respondents = 800 but there is one Null value for some of the variables

 #Demographics of Respondents:
 The average age of respondents is 41.1 years.
 There is a higher proportion of female respondents (63.8%)   compared to males (36.2%).
 
 #Overall Satisfaction:
 81.2% of respondents reported being satisfied with the OPD  services.
 A smaller proportion (18.8%) expressed dissatisfaction.

 #Cleanliness of the OPD:
 Among old clients, the majority rated cleanliness as "Very Good" (321 respondents) or "Good" (273 respondents), with minimal  complaints.
  New clients also expressed high satisfaction with cleanliness, but their numbers are smaller.

 #Proportion of Dissatisfaction Points:
 The highest dissatisfaction was associated with the Records section (38.1%).
 The Pharmacy and History Table/Revenue sections were tied for the next highest dissatisfaction levels (19.05% each).
 Consulting Room and ANC had the least dissatisfaction (4.76% each).

#Availability of Seating:
 A significant majority (87.61%) of respondents reported seating availability, while 12.39% experienced a lack of seating.

#Satisfaction Trends Over Time:
 Overall satisfaction improved slightly from 80.3% in 2021 to 81.8% in 2024, showing a positive trend.
 Dissatisfaction dropped marginally from 19.7% in 2021 to 18.2% in 2024.

#Insurance Coverage:
 A vast majority of respondents were insured (92.62%), while a small portion (7.38%) were uninsured.

#Satisfaction with Time Spent:
Over half of the respondents (55.82%) were "Very Satisfied" with the time spent at the OPD.
Another 36.55% reported being "Satisfied," leaving only a minority dissatisfied (7.01% Dissatisfied and 0.63% Very Dissatisfied).
        
