# Exploration
This is in two parts: Solution and Data. In both cases please refer to the
[Questions to Ask](questions_to_ask.md) document for ideas of what kind of 
things we may want to check for.

## Data Exploration
High level thoughts below:
* Do the labels make sense?   
* Missing data/single valued columns/failed joins etc  
* Joins and database completeness  
* Can we make the predictor? 
* Do we notice any odd data quirks or types that need validation? 
* What would our feature set look like? What are their completeness?
    * This is a great chance to have a team review session for ideas!
* Are the data up to the task?  

### Team Feature Selection Session? 
Present the problem and your current exploration/feature set. Anyone can 
then contribute potential feature sets (including if they require new data!)

## Solution Exploration
This is a chance to have a deeper review of established toolsets that we will 
be using, are they up to the job? It includes a search for past work, blogs and 
papers that highlight the ways this could work (or not) in similar problem spaces. 

It's fine to have a preferred choice that seems to be the path of least resistance, but what's your plan B? C?
Why are they not the primary choice? We may need to either adjust our approach or 
pivot if there are problems. 


### Deploy-ability Check
As part of the above it may be wise to ask the question "How hard will this be to
deploy/productionise?" This may not be a q we can answer with the current state of
the function but it is something we need to at least accept our ignorance of and think
about!

* What  would the deployed model look like? What would be needed? 
* Will deployment be easy or hard? Will there be a complex bespoke model? Will we need engineering support? 
* Also consider things like retraining and monitoring.
* Will the deployed solution be costly to maintain (ie an always on API against a once a week batch?)

