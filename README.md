# Mental-Project
#Project overview
This repository contains a mental project. 
This project involves some functins like ranking,aggregation,navigation and distribution to extract actionable results aboout therapy usage,patient engagement and demand trends
Enxirnment:Oracle database 10g
         ## STEP 1
     # Businesss content
A mental health counselling center provides sessions to patients across regions. The operations and research team needs analytics therapist allocations, identify demand patterns, and priotize follow-ups.
    # Data challenge
The clinic records session-level data, but lacks consolidated analytics to:identify top therapies by regions,monitor monthly demand trends, and segment patii=ents by engagemnt level 
    # Expected output
Produce insights to:identify the top 5 therapies per region per quarter;compute running monthly session totals and month-over-month groeth;segment patients into quartiles; and compute 3 month moving averages to smooth demand
      
  #STEP 2
1. Top 5 patients per region -RANK()
   Returns top 5 patints per toatal therapy minutes for each region.
2. Running monthly session totals -SUM() OVER()
   Produce cumulative session counts month by month.
3. Month over month growth -LAG()/LEAD()
   Percent growth/decline in session counts vs previous month.
4. Patient quartiles -NTILE(4)
   Assign each patient to a quartle based on total minutes.
5. 3 Month moving average -AVG() OVER() with rows frame
   Rolling over sessions over last 3 months

    # STEP 3
   Create user
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/089af6d120db4727d5145ee5bf47c9b88b6e71b9/Screenshot%20(216).png)
   Grant the DBA
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/56db4beb6e888c7baafdd2f77f801ca6f0fd4d98/Screenshot%20(215).png)

    Tables

 codes
   .patients
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/4f4a1b0642993f0131eb87eeaaa2a043ba7e01eb/Screenshot%20(217).png)
   .thearapies
   .sessions
   .sequence session
   .triggers sessions
   The result
   >patient table
   >therapies table
   >session table

   THE ERD DIAGRAMS

     #STEP 4
   Window functions
   1.Ranking Function
 The query identifies which patients are most engaged wthin ach region  bytotal minutes. RANK() highlights ties,ROW_NUMBER() gives a unique order, and PERCENT_RANK() places patients on a 0.1 scale for relative position.


    2.Aggregate function
Monthly_sessions shows the number of sessions each month.running_total accumulats counts across months and helps visualize growth.


    3.Navigation functions
LAG() brings the previous month count into the current row.growth_pct computes the percent cange and shows where demand rose or fell


    4.Distibution function
NTILE(4) creates four grroups;the top quartile helps identify the clinic's most frequent patients.CUME_DIST() shows cumulative proportion at each row.
   
     
   
           
       
                

    
