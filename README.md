# Mental-Project

# Project overview
This repository contains a mental project. 
This project involves some functins like ranking,aggregation,navigation and distribution to extract actionable results aboout therapy usage,patient engagement and demand trends
**Envirnment**:Oracle database 10g
        
# ***STEP 1***
  # **Businesss content**
A mental health counselling center provides sessions to patients across regions. The operations and research team needs analytics therapist allocations, identify demand patterns, and priotize follow-ups.
   
  # **Data challenge**
The clinic records session-level data, but lacks consolidated analytics to:identify top therapies by regions,monitor monthly demand trends, and segment patii=ents by engagemnt level 

  # **Expected output**
Produce insights to:identify the top 5 therapies per region per quarter;compute running monthly session totals and month-over-month groeth;segment patients into quartiles; and compute 3 month moving averages to smooth demand
      
# ***STEP 2***
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

# ***STEP 3***
   Create user
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/089af6d120db4727d5145ee5bf47c9b88b6e71b9/Screenshot%20(216).png)
   Grant the DBA
  ![image alt](https://github.com/Melissa-10-10/plsql-window-functions--KAMANZI---MELISSA-/blob/752df6092d1dfe7550f90051946627f5c0c284dc/Screenshot%20(215).png)

**Tables**

   **codes**
  
   * patients
     
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/4f4a1b0642993f0131eb87eeaaa2a043ba7e01eb/Screenshot%20(217).png)

   * thearapies
  
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/70787dcfaf5cd2da7ce7c17e9da7232097b09998/Screenshot%20(218).png)
  
   * sessions
  
   * sequence session
  
   * triggers sessions
     
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/ca3237e3e33142f1f09fd7073a98725b53510ea1/Screenshot%20(219).png)
   
   **The result**
  
   * patient table
   
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/2ccf1987a0aa20fa58abbfdfbf2743cd31321dbc/Screenshot%20(220).png)
   
   * therapies table
   
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/f89473514a1628ed08e3fc40b0fc6166be4414ad/Screenshot%20(222).png)
   
   * session table
  
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/f1b22c6b635562ea68fe7bc763aa32e7ffecc9c1/Screenshot%20(221).png)

  ***THE ERD DIAGRAMS***
  
   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/df9581bb1e62ab6dd57fc18f3ebc1f807a6f0b5e/Screenshot%20(223).png)

   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/4f32d8f89101ea507d4dc23cf4c579c9b03cfae0/Screenshot%20(224).png)

   ![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/45e44e333800aa422731f335b01cd593502ca1ea/Screenshot%20(225).png)

    
# ***STEP 4***
  
   
   Window functions
   1.Ranking Function
 The query identifies which patients are most engaged wthin ach region  bytotal minutes. RANK() highlights ties,ROW_NUMBER() gives a unique order, and PERCENT_RANK() places patients on a 0.1 scale for relative position.
 ![image](https://github.com/Melissa-10-10/Mental-Project/blob/e71049d70af8f7d004216295f421bb7fdf8b9913/Screenshot%20(226).png)


  2.Aggregate function
Monthly_sessions shows the number of sessions each month.running_total accumulats counts across months and helps visualize growth.
![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/493ccb5a65ab2983c7d0c46557cafe28355fc486/Screenshot%20(227).png)


  3.Navigation functions
LAG() brings the previous month count into the current row.growth_pct computes the percent cange and shows where demand rose or fell
![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/9f05dcafd63b14ee0e7195bd7b66f0a370a55252/Screenshot%20(228).png)


   4.Distibution function
NTILE(4) creates four grroups;the top quartile helps identify the clinic's most frequent patients.CUME_DIST() shows cumulative proportion at each row.
![image alt](https://github.com/Melissa-10-10/Mental-Project/blob/610d33a8123dae1c2dbba9b7bdd7ec46bef45076/Screenshot%20(229).png)

# ***STEP 6***
 
**Descriptive (What happened)**

  * Example:Sessions increased from January to April, peaking in April, then fluctuated.
  * Example:Top 5 therapies account for the majority of sessions; top quartile patients account for  60% of the therapy minutes


**Diagnostic(why)**

  * Example:Higher counts in the cpital(Kigali) reflect better access and available therapists.
  * Example:Campaigns, workshops, or seasonal factors may expalin spikes


**Prescriptive(What next)**
  *Example:Expand teletherapy to rural regions to even out access.
  *Example:Assign more therapies in high-demand months and launch retention programs foe mid quartile patients.

# ***STEP 7***

# **REFERENCES**
 

1. Oracle Corporation. (2024). *Oracle® Database SQL language reference 19c.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/  

2. Oracle Corporation. (2024). *Oracle® Database PL/SQL language reference 19c.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://docs.oracle.com/en/database/oracle/oracle-database/19/lnpls/  

3. Oracle Corporation. (2010). *Oracle® Database SQL reference 10g release 2.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://docs.oracle.com/cd/B19306_01/server.102/b14200/toc.htm  

4. Kimball, R., & Ross, M. (2013). *The data warehouse toolkit: The definitive guide to dimensional modeling* (3rd ed.). Wiley.  

5. Viescas, J. L., & Hernandez, M. (2020). *SQL queries for mere mortals* (4th ed.). Addison-Wesley.  

6. Ben-Gan, I. (2021). *T-SQL window functions: For data analysis and beyond* (3rd ed.). Microsoft Press.  

7. Ramakrishnan, R., & Gehrke, J. (2020). *Database management systems* (3rd ed.). McGraw-Hill.  

8. American Psychological Association. (2023). *Mental health statistics and research.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://www.apa.org/topics/mental-health/statistics  

9. Mental Health Foundation. (2023). *Data on mental health engagement.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://www.mentalhealth.org.uk/explore-mental-health/statistics  

10. Oracle Live SQL. (2024). *Sample scripts – Analytic functions.* Retrieved from  
&nbsp;&nbsp;&nbsp;&nbsp;https://livesql.oracle.com/apex/livesql/file/index.html




  

   
     
   
           
       
                

    
