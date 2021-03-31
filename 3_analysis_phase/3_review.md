# Output Review

*This process is iterative build, test, review, repeat. As such, each stage should
be checked against KPIs and requirements to assess if it's good enough.* 

The above being said, there is no need to wait until we are finished to review 
either internally or externally. There should be obvious check-gates during the 
process: I've got an MVP, I've tried a new feature set, I'm trying a different
model type, etc. For these, simply use parts of the External Review stage, below.

## Code Review
Before proceeding to external review or catchup session then another DS should 
review the code/approach. 

## Internal Review
Outline Agenda might be:
* Reminder: Project scope and product need
* Reminder: Selected approach after research phase
* Metric + soft & hard constraints for model selection
* Data used, pre-processing and feature engineering
* Models examined, training regime, hyper-parameter optimization.
* Selected model, alternatives & pros/cons of each.
* Next steps: Automation, productisation, performance optimization, monitoring, etc.
* Check the checklist. 

## External Review 
This phase doesn't have to happen whenever an internal review takes place. 

* Present the current model/solution to the stakeholder and evaluate it against any 
soft metrics. Effectively, make sure that it actually addresses the problem posed 
in the manner in which it is supposed to. 
    >For example, we may want to predict customer tiers but the owner notices that 
    all the customers that are in error are from a certain salesperson, we can 
    then add that to the model or adjust our KPIs/training data appropriately. 
* This is where you sign off any soft KPIs, but if this is an interim checkin then
you are simply checking progress. 
* You may additionally want to get some info from actual customers on the ground. 
* The stakeholder(s) need to be happy before we proceed to the next phase. 
