The order of the VR notebooks from start to finish (predictions)
is 45_48VRNotebook1wFirstPoint-Copy1 --->
5_18__45_48_53_46FunctionClass --->
NEWESTall_SubsetFunctionClass-Copy1 --->
NEWESTRefPredNASA45_48_FULLDATA & then one each for subsets

I am only focusing on cells 45, 46, 47, 48.
Starting with the first notebook:

I look at cell 45 and the voltage and current for selected steps.
You can see there is VR based on the jump in voltage and
current. So, the filter_after_zero_current function aims
to capture that window where VR is happening. The filtering
looks at where 'Step_Time' is greater than 1000 and the 
difference in current is = to or > than 0.9. For other cells this
value may be 1. You have to look at the plots above to see
generally how big the jump in current is when VR happens and
adjust accordingly.

You have to run this function on each cell. Check the min()
values of the cell after this filtering to see which cells
were filtered. Some cells may return nan because no steps within them
experience VR. 

IMPORTANT: when we look at partial discharge data this
is where we could filter to see which steps did not fully 
discharge. The voltage to which the cells are supposed to 
discharge to might be different for each cell. We will have to 
look at the readme. So, we'd filter for VR and then filter for
partial discharge before moving on to the next notebook.

----------- NEXT NOTEBOOK ------------
Use the filtered VR data from the last notebook for this. 
This notebook contains several cell classes (45-48, 5-18, 53-56)
The logisitic-like function is the one we are using. If there
are other functions fit on the VR data, then it's just exploratory work.

So, you'll fit the function on each discharge step in a cell
and obtain the parameters ('fitted_df'). After, I am just looking
at how well the function fit on the data with the MSE and R2 values.
Finally, you'll merge that fitted_df with the original df_45 or df_whatevercell.
Add the 'Max_Temp' and get unique step and rebound pairs.
Then, save your parameter dataset as you see in the notebook.

^-- Do this for each cell.

-----NEXT NOTEBOOK------
This notebook takes the filtered VR data from the first notebook.
You are doing the same thing as the last notebook but breaking
it up into subsets of data. Subsets means time windows within
each step (30s, 60s, 120s, 180s). You will have to fit anf define 
these subsets for each cell. The idea is to compare the 
average parameter values from the full dataset to those (averaged) in each time window.
You can see mostly that (there are some exceptions as noted in notebook) the
smaller the time window, the most diff. the parameter values
are compared to the full dataset parameters. The reason we extract the parameters 
in each time window and the full is because we want to see
if the avg. % differences carry over into the prediction model as higher error.
The best case scenario is that Duke Energy can estimate the VR curve as soon as possible 
(30 seconds) and use that to accurately predict the discharge ref. capacity.

---NEXT NOTEBOOK---
This is pretty straight forward. Use either the parameter 
data from the full dataset (obtained in notebook 2) or
the parameter data from each subset (from notebook 3). Plug that
in and everything will run. Pay attemtion to the % RMSE 
for the models each time. 