
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


#Surgery Dashboard

##Problem statement
This dashboard will enhance operating theatre utilization and empower surgeons with actionable insights. This solution will provide real-time data on revenue generation, procedural trends, and individual performance metrics, enabling data-driven decision-making to optimize operations and improve overall efficiency.

###Summary 
Total of 710 surgeries were performed generating a total revenue of over GHC300,000 over the 12months period


#Steps followed
 - Step 1 : Load data into Power BI Desktop, dataset is a csv file.

- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : The data type for Age column was changed to whole number from text .
- Step 4 : We created new measures
 using the following DAX 

Total surgeries performed = COUNTROWS(Surgery2024)
%Percent of surgeries = Surgery2024[Total surgeries performed]/710*100

Number of surgery by OT = CALCULATE(SUM(Surgery2024[Cost of Surgery]), ALLEXCEPT(Surgery2024,Surgery2024[OT Name]))

Procedure cost = CALCULATE(SUM(Surgery2024[Cost of Surgery]), ALLEXCEPT(Surgery2024,Surgery2024[Procedure Performed]))

Revenue by OT = CALCULATE(SUM(Surgery2024[Cost of Surgery]), ALLEXCEPT(Surgery2024,Surgery2024[OT Name]))

Procedure revenue by Surgeon in each month= CALCULATE(SUM(Surgery2024[Cost of Surgery]), ALLEXCEPT(Surgery2024,Surgery2024[Month Name],Surgery2024[Surgeon],Surgery2024[Procedure Performed]))

TOTAL REVENUNE BY SURGEON = CALCULATE(SUM(Surgery2024[Cost of Surgery]), ALLEXCEPT(Surgery2024, Surgery2024[Surgeon]))


5. Key Metrics: Total Surgeries Performed and Total Surgery Revenue
![Totals](https://github.com/user-attachments/assets/47ad0b51-58f1-47e7-98ca-65504769bb42)

Visual Type: Card
Steps to Create:
Drag a Card visual onto the canvas.
Add the total count of surgeries field for the first card.
Repeat for the second card, using the sum of the surgery revenue field.
Format the visuals for alignment and appearance.
Purpose: Displays key performance indicators (KPIs) prominently.
6. Filter by Surgeon
![FilterbySurgeon](https://github.com/user-attachments/assets/bd501a41-cc5b-491c-86ae-d2506ceb4168)
Visual Type: Slicer
Steps to Create:
Drag a Slicer visual onto the canvas.
Add the field containing surgeon names to the slicer.
Enable the selection of multiple or single names in the slicer settings.
Purpose: Enables filtering of data by individual surgeons.
7. Surgeries by Month
Visual Type: Ribbon Chart

![Surgeries_bymonth](https://github.com/user-attachments/assets/d82cc9f8-fa80-4693-92cc-aa6500f67a37)
Steps to Create:
Add a Clustered Bar Chart to the canvas.
Drag the month field to the x-axis.
Drag the count of surgeries field to the y-axis.
Format the chart to include gridlines and labels.
Purpose: Shows the distribution of surgeries over time.
8. Total Surgeries Performed in Each OT by Month
Visual Type: Line Chart
![Screenshot 2024-12-30 200128](https://github.com/user-attachments/assets/8b4b77cd-66e2-45d8-a62a-731f52ad290c)
Steps to Create:
Insert a Line Chart onto the canvas.
Add the month field to the x-axis.
Add the count of surgeries to the y-axis.
Use the operating theater field in the legend for comparison.
Format with colors to differentiate between theaters.
Purpose: Displays trends in surgical activity across different theaters.
9. Total Surgeries by Surgeon
Visual Type: Multi-row card
![Screenshot 2024-12-30 200326](https://github.com/user-attachments/assets/4d81761b-2347-4873-80f3-47c095d78319)
Steps to Create:
Drag a Table visual onto the canvas.
Add fields for surgeon names, total surgeries performed, percentage of surgeries, and surgery revenue.
Format columns for alignment and sorting.
Purpose: Provides detailed performance data for each surgeon.
10. Revenue by Type of Surgery
Visual Type: Clustered Bar Chart
Steps to Create:
Insert a Clustered Bar Chart.
Drag the procedure type field to the x-axis.
Add the total revenue field to the y-axis.
Customize colors and axis labels.
Purpose: Highlights the revenue contribution of each type of surgery.
11. Revenue by OT
Visual Type: Donut Chart
Steps to Create:
Add a Donut Chart to the canvas.
Use the theater type field in the legend.
Add the sum of revenue field to the values.
Adjust chart size and format for clarity.
Purpose: Visualizes the revenue distribution between operating theaters.
12. Date Range Filter
Visual Type: Date Slicer
Steps to Create:
Add a Slicer to the canvas.
Drag the date field into the slicer.
Configure the slicer settings to show a date range slider.
Purpose: Allows users to filter data by a specific time period.


#PowerBi dashboaed
![Dashboard](https://github.com/user-attachments/assets/44a4a910-3f57-443d-818d-4e1ecadc385a)
#Insights 
-Theater Utilization:

The General Operation Theatre is more consistently utilized compared to Theatre 2, which shows a spike in June but lower usage overall.
This suggests potential underutilization of Theatre 2 or differences in case distribution.
-Surgery Revenue:

Caesarean Sections are the most significant contributor to revenue ($162K), making them a critical focus for resource allocation.
Other procedures like External Hernia Repair, Myomectomy, and Laparotomy generate significantly less revenue.
-Surgeon Performance:

Dr. Frank Adu-Poku leads in surgeries performed (223) and revenue generated, accounting for 31.41% of all surgeries.
Surgeries peak in May and June, with notable dips in February and August. This could indicate scheduling patterns, seasonal demands, or resource availability.

-Revenue Distribution by Theater:
The General Operation Theatre generates 68.32% of total revenue, significantly outperforming Theatre 2.
This dashboard provides a clear view of operational performance, helping stakeholders make informed decisions to optimize resources, enhance surgeon performance, and improve financial outcomes.
        
