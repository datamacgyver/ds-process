# KPI Checks

The methodology here is dependent on how hard your KPIs are (giggerdy). 

If your KPIs are measurable (ie 70% accuracy), just make sure that you are 
able to tune for that in your model and keep tabs on it as you go through
your experiments. 

If they are softer then how will you evaluate them? What code/procedures do you 
need to produce an output that can be evaluated? How often will you do that? With
whom? 

## Baseline
This is a vitally important first step (if it's relevent to the output, of course). 
What is our naive performance? This may be:
* If we just gave everyone the same class/average value
* If we just matched on equality
* If we didn't attempt to tidy the data