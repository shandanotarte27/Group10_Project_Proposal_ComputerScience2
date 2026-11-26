# 📌 Project Proposal (Draft)

## 📝 Project Title  
KILOWATT: Know Your Usage. Make Every Watt Count.

---

## 🔍 Problem Statement  
What real-world problem does your project want to solve?  
- Households often find it difficult to determine how individual appliances contribute to their electricity consumption and expenses, particularly how wattage, quantity, and daily operating hours affect estimated electricity costs..  
- Electricity is essential household expense. Understanding appliance consumption can help households recognize usage patterns, compare appliances, and make more informed decisions about their electricity usage..  
- KiloWatt utilizes appliance names, categories, wattage, quantity, daily operating hours, and a configurable electricity rate to calculate estimated consumption and costs, analyze usage, compare appliances, and simulate hypothetical changes in operating hours.

---

## 🎯 Project Objectives  
Write at least **2–3 clear objectives** your project aims to achieve. Example:  
- Objective 1: To develop a system that records, manages, and stores household appliance data using JSON.  
- Objective 2: To calculate and analyze household electricity consumption and estimated costs through organized summaries, rankings, and comparisons.  
- Objective 3: To simulate changes in appliance usage hours and evaluate their potential effects on electricity consumption and costs.

---

## ⚙️ Planned Features  
Your program must have **at least 5 features (minimum)**.  
We have provided **2 starter ideas** for each dataset — you must design **at least 3 additional features**.  

- Feature 1: Appliance Registry – Add, view, search, update, and delete household appliance records. 
- Feature 2: Consumption Calculator – Calculate the estimated daily and monthly electricity consumption and costs of appliances and the household.  
- Feature 3: Energy Analysis – Generate consumption rankings, percentages, category breakdowns, and household summaries. 
- Feature 4: Appliance Comparator – Compare two appliances based on their estimated electricity consumption and costs.  
- Feature 5: Usage Simulator – Simulate changes in an appliance's daily operating hours and evaluate their effects on consumption and costs without modifying the original records.

---

## ⌨️ Planned Inputs and Outputs  

- **Inputs**  
  - Appliance category (Cooling, Lighting, Kitchen, Entertainment, Laundry/Cleaning, or Other)
  - Wattage (in watts)
  - Quantity
  - Daily operating hours (0–24 hours)
  - Electricity rate (₱/kWh)
  - Appliance ID (for searching, updating, deleting, or comparing records)
  - imulated daily operating hours (for the Usage Simulator)
    
- **Outputs**
  - Estimated daily and monthly electricity costs (₱)
  - Total household electricity consumption and expenses
  - Appliance consumption rankings and percentage breakdowns
  - Category-based consumption summaries and averages
  - Comparison of two appliances' consumption and costs
  - Simulated consumption and costs based on adjusted operating hours
  - Updated appliance records and electricity rate settings

---

## 🧠 Logic Plan  
Describe your program’s logic:  

### Pseudocode  
Write your steps in plain English. Example:  
Load JSON file
Display menu of features
If user chooses "1", compute average grade per student
If user chooses "2", list all borrowed books
Repeat until user exits program

## Sample Wireframe
 -Main Menu
```
====================================================
                      		          KILOWATT
          Know Your Usage. Make Every Watt Count.
====================================================

          		HOUSEHOLD ELECTRICITY ANALYSIS

  [1] Appliance Registry
  [2] Consumption Calculator
  [3] Energy Analysis
  [4] Appliance Comparator
  [5] Usage Simulator
  [6] Settings and Data
  [7] Exit
----------------------------------------------------
Enter your choice:
```
- Appliance Registry
```
=============== APPLIANCE REGISTRY ===============

  [1] Add Appliance
  [2] View All Appliances
  [3] Search Appliances
  [4] Update Appliance
  [5] Delete Appliance
  [6] Return to Main Menu

-------------------------------------------------
Enter your choice:
```
(more in-depth sample wireframes in the pdf)
-Consumption Calculator
```
============== CONSUMPTION CALCULATOR ==============

ELECTRIC FAN
Daily Consumption:      0.480 kWh
Monthly Consumption:   14.400 kWh
Daily Cost:             PHP 5.76
Monthly Cost:            PHP 172.80

----------------------------------------------------

LED BULBS
Daily Consumption:      0.180 kWh
Monthly Consumption:    5.400 kWh
Daily Cost:             PHP 2.16
Monthly Cost:             PHP 64.80

----------------------------------------------------

TELEVISION
Daily Consumption:      0.400 kWh
Monthly Consumption:   12.000 kWh
Daily Cost:             PHP 4.80
Monthly Cost:            PHP 144.00
====================================================
               		  HOUSEHOLD TOTAL
====================================================
Daily Consumption:     1.060 kWh
Monthly Consumption:   31.800 kWh
Daily Cost:             PHP 12.72
Monthly Cost:            PHP 381.60
====================================================
```
-Energy Analysis
```
================ ENERGY ANALYSIS ================

Total Daily Consumption:    1.060 kWh
Total Monthly Consumption:  31.800 kWh
Estimated Monthly Cost:     PHP 381.60

--------------- CONSUMPTION RANKING --------------
1. Electric Fan - 14.400 kWh (45.28%)
2. Television   - 12.000 kWh (37.74%)
3. LED Bulbs    -  5.400 kWh (16.98%)

-------------- HIGHEST-CONSUMING APPLIANCE --------------
Electric Fan
14.400 kWh/month

-------------- AVERAGE CONSUMPTION ---------------
10.600 kWh/month per record

-------------- CATEGORY BREAKDOWN ---------------
Cooling:       14.400 kWh (45.28%)
Entertainment:  12.000 kWh (37.74%)
Lighting:       5.400 kWh (16.98%)

=================================================
```
-Appliance Comparator
```
=============== APPLIANCE COMPARATOR ===============

AVAILABLE APPLIANCES

ID: 1 - Electric Fan
ID: 2 - LED Bulbs
ID: 3 - Television
---------------------------------------------------
Enter first appliance ID: 1
Enter second appliance ID: 3

--------------- COMPARISON RESULTS -----------------
ELECTRIC FAN
Consumption: 14.400 kWh/month
Estimated Cost: PHP 172.80

TELEVISION
Consumption: 12.000 kWh/month
Estimated Cost: PHP 144.00
---------------------------------------------------
Consumption Difference: 2.400 kWh/month
Cost Difference: PHP 28.80
Electric Fan has the higher estimated consumption.

===================================================
```
-Usage Simulator
```
================ USAGE SIMULATOR ================

AVAILABLE APPLIANCES

ID: 1 - Electric Fan
ID: 2 - LED Bulbs
ID: 3 - Television

-------------------------------------------------
Enter appliance ID to simulate: 1
Selected Appliance: Electric Fan
Original Daily Usage: 8 hours
Enter hypothetical daily usage hours: 6

--------------- SIMULATION RESULTS ---------------
                  ORIGINAL       SIMULATED
Usage Hours:      8 hours        6 hours
Monthly kWh:      14.400         10.800
Monthly Cost:     PHP 172.80     PHP 129.60
-------------------------------------------------
Estimated Consumption Difference: 3.600 kWh/month
Estimated Cost Difference: PHP 43.20
Estimated cost is lower in this scenario.
Original appliance record remains unchanged.
=================================================
```
-Settings and Data
```
=============== SETTINGS AND DATA ===============

CURRENT ELECTRICITY RATE:
PHP 12.00/kWh

  [1] Change Electricity Rate
  [2] Return to Main Menu

-------------------------------------------------
Enter your choice: 1

Enter new rate per kWh (PHP): 13.50

Electricity rate successfully updated!
Saved for future calculations and simulations.

=================================================
```

### Flowchart  
Attach or draw a flowchart showing how the program will work.  

---

## 📂 GitHub Repository Link  
Paste your GitHub repository link here:  
https://github.com/shandanotarte27/Group10_Project_Proposal_ComputerScience2

## Assigned Team Members and Responsibilities
##Jeph Azriel G. Buniel
- Create the sample wireframes for the application.
- Create the sample interfaces of the main menu, appliance registry, consumption calculator, energy analysis, appliance comparator, usage simulator, and settings and data. Creating the pseudocode and flowchart.

##Gabrielle P. Exclamador
- Handle the GitHub Repository Link
- Provide the Github description, the ReadMe.md. Provide the brief description and problem statement.

##Shanda Therese D. Notarte
- Finish the Google Docs
- Encoding the project proposal on Google Documents and passing it on GitHub. Provide the outline of features. Inputting the Proposal Template on GitHub.

---
