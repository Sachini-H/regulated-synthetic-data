This script  constrained_data_for_multiple_days.ipynb can be used to generate the following events given some KPI constarints for one palnned date for one particular line:

*   FTT
*   Defective
*   Defects
*   Reject
*   Rectified
*   Manpower
*   Reject reasons

The inputs we need are:

1. A plan for one day/ multipe days  for the line of interest
2. An hourly table of KPIs for each day (date column and hour column both)
3. General schedule (Assuming we reuse the same schedule for all days)
4. An example etmplate for each event type (just to order the columns)

We have all 4 sheets in one file  constraints_mul_days.xlsx  here which we will upload to **content/sample_data** in Colab when running the script.


 5. Synthesizers : Dump of all the pretrained synthesizers needed to generate  
    the constrained synthetic data.
    file names :
    count_synthesizer.pkl
    reject_synthesizer.pkl
    ftt_synthesizer.pkl
    defective_synthesizer.pkl
    defects_synthesizer.pkl
    rr_synthesizer.pkl
    
    **(Upload to content/sample_data when running the script)**



Now you can run the full script. 

The output files per attribute will be dumped under **content/** using the attribute name in .csv format.
The plan data will be saved to plan.csv file. 
FTT, reject, defective and rectified combined will be written to production.csv as well as to seperate files.
defects and reject reasons will also be avaialble as seperate .csv files.
