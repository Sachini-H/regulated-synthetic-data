This script  multiple_lines_multiple_days.ipynb can be used to generate the following events given some KPI constarints for multiple line for multiple days.

    FTT
    Defective
    Defects
    Reject
    Rectified
    Manpower
    Reject reasons
    Change

The inputs(in .xlsx format) we need are:

1. A plan for one day/ multipe days for the lines of interest
2, An hourly target table of KPIs for each day for each line (date column and hour column both)
3. General schedule (Assuming we reuse the same schedule for all days and all lines)
4. An example template for each event type (just to order the columns)


Step 1: In your google drive My Drive, create a folder named 'plan_data' .
Step 2: Download the constraints.xlsx file on this repo and upload it there.
Step 3: Download the following pre-trained synthesizer files to the fsame folder.
    count_synthesizer.pkl
    reject_synthesizer.pkl
    ftt_synthesizer.pkl
    defective_synthesizer.pkl
    defects_synthesizer.pkl
    rr_synthesizer.pkl

Now, if you want to create any set of events for the example plan data, 
-----------------------------------------------------------------------

Step 4: Run the script multiple_lines_targets.ipynp on Colab( You maybe required to provide drive access througha pop-up
UI when running the script.) This would generate some target basic KPI values for each line and module_id in the provided plan
and write the output to My Drive > plan_data > constraints.xlsx > target_kpis.

Now, if you want to create derived kpis such as hourly linewise efficiency and or hourly linewise defective rate values set to a pre-determined value, 
------------------------------------------------------------------------------------------------------------------------------------------------------
Step 4: Run the script targets_from_derived_kpis.ipynb on Colab( You maybe required to provide drive access througha pop-up
UI when running the script.) This would generate some target basic KPI values calculated from the derived kpis you can eneter from scratch or edit on 
constraints.xlsx > derived_kpis. Please refer the notes on the script about editing the details at the appropriate moment. This script would ultimately
calculate and write the basic rtarget KPI values to My Drive > plan_data > constraints.xlsx > target_kpis.


For any option above,
----------------------

Step 5: Now refresh the constarints.xlsx sheet and run the multiple_lines_multiple_days.ipynb on Colab (again providing access if needed)
Note : Make sure to edit the enline_qc station ids on cell 05 if the factory is different from the example. This script will generate the follwing .csv outputs on the colab files itself which you can download. It would also write all the resukts in .csv format to My Drive> example_results > csv_results folder which will be a newly generated folder specifically for writing the results.

    production.csv: contains all the FTT, Rectified, Reject and Defective events generated.
    plan.csv: plan dupmed as a .csv file. 
    regulated_synthetic_....csv : Each event type in a seperate csv file where ... referes to the above output event types mentioned in the begining.   

For generating json events from the above events,
--------------------------------------------------

Download 'generate_events_from_csv.ipynb' and run using Google Colb. You may need to provide access to the Google Drive. The script will write the results 
to My Drive> example_results > json_results folder which will be newly generated from the script to contain the json events.

    running_order_change, manpower, ftt, reject, defective, rectified .json files will contain json events for each event type.
    all_events.json will contain all the events combined into one json file. 
    







