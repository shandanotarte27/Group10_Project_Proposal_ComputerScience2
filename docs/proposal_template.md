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
```
START PROGRAM

DECLARE rate AS REAL
DECLARE appliances AS ARRAY OF RECORD
DECLARE choice, subchoice AS INTEGER
DECLARE id, id_1, id_2, quantity, next_id AS INTEGER
DECLARE wattage, hours, sim_hours, new_rate AS REAL
DECLARE daily_kwh, monthly_kwh, daily_cost, monthly_cost AS REAL
DECLARE orig_daily_kwh, orig_monthly_kwh, orig_daily_cost, orig_monthly_cost AS REAL
DECLARE sim_daily_kwh, sim_monthly_kwh, sim_daily_cost, sim_monthly_cost AS REAL
DECLARE kwh_1, kwh_2, cost_1, cost_2, kwh_diff, cost_diff AS REAL
DECLARE total_kwh, total_cost, average_kwh, share_pct AS REAL
DECLARE name, category, search_field, query AS STRING
DECLARE found AS BOOLEAN

LOAD rate, appliances FROM "kilowatt_data.json"
IF file is missing OR invalid THEN
    rate = 12.00
    appliances = empty list
    SAVE rate, appliances TO "kilowatt_data.json"
END IF

LOOP forever
    DISPLAY main menu (1. Registry, 2. Calculator, 3. Analysis, 4. Comparator, 5. Simulator, 6. Settings, 7. Exit)
    INPUT choice

    SWITCH choice
        CASE 1:
            DISPLAY registry menu (1. Add, 2. View, 3. Search, 4. Update, 5. Delete, 6. Back)
            INPUT subchoice
            SWITCH subchoice
                CASE 1:
                    INPUT name, category, wattage, quantity, hours
                    VALIDATE name non-empty, category valid, wattage > 0, quantity >= 1, hours from 0 to 24
                    next_id = maximum id in appliances + 1 (or 1 if empty)
                    ADD record (next_id, name, category, wattage, quantity, hours) TO appliances
                    SAVE rate, appliances TO "kilowatt_data.json"
                CASE 2:
                    IF appliances is empty THEN
                        DISPLAY "No appliances registered"
                    ELSE
                        DISPLAY all records in appliances
                    END IF
                CASE 3:
                    IF appliances is empty THEN
                        DISPLAY "No appliances registered"
                    ELSE
                        INPUT search_field, query
                        SEARCH appliances by id, name, or category matching query
                        IF no matches found THEN
                            DISPLAY "No matching records"
                        ELSE
                            DISPLAY matched records
                        END IF
                    END IF
                CASE 4:
                    IF appliances is empty THEN
                        DISPLAY "No appliances registered"
                    ELSE
                        INPUT id
                        FIND record in appliances with record.id == id
                        IF not found THEN
                            DISPLAY "Appliance not found"
                        ELSE
                            INPUT updated fields (keep existing value if left blank)
                            VALIDATE updated fields
                            UPDATE record in appliances
                            SAVE rate, appliances TO "kilowatt_data.json"
                        END IF
                    END IF
                CASE 5:
                    IF appliances is empty THEN
                        DISPLAY "No appliances registered"
                    ELSE
                        INPUT id
                        FIND record in appliances with record.id == id
                        IF not found THEN
                            DISPLAY "Appliance not found"
                        ELSE
                            REMOVE record FROM appliances
                            SAVE rate, appliances TO "kilowatt_data.json"
                        END IF
                    END IF
                CASE 6:
                    BREAK
            END SWITCH

        CASE 2:
            IF appliances is empty THEN
                DISPLAY "No appliances registered"
            ELSE
                total_kwh = 0.0
                total_cost = 0.0
                FOR EACH app IN appliances
                    daily_kwh = (app.wattage * app.quantity * app.hours) / 1000.0
                    monthly_kwh = daily_kwh * 30.0
                    daily_cost = daily_kwh * rate
                    monthly_cost = monthly_kwh * rate
                    total_kwh = total_kwh + monthly_kwh
                    total_cost = total_cost + monthly_cost
                    DISPLAY app, daily_kwh, monthly_kwh, daily_cost, monthly_cost
                END FOR
                DISPLAY total_kwh, total_cost
            END IF

        CASE 3:
            IF appliances is empty THEN
                DISPLAY "No appliances registered"
            ELSE
                total_kwh = 0.0
                total_cost = 0.0
                FOR EACH app IN appliances
                    app.monthly_kwh = ((app.wattage * app.quantity * app.hours) / 1000.0) * 30.0
                    app.monthly_cost = app.monthly_kwh * rate
                    total_kwh = total_kwh + app.monthly_kwh
                    total_cost = total_cost + app.monthly_cost
                END FOR
                SORT appliances descending BY monthly_kwh
                average_kwh = total_kwh / number of appliances
                GROUP and SUM monthly_kwh BY category
                FOR EACH app IN appliances
                    share_pct = (app.monthly_kwh / total_kwh) * 100.0
                    DISPLAY app, app.monthly_kwh, share_pct, app.monthly_cost
                END FOR
                DISPLAY category totals, highest consumer, average_kwh, total_kwh, total_cost
            END IF

        CASE 4:
            IF number of appliances < 2 THEN
                DISPLAY "Need at least two appliances"
            ELSE
                INPUT id_1, id_2
                IF id_1 == id_2 OR id_1 or id_2 not found THEN
                    DISPLAY "Select two distinct valid appliances"
                ELSE
                    kwh_1 = ((app_1.wattage * app_1.quantity * app_1.hours) / 1000.0) * 30.0
                    kwh_2 = ((app_2.wattage * app_2.quantity * app_2.hours) / 1000.0) * 30.0
                    cost_1 = kwh_1 * rate
                    cost_2 = kwh_2 * rate
                    kwh_diff = ABS(kwh_1 - kwh_2)
                    cost_diff = ABS(cost_1 - cost_2)
                    DISPLAY kwh_1, kwh_2, cost_1, cost_2, kwh_diff, cost_diff, higher consumer
                END IF
            END IF

        CASE 5:
            IF appliances is empty THEN
                DISPLAY "No appliances registered"
            ELSE
                INPUT id
                FIND app in appliances with app.id == id
                IF not found THEN
                    DISPLAY "Appliance not found"
                ELSE
                    orig_daily_kwh = (app.wattage * app.quantity * app.hours) / 1000.0
                    orig_monthly_kwh = orig_daily_kwh * 30.0
                    orig_daily_cost = orig_daily_kwh * rate
                    orig_monthly_cost = orig_monthly_kwh * rate
                    DISPLAY orig_daily_kwh, orig_monthly_kwh, orig_daily_cost, orig_monthly_cost
                    INPUT sim_hours
                    VALIDATE sim_hours from 0 to 24
                    sim_daily_kwh = (app.wattage * app.quantity * sim_hours) / 1000.0
                    sim_monthly_kwh = sim_daily_kwh * 30.0
                    sim_daily_cost = sim_daily_kwh * rate
                    sim_monthly_cost = sim_monthly_kwh * rate
                    DISPLAY sim_daily_kwh, sim_monthly_kwh, sim_daily_cost, sim_monthly_cost
                    DISPLAY (sim_monthly_kwh - orig_monthly_kwh), (sim_monthly_cost - orig_monthly_cost)
                END IF
            END IF

        CASE 6:
            DISPLAY settings menu (1. View Rate, 2. Change Rate, 3. Save Data, 4. Reload Data, 5. Back)
            INPUT subchoice
            SWITCH subchoice
                CASE 1:
                    DISPLAY rate
                CASE 2:
                    INPUT new_rate
                    IF new_rate > 0 THEN
                        rate = new_rate
                        SAVE rate, appliances TO "kilowatt_data.json"
                    ELSE
                        DISPLAY "Invalid rate"
                    END IF
                CASE 3:
                    SAVE rate, appliances TO "kilowatt_data.json"
                CASE 4:
                    LOAD rate, appliances FROM "kilowatt_data.json"
                CASE 5:
                    BREAK
            END SWITCH

        CASE 7:
            SAVE rate, appliances TO "kilowatt_data.json"
            EXIT LOOP

        DEFAULT:
            DISPLAY "Invalid choice"
    END SWITCH
END LOOP

END PROGRAM
```


## Sample Wireframe
 - Main Menu
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

- Consumption Calculator
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
- Energy Analysis
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
- Appliance Comparator
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
- Usage Simulator
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
- Settings and Data
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

```
                  ( START )
                      |
                      v
             / Load JSON Data /
                      |
                      v
              < Data Valid? >
               /          \
             Yes            No
              |              |
              v              v
       / Load Saved /   [ Initialize Data ]
       / Records    /          |
              \              /
               \            /
                    |
                    v
             [ Display Menu ]
                    |
                    v
             / Select Option /
                    |
        +-----------+-----------+-----------+-----------+-----------+-----------+
        |           |           |           |           |           |           |
        v           v           v           v           v           v           v
   [Registry]  [Calculator] [Analysis] [Comparator] [Simulator] [Settings]  [Exit]
        |           |           |           |           |           |           |
        v           v           v           v           v           v           v
 [Manage       [Calculate  [Generate   [Compare   [Simulate  [View/Change [Save Data]
  Records]      kWh & Cost] Insights]  Appliances] Usage]     Rate]          |
        |           |           |           |           |           |           v
        +-----------+-----------+-----------+-----------+-----------+       ( END )
                    |
                    v
              [ Return to Menu ]
                    |
                    +-------> [ Display Menu ]
```

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
