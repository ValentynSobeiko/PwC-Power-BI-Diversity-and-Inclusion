# PwC Power BI Project - Diversity and Inclusion Analysis

## Problem Statement :

Define relevant hiring, promotion, performance, and turnover KPIs, and create a visualization.

Please write what you think some root causes of their slow progress might be.

Calculating the following measures could help to define proper KPIs:

- Number of men
- Number of women
- Number of leavers
- % employees promoted (FY21)
- % of women promoted
- % of hires men
- % of hires women
- % turnover 
- Average performance rating: men
- Average Performance rating: women

## Datasource :

The dataset used for this task was presented by [Pwc](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and Diversity and Inclusion dataset:

Dataset: [Diversity and Inclusion](https://github.com/ValentynSobeiko/PwC-Power-BI-Diversity-and-Inclusion/blob/ba45d6355a7968685d5a035afe13c34f0e1a2d83/03%20Diversity-Inclusion-Dataset.xlsx)

## Data Analysis (DAX):

- Number of men = Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[Gender]="Male"))

- Number of women = Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[Gender]="Female"))

- Number of leavers = Calculate(countA('Pharma Group AG'[Employee ID]),'Pharma Group AG'[Leaver FY] in { "FY20" })
  
- % employees promoted (FY21) = Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[Promotion in FY21?]="Yes")),Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[In base group for Promotion FY21]="Yes")))

- % of women promoted = Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[Gender]="Female")),distinctcount('Pharma Group AG'[Employee ID]))
  
- % of hires men = Divide('Pharma Group AG'[# of men],('Pharma Group AG'[# of men]+'Pharma Group AG'[# of woman]))
  
- % of hires women = Divide('Pharma Group AG'[# of woman],('Pharma Group AG'[# of woman]+'Pharma Group AG'[# of men]))
  
- % turnover = ivide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[FY20 leaver?]="Yes")),Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG',NOT('Pharma Group AG'[Department @01.07.2020]=BLANK()))),2))

- Average performance rating: men = Calculate(Average('Pharma Group AG'[FY20 Performance Rating]),Filter('Pharma Group AG','Pharma Group AG'[Gender]="Male"))

- Average Performance rating: women = Calculate(Average('Pharma Group AG'[FY20 Performance Rating]),Filter('Pharma Group AG','Pharma Group AG'[Gender]="Female"))

## Data Visualization (Dashboard) :

| HR Dashboard 1 |
| ----------- |
![image](https://github.com/user-attachments/assets/c4d5d552-7365-434f-a785-34533449f495)

| HR Dashboard 2 |
| ----------- |
![image](https://github.com/user-attachments/assets/51f23f94-8e35-4ed7-b028-ff6acee28271)

| HR Dashboard 3 |
| ----------- |
![image](https://github.com/user-attachments/assets/43620ae6-343d-4d08-9a12-26510e2999f9)

## Conclusion of Analysis:


- The workforce hires show a gender distribution of 41% female and 59% male hires for the year.

- Female employees had the highest promotion rate in the Junior Officer category, representing 53.8% of promotions, while male promotions in the same category were at 47%.

- The Director level exhibited the longest average duration before receiving a promotion this year.

- The Finance department experienced the highest turnover rate, with 22% of its employees leaving during the year.

- Performance ratings between genders were similar, with female employees averaging a rating of 2.42% and male employees at 2.41%.

- In 2021, 54.34% of promoted employees were male, and 45.66% were female.

- The age group with the highest representation is 20–29, with 223 employees within this range.
